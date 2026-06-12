---
title: "Monitor-brightness went nuts!"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by Citta on 2013-11-20
[COLOR=#000000]Hi everyone,
[/COLOR]
Monitor-brightness is not(worked just once!) via keyboard Fn-F5orF6 in-or decreasable-what might be the problem? The monitor is always on maximum brightness!
Or is there another way to adjust the brightness, did not find one!

Thanks for your help!

---

### Post by Toz on 2013-11-20
It would be helpful if you provided some more information, specifically:

[LIST=1]
[*]The make and model of your computer.

[*]The version of lubuntu that you are using.

[*]Your current kernel boot parameters:
```
cat /proc/cmdline
```
[*]Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```
[*]A listing of your backlight interfaces and the values of the associated brightness settings:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
[*]Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

[*]Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.
[*]
[/LIST]

*If you get a message stating that **pastebinit** is not installed, you can install it by searching for it in the Software Centre or by running the following command:
```
sudo apt-get install pastebinit
```

---

### Post by Citta on 2013-11-21
1. Vaionetbook VPCW21C7E
2. Lubuntu 13.10 Desktop
3. I assume the code you provided I have to write in a terminal(which one?-there are three terminals existing) then writing this down, enter, and paste the result here?
    I ask this, because I am unexperienced!
Thanks!

---

### Post by Toz on 2013-11-21
> 3. I assume the code you provided I have to write in a terminal(which one?-there are three terminals existing) then writing this down, enter, and paste the result here?
Yes. Any terminal will do. Paste the results back here.

---

### Post by Citta on 2013-11-25
Booting the OS from flashdrive resulted in the same problem-just a check.
 
I pasted the outputs of the terminal on Abiword, this file-type is not mentioned eligible as attachment, nevertheless I will try it. If it does not work-what to do?
Pastebin seems, according to the terminal-output, to exist. When searching via Softwarecenter-Installed Software, Pastebin does not exist. 

Should I install it, based on mentioned result?

PS: Indeed, attaching the Abi-file did not work-invalid!

---

### Post by Toz on 2013-11-25
For steps 3 to 5, just copy the results from the terminal and past back here as a reply.

For steps 6 & 7, first install pastebinit by running this command in a terminal (its a small useful program):
```
sudo apt-get install pastebinit
```
...enter your password when prompted, then run the above commands and post back the links that the program generates.

---

### Post by Citta on 2013-11-26
Now  I use the netbook for the reply, with the PC I could not open the Abiworddoc..Here are the results:

```
jane@jane:~$ cat/proc/cmdline
bash: cat/proc/cmdline: No such file or directory
```

```
jane@jane:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
    Subsystem: Sony Corporation Device 9066
    Kernel driver in use: i915
```

```
jane@jane:~$  for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat  $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/intel_backlight
26010
26010
26015
```

```
jane@jane:~$ pastebinit /var/log/dmesg
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>

jane@jane:~$ pastebinit /var/log/Xorg.0.log
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>


jane@jane:~$ sudo apt-get install <selected package>
bash: syntax error near unexpected token `newline'

The steps 5 & 6:  jane@jane:~$ sudo apt-get pastebinit
[sudo] password for jane: 
E: Invalid operation pastebinit
```

The Softwarecenter offered at first a Nautilus pastebinit, the second trial yielded no results.

Thanks a lot for your assistance!

---

### Post by Toz on 2013-11-26
From a terminal window:

```
sudo -i leafpad /usr/share/X11/xorg.conf.d/20-intel.conf
```
...enter your password when prompted, then copy/paste this content in:

```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"    "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

Save the file then reboot. 

*Make sure you enter the commands in properly, including all spacing. Better to copy and paste the commands.

*After you reboot, check the brightness and please post back the contents of the file you created (/usr/share/X11/xorg.conf.d/20-intel.conf) to confirm accuracy.

---

### Post by Citta on 2013-11-26
Here what I did: Opened terminal, pasted there the first code, a window popped up, second code pasted, clicked "save", reboot.
Brightnes uncontrollable.
Pasted /usr/....in the terminal:

```
jane@jane:~$ /usr/share/X11/xorg.conf.d/20-intel.conf
bash: /usr/share/X11/xorg.conf.d/20-intel.conf: Permission denied
```

---

### Post by Toz on 2013-11-26
Can you post back the contents of **/usr/share/X11/xorg.conf.d/20-intel.conf**?

Can you also post back a couple of log files like this:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by Citta on 2013-11-26
Here is the content: bash: /usr/share/X11/xorg.conf.d/20-intel.conf: Permission denied, as mentioned above. The requested results of the two codes I will post when Lubuntu is running.

---

### Post by Toz on 2013-11-26
> **Citta said:**
> Here is the content: bash: /usr/share/X11/xorg.conf.d/20-intel.conf: Permission denied, as mentioned above. The requested results of the two codes I will post when Lubuntu is running.

Sorry, I should have been clearer. Try this command:
```
pastebinit  /usr/share/X11/xorg.conf.d/20-intel.conf
```
...and post back the link that is generated.

In addition to the other 2.

---

### Post by Citta on 2013-11-26
```
jane@jane:~$ pastebinit  /usr/share/X11/xorg.conf.d/20-intel.conf
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>


jane@jane:~$ pastebinit /var/log/dmesg
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>

jane@jane:~$ pastebinit /var/log/Xorg.0.log
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>
```

Perhaps I misunderstood something...log files and link are to get in a different way?
By the way, for some time Ubuntu was installed, such a problem did not occure.

---

### Post by Toz on 2013-11-26
> **Citta said:**
> jane@jane:~$ pastebinit  /usr/share/X11/xorg.conf.d/20-intel.conf
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>


jane@jane:~$ pastebinit /var/log/dmesg
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>

jane@jane:~$ pastebinit /var/log/Xorg.0.log
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>

Perhaps I misunderstood something...log files and link are to get in a different way?
By the way, for some time Ubuntu was installed, such a problem did not occure.

You need to install pastebinit. Do it like this:
```
sudo apt-get install pastebinit
```
...enter your password when prompted. When done, run the previous 3 pastebinit commands.

---

### Post by Citta on 2013-11-28
Now the pastebinit-installation was successful, whatever the reason might be. Same commands before did not work.
Here are the links:

[http://paste.ubuntu.com/6489493/](http://paste.ubuntu.com/6489493/)
jane@jane:~$ pastebinit /var/log/dmesg
[http://paste.ubuntu.com/6489524/](http://paste.ubuntu.com/6489524/)
jane@jane:~$ pastebinit /var/log/Xorg.0.log
[http://paste.ubuntu.com/6489527/](http://paste.ubuntu.com/6489527/)

Thanks a lot for your help!

---

### Post by Toz on 2013-11-28
Can you try the **acpi_backlight=vendor** kernel parameter? Here is how (from a terminal):

1. Edit the configuration file:
```
sudo -i leafpad /etc/default/grub
```
...enter your password when prompted.

2. Change the line that reads:
> GRUB_CMDLINE_LINUX=""
...so that it says:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Commit the change:
```
sudo update-grub
```

5. Reboot your computer and try again.

*If it still doesn't work, can you post back again:
```
pastebinit /var/log/dmesg
```
...and
```
pastebinit /var/log/Xorg.0.log
```

---

### Post by Citta on 2013-11-28
Quite stubborn.....

[http://paste.ubuntu.com/6489993/](http://paste.ubuntu.com/6489993/)
[http://paste.ubuntu.com/6489996/](http://paste.ubuntu.com/6489996/)

Just in case you need this, too:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Toz on 2013-11-29
With the acpi_backlight=vendor parameter active, what does the following command now return:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

Can you also install xbacklight:
```
sudo apt-get install xbacklight
```
...and try adjusting the backlight via:
```
xbacklight -dec 10
xbacklight -inc 10
```
...and see if that changes the backlight?

---

### Post by Citta on 2013-12-03
Hello,

Unfortunately that did not work out, too.

---

### Post by Toz on 2013-12-03
With the acpi_backlight=vendor parameter active, what does the following command now return:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by Citta on 2013-12-03
```
jane@jane:~$  for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
26015
26015
26015
/sys/class/backlight/sony
7
7
7
```

---

### Post by Toz on 2013-12-03
Ahh, now there is a sony backlight interface. Here are a couple of things to try:

1. Try deleting the **/usr/share/X11/xorg.conf.d/20-intel.conf** file:
```
sudo rm /usr/share/X11/xorg.conf.d/20-intel.conf
```
...logging out and back in again. Do brightness controls work now?



2. Try unloading the sony-laptop module:
```
sudo modprobe -r sony-laptop
```
...(post back any error messages if they occur) and log out and back in again. Do brightness controls work now?

---

### Post by Citta on 2013-12-03
The monitor still behaves as before.
The results:

```
jane@jane:~$ sudo rm /usr/share/X11/xorg.conf.d/20-intel.conf
rm: cannot remove &#8216;/usr/share/X11/xorg.conf.d/20-intel.conf&#8217;: No such file or directory

jane@jane:~$ sudo modprobe -r sony-laptop
[sudo] password for jane: 
jane@jane:~$ 
jane@jane:~$ sudo modprobe -r sony-laptop
jane@jane:~$
```

---

### Post by Toz on 2013-12-03
> **Citta said:**
> 
jane@jane:~$ sudo rm /usr/share/X11/xorg.conf.d/20-intel.conf
rm: cannot remove ‘/usr/share/X11/xorg.conf.d/20-intel.conf’: No such file or directory
Hmmm, we created this file in post #8. Did you delete it before?

> jane@jane:~$ sudo modprobe -r sony-laptop
[sudo] password for jane: 
jane@jane:~$ 
jane@jane:~$ sudo modprobe -r sony-laptop
jane@jane:~$
Try again:
```
sudo modprobe -r sony-laptop
lsmod | grep sony
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
cat /proc/cmdline
```

---

### Post by Citta on 2013-12-05
Hello,

No, I do not know how to this nor I would dare it, considering my knowledge!
What the terminal spit out:

```
jane@jane:~$ sudo modprobe -r sony-laptop
jane@jane:~$ lsmod | grep sony
jane@jane:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
26010
26010
26015
jane@jane:~$ cat /proc/cmdline
```

---

### Post by Toz on 2013-12-05
Do the backlight controls work now? 

If not, try this:
```
sudo -i leafpad /etc/modprobe.d/blacklist.conf
```
...and append to the end of the file:
```
blacklist sony-laptop
```
...save the file and reboot.



On reboot, test the backlight controls.

Also post back again:
```
lsmod | grep sony
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
cat /proc/cmdline
```

And finally, run the following command and let me know if the brightness changes:
```
echo 13000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

---

### Post by Citta on 2013-12-05
After entering the first code a white window popped up, labeled as (blacklist). As the window was empty I did not apppend the second code, because, as mentioned, no file inside.

---

### Post by Toz on 2013-12-05
> **Citta said:**
> After entering the first code a white window popped up, labeled as (blacklist). As the window was empty I did not apppend the second code, because, as mentioned, no file inside.

Sorry, my bad. The file should be **/etc/modprobe.d/blacklist.conf**. I'll update my last post with the correct info.

---

### Post by Citta on 2013-12-10
It seems the problem is not solvable. For getting some learning out of all this futile work, what would be the headline and where can  I find information, manuals, etc.?
Last, but not least, how can I remove Lubuntu without leftovers, finishing my excursion to Linux?

---

### Post by Toz on 2013-12-10
So, with sony-laptop blacklisted, is it not running:
```
lsmod | grep sony-laptop
```
...and if so, still no control of the brightness?

You could also give /usr/share/X11/xorg.conf.d/20-intel.conf one more try to see if you can force it to use the intel backlight interface.

> **Citta said:**
> It seems the problem is not solvable. For getting some learning out of all this futile work, what would be the headline and where can  I find information, manuals, etc.?
There is an Ubuntu Backlight wiki entry [here]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight").
> Last, but not least, how can I remove Lubuntu without leftovers, finishing my excursion to Linux?
There is a [step-by-step guide here]("http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on") that should help.

---

### Post by Citta on 2013-12-10
I repeated the commands from #26, this time the blacklist was not empty, so I appended the command.
That resulted in a greyish appearance of Firefox and Abiword. Here the terminal:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist sony-laptop
```

The result from # 30:

```
ane@jane:~$ sudo -i leafpad /etc/modprobe.d/blacklist.conf
[sudo] password for jane: 
jane@jane:~$ lsmod | grep sony
jane@jane:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
26015
26015
26015
jane@jane:~$ cat /proc/cmdlineecho 13000 | sudo tee /sys/class/backlight/intel_backlight/brightness
cat: /proc/cmdlineecho: No such file or directory
cat: 13000: No such file or directory
[sudo] password for jane: 
jane@jane:~$ 
jane@jane:~$ echo 13000 | sudo tee /sys/class/backlight/intel_backlight/brightness
13000
jane@jane:~$ 
```

Brighness is uncontrolable!

---

### Post by Toz on 2013-12-10
Okay then. First, remove the "blacklist sony-laptop" from the **/etc/modprobe.d/blacklist.conf** file and reboot.

Secondly, repeat the instructions from post #8. Specifically:
Create the config file:
```

sudo -i leafpad /usr/share/X11/xorg.conf.d/20-intel.conf
```
...enter your password when prompted, then copy/paste this content in:
```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"    "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
..and reboot the system.



After reboot, post back:
```
lsmod
```
```
cat /proc/cmdline
```
```
cat /usr/share/X11/xorg.conf.d/20-intel.conf
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
...and test the brightness both with the function keys and the brightness slider.

---

### Post by Citta on 2013-12-12
Brightness via function keys uncontrolable, the slider....I do not know where it is, under Lubuntu, under Win there are few clicks required to go there.

Here the results:

```
jane@jane:~$ lsmod
Module                  Size  Used by
zram                   18070  2 
vesafb                 13500  0 
coretemp               13195  0 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
arc4                   12536  2 
ath9k                 135969  0 
ath9k_common           13619  1 ath9k
ath9k_hw              429197  2 ath9k_common,ath9k
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
microcode              18830  0 
mac80211              513247  1 ath9k
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
joydev                 17097  0 
psmouse                90642  0 
serio_raw              13189  0 
lpc_ich                16864  0 
snd_hda_codec_realtek    45592  1 
i915                  589697  2 
cfg80211              401436  3 ath,ath9k,mac80211
drm_kms_helper         46867  1 i915
snd_hda_intel          42658  1 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
mac_hid                13037  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
drm                   242354  3 i915,drm_kms_helper
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
video                  18777  1 i915
snd                    60790  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
sdhci_pci              18481  0 
sdhci                  37468  1 sdhci_pci
atl1c                  40949  0 
jane@jane:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=73468c33-4a9c-4f5c-bbdf-e68c7e1046c4 ro acpi_backlight=vendor quiet splash vt.handoff=7
jane@jane:~$ cat /usr/share/X11/xorg.conf.d/20-intel.conf
cat: /usr/share/X11/xorg.conf.d/20-intel.conf: No such file or directory
jane@jane:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
26015
26015
26015
jane@jane:~$ 
```
Thanks for your patience!

---

### Post by Toz on 2013-12-12
> jane@jane:~$ cat /usr/share/X11/xorg.conf.d/20-intel.conf
cat: /usr/share/X11/xorg.conf.d/20-intel.conf: [COLOR="#FF0000"]**No such file or directory**[/COLOR]
You need to create this file as per the instructions.

I don't see **sony-laptop** in your modules list. Did you delete the "blacklist sony-laptop" line from **/etc/modprobe.d/blacklist.conf**?

Please re-try the instructions in post #32.

---

### Post by Citta on 2013-12-12
In one of your posts you adviced me to delete the last line of code, I believe it was the mentioned one. I highlighted this line-delete. I repeated #8, #32. 

```
jane@jane:~$  /etc/modprobe.d/blacklist.conf 
bash: /etc/modprobe.d/blacklist.conf: Permission denied
```
```
jane@jane:~$ lsmod
Module                  Size  Used by
zram                   18070  2 
coretemp               13195  0 
snd_hda_codec_realtek    45592  1 
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18893  2 
bluetooth             323622  10 bnep,rfcomm
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
arc4                   12536  2 
joydev                 17097  0 
snd_hda_intel          42658  1 
ath9k                 135969  0 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
ath9k_common           13619  1 ath9k
snd_hwdep              13272  1 snd_hda_codec
ath9k_hw              429197  2 ath9k_common,ath9k
microcode              18830  0 
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
mac80211              513247  1 ath9k
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
psmouse                90642  0 
serio_raw              13189  0 
lpc_ich                16864  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  589697  2 
snd_rawmidi            25094  1 snd_seq_midi
cfg80211              401436  3 ath,ath9k,mac80211
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         46867  1 i915
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
drm                   242354  3 i915,drm_kms_helper
snd                    60790  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac_hid                13037  0 
video                  18777  1 i915
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
sdhci_pci              18481  0 
sdhci                  37468  1 sdhci_pci
atl1c                  40949  0 
jane@jane:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=73468c33-4a9c-4f5c-bbdf-e68c7e1046c4 ro acpi_backlight=vendor quiet splash vt.handoff=7
```
```
jane@jane:~$ cat /usr/share/X11/xorg.conf.d/20-intel.conf
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"    "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
``````
jane@jane:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brigh $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
26015
26015
```

---

### Post by Toz on 2013-12-12
Do the brightness controls (Fn+F5 & Fn+F6) work?

Do the following commands change the brightness?
```
echo 13000 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 26000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

What does the following return?
```
cat /etc/modprobe.d/blacklist.conf 
```

---

### Post by Citta on 2013-12-12
Yes, after pasting this 2 lines of code, brightness was reduced!
After "enter" it returned to full brightness. I use always the function keys, without effect. I do not know another way.
Here the output:

```
jane@jane:~$ echo 13000 | sudo tee /sys/class/backlight/intel_backlight/brightness
13000
jane@jane:~$ echo 26000 | sudo tee /sys/class/backlight/intel_backlight/brightness
26000
```
```
jane@jane:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist sony-laptop


jane@jane:~$
```

---

### Post by Toz on 2013-12-12
> **Citta said:**
> Yes, after pasting this 2 lines of code, brightness was reduced!
After "enter" it returned to full brightness. I use always the function keys, without effect. I do not know another way.
Here the output:

jane@jane:~$ echo 13000 | sudo tee /sys/class/backlight/intel_backlight/brightness
13000
jane@jane:~$ echo 26000 | sudo tee /sys/class/backlight/intel_backlight/brightness
26000

Good. now lets have a look to see why the brightness keys don't work. In a terminal window, execute the following line of code:
```
sudo acpi_listen
```
...(enter your password when prompted) and then press the FN+F5 and then the FN+F6 key combinations. Post back what codes are displayed in the terminal window.

---

### Post by Citta on 2013-12-12
Resulted in the following output:

```
jane@jane:~$ sudo acpi_listen
[sudo] password for jane: 
sudo: acpi_listen: command not found
```

---

### Post by Toz on 2013-12-12
> **Citta said:**
> Resulted in the following output:

jane@jane:~$ sudo acpi_listen
[sudo] password for jane: 
sudo: acpi_listen: command not found

acpid is not installed in lubuntu 13.10 by default (I just checked the manifest file)? I don't use lubuntu, but I find that really odd. I remember an eary beta of Xubuntu that omitted that package but we had it added before the release.

Can you try installing acpid?
```
sudo apt-get install acpid
```
...then reboot and try your brightness function keys.

---

### Post by Citta on 2013-12-12
Installation done, brightness uncontrollable!

---

### Post by Toz on 2013-12-12
> **Citta said:**
> Installation done, brightness uncontrollable!
Do the brightness keys work?

What backlight interfaces do you have?
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```

Does this command lower the brightness?
```
echo 13000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

And finally, run:
```
sudo acpi_listen
```
...in a terminal window, press the FN+F5 and FN+F6 key combinations and post back what codes appear in the terminal window.

---

### Post by Citta on 2013-12-12
The second code lowered brightness. Last one, hm, left the cursor just below the code, after "enter"....

jane@jane:~$ for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
/sys/class/backlight/intel_backlight
26015
26015
jane@jane:~$ echo 13000 | sudo tee /sys/class/backlight/intel_backlight/brightness
[sudo] password for jane: 
13000
jane@jane:~$ sudo acpi_listen

---

### Post by Toz on 2013-12-12
> Last one, hm, left the cursor just below the code, after "enter"....
So acpi isn't registering any key presses - which is why brightness keys aren't working. The bios is handling these commands and they're not properly being translated. 

Lets try to see if X can pick up the key presses. Enter this code into a terminal window:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
...press FN+F5 then FN+F6 and post back any codes that appear in the terminal window.

---

### Post by Citta on 2013-12-12
"Event Tester" popped up-the key-strokes are without effect, later, during the time I wrote the post and took  a look at the terminal:

jane@jane:~$ xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
38 a
38 a
38 a

---

### Post by Toz on 2013-12-12
Can you try:
```
xbacklight -dec 25
xbacklight -inc 25
```
...to see if that changes your brightness.

If you get a message that xbacklight is not installed, you can install it via:
```
sudo apt-get install xbacklight
```

---

### Post by Citta on 2013-12-12
Yes, it in-and decreased brightness.

---

### Post by Toz on 2013-12-12
Okay then. You can use xbacklight to increase and decrease brightness for the time being.

I'm not exactly sure why you're function keys are not being picked up. Can you look into the bios of your machine to see if there are any settings related to the function keys? Maybe something that will help to enable them to work inside Linux?

---

### Post by Citta on 2013-12-13
Had a look into bios. It is pretty simple, just a few options, nothing for function keys. It is InsydeH2O bios.
After installation those function keys worked as to be expected, a small bar popped up, with a sun-symbol. Later nothing worked, whatever the reason might be, I believe I mentioned that in the beginning.

---

### Post by Toz on 2013-12-13
> **Citta said:**
> Had a look into bios. It is pretty simple, just a few options, nothing for function keys. It is InsydeH2O bios.
After installation those function keys worked as to be expected, a small bar popped up, with a sun-symbol. Later nothing worked, whatever the reason might be, I believe I mentioned that in the beginning.
Yes you did, you stated that it worked once and then stopped. Perhaps it was a kernel update that changed it.

Can I have another look at your kernel command line? Post back the results of:
```
cat /proc/cmdline
```

---

### Post by Toz on 2013-12-13
Lets try re-enabling the sony-laptop module:
```
sudo -i leafpad /etc/modprobe.d/blacklist.conf 
```
...and delete the line that says **blacklist sony-laptop** then save the file.

```
cat /etc/modprobe.d/blacklist.conf
```

Reboot.

```
lsmod
```
Try your function brightness keys. Do they work?

Do these commands still work:
```
xbacklight -dec 25
xbacklight -inc 25
```
...to lower and raise the brightness.

```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```

```
cat /proc/cmdline
```

---

### Post by Citta on 2013-12-13
Function keys did not work.
Inc/dec brightness via terminal worked.

Terminal:

```
jane@jane:~$ for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
/sys/class/backlight/intel_backlight
19510
26015
/sys/class/backlight/sony
7
7
```
```
jane@jane:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=73468c33-4a9c-4f5c-bbdf-e68c7e1046c4 ro acpi_backlight=vendor quiet splash vt.handoff=7
```

---

### Post by Toz on 2013-12-13
Thanks.

Next, lets add another kernel parameter.
```
sudo -i leafpad /etc/default/grub
```
...and change the lines that read:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
...to read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
...save the file and run:
```
sudo update-grub
```

Reboot.

Post back:
```
cat /proc/cmdline
```
...and check if function keys work.

Also:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
...and press FN+F5 & FN+F6 and post back if any codes appear in the terminal window.

---

### Post by Citta on 2013-12-13
Changing this lines does mean to delete the two lines and replacing them as adviced in your post!?

```
jane@jane:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=73468c33-4a9c-4f5c-bbdf-e68c7e1046c4 ro acpi_osi=Linux acpi_backlight=vendor quiet splash vt.handoff=7
jane@jane:~$ 
```

Function did not work.

The output of the last command:

```
jane@jane:~$ xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
232 XF86MonBrightnessDown
233 XF86MonBrightnessUp
```

---

### Post by Toz on 2013-12-13
Yes and we have a response - the keys are being recognized! 

Try blacklisting sony-laptop again and see if it works:
```
sudo -i leafpad /etc/modprobe.d/blacklist.conf
```
...and add:
```
blacklist sony-laptop
```
...to the end of the file. Save the file.

Reboot.

Then:
```
cat /proc/cmdline
```
```
lsmod  |grep sony
```
```
cat /etc/modprobe.d/blacklist.conf
```
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```
...and try the brightness function keys.

---

### Post by Citta on 2013-12-13
The keys still do not obey-just cooked mushrooms and ate them...no, they were not magic!

Output:

```
jane@jane:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=73468c33-4a9c-4f5c-bbdf-e68c7e1046c4 ro acpi_osi=Linux acpi_backlight=vendor quiet splash vt.handoff=7
```
```
jane@jane:~$ lsmod  |grep sony
```
```
jane@jane:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist sony-laptop
```


```
jane@jane:~$ for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
/sys/class/backlight/intel_backlight
26015
26015
```

---

### Post by Toz on 2013-12-13
Okay, good. Now we know that they still aren't being picked up automatically even with one backlight interface. 

We need to add this code:
```

<!-- Keybindings for brightness control -->
<keybind key="XF86MonBrightnessUp">
     <action name="Execute">
       <command>xbacklight +10</command>
     </action>
</keybind>
<keybind key="XF86MonBrightnessDown">
     <action name="Execute">
       <command>xbacklight -10</command>
     </action>
</keybind>
```
...to the **<keyboard>** section of your **~/.config/openbox/rc.xml ** configuration file.

If you like, post back the contents of your ~/.config/openbox/rc.xml file and I can help show you where to enter in the snippet. 

This snippet will direct openbox to respong to your FN+F5 & FN+F6 key combinations by running the xbacklight command to increase or decrease the brightness.

---

### Post by Citta on 2013-12-17
Ok, the story continues, the output of the terminal:

jane@jane:~$  ~/.config/openbox/rc.xml 
bash: /home/jane/.config/openbox/rc.xml: No such file or directory
jane@jane:~$

---

### Post by Toz on 2013-12-17
Just installed lubuntu in a VM to have a closer look. It looks like the file is named **~/.config/openbox/lubuntu-rc.xml**.

So, try instead:
```
leafpad ~/.config/openbox/lubuntu-rc.xml
```

(sorry, I don't use lubuntu).

---

### Post by Citta on 2013-12-17
That  worked, I did find the keyboard section. I am not sure, where to add  this snippet, at the end, after " keyboard" and before "mouse"?
```

<?xml version="1.0" encoding="UTF-8"?>
<!-- Do not edit this file, it will be overwritten on install.
        Copy the file to $HOME/.config/openbox/ instead. -->
<openbox_config xmlns="http://openbox.org/3.4/rc" xmlns:xi="http://www.w3.org/2001/XInclude">
  <resistance>
    <strength>10</strength>
    <screen_edge_strength>20</screen_edge_strength>
  </resistance>
  <focus>
    <focusNew>yes</focusNew>
    <!-- always try to focus new windows when they appear. other rules do
       apply -->
    <followMouse>no</followMouse>
    <!-- move focus to a window when you move the mouse into it -->
    <focusLast>yes</focusLast>
    <!-- focus the last used window when changing desktops, instead of the one
       under the mouse pointer. when followMouse is enabled -->
    <underMouse>no</underMouse>
    <!-- move focus under the mouse, even when the mouse is not moving -->
    <focusDelay>200</focusDelay>
    <!-- when followMouse is enabled, the mouse must be inside the window for
       this many milliseconds (1000 = 1 sec) before moving focus to it -->
    <raiseOnFocus>no</raiseOnFocus>
    <!-- when followMouse is enabled, and a window is given focus by moving the
       mouse into it, also raise the window -->
  </focus>
  <placement>
    <policy>Smart</policy>
    <!-- 'Smart' or 'UnderMouse' -->
    <center>yes</center>
    <!-- whether to place windows in the center of the free area found or
       the top left corner -->
    <monitor>Mouse</monitor>
    <!-- with Smart placement on a multi-monitor system, try to place new windows
       on: 'Any' - any monitor, 'Mouse' - where the mouse is, 'Active' - where
       the active window is, 'Primary' - only on the primary monitor -->
    <primaryMonitor>Mouse</primaryMonitor>
    <!-- The monitor where Openbox should place popup dialogs such as the
       focus cycling popup, or the desktop switch popup.  It can be an index
       from 1, specifying a particular monitor.  Or it can be one of the
       following: 'Mouse' - where the mouse is, or
                  'Active' - where the active window is -->
  </placement>
  <theme>
    <name>Lubuntu-default</name>
    <titleLayout>NLIMC</titleLayout>
    <!--
      available characters are NDSLIMC, each can occur at most once.
      N: window icon
      L: window label (AKA title).
      I: iconify
      M: maximize
      C: close
      S: shade (roll up/down)
      D: omnipresent (on all desktops).
  -->
    <keepBorder>yes</keepBorder>
    <animateIconify>yes</animateIconify>
    <font place="ActiveWindow">
      <name>Ubuntu Medium</name>
      <size>11</size>
      <!-- font size in points -->
      <weight>bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="InactiveWindow">
      <name>Ubuntu Medium</name>
      <size>11</size>
      <!-- font size in points -->
      <weight>bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuHeader">
      <name>Ubuntu</name>
      <size>11</size>
      <!-- font size in points -->
      <weight>normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuItem">
      <name>Ubuntu</name>
      <size>11</size>
      <!-- font size in points -->
      <weight>normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="ActiveOnScreenDisplay">
      <name>Ubuntu Medium</name>
      <size>11</size>
      <!-- font size in points -->
      <weight>bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="InactiveOnScreenDisplay">
      <name>Ubuntu Medium</name>
      <size>11</size>
      <!-- font size in points -->
      <weight>bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
  </theme>
  <desktops>
    <!-- this stuff is only used at startup, pagers allow you to change them
       during a session

       these are default values to use when other ones are not already set
       by other applications, or saved in your session

       use obconf if you want to change these without having to log out
       and back in -->
    <number>2</number>
    <firstdesk>1</firstdesk>
    <names>
      <!-- set names up here if you want to, like this:
    <name>desktop 1</name>
    <name>desktop 2</name>
    -->
    </names>
    <popupTime>875</popupTime>
    <!-- The number of milliseconds to show the popup for when switching
       desktops.  Set this to 0 to disable the popup. -->
  </desktops>
  <resize>
    <drawContents>no</drawContents>
    <popupShow>Nonpixel</popupShow>
    <!-- 'Always', 'Never', or 'Nonpixel' (xterms and such) -->
    <popupPosition>Center</popupPosition>
    <!-- 'Center', 'Top', or 'Fixed' -->
    <popupFixedPosition>
      <!-- these are used if popupPosition is set to 'Fixed' -->
      <x>10</x>
      <!-- positive number for distance from left edge, negative number for
         distance from right edge, or 'Center' -->
      <y>10</y>
      <!-- positive number for distance from top edge, negative number for
         distance from bottom edge, or 'Center' -->
    </popupFixedPosition>
  </resize>
  <!-- You can reserve a portion of your screen where windows will not cover when
     they are maximized, or when they are initially placed.
     Many programs reserve space automatically, but you can use this in other
     cases. -->
  <margins>
    <top>0</top>
    <bottom>0</bottom>
    <left>0</left>
    <right>0</right>
  </margins>
  <dock>
    <position>TopLeft</position>
    <!-- (Top|Bottom)(Left|Right|)|Top|Bottom|Left|Right|Floating -->
    <floatingX>0</floatingX>
    <floatingY>0</floatingY>
    <noStrut>no</noStrut>
    <stacking>Above</stacking>
    <!-- 'Above', 'Normal', or 'Below' -->
    <direction>Vertical</direction>
    <!-- 'Vertical' or 'Horizontal' -->
    <autoHide>no</autoHide>
    <hideDelay>300</hideDelay>
    <!-- in milliseconds (1000 = 1 second) -->
    <showDelay>300</showDelay>
    <!-- in milliseconds (1000 = 1 second) -->
    <moveButton>Middle</moveButton>
    <!-- 'Left', 'Middle', 'Right' -->
  </dock>
  <keyboard>
    <chainQuitKey>C-g</chainQuitKey>
    <!-- Keybindings for desktop switching -->
    <keybind key="C-A-Left">
      <action name="GoToDesktop">
        <to>left</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Right">
      <action name="GoToDesktop">
        <to>right</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Up">
      <action name="GoToDesktop">
        <to>up</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Down">
      <action name="GoToDesktop">
        <to>down</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Left">
      <action name="SendToDesktop">
        <to>left</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Right">
      <action name="SendToDesktop">
        <to>right</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Up">
      <action name="SendToDesktop">
        <to>up</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Down">
      <action name="SendToDesktop">
        <to>down</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="W-F1">
      <action name="GoToDesktop">
        <to>1</to>
      </action>
    </keybind>
    <keybind key="W-F2">
      <action name="GoToDesktop">
        <to>2</to>
      </action>
    </keybind>
    <keybind key="W-F3">
      <action name="GoToDesktop">
        <to>3</to>
      </action>
    </keybind>
    <keybind key="W-F4">
      <action name="GoToDesktop">
        <to>4</to>
      </action>
    </keybind>
    <keybind key="W-d">
      <action name="ToggleShowDesktop"/>
    </keybind>
    <!-- Keybindings for windows -->
    <keybind key="A-F4">
      <action name="Close"/>
    </keybind>
    <keybind key="A-Escape">
      <action name="Lower"/>
      <action name="FocusToBottom"/>
      <action name="Unfocus"/>
    </keybind>
    <keybind key="A-space">
      <action name="ShowMenu">
        <menu>client-menu</menu>
      </action>
    </keybind>
    <!-- Take a screenshot of the current window with scrot when Alt+Print are pressed -->
    <keybind key="A-Print">
      <action name="Execute">
        <command>lxsession-default screenshot window</command>
      </action>
    </keybind>
    <!-- Keybindings for window switching -->
    <keybind key="A-Tab">
      <action name="NextWindow">
        <dialog>icons</dialog>
        <finalactions>
          <action name="Focus"/>
          <action name="Raise"/>
          <action name="Unshade"/>
        </finalactions>
      </action>
    </keybind>
    <keybind key="A-S-Tab">
      <action name="PreviousWindow">
        <finalactions>
          <action name="Focus"/>
          <action name="Raise"/>
          <action name="Unshade"/>
        </finalactions>
      </action>
    </keybind>
    <keybind key="C-A-Tab">
      <action name="NextWindow">
        <panels>yes</panels>
        <desktop>yes</desktop>
        <finalactions>
          <action name="Focus"/>
          <action name="Raise"/>
          <action name="Unshade"/>
        </finalactions>
      </action>
    </keybind>
    <!-- Keybindings for window switching with the arrow keys -->
    <keybind key="W-S-Right">
      <action name="DirectionalCycleWindows">
        <direction>right</direction>
      </action>
    </keybind>
    <keybind key="W-S-Left">
      <action name="DirectionalCycleWindows">
        <direction>left</direction>
      </action>
    </keybind>
    <keybind key="W-S-Up">
      <action name="DirectionalCycleWindows">
        <direction>up</direction>
      </action>
    </keybind>
    <keybind key="W-S-Down">
      <action name="DirectionalCycleWindows">
        <direction>down</direction>
      </action>
    </keybind>
    <!-- Keybindings for window tiling -->
    <keybind key="W-Left">        # HalfLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <height>97%</height>
        <width>50%</width>
      </action>
    </keybind>
    <keybind key="W-Right">        # HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <height>97%</height>
        <width>50%</width>
      </action>
    </keybind>
    <keybind key="W-Up">        # HalfUpperScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>100%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-Down">        # HalfLowerScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>100%</width>
        <height>50%</height>
      </action>
    </keybind>
    <!-- Keybindings for running applications on Home + E -->
    <keybind key="W-e">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>PCManFM</name>
        </startupnotify>
        <command>pcmanfm</command>
      </action>
    </keybind>
    <!-- Keybindings for running Run menu from Lxpanel on Home + R-->
    <keybind key="W-r">
      <action name="Execute">
        <command>lxpanelctl run</command>
      </action>
    </keybind>
    <keybind key="A-F2">
      <action name="Execute">
        <command>lxpanelctl run</command>
      </action>
    </keybind>
    <!-- Keybindings for running Menu from Lxpanel -->
    <keybind key="A-F1">
      <action name="Execute">
        <command>lxpanelctl menu</command>
      </action>
    </keybind>
    <keybind key="C-Escape">
      <action name="Execute">
        <command>lxpanelctl menu</command>
      </action>
    </keybind>
    <!-- Keybindings to toggle fullscreen -->
    <keybind key="F11">
      <action name="ToggleFullscreen"/>
    </keybind>
    <!-- Launch task manager on Ctrl + Alt + Del-->
    <keybind key="C-A-Delete">
      <action name="Execute">
        <command>lxtask</command>
      </action>
    </keybind>
    <!-- Launch a terminal on Ctrl + Alt + T-->
    <keybind key="C-A-T">
      <action name="Execute">
        <command>lxsession-default terminal</command>
      </action>
    </keybind>
    <!-- Launch a filemanager on Ctrl + Alt + D-->
    <keybind key="C-A-D">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>PCManFM</name>
        </startupnotify>
        <command>pcmanfm</command>
      </action>
    </keybind>
    <!-- Lock the screen on Ctrl + Alt + l-->
    <keybind key="C-A-l">
      <action name="Execute">
        <command>xscreensaver-command -lock</command>
      </action>
    </keybind>
    <!-- Keybinding for Volume management -->
    <keybind key="XF86AudioRaiseVolume">
        <action name="Execute">
            <command>amixer -q sset Master 3%+ unmute</command>
        </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
        <action name="Execute">
            <command>amixer -q sset Master 3%- unmute</command>
        </action>
    </keybind>
    <keybind key="XF86AudioMute">
        <action name="Execute">
            <command>amixer -q sset Master toggle</command>
        </action>
    </keybind>
    <!-- Keybinding for terminal button-->
    <keybind key="XF86WWW">
      <action name="Execute">
        <command>lxsession-default terminal</command>
      </action>
    </keybind>
    <keybind key="XF86Terminal">
      <action name="Execute">
        <command>lxsession-default terminal</command>
      </action>
    </keybind>
    <!-- Keybinding for calculator button-->
    <keybind key="XF86Calculator">
      <action name="Execute">
        <command>galculator</command>
      </action>
    </keybind>
    <!-- Keybinding for computer button-->
    <keybind key="XF86MyComputer">
      <action name="Execute">
        <command>pcmanfm</command>
      </action>
    </keybind>
     <!-- Keybindings for Multimedia Keys and LCD Backlight (alternative  when not using gnome-power-manager or xfce4-volumed) -->
    <keybind key="C-F7">
      <action name="Execute">
        <command>sleep 2;xset dpms force off</command>
      </action>
    </keybind>
    <keybind key="C-F10">
      <action name="Execute">
        <command>xbacklight -dec 10</command>
      </action>
    </keybind>
    <keybind key="C-F11">
      <action name="Execute">
        <command>xbacklight -inc 10</command>
      </action>
    </keybind>
    <!-- Launch scrot when Print is pressed -->
    <keybind key="Print">
      <action name="Execute">
        <command>lxsession-default screenshot</command>
      </action>
    </keybind>
    <!-- Launch logout when push on the shutdown button -->
    <keybind key="XF86PowerOff">
      <action name="Execute">
        <command>lxsession-default quit</command>
      </action>
    </keybind>
  </keyboard>
  <mouse>
    <dragThreshold>8</dragThreshold>
    <!-- number of pixels the mouse must move before a drag begins -->
    <doubleClickTime>200</doubleClickTime>
    <!-- in milliseconds (1000 = 1 second) -->
    <screenEdgeWarpTime>400</screenEdgeWarpTime>
    <!-- Time before changing desktops when the pointer touches the edge of the
       screen while moving a window, in milliseconds (1000 = 1 second).
       Set this to 0 to disable warping -->
    <screenEdgeWarpMouse>false</screenEdgeWarpMouse>
    <!-- Set this to TRUE to move the mouse pointer across the desktop when
       switching due to hitting the edge of the screen -->
    <context name="Frame">
      <mousebind button="A-Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="A-Left" action="Click">
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="A-Left" action="Drag">
        <action name="Move"/>
      </mousebind>
      <mousebind button="A-Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="A-Right" action="Drag">
        <action name="Resize"/>
      </mousebind>
      <mousebind button="A-Middle" action="Press">
        <action name="Lower"/>
        <action name="FocusToBottom"/>
        <action name="Unfocus"/>
      </mousebind>
      <mousebind button="A-Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="A-Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
      <mousebind button="C-A-Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="C-A-Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
      <mousebind button="A-S-Up" action="Click">
        <action name="SendToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="A-S-Down" action="Click">
        <action name="SendToDesktop">
          <to>next</to>
        </action>
      </mousebind>
    </context>
    <context name="Titlebar">
      <mousebind button="Left" action="Drag">
        <action name="Move"/>
      </mousebind>
      <mousebind button="Left" action="DoubleClick">
        <action name="ToggleMaximize"/>
      </mousebind>
      <mousebind button="Up" action="Click">
        <action name="if">
          <shaded>no</shaded>
          <then>
            <action name="Shade"/>
            <action name="FocusToBottom"/>
            <action name="Unfocus"/>
            <action name="Lower"/>
          </then>
        </action>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="if">
          <shaded>yes</shaded>
          <then>
            <action name="Unshade"/>
            <action name="Raise"/>
          </then>
        </action>
      </mousebind>
    </context>
    <context name="Titlebar Top Right Bottom Left TLCorner TRCorner BRCorner BLCorner">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Middle" action="Press">
        <action name="Lower"/>
        <action name="FocusToBottom"/>
        <action name="Unfocus"/>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="ShowMenu">
          <menu>client-menu</menu>
        </action>
      </mousebind>
    </context>
    <context name="Top">
      <mousebind button="Left" action="Drag">
        <action name="Resize">
          <edge>top</edge>
        </action>
      </mousebind>
    </context>
    <context name="Left">
      <mousebind button="Left" action="Drag">
        <action name="Resize">
          <edge>left</edge>
        </action>
      </mousebind>
    </context>
    <context name="Right">
      <mousebind button="Left" action="Drag">
        <action name="Resize">
          <edge>right</edge>
        </action>
      </mousebind>
    </context>
    <context name="Bottom">
      <mousebind button="Left" action="Drag">
        <action name="Resize">
          <edge>bottom</edge>
        </action>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="ShowMenu">
          <menu>client-menu</menu>
        </action>
      </mousebind>
    </context>
    <context name="TRCorner BRCorner TLCorner BLCorner">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize"/>
      </mousebind>
    </context>
    <context name="Client">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Middle" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
    </context>
    <context name="Icon">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
        <action name="ShowMenu">
          <menu>client-menu</menu>
        </action>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="ShowMenu">
          <menu>client-menu</menu>
        </action>
      </mousebind>
    </context>
    <context name="AllDesktops">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="ToggleOmnipresent"/>
      </mousebind>
    </context>
    <context name="Shade">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="ToggleShade"/>
      </mousebind>
    </context>
    <context name="Iconify">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="Iconify"/>
      </mousebind>
    </context>
    <context name="Maximize">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Middle" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="ToggleMaximize"/>
      </mousebind>
      <mousebind button="Middle" action="Click">
        <action name="ToggleMaximize">
          <direction>vertical</direction>
        </action>
      </mousebind>
      <mousebind button="Right" action="Click">
        <action name="ToggleMaximize">
          <direction>horizontal</direction>
        </action>
      </mousebind>
    </context>
    <context name="Close">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="Close"/>
      </mousebind>
    </context>
    <context name="Desktop">
      <mousebind button="Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
      <mousebind button="A-Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="A-Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
      <mousebind button="C-A-Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="C-A-Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
    </context>
    <context name="Root">
      <!-- Menus -->
      <mousebind button="Middle" action="Press">
        <action name="ShowMenu">
          <menu>client-list-combined-menu</menu>
        </action>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="ShowMenu">
          <menu>root-menu</menu>
        </action>
      </mousebind>
    </context>
    <context name="MoveResize">
      <mousebind button="Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
      <mousebind button="A-Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="A-Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
    </context>
  </mouse>
  <menu>
    <!-- You can specify more than one menu file in here and they are all loaded,
       just don't make menu ids clash or, well, it'll be kind of pointless -->
    <!-- default menu file (or custom one in $HOME/.config/openbox/) -->
    <file>/usr/share/lubuntu/openbox/menu.xml</file>
    <file>menu.xml</file>

    <hideDelay>200</hideDelay>
    <!-- if a press-release lasts longer than this setting (in milliseconds), the
       menu is hidden again -->
    <middle>no</middle>
    <!-- center submenus vertically about the parent entry -->
    <submenuShowDelay>100</submenuShowDelay>
    <!-- time to delay before showing a submenu after hovering over the parent
       entry.
       if this is a negative value, then the delay is infinite and the
       submenu will not be shown until it is clicked on -->
    <submenuHideDelay>400</submenuHideDelay>
    <!-- time to delay before hiding a submenu when selecting another
       entry in parent menu
       if this is a negative value, then the delay is infinite and the
       submenu will not be hidden until a different submenu is opened -->
    <applicationIcons>yes</applicationIcons>
    <!-- controls if icons appear in the client-list-(combined-)menu -->
    <manageDesktops>yes</manageDesktops>
    <!-- show the manage desktops section in the client-list-(combined-)menu -->
    <showIcons>yes</showIcons>
    <!-- show icons on the menu -->
  </menu>
  <applications>
    <!--
  # this is an example with comments through out. use these to make your
  # own rules, but without the comments of course.
  # you may use one or more of the name/class/role/title/type rules to specify
  # windows to match

  <application name="the window's _OB_APP_NAME property (see obxprop)"
              class="the window's _OB_APP_CLASS property (see obxprop)"
               role="the window's _OB_APP_ROLE property (see obxprop)"
              title="the window's _OB_APP_TITLE property (see obxprop)"
               type="the window's _OB_APP_TYPE property (see obxprob)..
                      (if unspecified, then it is 'dialog' for child windows)">
  # you may set only one of name/class/role/title/type, or you may use more
  # than one together to restrict your matches.

  # the name, class, role, and title use simple wildcard matching such as those
  # used by a shell. you can use * to match any characters and ? to match
  # any single character.

  # the type is one of: normal, dialog, splash, utility, menu, toolbar, dock,
  #    or desktop

  # when multiple rules match a window, they will all be applied, in the
  # order that they appear in this list


    # each rule element can be left out or set to 'default' to specify to not 
    # change that attribute of the window

    <decor>yes</decor>
    # enable or disable window decorations

    <shade>no</shade>
    # make the window shaded when it appears, or not

    <position force="no">
      # the position is only used if both an x and y coordinate are provided
      # (and not set to 'default')
      # when force is "yes", then the window will be placed here even if it
      # says you want it placed elsewhere.  this is to override buggy
      # applications who refuse to behave
      <x>center</x>
      # a number like 50, or 'center' to center on screen. use a negative number
      # to start from the right (or bottom for <y>), ie -50 is 50 pixels from the
      # right edge (or bottom).
      <y>200</y>
      <monitor>1</monitor>
      # specifies the monitor in a xinerama setup.
      # 1 is the first head, or 'mouse' for wherever the mouse is
    </position>

    <focus>yes</focus>
    # if the window should try be given focus when it appears. if this is set
    # to yes it doesn't guarantee the window will be given focus. some
    # restrictions may apply, but Openbox will try to

    <desktop>1</desktop>
    # 1 is the first desktop, 'all' for all desktops

    <layer>normal</layer>
    # 'above', 'normal', or 'below'

    <iconic>no</iconic>
    # make the window iconified when it appears, or not

    <skip_pager>no</skip_pager>
    # asks to not be shown in pagers

    <skip_taskbar>no</skip_taskbar>
    # asks to not be shown in taskbars. window cycling actions will also
    # skip past such windows

    <fullscreen>yes</fullscreen>
    # make the window in fullscreen mode when it appears

    <maximized>true</maximized>
    # 'Horizontal', 'Vertical' or boolean (yes/no)
  </application>

  # end of the example
-->
    <!-- Option to maximize all normal window when launched-->
    <!--
    <application type="normal">
      <maximized>true</maximized>
    </application>
    -->

  </applications>
</openbox_config>
```

---

### Post by Toz on 2013-12-17
If you don't mind, when you post code or contents of files, can you paste it inbetween **[noparse]```
 
```[/noparse]** tags? It makes it easier to read.

Add the snippet right after:
>     <chainQuitKey>C-g</chainQuitKey>
...in the **<keyboard>** section.

I'm not sure about openbox config changes, but it might be a good idea to log out and back again afterwards for the config file to be re-read.

---

### Post by Citta on 2013-12-19
This snippet inserted, saved, the Fn keys still do not obey. Is there a way to have the same brightness after a reboot, having it decreased before-after reboot the brightness is always at max..and I have to decrease it via terminal again.

"If you don't mind, when you post code or contents of files, can you paste it inbetween  tags? It makes it easier to read." What do you mean and how to do this?

Thanks a lot!

PS: In the Email I did find this: 
Here is the message that has just been posted:
***************
If you don't mind, when you post code or contents of files, can you paste it inbetween ** tags? It makes it easier to read.

Add the snippet right after:

---Quote---
    <!-- Keybindings for desktop switching -->
---End Quote---
..in the *<keyboard>* section.


[FONT=arial]That is something different, when clicking the link in the mail I am directed to post #61...enigmatic. 
In "Getting Started with Ubuntu" on p.120, Asusnetbook, they have problems with Fn-key, perhaps a solution??[/FONT]

---

### Post by Toz on 2013-12-19
Can you post back the complete contents of your ~/.config/openbox/lubuntu-rc.xml file?

And can you also run this command one more time:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
... press FN+F5 & FN+F6 and post back if any codes appear in the terminal window. 

> Is there a way to have the same brightness after a reboot,
Yes. Add to the file **/etc/rc.local**, above the *exit 0* command, the following command:
```
echo 13000 > /sys/class/backlight/intel_backlight/brightness
```
...(change 13000 to any number you want between 0 (completely dark) and 26015 (brightness on full).
*Note, to edit the /etc/rc.local file, you'll need to:
```
sudo -i leafpad /etc/rc.local
```

---

### Post by Citta on 2013-12-21
[FONT=SimSun]In spite of my intention not to use Lubuntu before having solved that problem, I started it, plugged in an external HDD, with video/audiofiles. Started VLC-player, that worked for a while..
..stopped. Impossible to start VLC again. Audace, or so, that worked, the other player, also shipped with Lubuntu, worked, too. Windows popped up...Sorry,Ubuntu 13.10 experienced an [/FONT][FONT=SimSun]internal error..System error..! Now the desktop is very different, clicking icons resulted in "Authentication" then nothing else. Seems to be broken, the OS. [/FONT]
After a reboot Memory-Test was started, a red area outputted-perhaps a RAM-problem? I cannot interprete this result. 
What diagnostical steps could be taken? Win does not start, too, despite starting all recovery tools, but certain tools do not start at all, so chances of repair are dim.

---

### Post by Citta on 2013-12-22
Started the netbook to test the RAM again, before a tear-down and purchasing a RAM, this time Memtest did not complain. Win did not start, Lubuntu is working again! DE is very different from the original one, reason I do not know.

Ouput:

jane@jane:~$ ~/.config/openbox/lubuntu-rc.xml 
bash: /home/jane/.config/openbox/lubuntu-rc.xml: Permission denied
jane@jane:~$ xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
36 Return

rc-local file:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
  echo 13000 > /sys/class/backlight/intel_backlight/brightness
exit 0

The brightness did not decrease, perhaps after reboot........

---

