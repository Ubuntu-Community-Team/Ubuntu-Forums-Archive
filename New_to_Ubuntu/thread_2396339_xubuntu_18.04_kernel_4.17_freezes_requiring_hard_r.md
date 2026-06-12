---
title: "xubuntu 18.04 kernel 4.17 freezes requiring hard reboot"
date: 2018-07-14
forum: New to Ubuntu
---

### Post by skydivingdrunk on 2018-07-14
Sorry to bother yall, I usually am able to just read enough threads on here and figure out things for myself, All I have done so far is update to the 4.17. 
I got that idea from this thread [https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly](https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly)
I'll post some stuff that I hope helps:
```
$ sudo swapon --show
NAME      TYPE      SIZE USED PRIO
/dev/sda7 partition 7.5G   0B   -2
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           3.7G        1.0G        2.0G         87M        688M        2.5G
Swap:          7.5G          0B        7.5G
The above brings me to believe I don't swap configured correctly.
$sudo lshw -short
H/W path       Device      Class       Description
==================================================
                           system      HP 15 Notebook PC (N5Y04UA#ABA)
/0                         bus         233F
/0/0                       memory      64KiB BIOS
/0/4                       processor   Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz
/0/4/6                     memory      32KiB L1 cache
/0/4/7                     memory      1MiB L2 cache
/0/5                       memory      24KiB L1 cache
/0/25                      memory      4GiB System Memory
/0/25/0                    memory      4GiB SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1333 MHz (0.8 ns)
/0/25/1                    memory      DDR Synchronous [empty]
/0/100                     bridge      Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
/0/100/2                   display     Atom Processor Z36xxx/Z37xxx Series Graphics & Display
/0/100/13                  storage     Atom Processor E3800 Series SATA AHCI Controller
/0/100/14                  bus         Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI
/0/100/14/0    usb1        bus         xHCI Host Controller
/0/100/14/0/1              bus         USB3.0 Hub
/0/100/14/0/4              multimedia  HP Webcam
/0/100/14/1    usb2        bus         xHCI Host Controller
/0/100/14/1/1              bus         USB3.0 Hub
/0/100/1a                  generic     Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
/0/100/1b                  multimedia  Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
/0/100/1c                  bridge      Atom Processor E3800 Series PCI Express Root Port 1
/0/100/1c/0                generic     RTS5229 PCI Express Card Reader
/0/100/1c.1                bridge      Atom Processor E3800 Series PCI Express Root Port 2
/0/100/1c.1/0  wlo1        network     RTL8188EE Wireless Network Adapter
/0/100/1c.2                bridge      Atom Processor E3800 Series PCI Express Root Port 3
/0/100/1c.2/0  enp3s0      network     RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
/0/100/1c.3                bridge      Atom Processor E3800 Series PCI Express Root Port 4
/0/100/1f                  bridge      Atom Processor Z36xxx/Z37xxx Series Power Control Unit
/0/100/1f.3                bus         Atom Processor E3800 Series SMBus Controller
/0/1           scsi0       storage     
/0/1/0.0.0     /dev/sda    disk        500GB WDC WD5000LPCX-6
/0/1/0.0.0/1   /dev/sda1   volume      259MiB Windows FAT volume
/0/1/0.0.0/2   /dev/sda2   volume      15MiB reserved partition
/0/1/0.0.0/3   /dev/sda3   volume      227GiB Windows NTFS volume
/0/1/0.0.0/4   /dev/sda4   volume      979MiB Windows NTFS volume
/0/1/0.0.0/5   /dev/sda5   volume      11GiB Windows NTFS volume
/0/1/0.0.0/6   /dev/sda6   volume      18GiB EXT4 volume
/0/1/0.0.0/7   /dev/sda7   volume      7628MiB Linux swap volume
/0/1/0.0.0/8   /dev/sda8   volume      199GiB EXT4 volume
/0/2           scsi1       storage     
/0/2/0.0.0     /dev/cdrom  disk        DVDRW GUD1N
/1                         power       LA03031DF
/2                         power       OEM_Define5
```

---

