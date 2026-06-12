---
title: "How-to: Ati 8.16.20 (easy Way)"
date: 2005-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by dcarpenter on 2005-10-14
I have seen several how to's on this subject matter and all of them involve several steps that are not important or not needed.  This is a simple way of getting 3d acceleration running in less than 2 minutes.

open up synaptic
search for fglrx
mark xorg-driver-fglrx for installation
mark fglrx-control for installation
apply changes

once the packages are installed, open a terminal

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo gedit /etc/X11/xorg.conf

in the gedit window, find the section "devices"
in this section you will see:
driver      "ati"
change the "ati" to "fglrx"
save

at this point you will want to restart x so either save all your open work and press CTRL ALT BACKSPACE or restart your computer. 

when you log back in open a console and type

fglrxinfo

you should see information about your ATI video card.  If you see something about MESA then you did something wrong.

If for some reason you can not start xorg after this then log in via command prompt and type sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf to restore you old xorg settings.

I hope this helps!

---

### Post by arpanaut on 2005-10-15
Thank You Very Much!
```

macbuntu@breezy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

macbuntu@breezy:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
22913 frames in 5.0 seconds = 4582.433 FPS
22881 frames in 5.0 seconds = 4576.098 FPS
22881 frames in 5.0 seconds = 4576.189 FPS
22882 frames in 5.0 seconds = 4576.347 FPS
22879 frames in 5.0 seconds = 4574.922 FPS
22889 frames in 5.0 seconds = 4577.761 FPS
22884 frames in 5.0 seconds = 4576.611 FPS
22886 frames in 5.0 seconds = 4577.093 FPS
22883 frames in 5.0 seconds = 4576.586 FPS
22884 frames in 5.0 seconds = 4576.698 FPS
22880 frames in 5.0 seconds = 4575.941 FPS
22882 frames in 5.0 seconds = 4576.330 FPS
22879 frames in 5.0 seconds = 4575.754 FPS
macbuntu@breezy:~$ fgl_glxgears
4177 frames in 5.0 seconds = 835.400 FPS
4512 frames in 5.0 seconds = 902.400 FPS
4551 frames in 5.0 seconds = 910.200 FPS
3574 frames in 5.0 seconds = 714.800 FPS
4531 frames in 5.0 seconds = 906.200 FPS
5042 frames in 5.0 seconds = 1008.400 FPS
5053 frames in 5.0 seconds = 1010.600 FPS
5049 frames in 5.0 seconds = 1009.800 FPS
5046 frames in 5.0 seconds = 1009.200 FPS
5050 frames in 5.0 seconds = 1010.000 FPS
5053 frames in 5.0 seconds = 1010.600 FPS
5076 frames in 5.0 seconds = 1015.200 FPS
4462 frames in 5.0 seconds = 892.400 FPS
macbuntu@breezy:~$
```

Running 9800Pro,  I couldn't get this driver working on the early release Previews, but now with everything updated it's running fine. 

On to working out sound issues.

Thanks Again! :cool:

---

### Post by duffydack on 2005-10-15
Dont u need to run fglrxconfig to get all the other "options" added to xorg.conf>

---

### Post by jamesford on 2005-10-15
how come full screen movies and other 2D jobs use waaaaaay more cpu after installing this ?
full screen movie b4 fglrx = 5% cpu
full screen movie after fglrx = 70 % cpu

athlon 2600+

---

### Post by bionnaki on 2005-10-15
my cpu is just fine for me.
...and 3d is working on my ati card.
thanks!

---

### Post by matthew on 2005-10-15
Worked perfectly for me the first time...this was TONS easier than getting fglrx drivers to work under Hoary.

---

### Post by JediPottsy on 2005-10-15
ive followed this, but when i do fglrxinfo i get this

jedipottsy@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

---

### Post by Adamal on 2005-10-15
[QUOTE=JediPottsy]ive followed this, but when i do fglrxinfo i get this

jedipottsy@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)[/QUOTE]

Same here.  I think there is something broken in the packages.

---

### Post by mlomker on 2005-10-15
> Same here.  I think there is something broken in the packages.

Could I get a couple of you to test something for me?  Everything worked out of the box on my machine, so I need some help figuring this out.

Does this file exist?

```

ls -l /etc/ld.so.conf

```

If so, what is in it?

```

cat /etc/ld.so.conf

```

If it doesn't exist then try these commands and post the output of the last one, at least.

```

sudo echo "/usr/X11R6/lib" >> /etc/ld.so.conf
sudo ldconfig
ldd /usr/bin/fglrxinfo

```

---

### Post by leezer3 on 2005-10-15
You two wouldn't be using Radeon9550 cards would you? From reading the other threads, seems the Radeon 9550s aren't working with the current drivers?

Cheers

-Leezer-

---

### Post by Adamal on 2005-10-15
[QUOTE=mlomker]Could I get a couple of you to test something for me?  Everything worked out of the box on my machine, so I need some help figuring this out.

