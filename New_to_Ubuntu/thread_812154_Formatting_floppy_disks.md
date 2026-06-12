---
title: "Formatting floppy disks"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Ludwig9 on 2008-05-29
I am in Hardy and have installed kfloppy, but cannot copy anything with it to floppy disks. When formatting floppy disks with kfloppy what file system should one use: Ext2 or Minix? I assume one should not use DOS. 
I have successfully (I think) formatted a 3.5 floppy in Ext2, but my computer refuses to open the floppy disk saying that there was "an invalid mount option when attempting to mount the volume KDE floppy." And later:
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
The floppy disk is not write-protected. What is the best way to copy a data file to a 3.5" floppy? I have tried to copy the file, then open the floppy, and then paste the file into the floppy. I believe I have done it that way before with Ubuntu, but today it will not work.

---

### Post by kwacka on 2008-05-29
Its been a while since I used floppies, but IIRC

To format use ```
sudo mkfs -t ext2 -c /dev/fd0H1440
```

You'll probably need to:```
 sudo mkdir /media/floppy
```

To mount use:```
    sudo mount -t ext2 /dev/fd0 /media/floppy
```

I'll be quite happy to get slapped down about this.

Another alternative might be to use mtools (you'll probably need to install this package)

---

### Post by Ludwig9 on 2008-05-30
After the first command (sudo mkfs -t ext2 -c /dev/fd0H1440) I received the following response:
> sudo mkfs -t ext2 -c /dev/fd0H1440
[sudo] password for george: 
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/fd0H1440 --- No such file or directory

The device apparently does not exist; did you specify it correctly?


---

### Post by Ludwig9 on 2008-05-30
I would also like to know what file system one should use when formatting floppy disks for Open Office in Ubuntu: DOS, Ext2 or Minix. 

And how does one install mtools?

What does "but IIRC" mean? That I should use IRC in seeking info?

---

### Post by plucky on 2008-05-30
IIRC= If I Remember Correctly


To format ```
mkfs -t ext2  /dev/fd0
```


Then mount it as **kwacka** said.


Good Luck

---

### Post by chrisccoulson on 2008-05-30
gfloppy is installed by default in Hardy. It's hidden in the System Tools menu though. You can show it by checking it in Alacarte

---

### Post by Ludwig9 on 2008-05-30
> **plucky said:**
> IIRC= If I Remember Correctly


To format ```
mkfs -t ext2  /dev/fd0
```


Then mount it as **kwacka** said.


Good Luck
I gave it your command and it seemed to work. But when I gave it the command:  sudo mkdir /media/floppy, I received this response: 
> mkdir: cannot create directory `/media/floppy': File exists

Should I now proceed to write kwacka's next command: sudo mount -t ext2 /dev/fd0 /media/floppy

---

### Post by Duck2006 on 2008-05-30
> Should I now proceed to write kwacka's next command: sudo mount -t ext2 /dev/fd0 /media/floppy

Yes

---

### Post by Ludwig9 on 2008-05-30
> **chrisccoulson said:**
> gfloppy is installed by default in Hardy. It's hidden in the System Tools menu though. You can show it by checking it in Alacarte
Applications/System Tools produces no menu on my machine. When I click on System Tools a small window appears which says: HPLJ 10xx Replaced Paper.
That is, HP laser jet ten times replaced paper!

I have not heard of Alacarte! Where is it?

---

### Post by chrisccoulson on 2008-05-30
Right click on the Applications menu and click 'Edit Menus'. This will open Alacarte.

---

### Post by Ludwig9 on 2008-05-30
> **Ludwig9 said:**
> I would also like to know what file system one should use when formatting floppy disks for Open Office in Ubuntu: DOS, Ext2 or Minix. 

And how does one install mtools?

Well I installed mtools using synaptic, but I would still like an answer from someone about what to do in formatting floppies for Ubuntu. Are all 3 file systems compatible with Ubuntu? Or what? Thanks to all!

---

### Post by Duck2006 on 2008-05-30
This may help.

[http://ubuntuforums.org/showthread.php?t=522094](http://ubuntuforums.org/showthread.php?t=522094)

---

### Post by Ludwig9 on 2008-05-30
> **chrisccoulson said:**
> Right click on the Applications menu and click 'Edit Menus'. This will open Alacarte.
I clicked on Edit Menus and that opened up a 2-sided window, one side with Menus, the other with Items. One of the menus was System Tools, I clicked on it, then checked "Floppy Formatter," then clicked Close. I now find Floppy Formatter in the System Tools menu under Applications, but I never saw "Alacarte." In any case, I now evidently have the GFloppy Formatter. But please tell me about what the file systems. With this formatter there are only 2 choices, DOS and Ext2. Are both compatible with .odt files?

---

### Post by Duck2006 on 2008-05-30
> With this formatter there are only 2 choices, DOS and Ext2. Are both compatible with .odt files?

Yes, Dos would be Fat16 or Fat32 witch linux will read and write to, and ext2 in linux file system.

---

### Post by Ludwig9 on 2008-05-30
> **Duck2006 said:**
> Yes, Dos would be Fat16 or Fat32 witch linux will read and write to, and ext2 in linux file system.
I have successfully formated at least one floppy in est2, but still have difficulty copy files to floppies and I received the following message when trying to format one floppy:

> The filesystem creation utility (/sbin/mke2fs) reported the following errors:

/dev/fd0 is mounted; will not make a filesystem here!
 (54)

---

