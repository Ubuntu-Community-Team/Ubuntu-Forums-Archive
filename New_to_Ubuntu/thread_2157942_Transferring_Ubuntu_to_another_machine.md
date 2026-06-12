---
title: "Transferring Ubuntu to another machine"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by wolfie52 on 2013-06-27
If this is for absolute beginners............I AM an absolute beginner. First things first.

I have two questions but deal with this first.

I run ubunto on a Dell net book, have done for around 4 years. Perfect.

Problem is net book is too small for my nimble fingers

I have aquired a desk top which is approx 4 years old and is aching with so much windows hardware and software. It barely runs. Previous owner assures me all files etc has been taken off.

I just want to wipe off this machine and install Ubuntu. Please, how to I do this, what information would you need to help me do this?

I am an ABSOLUTE beginner, but not an anorak / nerd or computer stalker.

Any help would be appreciated.

Geoff

---

### Post by snowpine on 2013-06-27
Hi Geoff!

Here are easy 1-2-3 instructions (with screenshots) to install Ubuntu on your desktop: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Choose which version you want and then click "Read the full installation instructions." :)

---

### Post by Kopkins on 2013-06-27
Once you install onto the desktop you can just take your files in /home and switch them over to the desktop. Or use ubuntuone backup to sync the files that way, just so you have all your documents.

Kopkins

---

### Post by Mark Phelps on 2013-06-27
Any machine that "barely runs" has serious problems, most likely hardware.  Ubuntu is not some kind of miracle cure that will turn a rundown PC into a powerhouse; instead, current releases need much the same hardware capability as do current Windows versions.

If you have installed any restricted drivers, especially video and/or sound, in the current Ubuntu install, it may not boot on the other PC.

There are a couple of steps you should consider:
1) Live USB -- make a LiveUSB of the Ubuntu version you want to "migrate", boot the desktop from that and see how well it performs.  IF there are any major problems, come back here with those before you make the move.
2) If there are no major problems, then use Clonezilla to image off the current Ubuntu setup to an external drive. Make a boot CD from Clonezilla, boot the desktop from it, connect up the external drive, and "restore" the saved image to that drive. This will allow you to keep using the current Dell to get technical help from the forums if the desktop won't network correctly.

---

### Post by snowpine on 2013-06-27
> **Mark Phelps said:**
> 
2) If there are no major problems, then use Clonezilla to image off the current Ubuntu setup to an external drive. Make a boot CD from Clonezilla, boot the desktop from it, connect up the external drive, and "restore" the saved image to that drive. This will allow you to keep using the current Dell to get technical help from the forums if the desktop won't network correctly.

OP hasn't provided enough details for me to be certain, but I *suspect* this method will not work unless the desktop has an Atom processor, and will result in an end-of-life system in any case. (Hence my recommendation to do a fresh install of a supported release following the official instructions.)

Geoff, you can confirm my suspicions by opening a Terminal and copy & pasting the output of this command:

```
uname -a
```

---

### Post by Mark Phelps on 2013-06-27
> **snowpine said:**
> ... and will result in an end-of-life system in any case...

You're right -- I skipped over the details that their current install is 4 years old -- my bad.

Never mind ...

---

### Post by mansonfan78 on 2013-06-27
> **Kopkins said:**
> Once you install onto the desktop you can just take your files in /home and switch them over to the desktop. Or use ubuntuone backup to sync the files that way, just so you have all your documents.

Kopkins

I would do this.  Just install the current release of Ubuntu (or current LTS release: 12.04) and use the same username and password during setup that you have on your existing computer.

---

### Post by wolfie52 on 2013-06-28
Thank you all of you for your excellent replies. I am digesting the responses and will act accordingingly. God that sounds very corporate somehow!!

Thank you.

I will be back.

I will be reading and fumbling whilst  watching and listening to both the Assen MotoGP and Glastonbury

Geoff.

---

### Post by wolfie52 on 2013-06-29
Have read in more detail your replies and really appreciate your responses. I will be looking to sort this this weekend. Thanks to SnowPipe, Mark Phelps and Mansonfan for your points. Kopkins too. I thought I had lost this thread when I came back looking for your notes but eventually found it. weird. 

I did have a second point. I will just leave this taster. Google Chrome upload and it mucks everything else up? 

Dont worry about the above my main concern at present is the first point. I am off to try to sort.

Thanks 

Geoff

---

### Post by wolfie52 on 2013-06-29
is this what you want, or have I got this hopelesley wrong? please dont laugh!!


Linux Inspiron 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686 i686 i386 GNU/Linux
geoff@Inspiron:~$

---

### Post by snowpine on 2013-06-29
Looks like you are running the fully-supported 12.04 LTS, so I think Mark's method would probably work, if you decide to go that route. :)

---

