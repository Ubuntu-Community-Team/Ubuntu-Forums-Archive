---
title: "Black Screen after install cursor blinking"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by UBFan77 on 2012-02-23
I installed Ubuntu 11.10 desktop iso alongside windows 7  around two days ago. It installed fine and rebooted and i was presented with the desktop screen. I then installed wine 1.3  and chromium and updated the graphics drivers as recommended by ubuntu. then when i rebooted my notebook, after pressing ubuntu in the grub menu , all i get is a black screen and blinking cursor. i tried recovery mode but it stops midway while loading the files.
My windows 7 is installed in sda/1 and ubuntu in sda/8.

---

### Post by Gone fishing on 2012-02-23
Try starting up in recovery mode and report what happens - I suspect it is a problem with the graphics driver.

To start in recovery mode press shift after the BIO screen and then select recovery mode from the grub menu

---

### Post by UBFan77 on 2012-02-23
as i said above i tried recovery mode but it stops at some kernel helper   line.

---

### Post by roelforg on 2012-02-23
Try reinstalling but skip the updating of the extra video-driver.

---

### Post by UBFan77 on 2012-02-23
when i insert my ubuntu usb and select install ubuntu or try ubuntu, either way it says something like kernel panic not syncing

---

### Post by uRock on 2012-02-23
Merged and jailed triplicate posts. Please do not create more than one thread for a topic.

---

### Post by wildmanne39 on 2012-02-23
Hi, you should be able use one of the options on the link to load so you can change your driver for your video card.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by UBFan77 on 2012-02-23
@URock Sorry my network went down the exact second i posted the message so i thought that my message was not posted hence i posted it three times by mistake.


@wildmanne39 I tried nomodeset but that also yields a blinking cursor. and btw i had said above that my graphics is of intel not nvidia.

---

### Post by wildmanne39 on 2012-02-23
Hi, I am sorry but I do not see where you mentioned your video card in this thread but may be I am missing it.
Thanks

---

### Post by UBFan77 on 2012-02-24
@wildmanne39 no its not ur mistake. i had by mistake made triple posts on the above topic and while jailing them the mod must have by chance vcut that line out.

---

### Post by wildmanne39 on 2012-02-24
Hi, did you try all the options at that link one at a time? there are several there.

You have an intel card? how did you upgrade the driver?
Thanks

---

### Post by UBFan77 on 2012-02-24
i didn't install the driver, it was automatically installed during installation(i think so). after the installation completed i saw a pop up box about recommended hardware in the top right corner and opened it. it said something about activating and installing some display driver which i did. then i installed wine and chromium and the next time it rebooted i get that damn blinking cursor.

---

### Post by wildmanne39 on 2012-02-24
Hi, it would not do that for intel cards so you may have two cards which can cause problems so please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```

lspci | grep VGA
```
Thanks

---

### Post by UBFan77 on 2012-02-24
and yes i tried nomodeset and acpi=off but those lead to the same blinking cursor.

---

### Post by UBFan77 on 2012-02-24
i also tried this(since it said about intel drivers)  though it is for 10.04 but it didnt work as well-
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by wildmanne39 on 2012-02-24
Hi is this what you are talking about?>     GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash i915.modeset=1&#8243;I was going to suggest that as well.

Please show the output of the command in my last post that will give us a better idea of what we are dealing with.
Thanks

---

### Post by UBFan77 on 2012-02-24
the report is like this:
00:00.0 8086:2a00 [0600] Host Bridge
00:02.0 8086:2a02 [0300] VGA Controller
00:02.1 8086:2a03 [0380] Display Controller
00:1a.0 8086:2834 [0c03] USB Controller
00:1a.1 8086:2835 [0c03] USB Controller
00:1a.7 8086:283a [0c03] USB Controller [PI 20]
00:1b.0 8086:284b [0403] Multimedia Device
00:1c.0 8086:283f [0604] PCI-PCI Bridge
00:1c.2 8086:2843 [0604] PCI-PCI Bridge
00:1c.3 8086:2845 [0604] PCI-PCI Bridge
00:1d.0 8086:2830 [0c03] USB Controller
00:1d.1 8086:2831 [0c03] USB Controller
00:1d.2 8086:2832 [0c03] USB Controller
00:1d.7 8086:2836 [0c03] USB Controller [PI 20]
00:1e.0 8086:2448 [0604] PCI-PCI Bridge [PI 01]
00:1f.0 8086:2815 [0601] ISA Bridge
00:1f.1 8086:2850 [0101] IDE Controller [PI 8a]
00:1f.2 8086:2829 [0106] SATA Controller [PI 01]
00:1f.3 8086:283e [0c05] Serial Bus Controller
06:00.0 10ec:8136 [0200] Ethernet Controller

---

### Post by wildmanne39 on 2012-02-24
Hi, please copy and paste the command for accuracy because it should have looked more like this.
```
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)

```
Thanks

---

### Post by UBFan77 on 2012-02-24
@wildmanne39 Why would it show nvidia geforce gfx when i have intel. and yes i triple checked the above it shows the same everytime.

---

### Post by HeroOfCanton on 2012-02-24
> **UBFan77 said:**
> @wildmanne39 Why would it show nvidia geforce gfx when i have intel. and yes i triple checked the above it shows the same everytime.

Make sure you are using the pipe symbol (shift and backslash) between lspci and grep VGA. Your output appears to be showing just a dump from the lspci command.

---

### Post by UBFan77 on 2012-02-25
Since i cannot boot into Ubuntu i go to grub menu and press "c" to open up the terminal.
 As u said i typed lspci | grep VGA and it yields this error-

error : syntax error
error : incorrect command
error : syntax error


i tried various combinations of the above command like - lspci | grepVGA 
, lspci|grep VGA etc but all yield the same error.

Also one more problem is that when i insert my ubuntu installation usb through which i installed my current version i get a 'kernel panic not syncing unable to mount vfs' error. So that prevents me from either trying or installing ubuntu.:(

---

### Post by wildmanne39 on 2012-02-26
Hi, it wouldn't that was just an example of what the output should have looked like but with your cards information.
Thanks

---

