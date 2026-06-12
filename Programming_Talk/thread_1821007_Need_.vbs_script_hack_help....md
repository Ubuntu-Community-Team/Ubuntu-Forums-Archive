---
title: "Need .vbs script hack help..."
date: 2011-08-08
forum: Programming Talk
---

### Post by Moozillaaa on 2011-08-08
I need to modify syntax to target a folder in a particular drive, rather than the entire drive.

The entire script is at post #4 [here]("http://forums.techguy.org/software-development/965925-solved-script-file-multiple-hyperlink.html").

ALTHOUGH, I think the only modification necessary is in the beginning:
 
> strFirstDrive = "E"
strLastDrive = "N"
strSavePath = "C:\Test\Index.docx"
Const ShowDoc = True
Const CloseDoc = True
[SIZE=4]**...**[/SIZE]Only 1 drive will be read, so I can change first + last drive accordingly:
 
> strFirstDrive = "**[COLOR=Red]J[/COLOR]**"[COLOR=White]..................**.**[/COLOR]**[COLOR=Red]"J:\FolderName"[/COLOR] maybe???**
strLastDrive = "[COLOR=Red]**J**[/COLOR]"
strSavePath = "C:\Test\Index.docx"
Const ShowDoc = True
Const CloseDoc = True
[SIZE=4]**...**[/SIZE]

---

