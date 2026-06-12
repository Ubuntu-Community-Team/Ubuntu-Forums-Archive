---
title: "Making GUI to cmd?"
date: 2005-05-05
forum: Programming Talk
---

### Post by D4_B34M on 2005-05-05
Ok, I only have programmed 2 years on Windows with Visual C++, Visual Basic and Delphi, also after changing to Linux I tried Perl and Python.

Now... I want to do a GUI for an command line program (file transfer client), i dont need much functions, only simple things like directory listing in xml like:

<?xml version="1.0"?>
<!DOCTYPE folder-listing SYSTEM "listing.dtd"
<folder-listing version="1.0">
    <parent-folder />
    <file name="file.mp3" size="5123730" modified="20050427T165058" user-perm="RWD"/>
</folder-listing>


It has to be converted to a list where i can browse the directories, then also a file selector object.

I dont have any idea where to start making this...
So what should i try first? Is there any good visual programming tool (i dont like to make GUIs typing  :wink: )
I dont mind of the language (im fast to learn new ones) but... Easiest first...
And... The app is going to be for my self only on couple computers and im not going to publish it, so i only need to get it to work on ubuntu.

---

### Post by Burgundavia on 2005-05-05
Python and pygtk are your friend.

Corey

---

### Post by D4_B34M on 2005-05-05
[QUOTE=Burgundavia]Python and pygtk are your friend.

Corey[/QUOTE]


They are now, :)

Thanks, this seems to be very easy to use.

---

