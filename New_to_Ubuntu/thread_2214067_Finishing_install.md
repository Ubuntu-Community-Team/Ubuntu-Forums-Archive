---
title: "Finishing install"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by gandalf4582 on 2014-03-30
I'm installing Ubuntu 13.10 on a PC that runs Win XP. I have run the install from a Live DVD. It has partitioned the disk and all seems to have gone okay so far. It got as far as saying I need to reboot to finish the install. So I rebooted but it simply booted up the Live system again. If I remove the DVD and reboot it eventually comes up with a message (initramfs) unable to find a medium containing a live file system

Any ideas what I need to do to complete the install please?

---

### Post by su:bhatta on 2014-03-30
Did you check the ISO for integrity on download? 

Have a look at here: [http://askubuntu.com/questions/17764/how-can-i-check-the-integrity-of-a-downloaded-ubuntu-cd](http://askubuntu.com/questions/17764/how-can-i-check-the-integrity-of-a-downloaded-ubuntu-cd)
Look the the links given in the answer. 

You can try to reinstall once and see if that works out, maybe your first install didn't finish right.

---

### Post by gandalf4582 on 2014-03-30
Thanks. It was a purchased DVD rather than a download. I tried to install again but it wanted to partition the disk again and I don't want that. When I rebooted I paid a bit more attention and when it said it was completing the install I opted for verbose mode. It didn't seem to attempt to complete the install but started Live mode.

---

### Post by su:bhatta on 2014-03-30
> **gandalf4582 said:**
>  It didn't seem to attempt to complete the install but started Live mode.

 Dont keep the Live disc inside when you are rebooting. 

Ubuntu doesn't require a reboot to finish installing, at least not seen it in 13.10 installation media. 
General steps are that the entire installation is finished and after that the prompt is 'You can keep using the Live session, or reboot to start using the new install' 
The installation disk is ejected by the System itself and asks to remove the media and press 'Enter' to continue reboot.

You can Choose 'Something Else' from the Partition table screen and choose to reinstall Ubuntu in the partition that you used the first time.

See this Link : [http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

---

### Post by gandalf4582 on 2014-03-30
> **bhattabhishek said:**
> Dont keep the Live disc inside when you are rebooting.
Then I get an error message:
(initramfs) unable to find a medium containing a live file system
I'll have another try at installing it again and have a piece of paper ready to take notes - when I'm feeling braver...

---

