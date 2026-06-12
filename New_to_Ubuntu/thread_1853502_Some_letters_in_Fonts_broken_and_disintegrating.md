---
title: "Some letters in Fonts broken and disintegrating"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by Seraphim9 on 2011-10-02
I recently installed Ubuntu 11.04 and have been seeing this odd font disintegration while surfing online. I've noticed that it tends to occur once the computer has been on for awhile, at random, and disappears when the page is refreshed. It's not a major issue but has anyone else experienced this, what's causing it to happen and most importantly how to make it stop. I have attached a screenshot to give you a visual. Any help would be much obliged.

---

### Post by meatytaco on 2011-10-05
could be anti aliasing?

---

### Post by Seraphim9 on 2011-10-05
The little bit of research that I have done on the web points to a bug in the xserver.xorg-video-intel with no applicable solution. Wasn't an issue on Maverick. Weird. Do I even need this package? Is it safe to delete? Some have suggested creating an xorg.conf file and pasting:

Section "Device"
     Identifier "Intel"
     Driver "intel"
     Option "DebugWait" "true"
 EndSection

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/745608](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/745608)

But this caused my machine to crash and I had to do a fresh install!! Sadly this annoyance isn't disruptive enough to get the masses working on it. Bah!!

As far as anti-aliasing, I am using the open-source driver how would I go about enabling/disabling anti-aliasing. Thanks for the suggestion!

---

### Post by meatytaco on 2011-10-05
I'm not sure. I've never needed to. You can try this :[http://www.mombu.com/gnu_linux/mandriva/t-how-to-disable-blurring-antialiasing-of-text-1460553.html]("http://www.mombu.com/gnu_linux/mandriva/t-how-to-disable-blurring-antialiasing-of-text-1460553.html") or do a quick google search. There seems to be a lot on the net about it.

---

### Post by mschooler93 on 2011-10-05
i

---

