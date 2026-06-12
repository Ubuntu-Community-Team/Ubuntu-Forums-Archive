---
title: "How to stream mp3 to an airport express using only open source"
date: 2006-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by darkvad0r on 2006-06-09
First of all, all the credits go to Jon Lech Johansen, aka DVD Jon, who released JustePort, a tool which lets you stream MPEG4 Apple Lossless files and RAW audio files to your AirPort Express. More info in his blog: [http://nanocrew.net/index.php?s=justeport](http://nanocrew.net/index.php?s=justeport)
(He accepts donations ;) )

This is the only open source tool I've found to stream audio via wi-fi to the Airport Extreme base station.
[B]
What you can do with this How-to: [/B]
It's pretty basic, you can stream wirelessly single mp3 files or all the files in a given folder to your Airport Express base station (pretty basic AirTunes functionality). Hopefully this will inspire other people to make xmms/amarok/vlc plugins to accomplish more advanced functionalities.

**What you need:**
Mono: ```
sudo apt-get install mono mono-gmcs
```

JustePort.exe: Download JustePort-0.2.tar.gz from [http://nanocrew.net/sw/justeport/JustePort-0.2.tar.gz](http://nanocrew.net/sw/justeport/JustePort-0.2.tar.gz). Extract the contents somewhere, open a terminal, navigate to the folder you just extracted and compile JustePort with mono typing the following command:  ```
mcs -out:JustePort.exe *.cs
```
That will make a file named JustePort.exe that you'll have to move to /usr/bin/  to make it available as a shell command:
```
sudo cp JustePort.exe /usr/bin/
```

lame (free mp3 codec): If you're able to play mp3s chances are that you have it already installed, otherwhise type the following command in a terminal:
```
sudo apt-get install lame
```

**The command:**
Ok, once you're ready, you can type the following command in a terminal to play a single mp3 file (assuming the mp3 file is in the current directory and its name is file.mp3 and that the IP address of your airport express base station is 10.0.1.1):
```
lame --decode file.mp3 - | JustePort.exe - 10.0.1.1
```

On step further: to play all the mp3 files in a given folder, open the terminal, navigate to the folder containing the mp3s, and type the following command:
```
cat *.mp3 | lame --mp3input --decode - | JustePort.exe - 10.0.1.1
```
Note: you can simplify it a little bit by making an alias (for example, "playall"). Again, in a terminal type: ```
alias playall="cat *.mp3 | lame --mp3input --decode - | JustePort.exe - 10.0.1.1"
``` Now, to play all the mp3s in your current folder you just have to type playall.
EDIT: Aliases defined like this will be valid only for your current session (if you log out or reboot they disappear). If you want to make your alias permanent open the file .bashrc located in your home directory:```
gedit ~.bashrc
``` and add the alias to that file.

That's it for the moment, but you basically can stream any audio format if you have the right tool (for example, to stream ogg you'd type:  oggdec -Q -R -o - file.ogg | JustePort.exe - 10.0.1.1). Just try things and if they work post them here.

Again, **thanks to DVD Jon for making this possible**.

---

### Post by spanella47 on 2006-06-11
have you or anyone else tried raop-play.  
[http://raop-play.sourceforge.net/](http://raop-play.sourceforge.net/)

also, is anyone working on implimenting this functionality in rhythmbox/banshee/amarok

---

### Post by russbuss on 2006-06-20
[QUOTE=darkvad0r]Extract the contents somewhere, open a terminal, navigate to the folder you just extracted and compile JustePort with mono typing the following command:  ```
mcs -out:JustePort.exe *.cs
```[/QUOTE]

OK, so I got this far, but when I issue the above command, I get this:

```
mcs -out:JustePort.exe *.cs
bash: mcs: command not found
```

**UPDATE:**

The correct command to use is:

```
gmcs -out:JustePort.exe *.cs
```

Otherwise, this seems to be working like a charm.

THANKS!!!!

---

### Post by ltmon on 2006-06-20
[QUOTE=spanella47]have you or anyone else tried raop-play.  
[http://raop-play.sourceforge.net/](http://raop-play.sourceforge.net/)

also, is anyone working on implimenting this functionality in rhythmbox/banshee/amarok[/QUOTE]

I've tried raop-play, and it's a little lacking.

1. It buffers for 20 sec (!!!!) before sending to the airport.  That means and stop/play/pause/track change operations take 20 seconds to come through.

2. When not playing, but still running, it will continuosly flood the airport with empty packets.  Anyone sharing the airport with you might be a little annoyed at that :)

I'd like to know how well JustePort works compared to this.  I'll have to wait until I visit a friend with an Airport first.

L.

---

### Post by tpischke on 2006-10-07
This worked first try.  Impressive.  However there are a few flaws:

- Volume is VERY low.
- Music cuts out for ~1 second every 10 seconds, before resuming at the same spot.

Anyone else having issues like these?

---

### Post by darkvad0r on 2006-10-09
Well the volume can be set with the initial command. As I no longer have an Airport Extreme I don't remember how to do it, just check DVD Jon's website: [http://nanocrew.net/index.php?s=justeport](http://nanocrew.net/index.php?s=justeport)

As for the cuts everu 10 seconds I couldn't help you, I never experienced those.

Cheers

---

### Post by Jott on 2006-11-18
Hi - if anyone's still reading this thread, you should take a look at 

[http://www.jroller.com/page/nwinkler?entry=amarok_and_the_airport_express](http://www.jroller.com/page/nwinkler?entry=amarok_and_the_airport_express)

for a way to get raop-play to convince Amarok to stream music to the airport express.  I haven't tried it yet, but it might be fun if you've got the time or the desire.

---

### Post by greg.hagen on 2006-12-20
I tried the raop-play thing and it did work. Unfortunately, my laptop will now only play sound from one program at a time. I've tried an "apt-get --purge remove linux-sound-base alsa-base" followed by an install of those packages and it still didn't fix it. I wouldn't recommend installing it unless you like reinstalling ubuntu. Anyone else have this problem?

---

### Post by changuito on 2007-11-23
I've tried both methods in gutsy and failed miserably early on. Has anyone tried this in gutsy?

---

### Post by elamericano on 2008-01-02
Yes, Nils Winkler's howto still works, with a couple of caveats on Ubuntu 7.10. I will summarize the steps he has there:

1. Download raop-play source: [http://prdownloads.sourceforge.net/raop-play/raop_play-0.5.1.tar.gz?download]("http://prdownloads.sourceforge.net/raop-play/raop_play-0.5.1.tar.gz?download")

2. extract to a directory.

3. cd to the driver directory (e.g. raop_play-0.5.1/drivers/)

4. Download the patch for alsa_raoppcm.c: [http://sourceforge.net/tracker/download.php?group_id=119473&atid=684238&file_id=237676&aid=1756825]("http://sourceforge.net/tracker/download.php?group_id=119473&atid=684238&file_id=237676&aid=1756825")

5. Apply the patch with ```
patch -p0 < fix-typedefs.patch
```

6. Edit alsa_raoppcm.c and change #include <linux/config.h> to #include <linux/autoconf.h>

7. Install dependecies. I needed:
libssl-dev
libsamplerate0-dev
libfltk1.1
libfltk1.1-dev
libid3tag0-dev
fluid
libgtk2.0-dev
in addition to build-essential

*fluid is the tricky one, because ./configure won't tell you that it's missing but you'll get an error: aexcl_gui.cxx: No such file or directory.

8. Compile the driver:```
cd cd raop_play-0.5.1/drivers
./configure
make
sudo make install
```

9. Compile raop-play:```
cd raop_play-0.5.1
./configure
make
sudo make install
```

10. Create three scripts:
load_airport_express_driver```
#!/bin/sh
module=alsa_raoppcm
devnode=/tmp/pcmout
if ! grep "^$module" /proc/modules > /dev/null; then
    /sbin/modprobe alsa_raoppcm
fi
major=`sed -n -r "s/(^[0-9]+) pcmout/\\1/p" /proc/devices`
if [ -c $devnode ]; then
    rm -f $devnode;
fi
mknod $devnode c $major 0

```
start_airport_express```
#!/bin/bash
sudo load_airport_express_driver
raop_play airport /tmp/pcmout &
```
stop_airport_express```
#!/bin/bash
killall -9 raop_play
```
11. Make them executable with chmod +x and copy them to somewhere in your executable path, like /use/bin.

12. Type: ```
cat /proc/asound/cards
``` to get the number of your last sound card, and add 1 to know what raoppcm will be, or just run *start_airport_express* first. That will be the nuber to use for ALSA device configuration in Configure-Amarok->Engine->Configure Xine Engine->ALSA Device Configuiration->Mono and Stereo. In my case it was hw:2,0, since I had ): On-board sound and 2: Modem.

13. Append a line in /etc/hosts for 'airport':```
91.189.94.186    airport
``` Use the actual IP of your AirPort Express.

14. Run *sudo start_airport_express* after connecting to the network with your AirPort Express.

15. Play music via Amarok!

The sound is great, although you will notice an almost 10 second delay before it gets to your speaker. It's a welcome trade-off to not listen via headphones or the PC speaker. You don't have to connect directly to the AirPort express. Mine is configured as a station joined to my main wireless router. You could connect over ethernet too. Whatever works for you.

Many thanks to Shiro Ninomiya, and Nils Winkler

---

### Post by MurderCityDevil on 2008-01-23
Pardon me, but I'm a bit of a Linux newb.  I followed your directions exactly and I get the following when I run the start_airport_express script

> DBG: Audio-Jack-Status: connected; type=analog
DBG: CSeq: 2
DBG: Session: 809E3B40
DBG: Transport: RTP/AVP/TCP;unicast;interleaved=0-1;mode=record;server_port=6000
DBG: Audio-Jack-Status: connected; type=analog
DBG: CSeq: 3
DBG: Audio-Jack-Status: connected; type=analog
DBG: CSeq: 4
DBG: Audio-Jack-Status: connected; type=analog
connected
ERR: errror: auds_open


Not sure what the problem is.

---

### Post by elamericano on 2008-01-28
I'm not sure either. Maybe another computer was connected to your express when you ran it? I think it supports one connection only.

---

### Post by bensonious on 2008-02-05
Great thread guys, but I have one addition that will take this a step further. 

After following the second tutorial on this page to install raop_play alsa driver, install pulseaudio (there are plenty of tutorials online). This will let you send the audio of any app to your airport express, not just amorok.

One change that needs to be done is to add to following line

load-module module-alsa-sink device=hw:0,1

to /etc/pulse/default.pa

If you have any questions feel free to ask.

Ben

---

### Post by midtown on 2008-02-18
> **bensonious said:**
> Great thread guys, but I have one addition that will take this a step further. 

After following the second tutorial on this page to install raop_play alsa driver, install pulseaudio (there are plenty of tutorials online). This will let you send the audio of any app to your airport express, not just amorok.
Ben

Thanks, this sounds really cool! With pulseaudio integrated into Hardy hopefully this will be really easy to get to work with rhythmbox.

---

### Post by simoncullen on 2008-03-02
I use the raop_play alsa driver to stream my flac files to my Benchmark DAC1.  It usually works extremely well -- as well as any CD transport!  However I've just upgraded to the new development kernel from  Hardy "2.6.24-11-generic", and I can no longer load the driver.  [Edit: I'm using the 64bit Ubuntu, in case that's important]

raop_play -- including the essential alsa driver -- compiled and installed after applying the patch to the latest 0.5.1 release. 

When I try to load the driver I get this:

[INDENT]$ sudo sh driver_start
FATAL: Error inserting alsa_raoppcm (/lib/modules/2.6.24-11-generic/sound/alsa_raoppcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
mknod: missing operand after `0'
Try `mknod --help' for more information.[/INDENT]

here's the dmesg:

```

$ dmesg | grep alsa
[  322.098948] alsa_raoppcm: disagrees about version of symbol snd_pcm_new
[  322.098950] alsa_raoppcm: Unknown symbol snd_pcm_new
[  322.098994] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  322.098995] alsa_raoppcm: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  322.099029] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  322.099030] alsa_raoppcm: Unknown symbol snd_pcm_lib_malloc_pages
[  322.099043] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_ioctl
[  322.099043] alsa_raoppcm: Unknown symbol snd_pcm_lib_ioctl
[  322.099057] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_free_pages
[  322.099058] alsa_raoppcm: Unknown symbol snd_pcm_lib_free_pages
[  322.099071] alsa_raoppcm: disagrees about version of symbol snd_pcm_set_ops
[  322.099072] alsa_raoppcm: Unknown symbol snd_pcm_set_ops
[  322.099086] alsa_raoppcm: disagrees about version of symbol snd_pcm_period_elapsed
[  322.099087] alsa_raoppcm: Unknown symbol snd_pcm_period_elapsed
[  721.923178] alsa_raoppcm: disagrees about version of symbol snd_pcm_new
[  721.923181] alsa_raoppcm: Unknown symbol snd_pcm_new
[  721.923224] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  721.923225] alsa_raoppcm: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  721.923259] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  721.923260] alsa_raoppcm: Unknown symbol snd_pcm_lib_malloc_pages
[  721.923273] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_ioctl
[  721.923274] alsa_raoppcm: Unknown symbol snd_pcm_lib_ioctl
[  721.923287] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_free_pages
[  721.923288] alsa_raoppcm: Unknown symbol snd_pcm_lib_free_pages
[  721.923301] alsa_raoppcm: disagrees about version of symbol snd_pcm_set_ops
[  721.923302] alsa_raoppcm: Unknown symbol snd_pcm_set_ops
[  721.923316] alsa_raoppcm: disagrees about version of symbol snd_pcm_period_elapsed
[  721.923317] alsa_raoppcm: Unknown symbol snd_pcm_period_elapsed

