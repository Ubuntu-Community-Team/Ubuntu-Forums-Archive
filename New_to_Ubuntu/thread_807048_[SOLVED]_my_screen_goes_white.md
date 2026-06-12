---
title: "[SOLVED] my screen goes white"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by karlmp on 2008-05-25
my screen goes white so i have to press the quit button to get everything normal
screenshot:
[IMG]http://karlzt.angelfire.com/Screenshot.png[/IMG]

---

### Post by Joeb454 on 2008-05-25
There's no screenshot above ;)

And usually this is a compiz error, can you hit Alt+F2 (before it goes white) and type ```
metacity --replace
```

This should eliminate the error. Because it won't use compiz, what graphics card do you have?

---

### Post by karlmp on 2008-05-25
i don't have compiz, i completely dis-installed it using synaptic days ago.  

graphic card:
VGA compatible controller 
VIA technologies, inc. S3 Unichrome Pro VGA Adapter (rev 02)(prog-if 00 [VGA controller])
Subsystem:CLEVO/KAPOK Computer Unknown device 5402

i have metacity

graphics card (openchrome)

the screenshot lives at:[http://karlzt.angelfire.com/copy_of_Screenshot.png](http://karlzt.angelfire.com/copy_of_Screenshot.png)

---

### Post by karlmp on 2008-05-25
this is not the only problem that i have. When i go to screensaver it freezes, when i go to celestia i have to force the computer to shut down

---

### Post by unutbu on 2008-05-25
Perhaps there is a better driver for your video card.

Please post the output of 

```
sudo lshw -C video
```

---

### Post by karlmp on 2008-05-25
karl@ubuntu:~$ sudo lshw -C video
[sudo] password for karl: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: S3 Unichrome Pro VGA Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2

---

### Post by tim_wright on 2008-05-25
Have you enabled restriected drivers for your video card (if any)?

---

### Post by karlmp on 2008-05-25
no, i haven't

---

### Post by unutbu on 2008-05-25
Please post the output to 
```
cat /etc/X11/xorg.conf | grep -B2 -A10 Video
```

---

### Post by karlmp on 2008-05-25
karl@ubuntu:~$ cat /etc/X11/xorg.conf | grep -B2 -A10 Video

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by karlmp on 2008-05-25
another problem i didn't mention is that the resolution of the window login is too high, i only get the up left of the window

---

### Post by unutbu on 2008-05-25
First type 

```
locate via.ko
```

You should get a couple of lines of output. Look for a line that looks like this:
```

/lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/via.ko

```
via.ko is your video driver. If you don't have a line that looks like this, post a note and we'll think about what to do. Chances are good you have a line like the one above. If you do, then type
```

gksudo gedit /etc/X11/xorg.conf
```

A gedit text editing window should pop up. Change

```
Section "Device"
    Identifier "Configured Video Device"
EndSection
```

to 

```
Section "Device"
    Identifier "Configured Video Device"
    Driver "via"
EndSection
```

Now quit all your apps and log out, get back to the gdm login window. 
Now press CTRL-ALT-Backspace to restart the X server. Hopefully the X server will load the via driver.

Log back in. To check that the via driver has been loaded, type:

```
grep via /var/log/Xorg.0.log
```

Test if the white screen problem has gone away. If it doesn't work, post any error messages you see or the output of the commands suggested above.

---

### Post by karlmp on 2008-05-25
still happens


karl@ubuntu:~$ grep via /var/log/Xorg.0.log
(II) Module via: vendor="X.Org Foundation"
(II) [drm] loaded kernel module for "via" driver.
Fulfilled via DRI at 38952960

---

### Post by iaculallad on 2008-05-25
If you could hit the terminal with Ctrl+Alt+F1, try entering the command on the terminal:

Code:
> rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and try logging back with Ctrl+Alt+F7.

---

### Post by karlmp on 2008-05-26
thanks but i think that's a DANGEROUS COMMAND

---

### Post by LaRoza on 2008-05-26
> **iaculallad said:**
> If you could hit the terminal with Ctrl+Alt+F1, try entering the command on the terminal:


> **karlmp said:**
> thanks but i think that's a DANGEROUS COMMAND

It will only erase the settings and revert them back to default. You can always back them up if you want (mv them to a new directory for safe keeping) instead of deleting them.

---

### Post by unutbu on 2008-05-26
Please post 

```
cat /etc/X11/xorg.conf | perl -e "while (<STDIN>) {if (!(m/^#/)) {print}}"
```

Also, would you run 

```
sudo lshw -C video
```

again? I know adding the via driver to xorg.conf did not work, but I'd just like to know if the driver shows up in lshw output.

---

### Post by karlmp on 2008-05-26
```
karl@ubuntu:~$ cat /etc/X11/xorg.conf | perl -e "while (<STDIN>) {if (!(m/^#/)) {print}}"

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

karl@ubuntu:~$ sudo lshw -C video
[sudo] password for karl: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: S3 Unichrome Pro VGA Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2
```

---

### Post by unutbu on 2008-05-26
According to [http://ubuntuforums.org/showthread.php?t=806835](http://ubuntuforums.org/showthread.php?t=806835) (see Pumalite's post #4), when 

`lshw -C video` returns  
```

*-display UNCLAIMED
```

it means the kernel does not recognize your video card and therefore does not load the video driver module. 

To test that this is true, please post the output 
of 

```
lsmod | grep via
```

If you don't see anything, it means the via module has not been loaded by the kernel. Perhaps the fix then is to 
```

gksudo gedit /etc/modules
```

Add a line to the bottom which simply says
```
via
```

Also edit your /etc/X11/xorg.conf and add the
Driver "via" line again:

```
Section "Device"
    Identifier "Configured Video Device"
    **Driver "via"**
EndSection
```

Now reboot.
If the problem persists, run
```
dmesg | less
```
This is a desperation play because I hardly understand the output of dmesg, but if you find an error message that seems relevant, post it and perhaps someone will know something about it (or we can google it).

Also, click on the gnome panel menu: System>Administration>System Log and look for error messages there. (It wouldn't hurt to look in all of the files, but in particular, check /var/log/Xorg.0.log, /var/log/messages and /var/log/syslog.)

Again, post any relevant error messages here.

---

### Post by unutbu on 2008-05-26
Oops, hold on...

Your Monitor section should probably include HorizSync and VertRefresh lines:

```
Section "Monitor"
    Identifier     "Configured Monitor"
    HorizSync       ?? - ??
    VertRefresh     ?? - ??
EndSection

```

But BE CAREFUL! We need to find the right numbers for your laptop screen...

---

### Post by unutbu on 2008-05-26
Your /etc/X11/xorg.conf looks like the video sections are not configured at all.

Let's save a copy anyway so we can return to it just in case:
```

cd /etc/X11
sudo cp xorg.conf xorg.conf.bak
```

Now let's try to configure video by running

```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you questions regarding your video card and display resolution and such. When you quit that program your xorg.conf should be different. Reboot and see if the white screen problem goes away.

---

### Post by karlmp on 2008-05-26
karl@ubuntu:~$ lsmod | grep via
via                    43648  2 
drm                    82580  3 via
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
snd_mpu401_uart         9728  1 snd_via82xx
snd_via82xx_modem      16264  0 
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
snd_pcm                78596  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
via_ircc               27796  0 
irda                  203068  1 via_ircc
snd                    56996  19 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
i2c_viapro              9876  0 
i2c_core               24832  1 i2c_viapro
via_agp                11136  1 
agpgart                34760  2 drm,via_agp
pata_via               13316  2 
via_rhine              26632  0 
mii                     6400  1 via_rhine
libata                159344  3 pata_via,pata_acpi,ata_generic

---

### Post by gerben1 on 2008-05-26
I had a white screen too after today's upgrade, I do not know if you have the same problem as I had, but you might want to try to boot the previous kernel to see if that solves anything
see this thread: [http://ubuntuforums.org/showthread.php?t=808177](http://ubuntuforums.org/showthread.php?t=808177)

---

### Post by philinux on 2008-05-26
If he's running hardy there are no resolution settings in xorg.conf it is now a stub file.

---

### Post by karlmp on 2008-05-26
yes, I'm running hardy

---

### Post by karlmp on 2008-05-26
May 26 13:03:50 ubuntu kernel: [ 5378.969350] sd 3:0:0:0: [sdb] 501759 512-byte hardware sectors (257 MB)

---

### Post by karlmp on 2008-05-26
/var/log/syslog

```
May 26 10:23:11 ubuntu syslogd 1.5.0#1ubuntu1: restart.
May 26 10:23:11 ubuntu anacron[5522]: Job `cron.daily' terminated
May 26 10:23:11 ubuntu anacron[5522]: Normal exit (1 job run)
May 26 10:31:12 ubuntu kernel: [ 4051.206377] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16236 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 10:31:33 ubuntu kernel: [ 4082.405791] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=16237 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 10:43:08 ubuntu kernel: [ 5191.093117] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16308 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 10:46:33 ubuntu kernel: [ 5504.155045] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=16314 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 10:55:06 ubuntu kernel: [ 6431.474294] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16390 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 10:59:34 ubuntu kernel: [ 6832.870399] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16397 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 10:59:34 ubuntu kernel: [ 6833.839654] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16398 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 10:59:35 ubuntu kernel: [ 6834.823884] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16399 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 11:01:33 ubuntu kernel: [ 6996.500899] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=16420 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 11:07:03 ubuntu kernel: [ 7515.640890] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16426 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 11:16:33 ubuntu kernel: [ 8420.883750] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=16502 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 11:17:02 ubuntu /USR/SBIN/CRON[6712]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 26 11:19:02 ubuntu kernel: [ 8654.584291] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16503 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 11:30:14 ubuntu -- MARK --
May 26 11:31:04 ubuntu kernel: [ 9827.422375] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16584 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 11:31:21 ubuntu kernel: [ 9861.505467] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
May 26 11:31:21 ubuntu kernel: [ 9861.505485] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
May 26 11:31:21 ubuntu kernel: [ 9861.505494] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
May 26 11:31:33 ubuntu kernel: [ 9879.660630] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=16585 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 11:43:07 ubuntu kernel: [10987.550995] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16656 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 11:46:33 ubuntu kernel: [11318.364521] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=16662 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 11:55:06 ubuntu kernel: [12087.521367] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16738 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 11:59:43 ubuntu kernel: [12538.644857] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16745 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 11:59:44 ubuntu kernel: [12539.619576] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16746 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 11:59:45 ubuntu kernel: [12540.602407] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16747 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 12:01:33 ubuntu kernel: [12727.448853] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=16769 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 12:07:09 ubuntu kernel: [13244.030766] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16779 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 12:16:33 ubuntu kernel: [14144.306438] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=16921 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 12:17:02 ubuntu /USR/SBIN/CRON[6875]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 26 12:19:11 ubuntu kernel: [14391.753610] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=16927 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 12:30:14 ubuntu -- MARK --
May 26 12:31:11 ubuntu kernel: [15575.030941] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=17003 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 12:31:33 ubuntu kernel: [15603.649870] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=17004 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 12:43:09 ubuntu kernel: [16599.717620] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=17075 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 12:46:33 ubuntu kernel: [16884.731630] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=17086 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 12:55:12 ubuntu kernel: [17599.014661] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=17369 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 12:56:42 ubuntu kernel: [ 5057.699987] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17884 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 12:56:43 ubuntu kernel: [ 5058.214515] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17892 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 12:56:44 ubuntu kernel: [ 5058.961683] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17894 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 13:01:33 ubuntu kernel: [13708.564616] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=19123 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 13:07:11 ubuntu kernel: [18830.265559] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=21778 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 13:16:33 ubuntu kernel: [19618.234090] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=21887 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 13:17:01 ubuntu /USR/SBIN/CRON[6910]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 26 13:19:10 ubuntu kernel: [19824.221592] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=21904 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 13:30:14 ubuntu -- MARK --
May 26 13:31:10 ubuntu kernel: [20768.847398] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=22086 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 13:31:33 ubuntu kernel: [20800.187696] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=22087 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 13:43:10 ubuntu kernel: [21716.130558] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=22197 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 13:46:33 ubuntu kernel: [21982.424496] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=22217 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 13:47:08 ubuntu kernel: [22027.954561] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=22222 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 13:47:09 ubuntu kernel: [22028.938314] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=22223 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 13:47:10 ubuntu kernel: [22029.922534] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=22224 PROTO=UDP SPT=137 DPT=137 LEN=58 
May 26 13:55:12 ubuntu kernel: [22672.331583] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=22367 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 14:01:33 ubuntu kernel: [23172.717046] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=22395 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 14:07:12 ubuntu kernel: [ 6759.372143] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=22500 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 14:16:34 ubuntu kernel: [24593.907862] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=22598 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 14:17:02 ubuntu /USR/SBIN/CRON[6962]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 26 14:19:10 ubuntu kernel: [24846.760188] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=22623 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 14:30:14 ubuntu -- MARK --
May 26 14:31:08 ubuntu kernel: [25989.582837] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=22844 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 14:31:34 ubuntu kernel: [ 7425.404497] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=22845 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 14:43:10 ubuntu kernel: [27167.460479] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=22992 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 14:46:34 ubuntu kernel: [27541.667628] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=240 TOS=0x00 PREC=0x00 TTL=128 ID=22999 PROTO=UDP SPT=138 DPT=138 LEN=220 
May 26 14:52:18 ubuntu kernel: [28045.088404] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=23090 PROTO=UDP SPT=138 DPT=138 LEN=209 
May 26 14:52:19 ubuntu kernel: [28046.746541] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=23091 PROTO=UDP SPT=137 DPT=137 LEN=76 
May 26 14:52:21 ubuntu kernel: [28050.013366] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=23092 PROTO=UDP SPT=137 DPT=137 LEN=76 
May 26 14:52:21 ubuntu kernel: [28050.013850] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=23093 PROTO=UDP SPT=137 DPT=137 LEN=76 
May 26 14:52:21 ubuntu kernel: [28050.014311] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=23094 PROTO=UDP SPT=137 DPT=137 LEN=76 
May 26 14:52:21 ubuntu kernel: [28050.014775] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=23095 PROTO=UDP SPT=137 DPT=137 LEN=76 
May 26 14:52:21 ubuntu kernel: [28050.015228] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:4b:f5:04:f4:08:00 SRC=192.168.1.103 DST=192.168.1.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=23096 PROTO=UDP SPT=137 DPT=137 LEN=76
```

---

### Post by karlmp on 2008-05-26
hhh

---

### Post by philinux on 2008-05-26
Try setting you display using this.

gksu displayconfig-gtk

---

### Post by Primefalcon on 2008-05-26
try

```
sudo displayconfig-gtk
```

and select your graphics card and monitor from there

EDIT: nvm philinux beat me to what i was gonna say, trust him, that worked for me I was having a display problem recently myself

---

### Post by karlmp on 2008-05-28
i used the Screens and Graphics GUI, now everything is fixed Celestia works, when i go to screen saver it doesn't freeze, the resolution of the GDM login window is right, the screen doesn't go white (or at least it hasn't happened). But the quality is not the same as before is worse, and when i start Ubuntu after putting my name and password i get this message: 

There already appears to be an X server running on display :0. should another display number by tried? Answering no will cause GDM to attempt starting the server on :0 again.(you can change consoles by pressing ctrl-alt plus a function key, such as ctrl-alt-f7 to go to console 7. X servers usually run on consoles 7 and higher.)

<yes>               <no>

after pressing yes the other message appears:

the specified display number was busy, so this server was started on display :1
                                                          <ok>

then press ok and it starts.


```
karl@ubuntu:~$ sudo lshw -C video
[sudo] password for karl: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: S3 Unichrome Pro VGA Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2


```
```
karl@ubuntu:~$ cat /etc/X11/xorg.conf | perl -e "while (<STDIN>) {if (!(m/^#/)) {print}}"

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"OpenChrome"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"OpenChrome"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

```
karl@ubuntu:~$ grep vesa /var/log/Xorg.0.log
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
(II) VESA: driver for VESA chipsets: vesa
(--) Chipset vesa found

karl@ubuntu:~$ grep via /var/log/Xorg.0.log
karl@ubuntu:~$
```

---

### Post by unutbu on 2008-05-28
> **karlmp said:**
> i used the Screens and Graphics GUI, now everything is fixed Celestia works, when i go to screen saver it doesn't freeze, the resolution of the GDM login window is right, the screen doesn't go white (or at least it hasn't happened).

Wow, great!

> But the quality is not the same as before is worse, 
In what way is the quality worse? The graphics are probably not quick since you are using the vesa driver. I don't think we can fix that unless we can get the via driver working.

What happens if you simply replace "vesa" with "via" in xorg.conf?

> 
and when i start Ubuntu after putting my name and password i get this message: 

There already appears to be an X server running on display :0. 

Does this happen right after a reboot? If so, it sounds like some bootup script is running X before gdm. Hm. I'm not sure what could be causing this.

Do you have anything that might launch X in your /etc/rc.local, or ~/.profile?

---

### Post by unutbu on 2008-05-28
I've been googling around for a driver for "VIA technologies, inc. S3 Unichrome Pro VGA Adapter (rev 02)", and was eventually led to the package [xserver-xorg-video-openchrome]("http://packages.ubuntu.com/hardy/xserver-xorg-video-openchrome").
The link is for Hardy; if you are using a different version of Ubuntu, click on the appropriate version link near the top of the page.

To test if you have this package installed already, type
```
apt-cache policy xserver-xorg-video-openchrome
```

I was led to this package while poking around [http://www.openchrome.org/](http://www.openchrome.org/)
(then click on the link to binary packages). I think this is the appropriate package for you. 

This is the list of files it installs:

```
/usr/lib/xorg/modules/drivers/openchrome_drv.la
**/usr/lib/xorg/modules/drivers/openchrome_drv.so**
/usr/share/doc/xserver-xorg-video-openchrome/changelog.Debian.gz
/usr/share/doc/xserver-xorg-video-openchrome/copyright
/usr/share/man/man4/openchrome.4.gz
/usr/share/xserver-xorg/pci/openchrome.ids
```

So it appears the driver is called "openchrome".
When you install the package, it might automatically change your xorg.conf to say

```
    Driver         "openchrome"
```

If it does not, you'll need to edit xorg.conf manually. I suggest you try that and see what happens.

---

### Post by karlmp on 2008-05-28
i replaced "vesa" with "via". Now the screensavers are better but celestia won't run

> Does this happen right after a reboot? If so, it sounds like some bootup script is running X before gdm. Hm. I'm not sure what could be causing this.

yes it happens after reboot or starting the computer

> To test if you have this package installed already, type


karl@ubuntu:~$ apt-cache policy xserver-xorg-video-openchrome
xserver-xorg-video-openchrome:
  Installed: 1:0.2.901-0ubuntu4
  Candidate: 1:0.2.901-0ubuntu4
  Version table:
 *** 1:0.2.901-0ubuntu4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
        100 /var/lib/dpkg/status

---

### Post by karlmp on 2008-05-28
i went to synaptic, all the files you listed above are installed
what should i do? 
mark for reinstallation?

---

### Post by unutbu on 2008-05-28
```
gksu gedit /etc/X11/xorg.conf
```
Change
```

    Driver         "vesa"
```
to
```
    Driver         "openchrome"
```
Then reboot. 

Check to see the openchrome driver was loaded with no error messages:
```

grep openchrome /var/log/Xorg.0.log
```

---

### Post by unutbu on 2008-05-28
```
gksu gedit /etc/X11/xorg.conf
```
Change
```

    Driver         "vesa"
```
to
```
    Driver         "openchrome"
```
Then reboot. 

Check to see the openchrome driver was loaded with no error messages:
```

grep openchrome /var/log/Xorg.0.log
```

---

### Post by karlmp on 2008-05-28
karl@ubuntu:~$ grep openchrome /var/log/Xorg.0.log
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(!!) For support, refer to [http://www.openchrome.org/](http://www.openchrome.org/).

the GDM login window appeared twice: i had to put my name and password twice, the message: "There already appears to be an X server running on display :0." didn't appear, the session started normally then when i went to Celestia it didn't run, the screensaver made the white screen appear and crash the computer 
I had to press the power button

---

### Post by unutbu on 2008-05-28
I'm sorry karlmp, I'm really stumped. :(

---

### Post by karlmp on 2008-06-04
is this:[https://help.ubuntu.com/community/OpenChrome#head-61015b8de079166a76899b391e1dca3f843fa11d](https://help.ubuntu.com/community/OpenChrome#head-61015b8de079166a76899b391e1dca3f843fa11d) the solution?

---

### Post by unutbu on 2008-06-04
Well, on the one hand, those directions are for edgy or feisty, so they are a little old. I would think that those instructions would have been incorporated into later distributions so things would work out-of-the-box.

On the other hand, it wouldn't hurt to try.

---

### Post by karlmp on 2008-09-21
i reinstalled GDM and now is fixed

---

### Post by karlmp on 2008-11-14
thank you unutbu

[SIZE="7"]thank you all[/SIZE]

---

