# Techo Tales

When setting up your own book, you'll want to put your title here instead of mine.

## About the Book

10 Technical Parables for the Modern Age

## Getting Started

These instructions will guide you through the setup and understanding of the structure of this book project.

### Prerequisites

- Pandoc for converting Markdown to various formats.
- Node.js for running scripts and managing dependencies.
- Basic understanding of Markdown and YAML.

### Structure

- `back-matter/`: Contains the back matter of the book, such as index, bibliography, appendices, etc.
- `chapters/`: Each Markdown file here represents a chapter of the book.
  - `images/`: Images used in the chapters are stored here.
- `front-matter/`: Contains the front matter of the book, including title page, foreword, preface, and table of contents.
- `output/`: The destination for the book's compiled output files (PDF, EPUB, etc.).
- `custom-reference.docx`: Custom reference document for styling the book.
- `package.json`: Node.js package file for managing scripts and dependencies.
- `title.yaml`: Contains metadata for the book (title, author, etc.).

### Setup

1. Clone the repository or download the files to your local machine.
2. Ensure Pandoc and Node.js are installed on your system.
3. Navigate to the project's root directory in your terminal.
4. Run `npm install` to install required Node.js dependencies.

## The `title.yaml` File

The `title.yaml` file is a crucial component of the book project. It contains metadata about the book which is used in the compiling process, especially when generating different formats like EPUB, PDF, or DOCX. Here's how to understand and use this file:

### Structure and Content

Your current `title.yaml` file contains the following fields:

- `title`: The main title of your book.
- `subtitle`: A secondary, more descriptive title.
- `author`: The name of the book's author.
- `language`: The language code (e.g., `en-US` for American English).
- `rights`: Copyright notice or rights statement.
- `cover-image`: The path to the cover image file.

### Editing the `title.yaml`

You can edit or add more fields to the `title.yaml` file depending on your requirements. Some additional fields you might consider are:

- `publisher`: The name of the publishing entity.
- `published`: The publication date.
- `ISBN`: The International Standard Book Number.
- `keywords`: A list of relevant keywords for searchability and categorization.

### Usage

When you compile your book, Pandoc (or any other tool you're using) will use the information in `title.yaml` to populate metadata fields in the output formats. For example:

- In an EPUB file, this metadata helps e-reader software display your book correctly.
- In PDFs, this metadata can be used for properties like author name and title.

Make sure the fields in `title.yaml` are accurate and up-to-date, as they play a significant role in how your book is presented and identified in digital formats.

### Example

Here's an extended example of what `title.yaml` might look like:

```yaml
---
title: Technotales
subtitle: Reimagined Parables for the Modern Age
author: Michael D. Callaghan
language: en-US
rights: © 2023 Michael D. Callaghan, All Rights Reserved
cover-image: chapters/images/cover.jpg
publisher: [Your Publisher Name]
published: 2023-12-08
ISBN: 123-4567890123
keywords: [technology, parables, software development, tech enthusiasts]
---
```

This file is not just a part of the book; it's a part of its identity in the digital world. Make sure to keep it updated as your book evolves.

## The `custom-reference.docx` File

The `custom-reference.docx` file plays a crucial role in the formatting and styling of your book when it is converted to document formats like Word (.docx) or Kindle (.kdp.docx). This file acts as a template, influencing the appearance of the final output.

### Purpose and Functionality

When converting Markdown files to a Word document, Pandoc can use a custom reference Word document to apply specific styling and formatting. This includes:

- Font types and sizes.
- Heading styles.
- Paragraph spacing and indentation.
- Page margins, headers, and footers.
- Any other Word-specific formatting that Pandoc can interpret.

### How to Edit and Customize

1. **Open and Modify**:

   - Open `custom-reference.docx` in a word processor like Microsoft Word or LibreOffice.
   - Modify the styles as you would in any Word document. For instance, change the heading styles, adjust paragraph formats, or set the desired page layout.

2. **Save Your Changes**:

   - After making the necessary stylistic adjustments, save the document. Ensure it remains in the `.docx` format.

3. **Consistent Styles Across Formats**:
   - When you apply styles in the reference document, ensure they align with the styles used in your Markdown files for consistency across different formats.

### Usage in the Project

- The `custom-reference.docx` is referenced in the scripts within your `package.json` for generating `.docx` and `.kdp.docx` files.
- When these scripts are executed, Pandoc looks at your `custom-reference.docx` and applies its styles to the output document.

### Example

If you want your book chapters to have a specific font or size in the Word document, you would set this in the `custom-reference.docx`. When Pandoc generates the Word version of your book, it will use these style settings, ensuring your chapters appear as intended.

### Best Practices

- **Version Control**: Keep your `custom-reference.docx` under version control to track changes over time.
- **Consistency**: Ensure the styling in the `custom-reference.docx` is consistent with the overall design and tone of your book.
- **Testing**: After modifying the reference file, generate a test document to ensure the output meets your expectations.

The `custom-reference.docx` is a powerful tool for ensuring that your book's digital formats maintain a consistent and professional appearance. Carefully crafting this document can significantly enhance the readability and aesthetic appeal of your book.

## Compiling the Book

This project includes several NPM scripts defined in `package.json` for compiling the book into various formats. Here's how to use each script:

1. **Split Markdown**:

   - Command: `npm run split-md <filename>`
   - This script uses `awk` to split a single Markdown file into multiple chapter files. It's helpful if you have a large Markdown file that needs to be divided into separate chapters.

2. **Generate EPUB**:

   - Command: `npm run generate:epub`
   - This script compiles the book into an EPUB format. It gathers content from the front matter, chapters, back matter, and uses the `title.yaml` for metadata. The output is saved in the `./output` directory.

3. **Generate PDF**:

   - Command: `npm run generate:pdf`
   - This script creates a PDF version of the book. It includes a table of contents and combines content from the front matter, chapters, and back matter. The final PDF is stored in the `./output` directory.

4. **Generate Word Document**:

   - Command: `npm run generate:word`
   - Use this script to generate a Word document (.docx) version of the book. It uses the `custom-reference.docx` file for styling and includes content from all parts of the book. The output is placed in the `./output` directory.

5. **Generate KDP (Kindle Direct Publishing) Format**:
   - Command: `npm run generate:kdp`
   - This script is specifically for preparing a document suitable for Kindle Direct Publishing. It outputs a .docx file formatted for KDP requirements, including the necessary front matter, chapters, and back matter.

Before running these scripts, ensure that Pandoc is installed on your system as it's the tool used for the conversion process. Each script is designed to make the compilation process straightforward, allowing you to focus on writing and content organization.