```

And here's all the output from the compile/install:
```

[INDENT]
$ make
for i in rendezvous raop_play aexcl; do make -C $i; done
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/rendezvous'
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o mDNSPosix.o mDNSPosix.c
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o mDNSUNP.o mDNSUNP.c
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o ExampleClientApp.o ExampleClientApp.c
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o mDNS.o mDNS.c
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o Client.o Client.c
Client.c: In function 'main':
Client.c:333: warning: format '%ld' expects type 'long int', but argument 4 has type 'mStatus'
gcc  mDNSPosix.o mDNSUNP.o ExampleClientApp.o mDNS.o Client.o -o mDNSClient
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/rendezvous'
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/raop_play'
gcc -Wall -c raop_play.c -o raop_play.o
gcc -Wall -c raop_client.c -o raop_client.o
gcc -Wall -c rtsp_client.c -o rtsp_client.o
gcc -Wall -c aexcl_lib.c -o aexcl_lib.o
gcc -Wall -c base64.c -o base64.o
gcc -Wall -c aes.c -o aes.o
gcc -Wall -c m4a_stream.c -o m4a_stream.o
gcc -Wall -c audio_stream.c -o audio_stream.o
gcc -Wall -c wav_stream.c -o wav_stream.o
gcc -Wall -c mp3_stream.c -o mp3_stream.o
gcc -Wall -c flac_stream.c -o flac_stream.o
gcc -Wall -c ogg_stream.c -o ogg_stream.o
gcc -Wall -c aac_stream.c -o aac_stream.o
gcc -Wall -c pls_stream.c -o pls_stream.o
gcc -Wall -c pcm_stream.c -o pcm_stream.o
gcc -o raop_play  -lssl -lsamplerate -lid3tag raop_play.o raop_client.o rtsp_client.o aexcl_lib.o base64.o aes.o m4a_stream.o audio_stream.o wav_stream.o mp3_stream.o flac_stream.o ogg_stream.o aac_stream.o pls_stream.o pcm_stream.o
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/raop_play'
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/aexcl'
fluid -c aexcl_gui.fl
g++ -Wall -D_GNU_SOURCE -I../raop_play -I../rendezvous -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c aexcl_gui.cxx
g++ -Wall -D_GNU_SOURCE -I../raop_play -I../rendezvous -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c aexcl_play.cxx
aexcl_play.cxx: In function 'int play_next_song()':
aexcl_play.cxx:154: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx: In function 'int aex_contplay()':
aexcl_play.cxx:311: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx: In function 'int aex_pause()':
aexcl_play.cxx:341: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx: In function 'int main(int, char**)':
aexcl_play.cxx:436: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx:436: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx:436: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx:437: warning: deprecated conversion from string constant to 'char*'
g++ -Wall -D_GNU_SOURCE -I../raop_play -I../rendezvous -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c ipod_browser.cxx
gcc -Wall -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I../raop_play -DGLIB_SUBST -c ipod/itunesdb.c -o ipod/itunesdb.o
gcc -Wall -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I../raop_play -DGLIB_SUBST   -c -o ipod/glibsubst.o ipod/glibsubst.c
g++ -o aexcl_play  aexcl_gui.o aexcl_play.o ipod_browser.o ../raop_play/aexcl_lib.o ipod/itunesdb.o ipod/glibsubst.o -lfltk
rm aexcl_gui.cxx
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/aexcl'


$ sudo make install
for i in rendezvous raop_play aexcl; do make -C $i install; done
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/rendezvous'
/bin/bash ../mkinstalldirs /usr/local/bin/
install -s mDNSClient /usr/local/bin
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/rendezvous'
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/raop_play'
/bin/bash ../mkinstalldirs /usr/local/bin/
install -s raop_play /usr/local/bin
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/raop_play'
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/aexcl'
/bin/bash ../mkinstalldirs /usr/local/bin/
install -s aexcl_play /usr/local/bin
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/aexcl'[/INDENT]

And now the alsa driver:

[INDENT]
$ make
make -C /lib/modules/2.6.24-11-generic/build  SUBDIRS=/home/simon/Desktop/raop_play-0.5.1/drivers modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-11-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-11-generic'
simon@aristurtle:~/Desktop/raop_play-0.5.1/drivers$ sudo make install
install -d /lib/modules/2.6.24-11-generic/sound
cp -f alsa_raoppcm.ko /lib/modules/2.6.24-11-generic/sound || exit 1
strip -g /lib/modules/2.6.24-11-generic/sound/alsa_raoppcm.ko || exit 1
depmod
simon@aristurtle:~/Desktop/raop_play-0.5.1/drivers$ [/INDENT]

```

In case it's relevant, here are the kernel related packages I have installed:

```

$ apt-cache search 2.6.24
linux-image-2.6.24-11-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-restricted-modules-2.6.24-8-generic - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-common - Non-free Linux 2.6.24 modules helper script
linux-source-2.6.24 - Linux kernel source for version 2.6.24 with Ubuntu patches
linux-restricted-modules-2.6.24-11-generic - Non-free Linux 2.6.24 modules on x86/x86_64
linux-ubuntu-modules-2.6.24-11-generic - Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
linux-headers-2.6.24-11-generic - Linux kernel headers for version 2.6.24 on x86/x86_64
linux-image-2.6.24-8-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-headers-2.6.24-11 - Header files related to Linux kernel version 2.6.24
linux-ubuntu-modules-2.6.24-8-generic - Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64

