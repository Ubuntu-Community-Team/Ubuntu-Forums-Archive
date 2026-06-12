---
title: "grub loader did not install"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-10-09
Hello ya'll,
I am trying to install 8.04 LTS Ubuntu lamp server edition on a Pentium II notebook w/192 mgb RAM.  I have read that this is about the minuimum system Ubuntu will install on.  I plan on installing the Xubuntu desktop GUI if I can get to a command prompt.  I have gone completly through the server installation all but the installer hung up on the GRUB loader.  I retried it several times but kept getting GRUB Loader installation failed.  I finally went ahead and finished installation without loading the GRUB.  This is a 6 gb hard drive and I plan on having Ubuntu as the only O.S. When I reboot, if the CD is not in the drive it comes up to a Operating System not found error.  I assume this is because the GRUB loader did not install.  I can insert the CD and go into rescue mode but I can not get back to the install menu to try to install the GRUB loader. Is there anyway to install the GRUB through the rescue mode on the CD?  Or would it be better to install the complete O.S. over and hope it installs the GRUB loader the next time?

All responses will be appreciated.


James

---

### Post by phidia on 2008-10-09
You should be able to install grub from the install cd.
You want to install grub to the MBR I presume so the command:
> sudo grub-install hd0 should work-unless your drive designation is something very different. Keep in mind the grub commandline only recognizes "hdx" where x=a drive #  grub commandline doesn't use sd as a drive designation.

For more on grub see [this]("https://help.ubuntu.com/community /RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")
The grub wiki index of topics is [here]("https://help.ubuntu.com/community/Video?action=fullsearch&context=180&value=grub&titlesearch=Titles").

---

