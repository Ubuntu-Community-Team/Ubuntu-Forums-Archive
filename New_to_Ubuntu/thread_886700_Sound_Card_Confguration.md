---
title: "Sound Card Confguration"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Checkhovian on 2008-08-11
Well, yesterday my computer played sound and I could adjust the volume. Today I have no sound, the volume icon shows muted, and when I click the volume icon I get a popup that reads as follows:

> The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Running Hardy on a Dell Inspiron 1525 laptop. Have not made any changes to hardware or software since sound worked. Have GStreamer plugins installed already (had them before, still have them now).

HELP PLEASE!

---

### Post by Checkhovian on 2008-08-11
Update:

Checked the suggestions here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Went through steps and got ALSA drivers from fresh kernel. 

```
aplay -l
``` still doesn't list anything

I started trying to do the ALSA driver compilation, but it keeps asking me for the ubuntu install CD, and I don't have a ubuntu CD or a blank CD to burn one onto at the moment. Is there a way to do it without the CD?

---

### Post by wednesday allfather on 2008-08-11
Greetings,

I would suggest you try to reinstall ALSA-BASE from synaptic.  

I usually remove that CD from my list of software sources.

---

### Post by Checkhovian on 2008-08-11
> **wednesday allfather said:**
> I would suggest you try to reinstall ALSA-BASE from synaptic.

Already did. Did not help. Thanks anyway.

---

### Post by bobnutfield on 2008-08-11
Type in a terminal:

> lspci | grep Audio


and also:

> sudo lsmod | grep snd

Post the output.  We are looking to see what hardware is there and if the correct modules are loaded.

---

### Post by Checkhovian on 2008-08-11
First one doesn't output anything. Second one gives me

> snd_hda_intel         440408  0 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd

(by the way, thank you for telling me what to do in basic instructions, I was starting to get confused and frustrated)

---

### Post by bobnutfield on 2008-08-11
OK, your hardware uses the snd-hda-intel module and it appears to be loaded.

Try one more command before looking at anything else.  Type:

> sudo /etc/init.d/alsa-utils reset

This just resets the alsa drivers.  Can't guarantee it will work, but if it does it will prevent looking deeper.

---

### Post by Checkhovian on 2008-08-11
It output "resetting alsa" and then "ok", but other than that no change...

---

### Post by bobnutfield on 2008-08-11
Ok, so you still have no sound.  When you go to System>Preferences>Sound, the box that says "Devices", what is the entry shown in that box?  If it is blank, check and see if the drop down menu shows any options.  If it does not, I will post back a link that will give instructions on how to restore your sound.

---

### Post by Checkhovian on 2008-08-11
Nothing in the box or drop-down menu.

Thank you for all your help so far!

---

### Post by bobnutfield on 2008-08-11
[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/]("http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/")

This is a link to a rather lengthy set of instructions for re-storing sound with a problem which appears to be identical to yours.  The instructions are for Gutsy, but they will work in Hardy as well, just change the kernel information where it is shown to your current kernel.