Does this file exist?

```

ls -l /etc/ld.so.conf

```

If so, what is in it?

```

cat /etc/ld.so.conf

```

If it doesn't exist then try these commands and post the output of the last one, at least.

```

sudo echo "/usr/X11R6/lib" >> /etc/ld.so.conf
sudo ldconfig
ldd /usr/bin/fglrxinfo

```[/QUOTE]

I did not have the /etc/ld.so.conf file.  After running ```

sudo echo "/usr/X11R6/lib" >> /etc/ld.so.conf
sudo ldconfig
ldd /usr/bin/fglrxinfo

```  it still does not work.

I have a Radeon Mobility 9000 64MB.  Dell 600m

---

### Post by mlomker on 2005-10-15
```

cat /etc/ld.so.conf
ldd /usr/bin/fglrxinfo

```  
> 
it still does not work.


And you didn't give me the information that I asked for.  I've had about a dozen people give me the *it ain't working* response instead of the specific questions that I'm asking.  

My drivers already work...I'm *trying* to help.

---

### Post by Adamal on 2005-10-15
Sorry I missed that last line.  Here I hope this helps:
ldd /usr/bin/fglrxinfo
       >  linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7e72000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7db2000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7da4000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c76000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c64000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c61000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c5e000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c5a000)
        /lib/ld-linux.so.2 (0xb7f1e000)

---

### Post by mincho on 2005-10-15
does its work with ATI Radeon 9550 AGP Card. please check it and then tell me please.
                i am sick of ATI if this driver not install "correctly" i will go to buy nVidia GeForce 5700 256mb.. ](*,)
                       tha:KS :rolleyes: nks

---

### Post by mlomker on 2005-10-15
[QUOTE=mincho]does its work with ATI Radeon 9550 AGP Card.[/QUOTE]

All versions of the fglrx drivers support the card.  I've heard that a number of people are having trouble with the 9550 models right now, though.

---

### Post by blackwind747 on 2005-10-16
[quote=mlomker]Could I get a couple of you to test something for me? 

<snip>

```

sudo echo "/usr/X11R6/lib" >> /etc/ld.so.conf
sudo ldconfig
ldd /usr/bin/fglrxinfo

```[/quote] 

I tried this How-to and mine is still showing Mesa too. I have followed these steps suggested by mlomker and I did not have the ld.so.conf file. Here is my out put from ldd /usr/bin/fglrxinfo...

```

rickc@blackwind:/etc$ ldd /usr/bin/fglrxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7e66000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7da6000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7d98000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c6a000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c58000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c55000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c52000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c4e000)
        /lib/ld-linux.so.2 (0xb7f12000)

```

My card is a Radeon 9600 XT. Thanks for all your help.

Cheers
Rick

---

### Post by alex_esplin on 2005-10-16
I installed the fglrx driver, but when I restarted X, my widescreen resolution (1280x800) was gone.

I have a HP zt3000 laptop with 15.4" widescreen display and mobility radeon 9200.  

Anybody seen anything like this?  Or know how I could have 3D AND widescreen?  I don't remember having any problems in Hoary...

---

### Post by bionnaki on 2005-10-16
just thought I'd share my experiences with this How-To...

the first time I tried this, it worked 100% no problem.
I had to re-install breezy (long story) and I followed these instructions perfectly again, but they did not work. I got the MESA error after rebooting. So, I did a complete removal of the fglrx drivers & controls in synaptic and then reinstalled them - driver first, controls second. I edited the file again & retyped "fglrx" in place of "ati" (I literally retyped it). I rebooted and ran fglrxinfo and did the gear framerate test & everything was working again.

no idea what the cause of this is because I did the exact same thing both times. so, those who are getting an error, keep trying...

---

### Post by snoochems on 2005-10-16
I'm about to install Breazy.  (only got windows x64 running ATM)

I'll be dual booting.  THe reason why i'm only on windows ATM is that i could not get ATI drivers to work for my X800XT on hoary or pre-release breazy.

The thing is, will this' easy way' work for the 64 bit version?

---

### Post by mlomker on 2005-10-16
>  installed the fglrx driver, but when I restarted X, my widescreen resolution (1280x800) was gone

I do.  That's a bug in the 8.16.20 driver when used with certain monitors.  You'll have to try the [8.18.16]("http://ubuntuforums.org/showthread.php?p=411503"), which fixes that.

---

### Post by mlomker on 2005-10-16
> I had to re-install breezy (long story) and I followed these instructions perfectly again, but they did not work. 

I made an addition to [my how-to]("http://www.ubuntuforums.org/showthread.php?p=348911") for how to do a more complete removal and reinstall.  Let me know if it helps.

---

### Post by snoochems on 2005-10-16
I tried this method, and i just want to warn everyone that it doesn't work for AMD64.

---

### Post by alex_esplin on 2005-10-16
Thanks for the tutorial.  I've tried a couple of different ones in the last day or so](*,) , and it finally works.  Glxgears is in the 1400-1700 range, I still have 1280x800, and hibernate still works.  

