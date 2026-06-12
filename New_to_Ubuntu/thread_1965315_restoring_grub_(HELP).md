---
title: "restoring grub (HELP)"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by jakespet on 2012-04-25
I have just installed ubuntu 12.1 alongside ubuntu 10.11. While I was installing 12.1 I was given the choice to dual boot. BUT,when I start up I am not given a choice which one I want to load. It automatically loads 12.1. Now I cannot access my files that I have on 11.10.And I really need most of tyhose files.
I'm sure there's someone out t here who can help me. (Please tell me it's simple.) :)
By the way i haven't discovered how to update my profile on Forums and my email address has changed {deleted}  Thank you

---

### Post by strask on 2012-04-25
Ok first of all, try pressing shift when you first boot to see if you can get a grub menu, that might have the options you are looking for.

If you get the grub menu but it doesn't list your other install, then go ahead and boot into the new linux install and try ```
sudo update-grub
``` to rebuild your grub configuration; it might detect your old ubuntu and add it to the grub menu for the next time you reboot.

If that doesn't work, download the boot info script from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) and run it, post the output here inside [ CODE ] tags.

---

### Post by oldfred on 2012-04-25
The forums get so much spam that they changed to only allow users with 50 posts to update profile. If you need changes post Forum Feedback and help.

I removed your email as the forums are constantly scanned and you would get lots of spam. An email address in your profile is not public where here in a thread it is. You should just post in threads, and can use advanced search to find all your threads if need be.

+1 on suggestions by strask

---

### Post by click4851 on 2012-04-25
could try supergrubdisk, and see if it can recover your ability to boot to the different installs.

---

### Post by gordintoronto on 2012-04-25
> **jakespet said:**
> Now I cannot access my files that I have on 11.10.And I really need most of tyhose files...

When you run Nautilus (file manager) you should see entries such as "138 GB filesystem" near the top-left. Those are other partitions on your hard drive, one click and you should be able to access the files.

Having gotten access, make a backup! Get a stack of DVD-Rs and a couple of flash drives, or buy an external hard drive.

---