### Post by skydivingdrunk on 2018-07-15
I tried to attach an image, hopefully I did it right..
Anyways, It seems that the swap partition is working as its showing 524KB..
Any suggestions on what to look at or for?

---

### Post by NM5TF on 2018-07-17
your question is so vague that it is impossible to answer without much more information.....

can you post the output of

```
inxi -F
```

you may have to install inxi first......

we can proceed from there.....

---

### Post by skydivingdrunk on 2018-07-18
Thank you so much for helping me. This is driving me nuts. I'll be surfing the web, or watching a video, then the pc just freezes up. I'm sure it says something useful in one of the logs, just not sure which one to post on here. As requested:

```
$ inxi -F
System:    Host: PC Kernel: 4.17.0-041700-generic x86_64 bits: 64
           Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: HP product: HP 15 Notebook PC v: Type1 - ProductConfigId serial: N/A
           Mobo: Hewlett-Packard model: 233F v: 06.27 serial: N/A
           UEFI: Insyde v: F.35 date: 04/25/2017
Battery    BAT0: charge: 29.1 Wh 100.0% condition: 29.1/29.1 Wh (100%)
CPU:       Quad core Intel Pentium N3540 (-MCP-) cache: 1024 KB
           clock speeds: max: 2665 MHz 1: 1419 MHz 2: 620 MHz 3: 499 MHz
           4: 499 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel Bay Trail version: 4.2 Mesa 18.0.5
Audio:     Card Intel Atom Processor Z36xxx/Z37xxx Series High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.17.0-041700-generic
Network:   Card-1: Realtek RTL8188EE Wireless Network Adapter
           driver: rtl8188ee
           IF: wlo1 state: up mac: d4:6a:6a:0f:4d:6c
           Card-2: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169
           IF: enp3s0 state: down mac: 48:ba:4e:51:23:57
Drives:    HDD Total Size: 500.1GB (30.8% used)
           ID-1: /dev/sda model: WDC_WD5000LPCX size: 500.1GB
Partition: ID-1: / size: 19G used: 5.4G (32%) fs: ext4 dev: /dev/sda6
           ID-2: /home size: 196G used: 131G (71%) fs: ext4 dev: /dev/sda8
           ID-3: swap-1 size: 8.00GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda7
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 185 Uptime: 11 min Memory: 1060.6/3835.2MB
           Client: Shell (bash) inxi: 2.3.56
```

---

### Post by NM5TF on 2018-07-18
just to be clear....

everything was working before you upgraded to the 4.17 kernel ???

my research into the issues shows this command may resolve your problem....

```
systemctl reboot --firmware-setup
```

this seems to have worked for several others with similar hardware....

good luck

tommy

---

### Post by VMC on 2018-07-19
> **NM5TF said:**
> just to be clear....

everything was working before you upgraded to the 4.17 kernel ???

my research into the issues shows this command may resolve your problem....

```
systemctl reboot --firmware-setup
```

this seems to have worked for several others with similar hardware....

good luck

