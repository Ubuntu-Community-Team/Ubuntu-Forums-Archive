---
title: "Script: Compile &amp; Install 2.6.14.3 Customized Vanilla Kernel"
date: 2005-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by ^NoX on 2005-12-04
The script has been updated and it is currently compiles the 2.6.14.4 vanilla kernel.
1. Download @ [http://ilunix.org/scripts/CompileKernel26144.sh](http://ilunix.org/scripts/CompileKernel26144.sh)
2. chmod +x CompileKernel26144.sh
3. ./CompileKernel26144.sh
4. Read all the warnings and instructions, if it asks you for your password - you know what to do.
5. Do as said before the xconfig window comes up.

[B]
Note: The script will replace your sources.list file![/B]

The script is well documented, you can read it to see what exactly happens.

Don't worry - If your new kernel doesn't work, you can just use your old kernel by choosing it in the GRUB menu.

After running it:
ofer@nettux:~/old/security$ uname -a
Linux nettux 2.6.14.4 #1 Thu Dec 22 02:20:41 IST 2005 i686 GNU/Linux
ofer@nettux:~/old/security$

**If it doesn't works, please upload your logfile, can be found @ /home/username/kcompilation26144.log, and specify the exact error you get on your main screen.**

---

### Post by ^NoX on 2005-12-22
Version updated. Currently contains 2.6.14.4 not 2.6.14.3 kernel.
Will continue to update every time there's a new stable kernel out there.

---

### Post by veloct on 2005-12-22
Does the new kernel break 3d acceleration for ATI cards?  (May be too broad of a question but I figured I ask anyway).  Does it install the kernel headers?

---

### Post by ^NoX on 2005-12-22
[QUOTE=veloct]Does the new kernel break 3d acceleration for ATI cards?  (May be too broad of a question but I figured I ask anyway).  Does it install the kernel headers?[/QUOTE]

1. About your question with ATi -> That's a very good question. I'll have an answer within an hour.
2. No, it doesn't installs the linux-kernel-headers package, since there is no need for it.

---

### Post by tseliot on 2005-12-22
1) Nice script, I haven't tried it myself yet but I think you might add the function to make kernel headers (which might be useful).
You can do it (maybe you already know that) in this way:
```
sudo -H make-kpkg -initrd --revision=customkern0 kernel_image [COLOR="Red"]kernel_headers[/COLOR]
```

2) Does the new pmount solve the mounting issues of kernel 2.6.14 some users have been complaining about?

---

### Post by ^NoX on 2005-12-22
[QUOTE=tseliot]1) Nice script, I haven't tried it myself yet but I think you might add the function to make kernel headers (which might be useful).
You can do it (maybe you already know that) in this way:
```
sudo -H make-kpkg -initrd --revision=customkern0 kernel_image [COLOR="Red"]kernel_headers[/COLOR]
```

2) Does the new pmount solve the mounting issues of kernel 2.6.14 some users have been complaining about?[/QUOTE]

First of all, thanks for your reply.
1. Yeah, I just might do it. Do I have to include the linux-kernel-headers package to make it work?
2. Yes, it is.

---

### Post by tseliot on 2005-12-22
[QUOTE=^NoX]First of all, thanks for your reply.
1. Yeah, I just might do it. Do I have to include the linux-kernel-headers package to make it work?[/QUOTE]
I guess not. It is not included in my guide but kernel headers compile fine.

---

### Post by veloct on 2005-12-22
let me know on the ATI question, also do I have to do anything if I want to compile it for 686-SMP?  I have a Pentium 4 w/ HT chip. Thanks.

---

### Post by ^NoX on 2005-12-22
[QUOTE=veloct]let me know on the ATI question, also do I have to do anything if I want to compile it for 686-SMP?  I have a Pentium 4 w/ HT chip. Thanks.[/QUOTE]

