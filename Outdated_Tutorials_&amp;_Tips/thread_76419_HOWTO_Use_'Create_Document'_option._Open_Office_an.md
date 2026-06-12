---
title: "HOWTO: Use 'Create Document' option. Open Office and custom files."
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2005-10-15
**Also works for previous releases of Ubuntu**

1. This howto will show you how to making files fast in your desktop.
2. What it does: When you right click your desktop, you can easely pick a file type under Create Document.


Open file browser. In the tab choose Go --> Templates

To create a Text Document. Make a new file in Templates and name it Text document.txt
Now you can see that if you right clicks somewhere on your desktop and choose create Document there's a Text Document to choose.
You can do that with any file type. Eg. making a Shell Script: Shell Script.sh in the templates.


_For Open Office, Here's how you do._

Open OpenOffice Calc. Then 'Save as' OpenOffice Calc.ods into Templates.
Do the same with the other OpenOffice application.
OpenOffice Calc.ods
OpenOffice Draw.odg 
OpenOffice Impress.odp 
OpenOffice Math.odf
OpenOffice Word.odt


Or simple download the file I've linked an unpack it in Templates. It contains the OpenOffice, text document and shell script template file ready to use immedatly. (see attachment)

If you want to split it up in catagories just make a folder in Template and move around the diffrent Template files.

[IMG]http://thilockdominus.freehomepage.com/Screenshots/Templates.jpg[/IMG]

---

### Post by jobezone on 2005-10-17
I think this menu is very interesting for users who tipically has to often create a certain type of file, with a certain type of content.
 As an example, say a person regularly creates Tests/Exams of various kinds. He could pick from the ones the did the most typical ones, edit them, remove or replace their content, leaving the structure intact, then save them as "Psichology/whatever Exam" files under that directory. Other exaples of very used files: CD-labels (with different versions of weather it's for an audiocd, a ogg music cd, a data cd, or a video cd), Professional Letters (with the typical, "Dear Sir", "Signature", etc.), etc.

---

### Post by Wolki on 2005-10-17
This is a very useful thread.

Two additions: You can also create files in other folders, not only on your desktop.
The Templates folder is also available in spatial Nautilus from the Places menu.

---

### Post by mgor on 2005-10-17
ah, i've wondered how to make more templates ;-)

just a little note, when you create, lets say, Shell script.sh in the templates directory, open the file and add
```
#!/bin/bash
```
or PHP Script.php, open the file and add
```
<?php
?>
```

so when you create the file from the template it'll contain what ever you put in it!

*edit* wops, that's what jobezone said.

---

### Post by craigmac on 2005-10-17
Thanks for the excellent tip. It works a treat. 

There really are a lot of things that I took for granted in Windows that I haven't found out how to do yet. I can cross this off the list.:p

---

### Post by sethmahoney on 2005-10-17
Hey, great!  Thanks for the howto (and the files) - they work perfectly!

(BTW, what theme are you using in the screenshot?)

---

### Post by henrypootel on 2005-10-17
Great Tip.
Thats one thing i miss(!) from windows.

---

### Post by bam on 2005-10-19
was wondering what do do with that....great tip! Thanks!

---

### Post by Perfect Storm on 2005-10-20
[QUOTE=jobezone]I think this menu is very interesting for users who tipically has to often create a certain type of file, with a certain type of content.
 As an example, say a person regularly creates Tests/Exams of various kinds. He could pick from the ones the did the most typical ones, edit them, remove or replace their content, leaving the structure intact, then save them as "Psichology/whatever Exam" files under that directory. Other exaples of very used files: CD-labels (with different versions of weather it's for an audiocd, a ogg music cd, a data cd, or a video cd), Professional Letters (with the typical, "Dear Sir", "Signature", etc.), etc.[/QUOTE]

Aye, there's a lot of possibilities. Especially at work where you can make diffrent standard letters or formulars. Like making a folder in Templates called eg. Water Pipe formulars and in there you have diffrent text documents with each diffrent setups.

---

### Post by royg1234 on 2005-12-06
I want to make a GIMP template, but I don't like the way the icon in the menu is a thumbnail of an empty image.  How do I change the icon to be the same as the system's icon for xcf files?

---

### Post by ToastedToad on 2005-12-06
Thank you very much. Very Useful.

---

### Post by christooss on 2005-12-06
Very very very nice and useful :)

Thanks and Bye

---

### Post by benplaut on 2005-12-06
that's incredibly useful! also, put a number in front of the name of each type to make a bit more order ;)

---

### Post by bicchi on 2005-12-06
Great tip. You actually inspired me to write my own set of templates:

Cascading Style Sheets.css
C C++ Header.h
C source code.c
C++ source code.cpp
HTML Document.html
JavaScript.js
Java source code.java
Makefile
OpenOffice Calc.sxc
OpenOffice Draw.sxd
OpenOffice Impress.sdd
OpenOffice Math.sxm
OpenOffice Word.sxw
Perl Script.pl
PHP Script.php
Python Script.py
Shell Script.sh
Tar compressed with gzip.tgz
Tar uncompressed.tar
Text Document.txt
Zip compressed.zip


The (tar, tgz and zip) files were created with "Archive Manager". Just create 3 empty (tar, tgz and zip) files, place any file inside each of them and then remove the file you put in it. This process actually creates the (tar, tgz and zip) files but leaves you with no documents compresssed/tarred inside the file.

You can put "Hello Word" applications in the rest of the files to get to you started when coding. Or perhaps you favorite template for a Makefile. 

Thanks for providing the tip. :)

