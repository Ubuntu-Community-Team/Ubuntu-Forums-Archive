---
title: "How to scan and extract text from a printed document?"
date: 2015-03-30
forum: New to Ubuntu
---

### Post by g-me-5 on 2015-03-30
Hello everyone,

I need an app that i can use to scan documents with my scanner and then start on-screen character recognitioin to extract the text and formatting from it so that I can use on libre office writer.
Can anyone propose a solution?
Thanks.

---

### Post by slickymaster on 2015-03-30
After scanning the document, you'll have a .jpeg file. To make text in a .jpeg editable you'll need Optical Character Recognition (OCR) software.

See this: [OCR - Optical Character Recognition]("https://help.ubuntu.com/community/OCR")

---

### Post by Holger_Gehrke on 2015-03-30
The info about Tesseract in the wiki-page slickymaster linked to is *slightly misleading*. It correctly states that Tesseract uses the leptonica library for reading images but then later on warns that you need tif-files and that you get the best results by using black-and-white uncompressed tif. This used to be true for early 2.x versions but is simply and completely wrong by now. I've used it on both png and jpg files and it worked fine.

---

### Post by vasa1 on 2015-03-30
> **Holger_Gehrke said:**
> The info about Tesseract in the wiki-page slickymaster linked to is *slightly misleading*. It correctly states that Tesseract uses the leptonica library for reading images but then later on warns that you need tif-files and that you get the best results by using black-and-white uncompressed tif. This used to be true for early 2.x versions but is simply and completely wrong by now. I've used it on both png and jpg files and it worked fine.
You can edit that page and make necessary corrections.

---

### Post by g-me-5 on 2015-03-31
Thank you for your answers.
I found the solution.
I am using gscan2pdf and tesseract. And I do the scanning and OCR on the same GUI interface.

---

### Post by slickymaster on 2015-03-31
> **vasa1 said:**
> You can edit that page and make necessary corrections.
This ^^^

It's a community work.

---

