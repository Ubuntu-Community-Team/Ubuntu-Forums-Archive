---
title: "No driver I use works with my nvidia NVS 130m"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by GusChavez on 2012-08-26
Using Ubuntu 12.04.1 LTS

I am fairly new to Ubuntu and really love it but this is the damnedest issue I have come across so far. I have a used Tecra A9 and using a nvidia NVS 130m card and ever driver I have installed via the built in software driver program as well as the driver I installed from nvidia themselves version 304.37 causes the same problem. On reboot I just get a black screen then sometimes the Ubuntu logo will flash then a flicker then back to black/dark purple screen. 

Now by the time I have written this I have tried everything I could find on the web to try and fix this. I held down a left shift button to access safe graphics mode and try and fix it from there. Sometimes it let me in sometimes not but was unable to fix it. I have suspected the drive was going so pulled it and am now running off a external HD with same issue. Everything runs great I can install Cinnamon, WINE, and any other app all I want. As soon as I try to install any graphics driver the issue I have described happens. I really want to get to work on this laptop! any help would be gladly received.

Forgive me its late. I left out how I tried to install the driver from Nvidia themselves. I used.
[LEFT]
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings[/LEFT]

---

### Post by bogan on 2012-08-26
Hi!, [B]GusChavez,
[/B]
The method you describe does not download the Nvidia>Downloads driver, but the xswat ubuntu version.

Is your graphics card a QUADRO NVS 130M, as the nvidia site does not have an entry for NVS130M except in the QUADRO series.

For that it does not reccomend a release driver only Beta drivers, where it lists 304.37 and 295.71. The QUADRO Notebook NVS 130M is shown as a 'Supported Product' in both.
[http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk)

Please Post:```
 lspci -nnk | grep -iA3 VGA # or, if no output:
 lspci -nnk | grep -iA3 nvidia
```You Posted:> I held down a left shift button to access safe graphics mode and try and fix it from thereDid you select [highlighyt] a ubuntu entry and press 'e' to edit the Linux line in the script, entering 'nomodeset' after 'quiet splash' and pressing Crtl+x to boot.??

Chao!, **bogan**.

---

### Post by GusChavez on 2012-08-26
Output was:

[B]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86M [Quadro NVS 130M] [10de:042a] (rev a1)
    Subsystem: Toshiba America Info Systems Device [1179:0002]
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb[/B]


I did not try  'nomodeset'  after 'quiet splash' and pressing Crtl+x to boot. I will try right now. The machine in question is dual booted now with Ubuntu 12.04 and pinguy OS 12. The ubuntu side has the current driver issue I left the Pinguy OS one untouched so I could post here. Why would all of the drivers suggested to me cause the same issues as the one I tried to get off Nvidia?

---

### Post by bogan on 2012-08-26
Hi!, **GusChavez**,

Right, I presume you ran the lspci cmd from the Pinguy install, but that confirms your card is a QUATRO,

Unfortunalely, I know zero about those, or how they may differ from other nvidia cards, so I am unable to answer your question, apart from the guess that it is a problem with the Xorg.conf file and you need to run the nvidia-config, after installing the driver, and renaming or backing-up the .conf file.

It is quite possible you do not have such a file at all, [ /etc/X11/xorg.conf ] as it is not always needed, for instance by the Nouveau driver you are currently using, presumably in the Pinguy OS installation.

Does your 'blackscreen' respond to pressing 'Crtl+Alt+F1' and give you a 'tty' Terminal Log-in prompt?

If so: Try running the lspci cmd from there, and also: ```
/usr/lib/nux/unity_support_test -p
``` both in that tty and in Pinguy to see if your graphics are capable of working OK; and Post the results here.

Chao!,** bogan**.

---

### Post by GusChavez on 2012-11-25
So a move out of my state a chance of jobs and a death in the family later I am here to answer the last question.

guschavez@Stormbreaker ~ $ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV86
OpenGL version string:  3.0 Mesa 9.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
guschavez@Stormbreaker ~ $ 

Running Linux Mint14 i was able to install drivers from the bumblebee project but it didnt seem to allow any better performance.

---

### Post by bogan on 2012-11-25
Hi!, **GusChavez**. Welcome back!

Please clarify if you ran the unity-test from Ubuntu or Pinguy, as it is clear the nvidia driver is not running there. As previously suggested please run it in both.

Similarly for 'lspci', and did you try editing the grub boot script to add 'nomodeset.?

Also please run in both:```
 sudo apt-cache policy nvidia-current
```Chao!**, bogan**.

---

