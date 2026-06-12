---
title: "Grub not working now, after working for a week."
date: 2016-09-05
forum: New to Ubuntu
---

### Post by bjskifreak on 2016-09-05
I installed Ubuntu 16.04.1 about a week ago on a partition from my Windows 10 OS.  Since then, I have been able to successfully use Grub to choose either windows or Ubuntu to boot.  Just now, however, I restarted and the Grub menu didn't appear.  The bios menu also did not appear.  It then booted straight into Ubuntu.  This happened after I tried to hard restart with the power button and the prompt appeared suggesting that I save files first.  My files were all saved, but I exited out and saved them all anyways, and then shut down just from the actual software option.  Settings seem to have changed as well.  For example, my desktop is now stuck at 1024x768, while before I was at 1920x1080.  The only other option is 800x600.  This was the case before I installed drivers for my graphics card.  Also, when I signed into gmail, it recognized me as logging in on a new computer, even though I have logged in on this before.  I've tried holding down shift on startup, and it still just boots straight to Ubuntu.  I have updated Grub as well.

---

### Post by yancek on 2016-09-05
Nothing in Ubuntu is going to have any effect on the BIOS so that is a separate problem.

Were any changes made before this problem occurring?

In order for someone to help you it would be necessary to provide more detailed information.  You can get that by using the boot repair tool which you can download from the site at the link below and burn to a CD and boot it.  Select the option to Create BootInfo Summary and do not make any changes.  Post a link to the output here and someone should be able to suggest a possible solution.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Norm24 on 2016-09-05
Install Grub Customizer.It will give you a lot of options to tweak the Grub menu,including showing the menu and looking for other OSs.

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by bjskifreak on 2016-09-06
I was able to configure grub to have Windows as the first option.  And it now boots to Windows.  I believe it is actually going through the BIOS screen and grub, and then when grub times out it just boots the first option.  So I'm guessing it's motherboard related.  So I'm going to try to go through support for that.  Thank you for your help.

---

