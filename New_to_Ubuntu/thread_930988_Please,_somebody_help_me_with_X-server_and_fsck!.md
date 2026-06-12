---
title: "Please, somebody help me with X-server and fsck!"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by jorgecarrillo150990 on 2008-09-26
Look, I have posted the message in every forum that I think can solve it, but I only get views, not replies. So please Im begging you to help me because I can't use my laptop due to this two problems.

Some useful data about my Laptop.
Uses Hardy Heron.
Nvidia Videocard
Drive with the fsck problem is "sda5"

Now that I have given a small intro about my problem, I am going to explain what happened (even with picture!)

I have been having one of this problems for a while, and let me explain it to you. I run Hardy. You know how at 34 number of times you start Ubuntu, an automatic fsck is made.
I usually press Esc, because I am in a hurry, but one time when I left Ubuntu do the fsck an error happened and I was sent to the terminal.  The first pic included is regarding this problem.
[IMG]http://i73.photobucket.com/albums/i222/MexAlbum/100_1115.jpg[/IMG]

One curious thing that happened is that the first time it failed to do the fsck it had 95% progress, today it just had 5% and BAM! to the terminal.

I can live with this problem, because I usually skip the fsck process. But there is the new problem, and the one that I think is the worst, becuase I can't handle it.

I do the usual skipping of the fsck and go to the GDM. Log in and wait to my desktop to charge. Today I did the same thing until I thought I had been waiting for a long time and my desktop didn't appear. I did the Ctrl+Alt+Backspace to go back to the GDM and a blue screen appears saying that:

THE X SERVER COULDN'T BE STARTED DUE TO AN INTERNAL ERROR, THAT I SHOULD CONTACT THE ADMINISTRATOR AND WAIT FOR A DIAGNOSIS.
AT THE END IT SAYS THAT MEANWHILE THE SCREEN WILL BE DEACTIVATED AND THAT I SHOULD RESTART THE GDM WHEN THE PROBLEM IS SOLVED. 
[IMG]http://i73.photobucket.com/albums/i222/MexAlbum/100_1117.jpg[/IMG]

But the problem is that I don't know what went wrong, it doesn't give any details. So im counting on you to help me.

Please, treat me as a noob and give me step-by-step directions for how to solve this two problems...please:(

---

### Post by jorgecarrillo150990 on 2008-09-26
COME ON!!! I have asked the question all day long in all the forums and I dont get any responses!!!!!

---

### Post by starcannon on 2008-09-26
on the first screen, press Ctrl-D

on the second screen, after it dumps you to a shell type:
```
cp /etc/X11/xorg.conf ~/xorg.bak
```

Then try:
```
sudo rm /etc/X11/xorg.conf
sudo dpk-reconfigure -phigh  xserver-xorg
sudo /etc/init.d/gdm start

```

if all went well you should have a gui to start working in again, we'll then start collecting information to troubleshoot and get things back to a more optimal situation.

GL

---

### Post by Tatty on 2008-09-26
Well it sounds as though your hard drive may be failing on you.  The data on your drive is slowly being corrupted for some reason which is what has been causing the fsck errors to appear.

Now that part of your X server appears to be corrupted I think it is probable that you will have to re-install to get ubuntu working again.  You could try to re-install individual components bit by bit, however as it appears that there is corruption all over your hard drive, it could get very time consuming to fix all the errors, easiest to just re-install

However, the larger issue is your hard drive itself.  Its probable from your description that you need to buy a new hard drive, as it sounds like a hardware problem.

I assume you always shut down the computer cleanly before turning the power off?  If so then its probably a hardware issue.

You may want to try completing that fsck.  It suggests on the error message in the first pic to run fsck manually -try that.

---

### Post by Kellemora on 2008-09-26
Hi JC

I got something similar on the XP portion of a drive only last week that I tried gparted on to partition it.
Said I had 8 bad blocks!
Ran chkdisk /f on it, found no errors, but gparted said it had 105 bad blocks now.
Did it again and it came back with 149 bad blocks.
XP was working perfectly with no data loss and nothing with windows found any errors at all.

I needed this drive for a clean install of Ubuntu too!

I finally deleted Windoze, reformatted the drive, it found NO bad blocks or Sectors at all.
Played around with gparted and qtparted both, made partitions, moved them around, resized them, all worked great, until I reinstalled Windoze XP again.  Then I was back to square one all over again with 119 bad blocks and file inconsistencies.

Wiped XP again and now just have Ubuntu and Debian on there.

I've heard of this before too and found messages about it too last week when I was having the problems myself.  Seems related to Doze.

If you don't have the Doze on your computer, perhaps the hard drive is going south.  They don't make them to hold up very long like they used to.  A couple of years is all these new hard drives last, if that.  The old ones, well, I've got some with Doze 95 on them and they have NO errors.

TTUL
Gary

---

