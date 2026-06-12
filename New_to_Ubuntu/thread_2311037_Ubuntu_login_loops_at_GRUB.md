---
title: "Ubuntu login loops at GRUB"
date: 2016-01-24
forum: New to Ubuntu
---

### Post by romitm on 2016-01-24
Hi everyone,

I've been using ubuntu on my Lenovo Z50 laptop for over two years with rare hiccups (nothing that couldn't be solved by reading up), and yesterday for the first time I faced a problem booting up. To be clear, I didn't make any explicit changes leading up to the problem. The most I may have done is to run a apt-get update/upgrade (I don't remember, but I do do that often)

I'm running Ubuntu 15.10. Until maybe 6 months ago I used to restrict myself to LTS; however since the Lenovo z50 uses a hybrid graphics mode (nVidia/intel) I used to get very frequent freezes. After reading that 15.10 was better treating that issue, I moved to 15.10 and that problem seems to have vanished.

Anyway, yesterday the login came to the GRUB2 menu and any attempts to click through looped back to the menu. The recover mode option led to the same. I had a liveUSB of 14.04, booted it and followed instructions from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

After rebooting, the issue has persisted. Here is the pastebin: [http://paste.ubuntu.com/14628303/](http://paste.ubuntu.com/14628303/)

I'd appreciate any tips on what I can do next. I'm aware I can probably reinstall and keep my data but I'm hoping there is something obvious I'm missing.

Thanks!

---

### Post by yancek on 2016-01-24
> The boot of your PC is in EFI mode, but no EFI partition was detected.

The message above is at the bottom of the boot repair output.  You have Grub code in the MBR of the drive which should not be there if you are using UEFI.  
Were you originally using EFI?  If you were using MBR to boot you need to go into the BIOS and change that setting, disable EFI and enable MBR which is referred to as CSM.  I don't use UEFI and the manner in which it is changed varies by manufacturer so you'll need to check your manual if you have it or look for it online or wait for someone with more detailed knowledge on it to post.

---

### Post by grahammechanical on 2016-01-24
If the solution is not solved by booting the OS in BIOS/Legacy/CSM mode then please consider this post

[http://ubuntuforums.org/showthread.php?t=2277509](http://ubuntuforums.org/showthread.php?t=2277509)

If we are getting to a login screen then the problem is nothing to do with the Grub boot loader. And Boot Repair only tries to fix boot loader problems.

If we are getting to a login screen screen then Linux is loading as it should.

This might also be a solution

[http://ubuntuforums.org/showthread.php?t=2267058](http://ubuntuforums.org/showthread.php?t=2267058)

Another possible solution

[http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

Regards.

---

