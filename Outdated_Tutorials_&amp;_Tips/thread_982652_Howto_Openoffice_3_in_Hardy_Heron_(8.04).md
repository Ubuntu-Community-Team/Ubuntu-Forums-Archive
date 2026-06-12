---
title: "Howto: Openoffice 3 in Hardy Heron (8.04)"
date: 2008-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by RequinB4 on 2008-11-14
A note for this tutorial: if you are using a language other than English the exact commands that I post here won't work, but you can substitute for non-English file names.

This tutorial is written assuming you want to keep the 2.4 version on your box.

Step 1 - Download

Go to [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the file in your language (english) under the "Linux DEB" column.  Save in your home directory.

Step 2 - Install

Open a terminal in Applications - Accessories - Terminal and run:
```

tar xvfz OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
cd OOO300_m9_native_packed-1_en-US.9358/DEBS/
sudo dpkg -i *.deb

```

Step 3 - Shortcut (If you don't wish to keep 2.4, remove 2.4 using synaptic and do the following instead: [http://ubuntuforums.org/showpost.php?p=6208676&postcount=2](http://ubuntuforums.org/showpost.php?p=6208676&postcount=2))

Open your favorite text editor and copy, paste, and save the following as ooo3.desktop in  ~/.local/share/applications/ 

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Terminal=0
Exec=/opt/openoffice.org3/program/soffice
Icon=ooo-template
Type=Application
Categories=Application;Office;WordProcessor
StartupNotify=false
MimeType=text/plain;
InitialPreference=5
Name=OpenOffice.org 3.0
Comment=Create and edit text, graphics, presentations, and databases in letters, reports, documents, and Web pages.
NoDisplay=false

```

Step 4 - Filetypes

Simply go to a .doc or .odt or whatever file in nautilus (the file manager), right click 'Properties' and click 'Open With'- 'Add' - 'Use custom command'

enter
```

/opt/openoffice.org3/program/soffice

```

And press Add.  The 'soffice' button should be already selected - select it if it isn't.

=========================================================================

That's it.  Now you should open .doc and .odt files with OpenOffice 3.0 and you can open 3.0 by going to applications - Office - OpenOffice.org 3.0

---

### Post by bluelightav on 2008-11-19
I wouldn't use the suggested short cut (step 3) but instead 

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration

sudo dpkg -i *.deb
```

Log out  and in again and you have nice icons:)

---

### Post by RequinB4 on 2008-11-20
> **bluelightav said:**
> I wouldn't use the suggested short cut (step 3) but instead 

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration

sudo dpkg -i *.deb
```

Log out  and in again and you have nice icons:)

I was going to put that but I recall reading somewhere it conflicts with 2.4 icons.  True?

---

### Post by bluelightav on 2008-11-20
> **RequinB4 said:**
> I was going to put that but I recall reading somewhere it conflicts with 2.4 icons.  True?

I removed OpenOffice 2.4 as I want to use 3.0.

---

### Post by Vim on 2009-03-18
The current version of OO is 3.0.1.  I therefore replaced the first of the 3 commands of your step 2 with:
[INDENT]tar xvfz OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz
[/INDENT]
After I executed that command something like 20 or 30 lines scrolled by each, except the first one, beginning with:
[INDENT]000300_m15_native_packed-1_en-US.9379/DEBS/o.....
[/INDENT]It seemed like the ending of each of the 20 or 30 lines was unique.  The output then ended with a blank line, followed by:
[INDENT]gzip: stdin: unexpected end of file
   tar: Unexpected EOF in archive
   tar: Unexpected EOF in archive
   tar: Error is not recoverable: exiting now
[/INDENT]I would appreciate any suggestion as what to do next.

---

### Post by Roanoke on 2009-03-21
Or you could just add the open office ppa :P

---

