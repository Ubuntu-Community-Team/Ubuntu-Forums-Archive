---
title: "Setting up dual boot and Grub2"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by will_s2 on 2013-10-21
My PC with win 7 on it has died , pretty sure the MBR is corrupted . I have plugged in my Ubuntu SSD drive and have recovered all my files. Now thats a very short and brief history.....  

 Ubuntu is on a separate drive by itself and I dont want Ubuntu or Grub to manage my bootups. I will use the F12 key to select the Ubuntu drive but normally it will just boot to Windows 7. I will do this by installing or fixing the win7 hard drive without Ubuntu drive installed and then I will connect the Ubuntu drive and use the F12 key when I want Ubuntu.

Now this Ubuntu version was operated with a different Win7 and I would select win7 from the GRUB menu or just boot into Ubuntu. Now as this win7 drive is not there I want to edit my GRUB2 file so that it doesnt show anymore ie. remove it. Actually not sure that I really need GRUB anymore but it does give me a few options like memtest.

What is the best way to edit my GRUB2 boot file ?  Hope there is a little app as I am not good with the command line.

Also how do you remove all links to Ubuntu from the old Win7 hard drive  .. it wont boot directly but will boot if I use GRUB ie. boot to the ubuntu SSD. 

I

---

### Post by oldfred on 2013-10-21
Grub2 is actually two things, a boot manager that lists all systems to boot & a boot loader. You have to have grub to boot Ubuntu.

If you unplug or do not have a working Windows 7, this will update the grub menu and if Windows not found will not offer it to boot. But if it can see valid boot files it will still add a Windows boot entry.

sudo update-grub

You can turn off the os-prober so it does not look for other systems to boot. You can later turn it on if you do have others systems.

I turn it off in my systems as I manually add my own entries.
Backup grub.cfg just in case.
 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

 In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by will_s2 on 2013-10-21
well turning of probe looks like what I want

thanks for that, will let you know how I go

---

### Post by will_s2 on 2013-10-21
well have done it all  ..... rebooted and it looked and worked ok

thanks young fella  , pretty sure I am older:mad:

---

### Post by oldfred on 2013-10-22
Glad that worked.

The only time it may need redoing is if you totally reinstall grub2 for some reason. Normal updates should keep settings.

---