1. Okay.. There is a solution: you just have to reinstall the regular ATi driver from APT repos.
2. No. The scripts works for all archs. You just have to choose your correct CPU type. Just read the warnings and instructions and you will be just fine.

---

### Post by veloct on 2005-12-22
[QUOTE=^NoX]1. Okay.. There is a solution: you just have to reinstall the regular ATi driver from APT repos.
[/QUOTE]

So you lose 3D acceleration then? I wonder if "dpkg-reconfigure xorg-xserver" and choosing 'fglrx' as the driver would work.

If you startup with the 2.6.12 kernel (i have 2.6.12.10 now), will 3d acceleration work or no?

:)

---

### Post by tseliot on 2005-12-22
[QUOTE=^NoX]1. Okay.. There is a solution: you just have to reinstall the regular ATi driver from APT repos.
2. No. The scripts works for all archs. You just have to choose your correct CPU type. Just read the warnings and instructions and you will be just fine.[/QUOTE]
You can install ATI drivers from the repos only if the restricted modules for your kernel are available. In other words if you compile a new kernel you will have to compile the Ati modules for it.

---

### Post by Royle on 2005-12-22
[QUOTE=tseliot]You can install ATI drivers from the repos only if the restricted modules for your kernel are available. In other words if you compile a new kernel you will have to compile the Ati modules for it.[/QUOTE]

How would I do that?

---

### Post by ^NoX on 2005-12-23
[QUOTE=tseliot]You can install ATI drivers from the repos only if the restricted modules for your kernel are available. In other words if you compile a new kernel you will have to compile the Ati modules for it.[/QUOTE]

Okay thank you for the information.
The ATi modules are included in the kernel, so all I got to do it compile them through there, or I got to download it and patch the kernel before compiling?

---

### Post by celluloid on 2005-12-23
Hey,
How can I remove this kernel?
I tried removing the entry from grub/menu.1st but it still loads this kernel, which does not work for me.

---

### Post by ^NoX on 2005-12-23
[QUOTE=celluloid]Hey,
How can I remove this kernel?
I tried removing the entry from grub/menu.1st but it still loads this kernel, which does not work for me.[/QUOTE]

Easy one :)
sudo apt-get remove kernel-image-2.6.14.4

What didn't work? Can you please help detecting the problem so I can fix it?

---

### Post by celluloid on 2005-12-23
My wifi did not work at all, Other than that things were nice.
If you can find a way to have wifi working I'll use it ;)

Thanks heaps.

---

### Post by ^NoX on 2005-12-23
[QUOTE=celluloid]My wifi did not work at all, Other than that things were nice.
If you can find a way to have wifi working I'll use it ;)

Thanks heaps.[/QUOTE]

Hmm.. Load the WiFi module and it should work fine.
When running the old kernel, execute:
lsmod > oldkern.log
sudo lspci >> oldkern.log
Then run the new kernel, and execute:
lsmod > newkern.log
sudo lspci >> newkern.log
If you can upload those 2 files (oldkern.log and newkern.log), I will tell you how to fix it.

---

### Post by celluloid on 2005-12-23
After running the script, where do these logs go?

---

### Post by celluloid on 2005-12-23
oldkern.log

Module                  Size  Used by
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
ipv6                  217408  6 
af_packet              20232  2 
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
tsdev                   7616  0 
usbhid                 30688  0 
acx_pci               122752  0 
firmware_class          9472  1 acx_pci
snd_seq_dummy           3844  0 
snd_seq_oss            29440  0 
snd_seq_midi            8608  0 
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  2 
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  2 snd
i2c_viapro              7696  0 
via686a                17816  0 
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
pci_hotplug            24628  0 
via_agp                 9472  1 
agpgart                32328  1 via_agp
dm_mod                 50364  1 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
uhci_hcd               28048  0 
usbcore               104316  3 usbhid,uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  4 
ide_generic             1664  0 
via82cxxx              12188  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  610 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev 0b)

---

### Post by celluloid on 2005-12-23
newkern.log

