---
title: "dpkg-reconfigure xserver-xorg does nothing"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by Yags on 2012-02-04
Hi, I'm brand new to Ubuntu, but have a long history with dos, etc. so I'm not scared! :)

I installed from the 11.10 CD that I downloaded from ubuntu.com.  Everything went smoothly in the install, but my video performance is very slow.  I searched around and found a few threads like this one: [http://ubuntuforums.org/showthread.php?t=1095102](http://ubuntuforums.org/showthread.php?t=1095102) for my vid card.

My problem is that when I try "sudo dpkg-reconfigure xserver-xorg" in the terminal, absolutely NOTHING happens.  The cursor just goes to the next line.

I tried the "terminal" app, the "Xterm" app, and pressing ctrl+alt+f1 to get a full screen terminal.  All behaved the same.  I tried re-installing Ubuntu without 3rd-party updates, but it still wont work.  What else can I try?

Thanks for the help!

---

### Post by Yags on 2012-02-04
I thought maybe I need to create the file for the editor to work.  As I looked for a way to do that, I saw that it seems like xorg is going out of fashion in newer versions of ubuntu.  For example, it tells me that it can't find the command for "xorg -configure".

Is there a different configuration file I should be trying to edit now, besides xorg.conf?

---

### Post by ksa-_-jed on 2012-03-25
> **Yags said:**
> I 
"xorg -configure".

?
Xorg -configure not "xorg -configure" capital X not small  x

---

### Post by collisionystm on 2012-03-25
What video card do you have?

---

### Post by ikt on 2012-03-25
> **Yags said:**
> Everything went smoothly in the install, but my video performance is very slow.

Where do you see slow video performance?

You are using an ATI card, your performance should not be slow as the open source drivers are great.

---

