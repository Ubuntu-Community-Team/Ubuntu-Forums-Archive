---
title: "Windows or standard install of 12.04"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by frankelr on 2012-08-01
I will be installing 12.04 to a new windows 7 machine.
This computer will be upgraded to Windows 8 in the fall.

Which is the safest Ubuntu install to allow for a new Windows OS later?  Is this a lost cause because any windows upgrade will destroy Ubuntu?  I'd thought having Ubuntu in a directory might
solve this problem.  This is my wife's computer and must be kept running.

Any advice is appreciated

Bob

---

### Post by kabukiM0n0 on 2012-08-01
I'm a little lost. When you say "Which is the safest Ubuntu install to allow for a new Windows OS later?" are you referring to wanting a dual boot hard drive at the moment and at a later date upgrade to Win 8? or completely removing Win7 for the time being - using Linux and then re-running only win8?

---

### Post by Lars Noodén on 2012-08-01
It's not a matter of Ubuntu.  Windows does not play nice with other systems.  It's well documented, for ages.  If Vista 8 is like the earlier versions then it will be most efficient to install Ubuntu after installing Windows.  If you do it the other way around, you'll have to repair the bootloader (at least).  It's doable, but Windows makes it unnecessarily hard.  It's a common enough problem that it's written up in a lot of places:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by drmrgd on 2012-08-01
As Windows 8 might only be installed UEFI Secure Boot (I'm not sure if an absolute clear decision has been made on this yet), you'll want to take that into consideration in terms of how you install.  If your motherboard is capable of UEFI, I would recommend you be sure to install Ubuntu as UEFI, which is a bit more challenging, but certainly possible.  It may be that it will be possible to install Windows 8 in BIOS mode, but if you can install everything GPT / UEFI, it's probably worth it as this is where the technology is going.

Here's a few tidbits on UEFI dual booting for you to consider:

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187](http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Update:  As I was Googling for my usual cache of UEFI links, I came across this, which might be relevant:

[http://www.phoronix.com/scan.php?page=news_item&px=MTEyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNDY)

---

### Post by frankelr on 2012-08-01
She is mainly a Ubuntu user on a failing dual boot (Vista and Ubuntu 11.10) computer.  We have to replace it now.  It sounds like my choice is leave the new computer at Windows 7 and dual boot
12.04 OR tell her to use Windows 7 now, update to Windows 8 in October and add Ubuntu (probably 12.10) in November.  I was sort of
hope that by using the dual boot windows install method. Microsoft's upgrade would not destroy the Ubuntu install


Bob

---

### Post by drmrgd on 2012-08-01
Unless there's a specific reason you need to upgrade to Windows 8 when it comes out, why not wait?  It looks like there will be some fixes and workarounds for dual booting the two OSes after they've been out a short time.  So, if you don't absolutely need to be on the bleeding edge, I'd recommend dual booting Windows 7 and Ubuntu (I think it's still better to set things up in UEFI mode), and hang on to that until there's a good, proven way to dual boot Windows 8 and Ubuntu.

---