Module                  Size  Used by
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
ipv6                  217408  6 
af_packet              20232  2 
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
tsdev                   7616  0 
usbhid                 30688  0 
acx_pci               122752  0 
firmware_class          9472  1 acx_pci
snd_seq_dummy           3844  0 
snd_seq_oss            29440  0 
snd_seq_midi            8608  0 
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  2 
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  2 snd
i2c_viapro              7696  0 
via686a                17816  0 
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
pci_hotplug            24628  0 
via_agp                 9472  1 
agpgart                32328  1 via_agp
dm_mod                 50364  1 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
uhci_hcd               28048  0 
usbcore               104316  3 usbhid,uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  4 
ide_generic             1664  0 
via82cxxx              12188  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  610 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev 0b)

---

### Post by sabitha on 2005-12-23
i can use my webcam after do this. plzz help me out .....
before i upgrade the kernel using this script i use spca5xx driver
but when i want to reinstall the driver it needs kernel header
this the erorr :
> client@client-12:~$ sudo apt-get install build-essential linux-headers-`uname -r` libpt-plugins-v4l
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
E: Couldn't find package linux-headers-2.6.14.4

how do i get kernel header to make it run again ....

---

### Post by Royle on 2005-12-23
I don't think anyone has answered this, how do I compile in the ATI fglrx driver module, after running this script?

---

### Post by ^NoX on 2005-12-23
[QUOTE=celluloid]After running the script, where do these logs go?[/QUOTE]

There is one log (STDOUT) @ /home/user/kcompilation26144.log
And the other log, you should copy from your screen if you see any errors.

---

### Post by veloct on 2005-12-23
[QUOTE=Royle]I don't think anyone has answered this, how do I compile in the ATI fglrx driver module, after running this script?[/QUOTE]

Yeah, if someone tells me how to compile that in I'll be willing to give it a shot :)

---

### Post by tseliot on 2005-12-23
[QUOTE=Royle]I don't think anyone has answered this, how do I compile in the ATI fglrx driver module, after running this script?[/QUOTE]
Follow these steps AFTER you have used the script:
Open Terminal or Konsole and type:

```
sudo apt-get install fglrx-kernel-source
cd /usr/src
sudo tar -xvf fglrx-kernel-source.tar.gz
cd linux
sudo make-kpkg -initrd --revision=customkern0 modules_image
```

A new .deb package will be created
```
cd /usr/src
ls
```
A list of files will show up. Look for a file (.deb) which contains the word "fglrx" in its name
```
sudo dpkg -i name_of_that_file.deb
```

And your modules will be installed.

Then Set the "fglrx" driver in your /etc/X11/xorg.conf.

I think I will add this to my guide about kernel compilation

---

### Post by Royle on 2005-12-23
I just tried following what tseliot said, but I get this error:
```
mike@ubuntu:/usr/src/linux$ sudo make-kpkg -initrd --revision=customkern0 module s_image
Please ignore the warning about overriding and ignoring targets above.
These are harmless. They are only invoked in a part of the process
that tries to snarf variable values for the conf.vars file.
echo done >  stamp-configure
for module in /usr/src/modules/fglrx-kernel ; do                       \
          if test -d  $module; then                                \
    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.14.4" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL=" unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"         \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="customkern0" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
  fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
./debian/rules:77: *** missing separator (did you mean TAB instead of 8 spaces?) .  Stop.
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue
```

Does anyone know whats wrong? Thanks a lot for your support.

---

### Post by tseliot on 2005-12-23
> **Royle]I just tried following what tseliot said, but I get this error:
```
mike@ubuntu:/usr/src/linux$ sudo make-kpkg -initrd --revision=customkern0 module s_image
Please ignore the warning about overriding and ignoring targets above.
These are harmless. They are only invoked in a part of the process
that tries to snarf variable values for the conf.vars file.
echo done >  stamp-configure
for module in /usr/src/modules/fglrx-kernel  said:**
> ; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
  fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
./debian/rules:77: *** missing separator (did you mean TAB instead of 8 spaces?) .  Stop.
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue
```

