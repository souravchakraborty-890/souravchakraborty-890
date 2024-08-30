-from fpdf import FPDF

# Create a PDF class inheriting from FPDF
class ResumePDF(FPDF):
    def header(self):
        self.set_font('Arial', 'B', 16)
        self.cell(0, 10, 'Your Name', ln=True, align='C')

    def footer(self):
        self.set_y(-15)
        self.set_font('Arial', 'I', 10)
        self.cell(0, 10, 'Page %s' % self.page_no(), 0, 0, 'C')

    def add_section_title(self, title):
        self.set_font('Arial', 'B', 12)
        self.cell(0, 10, title, ln=True, align='L')

    def add_text(self, text):
        self.set_font('Arial', '', 10)
        self.multi_cell(0, 10, text)

# Initialize the PDF
pdf = ResumePDF()
pdf.add_page()

# Personal Details
pdf.add_section_title('Contact Information')
pdf.add_text('Email: your.email@example.com\nPhone: +1234567890\nLinkedIn: linkedin.com/in/yourprofile')

# Objective
pdf.add_section_title('Objective')
pdf.add_text('A brief description of your career objective or summary.')

# Work Experience
pdf.add_section_title('Work Experience')
pdf.add_text(
    'Job Title at Company Name\n'
    'Dates of Employment\n'
    'Brief description of responsibilities and achievements.'
)

# Education
pdf.add_section_title('Education')
pdf.add_text(
    'Degree, Major\n'
    'University Name, Year of Graduation\n'
    'Relevant coursework or achievements.'
)

# Skills
pdf.add_section_title('Skills')
pdf.add_text('List of skills: Programming, Design, Communication, etc.')

# Save the PDF
pdf.output('resume.pdf')

print("Resume created successfully!")