[http://ubuntuforums.org/showthread.php?t=769492&highlight=sound+howto]("http://ubuntuforums.org/showthread.php?t=769492&highlight=sound+howto")

This link is from this forum with solutions for the same problem.  It appears as though the connection with your alsa drivers is gone.  You will a solution in one of these two links, but if you have trouble,post back and I am sure we can get you going.

---

### Post by Checkhovian on 2008-08-11
Tried working on the second one (using the directions in this [http://ubuntuforums.org/showpost.php?p=4820543&postcount=8](http://ubuntuforums.org/showpost.php?p=4820543&postcount=8) post

Got though all of sections one, two, and three successfully. Tried to do ```
./configure --with-cards=ICH8
``` but got > bash: ./configure: No such file or directory

---

### Post by bobnutfield on 2008-08-11
Did you cd into the directory with the makefile?

---

### Post by Checkhovian on 2008-08-11
*groan* Missed that.

So I did that with all the other packages, except utils (as directed), but (A) got errors for all of the packages and (B) still have no sound.

Configuring and Making went okay, but the "make install" seemed to go awry each time. Here's what it gave me back...
> dell@dell-laptop:~/alsa-firmware-1.0.16$ make install
Making install in hdsploader
make[1]: Entering directory `/home/dell/alsa-firmware-1.0.16/hdsploader'
make[2]: Entering directory `/home/dell/alsa-firmware-1.0.16/hdsploader'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/alsa/firmware/hdsploader" || mkdir -p -- "/usr/local/share/alsa/firmware/hdsploader"
mkdir: cannot create directory `/usr/local/share/alsa': Permission denied
make[2]: *** [install-firmwareDATA] Error 1
make[2]: Leaving directory `/home/dell/alsa-firmware-1.0.16/hdsploader'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dell/alsa-firmware-1.0.16/hdsploader'
make: *** [install-recursive] Error 1

Did I miss something again?

---

### Post by bobnutfield on 2008-08-11
You must use "sudo make install".  You are getting "permission denied" errors.

---

### Post by Checkhovian on 2008-08-11
Thank you very much again. I'm sorry to keep making such basic errors.

I sudo make installed the lib and firmware with no problem, but got an eror when I tried to do the driver. > dell@dell-laptop:~/alsa-driver-1.0.16$ sudo make install
if [ -L /include/sound ]; then \
		rm -f /include/sound; \
		ln -sf /home/dell/alsa-driver-1.0.16/include/sound /include/sound; \
	else \
		rm -rf /include/sound; \
		install -d -m 755 -g root -o root /include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /include/sound; \
		done \
	fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1

---

### Post by bobnutfield on 2008-08-11
I believe you need the linux-headers for your kernel to complete this make install.  In a terminal, do:

> sudo apt-get install linux-headers-2.6.24-19-generic

That is, of course you are in fact running the latest kernel (2.6.24-19-generic.)

Then run the make install command again.

---

### Post by Checkhovian on 2008-08-11
I'm actually running a slightly outdated kernel - 2.6.24-16

> dell@dell-laptop:~$ sudo apt-get install linux-headers-2.6.24-16-generic
[sudo] password for dell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-16-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libswfdec-0.6-90
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 193 not upgraded.

dell@dell-laptop:~$ cd /home/dell/alsa-driver-1.0.16
dell@dell-laptop:~/alsa-driver-1.0.16$ sudo make install
if [ -L /include/sound ]; then \
		rm -f /include/sound; \
		ln -sf /home/dell/alsa-driver-1.0.16/include/sound /include/sound; \
	else \
		rm -rf /include/sound; \
		install -d -m 755 -g root -o root /include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /include/sound; \
		done \
	fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1


---

### Post by bobnutfield on 2008-08-11
Well, I will be glad to help research this error for you, but unfortunately I have to sign off for now till tomorrow.  Hopefully, someone will pick up and chime in.  This error should not be difficut to sort out and get the drivers installed for you. I will bookmark this post and check in tomorrow to see if you have it sorted.

---

### Post by Checkhovian on 2008-08-11
Thank you very much for all of your time!

If anyone else is out there, please do chime in!

---

### Post by Checkhovian on 2008-08-11
Have continued to read through the sound card threads around here, and haven't found a solution that works yet. Anyone have any ideas on how to re-introduce ALSA to my sound card and vice versa?

---

### Post by strel1337 on 2009-10-30
I get this error: anyone know what to do
```

root@HOST:/usr/src/alsa/alsa-driver# sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yeschecking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver
checking cross compile... 
checking for directory with kernel source... ./configure: line 5039: cd:[COLOR=Red] /usr/src/linux-headers-2.6.27-11-generic: No such file or directory
/usr/src/linux-headers-2.6.27-11-generic[/COLOR]
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


```

---

