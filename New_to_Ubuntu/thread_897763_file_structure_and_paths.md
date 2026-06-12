---
title: "file structure and paths"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by echeddar on 2008-08-22
I seem to have a lot of problems navigating my drive in Linux.  I have installed Ubuntu on half my drive, surf the web a bit on it, and even mounted my NTFS half or my drive so I could import my music to rhythmbox.  But when I need to indicate a location, I don't know how.  For example, I recently used Synaptic to install acidrip so I could copy a DVD to my hard drive.  When it starts, there is a space where it asks for the path to the DVD.  It defaults to "/dev/dvd", but says that there is no file there.  If I insert the DVD into the computer, Ubuntu detects it and launches the movie in Totem, so it must be mounted or whatever.

I can use the places menu to bring up the file browser, but I don't really know where the folder I'm looking at is located.  There is a Location Bar i the file browser, but that doesn't seem to really indicate the actual path to the files.  With the DVD issue, I could navigate to the DVD, then click the up-arrow in the browser to see the folder from the outside, then drag that folder to the path field in acidrip.  By that method, the path to my DVD drive is: "file:///media/cdrom1", but that didn't work, either.

I had a similar problem just navigating in the command-line terminal.  If I type in ls, I get a list of folders like music, documents, pictures, etc.  But if i try to cd to one of those locations, I get an error.  

Can anyone point me to a nice tutorial about the Ubuntu file structure and  how to navigate basic file management?

Thanks in advance!

echeddar

---

### Post by mr.moch on 2008-08-22
for the location bar, it should be /mebia/cdrom1.  no need for file:///.  That's only if you're using Firefox for some reason.  The default drive seems to be wrong, but I'm not positive.

For the file structure, I really don't know it much myself, either.  But we'll find out some day!

---

### Post by Too Late on 2008-08-22
> **echeddar said:**
> I had a similar problem just navigating in the command-line terminal.  If I type in ls, I get a list of folders like music, documents, pictures, etc.  But if i try to cd to one of those locations, I get an error.
Linux is case sensitive! So "music" is not the same as "Music".

In Nautilus (file browser) press Ctrl+L (or go to Go -> Location...) to see the full path.

---

### Post by elmoosecapitan on 2008-08-22
Linux is utmost sensitive to case and to some extent spacing. Linux file path construction is different from Windows in the sense that for windows, everything is defined with respect to the different storage media, i.e., C:\\, D:\\, A:\\, (does anyone know what B:\\ is for?); linux on the other hand is entirely within your main drive and drives position with respect to the main drive, i.e., / , /home/username, /media/cdrom0/, /media/flashdrivename/, etc...

After a while you get the hang of it and become completely fluent with the directory structure.

In terms of tutorials: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

It is mostly a tutorial about commands, but you get the feeling for structure and plus there are additional tutorials (including linuxcommands.org) at the bottom of the page.

---

### Post by coffeecat on 2008-08-22
> **elmoosecapitan said:**
> does anyone know what B:\\ is for?

Ah! (Sighs nostalgically.)

Funny you should ask that. Have a look at my second post (#4 in the thread) [in this thread]("http://ubuntuforums.org/showthread.php?t=897611").

---

### Post by echeddar on 2008-09-01
That was it, Mr. Moch!  I at least got it to find and recognize the media.  I'll let you know how the rest comes out.

---

### Post by echeddar on 2008-09-04
/media/cdrom1 worked like a charm, thanks!

I'll be checking out the file structure info tonight.  Thanks again for all the help!

---

