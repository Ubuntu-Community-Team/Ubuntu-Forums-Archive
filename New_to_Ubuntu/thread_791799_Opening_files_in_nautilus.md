---
title: "Opening files in nautilus"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-12
I'm trying to tailor nautilus to use my commandline to open a file with the extension of .RSS. I've been using that extension on windows for years. It contains data for my R...SlideShow program.

I have set up a script (in ~/.local/share/applications) to open the file with my commmandline.  I have several scripts there that are working.

In nautilus:
 if I RC on a .RSS file, select Open with Other Application ... and select "Slide show (RSS)", my program starts, reads the file and starts the slideshow.  IE the commandline is OK.
 if I RC on a .RSS file, select Properties, select the "Open With" tab, I see two entries. The "Slide show (RSS)" entry is selected (dot in circle). The other entry is for Firefox, which I can't remove. I would expect that the selection means that "Slide show (RSS)" would be the default.
 The RC menu shows "Open" as the first choice. For other extensions that I've tailored entries for, the first entry shows the name that I gave to my commandline.

  if I double click on the .RSS file, nothing happens???

How can I change how nautilus to use my commandline as the default?

Thanks,
Norm

---

### Post by NormR2 on 2008-05-17
Why is it that in nautilus when I double click on a file with extension of .html and Type= plain text document, some times the file is opened in gedit and sometimes NOTHING HAPPENS?

If the file is on a vfat(Windows) partition with owner=root and group=plugdev, it is NOT opened.
If the file is on a Ubuntu disk, the file is opened in Firefox.
The rightclick menus are different for these two files. One first just has "Open" at the top,
the second has "Open with Firefox" at the top.  Why the difference? 
Where are these setting saved?
How can I find them?

With the file on the Windows partition, if I RC and select "Open the other Application" and then select "Firefox" it opens ok.

The Properties|"Open With" tab for the .html file on the Windows partition show Firefox as the default. 


Where are the Properties|"Notes" tab data written? 
Are the notes only associated with that single file? And not with all files with the same extension and Type?

---

### Post by chewearn on 2008-05-19
First, I have rudimentary knowledge in this area.  I reply to you question to give you a clue on where to look, but I'm not familiar with the details myself.

The gnome desktop take care of file association not by file extension alone, but by examining the file content to determine the mime type.  Here is a page explaining it:
[http://developer.gnome.org/doc/whitepapers/SystemConfig/mime-info.html](http://developer.gnome.org/doc/whitepapers/SystemConfig/mime-info.html)

.

---

### Post by NormR2 on 2008-05-19
Thanks for the response. 
I looked at the page you give the link to and it looks very interesting. However, I can only find a few files on my system that appear to follow the scheme described. Several of the folders refered to do NOT exist on my system.
I've added several items to my rightclick and none of them are shown or created changes in the files or folders described.
:confused:

---

