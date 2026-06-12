---
title: "Really struggling with my dual boot Ubuntu 16.04!"
date: 2020-06-24
forum: New to Ubuntu
---

### Post by oskar1111 on 2020-06-24
Hi,

I need Ubuntu 16.04 on my laptop for work (virtual OS didn't work properly) and have spent the day trying to install it in dual boot with my Windows 10 Enterprise. However, after installing from a USB drive with a success-message at the end, after rebooting I get shipped straight into Windows. I followed this guide for installing: [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/) , and my disk partitions used for the installation are named {/dev/nvme0np6 ext4 /, /dev/nvme0np7 swap, /dev/nvme0np8 ext4 /home} (<- might be relevant looking at the Boot-Repair report). My laptop is a Lenovo ThinkPad P51s.

Trying to solve this, I have: 
- Disabled fast boot and UEFI secure boot
- Used, in Windows cmd (administrator), the commands "bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi" and "powercfg /h off"
- Run Ubuntu from the USB in try-mode and installed/run Boot-Repair through the terminal. The url for the report is: [http://paste.ubuntu.com/p/fRX5mkNy4p/](http://paste.ubuntu.com/p/fRX5mkNy4p/)

Problem is still:
- I can find no sign of having installed Ubuntu, either in BIOS, the boot-manager (pressing F12 on PC restart), anywhere, except the Boot-Repair report seems to have identified it being installed in one partition, however further interpretation of the report is way beyond my skills.


Best regards!


Oskar

---

### Post by oldfred on 2020-06-24
You did not have an entry in UEFI to boot Ubuntu. From this in report when using terminal:
sudo efibootmgr -v

But it reinstalled grub and said no error and added an entry in UEFI.
If you choose the one time boot key (same key you used to boot installer flash drive) does it not show an Ubuntu entry. And then does that boot Ubuntu?

It also looks like you get a lot of errors on trying to mount the Windows NTFS partition. That normally is from hibernation or fast start up which also sets hibernation flag.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Some UEFI or Windows sync Windows BCD & UEFI, so adding entry to BCD keeps the Ubuntu entry in UEFI as a boot option.

---

### Post by oskar1111 on 2020-06-25
Thank you,

If I boot with the USB stick (=key?) that I used to install Ubuntu, it takes me to GRUB where the options are "Try Ubuntu without installing", "Install Ubuntu", "OEM install (for manufacturers)", "Check disc for defects". Were you thinking I might see another option here to boot from the installed instance of Ubuntu? I have also tried all the ways to make sure hibernation and fast start up are disabled - no luck!

Best regards

---

### Post by oldfred on 2020-06-25
Line 100 in report shows the output of "sudo efibootmgr -v" after grub reinstall. It added the Ubuntu entry.


> BootOrder: [COLOR=#ff0000]0001[/COLOR],0000,0010,0011,0012,0013,0017,0018,0019,001A,001B,001C,001D,001E,001F
Boot0000* Windows Boot Manager    HD(2,GPT,565a274a-472a-4006-95de-36dcfbe553e8,0xe1800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...1................
Boot[COLOR=#ff0000]0001[/COLOR]* [COLOR=#ff0000]ubuntu[/COLOR]    HD(2,GPT,565a274a-472a-4006-95de-36dcfbe553e8,0xe1800,0x32000)/File(EFIubuntushimx64.efi)

It also made Ubuntu as first entry, so should be default boot.
Some UEFI do reset Windows to first, after first reboot.

---

