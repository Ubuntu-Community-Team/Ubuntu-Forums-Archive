---
title: "App for .tsv files (tabular separated values)"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by JustinTBrown on 2012-01-14
Hi all, I've searched through previous posts but could not find anything.

Is there a spreadsheet application for linux that can import/export .tsv files? I've tried LibreOffice, Gnumeric and KSpread but neither will work with .tsv files.

Any suggestions?

Best,
Justin

---

### Post by I_can_see_the_light on 2012-01-14
Welcome to the forums :)

So starting LibreOffice Calc and going *Insert>Sheet from file*selecting your file and changing **Separator options** to Tab doesn't do it?

---

### Post by JustinTBrown on 2012-01-21
Thanks for the warm welcome!

Regarding LibreOffice Calc, the separator options do allow you to import .tsv data, but there is no way I know of to export the data you're working with back to a .tsv file.

---

### Post by HermanAB on 2012-01-21
Just save it to CSV and then change the \t to \n using cat and the s// operator, or vice versa.  Read a Bash guide.

---

### Post by SeijiSensei on 2012-01-21
In gnumeric, select "text (configurable)" in the Save dialog.  You'll then be able to select Tab as the delimiter.  I think you can name the file something.tsv, but if it is saved as something.txt, just rename it to something.tsv if you have an application that requires that extension to define a tab-delimited file.

While most file extensions are arbitrary, I've not seen .tsv very often if at all.  .csv is widespread because it was used by Microsoft.  I just use .txt for tab-delimited files like I do for all plain-text files.

---

### Post by JustinTBrown on 2012-01-21
Thanks SeijiSensei!

Gnumeric does in fact let you save directly to .tsv filetype via the "text (configurable)" option in the save dialog.

---

