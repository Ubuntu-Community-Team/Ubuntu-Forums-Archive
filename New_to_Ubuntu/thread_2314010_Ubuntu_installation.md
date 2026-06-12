---
title: "Ubuntu installation"
date: 2016-02-17
forum: New to Ubuntu
---

### Post by jose63 on 2016-02-17
I installed Ubuntu 14.04.3 LTS on a USB and on a CD, but the CD wouldn't boot up on my computer after I prioritize the BIOS boot or neither F12.
So I ran from the USB after booted into Windows and clicked the Wubi application in the installer that I download.
I selected to get 'Get Help to Reboot' option from the Ubuntu installer windows. Later after a total reboot, the message shows below and did not continue anywhere. I don't know what command to run to continue the installation. Please help me complete the installation. Thanks, Jose

____________________________________
Completing the Ubuntu installation.

BusyBox c1.21.1(Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help; for a list of built-in commands.

(initramfs)Unable to find a medium, containing a live file system.

---

### Post by oldos2er on 2016-02-17
Don't use Wubi, it is no longer supported and doesn't work on Win 8.* or later.

Did you disable Secure Boot and Windows "fast boot"?

---

### Post by hakuna_matata on 2016-02-19
> **jose63 said:**
> 
BusyBox c1.21.1(Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help; for a list of built-in commands.

(initramfs)Unable to find a medium, containing a live file system.
It is possible that the [BusyBox]("https://en.wikipedia.org/wiki/BusyBox") appears without Wubi, too. It is also possible to run Wubi only for rebooting without Wubi install.

So my first question is, "did you only run Wubi or did you also install Ubuntu with Wubi?". If you install Ubuntu with Wubi you should see [this picture from Wubi guide.]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=wubi-123.png")

If you installed Ubuntu with Wubi, my second question is, "which Wubi version did you use?"

The Wubi version from [official release site]("http://releases.ubuntu.com/trusty") has an initramfs issue which could finally end in a BusyBox. see [here]("http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted") 
The maintained versions from [here]("https://github.com/hakuna-m/wubiuefi/wiki") do not have this issue.

Another issue could be "Fast Startup". Generally, you can use Windows guides like [this one]("http://www.intowindows.com/enabledisable-fast-startup-in-windows-8") to disable "Fast Startup".
In [some Wubi versions]("https://github.com/hakuna-m/wubiuefi/wiki#fast-startup-and-hibernate") we disabled this feature in UEFI mode by default.

But there are also other BusyBox issues which depend on your hardware.

---

