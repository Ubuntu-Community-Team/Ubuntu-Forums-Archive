---
title: "[SOLVED] Suggestion for creating documents using PHP"
date: 2008-01-20
forum: Programming Talk
---

### Post by Maxtorm on 2008-01-20
I wonder if I could pick your collective brains. I've designed a web-based sales application in PHP. The backend of the system is PostgreSQL. As part of the workflow for a given client record, the user will generate a document (a PDF in the current version) to present to the client. The document pulls together information from multiple tables in the database.

In the production version of the application, I am using AurgiaDoc ([http://aurigadoc.sourceforge.net/](http://aurigadoc.sourceforge.net/)) to generate the PDF, but this is not viable for the version currently in development. For one, control over the format is very limited. Secondly, it appears that AurigaDoc has not been actively developed for a number of years.

I've experimented with a couple of alternatives to AurigaDoc: PDFlib is great for creating simple PDFs, but as soon as you want to add any complexity to the document, it gets unwieldy from a coding perspective. I've tried outputting the data in LaTeX format and then converting the TeX document to PDF. This works well, but the resulting document always ends up looking like a research paper (as I understand it, this was the original intent of TeX, so no surprise there).

Recently I've toyed with the notion of using HTML and CSS's @media attribute to output the document. There are some limitations to this method too though: (1) headers and footers are controlled by the browser and therefore appear on every page -- in other words, forget about a "title" page; (2) though CSS does give you control over page breaks, it is difficult to predict where pages will break when the data is dynamic -- Section 2 might by three pages long in one document and 1/2 a page long in another -- so creating a table of contents would be difficult.

I apologize for the length of the post, but any suggestions you can offer will be greatly appreciated.

---

### Post by naugiedoggie on 2008-01-21
> **Maxtorm said:**
> I wonder if I could pick your collective brains. I've designed a web-based sales application in PHP. The backend of the system is PostgreSQL. As part of the workflow for a given client record, the user will generate a document (a PDF in the current version) to present to the client. The document pulls together information from multiple tables in the database.

In the production version of the application, I am using AurgiaDoc ([http://aurigadoc.sourceforge.net/](http://aurigadoc.sourceforge.net/)) to generate the PDF, but this is not viable for the version currently in development. For one, control over the format is very limited. Secondly, it appears that AurigaDoc has not been actively developed for a number of years.


Hello,

Perhaps, this will help.

[Apache FOP]("http://xmlgraphics.apache.org/fop")

Your PHP would output XML and FOP would convert to PDF.  I'm not sure if you will have to do any intermediary processing, or not.  No doubt, you'll have to write the stylesheets.

Thanks.

mp

---

### Post by Maxtorm on 2008-01-21
That is perfect. Thank you!

---

