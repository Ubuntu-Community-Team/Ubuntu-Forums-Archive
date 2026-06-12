---
title: "text editor where curly quotes don't become boxes or question marks"
date: 2015-09-08
forum: New to Ubuntu
---

### Post by dave194 on 2015-09-08
Switching from Windows to Ubuntu 14.04 I find that my HTML documents that I need to edit now display a box or a question mark instead of characters like curly quotes, etc.  I have tried LibreOffice and Bluefish.  Is there a text editor for Ubuntu that won't give me this issue?

Thanks,
Dave

---

### Post by coldraven on 2015-09-08
What is the output from the following command? It may be that you need to convert the character encoding.
```
file your_file.html
```

---

### Post by SeijiSensei on 2015-09-08
You should use HTML entities like &quot; to insure that your pages will display correctly everywhere.

---

### Post by vasa1 on 2015-09-08
Or upload a file that illustrates your issue?

---

### Post by Habitual on 2015-09-08
How are you 'editing' presently?

---

### Post by dave194 on 2015-09-09
> **coldraven said:**
> What is the output from the following command? It may be that you need to convert the character encoding.
```
file your_file.html
```
Sorry about the delay.  I didn't have access to the Ubuntu laptop until now.

The output is "HTML document, Non-ISO extended-ASCII text, with very long lines"

Thanks for your interest and help!

Dave

---

### Post by dave194 on 2015-09-09
> **Habitual said:**
> How are you 'editing' presently?For the past 15 years or so I have been creating and editing HTML files on Windows PCs, mostly using Eversoft's [IMG]http://www.evrsoft.com/images/dot_line.gif[/IMG]1st Page          2000.

Thanks,
Dave

---

### Post by dave194 on 2015-09-09
> **SeijiSensei said:**
> You should use HTML entities like &quot; to insure that your pages will display correctly everywhere.
Yes, that is the way I do it when I create pages myself.  But the project I'm working on has more than a thousand pages that were created by Microsoft Windows automatic process that converts a MS Word document to HTML -- and that's where all the curly quotes, hyphens, etc. come from.

Thanks.

---

### Post by The Cog on 2015-09-09
Well, I suspect it's been doing a pretty poor job of the conversion. Are you able to upload a small sample file that shows the problem (or a made-up sample if all the real documents contain private information)?

There is an editor called geany that edits ttxt files and has a very wide range of character encoding schemes to choose from. That might do the job for you. But once we know what the problem characters and correct replacements are, we can probably do the lot using sed in just a few minutes.

---

### Post by SeijiSensei on 2015-09-09
Dave has another thread about this subject where I made the same suggestion as The Cog: [http://ubuntuforums.org/showthread.php?t=2293773](http://ubuntuforums.org/showthread.php?t=2293773)

---

### Post by dave194 on 2015-09-09
Issue resolved!   In another thread in this forum  (  [http://ubuntuforums.org/showthread.php?t=2293773&p=13353073#post13353073](http://ubuntuforums.org/showthread.php?t=2293773&p=13353073#post13353073)  )  [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") gave me the solution:  use the **iconv** command-line utility like this:
```
iconv -f WINDOWS-1252 -t UTF-8 -o newfile.docx oldfile.docx
```
to translate from Win-1252 to UTF-8 before opening the file for editing in gedit. While editing I also change the charset line at the beginning of the HTML file  from iso-8859-1 to UTF-8.

So, gedit works fine after converting files using iconv.

Thank you, everyone, for your help.  Much appreciated!!!

---

### Post by Geoffrey_Arndt on 2015-09-09
SeijiSensei:   great work on the other thread (and for free yet)

But, this affirms another reason to be wary of "Vendor-Lockin" . . . . in other words, create those html, text-word, spreadsheet, project, and similar formats in a tool that uses real open formats.   Those folks that just continue to use only doc, docx yada yada yada just don't have a clue as to the long-term risks.

---