```

Any help will be *really* appreciated (I have my new Sonus Faber speakers coming tomorrow and I'd really like to test them out!)


Thanks!

Simon

---

### Post by elamericano on 2008-03-24
This no longer works on Hardy (Beta)

I get these warnings during the build:
```
WARNING: "snd_pcm_lib_ioctl" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_pcm_period_elapsed" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_card_register" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_pcm_new" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_card_new" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
WARNING: "snd_card_free" [/home/kirby/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
```

after installing, sudo /sbin/modprobe alsa_raoppcm does not return.

Is this the end of the road for raop_play?

---

### Post by MTiN on 2008-03-24
same warnings here, and some errors too:
during make of raop_play
> make[1]: *** [ipod/glibsubst.o] Error 1
rm aexcl_gui.cxx
make[1]: Leaving directory `/home/mtin/Desktop/raop_play-0.5.1/aexcl'
make: *** [all] Error 2

during make install
> install -s aexcl_play /usr/local/bin
install: cannot stat `aexcl_play': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/mtin/Desktop/raop_play-0.5.1/aexcl'
make: *** [install] Error 2


and yeah its not working anymore....if I run the script, i just get > mtin@mtin-desktop:~$ start_ae
mknod: missing operand after `0'
Try `mknod --help' for more information.
mtin@mtin-desktop:~$
then, after a few seconds this appears and thats all:
> mtin@mtin-desktop:~$ start_ae
mknod: missing operand after `0'
Try `mknod --help' for more information.
mtin@mtin-desktop:~$ DBG: CSeq: 1
DBG: Apple-Response: AR/FD3MCvUGYdYToOb1CUT/FjXjXvXbJJQYQqk/UShLQMSz/4frt1mZ1Pn3K1q3JPqivz0JyrGAZ8IyviL2uSoa54BXx7WWscJdeHEh3CqwLdDpmy5XQsEpb0h3LGKy5oj5LAfhauDyo1sDpMKOpNyNva4qVPuZD6054xFej3zgjjJwb2Z2tSqjS/IRKfMB9/bz79zYl6eE6fDXVmyCIoEH0XF9zvTpu0ip8e3Ns9fIYT4ssiCtEohxeWvxWhkcDcQGLve1qQbSBdKTRfW0dXSBfWjjCegL9IUxwaYjl/Qdnpbcu1PcF/XmcTgPYXLgCQ/qW0XwZiiqvig39hezIzw
DBG: Audio-Jack-Status: connected; type=analog
DBG: CSeq: 2
DBG: Session: 80947B60
DBG: Transport: RTP/AVP/TCP;unicast;interleaved=0-1;mode=record;server_port=6000
DBG: Audio-Jack-Status: connected; type=analog
DBG: CSeq: 3
DBG: Audio-Jack-Status: connected; type=analog
DBG: CSeq: 4
DBG: Audio-Jack-Status: connected; type=analog
connected
ERR: errror: auds_open



so, well.....seems pretty broken...used to work with 7.10 before I upgraded to this damn beta  :)
:mad:
can anybody help here?
and another question, IF it would work again, would it be possible to route the whole system sound to the airport express via pulse audio? so that everything gets played there, expecially rhythmbox!? that would be so great *dream*.... :D

---

### Post by elamericano on 2008-03-24
I can compile by making this patch to aexcl/ipod/glibsubst.c:

```
--- ../raop_play-0.5.1-original/aexcl/ipod/glibsubst.c	2005-12-16 06:17:00.000000000 -0800
+++ aexcl/ipod/glibsubst.c	2008-03-24 11:31:24.000000000 -0700
@@ -32,12 +32,12 @@
 #include "aexcl_lib.h"
 
 
-inline gpointer g_malloc(gulong size)
+inline gpointer g_malloc(gsize size)
 {
 	return malloc(size);
 }
 
-inline gpointer g_malloc0(gulong size)
+inline gpointer g_malloc0(gsize size)
 {
 	gpointer p;
 	if((p=malloc(size))) memset(p,0,size);
```

but the bigger problem is that the module still doesn't load.

---

### Post by bzzzzz on 2008-03-29
This is the only open source tool I've found to stream audio via wi-fi to the Airport Extreme base station.
[B]
What you can do with this How-to: [/B]
It's pretty basic, you can stream wirelessly single mp3 files or all the files in a given folder to your Airport Express base station (pretty basic AirTunes functionality). Hopefully this will inspire other people to make xmms/amarok/vlc plugins to accomplish more advanced functionalities.

**What you need:**
Mono: ```
sudo apt-get install mono mono-gmcs
```

JustePort.exe: Download JustePort-0.2.tar.gz from [http://nanocrew.net/sw/justeport/JustePort-0.2.tar.gz](http://nanocrew.net/sw/justeport/JustePort-0.2.tar.gz). Extract the contents somewhere, open a terminal, navigate to the folder you just extracted and compile JustePort with mono typing the following command:  ```
mcs -out:JustePort.exe *.cs
```
That will make a file named JustePort.exe that you'll have to move to /usr/bin/  to make it available as a shell command:
```
sudo cp JustePort.exe /usr/bin/
```


I've been following the instructions above but get stuck when I try to move the JustePort.exe to the usr/bin/ because apparently I don't have the permission to copy the file into that folder.  

Any help much appreciated

---

### Post by simoncullen on 2008-03-29
> **bzzzzz said:**
> 

I've been following the instructions above but get stuck when I try to move the JustePort.exe to the usr/bin/ because apparently I don't have the permission to copy the file into that folder.  

Any help much appreciated

Are you sure your using "sudo"?  That should give you adequate permission to copy to the /usr/bin folder.  

Try:    sudo -s

And then just:   cp JustePort.exe /usr/bin


You can run the program without putting it in the /usr/bin directory.

Just run it with:   sudo ./JustePort.exe

---

### Post by gfunkdave on 2008-04-02
elamericano- Thanks a ton for this! I spent most of this morning trying to get this damn thing to work. I was shocked - shocked! - when my stereo speaker by my right ear started playing music.

But does anyone know why the audio output through the stereo is choppy for about 10 seconds when first starting to play it?

---

### Post by bzzzzz on 2008-04-02
I don't think I got it being choppy.

Is there anyway to have this working through a program like itunes?  I am very impressed with the way this apears to work.  Didn't have too much delay either.

---

### Post by gfunkdave on 2008-04-02
iTunes has this support built in. The Airport is designed to work with iTunes.

If you're on a Windows or Mac box, there's a $25 shareware program called Airfoil ([www.rogueamoeba.com](www.rogueamoeba.com)) that can capture the audio from any program and output it to an Airport on your network.

> **bzzzzz said:**
> I don't think I got it being choppy.

Is there anyway to have this working through a program like itunes?  I am very impressed with the way this apears to work.  Didn't have too much delay either.

---

### Post by bzzzzz on 2008-04-02
Yeah I can use that when I'm using xp, but how can I use it in ubuntu?

---

### Post by macLuntu on 2008-04-02
> **bzzzzz said:**
> Yeah I can use that when I'm using xp, but how can I use it in ubuntu?

You can install iTunes with wine. I just did it one hour ago on my iMac running Fedora :-)
It's working, but there are some issues. The screen goes black every time you start iTunes. GUI is very slow. If you have a large library to browse through making a mixed playlist takes time. I haven't tested importing cd's, and since I get an error message on launch regarding some registry values for importing/burning I wouldn't bet to much on this working.

But streaming to my airport express works perfectly, and this is much less hastle than raop_play (I think). If you are running a fw with you ubuntu installation you need to open port 5353 (udp) for iTunes to find your airport express basestation.

---

### Post by timredfern on 2008-04-28
I think I'm seeing this problem too.

When I compile raop_driver I'm seeing messages like this:

WARNING: "snd_pcm_lib_ioctl" [/home/tim/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!

WARNING: "snd_pcm_period_elapsed" [/home/tim/raop_play-0.5.1/drivers/alsa_raoppcm.ko] undefined!


And when I try to load the module it just hangs.

Ironically I decided to try this the day after I installed hardy!

There must be a workaround.. anyway... maybe I'll look into the diffciulty of turning the raop driver into a pulse sink... its not that long..

Tim

---

### Post by MTiN on 2008-05-05
please...someone capable should do something about this :(

an AirTunes pulseaudio-sink...holy ****...I'd instantly fall in love with you =P~

---

### Post by simoncullen on 2008-05-15
Are there any developments?  I'm still using vmware to stream with raop_play . . . It's a pain:

> **simoncullen said:**
> I use the raop_play alsa driver to stream my flac files to my Benchmark DAC1.  It usually works extremely well -- as well as any CD transport!  However I've just upgraded to the new development kernel from  Hardy "2.6.24-11-generic", and I can no longer load the driver.  [Edit: I'm using the 64bit Ubuntu, in case that's important]

raop_play -- including the essential alsa driver -- compiled and installed after applying the patch to the latest 0.5.1 release. 

When I try to load the driver I get this:

[INDENT]$ sudo sh driver_start
FATAL: Error inserting alsa_raoppcm (/lib/modules/2.6.24-11-generic/sound/alsa_raoppcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
mknod: missing operand after `0'
Try `mknod --help' for more information.[/INDENT]

here's the dmesg:

```

$ dmesg | grep alsa
[  322.098948] alsa_raoppcm: disagrees about version of symbol snd_pcm_new
[  322.098950] alsa_raoppcm: Unknown symbol snd_pcm_new
[  322.098994] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  322.098995] alsa_raoppcm: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  322.099029] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  322.099030] alsa_raoppcm: Unknown symbol snd_pcm_lib_malloc_pages
[  322.099043] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_ioctl
[  322.099043] alsa_raoppcm: Unknown symbol snd_pcm_lib_ioctl
[  322.099057] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_free_pages
[  322.099058] alsa_raoppcm: Unknown symbol snd_pcm_lib_free_pages
[  322.099071] alsa_raoppcm: disagrees about version of symbol snd_pcm_set_ops
[  322.099072] alsa_raoppcm: Unknown symbol snd_pcm_set_ops
[  322.099086] alsa_raoppcm: disagrees about version of symbol snd_pcm_period_elapsed
[  322.099087] alsa_raoppcm: Unknown symbol snd_pcm_period_elapsed
[  721.923178] alsa_raoppcm: disagrees about version of symbol snd_pcm_new
[  721.923181] alsa_raoppcm: Unknown symbol snd_pcm_new
[  721.923224] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  721.923225] alsa_raoppcm: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  721.923259] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  721.923260] alsa_raoppcm: Unknown symbol snd_pcm_lib_malloc_pages
[  721.923273] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_ioctl
[  721.923274] alsa_raoppcm: Unknown symbol snd_pcm_lib_ioctl
[  721.923287] alsa_raoppcm: disagrees about version of symbol snd_pcm_lib_free_pages
[  721.923288] alsa_raoppcm: Unknown symbol snd_pcm_lib_free_pages
[  721.923301] alsa_raoppcm: disagrees about version of symbol snd_pcm_set_ops
[  721.923302] alsa_raoppcm: Unknown symbol snd_pcm_set_ops
[  721.923316] alsa_raoppcm: disagrees about version of symbol snd_pcm_period_elapsed
[  721.923317] alsa_raoppcm: Unknown symbol snd_pcm_period_elapsed

