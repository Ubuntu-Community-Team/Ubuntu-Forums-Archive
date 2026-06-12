---
title: "Hardy not updating"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by DeliriousNor on 2008-04-28
Hi! I installed Hardy on my computer on Friday, however I have not received a single update through the update manager. There has to be some updates after the final release. What could I do to fix this?

---

### Post by DezSP on 2008-04-28
AFAIK there haven't been any major updates yet (by which I mean updates to reguarly-used packages). No doubt some will come along before long. :)

---

### Post by dark_harmonics on 2008-04-28
Yea i noticed this too. Its probably that they just want to let the distribution updates happen before they start releasing more fixes for anything.

---

### Post by grannyw on 2008-04-28
dont worry people i guess there going to be enough updates,yet hardy has  enough to fix

---

### Post by DeliriousNor on 2008-04-29
Yeah, probably. But I thought there would be allot of updates the first days...

Hardy has some bugs, but it is working quite well for me:)

---

### Post by DeliriousNor on 2008-04-30
Still not any updates at all. Should I be more patient?:)

It's just that I have experience quite a few lock-ups lately..

---

### Post by mivo on 2008-04-30
Yes. :) There haven't been any updates yet. I only got a handful when I added the medibuntu repository, but that's normal. It's all well, nothing is broken. When Gutsy was released, there were no updates for a few days either.

---

### Post by DukeNuke2 on 2008-04-30
there are some bad hangups when i copy lots of files... the whole system slows down realy badly... so, let's hope for some updates soon!

---

### Post by mivo on 2008-04-30
Oh, and by "nothing is broken" I meant that there haven't been any updates yet, so not getting any isn't an error. I didn't mean that there aren't issues that some systems/users experience with Hardy. :)

---

### Post by Mad_Max_1412 on 2008-05-04
Guys,

If I open "Update Manager" and click "Check", I don't get any indication like I usually did where it says "Downloading 23 of 55" (for example)

All that happens now is I get the round rotating icon but nothing happens.  Even if I try to close the window by clicking on the cross in the top right corner, or by right clicking the menu bar and choosing "Close" it still stays open.

The only way to kill it is to re-boot (unless someone can tell me another method) :-)

BTW, just as I was about to click "Post" my top toolbar is now showing that there are updates, and when I hover over it, it says there are 2 updates available.  Unfortunately the Update Manager is still "stuck".

Cheers

---

### Post by forestpixie on 2008-05-04
Try using the terminal 

```
sudo apt-get update &&sudo apt-get upgrade
```

---

### Post by Mad_Max_1412 on 2008-05-04
I end up with

max@ubuntu:~$ sudo apt-get update &&sudo apt-get upgrade
sudo: unable to resolve host ubuntu


Also, after my reboot, I clicked on the notification icon about the updates.  It showed me what the two updates were, but I've clicked on "Update" and after 30 minutes or so it still hasn't downloaded any.

---

### Post by forestpixie on 2008-05-04
Not having had that problem - I found these on the forum - it appears that a file needs to be edited.

/etc/hosts and /etc/hostname should both have the same name in

I'm guessing that in /etc/hosts - it doesn'tt refer to ubuntu, use this to get you in 
[http://ubuntuforums.org/showpost.php?p=4872544&postcount=4](http://ubuntuforums.org/showpost.php?p=4872544&postcount=4)

Hope that helps

---

### Post by Mad_Max_1412 on 2008-05-04
Under Gutsy I didn't have this problem but looking at the thread I decided to check my hosts and hostname files.

My hosts file has:

127.0.0.1 localhost
127.0.1.1 ubuntu.necau

My hostname file has:

ubuntu

Obviously I've very creative when I installed Ubuntu and it came to naming the box.

I will change the 127.0.0.1 entry to read ubuntu instead of localhost and will let you know how it goes.

** EDIT **

Well it all works fine now.  Once I made the change, I clicked on the "Updates available" notification icon, it told me about the 2 that were available and once I clicked on update, it prompted for my password and downloaded them.  I then did a check and it downloaded the 66 files required and confirmed I'm up to date.

It must be something new in Hardy that wasn't needed in Gutsy.

BTW, I noticed the password box didn't disappear until well after the updates had downloaded and installed, and there's still grey shading over parts of the top area of the screen.  This is from when the screen "greys out" when prompting for the password.  It basically never cleared the screen properly once the password had been entered - but I guess that's a new bug for a new thread.

Thanks

---

### Post by forestpixie on 2008-05-04
I think that you need to change the other one, my 127.0.0.1 is localhost, but 127.0.1.1 matches my pc name

change your 127.0.1.1 to ubuntu from ubuntu.necau

---

