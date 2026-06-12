---
title: "Copy to"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by mijdrawoh on 2011-10-01
Despite research, I have not found a definitive answer on copying a single file to a directory on a separate HDD. I've tried cp source destination without success. Is there a simpler way than copy-paste?

---

### Post by MartyBuntu on 2011-10-01
copy/paste works if you have write permission on the destination drive.
Did you research that?

---

### Post by coffeecat on 2011-10-01
> **mijdrawoh said:**
>  I've tried cp source destination without success. 

What was the exact syntax of the command you used, and what error did you get? There should be no problem copying a single file to an external hard drive, so long as it is mounted and you have appropriate permissions as MartyBuntu points out.

Sorry to ask the obvious question, but have you tried drag and drop in the GUI?

---

### Post by mijdrawoh on 2011-10-01
I can cut/paste and drag/drop without a problem.  I am looking for a simpler way. For example, in KDE you can right click on any file and Copy To any directory on your computer.  I am hoping to find a similar capability on 11.04.

---

### Post by coffeecat on 2011-10-01
When you said...

> **mijdrawoh said:**
> I've tried cp source destination without success. 

... it sounded as thought you were using the "cp" command in the terminal. I'm not aware of any other way than you've already found in 11.04. KDE tends to have a few more features than gnome. I don't know whether there is a nautilus extension or script you could install. Someone else might know.

---

### Post by QLee on 2011-10-02
[QUOTE=mijdrawoh]For example, in KDE you can right click on any file and Copy To any directory on your computer.  I am hoping to find a similar capability on 11.04.[/QUOTE]
Sorry to be so late in seeing this, will write this anyway in case it might help.

I guess you are referring to the feature in Konqueror that allows you to browse to a location for the copy.

It is possible to run Konqueror on a non-KDE installation of Ubuntu. It will pull in some dependencies but unless you are short of disc space that might be one way to have the feature you want.

---

### Post by realzippy on 2011-10-02
> **QLee said:**
> 
I guess you are referring to the feature in Konqueror 

...you mean dolphin,not konquerer? (which now is called rekonq)

---

### Post by carranty on 2011-10-02
> **mijdrawoh said:**
> Is there a simpler way than copy-paste?

Surely drag and drop ***is*** the simplest way.  left click on the file you want to copy, hold the control key and drag it where ever you like.  Even in KDE you still have to navigate to the source/destination directories??

Or if you're a quick typist use the cp terminal command.

Either method takes seconds, and is very simple.

---

### Post by F.G. on 2011-10-02
um, i think you can use ctr+c and ctr+v like you are copying and pasting text.
that might be easier?

---

### Post by QLee on 2011-10-02
> **realzippy said:**
> ...you mean dolphin,not konquerer? (which now is called rekonq)
That could well be, I haven't used a KDE desktop in a couple of years, haven't kept up. However, I do have a standalone copy of Konqueror on a 10.04LTS GNOME install and it is still called Konqueror and it has the detailed feature. 

If you are a current KDE user, then you would know better than me.

[edit:] Realzippy, if the Dolphin filemanager has the feature that the OP is looking for (browse to a location for a "copy to") would you recommend it instead of Kong (which seems to now be used mostly as a web browser in KDE)? The OP wants that in the right click context menu of the file manager used. I don't think the poster is having trouble copying & pasting, just wants that aspect of the GUI.

---

### Post by mcduck on 2011-10-02
> **carranty said:**
> Surely drag and drop ***is*** the simplest way.  left click on the file you want to copy, hold the control key and drag it where ever you like.  Even in KDE you still have to navigate to the source/destination directories??

Or if you're a quick typist use the cp terminal command.

Either method takes seconds, and is very simple.

Since the question is about copying to another drive there's no need to hold down Ctrl. Drag & dropping between different file systems always defaults to copying instead of moving.

Also you can drag & drop with middle mouse button, which gives you a popup asking if you want to copy, move or link the file.

---

