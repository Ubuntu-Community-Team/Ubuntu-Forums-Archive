---
title: "about using Microsoft Core Fonts license"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by devjustly on 2012-10-23
Hello

i want ask about this package 
[https://apps.ubuntu.com/cat/applications/msttcorefonts/](https://apps.ubuntu.com/cat/applications/msttcorefonts/)

and i'm not sure, but i think is project from microsoft started and finished,
[http://en.wikipedia.org/wiki/Core_fonts_for_the_Web](http://en.wikipedia.org/wiki/Core_fonts_for_the_Web)
and in wikipedia said "These packages were published as freeware under a proprietary license imposing some restrictions on usage and distribution".


my questions are:

1 - can i download this pack of fonts "  Microsoft Core Fonts  "  or not, in other words can i install this fonts in ubuntu or not? and this pack is  **[COLOR="DarkRed"]legal[/COLOR]** or **[COLOR="DarkRed"]illegal[/COLOR]**, to use? and this is violation copyright or not??

more links:
[URL="http://www.microsoft.com/typography/faq/faq8.htm"]TrueType core fonts for the Web FAQ
[/URL]
[URL="http://www.microsoft.com/typography/fontpack/eula.htm"]TrueType core fonts for the Web EULA
[/URL]

i'm sorry for english, but is not my native language, and i can't understand clearly the END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE

and even this package contain TrueType fonts from microsoft i think
[URL="https://apps.ubuntu.com/cat/applications/ubuntu-restricted-extras/"]Ubuntu restricted extras
[/URL]
and why this statement "Commonly used applications with[COLOR="DarkRed"] restricted copyright [/COLOR]" this mean violation copyright ??

---

### Post by mikewhatever on 2012-10-23
Restricted does not mean not legal or violation. It simply means limited, and the EULA tells what you may do and may not do with the software. 

For example: 
> You may install and use an unlimited number of copies of the SOFTWARE PRODUCT

but, 
> You may not reverse engineer, decompile, or disassemble the SOFTWARE PRODUCT...

...and lastly,
>  Should you have any questions concerning this EULA, or if you desire to contact Microsoft for any reason, please contact the Microsoft subsidiary serving your country, or write: Microsoft Sales Information Center/One Microsoft Way/Redmond, WA 98052-6399.


---

### Post by mcduck on 2012-10-23
You have the freedom to download the fonts, and to use them, and it definitely isn't illegal.

However *distributing* the fonts is limited by certain rules(no renaming, no repackaging, no modifying, no derivative works etc.), which is why Ubuntu can't give the fonts to you or package them and distribute them directly from it's own servers. For this reason the package in the repositories uses a script to dowload the actual fonts for you.

---

### Post by devjustly on 2012-10-23
> **mikewhatever said:**
> Restricted does not mean not legal or violation. It simply means limited, and the EULA tells what you may do and may not do with the software. 

For example: 


but, 


...and lastly,
the following page contain microsoft fonts core
[http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/)

i'm using ubuntu 12.10.
if i download one of them to use, like **arial32.exe**	, this file is .exe extension, and when i double click i automatically open with archive manager, and if i extract it, i think this is considered as **decompile** or **disassemble**??

sorry for my english because is not my native language, and for my question may be little stupid, but i want to know, i not use illegal stuff

---

### Post by devjustly on 2012-10-23
> **mcduck said:**
> You have the freedom to download the fonts, and to use them, and it definitely isn't illegal.

However *distributing* the fonts is limited by certain rules(no renaming, no repackaging, no modifying, no derivative works etc.), which is why Ubuntu can't give the fonts to you or package them and distribute them directly from it's own servers. For this reason the package in the repositories uses a script to dowload the actual fonts for you.
but this 
[https://apps.ubuntu.com/cat/applications/msttcorefonts/](https://apps.ubuntu.com/cat/applications/msttcorefonts/)
is package, and is not permitted by microsoft like in EULA, and why this package is permitted by ubuntu, and why ubuntu not remove it from Ubuntu Software Center even added from other??

---

### Post by deadflowr on 2012-10-23
> **devjustly said:**
> the following page contain microsoft fonts core
[http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/)

i'm using ubuntu 12.10.
if i download one of them to use, like **arial32.exe**	, this file is .exe extension, and when i double click i automatically open with archive manager, and if i extract it, i think this is considered as **decompile** or **disassemble**??

sorry for my english because is not my native language, and for my question may be little stupid, but i want to know, i not use illegal stuff

Opening a file with archive manager only decompresses the image selected. There is no decompiling or disassembly involved.
Unfortunately, .exe files are windows-type files, and not linux-type files. As such, linux(Ubuntu) has to choose the most appropriate program to open and run it,m and so it uses the archive manager.

---

### Post by grahammechanical on 2012-10-23
You seemed to have missed a point that was made earlier:

>  For this reason the package in the repositories uses a script to dowload the actual fonts for you.

The fonts are not re-packaged. They are downloaded and installed as individual files. Each font is extracted from its exe file into a ttf font file. That is not decompiling or disassembling.


Microsoft released these fonts as Freeware. As much as they like they cannot remove those fonts from the public domain or take legal action against anyone using those fonts who has agreed to abide by the Microsoft End User Licence.

Ubuntu does not provide those fonts but does make it easier for a user to install them if the user makes a decision to install Microsoft Core fonts.

Ubuntu is open source and it is possible to use Ubuntu without any proprietary software at all. Some people may chose to have a completely Free and Open Source operating system. And that is another reason why Ubuntu does not install these things without the users agreement.

If you install Microsoft Core fonts through the Ubuntu Software Centre you will be asked to confirm your acceptance of Microsoft's licensing terms.

If you are unsure about the legality of any of this, then just do not accept the licensing agreement and the fonts will not be downloaded or installed.

Problem solved!

---

### Post by mikewhatever on 2012-10-23
> **devjustly said:**
> the following page contain microsoft fonts core
[http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/)

i'm using ubuntu 12.10.
if i download one of them to use, like **arial32.exe**	, this file is .exe extension, and when i double click i automatically open with archive manager, and if i extract it, i think this is considered as **decompile** or **disassemble**??

sorry for my english because is not my native language, and for my question may be little stupid, but i want to know, i not use illegal stuff

This forum is not the best place to seek legal advice. Since everything said so far has not been enough to reassure you, please contact Microsoft representative in your country and obtain a written permission to do whatever you do.

---

### Post by newb85 on 2012-10-23
> **mikewhatever said:**
> This forum is not the best place to seek legal advice.

+1

F.Y.I., *extract* is not the same as *decompile* or *disassemble*.  *Extract* is what you have to do in order to use to the font at all.  (Even Windows uses fonts in their .ttf form, not their .exe form.)  *Decompile* and *Disassemble* are both terms for reverse-engineering.

---

### Post by devjustly on 2012-10-24
i reassure now.
i just download .exe file "that freeware" and decompress it and move .ttf fonts and other file with it to my fonts folder in linux, and set fonts it as default font in my browser, that all.
and i think this is not violation of EULA of microsoft

thanks to all.

---

