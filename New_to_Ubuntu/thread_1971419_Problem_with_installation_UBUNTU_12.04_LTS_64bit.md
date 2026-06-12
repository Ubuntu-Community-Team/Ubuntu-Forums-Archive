---
title: "Problem with installation UBUNTU 12.04 LTS 64bit"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by sunsina on 2012-05-02
I donwloaded the UBUNTU 64BIT 12.04LTS final release from UBUNTU website I used Virtual BOX to install  that linux on my USB Stick (bootable) in Windows7 64bit Environment.

Installation is correct and works flawlessly (direct booting from USB Stick) but when I want to use that USB Stick on my Alienware M11x (Optimus GTX-540M with SandyBridge i7) it does not boot at all it freezes and shows blank screen without any error message....
I think there must be some problem with (Hybrid) Graphic card  or ACPI or ....
I don't know if there exists any solutions for that or not since even I don't get any error messages.
I have tried other linux forums to get any answer but I didn't get any useful  reply.
I would be very glad if someone could help me with that issue
Thanks

---

### Post by kc1di on 2012-05-02
here's a page that may give some clues 

hope it helps 
D ;) 
[http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/]("http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/")

---

### Post by sunsina on 2012-05-04
:(
No!It does not work.
Is it any possibility to boot Linux directly without grub
I just want my linux to be installed and booted from USB Stick and I don't need any 
useless boot manager like GRUB.

In addition when I install BumbleBee (since I have to use another notebook without optimus to boot into linux) I get an error.
Is there any other better boot loader than GRUB?
Thanks

---

### Post by MartyBuntu on 2012-05-04
What's wrong with GRUB?

---

### Post by pqwoerituytrueiwoq on 2012-05-04
make the usb using unetbootin 
press the tab key to edit the boot line 
between splash and quite put "nomodeset" no quotes (i don't know if it will work if it is after the --)
and once you install before you reboot open up /media/[something_here]/boot/grub/grub.cfg as root (sudo gedit) and scroll down to the 1st boot entry and add nomodeset to it 
```
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 5da737f4-8535-430c-8d5a-e228bccf58e1
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=5da737f4-8535-430c-8d5a-e228bccf58e1 ro   splash **nomodeset **quiet $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}

```once you boot into the system edit /etc/default/grub
do this to it
```
GRUB_CMDLINE_LINUX_DEFAULT="splash **nomodeset** quiet"
```and run [FONT=Courier New]sudo grub-update[/FONT]
yuo may need to get the latest nvidia driver 295.49 from the xswap ppa (i dont think it is in there quite yet)

---