tommy
[COLOR=#000000][FONT=&quot]Regarding the 'systemctl'. Note that this is currently only supported on some EFI systems and only if the system was booted in EFI mode.
I can't figure out how he's booting. Most likely EFI.[/FONT][/COLOR]

---

### Post by VMC on 2018-07-19
> **skydivingdrunk said:**
> I tried to attach an image, hopefully I did it right..
Anyways, It seems that the swap partition is working as its showing 524KB..
Any suggestions on what to look at or for?
This 'top' shows your using some swap memory, but still have available ram? Don't understand. Also, it this 'top' picture straight from boot. If so, why is 'Parole' running.

Output this:
```
pstree root
```

---

### Post by skydivingdrunk on 2018-07-19
I was reading different things from here and there, and came across the top command, so I randomly ran it while listening to some music and browsing the web. I just restarted my laptop and waited a couple minutes then ran top again. attached it a screenshot.

---

### Post by skydivingdrunk on 2018-07-19
```
$ pstree root
systemd&#9472;&#9516;&#9472;ModemManager&#9472;&#9472;&#9472;2*[{ModemManager}]
        &#9500;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
        &#9474;                &#9492;&#9472;2*[{NetworkManager}]
        &#9500;&#9472;Thunar
        &#9500;&#9472;accounts-daemon&#9472;&#9472;&#9472;2*[{accounts-daemon}]
        &#9500;&#9472;acpid
        &#9500;&#9472;agetty
        &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
        &#9500;&#9472;bluetoothd
        &#9500;&#9472;cron
        &#9500;&#9472;cups-browsed&#9472;&#9472;&#9472;2*[{cups-browsed}]
        &#9500;&#9472;cupsd&#9472;&#9472;&#9472;dbus
        &#9500;&#9472;dbus-daemon
        &#9500;&#9472;exo-helper-1&#9472;&#9472;&#9472;xfce4-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
        &#9474;                               &#9492;&#9472;3*[{xfce4-terminal}]
        &#9500;&#9472;gimp-2.8&#9472;&#9516;&#9472;script-fu&#9472;&#9472;&#9472;2*[{script-fu}]
        &#9474;          &#9492;&#9472;6*[{gimp-2.8}]
        &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;3*[{gnome-keyring-d}]
        &#9500;&#9472;irqbalance&#9472;&#9472;&#9472;{irqbalance}
        &#9500;&#9472;2*[kerneloops]
        &#9500;&#9472;lightdm&#9472;&#9516;&#9472;Xorg&#9472;&#9472;&#9472;{Xorg}
        &#9474;         &#9500;&#9472;lightdm&#9472;&#9516;&#9472;sh&#9472;&#9516;&#9472;ssh-agent
        &#9474;         &#9474;         &#9474;    &#9492;&#9472;xfce4-session&#9472;&#9516;&#9472;applet.py&#9472;&#9472;&#9472;{applet.py}
        &#9474;         &#9474;         &#9474;                    &#9500;&#9472;blueman-applet&#9472;&#9472;&#9472;3*[{blueman+
        &#9474;         &#9474;         &#9474;                    &#9500;&#9472;light-locker&#9472;&#9472;&#9472;3*[{light-loc+
        &#9474;         &#9474;         &#9474;                    &#9500;&#9472;nm-applet&#9472;&#9472;&#9472;3*[{nm-applet}]
        &#9474;         &#9474;         &#9474;                    &#9500;&#9472;polkit-gnome-au&#9472;&#9472;&#9472;2*[{polkit+
        &#9474;         &#9474;         &#9474;                    &#9500;&#9472;update-notifier&#9472;&#9472;&#9472;3*[{update+
        &#9474;         &#9474;         &#9474;                    &#9492;&#9472;2*[{xfce4-session}]
        &#9474;         &#9474;         &#9492;&#9472;2*[{lightdm}]
        &#9474;         &#9492;&#9472;2*[{lightdm}]
        &#9500;&#9472;networkd-dispat&#9472;&#9472;&#9472;{networkd-dispat}
        &#9500;&#9472;polkitd&#9472;&#9472;&#9472;2*[{polkitd}]
        &#9500;&#9472;pulseaudio&#9472;&#9472;&#9472;2*[{pulseaudio}]
        &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
        &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
        &#9500;&#9472;snapd&#9472;&#9472;&#9472;13*[{snapd}]
        &#9500;&#9472;syndaemon
        &#9500;&#9472;systemd&#9472;&#9516;&#9472;(sd-pam)
        &#9474;         &#9500;&#9472;at-spi-bus-laun&#9472;&#9516;&#9472;dbus-daemon
        &#9474;         &#9474;                 &#9492;&#9472;3*[{at-spi-bus-laun}]
        &#9474;         &#9500;&#9472;at-spi2-registr&#9472;&#9472;&#9472;2*[{at-spi2-registr}]
        &#9474;         &#9500;&#9472;dbus-daemon
        &#9474;         &#9500;&#9472;dconf-service&#9472;&#9472;&#9472;2*[{dconf-*********]
        &#9474;         &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;3*[{gvfs-afc-volume}]
        &#9474;         &#9500;&#9472;gvfs-goa-volume&#9472;&#9472;&#9472;2*[{gvfs-goa-volume}]
        &#9474;         &#9500;&#9472;gvfs-gphoto2-vo&#9472;&#9472;&#9472;2*[{gvfs-gphoto2-vo}]
        &#9474;         &#9500;&#9472;gvfs-mtp-volume&#9472;&#9472;&#9472;2*[{gvfs-mtp-volume}]
        &#9474;         &#9500;&#9472;gvfs-udisks2-vo&#9472;&#9472;&#9472;2*[{gvfs-udisks2-vo}]
        &#9474;         &#9500;&#9472;gvfsd&#9472;&#9516;&#9472;gvfsd-dnssd&#9472;&#9472;&#9472;2*[{gvfsd-dnssd}]
        &#9474;         &#9474;       &#9500;&#9472;gvfsd-network&#9472;&#9472;&#9472;3*[{gvfsd-network}]
        &#9474;         &#9474;       &#9500;&#9472;gvfsd-trash&#9472;&#9472;&#9472;2*[{gvfsd-trash}]
        &#9474;         &#9474;       &#9492;&#9472;2*[{gvfsd}]
        &#9474;         &#9500;&#9472;gvfsd-fuse&#9472;&#9472;&#9472;5*[{gvfsd-fuse}]
        &#9474;         &#9500;&#9472;indicator-messa&#9472;&#9472;&#9472;3*[{indicator-messa}]
        &#9474;         &#9500;&#9472;obexd
        &#9474;         &#9500;&#9472;xfce4-notifyd&#9472;&#9472;&#9472;2*[{xfce4-notifyd}]
        &#9474;         &#9492;&#9472;xfconfd
        &#9500;&#9472;systemd-journal
        &#9500;&#9472;systemd-logind
        &#9500;&#9472;systemd-resolve
        &#9500;&#9472;systemd-timesyn&#9472;&#9472;&#9472;{systemd-timesyn}
        &#9500;&#9472;systemd-udevd
        &#9500;&#9472;thermald&#9472;&#9472;&#9472;{thermald}
        &#9500;&#9472;tor
        &#9500;&#9472;udisksd&#9472;&#9472;&#9472;4*[{udisksd}]
        &#9500;&#9472;upowerd&#9472;&#9472;&#9472;2*[{upowerd}]
        &#9500;&#9472;whoopsie&#9472;&#9472;&#9472;2*[{whoopsie}]
        &#9500;&#9472;wpa_supplicant
        &#9500;&#9472;xfce4-panel&#9472;&#9516;&#9472;chromium-browse&#9472;&#9516;&#9472;chromium-browse&#9472;&#9472;&#9472;chromium-browse&#9472;&#9516;&#9472;3+
        &#9474;             &#9474;                 &#9474;                                   &#9500;&#9472;2+
        &#9474;             &#9474;                 &#9474;                                   &#9500;&#9472;c+
        &#9474;             &#9474;                 &#9474;                                   &#9492;&#9472;c+
        &#9474;             &#9474;                 &#9500;&#9472;chromium-browse&#9472;&#9516;&#9472;chromium-browse
        &#9474;             &#9474;                 &#9474;                 &#9492;&#9472;7*[{chromium-browse+
        &#9474;             &#9474;                 &#9492;&#9472;33*[{chromium-browse}]
        &#9474;             &#9500;&#9472;panel-1-whisker&#9472;&#9472;&#9472;2*[{panel-1-whisker}]
        &#9474;             &#9500;&#9472;panel-13-places&#9472;&#9472;&#9472;2*[{panel-13-places}]
        &#9474;             &#9500;&#9472;panel-4-systray
        &#9474;             &#9500;&#9472;panel-5-notific&#9472;&#9472;&#9472;2*[{panel-5-notific}]
        &#9474;             &#9500;&#9472;panel-6-indicat&#9472;&#9472;&#9472;2*[{panel-6-indicat}]
        &#9474;             &#9500;&#9472;panel-7-statusn&#9472;&#9472;&#9472;2*[{panel-7-statusn}]
        &#9474;             &#9500;&#9472;panel-8-power-m&#9472;&#9472;&#9472;2*[{panel-8-power-m}]
        &#9474;             &#9500;&#9472;panel-9-pulseau&#9472;&#9472;&#9472;2*[{panel-9-pulseau}]
        &#9474;             &#9492;&#9472;2*[{xfce4-panel}]
        &#9500;&#9472;xfce4-power-man&#9472;&#9472;&#9472;2*[{xfce4-power-man}]
        &#9500;&#9472;xfdesktop&#9472;&#9472;&#9472;2*[{xfdesktop}]
        &#9500;&#9472;xfsettingsd&#9472;&#9472;&#9472;2*[{xfsettingsd}]
        &#9492;&#9472;xfwm4
```

---

### Post by skydivingdrunk on 2018-07-19
> **NM5TF said:**
> just to be clear....

everything was working before you upgraded to the 4.17 kernel ???

No, I just bought a new laptop, and installed Xubuntu 18.04 on it, while browsing the web the laptop would just freeze up, the only thing I could do was hold down the power button to reboot. So why searching around for a solution, I read the thread I linked in the OP and updated the kernel to the latest version. I'm now gonna try the "systemctl reboot --firmware-setup" which I believe is going to restart the pc, so I'm going to submit this reply before I do so. I think I'm booting in EFI mode, as its a new laptop, and I vaguely remember having to go into bios and disable fastboot or something when I installed xubuntu..

---

### Post by skydivingdrunk on 2018-07-19
> **NM5TF said:**
> just to be clear....

everything was working before you upgraded to the 4.17 kernel ???

my research into the issues shows this command may resolve your problem....

```
systemctl reboot --firmware-setup
```

this seems to have worked for several others with similar hardware....

good luck

tommy

I entered that command, then the pc rebooted, and brought up a menu, f1 to enter bios, f2 to something, f3 etc.. I pressed enter to continue, as I didn't know what to do here, and it booted into Windows. I shutdown, then upon reboot, grub was gone, it just goes straight to windows now. How do I get grub back? I'm sure I can just google this one, but I don't want to mess anything up..

---

### Post by skydivingdrunk on 2018-07-19
I think I found a way to restore grub, gonna try the instructions here: [https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/)
Will report back..

---

### Post by skydivingdrunk on 2018-07-19
So, I'm back to where I started lol. I restored Grub, and am now back to running Xubuntu. What was I supposed to do in the EFI menu?

---

### Post by skydivingdrunk on 2018-07-19
When I installed xubuntu alongside of W10, I disabled secure boot in UEFI first as instructed here: [https://www.howtogeek.com/175641/how-to-boot-and-install-linux-on-a-uefi-pc-with-secure-boot/](https://www.howtogeek.com/175641/how-to-boot-and-install-linux-on-a-uefi-pc-with-secure-boot/)

---

### Post by skydivingdrunk on 2018-07-19
Also worth mentioning, I disabled fast boot too, I think.. This is the guide I followed while installing xubuntu: [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

---

### Post by skydivingdrunk on 2018-07-22
Just rebooted from a crash. Here's the contents from dmesg

[https://paste.ubuntu.com/p/GqmSpNcm5G/](https://paste.ubuntu.com/p/GqmSpNcm5G/)

---

### Post by karthikeyan.d on 2018-10-05
Is your system freeze issue resolved? I faced the same issue with a fresh installation of Ubuntu 18.04.1. The experiments I did so far show that the problem happens only with iPhone USB tethering. The details of my experiments can be found in the following thread

[https://ubuntuforums.org/showthread.php?t=2399736](https://ubuntuforums.org/showthread.php?t=2399736)

Thanks

---

### Post by skydivingdrunk on 2018-10-14
Still freezing, I connect to the internet via wifi. I asked this question on askunbuntu too, still no luck.
[https://askubuntu.com/questions/1080742/xubuntu-18-04-freezes-constantly-requiring-a-hard-reboot/1081789](https://askubuntu.com/questions/1080742/xubuntu-18-04-freezes-constantly-requiring-a-hard-reboot/1081789)

---

