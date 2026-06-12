---
title: "HowTo: Find out the maximum framebuffer resolution"
date: 2006-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by i3dmaster on 2006-01-31
I don't know if anyone has any better solution to find out the max fb resolution of a box, but the way I provided below should be a relative easier one than trying out the framebuffer vga mode matrix one by one. Ok, here we go:

1. You need a ubuntu install cd (or maybe a live cd), whichever one having an option for vga mode that you can pick. I used a dapper daily build install CD which works like a charm.
2. Insert the cd and reboot your box.
3. Boot from the CD and you should see the boot menu. Pick the maximum VGA mode in the list (normally F3 for the vga mode and you should see a list, then go down to the max one), then choose boot to **rescue your system** (**You don't want to do a fresh install just because of this** Actually, pick the rescue one isn't going to rescue anything but just need a prompt to your system). Note: If the screen goes black or messed up by using the resolution, then reboot and pick the one above until you get the max resolution that can display everything correctly.
4. Go on to the boot procedure, when it asks where to execute a shell, pick the one saying "execute a shell in the installer environment".
5. When you see the prompt, run this command```

cat /proc/cmdline
```
6. Do you see the **vga=xxxx ** option? That is your maximum framebuffer resolution that your graphic card and the monitor supported. Write it down.
7. Get the CD out and reboot your box to your hard disk normally. 
8. Open your favorite editor and edit the /boot/grub/menu.lst file. Go to the line like this: ```
# nonaltoptions=quite splash
``` to ```
# nonaltoptions=quite splash vga=xxxx
```. Replace the xxxx to the mode you just wrote down.
9. Save the menu.lst file. Then do ```
sudo update-grub
```.
10. After upgrading the grub system, all your kernel option except single mode should have vga=xxxx added.

An example of my box:
I have an intel graphic card and 20" monitor which I thought it can only support max to 16x12@32 before I did all above, but I found out when I boot from the ubuntu CD, it gave me 1920x1440@16 option. Then I boot from that and fortunately, it supported. Then I changed my grub option to vga=0x34d (which is 1920x1440@16) and now I have 1920x1440 resolution at console mode. Somebody might not like that huge screen with tiny fonts but I like it, its super for coding.

Have fun ...

---

### Post by dcstar on 2006-02-04
[QUOTE=i3dmaster]I don't know if anyone has any better solution to find out the max fb resolution of a box, but the way I provided below should be a relative easier one than trying out the framebuffer vga mode matrix one by one. Ok, here we go:

1. You need **an ubuntu install cd** (or maybe a live cd), whichever one having an option for vga mode that you can pick. I used a dapper daily build install CD which works like a charm.
2. Insert the cd and reboot your box.
3. Boot from the CD and you should see the boot menu. Pick the maximum VGA mode in the list (normally F3 for the vga mode and you should see a list, then go down to the max one), then choose boot to **rescue your system**
.......[/QUOTE]
Just out of interest, my Breezy Install CD didn't give me any VGA info/choices when I selected F3, just a list of install choices.

Perhaps this only works with Dapper CDs?

---

### Post by i3dmaster on 2006-02-05
Ok thanks for update. Its probably only from Dapper where you can choose the VGA mode.

---

### Post by anacron on 2006-03-02
> Perhaps this only works with Dapper CDs?

quite wrong... with breezy install you can add option like ```
vga=792
``` which is 1024x768 resolution, or ```
vga=794
``` 1280x1024 etc. also you can add that to your grub when installed if it's not in there after the install...

anyway those bigger resolutions might be harder to get work, but i'll assume you can get those work too :)

---

### Post by dcstar on 2006-03-04
[QUOTE=anacron]quite wrong... with breezy install you can add option like ```
vga=792
``` which is 1024x768 resolution, or 
......[/QUOTE]
No, it **is not** wrong - these "F3" options do not work with a Breezy CD.

The whole point of the option was to list the available VGA selections, and to find the maximum for your system as is stated in the title of this thread.

---

### Post by lars_p on 2006-05-15
you could also just:
```

apt-get install hwinfo
hwinfo --framebuffer

```

---

### Post by Czubek on 2006-05-16
[QUOTE=lars_p]you could also just:
```

apt-get install hwinfo
hwinfo --framebuffer

```[/QUOTE]
And what after that?

---

### Post by lars_p on 2006-05-16
[QUOTE=Czubek]And what after that?[/QUOTE]

You'll see a list of all supported framebuffer-modes. You can choose one and proceed like described in the first post. 

No live-CD needed for this.

---

### Post by Czubek on 2006-05-16
Hmmm, thats intresting cause i have:
czubek@cassandra:~$ hwinfo --framebuffer
czubek@cassandra:~$

---

### Post by tanawana on 2006-05-16
Does or would "fbset" do anything to help??

---

### Post by Co.Sinecure on 2006-08-01
> **Czubek said:**
> Hmmm, thats intresting cause i have:
czubek@cassandra:~$ hwinfo --framebuffer
czubek@cassandra:~$

Seems to not work when you do --framebuffer
Try:
hwinfo --log logfile
vim logfile

Although the only monitor info I found said my max resolution was 640x480, which is wrong. So i'm not sure hwinfo is the answer..

---

### Post by gschoper on 2006-08-01
> **Co.Sinecure said:**
> Seems to not work when you do --framebuffer
Try:
hwinfo --log logfile
vim logfile

Although the only monitor info I found said my max resolution was 640x480, which is wrong. So i'm not sure hwinfo is the answer..

I got the same thing when running it as a regular user. Try:

```
sudo hwinfo --framebuffer
```

gschoper

---

### Post by robnardo on 2007-12-31
OK.  I rebooted with my Xubuntu AMD 64 (Gusty) cd, chose my VGA of 1280x1024 using F4, and chose to 'recover the system'.  The framebuffer looked AWESOME - very crisp and tight!  I then went to the 'ash' command line, and the **cat /proc/cmdline** reported **vga=0x31b** - which is equivalent to vga=795.

I then followed the instructions from **i3dmaster** to change the **/boot/grub/menu.lst** file, then did the **update-grub** and it did change the kernel line and added **vga=0x31b** to the end of the line as expected.

I then rebooted normally, but did it not work!  :(  All I saw was a short line of magenta pixels.

Just taking a shot in the dark here, but I suspect that the the kernel that loads from the install CD is different from that on my hard drive and can accept the vga=0x31b option - while the other cannot.  Thoughts?

ANY help would be appreciated.

---

### Post by amohanty on 2008-04-26
I just posted something for this:
[http://ubuntuforums.org/showpost.php?p=4797563&postcount=13](http://ubuntuforums.org/showpost.php?p=4797563&postcount=13)

hth
am

---

### Post by mr_skater99 on 2009-07-02
I know this is an old thread - but thought i'd try anyway.

I now have a new LCD - that actually does 1920x1080, however when i run hwinfo this is what i get - 

02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.450]
  Unique ID: rdCR.Iu3tbmp2o4F
  Hardware Class: framebuffer
  Model: "NVIDIA G96 Board - 07290000"
  Vendor: "NVIDIA Corporation"
  Device: "G96 Board - 07290000"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xfb000000-0xfbdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown


No 1920x1080.  Anyone know what the code is for this res - at either 8,16 or 24 bits?  I can't find it anywhere...

Cheers.

---

### Post by netguy on 2009-08-02
The easiest way to find working framebuffer resolution codes is to append vga=0x9999 in GRUB and let kernel display a table of proper modes.

[Here]("http://www.firerouter.com/2009/07/28/high-resolution-console-in-linux/") is a complete guide for setting up console resolution.

---

