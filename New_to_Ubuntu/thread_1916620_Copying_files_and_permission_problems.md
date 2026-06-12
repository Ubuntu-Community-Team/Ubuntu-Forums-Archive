---
title: "Copying files and permission problems"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by zcacogp on 2012-01-28
Hello, 

Posting in Absolute Beginner Talk as I am really struggling with what should be a simple thing ... 

I've just downloaded a PDF file (my wife's tax return), and am trying to save it. It won't let me save it directly into a mounted volume locally, but will let me save it to the desktop. 

I can open it fine from the desktop, and also copy it to the mounted volume locally. However I can't then open the copied copy ... 

I have tried running as root (typing 'sudo nautilus' from the terminal and finding the file from there), but that doesn't let me open it either - telling me "Cannot parse arguments: Cannot open display:". The permissions on the file are as follows; 

```
-rwxrwxrwx 1 ogp ogp 778004 2012-01-28 17:14 viewTaxReturnPdf
```

(I changed them from the command line, and by my reckoning that should allow pretty much anyone to open it, but no joy, even when trying to open as root.) 

I have tried copying the file directly from the 'Downloads' folder (of firefox) and that made no difference. 

What am I doing wrong? (I know i have had problems with this sort of thing before - with the tax return from last year, for instance - but can't remember what I did to solve them.) 

Thanks, in advance, for any help. 


Oli.

---

### Post by mcduck on 2012-01-28
What kind of filesystem (and drive/media) is the mounted volume you are talking about?

---

### Post by zcacogp on 2012-01-28
mcduck, 

Thanks. It's a locally mounted partition, formatted as EXT4. 

It's mounted under /media, and the folder I am trying to copy it into is /media/Ianthe/Financial/Tax10-11 - Ianthe is the name of the partition. It is mounted with fstab when the machine boots up. 


Oli.

---

### Post by ajgreeny on 2012-01-28
You will need to change the ownership of the volume (partition/disk) mount folder with command ```
sudo chown *-R user:user* /media/*mountpoint*
```change *user:user* to the username you want to own the folder (you or your wife) and /media/*mountpoint* to whatever the folder name is.  If there is nothing in the folder /media/Ianthe yet, you can forget the -R option of the command, but it will do no harm if you use it.

---

### Post by zcacogp on 2012-01-28
ajgreeny, 

Thanks. 

That sounds a bit drastic; how do I find out who currently owns the folder (I'd be surprised if it wasn't me)? 

If the problem is with the ownership of the folder (and possibly starting some way further up the directory tree) then why do the other files apparently work fine? 


Oli.

---

### Post by mcduck on 2012-01-28
OK, what are the permissions of the directory where you are trying to copy the file to?

You'll need to have execute permission on the directory to be able to open files inside it, and read permission to be able to list the files.

...I also noticed that at least based on your ls output, the file doesn't have the file name extension (.pdf). While Linux in general doesn't care about such things, it can still confuse some programs so you might want to add it to the filename.

What comes to the error you got when you tried to open the file as root ("Cannot open display"), that sounds like you tried to do it from a TTY instead of your desktop. Graphical applications need a graphical environment to run, without one you'll get this error.

---

### Post by zcacogp on 2012-01-28
MCduck, 

Crumbs, I am impressed! Thank you very much - you spotted the problem and have solved it! You were right - there was no file extension on the file name (it's a PDF), and adding .pdf to the end made it open just fine!

Two odd things occur to me; 

1. Without the extension it still lists in Nautilus as being of 'type - PDF document'. So the machine recognises it as being a PDF, but apparently can't call the correct viewer. Why is this? 

2. With the document on the desktop, even without the .pdf extension, it will still open. It appears that moving it to the filestore causes it to lose the ability to open it. 

So the problem is solved - thank you. But it has raised some more questions, which I don't understand. 

Thank you again mcduck. 


Oli.

---

### Post by mcduck on 2012-01-28
It's indeed a bit of a mess sometimes. Linux itself detects file types based on [magic numbers]("http://en.wikipedia.org/wiki/File_format#Magic_number"), the actual content of the file. But many of the programs and even some mechanisms the desktop environments use depend on file name extensions.

I'd assume that the mechanism Nautilus uses to detect a file's type would be different from the one it uses to decide which program to open a file with. Sounds strange, though, but I can't think of any other reason why it would show you the correct file type but not be able to pick a program to open the file with. Anyway, you can get even stranger results if you have a file that has a extension indicating a completely different file type than what the file's contents are... ;)

If you want better answer, I suppose you'll have to ask the developers. :D

---

### Post by zcacogp on 2012-01-29
mcduck, 

Where do the developers hang out? Do they appear on this forum? 

(More out of curiosity than anything else, of course!) 


Oli.

---

### Post by mcduck on 2012-01-29
> **zcacogp said:**
> mcduck, 

Where do the developers hang out? Do they appear on this forum? 

(More out of curiosity than anything else, of course!) 


Oli.

Very rarely, if ever. I'd bet they are too busy working to have much time to hang around on web forums... ;)

They do sometimes answer questions on [askubuntu.com]("http://askubuntu.com/"), although it might take quite long time to get an answer. I'd assume most of the discussion is handled through [mailing lists]("https://lists.ubuntu.com/") and IRC.

Bug reports in Launcpad are usually the best way to get in contact with the devs, but of course that would only apply to actual bugs. And this isn't really even an Ubuntu-related question, you'd have to ask Nautilus or Gnome developers (I honestly have no idea how to get in any contact with them...)

---

### Post by zcacogp on 2012-01-29
Interesting. They are clearly busy people ... I'd hate to disturb them from their important work! 

Thanks again for your help. 


Oli.

---