Does anyone know whats wrong? Thanks a lot for your support.
You made a typo. You wrote:
```
sudo make-kpkg -initrd --revision=customkern0 [COLOR="Red"]module s_image[/COLOR]
```

instead of:
```
sudo make-kpkg -initrd --revision=customkern0 [COLOR="Red"]modules_image[/COLOR]
```

---

### Post by Royle on 2005-12-23
I don't think I made a typo, I think the post just got messed up, I just tried it 3 times, checking to make sure it was right and I still get this error: ```
mike@ubuntu:/usr/src/linux$ sudo make-kpkg -initrd --revision=customkern0 modules_image
for module in /usr/src/modules/fglrx-kernel ; do                       \
          if test -d  $module; then                                \
    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.14.4" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="customkern0" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
  fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
./debian/rules:77: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue
```

Anyone have an idea?

---

### Post by ^NoX on 2005-12-23
[QUOTE=celluloid]newkern.log

Module                  Size  Used by
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
ipv6                  217408  6 
af_packet              20232  2 
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
tsdev                   7616  0 
usbhid                 30688  0 
acx_pci               122752  0 
firmware_class          9472  1 acx_pci
snd_seq_dummy           3844  0 
snd_seq_oss            29440  0 
snd_seq_midi            8608  0 
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  2 
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  2 snd
i2c_viapro              7696  0 
via686a                17816  0 
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
pci_hotplug            24628  0 
via_agp                 9472  1 
agpgart                32328  1 via_agp
dm_mod                 50364  1 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
uhci_hcd               28048  0 
usbcore               104316  3 usbhid,uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  4 
ide_generic             1664  0 
via82cxxx              12188  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  610 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev 0b)[/QUOTE]


That is so weird. I used diff to find differences between the files, and I found nothing. You have the same modules, and the kernel discovered the same hardware.
You have any type of an error when trying to use the WiFi card?

---

### Post by ^NoX on 2005-12-23
[QUOTE=tseliot]Follow these steps AFTER you have used the script:
Open Terminal or Konsole and type:

```
sudo apt-get install fglrx-kernel-source
cd /usr/src
sudo tar -xvf fglrx-kernel-source.tar.gz
cd linux
sudo make-kpkg -initrd --revision=customkern0 modules_image
```

A new .deb package will be created
```
cd /usr/src
ls
```
A list of files will show up. Look for a file (.deb) which contains the word "fglrx" in its name
```
sudo dpkg -i name_of_that_file.deb
```

And your modules will be installed.

Then Set the "fglrx" driver in your /etc/X11/xorg.conf.

I think I will add this to my guide about kernel compilation[/QUOTE]

Thank you very much! If you agree, I will add it to the script in the next version.

---

### Post by tseliot on 2005-12-23
[QUOTE=^NoX]Thank you very much! If you agree, I will add it to the script in the next version.[/QUOTE]
Yes, sure. I was working on my own script a few days ago but I won't continue writing it until I can get my hands on a book I bought on Amazon.co.uk which hasn't arrived yet.

---

### Post by Royle on 2005-12-23
Ok looking at the error I was getting, it seemed there was something wrong with line 77 in /usr/src/modules/fglrx-driver/debian/rules.  I looked at the line and instead of a tab, it had 8 spaces, unline all the other lines.  So I deleted the spaces and replaced it with a tab.  This is what I get now: ```
mike@ubuntu:/usr/src/linux$ sudo make-kpkg -initrd --revision=customkern0 modules_image
for module in /usr/src/modules/fglrx-kernel ; do                       \
          if test -d  $module; then                                \
    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.14.4" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="customkern0" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
  fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
