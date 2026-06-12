---
title: "Ubuntu 14.04 Freezes"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by svt_raiden on 2014-04-29
Hi guys, 

My Ubuntu 14.04 freezes (hangs) all the time after 5 min use. 

Any help please?

---

### Post by LastDino on 2014-04-29
Please tell us more, starting with the configuration of your system

---

### Post by svt_raiden on 2014-04-29
Desktop System: 

Gigabyte Main Board
Intel i7 3rd Gen
16 GB Ram
ASUS Nvidia 590 GTX EVGA Classified (dual Core) 3GB VRAM 768 Bit
1st SSD 256 GB
2nd HDD 2 TB
DELL U2410 Monitor

I have setup as Dual Boot: Windows 7 Professional and Ubuntu

Partitions go as follows: 

0. the SSD is entirely for the C: of the windows (too small to split up)

the 2 TB drive is split as follows: 

1. 256 GB for / mount of the Ubuntu (Primary, Boot - contains the Grub as well)
2. swap partition
3. ~ 350 GB for the /home mount of Ubuntu (Primary Patition)
4. The rest of the HDD os for D: of the Windows (Logical partition)

I hope that helps. 

I will appreciate any information: 
- log files that I need to check out, 
- Actions to take
- research to make

Usually I start it, load Ubuntu and when open the first window (Browser or File Explorer) it lasts only few minutes and hangs (freezes). Won't even let me go to CTRL+ALT+F2 to use terminal and see from the CLI what is going on.

Any advice helps!

---

### Post by LastDino on 2014-04-30
Why have you assigned 256 GB for ''/''? Only 24 Max. is needed. 
Which drivers have you installed for GPU?

  System logs could be found in /var/log/*
Check ''/var/log/syslog''

Command line option >
tail -f /var/log/syslog

<
 Please have a look at them and let us know exact error you're getting.

---

### Post by svt_raiden on 2014-04-30
OK guys, 

here is the tail -f output from the /var/log/syslog file at the moment of crash.

Apr 30 18:39:25 svetoslav-Desktop kernel: [  876.521204] nouveau E[   PFIFO][0000:05:00.0] read fault at 0x40c0000000 [PT_NOT_PRESENT] from PGRAPH/CTXCTL on channel 0x005fb77000 [Xorg[1099]]
Apr 30 18:39:58 svetoslav-Desktop kernel: [  909.098438] nouveau E[     DRM] GPU lockup - switching to software fbcon
Apr 30 18:40:22 svetoslav-Desktop kernel: [  933.292161] nouveau E[Xorg[1099]] failed to idle channel 0xcccc0001 [Xorg[1099]]
Apr 30 18:40:37 svetoslav-Desktop kernel: [  948.299085] nouveau E[Xorg[1099]] failed to idle channel 0xcccc0001 [Xorg[1099]]
Apr 30 18:40:39 svetoslav-Desktop kernel: [  950.300308] nouveau E[   PFIFO][0000:05:00.0] playlist update failed
Apr 30 18:40:54 svetoslav-Desktop kernel: [  965.306932] nouveau E[Xorg[1099]] failed to idle channel 0xcccc0000 [Xorg[1099]]
Apr 30 18:41:09 svetoslav-Desktop kernel: [  980.313857] nouveau E[Xorg[1099]] failed to idle channel 0xcccc0000 [Xorg[1099]]
Apr 30 18:41:09 svetoslav-Desktop kernel: [  980.314067] nouveau W[   PFIFO][0000:05:00.0] INTR 0x00000100: 0x0000000d
Apr 30 18:41:11 svetoslav-Desktop kernel: [  982.314905] nouveau E[   PFIFO][0000:05:00.0] channel 2 [Xorg[1099]] kick timeout
Apr 30 18:41:11 svetoslav-Desktop kernel: [  982.315239] nouveau W[   PFIFO][0000:05:00.0] INTR 0x00000100: 0x0000000d
Apr 30 18:41:13 svetoslav-Desktop kernel: [  984.316075] nouveau E[   PFIFO][0000:05:00.0] playlist update failed
Apr 30 18:41:13 svetoslav-Desktop kernel: [  984.316163] nouveau W[   PFIFO][0000:05:00.0] INTR 0x00000001: 0x0000000b


I think it requires to install NVIDIA driver for this videocard. 
I went with the following NVIDIA Driver: 

[TABLE]
[TR]
[TD]Version[/TD]
                             [TD]331.67[/TD]
                            [/TR]
                            [TR]
                             [TD]Release Date[/TD]
                             [TD]Wed Apr 09, 2014[/TD]
                           [/TR]
	                            [TR]
                             [TD]Operating System[/TD]
                             [TD]Linux 64-bit[/TD]
                           [/TR]
                            [TR]
                             [TD]Language[/TD]
                             [TD]English (US)[/TD]
                           [/TR]
                                            [TR]
                             [TD]File Size[/TD]
                             [TD]57.44 MB[/TD]
[/TR]
[/TABLE]

So far runs good in X, just one problem. 
when in terminal xrandr -s <resolution> won't change the resolution. 
It says can't open display

Any help on that? 

Thank you again!

---

### Post by LastDino on 2014-05-01
Have you tried installing GUI front end and changing resolution? I don't have the same machine so I can't replicate the issue but I'm guessing. Try installing ''arandr'' from software center and see if it opens or not.

---

### Post by svt_raiden on 2014-05-01
I mean resolution when I start ubuntu with GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text" mode, will run straight in tty1

there i have low resolution and xrandr won't change the resolution. 

Can I set high resolution from some configuration file so it affects the TTY ?

---

### Post by LastDino on 2014-05-01
I haven't tested this (because I can't), but you can try
[http://ubuntuforums.org/showthread.php?t=2087827](http://ubuntuforums.org/showthread.php?t=2087827)

You should probably make different thread for that problem.

---

