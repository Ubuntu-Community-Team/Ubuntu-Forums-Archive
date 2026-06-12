---
title: "Accessing the Original Harddrive"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Darkshrimp on 2008-05-12
I have always wanted to install linux on my laptop. Up to now, I've never had much confidence with installing it. Because every time i see the lines of code in the terminal, i ask myself, why am I using linux is windows is working just fine...

Today, for no reason at all, the system file on windows crashed. By following the help steps on Microsoft site lead me delete all my system files without replacing it.. (i'm sure that's partly due to my inexperience with cmd lines, but there the files Microsoft telling me i had i just didn't have)..

Anyway, after my long life story.

**I've decided, forget about this, lets just use linux...but got one problem, is there anywa of installing ubuntu and accessing the my hard drive from before? Because I have a few very important files and some photos i don't want to lose. If that's possible, then everything would be perfect :)**

Anyone can help me? or is it simply not possible?'

Thank you all

---

### Post by sjprice on 2008-05-12
I would download the Ubuntu Live CD on another PC, burn it, boot your laptop from the CD, put in a USB key and you will be able to transfer off the files you want to keep.

Then slap Ubuntu on there and never look back.

---

### Post by bryncoles on 2008-05-12
oooh - i think i know the answer to this one! 

if you download the ubuntu 8:4 iso file from the homepage, and burn it to cd, you'll create a 'live cd'. put this in your cd drive and boot your computer (assuming the boot sequence is set to cd first). it'll load from cd entirely, this is known as the 'live session'. from here you can accesss all files on your hard drive, play with everything and you should be fine. 

i managed to install ubuntu on a partition - which the cd walks you through doing - which would allow you to install ubuntu without losing data (though its a good idea to back stuff up first anyway, obviously. 

so the short version - is if you can, boot from the ubuntu cd. you can access the windows drives, as ubuntu can read fat32 and ntfs (windows formats). move all your stuff onto an external hard drive if you can, and welcome to ubuntu!

---

### Post by Darkshrimp on 2008-05-12
i currently have a ubuntu 5.10 live CD at my disposal, can that read the drives too, or do i have to get the latest one?

oh and is there any special thing i gota do to get the drives?

---

### Post by sjprice on 2008-05-12
That Live CD will be able to get you up and running to get your important files. But I would try and get the 7.10 or 8.04 CD for installation.

The Live CD should be able to see your harddrive without doing anything special.

---

### Post by Darkshrimp on 2008-05-12
i've been looking around on the net and they say i have to mount it

so i'm in terminal, using mount /dev/hda1 /home/ubuntu/Desktop/drivec 
command
but it keeps on telling me:

mount: only root can do that

but aren't I root already :S

---

### Post by H.Callahan on 2008-05-12
Make that:

```
sudo mount /dev/hda1 /home/ubuntu/Desktop/drivec
```

The "sudo" gives you temporary root access.

...and no, you are not root, unless you make yourself the root.  In Ubuntu, that is generally done via "sudo" (short for **S**uper **U**ser **DO**) to temporarily grant root access for the duration of the process.  Permanently making yourself root is a bit of a no-no.

---

### Post by logos34 on 2008-05-12
you have to do everything manually with the older ubuntu live cds so if the above doesn't work try this:

sudo mkdir /mnt/windows

sudo mount -t ntfs /dev/hda1 /mnt/windows

---

### Post by logos34 on 2008-05-12
delete [duplicate]

---

### Post by Darkshrimp on 2008-05-13
more and more problems now :S

i mounted the drive

but when i try to open the folder, it says 

<code>The Folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "drivec" </code>

why :S

**[edit]Don't worry, i've got the latest ubuntu and it automounts drives :D so i'm just backing everything up now, thanks all**

---