echo "ROOT_CMD = "
ROOT_CMD =
/usr/bin/make -w -f debian/rules binary_modules
make[2]: Entering directory `/usr/src/modules/fglrx-kernel'
make[2]: *** No rule to make target `config.Makefile', needed by `configure-stamp'.  Stop.
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue
```

Does anyone know what I should do?

---

### Post by tseliot on 2005-12-23
You can follow my guide about Kernel compilation [HOWTO: Kernel Compilation for Newbies]("http://www.ubuntuforums.org/showthread.php?t=85064") and recompile the kernel with ati modules(I explain also how to compile additional modules: do for fglrx the same as I suggest for nvidia modules)

---

### Post by celluloid on 2005-12-23
[QUOTE=^NoX]That is so weird. I used diff to find differences between the files, and I found nothing. You have the same modules, and the kernel discovered the same hardware.
You have any type of an error when trying to use the WiFi card?[/QUOTE]


No, It simply just won't kick up and let me connect, first sign I got of this was failure at the bootscreen to synchronise to ubuntu, then no net at all inside gnome.

---

### Post by limit223 on 2005-12-24
Regarding fglrx modules for ATI driver:
Usually when I compile a new version of kernel I make new fglrx modules from  ati-driver-installer. So, actually a combine 2 how-to in installation: one of the kernel ( and here don't forget to link new kernel in /usr/src/linux) and the second of the ati driver installation. 

Notes:
-my kernel is very simplified on grafical, network, and sound cards, it contains mostly modules that my cards belongs to. In the case of ATI card I choose (fired the command in /usr/src/linux sudo make xconfig) ATI Radeon display support with DDC/I2C and Lots of debug output form Radeon
- after installing  fglrx modules (fglrx-control, fglrx-kernel-source, xorg-driver-fglrx) and compile kernel driver, especially right **before **command-line:

sudo module-assistant a-i fglrx

make sure you remove the old fglrx -kernel*.deb from /usr/src. I remember several failure in installation because of that.

I have no problem with my ATI 3d acceleration after kernel compilation.

---

### Post by celluloid on 2005-12-26
Any ideas ^Nox?

---

### Post by ^NoX on 2005-12-26
[QUOTE=celluloid]Any ideas ^Nox?[/QUOTE]

Nope... I don't see a reason for why it wouldn't work. Sorry :(

---

### Post by ^NoX on 2005-12-26
[QUOTE=limit223]Regarding fglrx modules for ATI driver:
Usually when I compile a new version of kernel I make new fglrx modules from  ati-driver-installer. So, actually a combine 2 how-to in installation: one of the kernel ( and here don't forget to link new kernel in /usr/src/linux) and the second of the ati driver installation. 

Notes:
-my kernel is very simplified on grafical, network, and sound cards, it contains mostly modules that my cards belongs to. In the case of ATI card I choose (fired the command in /usr/src/linux sudo make xconfig) ATI Radeon display support with DDC/I2C and Lots of debug output form Radeon
- after installing  fglrx modules (fglrx-control, fglrx-kernel-source, xorg-driver-fglrx) and compile kernel driver, especially right **before **command-line:

sudo module-assistant a-i fglrx

make sure you remove the old fglrx -kernel*.deb from /usr/src. I remember several failure in installation because of that.

I have no problem with my ATI 3d acceleration after kernel compilation.[/QUOTE]

Can you please explain this subject, maybe with additional details? I can write a script for that too.

---

### Post by limit223 on 2005-12-26
^Nox,

there are already 2 how-to in this section:
1. how to compile a kernel
2. how to ATI fglrx driver 8.xx.xx
very well explained...I didn't do nothing special than my notes above.
Picking the right modules that match everyone's hardware I don't thing it can be customize in a script.
My Grafics Support section (including ATI modules) in the .config file contains just these modules(I've got an Radeon Saffire PCI 128 card):
#
# Graphics support
#
CONFIG_FB=y
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
# CONFIG_FB_MACMODES is not set
CONFIG_FB_MODE_HELPERS=y
# CONFIG_FB_TILEBLITTING is not set
# CONFIG_FB_CIRRUS is not set
CONFIG_FB_PM2=m
CONFIG_FB_PM2_FIFO_DISCONNECT=y
# CONFIG_FB_CYBER2000 is not set
# CONFIG_FB_ARC is not set
# CONFIG_FB_ASILIANT is not set
# CONFIG_FB_IMSTT is not set
CONFIG_FB_VGA16=m
CONFIG_FB_VESA=y
CONFIG_VIDEO_SELECT=y
# CONFIG_FB_HGA is not set
# CONFIG_FB_S1D13XXX is not set
# CONFIG_FB_NVIDIA is not set
# CONFIG_FB_RIVA is not set
CONFIG_FB_I810=m
# CONFIG_FB_I810_GTF is not set
CONFIG_FB_INTEL=m
# CONFIG_FB_INTEL_DEBUG is not set
# CONFIG_FB_MATROX is not set
CONFIG_FB_RADEON_OLD=m
CONFIG_FB_RADEON=m
CONFIG_FB_RADEON_I2C=y
CONFIG_FB_RADEON_DEBUG=y
CONFIG_FB_ATY128=m
CONFIG_FB_ATY=m
CONFIG_FB_ATY_CT=y
CONFIG_FB_ATY_GENERIC_LCD=y
CONFIG_FB_ATY_XL_INIT=y
CONFIG_FB_ATY_GX=y
# CONFIG_FB_SAVAGE is not set
# CONFIG_FB_SIS is not set
# CONFIG_FB_NEOMAGIC is not set
# CONFIG_FB_KYRO is not set
# CONFIG_FB_3DFX is not set
# CONFIG_FB_VOODOO1 is not set
# CONFIG_FB_CYBLA is not set
# CONFIG_FB_TRIDENT is not set
# CONFIG_FB_PM3 is not set
# CONFIG_FB_GEODE is not set
CONFIG_FB_VIRTUAL=m

. The other note that I mentioned was to remove old fglrx -kernel*.deb from /usr/src it can be write in your script and it goes righ between this commands in the guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
```