---

### Post by Ali_Taimur on 2005-12-06
:( :(  How can i do this in kubuntu??

Why do i always get this is feeling that kubuntu folks are considered step children of ubuntu here :(

---

### Post by Perfect Storm on 2005-12-07
To Ali Taimur.

I really don't know how to do this in KDE. I'm completly a gnome user (and with E17 as my play DE). But perhaps there's a KDE user out there who can write a HOWTO on this ssubject for the KDE users.

> 
Why do i always get this is feeling that kubuntu folks are considered step children of ubuntu here

because the KDE users are a minority in ubuntu, if you want some howto/tips/tricks perhaps you could write in the KDE forum and ask to pull them self together ;)

---

### Post by sabmann on 2005-12-07
is there a way to change the ```
/home/<username>/Templates 
```folder to ```
/home/<username>/.Template
```
I really hate it when I see my home dir with a lot of folders that I don't use :rolleyes:

---

### Post by Wolki on 2005-12-07
[QUOTE=sabmann]is there a way to change the ```
/home/<username>/Templates 
```folder to ```
/home/<username>/.Template
```
I really hate it when I see my home dir with a lot of folders that I don't use :rolleyes:[/QUOTE]

Not that I know of. You can create a text file called ".hidden" in your home directory and write "Templates" there, this will cause nautilus to hide it. The File Selector (ie open dialog) will still show it, but that will hopefully be fixed for the next version.

---

### Post by jmooney on 2005-12-15
That's very helpful, thanks.  The one gripe I do have about GNOME is good documentation is hard to find.

I wonder if you could answer another question?  How do I get the "Open Terminal" option when I right click?  Even better, can I configure it so that when I've browsed to a specific location in Nautilus, I can open a terminal in that directory?  (like you can do with KDE?)

If somebody could point me to full documentation on use and configuration of GNOME, that would be great as well.

Thanks,

Joe

---

### Post by vyruss on 2005-12-16
[QUOTE=jmooney]I wonder if you could answer another question?  How do I get the "Open Terminal" option when I right click?  Even better, can I configure it so that when I've browsed to a specific location in Nautilus, I can open a terminal in that directory?  (like you can do with KDE?)[/QUOTE]
Follow these steps:

[LIST=1][*]Download the attached script I wrote[*]Copy it to **~/.gnome2/nautilus-scripts**[*]Rename it to "Open Terminal Here" or whatever you like[*]Make it executable by: **chmod +x "Open Terminal Here"**[/LIST]

Now whenever you right-click in a folder, choose **Scripts -> Open Terminal Here**.

---

### Post by jmooney on 2005-12-16
[QUOTE=vyruss]Follow these steps:

[LIST=1][*]Download the attached script I wrote[*]Copy it to **~/.gnome2/nautilus-scripts**[*]Rename it to "Open Terminal Here" or whatever you like[*]Make it executable by: **chmod +x "Open Terminal Here"**[/LIST]

Now whenever you right-click in a folder, choose **Scripts -> Open Terminal Here**.[/QUOTE]

Thanks, I'll give it a shot...

Joe

---

### Post by jmooney on 2005-12-18
Works great, thanks.  Plus, with a slight tweak to your script, I was able to add a root terminal as well.

Joe

---

### Post by henriquemaia on 2005-12-22
Great tip. It's a great help.

There are also quite good tips along this thread. To all, thanks.

---

### Post by leech on 2006-01-10
[QUOTE=vyruss]Follow these steps:

[LIST=1][*]Download the attached script I wrote[*]Copy it to **~/.gnome2/nautilus-scripts**[*]Rename it to "Open Terminal Here" or whatever you like[*]Make it executable by: **chmod +x "Open Terminal Here"**[/LIST]

Now whenever you right-click in a folder, choose **Scripts -> Open Terminal Here**.[/QUOTE]

He could also just 'sudo apt-get install nautilus-open-terminal' :D

This is a great tip, I was always wondering how to create the templates, but never really looked into it too much.

Leech

---

### Post by vyruss on 2006-01-13
[QUOTE=leech]He could also just 'sudo apt-get install nautilus-open-terminal' :D

This is a great tip, I was always wondering how to create the templates, but never really looked into it too much.

Leech[/QUOTE]


[Bart Simpson voice] Oh, man!

I had no idea this already existed! Oh well, at least we all learned something useful :)

---

### Post by jamesdodd on 2006-03-01
Some great tips in this post, thanks to all who contributed.

I know a few friends who will appreciate this too ;)

---

### Post by Perfect Storm on 2006-03-26
Updated the howto:
- Link broken, added an attachment of the file instead.
- Tested on Dapper: Works.

---

### Post by Perfect Storm on 2006-06-01
Change the howto 6.06.
But it also works for all other Ubuntu releases.

---

### Post by satanislav on 2011-03-26
Ubuntu 10.10: file /home/<username>/.config/user-dirs.dirs needs to be edited. Make sure you have a line with something like XDG_TEMPLATES_DIR="$HOME/Templates".

---

