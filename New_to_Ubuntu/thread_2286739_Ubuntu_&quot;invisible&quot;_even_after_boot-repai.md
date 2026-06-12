---
title: "Ubuntu &quot;invisible&quot; even after boot-repair"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by bobb3 on 2015-07-14
[FONT=arial]Hi all,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I have an ACER Aspire V13-371-570S currently working under Windows 8. I wanted to create partition and install ubuntu on it.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I therefore proceeded as follows:[/FONT]
[FONT=arial]I created a partition (141,86 GB) that you can see on this screenshot:

[ATTACH=CONFIG]263196[/ATTACH]

Then I installed ubuntu on the partition thanks to a LiveUSB.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]But when I tried to reboot the PC started straight to Windows 8, I therefore used Boot repair via my LiveUSB, at the end of the boot repair process it said the repair was successfull and it generated the following report:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][paste.ubuntu.com/11874993]("http://paste.ubuntu.com/11874993")[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]This did change nothing, there is no menu to get Ubuntu and the Windows 8 start straight as usual. As advised by Boot repair I used the command:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]bcdedit/set {bootmgr} path \EFI\ubuntu\shimx64.efi[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]You can see the edition of bcdedit in this screenshot:

[ATTACH=CONFIG]263195[/ATTACH]

[/FONT]
[FONT=arial]The problem was not solved so following some advices I disabled the quick start of Windows 8 but nothing again.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I also tried to change the boot order, I need to mention that there was no Grub or Ubuntu mention on the boot menu. I write here the order and composition of my boot ranking:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]1 HDD: ST500LM00-1EJ162[/FONT]
[FONT=arial]2 Windows Boot Manager
3 USB FDD
4 USB HDD
5 Network Boot-IPv4
6 USB CDROM[/FONT]
[FONT=arial]7 Network Boot-IPv6[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]After several trials I got nothing too. I then switched UEFI to legacy -> it displayed "no bootable device" when starting computer.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Could you help me to boot on Ubuntu? :)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Many thanks for your help,[/FONT]

---

### Post by CitadelUniversal on 2015-07-14
Welcome to the forums, have you followed these instructions [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) ?

---

### Post by bobb3 on 2015-07-14
Thanks for welcoming me :),
by default my PC is under Windows8, I used a live USB for installing Ubuntu, I installed it manually. However these instructions say:
"[COLOR=#333333][FONT=Ubuntu] the only thing in your computer outside of Ubuntu that needs to be changed is a small code in the MBR (Master Boot Record) of the first hard disk, or the EFI partition"

I did not do that. Should I use EasyBCD for that?
[/FONT][/COLOR]

---

### Post by oldfred on 2015-07-15
Your installs are UEFI, so do not use CSM/legacy/BIOS boot mode.

I do not recommended EasyBCD. It is just another menu and you have UEFI & grub as menus or bootmanagers already. Grub is both a boot manager & boot loader for Linux.

Some vendors modify UEFI to also use description to restrict what can boot. That is not UEFI standard.

The main work around has been to copy /EFI/ubuntu into /EFI/Boot and rename grubx64.efi or shimx64.efi to bootx64.efi. The /EFI/Boot/bootx64.efi is a hard drive boot entry or fallback boot entry. If you have bootx64.efi it probably is just a copy of Windows own bootmgfw.efi. But you should backup bootx64.efi anyway.

Also Acer is one brand that requires you to set an UEFI password and then set trust on other entries. Never lose that password, but that may be all you need.

       Screenshots of secure boot settings Asrock, Asus, HP, Acer
[URL="https://neosmart.net/wiki/disabling-secure-boot/"]https://neosmart.net/wiki/disabling-secure-boot/
[/URL]
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot

      [/URL]
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

    [URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]
[/URL]

[URL="https://neosmart.net/wiki/disabling-secure-boot/"]
[/URL]

---

### Post by dan183 on 2015-07-15
Thanks. Got the problem sorted out.

---

