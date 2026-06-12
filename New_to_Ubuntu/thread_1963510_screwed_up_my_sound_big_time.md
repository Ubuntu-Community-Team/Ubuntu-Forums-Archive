---
title: "screwed up my sound big time"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Doxa on 2012-04-22
Like a noob, I tried adjusting my configurations to get Skype 2.2 to work in Lucid Lynx.  Instead, I now have no sound whatsoever.  Every tutorial and post I've looked at and tried has resulted in me getting more stuff of my computer and still nowhere.  Can someone help me?  I've already gone through the troubleshooter a million times and have tried to upgrade to alsa 1.0.23(?).  I've pretty much done everything on the first 3 pages of google search.  

Losing my mind....but loving it just the same.

Thanks
Doxa
:KS

I did this: 
aplay -l
aplay: device_list:240: no soundcards found...

Now what do I do?

---

### Post by GlazedWicker on 2012-04-22
Do you remember what the configurations were that you adjusted originally? 

Can you post the output to:
```
lspci -v | grep -A7 -i "audio"
```

---

### Post by Doxa on 2012-04-22
No, I don't.

aplay: device_list:240: no soundcards found...
doxa@Gloria:~$ lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 036e
    Flags: bus master, slow devsel, latency 0, IRQ 16
    Memory at f2300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: oss_hdaudio
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 036e
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01)
--
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Acer Incorporated [ALI] Device 036e
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f2210000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)

---

### Post by GlazedWicker on 2012-04-22
You can try resetting your sound with
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

(from Sound Troubleshooting)

If that doesn't work, try: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Doxa on 2012-04-22
Did this come out right?

doxa@Gloria:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
[sudo] password for doxa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-41-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-41-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.32-41-generic 
  linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/33.5MB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 227677 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-41-generic 2.6.32-41.88 (using .../linux-image-2.6.32-41-generic_2.6.32-41.88_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-41-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-41-generic
Found initrd image: /boot/initrd.img-2.6.32-41-generic
Found linux image: /boot/vmlinuz-2.6.32-40-generic
Found initrd image: /boot/initrd.img-2.6.32-40-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Preparing to replace alsa-base 1.0.24+dfsg-0ubuntu2~lucid1 (using .../alsa-base_1.0.24+dfsg-0ubuntu2~lucid1_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace alsa-utils 1.0.24.2-0ubuntu6~lucid. (using .../alsa-utils_1.0.24.2-0ubuntu6~lucid._i386.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace libasound2 1.0.24.1-0ubuntu6~lucid1 (using .../libasound2_1.0.24.1-0ubuntu6~lucid1_i386.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace linux-sound-base 1.0.24+dfsg-0ubuntu2~lucid1 (using .../linux-sound-base_1.0.24+dfsg-0ubuntu2~lucid1_all.deb) ...
Unpacking replacement linux-sound-base ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-2.6.32-41-generic (2.6.32-41.88) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-41-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-41.88 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-41.88 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-41-generic
Found initrd image: /boot/initrd.img-2.6.32-41-generic
Found linux image: /boot/vmlinuz-2.6.32-40-generic
Found initrd image: /boot/initrd.img-2.6.32-40-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-41-generic /boot/vmlinuz-2.6.32-41-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-41-generic /boot/vmlinuz-2.6.32-41-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-41-generic /boot/vmlinuz-2.6.32-41-generic

Setting up libasound2 (1.0.24.1-0ubuntu6~lucid1) ...

Setting up linux-sound-base (1.0.24+dfsg-0ubuntu2~lucid1) ...

Setting up alsa-base (1.0.24+dfsg-0ubuntu2~lucid1) ...

Setting up alsa-utils (1.0.24.2-0ubuntu6~lucid.) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by Doxa on 2012-04-22
rebooted and went to the HdaIntelSoundHowto page

doxa@Gloria:~$ cat /proc/asound/card0/codec* | grep Codec
cat: /proc/asound/card0/codec*: No such file or directory
doxa@Gloria:~$ 

I know I have AMD.

---

### Post by GlazedWicker on 2012-04-22
It looks like apt couldn't find some of the packages. I copied and pasted that straight from the wiki. I'm guessing it didn't fix anything? 

 Your sound card uses the hda-intel drivers.

try rebooting and do 
```
sudo modprobe snd-hda-intel
```

---

### Post by Doxa on 2012-04-22
nothing....

doxa@Gloria:~$ sudo modprobe snd-hda-intel
doxa@Gloria:~$

---

### Post by GlazedWicker on 2012-04-22
That means the correct kernel module is loaded. I'm not a pro at ALSA by any means, so I don't know how much more I can help you.  Is your ubuntu installation on a laptop? If so try installing gnome-alsamixer
```
sudo apt-get install gnome-alsamixer
```run it
```
gnome-alsamixer
```and make sure the correct sound device is listed, and that the front speakers are turned all the way up.

---

### Post by Doxa on 2012-04-22
Okay, did this one:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

got to the part about the kernels and I don't have matching kernels installed in Synaptic.

doxa@Gloria:~$ uname -r
2.6.32-41-generic

Should I revert to another version? 
My sound works, but I don't know if everything is set up correctly.

---

### Post by Doxa on 2012-04-22
okay, got it working.  Thanks.  :) Took me doing the same thing I did to undo it, but somehow it came together.
Pink Floyd time!

---