```

And here's all the output from the compile/install:
```

[INDENT]
$ make
for i in rendezvous raop_play aexcl; do make -C $i; done
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/rendezvous'
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o mDNSPosix.o mDNSPosix.c
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o mDNSUNP.o mDNSUNP.c
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o ExampleClientApp.o ExampleClientApp.c
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o mDNS.o mDNS.c
gcc -Wall -DNOT_HAVE_SA_LEN   -c -o Client.o Client.c
Client.c: In function 'main':
Client.c:333: warning: format '%ld' expects type 'long int', but argument 4 has type 'mStatus'
gcc  mDNSPosix.o mDNSUNP.o ExampleClientApp.o mDNS.o Client.o -o mDNSClient
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/rendezvous'
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/raop_play'
gcc -Wall -c raop_play.c -o raop_play.o
gcc -Wall -c raop_client.c -o raop_client.o
gcc -Wall -c rtsp_client.c -o rtsp_client.o
gcc -Wall -c aexcl_lib.c -o aexcl_lib.o
gcc -Wall -c base64.c -o base64.o
gcc -Wall -c aes.c -o aes.o
gcc -Wall -c m4a_stream.c -o m4a_stream.o
gcc -Wall -c audio_stream.c -o audio_stream.o
gcc -Wall -c wav_stream.c -o wav_stream.o
gcc -Wall -c mp3_stream.c -o mp3_stream.o
gcc -Wall -c flac_stream.c -o flac_stream.o
gcc -Wall -c ogg_stream.c -o ogg_stream.o
gcc -Wall -c aac_stream.c -o aac_stream.o
gcc -Wall -c pls_stream.c -o pls_stream.o
gcc -Wall -c pcm_stream.c -o pcm_stream.o
gcc -o raop_play  -lssl -lsamplerate -lid3tag raop_play.o raop_client.o rtsp_client.o aexcl_lib.o base64.o aes.o m4a_stream.o audio_stream.o wav_stream.o mp3_stream.o flac_stream.o ogg_stream.o aac_stream.o pls_stream.o pcm_stream.o
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/raop_play'
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/aexcl'
fluid -c aexcl_gui.fl
g++ -Wall -D_GNU_SOURCE -I../raop_play -I../rendezvous -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c aexcl_gui.cxx
g++ -Wall -D_GNU_SOURCE -I../raop_play -I../rendezvous -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c aexcl_play.cxx
aexcl_play.cxx: In function 'int play_next_song()':
aexcl_play.cxx:154: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx: In function 'int aex_contplay()':
aexcl_play.cxx:311: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx: In function 'int aex_pause()':
aexcl_play.cxx:341: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx: In function 'int main(int, char**)':
aexcl_play.cxx:436: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx:436: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx:436: warning: deprecated conversion from string constant to 'char*'
aexcl_play.cxx:437: warning: deprecated conversion from string constant to 'char*'
g++ -Wall -D_GNU_SOURCE -I../raop_play -I../rendezvous -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c ipod_browser.cxx
gcc -Wall -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I../raop_play -DGLIB_SUBST -c ipod/itunesdb.c -o ipod/itunesdb.o
gcc -Wall -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I../raop_play -DGLIB_SUBST   -c -o ipod/glibsubst.o ipod/glibsubst.c
g++ -o aexcl_play  aexcl_gui.o aexcl_play.o ipod_browser.o ../raop_play/aexcl_lib.o ipod/itunesdb.o ipod/glibsubst.o -lfltk
rm aexcl_gui.cxx
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/aexcl'


$ sudo make install
for i in rendezvous raop_play aexcl; do make -C $i install; done
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/rendezvous'
/bin/bash ../mkinstalldirs /usr/local/bin/
install -s mDNSClient /usr/local/bin
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/rendezvous'
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/raop_play'
/bin/bash ../mkinstalldirs /usr/local/bin/
install -s raop_play /usr/local/bin
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/raop_play'
make[1]: Entering directory `/home/simon/Desktop/raop_play-0.5.1/aexcl'
/bin/bash ../mkinstalldirs /usr/local/bin/
install -s aexcl_play /usr/local/bin
make[1]: Leaving directory `/home/simon/Desktop/raop_play-0.5.1/aexcl'[/INDENT]

And now the alsa driver:

[INDENT]
$ make
make -C /lib/modules/2.6.24-11-generic/build  SUBDIRS=/home/simon/Desktop/raop_play-0.5.1/drivers modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-11-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-11-generic'
simon@aristurtle:~/Desktop/raop_play-0.5.1/drivers$ sudo make install
install -d /lib/modules/2.6.24-11-generic/sound
cp -f alsa_raoppcm.ko /lib/modules/2.6.24-11-generic/sound || exit 1
strip -g /lib/modules/2.6.24-11-generic/sound/alsa_raoppcm.ko || exit 1
depmod
simon@aristurtle:~/Desktop/raop_play-0.5.1/drivers$ [/INDENT]

```

In case it's relevant, here are the kernel related packages I have installed:

```

$ apt-cache search 2.6.24
linux-image-2.6.24-11-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-restricted-modules-2.6.24-8-generic - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-common - Non-free Linux 2.6.24 modules helper script
linux-source-2.6.24 - Linux kernel source for version 2.6.24 with Ubuntu patches
linux-restricted-modules-2.6.24-11-generic - Non-free Linux 2.6.24 modules on x86/x86_64
linux-ubuntu-modules-2.6.24-11-generic - Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
linux-headers-2.6.24-11-generic - Linux kernel headers for version 2.6.24 on x86/x86_64
linux-image-2.6.24-8-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-headers-2.6.24-11 - Header files related to Linux kernel version 2.6.24
linux-ubuntu-modules-2.6.24-8-generic - Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64

```

Any help will be *really* appreciated (I have my new Sonus Faber speakers coming tomorrow and I'd really like to test them out!)


Thanks!

Simon

---

### Post by Halsnalle on 2008-05-24
So, if I understand this thread correctly; if I want to have the same basic functionality to stream music to my Airport Express from Hardy & Amarok (or equivalent) as I have in Mac OS X & Itunes, I'm out of luck?

Switching to Ubuntu on my MacBook Pro has almost felt like an upgrade, and this is sort of the last thing I need to fix to run Ubuntu full time.

---

### Post by simoncullen on 2008-05-24
Yes, unfortunately.  You can install a lightweight virtual machine running e.g. Xubuntu to stream from Amarok.  Other than that, there are currently no options that I'm aware of.  If you only use iTunes supported formats (e.g., aac, mp3), then you should run a supported version of itunes + airtunes using wine.  I've heard of people having some success with this.  

Even when raop_play is working, it's still a less than optimal solution, and I'm surprised there hasn't been work on a more 'polished' system.  Perhaps the demand for it isn't as great as I imagine -- but as more people upgrade to Hardy there will be more people with this problem.  So I'm still hopeful that there'll be a fix or some new development.

If itunes would play flac (and read its tags) I'd play around with wine.   

Simon 

> **Halsnalle said:**
> So, if I understand this thread correctly; if I want to have the same basic functionality to stream music to my Airport Express from Hardy & Amarok (or equivalent) as I have in Mac OS X & Itunes, I'm out of luck?

Switching to Ubuntu on my MacBook Pro has almost felt like an upgrade, and this is sort of the last thing I need to fix to run Ubuntu full time.

---

### Post by nwinkler on 2008-05-26
Hi,

I'm the maintainer of RAOP-PLAY, I registered here to comment on this thread :-) Personally, I'm running Fedora, which is working great with RAOP-PLAY, BTW.

Here's a couple of comments:
[LIST]
[*]If you want to get this thing working, your help is greatly appreciated. You can help with testing, bug reports, patches or documentation. It would be great if someone could restructure the web site of the project, no programming skills required!
[*]If you have patches, like the one posted here in this thread for the Glib fix, it would be great if you add it to the patch section on the project's SourceForge page. I found the patch in this thread by accident and applied it to the code, but it would be easier if people would submit patches directly.
[*]The problem people are experiencing here is directly related to the Hardy kernel from what I can see. I have installed the brand new Fedora 9 in a virtual machine, it also has the 2.6.25 kernel, it also has the new ALSA version, and RAOP-PLAY works without problems.
[*]As you can see from the build logs posted in this thread, there aren't any compilation problems, all the right header files are used - and there aren't any incompatibilities with the used functions. The problems start when the module is loaded into the kernel, the messages indicate that the required libraries are not present in the kernel. This is a problem of the kernel, it's not something that can be fixed in the RAOP-PLAY code. If someone would be willing to compile a custom kernel, this would help a lot. Here's a bug on the Ubuntu launchpad outlining something similar (long!): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338)
Not sure if this related, but one of the last comments suggests installing some additional packages, maybe this helps: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/150)
It might be a good idea to create a bug entry in Launchpad outlining the problems you are experiencing here. Maybe someone from the Ubuntu kernel team can describe what the problem with the Ubuntu kernel is (and why it exists) and how to fix it.
[/LIST]

Please let me know if you have any comments or suggestions, I depend on your input ...

Nils

---

### Post by simoncullen on 2008-05-26
Thanks, Nils!  I can report that all of the packages listed on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/150) are installed, and the bug persists.  I'm running Hardy's kernel 2.6.24-16-generic, but I'm still using Gutsy.

Cheers,
Simon

---

### Post by nwinkler on 2008-05-27
> **simoncullen said:**
> Thanks, Nils!  I can report that all of the packages listed on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/150) are installed, and the bug persists.  I'm running Hardy's kernel 2.6.24-16-generic, but I'm still using Gutsy.
Hi Simon, thanks for confirming this. As I said, there isn't much I could do about this right now. If someone is willing, a custom kernel compile would probably help in identifying which modules are missing in Hardy - but this is not for the faint of heart. Maybe it would be best to file a bug in Launchpad - if you do so, please post a link here, I'm interested in seeing how this progresses.

Thanks,

Nils

---

### Post by ant1060 on 2008-05-29
Hi Simon,
Returning to Nils' idea of filing a bug in Launchpad in order to get this problems sorted, do you know how to do that?  I don't unfortunately so was hoping you might be able to help the whole community out here!!!!
Thanks in advance!
Ant

---

### Post by simoncullen on 2008-06-05
Hi Ant,

I'd be happy to do so.  Anyone can here: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

Perhaps we can decide on the best description of the bug here, before filing it in Launchpad?  (Nils might be able to help with this.)

Pinpointing the problem in our description could make fixing it considerably quicker!

Cheers,
Simon


> **ant1060 said:**
> Hi Simon,
Returning to Nils' idea of filing a bug in Launchpad in order to get this problems sorted, do you know how to do that?  I don't unfortunately so was hoping you might be able to help the whole community out here!!!!
Thanks in advance!
Ant

---

### Post by ant1060 on 2008-06-05
Hi Simon,
Thanks for replying!
Yes - my problem is knowing how to formulate what is wrong.... I had hoped that with the latest update to the kernel (now 2.6.24-18) that the difficulties would be solved.  I reapplied the patch that Nils made, but still I am left with warnings, the last of which is mknod: missing operand after '0'.
Best wishes from Brussels,
Ant

---

### Post by ant1060 on 2008-06-05
Sorry- that should say the kernel is 2.6.24-18 :)

---

### Post by simoncullen on 2008-06-06
No worries!

I'll post a draft in the next few days.

Simon

> **ant1060 said:**
> Hi Simon,
Thanks for replying!
Yes - my problem is knowing how to formulate what is wrong.... I had hoped that with the latest update to the kernel (now 2.6.24-18) that the difficulties would be solved.  I reapplied the patch that Nils made, but still I am left with warnings, the last of which is mknod: missing operand after '0'.
Best wishes from Brussels,
Ant

---

### Post by ant1060 on 2008-06-27
Hi Simon,
Were you able to post your bug report?
Regards from Brussels,
Ant

---

### Post by Kenzy on 2008-08-06
Well hello there eveyone, I just did a fresh install of Hardy on my laptop and started to pull things together. And guess what - i bumbed into this same problem, no way to stream anything to the Airport, damn it! It would be SUPERB to find a solution to this problem since the guys have already made the way for the raop_play, and it's a pity that it refuses to work under Hardy. I'm running kernel 2.6.24-19 and the problems still remain.

I can't even get the JustePort.exe working, and I really don't know what's going on - I downloaded the sources, used mcs to make the .exe- file and got some warnings like:
```

