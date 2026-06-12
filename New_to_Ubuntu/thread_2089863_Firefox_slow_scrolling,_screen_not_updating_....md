---
title: "Firefox slow scrolling, screen not updating ..."
date: 2012-11-30
forum: New to Ubuntu
---

### Post by cwmoser on 2012-11-30
My Firefox browser is slow scrolling and the screen does
not update properly.  Have to do reloads to make the
screen correct.

I have Ubuntu 12.04 64-bit, Firefox 17.0

Seems like it just happened a few days ago.

In addition, when I do uname -a I get 3.2.0-32-generic
But, I can also see in /boot these:  
3.2.0-33-generic
3.2.0-34-generic

and my grub menu just shows 3.2.0-32-generic

Could this be related???

Carl

---

### Post by arpanaut on 2012-11-30
Do you have more than one install of Ubuntu?
If so which is in control of booting?

If not have you run: ```
sudo update-grub
```
this will update your boot menu and the newest should become the default,
This should have happened when you updated these kernels,
sometimes funny things happen???

As far as firefox is concerned, you might want to check out if you have any conflicting plugins, you might want to create a new profile in firefox and see if that behaves badly too.

---

### Post by Charles Vairin on 2012-11-30
After upgrading from 11.04 to 11.10 the new firefox is doing the same thing. Very disconcerting. May be firefox.:guitar::guitar::guitar:

---

### Post by cwmoser on 2012-11-30
I tried this in Firefox ...
Help -> Troubleshooting information -> Reset Firefox
... to create a new profile.

Then disabled a number of plugins.

Still slow and sometimes does not paint the screen 
correctly.

Carl

---

### Post by SeanIM on 2012-11-30
Have you tried the "Chromium" browser?  It's really pretty decent.  At least you'll be able to make sure it's just a FF specific issue and not a graphics or system issue you're dealing with.

---

### Post by cwmoser on 2012-12-01
Looks like my scrolling issue is fixed.
Not sure if this was the fix but this is what I did.

1- I maintain an output of processes using ps -ejH > workingx.txt so I can tell
is there are processes that are slowing down Ubuntu.  I noted that
notify-osd was a difference --- so I  **sudo  apt-get  delete  notify-osd**

2- logged off and tried to log back in but could not log
on with GNOME.  So I rebooted and tried again - still
could not log on with GNOME. 

3- logged on with UNITY.  Went to Terminal and **sudo  apt-get  install gnome**

4- logged off

5- logged on with Gnome Classic and now it works.

Not sure if this is the fix but this is all I can remember I
was doing that could have affected a change.

Oh yeah, I did try **sudo apt-get update-grub** to see if I could get the kernel
to 3.2.0-34 but that did not work.  Doing this also may have fixed
my scrolling problem.

Carl

---

