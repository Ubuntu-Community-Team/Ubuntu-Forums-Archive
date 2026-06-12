---
title: "How to get rid of system start up options?"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by mapes12 on 2012-05-24
Here's what I did:-

- Clean install of 12.04 on my test rig
- Updated the theme ( [http://www.noobslab.com/2012/05/mac-os-x-lion-for-ubuntu-1204-precise.html](http://www.noobslab.com/2012/05/mac-os-x-lion-for-ubuntu-1204-precise.html) )
- Created a Remastersys backup
- Used the backup to install the custom installation onto my laptop that was previously running 10.04

Now everytime the laptop starts up I'm asked to select which kernel I want and a clock ticks down and loads the top one if I don't do anything. How can I get rid of this and have the laptop just boot into the 12.04 kernel?

Mark

---

### Post by MadmanRB on 2012-05-24
You mean bypass GRUB?
Personally I wouldnt do it, sure its an extra step but it comes in handy if you need recovery options.

---

### Post by glugT on 2012-05-24
You need not bypass the grub.Just make the default option to be 12.04.so in that way you wont have to move your arrows up and down to choose your kernel.The grub is essential for recovery purpose.
Edit your grub to make 12.04 your default :-) 
got to:  
/boot/grub/grub.cfg-here see which option is your 12.04(index starts from 0)
now go to etc/default/grub and change the default accordingly
you can look at this link for changing grub menu options
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by glugT on 2012-05-25
Let me know if the post was helpful

---