JustePort-0.2$ mcs -out:JustePort.exe *.cs
MP4.cs(299,18): warning CS0169: The private method `MP4Box.ParseSTSD(System.IO.BinaryReader)' is never used
MP4.cs(305,18): warning CS0169: The private method `MP4Box.ParseMP4A(System.IO.BinaryReader)' is never used
MP4.cs(310,18): warning CS0169: The private method `MP4Box.ParseDRMS(System.IO.BinaryReader)' is never used
MP4.cs(315,18): warning CS0169: The private method `MP4Box.ParseALAC(System.IO.BinaryReader)' is never used
MP4.cs(341,18): warning CS0169: The private method `MP4Box.ParseSTSZ(System.IO.BinaryReader)' is never used
MP4.cs(363,18): warning CS0169: The private method `MP4Box.ParseSTCO(System.IO.BinaryReader)' is never used
MP4.cs(382,18): warning CS0169: The private method `MP4Box.ParseSTSC(System.IO.BinaryReader)' is never used
MP4.cs(409,18): warning CS0169: The private method `MP4Box.ParseMETA(System.IO.BinaryReader)' is never used
MP4.cs(465,18): warning CS0169: The private method `MP4Box.WriteBytesSTSZ(System.IO.MemoryStream)' is never used
MP4.cs(487,18): warning CS0169: The private method `MP4Box.WriteBytesSTCO(System.IO.MemoryStream)' is never used
MP4.cs(506,18): warning CS0169: The private method `MP4Box.WriteBytesSTSC(System.IO.MemoryStream)' is never used
```

And trying sudo ./JustePort.exe gives "sudo: unable to execute ./JustePort.exe: Permission denied" - error. 

I got the raop_play compiled, as well as I got the driver too, but loading the driver fails. I get the same error as the others "mknod: missing operand after `0' Try `mknod --help' for more information. " when I try to load the airport driver. The aecxl_play doesn't work, it connects to the Airport, finds it and gets the plug information, but disconnects right after I've pressed the play-button. 

Guys, help us :)

Janne, Finland

EDIT: Wow, I have to take some of the text back, since I installed libstdc++5 and mpg321 packages and got aexcl_play working. I compiled the raop_play and the driver again after installing those two packages and it surprisingly did the trick. However the sound devices look like this:
```
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x78540000 irq 16

``` So the raop_play driver doesn't load.

---

### Post by ant1060 on 2008-08-12
Hi Janne,
I am sorry to see that nothing has happened to unblock the situation : I too would love to get my music streaming again!
Have you asked Nils Winkler specifically about your problem? [http://www.jroller.com/nwinkler/](http://www.jroller.com/nwinkler/)
Best wishes,
Ant

---

### Post by Kenzy on 2008-08-13
Hi,

Nice to see that someone's paying attention to this thread also. No, I haven't asked him about this problem, and I feel that I don't even have to since he can do nothing with this problem as he claims that the problem remains in the Ubuntu's kernel. Well, I have to acquiesce to stream music with iTunes over Crossover Office, at least it works properly :)

---

### Post by kronepils on 2008-08-24
I have also tried using iTunes through wine to get it working. But I'm having troubles installing.
How did you succeed?? Which version?


Thanks

---

### Post by nwinkler on 2008-08-25
Hi,

there are some hints in these bug reports here:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/201098](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/201098)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204578](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204578)

Apparently the only way to fix it is to a) recompile your kernel (described in one of the bug reports) or b) install a Debian kernel that has the correct version of ALSA (also described in one of the linked pages)

Hope that helps a bit,

Nils

---

### Post by Kenzy on 2008-08-31
> **kronepils said:**
> I have also tried using iTunes through wine to get it working. But I'm having troubles installing.
How did you succeed?? Which version?


Thanks

