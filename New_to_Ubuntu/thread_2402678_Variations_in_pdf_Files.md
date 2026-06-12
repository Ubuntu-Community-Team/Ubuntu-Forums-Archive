---
title: "Variations in pdf Files"
date: 2018-10-03
forum: New to Ubuntu
---

### Post by electrosteam on 2018-10-03
Lubuntu 18.04 LTS on a 2002 Dell laptop with LibreOffice 6.0.6.2 and LibreCad 2.1.2.

Did some simple CAD drawings, printed them to file as pdfs and transferred them to a USB flashdrive.

The pdf files on the USB open ok with LibreOffice Draw and Document Viewer under Lubuntu.
The home office modern laptop with Windows 10 opens the files and prints them, but the quality was poor due to bad inks.

The USB was taken to the local OfficeWorks centre on the self-serve machines where the files display with the pdf (Adobe) icon, but cannot be opened .
At the customer service desk, the files display as not recognised with a blank icon (presumably with a Windows OS).

Is there some sort of variation in pdf files that could explain this ?
If so, can it be corrected ?

John

---

### Post by Claus7 on 2018-10-04
Hello,

I guess that the version of adobe program in the OfficeWorks center might be older and cannot open the pdf files in question. You have already tested them in a windows system and they worked... Did you see, by any chance, the version used?

It would be a fuss, yet you could try an older ubuntu version with older versions of the programs in question and you could check if that way the files could be opened.

Someone else might have another idea about this issue,
Regards!

---

### Post by electrosteam on 2018-10-04
Claus7,
Searching the web reveals no mention of a specific problem.

Checked the files, they are Version 1.4.
I believe the latest version is either 1.8 or 2, so any 'modern' equipment should open them.
Actions:
 - visit a small local printer we do a lot of society business with and see what they know/do/comment,
 - re-do Print-to-File all the original dxf drawings on a Windows machine,
 - try the LibreCad 'Export to PDF' option.

I tried the Export option months ago without much joy, that is why the Print-to-File approach was adopted.
John

---

### Post by Claus7 on 2018-10-04
Hello,

apart from checking the version of your files, you might have to check, if possible, the version of adobe reader of the local store you are talking to. In case that is old (which I doubt) then it might not be possible to open the files. The weird thing is that a windows box could actually "see" those files. 

Another thing I suspect is an issue with the usb stick used: sometimes if not plugged correctly it might not load properly your files and that's why it was not possible for them to open.

Good luck,
Regards!

---

### Post by electrosteam on 2018-10-07
The small printer company also could not open the files, not known what version of Windows.
Tried the files on my wife's Windows 10 machine with attached printer, but the quality was terrible.

Back to LibreCad and ran the Export-as-PDF options, knowing that previous efforts were failures.
Persevered with several issues, but got there finally.
Discovered the real problem with this option is the need to do a Print-Preview before the export.

Back to OfficeWorks and printed fine.

The variations in pdf files is still a mystery.
John

---

### Post by mastablasta on 2018-10-09
don't know about CAD, but with text files you need to actually make sure you include fonts, page setups and such within the file. by default this stuff is usually omitted on exports or prints to file options. if they are not fully inlcuded they get displayed differently on different PDF readers. They also print in a different way. found that out when creating a digital book. and had to reuse it later when i did a PDF form for customers (don't ask).

the point is if it was opened on my PC where i had the fonts for example. it all displayed OK, but at customer who didn't have the font a replacement was used and it all got messed up.

---

### Post by electrosteam on 2018-10-09
mastablasta,
Thanks, this gives me a new line of investigation.
I will resolve it, because printing at the local OfficeWorks does give a much better quality suitable for presentation documents.
There was a hint on the Windows machine when I opened a faulty pdf file that it could export it as a PostScript file - something to check.
John.

---

