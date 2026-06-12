---
title: "copy file to usb flash drive"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by kaykav on 2008-10-23
Good afternoon,
                    I plug in the flash drive into a usb port, then check if drive is noticed, it is, then I open command line to type 
  ~$ sudo cp Documents/file#1 /media/USB_DISK , then prompt for my password.
    My home prompt comes back (~$), only to find nothing has been copied.
         I dragged the file to the usb disk and all is well. I must not be typing the correct command.  Please help...Rich
                  p.s.   where can I find how to do this without the forum?

---

### Post by bangmalley on 2008-10-23
i think u wanted to copy this
/home/*user*/Documents/file#1

the command should be
```
cp ~/Documents/file#1 /media/USB_DISK
```

you don't need sudo for your home folder

---

### Post by prematurebaby on 2008-10-23
sudo not nessesary and you have to start with /home/{user}/ or ~/ thats why it didn't work.

---

### Post by kaykav on 2008-10-24
Well I tried to copy, to no avail. There must be something I don't know about. Ques is : how do I copy a file from Documents to a thumb drive?
                               Thanks...Rich

---

### Post by frankleeee on 2008-10-24
> **kaykav said:**
> Well I tried to copy, to no avail. There must be something I don't know about. Ques is : how do I copy a file from Documents to a thumb drive?
                               Thanks...Rich

If your just trying to move a file from documents to the thumb drive drag and drop or copy and paste.

---

### Post by kaykav on 2008-10-24
thank you...rich

---

### Post by jerome1232 on 2008-10-24
I for one don't know what you guys are talking about, it doesn't need to be lead by a ~/ or by /home/user/...

When you pop open a terminal it IS in you home, so that command should have copied correctly. 


Go ahead try it, it'll work
```
~$ ls /media/disk
resume.doc  resume.odt
~$ cp Documents/text.file /media/disk
~$ ls /media/disk
resume.doc  resume.odt  text.file
```

I think /media/USB_DISK didn't exist and instead of copying to your drive, you copied it to /media and renamed the file as USB_DISK. That's just my guess.

The file got copied somewhere if it came back to your bash prompt without printing an error.

---

### Post by kaykav on 2008-10-25
Jerome1232,
                 I removed all traces of USB DISK from home folder, then I typed the following:


             kaykav@dittydiner2:~$ cp save\ this /media/USB\ DISK
             
           All is well
          Maybe the syntax of my command was the problem. I hope it doesn't come back to haunt me. Thank you for a lend of your knowledge.  Rich

---

### Post by kaykav on 2008-10-27
Good morning,
Well people I got it to invoke my command. I m running ubuntu 8.04
(hardy heron).
The problem was my syntax. When I type : cp save\ this /media/USB_DISK
I got the error message 'cannot create regular file', and consequently couldn't copy
the file. But when I type: cp save\ this /media/USB\ DISK, it copied.!
Note the 'back slash' after USB . If I put the device name in quotes, single or
double, it also works. Its when I use the under_score character ,that it does not
work. Im not sure why. Anybody?..Thank you all for your knowledgable help....
Rich

---

### Post by jerome1232 on 2008-10-27
USB\ DISK = USB DISK
USB_DISK = USB_DISK
"USB DISK" = USB DISK

Which one is the mount point? I'm guessing one is throwing an error because it trying to copy it to /media which you don't have permission to create files in and rename the copy to USB_DISK. The  other command is copying the file into the folder "USB DISK" which you do have write permissions to.

---

### Post by kaykav on 2008-10-27
jerome1232,
                Thanks for that info. Why dont I have permissions
                     to create a file in /media? I thought root could do anything.    Rich

---

### Post by jerome1232 on 2008-10-27
If you are running as root then yeah it would work.

---

