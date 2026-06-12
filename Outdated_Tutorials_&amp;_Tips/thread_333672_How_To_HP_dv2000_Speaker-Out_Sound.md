---
title: "How To: HP dv2000 Speaker-Out Sound"
date: 2007-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by heffo_j on 2007-01-07
I fixed the Speaker Out by following the advice of the link below. Although it was composed for Suse, it works for Ubuntu if you unpack your downloaded file to someplace and then complie as instructed. Instead of the "su -" command, use the more familiar Ubuntu preferred "sudo make install". Otherwise all went well.
 
[http://www.sundru.net/bblog-stuff/?sectionid=2]("http://www.sundru.net/bblog-stuff/?sectionid=2")


Best regards
John

---

### Post by dypfryst on 2007-01-11
thanks!! Been trying to fix the sound issues on my hp dv2017ea for a long time. this did it :)

---

### Post by xorti on 2007-01-13
I'm using a HP dv2173ea, and I've tried that  tutorial but when I run 'sudo make install' I've got this error.

xxx@laptop:~/Desktop/alsa-driver-1.0.14rc1$ sudo make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/jorge/Desktop/alsa-driver-1.0.14rc1/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1

Any help?

PS: Sorry for my english! :P

---

### Post by xorti on 2007-01-14
Problem solved! I've forgotten the 'make' command :P

---

### Post by tenzinmonlam on 2008-11-10
I have also the same issue with my Hp Dv2000 but i never had any issue on the Ubuntu 8.4. It only occurred when i installed the 8.10 few days back. . Will this work on my 8.10 as well. Other wise I have to switch back to 8.4. But I don't want to.. I really love the 8.10.. 

Hope This Will help:

#aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
Peace..

---

### Post by tenzinmonlam on 2008-11-10
I have also the same issue with my Hp Dv2000 but i never had any issue on the Ubuntu 8.4. It only occurred when i installed the 8.10 few days back. . Will this work on my 8.10 as well. Other wise I have to switch back to 8.4. But I don't want to.. I really love the 8.10.. 

Hope This Will help:

#aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
Peace..

---

