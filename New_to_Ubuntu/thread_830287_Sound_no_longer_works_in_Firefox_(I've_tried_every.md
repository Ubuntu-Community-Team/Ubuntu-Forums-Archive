---
title: "Sound no longer works in Firefox (I've tried everything)"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Psythik on 2008-06-15
I was watching flash vids the other day on Youtube, when suddenly, every other video I tried to watch crashed Firefox.  So I restarted my PC, and the next time it came up, the sound no longer worked in flash!

I've tried deleting my .mozilla profile, reinstalling flash, trying the free flash plugins, installing and removing all these different packages suggested in other topics, etc.  Nothing seems to work.  I don't remember everything I did in Synaptic, but I at least saved all the things I did in the terminal:

```
psythik@psythik-laptop:~$ sudo firefox
[sudo] password for psythik: 
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:7318): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7318): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7318): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7318): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7318): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7318): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
The application 'firefox' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
psythik@psythik-laptop:~$ cd /home/psythik/Desktop/
psythik@psythik-laptop:~/Desktop$ sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 112368 files and directories currently installed.)
Unpacking flashplugin-nonfree (from flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb) ...
Setting up flashplugin-nonfree (9.0.115.0ubuntu6~nolibflashsupport) ...
Downloading...
--12:10:44--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.138.70
Connecting to fpdownload.macromedia.com|72.247.138.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  294.70 KB/s
   50K .......... .......... .......... .......... ..........  3%  312.73 KB/s
  100K .......... .......... .......... .......... ..........  5%  188.67 KB/s
  150K .......... .......... .......... .......... ..........  6%  841.49 KB/s
  200K .......... .......... .......... .......... ..........  8%  312.33 KB/s
  250K .......... .......... .......... .......... .......... 10%  303.04 KB/s
  300K .......... .......... .......... .......... .......... 11%  313.56 KB/s
  350K .......... .......... .......... .......... .......... 13%  304.10 KB/s
  400K .......... .......... .......... .......... .......... 15%  311.92 KB/s
  450K .......... .......... .......... .......... .......... 16%  312.45 KB/s
  500K .......... .......... .......... .......... .......... 18%  304.10 KB/s
  550K .......... .......... .......... .......... .......... 20%  312.79 KB/s
  600K .......... .......... .......... .......... .......... 21%  312.46 KB/s
  650K .......... .......... .......... .......... .......... 23%  303.89 KB/s
  700K .......... .......... .......... .......... .......... 25%  312.76 KB/s
  750K .......... .......... .......... .......... .......... 26%  312.50 KB/s
  800K .......... .......... .......... .......... .......... 28%  303.94 KB/s
  850K .......... .......... .......... .......... .......... 30%  312.51 KB/s
  900K .......... .......... .......... .......... .......... 31%  304.10 KB/s
  950K .......... .......... .......... .......... .......... 33%  312.84 KB/s
 1000K .......... .......... .......... .......... .......... 35%  312.52 KB/s
 1050K .......... .......... .......... .......... .......... 36%  145.92 KB/s
 1100K .......... .......... .......... .......... .......... 38%   91.40 MB/s
 1150K .......... .......... .......... .......... .......... 40%  354.41 KB/s
 1200K .......... .......... .......... .......... .......... 42%  303.85 KB/s
 1250K .......... .......... .......... .......... .......... 43%  312.79 KB/s
 1300K .......... .......... .......... .......... .......... 45%  311.81 KB/s
 1350K .......... .......... .......... .......... .......... 47%  304.08 KB/s
 1400K .......... .......... .......... .......... .......... 48%  311.99 KB/s
 1450K .......... .......... .......... .......... .......... 50%  312.53 KB/s
 1500K .......... .......... .......... .......... .......... 52%  304.02 KB/s
 1550K .......... .......... .......... .......... .......... 53%  308.42 KB/s
 1600K .......... .......... .......... .......... .......... 55%  307.89 KB/s
 1650K .......... .......... .......... .......... .......... 57%  312.61 KB/s
 1700K .......... .......... .......... .......... .......... 58%  309.51 KB/s
 1750K .......... .......... .......... .......... .......... 60%  304.05 KB/s
 1800K .......... .......... .......... .......... .......... 62%  312.57 KB/s
 1850K .......... .......... .......... .......... .......... 63%  312.71 KB/s
 1900K .......... .......... .......... .......... .......... 65%  304.07 KB/s
 1950K .......... .......... .......... .......... .......... 67%  312.73 KB/s
 2000K .......... .......... .......... .......... .......... 68%  312.30 KB/s
 2050K .......... .......... .......... .......... .......... 70%  302.68 KB/s
 2100K .......... .......... .......... .......... .......... 72%  312.61 KB/s
 2150K .......... .......... .......... .......... .......... 73%  305.55 KB/s
 2200K .......... .......... .......... .......... .......... 75%  311.99 KB/s
 2250K .......... .......... .......... .......... .......... 77%  312.32 KB/s
 2300K .......... .......... .......... .......... .......... 79%  303.51 KB/s
 2350K .......... .......... .......... .......... .......... 80%  312.27 KB/s
 2400K .......... .......... .......... .......... .......... 82%  311.89 KB/s
 2450K .......... .......... .......... .......... .......... 84%  304.22 KB/s
 2500K .......... .......... .......... .......... .......... 85%  312.71 KB/s
 2550K .......... .......... .......... .......... .......... 87%  312.73 KB/s
 2600K .......... .......... .......... .......... .......... 89%  304.12 KB/s
 2650K .......... .......... .......... .......... .......... 90%  160.87 KB/s
 2700K .......... .......... .......... .......... .......... 92%    5.36 MB/s
 2750K .......... .......... .......... .......... .......... 94%  302.92 KB/s
 2800K .......... .......... .......... .......... .......... 95%  312.19 KB/s
 2850K .......... .......... .......... .......... .......... 97%  304.13 KB/s
 2900K .......... .......... .......... .......... .......... 99%  312.51 KB/s
 2950K .......... .......... ...                             100%  318.30 KB/s

12:10:54 (309.10 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

psythik@psythik-laptop:~/Desktop$ sudo apt-get remove libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libflashsupport
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 65.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112383 files and directories currently installed.)
Removing libflashsupport ...
psythik@psythik-laptop:~/Desktop$ 
psythik@psythik-laptop:~/Desktop$ 
psythik@psythik-laptop:~/Desktop$ 
psythik@psythik-laptop:~/Desktop$ 
psythik@psythik-laptop:~/Desktop$ wget http://launchpadlibrarian.net/13155153/flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb
--12:17:03--  http://launchpadlibrarian.net/13155153/flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb
           => `flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb.1'
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 18,414 (18K) [application/x-debian-package]

100%[====================================>] 18,414        50.82K/s             

12:17:04 (50.69 KB/s) - `flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb.1' saved [18414/18414]

psythik@psythik-laptop:~/Desktop$ sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb
(Reading database ... 112379 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.115.0ubuntu6~nolibflashsupport (using flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.115.0ubuntu6~nolibflashsupport) ...
Downloading...
--12:17:05--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.42.70
Connecting to fpdownload.macromedia.com|72.246.42.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  281.86 KB/s
   50K .......... .......... .......... .......... ..........  3%  312.26 KB/s
  100K .......... .......... .......... .......... ..........  5%  185.44 KB/s
  150K .......... .......... .......... .......... ..........  6%  911.82 KB/s
  200K .......... .......... .......... .......... ..........  8%  311.55 KB/s
  250K .......... .......... .......... .......... .......... 10%  304.04 KB/s
  300K .......... .......... .......... .......... .......... 11%  312.74 KB/s
  350K .......... .......... .......... .......... .......... 13%  303.83 KB/s
  400K .......... .......... .......... .......... .......... 15%  312.21 KB/s
  450K .......... .......... .......... .......... .......... 16%  312.58 KB/s
  500K .......... .......... .......... .......... .......... 18%  303.75 KB/s
  550K .......... .......... .......... .......... .......... 20%  312.37 KB/s
  600K .......... .......... .......... .......... .......... 21%  310.36 KB/s
  650K .......... .......... .......... .......... .......... 23%  302.66 KB/s
  700K .......... .......... .......... .......... .......... 25%  311.79 KB/s
  750K .......... .......... .......... .......... .......... 26%  312.65 KB/s
  800K .......... .......... .......... .......... .......... 28%  303.63 KB/s
  850K .......... .......... .......... .......... .......... 30%  312.75 KB/s
  900K .......... .......... .......... .......... .......... 31%  303.89 KB/s
  950K .......... .......... .......... .......... .......... 33%  312.86 KB/s
 1000K .......... .......... .......... .......... .......... 35%  312.49 KB/s
 1050K .......... .......... .......... .......... .......... 36%  304.13 KB/s
 1100K .......... .......... .......... .......... .......... 38%  266.37 KB/s
 1150K .......... .......... .......... .......... .......... 40%  378.77 KB/s
 1200K .......... .......... .......... .......... .......... 42%  303.75 KB/s
 1250K .......... .......... .......... .......... .......... 43%  311.23 KB/s
 1300K .......... .......... .......... .......... .......... 45%  311.59 KB/s
 1350K .......... .......... .......... .......... .......... 47%  304.44 KB/s
 1400K .......... .......... .......... .......... .......... 48%  311.48 KB/s
 1450K .......... .......... .......... .......... .......... 50%  312.55 KB/s
 1500K .......... .......... .......... .......... .......... 52%  303.04 KB/s
 1550K .......... .......... .......... .......... .......... 53%  309.96 KB/s
 1600K .......... .......... .......... .......... .......... 55%  303.81 KB/s
 1650K .......... .......... .......... .......... .......... 57%  312.01 KB/s
 1700K .......... .......... .......... .......... .......... 58%  312.73 KB/s
 1750K .......... .......... .......... .......... .......... 60%  303.64 KB/s
 1800K .......... .......... .......... .......... .......... 62%  312.25 KB/s
 1850K .......... .......... .......... .......... .......... 63%  312.75 KB/s
 1900K .......... .......... .......... .......... .......... 65%  304.04 KB/s
 1950K .......... .......... .......... .......... .......... 67%  312.32 KB/s
 2000K .......... .......... .......... .......... .......... 68%  312.45 KB/s
 2050K .......... .......... .......... .......... .......... 70%  304.10 KB/s
 2100K .......... .......... .......... .......... .......... 72%  311.75 KB/s
 2150K .......... .......... .......... .......... .......... 73%  232.46 KB/s
 2200K .......... .......... .......... .......... .......... 75%  439.27 KB/s
 2250K .......... .......... .......... .......... .......... 77%  312.51 KB/s
 2300K .......... .......... .......... .......... .......... 79%  303.45 KB/s
 2350K .......... .......... .......... .......... .......... 80%  312.81 KB/s
 2400K .......... .......... .......... .......... .......... 82%  312.86 KB/s
 2450K .......... .......... .......... .......... .......... 84%  303.98 KB/s
 2500K .......... .......... .......... .......... .......... 85%  312.57 KB/s
 2550K .......... .......... .......... .......... .......... 87%  312.21 KB/s
 2600K .......... .......... .......... .......... .......... 89%  304.10 KB/s
 2650K .......... .......... .......... .......... .......... 90%  312.78 KB/s
 2700K .......... .......... .......... .......... .......... 92%  312.28 KB/s
 2750K .......... .......... .......... .......... .......... 94%  303.99 KB/s
 2800K .......... .......... .......... .......... .......... 95%  312.54 KB/s
 2850K .......... .......... .......... .......... .......... 97%  303.85 KB/s
 2900K .......... .......... .......... .......... .......... 99%  312.14 KB/s
 2950K .......... .......... ...                             100%  322.49 KB/s

12:17:15 (308.59 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

psythik@psythik-laptop:~/Desktop$ sudo apt-get remove libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
psythik@psythik-laptop:~/Desktop$ mv ~/.mozilla ~/.mozilla.old
psythik@psythik-laptop:~/Desktop$ pulseconfig
bash: pulseconfig: command not found
psythik@psythik-laptop:~/Desktop$ yum remove pulseaudio* paman padevchooser libflashsupport
The program 'yum' is currently not installed.  You can install it by typing:
sudo apt-get install yum
bash: yum: command not found
psythik@psythik-laptop:~/Desktop$ libflash-mozplugin
bash: libflash-mozplugin: command not found
psythik@psythik-laptop:~/Desktop$ sudo apt-get libflash-mozplugin
[sudo] password for psythik: 
E: Invalid operation libflash-mozplugin
psythik@psythik-laptop:~/Desktop$ cd libflashsupport-1.2
bash: cd: libflashsupport-1.2: No such file or directory
psythik@psythik-laptop:~/Desktop$ cd /home/Psythik/libflashsupport-1.2/
bash: cd: /home/Psythik/libflashsupport-1.2/: No such file or directory
psythik@psythik-laptop:~/Desktop$ /home/psythik/libflashsupport-1.2
bash: /home/psythik/libflashsupport-1.2: is a directory
psythik@psythik-laptop:~/Desktop$ cd /home/psythik/libflashsupport1.2
bash: cd: /home/psythik/libflashsupport1.2: No such file or directory
psythik@psythik-laptop:~/Desktop$ cd /home/psythik/libflashsupport-1.2/
psythik@psythik-laptop:~/libflashsupport-1.2$ make sudoinstall
gcc -fPIC -shared -O2 -Wall -Werror  -lpthread -DLIBDIR=/usr/lib \
	-DALSA_INTERNAL  -DPULSEAUDIO -DLIBPULSEPATH='"/usr/lib/libpulse-simple.so.0"' -DESD -DLIBESDPATH='"/usr/lib/libesd.so.0"' \
	-DOSS -DOPENSSL -lssl  \
	flashsupport.c -o libflashsupport.so
flashsupport.c:225:17: error: esd.h: No such file or directory
flashsupport.c:290: error: expected ‘)’ before ‘format’
flashsupport.c: In function ‘FPX_SoundOutput_Detect’:
flashsupport.c:476: error: ‘FPX_esd_play_stream_fallback’ undeclared (first use in this function)
flashsupport.c:476: error: (Each undeclared identifier is reported only once
flashsupport.c:476: error: for each function it appears in.)
flashsupport.c: In function ‘ESD_FPX_SoundOutput_Open’:
flashsupport.c:1251: error: ‘ESD_DEFAULT_RATE’ undeclared (first use in this function)
flashsupport.c:1253: error: ‘ESD_BITS16’ undeclared (first use in this function)
flashsupport.c:1253: error: ‘ESD_STEREO’ undeclared (first use in this function)
flashsupport.c:1254: error: ‘ESD_STREAM’ undeclared (first use in this function)
flashsupport.c:1254: error: ‘ESD_PLAY’ undeclared (first use in this function)
flashsupport.c:1255: error: ‘esd_format_t’ undeclared (first use in this function)
flashsupport.c:1255: error: expected ‘;’ before ‘format’
flashsupport.c:1263: error: ‘format’ undeclared (first use in this function)
cc1: warnings being treated as errors
flashsupport.c:1271: warning: implicit declaration of function ‘FPX_esd_play_stream_fallback’
make: *** [libflashsupport.so] Error 1
psythik@psythik-laptop:~/libflashsupport-1.2$ 
psythik@psythik-laptop:~/libflashsupport-1.2$ sudo aptitude install alsa-oss
[sudo] password for psythik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information        
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libswfdec-0.6-90 
The following NEW packages will be installed:
  alsa-oss 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 52.6kB of archives. After unpacking 852kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com hardy/universe alsa-oss 1.0.15-1 [52.6kB]
Fetched 52.6kB in 1s (47.2kB/s)  
(Reading database ... 117077 files and directories currently installed.)
Removing libswfdec-0.6-90 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package alsa-oss.
(Reading database ... 117062 files and directories currently installed.)
Unpacking alsa-oss (from .../alsa-oss_1.0.15-1_i386.deb) ...
Setting up alsa-oss (1.0.15-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
psythik@psythik-laptop:~/libflashsupport-1.2$ sudo gedit /etc/firefox/firefoxrc
```

Also, I've noticed that system sounds no longer work either (but sound in Songbird works just fine), so maybe this is less of an issue with flash, and more of an issue with my PulseAudio ASLA sound drivers?  Maybe I can fix something from the PulseAudio config but I forgot how to get to it!

---

### Post by mevets on 2008-06-15
Yeah, I had pulseaudio problems on my computer. One work around is to change each dropdown under System > Preferences > Sound to ALSA

---

### Post by Psythik on 2008-06-15
But if I do that, I don't get sound in anything, let alone Firefox...

How do I get to the PulseAudio config?  I'm gonna play around with that until I either solve my problem or smash my PC with a hammer.

I cannot wait until I'm able to install Windows again.  Linux has been nothing but stress and frustration for me.

---

### Post by Psythik on 2008-06-16
Can anyone help me out?

---

### Post by Spainface on 2008-06-17
I'm having the same or similar problem. I found that opening system monitor and killing pulseaudio will give me back sound in firefox.  It's a pain in the *** though.... I've tried removing pulseaudio from my list of pre-loaded programs in my sessions but it didn't work.  Everything was fine until a few days ago and I have no idea what set this off.

thanks,

---

### Post by iaculallad on 2008-06-17
Close all open Firefox window and open your terminal:

```
 mv ~/.asoundrc .asoundrc.backup
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.backup
```

---

### Post by Psythik on 2008-06-17
> **Spainface said:**
> I'm having the same or similar problem. I found that opening system monitor and killing pulseaudio will give me back sound in firefox.  It's a pain in the *** though.... I've tried removing pulseaudio from my list of pre-loaded programs in my sessions but it didn't work.  Everything was fine until a few days ago and I have no idea what set this off.

thanks,I tried that but it didn't work for me...


> **iaculallad said:**
> Close all open Firefox window and open your terminal:

```
 mv ~/.asoundrc .asoundrc.backup
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.backup
``````
mv: cannot stat `/home/psythik/.asoundrc': No such file or directory
mv: cannot stat `/home/psythik/.asoundrc.asoundconf': No such file or directory
```:(


And again, how do I get to the PulseAudio config?

---

### Post by kansasnoob on 2008-06-17
I( know this sounds ridiculous, but I'm a gui guy and I always try the gui stuff first, have you tried just going to Synaptic and searching for pulseaudio, then just highlighting it and selecting "Mark For Reinstallation"?

There's a 10% chance that'll pull in all dependencies.

One other thing, while you're in Synaptic search gstreamer and install everything that begins with gstreamer, good, bad, ugly..... ALL gstreamer!

It may not work but it won't blow your computer up!

You might even try installing gnome-alsamixer which I've found sometimes plays better with some hardware.

---