.....................................
sudo module-assistant prepare
sudo module-assistant update
**sudo rm /usr/src/fglrx-kernel*.deb**
sudo module-assistant a-i fglrx
..........................................
```
Nothing special...compile a kernel and than install the ati driver once again following the steps in the guide.


Would be a very nice work from you if you can do this in a script, will shortcut a lot of work from us and help most of people with hard time installing the driver! Be aware, though by the new versions of ATI driver in the new versions of kernels...I experienced once and I had to do some dirty hacks to make it work for not long time version of kernel ago (more hack's info here: [http://www.rage3d.com/board/forumdisplay.php?f=88](http://www.rage3d.com/board/forumdisplay.php?f=88) ).

BTW..I made and installed fglrx-kernel-2.6.15-rc6-ck1-custom_8.20.8-1+10.00.Custom_i386.deb for my new compilation (kernel 2.6.15-rc6-ck1) with command
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image

but unfortunately 3d acceleration dri module failed to load after boot in the new kernel, although the fglrx module was fine...I must followed the other option to install 3D...the one described above.

---

### Post by limit223 on 2005-12-26
I guess I know another way (absolutely simple) to install the fglrx driver in a fresh compiled kernel which I used to make it in my "exlover"(SUSE box) and for sure would be helpfully for your script:

```
#check with your script if fglrx driver was installed in previous kernel version: if /lib/modules/fglrx directory exists if not echo "Please install ati Radeon driver"

cd /lib/modules/fglrx/build_mod

sudo ./make.sh

cd ..

sudo ./make_install.sh

#Reboot ...echo "If you configured xorg.conf previously with 3D acceleration you should see no errors of loading dri modules in /var/log/Xorg.0.log"
```


Have Fun!! :)

---