Great Job:D

/edit/
Spoke much too soon.  Hibernate doesn't wake up, and the scrolling area on my touchpad doesn't work.  Is there a way to remove this and go back to the original setting that Breezy came with?

---

### Post by mlomker on 2005-10-16
> Spoke much too soon.  Hibernate doesn't wake up, and the scrolling area on my touchpad doesn't work.  Is there a way to remove this and go back to the original setting that Breezy came with?

Hibernation is known to not work with the fglrx drivers--ATI documents that on their website.  You have to choose between 3D and hibernation.  Personally, I go with powering the machine down when I'm done.

You can edit the /etc/X11/xorg.conf file to change the Driver line from **fglrx** to **ati** again.

---

### Post by mangoshake on 2005-10-16
Thank you very much for the simple instructions!

Only took about 5 minutes and it's working. :D

Edit: forgot to mention, I'm running 9800pro 128 here

---

### Post by kwaanens on 2005-10-18
Worked for me. At least I have no Mesa-stuff. But does this look OK?

> $ glxgears -iacknowledgethatthistoolisnotabenchmark
9513 frames in 5.0 seconds = 1902.559 FPS
10114 frames in 5.0 seconds = 2022.648 FPS
10112 frames in 5.0 seconds = 2022.345 FPS
10111 frames in 5.0 seconds = 2022.037 FPS
9766 frames in 5.0 seconds = 1953.139 FPS
10054 frames in 5.0 seconds = 2010.729 FPS
9919 frames in 5.0 seconds = 1983.722 FPS
9962 frames in 5.0 seconds = 1992.287 FPS
9861 frames in 5.0 seconds = 1972.096 FPS
9992 frames in 5.0 seconds = 1998.267 FPS
8728 frames in 5.2 seconds = 1666.016 FPS
9709 frames in 5.0 seconds = 1941.697 FPS
9358 frames in 5.0 seconds = 1871.548 FPS
9553 frames in 5.0 seconds = 1910.467 FPS
10091 frames in 5.0 seconds = 2018.024 FPS
6351 frames in 5.0 seconds = 1270.177 FPS
17349 frames in 5.0 seconds = 3469.761 FPS

Just wondering, as I have no idea about this stuff.
I'm sure it worked because ppenguinracer's graphics was all screwed up yesterday, but now it works.

Using Dell Inspiron 9300 with ATI X300 card if anyone wonders.

- Ketil

---

### Post by dcarpenter on 2005-10-18
Those numbers look pretty good for an x300.  I get about 4800 with a 9800xt 256mb.

---

### Post by kwaanens on 2005-11-07
If anyone's having trouble getting this to work, here's a little story. I had the whole ATI-thing fixed. But: Recently I tried moving from the 386 to 686-kernel.
Some time later I tried glxgears, and it sucked. I got the Mesa-stuff in fglrxinfo. 
So I open Synaptic and try searching for fglrx in "name and description". There it is: When putting in the 686-kernel, I forgot linux-restricted-modules-2.6.12-9-686. Installed this, rebooted: fglrxinfo again shows ATI.
Better yet, with 386 I got:
```
 $ glxgears -iacknowledgethatthistoolisnotabenchmark
9513 frames in 5.0 seconds = 1902.559 FPS
10114 frames in 5.0 seconds = 2022.648 FPS
10112 frames in 5.0 seconds = 2022.345 FPS
10111 frames in 5.0 seconds = 2022.037 FPS
```
Now I get:
```
$ glxgears -iacknowledgethatthistoolisnotabenchmark
13485 frames in 5.0 seconds = 2696.962 FPS
6562 frames in 5.6 seconds = 1172.599 FPS
14259 frames in 5.0 seconds = 2851.779 FPS
16402 frames in 5.0 seconds = 3280.226 FPS
17239 frames in 5.0 seconds = 3447.794 FPS
17239 frames in 5.0 seconds = 3447.756 FPS
17240 frames in 5.0 seconds = 3447.932 FPS
17240 frames in 5.0 seconds = 3447.872 FPS

```
Which I am guessing is much better.

- Ketil

---

### Post by ThomThom on 2005-11-12
Great! I tried some of the screensavers when I first had installed Ubuntu and quite a few of them where pretty slow. After I followed this howto it works like a charm! I got an ATI Radeon 9800 128MB.

---

### Post by ThomThom on 2005-11-12
btw, I tried that glxgears thingy.
does this look allright for my card?
```

19388 frames in 5.0 seconds = 3877.516 FPS
19401 frames in 5.0 seconds = 3880.061 FPS
19400 frames in 5.0 seconds = 3879.984 FPS
19399 frames in 5.0 seconds = 3879.637 FPS
19400 frames in 5.0 seconds = 3879.980 FPS
19399 frames in 5.0 seconds = 3879.724 FPS
19398 frames in 5.0 seconds = 3879.517 FPS

```

---

