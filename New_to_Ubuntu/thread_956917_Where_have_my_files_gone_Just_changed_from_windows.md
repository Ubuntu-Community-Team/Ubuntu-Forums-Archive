---
title: "Where have my files gone? Just changed from windows to ubuntu"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by matt-lisa on 2008-10-23
I have just changed over from winXP and before doing this I copied all my wanted files (docs, pics, music, everything) over to a different HDD (as actual files not backups or an ISO file), disconnected it , installed ubuntu onto a new drive (which is now the main system drive), then reconnected the second drive (now labeled as new volume). I went to start looking for files on the second drive to retrieve all my files and some of them are not showing in the new volume. yet when I check the properties of the new volume it has the same amount of space used as before the install. (hope I'm making sense) basically the files are there on the drive but I cant access them (they aren't showing when I open the new volume)

have a feeling it is because the drive is formatted as NTSC before the install was done. Can somebody help?

---

### Post by cariboo on 2008-10-23
Are you trying  to access the drive from Windows or Ubuntu? If you were running Ubuntu I would ask if you have permission to  access the drive. It may be the same problem in Windows.

Jim

---

### Post by matt-lisa on 2008-10-23
from ubuntu. Did a clean install of ubuntu

---

### Post by matt-lisa on 2008-10-23
also i meant ntfs, not ntsc (must have been thinking of the new telly we are getting this week...lol)

---

### Post by pastalavista on 2008-10-23
have you tried control-h to show hidden files?.. also, you might try ntfs-config
```
sudo apt-get install ntfs-config
```

---

### Post by matt-lisa on 2008-10-23
when you say control H, do I do that in the drive window? also Ive noticed ona few of the forums about the "code" things (sorry I'm an absoloute newbie at ubuntu) how do I use them?

---

### Post by PhoenixP3K on 2008-10-23
The shortcut Ctrl+H simply shows hidden files. That option is in the "file browser" window under the View menu. In Ubuntu hidden files are identified as file names or folders that start with a . (dot).

Now Ubuntu is supposed to be able to mount NTFS drives with ease. 
However, you said you copied the files you had from Windows to a second disk? Right?

Because lets say you had files under Windows XP in your Matt user account, it's possible those files had special permissions to allow only Matt to access those files (lets say to make sure Lisa couldn't go snoop in your files).
Now Windows can set those permissions on any file in an NTFS partition, it is possible that if those files where set to be readable only by a certain user that Ubuntu is unable to even see them, but they would still take space on the hard drive.

That would explain your problem in my opinion, but if you just copied the files to a 2nd drive usually Windows doesn't retain the restrictive permission (usually it's set to your user Folder in Windows). Or did you copy the directory itself?

Still I'm not coming up with a solution for you but the least I can do is provide information that might help others out. 

Often people will refer to "command line" enclosed inside CODE box in the forums. Those usually represent things to type in a terminal window.

Applications > Accessories > Terminal

[IMG]http://www.roominside.com/usbadslmodem/term.png[/IMG]

It's a quick [text based] way to perform simple and complex operations in Ubuntu that would otherwise require many steps to complete with the mouse and keyboard.

---

### Post by pastalavista on 2008-10-23
In the Ubuntu file browser (Nautilus) when you are viewing a folder, just press ctrl-h (key combo) to toggle between show/hide hidden files (&folders).. the "code thingy" is the "terminal" where you enter DOS-like commands (Applications>Accessories>Terminal). I added it to my panel... (right-click/add to panel).. because I use it a lot.

Read [this post]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by matt-lisa on 2008-10-23
Thanks alot every one. Think I'll have to play around and see what comes up.
Matt

---

### Post by Miljet on 2008-10-23
I am assuming from your original post that you can see some, but not all, of your files. The first thing that comes to my mind is do the filenames that you aren't able to see contain spaces. I don't know if it has anything to do with your problem, but it is quite common to include spaces in file names under Windows but Linux doesn't like spaces in file names. Maybe someone more knowledgeable than I can comment.

---

