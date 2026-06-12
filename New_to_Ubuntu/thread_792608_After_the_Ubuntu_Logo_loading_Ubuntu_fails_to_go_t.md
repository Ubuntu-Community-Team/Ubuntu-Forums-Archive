---
title: "After the Ubuntu Logo loading Ubuntu fails to go to the login screen"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by wasim2050 on 2008-05-13
About a week ago I install Ubuntu 8.04 and it is working fine except sometimes when it just refuses to go to the login screen {after all the logo loading procedure} and sometimes it goes to the login screen smoothly. And when it fails to go the login screen I tries to go to the command prompt by pressing Alt-F1 but it do not go to the command prompt and even the Num lock does not work at this stage and the screen remains blank and all I can do is doing a hard reset with the hope that it will go to the login screen this time and most of the time it does but sometimes it just refuses to go to the login screen even after multiple hard reset. I thought that maybe this is a display driver problem but I am not able to find out which display driver Ubuntu is using I tried sudo dpkg-reconfigure xserver-xorg and it does not helped me. I even try looking at xorg.conf but it too did not revealed to me which display driver Ubuntu is using. My Motherboard is Asus with Intel 845GE Display card inbuilt and Samsung SyncMaster 732 NW widescreen LCD monitor.

Please Help

---

### Post by click4851 on 2008-05-13
Do you have a copy of the LiveCD, does it do this with that?

---

### Post by mapes12 on 2008-05-13
I had similar problems with 8.04 so I downloaded 7.10 alternatate CD. Burned it to disk and installed with the text based installer. OK, I haven't got 8.04 but I have Ubuntu running perfectly.

---

### Post by philinux on 2008-05-13
Use Applications>Accessories>terminal

type in

[FONT="Courier New"]lspci[/FONT]

Post the output of that.

---

### Post by wasim2050 on 2008-05-13
> **philinux said:**
> Use Applications>Accessories>terminal

type in

[FONT="Courier New"]lspci[/FONT]

Post the output of that.


Here is the Output

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by django0909 on 2008-05-13
My installation of 8.04 was freezing at this:

```
Running local boot scripts(/etc/rc.local) [ok]
```

I ended up going back to my previous installation. Sounds like you have the same problem...

---

### Post by wasim2050 on 2008-05-14
So any solution for my problem?

---

### Post by django0909 on 2008-05-14
Does the boot process hang at the above line?

---

### Post by wasim2050 on 2008-05-14
> **django0909 said:**
> Does the boot process hang at the above line?


Actually the whole process happens in GUI and there is no text display so I am not sure what is happening in the background.

---

### Post by PuppetMaster2070 on 2008-05-14
I had similar problem and all I did is:
i logged on to windows and then scanned all partitions twice with the Autmotically fix file system option on
and it went smoothly after that 

i hope it work with you

---

### Post by wasim2050 on 2008-05-15
Well I have submitted my problem as bug. Now let see what the ubuntu and linux gurus do about it.:) [https://bugs.launchpad.net/ubuntu/+bug/229686](https://bugs.launchpad.net/ubuntu/+bug/229686)

---

### Post by movd on 2008-05-19
I am having the exact same problem. Everything else works perfectly. The only problem I have is sometimes I can and sometimes I can't get to the login screen. I'm fairly new so I don't know many ways to try to find out the cause of this.

I've been searching to see if anyone else is experiencing the same thing and you are the only other person I've seen with this exact problem. Have you had any success with fixing it?

---

### Post by wasim2050 on 2008-05-19
@movd

The bug has been confirmed by the Ubuntu kernel team so we have to  wait for the solution but there is something you can do to speed up the process{I guess}. Go to this link [https://bugs.launchpad.net/ubuntu/+bug/229686](https://bugs.launchpad.net/ubuntu/+bug/229686) and submit your comment on that page that you are also facing the same problem and in this way they will understand that the problem is not unique to one individual.:)

---

### Post by snailmail on 2008-05-19
yep. same prob here. still on 8.04 B6, with 529 updates :rolleyes:
i updated, and i had to do a complete reinstall of the entire HD.

---