Well first I downloaded iTunes version 6.01 from [http://www.oldapps.com/itunes.htm](http://www.oldapps.com/itunes.htm) - site. I have the Crossover Office ver. 6 and I installed iTunes+Quicktime via the Crossover, and it works. Don't download the 7-version or above, because they won't work. The 6.01 works perfectly and finds the Airport nicely, although I have to put the terminal to ping the Airport before I start the iTunes.

EDIT: In fact, the easiest and the best way to do that is just install the Crossover Office Pro ver. 6, beause the iTunes+Quicktime-option is available in the supported software-list. It isn't there anymore in the 7-version of Crossover, and the iTunes version in CO 6 is 4. Works like a charm.

---

### Post by oliwally on 2008-09-08
Hi all,

I just bought an Airport Express and was eager to make it work Kubuntu 8.04 - Hardy. Although this thread suggest that this is really tricky, I've had excellent and easy success by installing Raop-Play using the instructions found at [http://raop-play.sourceforge.net/](http://raop-play.sourceforge.net/). After installing some of the dependencies needed (as listed in the instructions) it all worked well and I was able to stream audio to the Airport Express, virtually no lag, with the only prob being the volume control being quite touchy but workable. Cool stuff! I was so impressed!

I've had no luck following the instructions found in this thread to use Amarok to stream to the airport. I'm getting all sorts of errors, mainly during 'make' and 'make install', telling me that somehow there is no make file, or something like that.

I also read post on installing itunes in wine. Not a problem - installed and locally played audio from the computer's speakers. However, I cannot convince itunes to 'see' the airport express. I've read quite a few post saying that it should work well, but I'm having no luck.

How do I configure itunes to 'see' my airport express?

Thanks everyone for working on this. My mac-dedicated friends are very impressed that streaming to airport works in linux.

---

### Post by Burnout on 2008-10-16
Hello, is there a solution for loading the alsa driver please?

The load_airport_express_driver seems to fail on this line -> major=`sed -n -r "s/(^[0-9]+) pcmout/\\1/p" /proc/devices`

When I'm executing "sed -n -r "s/(^[0-9]+) pcmout/\\1/p" /proc/devices" I don't get any output. (running kernel 2.6.24-...)

---

### Post by Meyermagic on 2008-11-27
This doesn't solve the problems most people are having in this thread, but I wrote a little (ugly, will revise and repost later) Python script to help find the correct IP address for streaming to your Airport. It just parses output from the avahi-browse command and filters for the raop service.

```

from subprocess import Popen, PIPE

rdata = Popen(["avahi-browse", "-p", "-t", "-r", "-k", "-l", "-a"], stdout=PIPE).stdout.read()

def fix(p):
    if len(p[1].split(',')) > 1:
        return (p[0], p[1].split(','))
    return p

devices = []

for line in rdata.split("\n"):
    fields = line.split(";")
    if len(fields) == 10:
        txt = fields[9]
        if txt != "":
            txt = txt[1:-1].split('" "')
            txt = map(lambda a: a.split("="), txt)
            txt = map(lambda a: (a[0], a[1]), txt)
            txt = map(lambda p: fix(p), txt)
            txt = dict(txt)
        ldata = {'interface' : fields[1], 
            'ip_version' : fields[2], 
            'device_name' : fields[3],
            'service_type' : fields[4], 
            'local?' : fields[5], 
            'hostname' : fields[6], 
            'address' : fields[7], 
            'port' : fields[8], 
            'txt' : txt}
        devices.append(ldata)


print "Remote Speakers:"
print 
for device in devices:
    if device['service_type'] == '_raop._tcp':
        print device['hostname'], "at", device['address'], "port", device['port']
        print "Parameters:"
        for k, v in sorted(device['txt'].items()):
            print "\t" + k, "=", v
        print "----------------------------"

```

---

### Post by walter9258 on 2008-12-03
I came across [[COLOR="Red"]this page[/COLOR]]("http://www.metacafe.com/watch/1474216/building_a_laser_audio_transmitter_for_under_15_dollars/") today and thought it was pretty cool. I've been trying to get my Airtunes to work with Ubuntu for a long time now, but it just isn't very good. (Probably the only thing keeping me from running Ubuntu exclusively on my Macbook). The link shows how to use a laser to stream music wirelessly. Not quite the same concept as Airtunes, but a wireless solution none-the-less.

---

### Post by jobless on 2009-03-05
Has anyone tried espeak to airport express streaming? espeak is a text to speech utility. I tried to make the output from espeak stream to airport express with no luck. More details about what I did are at [http://ubuntuforums.org/showthread.php?p=6846426#post6846426](http://ubuntuforums.org/showthread.php?p=6846426#post6846426).

---

### Post by Bryan Larsen on 2009-04-03
I tried setting things up with Jaunty.   Using the CVS version ([http://www.jroller.com/nwinkler/entry/raop_play_code_updates](http://www.jroller.com/nwinkler/entry/raop_play_code_updates)), everything compiled without problems.  It even compiled a kernel module which modprobe'd in very sweetly.

Using aexcl_play to play songs worked great, too (after I installed mpg321).  However, I couldn't get the alsa module to work.  I haven't tried too hard, yet.

Poking around, it appears that pulseaudio 0.9.15 includes support for the airport express.  That's too new to include in Jaunty, but it's available here:  [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

---

### Post by Bryan Larsen on 2009-04-03
Very nice!   Pulseaudio works so much better than raop_play ever did.  No lag, audio discovery, no weird shell scripts & daemons to run.  Nice!

To use it:

add [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa) to your sources.list (rather, look at the instructions on that page).

sudo apt-get upgrade
sudo apt-get install pulseaudio-module-raop
pactl load-module module-raop-discover
pavucontrol # switch default output to your airport express

enjoy!

---

### Post by olavjunior on 2009-04-05
Am I missing out on something? I did as you said, but after changing default sink to appleTV, no player will play songs, they just hang.. 

Should I install some extra packages like raop play or something?

---

### Post by therevan on 2009-04-06
> **Bryan Larsen said:**
> To use it:

add [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa) to your sources.list (rather, look at the instructions on that page).

sudo apt-get upgrade
sudo apt-get install pulseaudio-module-raop
pactl load-module module-raop-discover
pavucontrol # switch default output to your airport express

Got all the way to the third terminal command "```
pactl load-module ...
``` and encountered ```
Failure: Module initialization failed
``` (harsh, right?).

Any suggestions? Seems like there's something missing in the audio back-end ...

---

### Post by therevan on 2009-04-06
Got it! ... Partially.

Had to install the **pavucontrol** package for pactl or pavucontrol commands to work. But in the pavucontrol dialog, I don't see anywhere I can add an AirPort/AirTunes output.

Any suggestions? (part 2)

---

### Post by clconway on 2009-04-06
> **therevan said:**
> Got it! ... Partially.

Had to install the **pavucontrol** package for pactl or pavucontrol commands to work. But in the pavucontrol dialog, I don't see anywhere I can add an AirPort/AirTunes output.

Any suggestions? (part 2)
The Airport should show up in the Output Devices list automatically if it is detected by the raop module. Try running "pulseaudio -vvv" and see what the output is when you do "pactl load-module ...".

---

### Post by Bryan Larsen on 2009-04-06
Everything works except for skype:  [http://ubuntuforums.org/showthread.php?p=6922395](http://ubuntuforums.org/showthread.php?p=6922395)

here's how to fix it: [https://answers.launchpad.net/medibuntu/+question/66498](https://answers.launchpad.net/medibuntu/+question/66498)

---

### Post by therevan on 2009-04-06
Oy vey, this is such a tease.

I got the AirTunes modele loaded, and PulseAudio Volume Control (pavucontrol) sees my AppleTV!

But no sound through the ATV speakers, and attempting to pause or stop playback causes a PulseAudio crash.

I'll post a log when I can recreate.

---

### Post by bzzzzz on 2009-05-03
The best way I've found to stream to my airport express was using el tunes.  

Just go to this website [www.el-tunes.com]("http://www.el-tunes.com")

For me I downloaded GSTransmit 1.0 -i386 DEB

I'm running Hardy Heron 8.04.

Then followed prompts to install the program.

I then started Rhythmbox.

I then opened a terminal and typed **gstransmit-toggle**

You should then be informed in the terminal that your computer is **Enabling airport device**

Then play any tune you like and it should come blaring out of your speakers.

---

### Post by KamikazeNY on 2009-05-17
Tried the PulseAudio raop module. Detected airport express no problem but the sound output to it was choppy. Cut out 2 or 3 times per second. No problems streaming to it via itunes on windows partition. Sound also plays fine localy through PA.

Using Jaunty, PA 0.9.15, x64 installation.

---

### Post by clconway on 2009-05-17
The skipping is a known bug. You might want to follow the ticket: [http://pulseaudio.org/ticket/495](http://pulseaudio.org/ticket/495)

---

### Post by KamikazeNY on 2009-05-18
> **clconway said:**
> The skipping is a known bug. You might want to follow the ticket: [http://pulseaudio.org/ticket/495](http://pulseaudio.org/ticket/495)
Thanks for the link!

---

### Post by sigve on 2009-06-02
If pulseaudio doesn't discover your airport device, check that moblock isn't blocking it!

I wretched my brains for quite some time until I discovered I just had to allow avahi-connections through moblock :oops:

---

### Post by bzzzzz on 2009-06-02
Just tried to do the same install of el tunes with jaunty with no success.

Rhythmbox just says it can't play the song.

I think something is going wrong with gstreamer but I don't know what it is.

I don't think I'm running Moblock like the previous poster.

---

### Post by brw02005 on 2009-06-02
I just Compiled a newer version of ALSA to get NVIDIA HDMI audio working (of course it not pulse audio friendly though) and just got your pulse audio airport express stuff working once I saw the hint about shutting off mo-block.  Now I have two airport expresses any chance of getting them to sync?  I also figure this would be something similar for getting the HDMI audio and on onboard intel audio to sync or at least switch with pulse audio controls intel shows up but not the nvidia.  Personally I'm impressed this all works all though I would like to get rid of the excessive tinkering to switch inputs and sync up some stuff if possible.

My future dream is to program my HTPC to hit one button and output to all my airport expresses.  But for now this is a babystep and my frontend XBMC still doesn't have pulse audio support yet although I'm told the newer versions might.

---

### Post by scottyec on 2009-06-08
Hey guys,

I'm running 8.04 Hardy.  I have tried to run gstransmit a few times, but since there doesn't seem to be any kind of control, I can't even tell if it's close to working.  My audio goes somewhere other than the internal soundcard when it's "Enabled" but I don't know how far it's getting.  The whole system thinks everything's working fine, but no audio at the amp.

I wish there was a way to get Hardy to install the new pulseaudio.  That would be sweet.  Any ideas?  Status right now: the updates are grayed out in the system updater program...

Thanks for putting up all this useful info up, guys. Take care.

Scott,

---

### Post by bzzzzz on 2009-06-11
Well mine works in hardy but not in jaunty.

have you installed all the packages that are needed

I think you need all of these

mono
mono-zeroconf
gstreamer
nemerle

---

### Post by Chebyshev on 2009-06-12
I am running Jaunty and followed the instructions for the Pulseaudio raop sink, but I always get

```
$ pactl load-module module-raop-discover
Failure: Module initalization failed
```

I installed pavucontrol as outlined in a previous post and still have the same problem. Any ideas?

---

### Post by bzzzzz on 2009-06-12
watch this [http://www.youtube.com/watch?v=UUZOQsNo_ws](http://www.youtube.com/watch?v=UUZOQsNo_ws) and then just apply what you see to this ppa [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa).

However I too get stuck when I enter the command

pactl load-module module-raop-discover

I get 

E: shm.c: shm_open() failed: Read-only file system
Failure: Module initalization failed

Anyone know what to do about this?

---

### Post by scottyec on 2009-06-12
> **bzzzzz said:**
> Well mine works in hardy but not in jaunty.

have you installed all the packages that are needed

I think you need all of these

mono
mono-zeroconf
gstreamer
nemerle

I tried to install mono and mono-zeroconf but it says they're not available.  I think they're installed, because I used to use banshee.  How would I make sure?  I know gstreamer is in there.  But I can't find nemerle, either.  I was expecting some error message if I didn't meet the dependencices.  Where can I find these packages?

Thanks for the help.

Scott,

---

### Post by bzzzzz on 2009-06-13
have a look in the synaptic.

make sure you have all the repositories open check the software sources that you have access to in the system, administrations drop down menu.

I was lucky enough in that it just worked when I installed it.

---

### Post by bzzzzz on 2009-06-28
Ok got this working in jaunty as well now.

Just followed the instructions outlined in this wiki

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

look down the menu or just find aex in the document.  It's pretty much the same as here but for some reason it just worked this time.

---

### Post by niyam on 2009-07-04
i've tried the steps detailed here:
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

pulseaudio cannot auto-detect the airportexpress device. have got PulseAudio DeviceChooser to work, PulseAudio Manager also shows up, the Volume Control within the Pulse Applet also shows up. However, 'Output Devices' does not show the airport express. the pactl load module... command detailed above gives the  module initialization failed error. what am i doing wrong? how do i fix this?

---

### Post by bzzzzz on 2009-07-05
When you go to the volume control do you get the option of choosing your airport express?

Have you got all the most recent updates running on your jaunty box?

---

### Post by niyam on 2009-07-05
> **bzzzzz said:**
> When you go to the volume control do you get the option of choosing your airport express?

Have you got all the most recent updates running on your jaunty box?
thanks bzzzzz for your response.
in the volume control i do not get the option of choosing the airport express. as a double-check on the AEX, the macbookpro does detect, connect, and stream music to it from under macOSX. therefore the hardware and connections are all okay.
i do a daily check-for-updates and promptly install any new updates. are there any specific versions of software you think i should check? here's my pulseaudio -v output:

I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: Giving up CAP_NICE
I: main.c: This is PulseAudio 0.9.15

what gives?


regards
niyam

---

### Post by bzzzzz on 2009-07-05
Not sure - I'm having a look.

In the meantime you'll know that your airport express has been picked up because on the volume control you'll see a second volume bar with the name of your airport express.

---

### Post by niyam on 2009-07-05
> **bzzzzz said:**
> Not sure - I'm having a look.

In the meantime you'll know that your airport express has been picked up because on the volume control you'll see a second volume bar with the name of your airport express.
yes, i imagined that. thanks for the tip. must mention i do run firestarter the firewall app. i allowed incoming for 5000, 6000, 5353 as mentioned elsewhere. later i sniffed around under macos and discovered it uses 5009, so enabled that too. also switched off the firewall, did a double-check on # iptables -L, and then ran a iptables --flush as well. no luck.

---

### Post by bzzzzz on 2009-07-05
have you checked make discoverable network sound devices and available locally and make discoverable apple airtunes sound devices available locally.
in the pulseaudio preferences menu (under system, preferences)
i remember when i first installed it i also had enable network access to local sound devices checked.  the aex failed to work until i unchecked that box.

in short just make sure only the bottom two boxes are checked.

---

### Post by niyam on 2009-07-05
> **bzzzzz said:**
> have you checked make discoverable network sound devices and available locally and make discoverable apple airtunes sound devices available locally.
in the pulseaudio preferences menu (under system, preferences)
i remember when i first installed it i also had enable network access to local sound devices checked.  the aex failed to work until i unchecked that box.

in short just make sure only the bottom two boxes are checked.
yes, only the two boxes are checked, and yesterday did try toggling the top box to see if it kicks some life into it. what should i do with the mutlicast/RTP settings in the second tab, and with the third tab, please?
also, decided to sniff around with portscan, and confirmed ports 5000 and 5009 are open on the aex, ditto on my laptop. now if only these two machines would give up their code of silence and burst into song the world would be a happier place for me :-)

niyam

---

### Post by bzzzzz on 2009-07-05
I've left everything else alone, no need to touch multicast/rtp

just for interest i've got mine with both box left unchecked
simultaneous output also unchecked.


It's probably irrelevant but 

i also have on notifications *show notifications for discovered sinks* but none of the other notifications boxes checked.  

i also have the start applet on session login checked

check that your version is the same as mine, click pulseaudio manager and then look at the server information

running server version 0.9.15
compiled with library version 0.9.14



Have you tried restarting your computer.

---

### Post by niyam on 2009-07-07
> **bzzzzz said:**
> I've left everything else alone, no need to touch multicast/rtp

just for interest i've got mine with both box left unchecked
simultaneous output also unchecked.


It's probably irrelevant but 

i also have on notifications *show notifications for discovered sinks* but none of the other notifications boxes checked.  

i also have the start applet on session login checked

check that your version is the same as mine, click pulseaudio manager and then look at the server information

running server version 0.9.15
compiled with library version 0.9.14



Have you tried restarting your computer.
thanks bzzzzz for the suggestions.
ditto on my machine and several reboots too.
interestingly, am connected to the internet through the airport express, so the machine does recognize it.
just that pulse-audio is clueless about its existence and the speakers connected to it.

to troubleshoot further, have also installed 'avahi zeroconf browser' from 'add/remove...'
it shows my local macbookpro, and nothing else.

frustrating, this pulseaudio...

regards
niyam

---

### Post by niyam on 2009-07-08
yesterday, my system recommended some updates. noticed some were for pulseaudio and other audio related components, so confirmed installing the updates.
at first nothing much happened. however, today, on booting in, the avahia zeroconf browser showed my macbookpro and the aex speakers. wow! on clicking the speakers i noticed the browser showed the IP address on a different class compared to my laptop. however, initially the pulse volumecontrol showed nothing but soon it did! i made it default, and this macbookpro with ubuntu 9.04 **did** actually stream music to the airport express! however within a few minutes it died. a quit and restart of pulse did not work. not even a reboot of the macbookpro and the airport express. i check the avahi zeroconf browser also could not sense my speakers or the aex. where earlier it displayed the net details of my macbookpro, the avahi zeroconf browser now only shows:
Error: org.freedesktop.Avahi.TimeoutError: Timeout reached

i think the problems are more with avahi and 'bonjour' style zeroconf than anything else?

regards
niyam

---

### Post by fbugnon on 2009-07-09
According to this post:

> **bzzzzz said:**
> The best way I've found to stream to my airport express was using el tunes.  

Just go to this website [www.el-tunes.com]("http://www.el-tunes.com")

For me I downloaded GSTransmit 1.0 -i386 DEB

I'm running Hardy Heron 8.04.

Then followed prompts to install the program.

I then started Rhythmbox.

I then opened a terminal and typed **gstransmit-toggle**

You should then be informed in the terminal that your computer is **Enabling airport device**

Then play any tune you like and it should come blaring out of your speakers.

GSTransmit works right away with 8.10, but apparently it doesn't for 9.04.
At least for me, I can only hear some noises from the speakers when playing music with Rhythmbox and Totem.

Has anyone managed to do it under Jaunty?

---

### Post by niyam on 2009-07-09
> **fbugnon said:**
> According to this post:



GSTransmit works right away with 8.10, but apparently it doesn't for 9.04.
At least for me, I can only hear some noises from the speakers when playing music with Rhythmbox and Totem.

Has anyone managed to do it under Jaunty?

tried this route last week. got gstransmit to finally install, yet everytime i toggle it on to output to aex, rhythmbox often crashes, or gives no sound output even to the built in speakers. just once, i heard some initial noise from the built-in speakers before it descended into silence.
totem worked normally, but strangely enough has stopped working right now. maybe a reboot might solve this (why do i sound like a windows user here ?)

regards
niyam

---

### Post by bzzzzz on 2009-07-09
Which install of ubuntu are you using.

Just to test it out try installing jaunty (lts) and then use the el-tunes method.  that will at least give an indication that it **can** work on your system.

keep trying

---

### Post by niyam on 2009-07-09
> **bzzzzz said:**
> Which install of ubuntu are you using.

Just to test it out try installing jaunty (lts) and then use the el-tunes method.  that will at least give an indication that it **can** work on your system.

keep trying
am using ubuntu 9.04:
Linux 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

totem works normally with pulseaudio. however, the moment i try that gstransmit-toggle, it stops working (outputting sound atleast to my laptop's built in speakers). when i quit totem, do a gstransmit-toggle to de-activte aex, relaunch totem, it no longer outputs to the internal speakers. only a reboot gets everything back to normal.

am really tantalized by the fact that my airport express speakers did work *once* under 9.04 using totem and pulseaudio, while having the speakers sensed by avahi zeroconf browser as well.
i wonder why it did work, and why it did not anymore?
complete mystery, and am just waiting for all these things to be resolved so i may consistently use airport express to stream any audio from my mackbook pro over ubuntu 9.04

regards
niyam

---

### Post by bzzzzz on 2009-07-09
So you have had it working in the past.  

Rather annoyingly my Jaunty version has stopped working (or stopped working properly).  If I place the arrow over the file the song will play and through the speakers.

If I open Rhythmbox then I cannot get an output to the speakers.  

However I also have on the same laptop a distribution of linux mint (which is heavily based on 9.04) on which I can stream to the stereo.  The thing which I have been most impressed by with linux mint is the sheer number of times things have worked first time.  

I'll probably find lots of bugs soon, but up till now I have to say that this is the best linux distro I've used.

---

### Post by niyam on 2009-07-09
it worked only once, for a few minutes.
why? how? i don't know.
my guess: some pulseaudio and other components got updated in the auto-update manager.
however, it has not worked again so far.

---

### Post by bzzzzz on 2009-07-10
I'm getting the music a bit choppy in linux mint now.  

Jaunty works again.  It seems at best temperamental.

---

### Post by niyam on 2009-07-10
> **bzzzzz said:**
> I'm getting the music a bit choppy in linux mint now.  

Jaunty works again.  It seems at best temperamental.
funny thing is, it worked today on my macbook pro as well. i reckoned this could be a firewall problem, even though i had switched off firestarter. as root, iptables -L showed some settings, so i reset with iptables --flush.
avahi zeroconf browser showed the airport speakers, where i promptly copied down the 'service name' which is actually understood by pulseaudio as the 'sink' name.
in the volume-control i also set playback to HDA NVIDIA PulseAudio Mixer.
the volume control of pulse showed the speakers! i set them as default and it worked.
on a reboot it did not work. not even avahi's browser showed the speakers.
a third reboot everything worked again, with heavily choppy audio.

so i guess, not only is this temperamental and buggy, but there is perhaps a mysterious design at work. am trying to decipher the pattern here: does pulseaudio work on even days of the month; or is it on days of the week that do not start with the letter 'T'; with a second condition of working on odd-numbered reboots; or is there some other divine madness at work? [just joking]

this thing is buggy and idiosyncratic.
opening users and groups, have added my user and root to pulse-rt, to try to cut out the choppiness. no help.

my feeling: the avahi daemon issues timeout errors, so the problem starts from some conflict or precdence of daemons. when my aex is auto-sensed as the first wifi connection and the machine establishes a connection with it, more chances of it working, pulse-audio needs settings for NICE to get preference for streaming and buffering without choppy sounds, and i guess there are a whole bunch of bugs lying underneath i can't fathom but needs an expert to make shallow and disappear.
until then, loved the hacking around, and hope to soon see an update on components which may eventually fix these bugs. back to a wired connection to speakers from the headphones port for me until then.

thanks bzzzzz for your prompt responses.

regards
niyam

---

### Post by niyam on 2009-07-12
just discovered this interesting snippet at the pulse-audio's blog site. scroll down to the airport express section

[http://0pointer.de/blog/](http://0pointer.de/blog/)

n

---

### Post by heluani on 2009-07-19
Can anyone point me to the sources for the raop modules for Pulseaudio? I can only find the binary packages on the web.

R.

---

### Post by heluani on 2009-07-19
Nevermind I guess I should've looked in the sources for pulseaudio :)

R.

---

### Post by bzzzzz on 2009-07-27
> **niyam said:**
> just discovered this interesting snippet at the pulse-audio's blog site. scroll down to the airport express section

[http://0pointer.de/blog/](http://0pointer.de/blog/)

n

I read the article which sounds a little defeatist, however I am not a hacker or programmer so I don't really know how hard the task is.  

The thing that strikes me as odd is that airfoil (which runs on windows and mac) allows lots of different applications to stream to the aex.  How come this is possible.  As far as I know the people that write airfoil have nothing to do with mac or windows.

---

### Post by heluani on 2009-08-02
running pulseaudio 0.9.15 with the raop module loaded I can stream to airport express with no problems.

For those who are stuck with older versions or want to use still the gstransmit option, I would take a look at the last two lines of /etc/pulse/daemon.conf

to have something like

```

default-fragments=4
default-fragment-size-msec=25

```
instead of (for example) 8,5. These latter numbers are better for applications like Skype, but certainly kill my streaming to Airport express.

R.

---

### Post by ballardhd on 2009-08-14
I am able to make my Apple TV my default sink in the volume control UI for pulseaudio. However, once I try and move the volume control, pulseaudio crashes and I get the error:


"Connection Failed. Connection Terminated."

Has anyone had any success in playing any actual music after connecting to their Airport Express / AppleTV device? I running Jaunty and Pulseaudio 0.9.15...

---

### Post by heluani on 2009-08-17
> **heluani said:**
> running pulseaudio 0.9.15 with the raop module loaded I can stream to airport express with no problems. 

Although I am not running Jaunty.

Edit: if the daemon is crashing, why don't you get a stacktrace and contact upstream (or even irc), those guys are really nice.

R.

---

### Post by yomyom on 2009-08-19
Hi there,

Has anybody heard about this Gstreamer plugin called "gstapexsink" (in the bad-plugins branch)? According to the developer ([http://bugzilla.gnome.org/show_bug.cgi?id=542510#c0]("http://bugzilla.gnome.org/show_bug.cgi?id=542510#c0")), with only a small edit in your gconf editor...

*/system/gstreamer/0.10/default/musicaudiosink "apexsink host=YOUR_AIRPORT_IP volume=100"*

... it should allow defining your Airport Express as an audio sink and, from there, stream any sound from your computer to your AE.
I have tried it without major successes so far... :(

After setting my AE as audio sink with the following command...

*gconftool-2 -t string --set /system/gstreamer/0.10/default/musicaudiosink "apexsink host=YOUR_AIRPORT_IP volume=100"*

... Rythmbox crashes each time I try to play some sound. Amarok keeps using the computer speakers. Only the sound preview in Nautilus seems to engender some communication with the AE (local network activity) but no sound.
Using the plugin with the gst-launch command in debug mode...

[I]for an ogg vorbis file:
gst-launch --gst-debug=apexsink:5 filesrc location=YOUR_FILE.ogg ! vorbisfile ! audioresample ! apexsink host=YOUR_AIRPORT_IP volume=100

for a mp3 file:
gst-launch --gst-debug=apexsink:5 filesrc location=YOUR_FILE.mp3 ! mad ! audioconvert ! audioresample ! apexsink host=YOUR_AIRPORT_IP volume=100[/I]

...produces better results. Some bits and pieces of my music file actually reach the speaker system connected to my AE, but nothing really listenable...

Any clues? Successful experiences?

My config: Ubuntu Jaunty + Airport Express firmware v.7.4.2 (also tested with v.7.3.2)

---

### Post by gianni1977 on 2010-02-15
Hi!

I have ubuntu 9.10 and my problem is the same as Ballardhd.

I can see the Airport, but can't stream anything to it. 

If I touch the volume slide, pulseaudio crashes, giving this error message:

"pa_context_set_sink_volume_by_index() 

Connection Failed. Connection Terminated"

Anyone got any solution so far?

Thanks!

---

### Post by bzzzzz on 2010-06-26
Anyone had any joy with 10.04.

I'm still drawing blanks.  

I can find my airport express with avahi browser (search for avahi discover in the synaptic)

For some reason pulseaudio can't see it.

---

### Post by bzzzzz on 2010-06-29
Got it working.  Very choppy though.  

In the pulseaudio settings you can tell it to look for the airport express by ticking a couple of boxes.

---

### Post by Takkat on 2010-08-14
> **bzzzzz said:**
> In the pulseaudio settings you can tell it to look for the airport express by ticking a couple of boxes.

Hi,

after months of instable connections I found out, that it is much better to connect the AirPort Express directly via it's IP, not using Avahi/Zeroconfig but still streaming through pulseaudio-module-raop. You'll find my little GUI **[stream2ip]("https://launchpad.net/stream2ip")** to ease this at LP ready for testing.

Have fun! Tak

---

### Post by raffraffraff on 2010-11-01
I haven't had a single minute of uninterrupted audio out of this thing. I've tried the configuration every which way, from full auto IPs and 'discovery' to full manually configuring everything. I have always been able to send sound to the device, but it's always horribly choppy. 

I haven't yet tried the suggested /etc/pulse/daemon.conf settings:
default-fragments=4
default-fragment-size-msec=25

...but I've spend hours with this piece of crap, so I'm sick of it.

Designing hardware and software to function well together is one thing, but Apple spends way too much effort on forcing their customers to buy more Apple products to work with their existing Apple products. Microsoft used to be a bastion of ruthless anti-competitiveness, and I'm not suggesting that they've gone soft, but Apple have taken the crown from them. They go out of their way to build proprietary interfaces and weird protocols instead of using industry standards. They continually reinvent new wheels that only work on their wheelbarrow, then they patent that wheel so that nobody else can make it. As you can see, they'll sue your as5 if you try...

[http://www.engadget.com/2010/11/01/hypermac-to-become-hyperjuice-in-response-to-hyperactive-apple-l/](http://www.engadget.com/2010/11/01/hypermac-to-become-hyperjuice-in-response-to-hyperactive-apple-l/)

This type of anti-competitive crap sums up all that's wrong with Apple. The "PC Vs Mac" debate isn't about fashion or usability. It boils down to this: if you want to use one Apple product, you HAVE TO become a fanboy and go all-in to the Apple game to get the most out of it. You have to stop choosing the 'best product' and start going for the 'best apple product'.

Technically, the AirPort Express is able to accept a stream of audio from any source over WiFi, but in reality you can only stream music from iTunes. You can't even direct your Mac audio to it. (I have a Mac - so I can confirm this). So, I have a laptop, two PCs and a Mac and I  can only stream sound from one app one the Mac to this $99 piece of crap.

The only reason it's (barely) usable on Linux is that some guy reverse-engineered the RAOP protocol and DVD Jon extracted the RSA key from iTunes. But it's not worth the effort.  I'm throwing this into the trash and buying an FM transmitter for the devices I want to stream from.  No lag, no horrible setup.

And Apple: Go f*ck yourselves.

---

### Post by TKoorn on 2010-12-28
I cound't get the alsa driver to compile but I could get Raop Play to compile. 

Since "Raop Play" can stream to the airport device I looked for a way to get it to accept a stream. 

I found I can do this: 
$ mkfifo /tmp/foo 

and then run 

raop_play 192.168.1.112 /tmp/foo 

raop_play is now sending any info written to /tmp/foo to the airport device 

I can then run mplayer and send its output to /tmp/foo like this: 

mplayer -ao pcm:file=/tmp/foo [name_of_file_to_play]

---

### Post by Takkat on 2010-12-28
It's admittedly not easy to get the AirportExpress playing smoothly but it's possible. I did not remember if changed my pulsaudio daemon.conf. Now it looks like this (everything else commented out):

```
resample-method = speex-float-1
[...]
flat-volumes = no
[...]
default-fragments = 8
default-fragment-size-msec = 10
[...]
```

I do **not** run PulseAudio in system mode either. Depending on the player I use, and of course **a very good WLAN signal** strength is needed, but then sound played via PulseAudio to the IP (using [stream2ip]("https://launchpad.net/stream2ip")) of the AEX is playing smoothly for hours. You definitely need to test this with several players, this was my main frustration with choppy playback. There is no good advice on what player to use as it seems to depend on other system factors as well. People complain on players where others are happy and vice versa. 

If this all does not help it may also be some router or WLAN-stick/card setting that breaks audio playback. I have a D-Link WLAN router **wired** to my Ubuntu box and to transmit WLAN signals to the AEX and to another machine 2 rooms away. This router comes with some "Quality of Service" traffic shaping, but I did not recognize much difference when switching this feature off.

One thing in addition: PulseAudio is an implementation of JustePort RAOP play for better integration in your sound system but it's using the same code. Only with PulseAudio you are able to stream in the sense of AirTunes using the AEX as audio output device for your favourite music player. Only drawback is a 6 seconds delay.

It'd interest me if raffraffraff had any luck with FM-transmitters (I always believed they had a limited sound quality) ;)

---

