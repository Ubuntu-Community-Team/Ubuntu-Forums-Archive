---
title: "slow boot after install"
date: 2020-02-15
forum: New to Ubuntu
---

### Post by alirezas on 2020-02-15
Hello Everyone,

I just installed ubuntu 19,10 on my M.2 NVME hard-drive and it loads very slow.  After running 

systemd-analyze
Startup finished in 2.664s (kernel) + 1min 41.971s (userspace) = 1min 44.635s 
graphical.target reached after 1min 41.966s in userspace

it is taking almost 2 minutes to load.  How can I speed this up.  I am new to linux and have no idea how to fix this issues.

Thanks for the help

---

### Post by TheFu on 2020-02-15
$ systemd-analyze blame
That can show a bunch of startup dependencies that can safely be removed if you don't use them.  For example, bluetooth can be really slow and on a system that never will use any bluetooth, it is a waste.

Also, check the log files for hardware errors.  Failing hardware can work just well enough to require longer tests before failing. Lots of timeouts slow down boots.

As to timeouts, a slow DNS or bad wifi can make for a slow system too.

Then there are always the low RAM, slow CPU, or incorrectly configured swap that can make for terrible startup.

---

### Post by him610 on 2020-02-15
There may be another factor to consider if you have an intel CPU. There was a (protective) microcode update a year or so ago that delays the boot process for about a minute; so on my intel powered machine that used to take about 15-20 seconds to boot, now it takes 1min 43sec.
This issue does not seem to effect AMD APUs.
I usually turn my on then walk the dog or get a cup of coffee.

---

### Post by CatKiller on 2020-02-15
> **alirezas said:**
> 
graphical.target reached after 1min 41.966s in userspace

That looks to me like a service is timing out; the default time to wait for things to properly start (or properly stop) is 90 seconds.

As TheFu says, you can check logs and things to see if that's the case for you. You can see if you can fix whichever thing is stalling, or turn it off, or - as a last resort - just make the timeout period shorter.

---

### Post by oldfred on 2020-02-15
I made a variety of changes and this is my boot with 20.04 on a skylake Intel chip with NVMe drive.
       fred@fred-Z170N-focal:~$  systemd-analyze
Startup finished in 3.229s (kernel) + 8.818s (userspace) = 12.048s 
graphical.target reached after 5.627s in userspace 

I updated UEFI to latest available.
Updated SSD firmware with Samsung ISO.

 turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
# only want .deb software
removed snaps 

           Changed systemctl daily timer 
housecleaned systemctl logs 

 # no thunderbolt so removed
systemctl status bolt 
boltctl list
systemctl mask bolt.service 

    Went thru these threads to pick up any other issues.
      Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html) 
   [https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything) &  
   [https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do](https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do)
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

---

### Post by TheFu on 2020-02-16
Here's mine:
```
$ systemd-analyze 
Startup finished in 1min 5.731s (kernel) + 14.702s (userspace) = **1min 20.433s**
```
on an 8th gen Core i5. But that isn't the true story.

I can assure you that it doesn't take a 1:20 to start.  It is closer to 20 sec, if even that long. Let me explain.
[LIST=1]
[*]Push the power button, wait about 5 sec for the LUKS decryption challenge to appear. The HDD has to be unlocked for access. This is a pre-boot task.
[*]Insert the correct yubikey
[*]Type in the yubikey challenge passphrase twice
[*]Wait about 5 sec for the login screen to appear.
[*]Type in the login username/password. I don't do the 'pick list'
[*]Wait about 5 seconds for the WM to display.  I don't do any DE.
[/LIST]
Regardless of what systemd claims, the other services after the WM is up can take 5 minutes for all that I care.  
See ... 
```
$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

**graphical.target @14.692s**
&#9492;&#9472;multi-user.target @14.691s
  &#9492;&#9472;snapd.seeded.service @14.665s +25ms
    &#9492;&#9472;snapd.service @12.549s +2.114s
      &#9492;&#9472;basic.target @12.422s
        &#9492;&#9472;sockets.target @12.422s
          &#9492;&#9472;dnscrypt-proxy.socket @12.422s
            &#9492;&#9472;network.target @12.422s
              &#9492;&#9472;networking.service @5.984s +6.437s
                &#9492;&#9472;apparmor.service @5.901s +78ms
                  &#9492;&#9472;local-fs.target @5.896s
                    &#9492;&#9472;var-lib-lxd-devlxd.mount @13.574s
                      &#9492;&#9472;local-fs-pre.target @881ms
                        &#9492;&#9472;lvm2-monitor.service @206ms +675ms
                          &#9492;&#9472;lvm2-lvmetad.service @312ms
                            &#9492;&#9472;systemd-journald.socket @198ms
                              &#9492;&#9472;-.mount @182ms
                                &#9492;&#9472;system.slice @197ms
                                  &#9492;&#9472;-.slice @182ms

```
It is important to know what is being displayed by the commands used. 15sec seems fast enough for something that happens 1-2 times a week.

Heck, I even installed a snap package yesterday.

---

### Post by alirezas on 2020-02-16
I am getting and error hda audio timeout, but I don't know how to get the error and fix it.  It looks like the audio codec is not installed or working.

---

### Post by GhX6GZMB on 2020-02-16
As long as you don't tell us what your hardware is, it's difficult to help.

---

### Post by TheFu on 2020-02-16
> **ml9104 said:**
> As long as you don't tell us what your hardware is, it's difficult to help.

The quick way to provide that is with **inxi -Fz**  Post the output, using code tags, so the output columns line up in these forums. 
[https://ubuntuforums.org/showthread.php?t=2436648&p=13931357#post13931357](https://ubuntuforums.org/showthread.php?t=2436648&p=13931357#post13931357) is an example.

**Adv Reply** has (#) - for *code tags*. Go Advanced also works.  Whenever posting terminal stuff, using code tags really helps people see what's important.  We recognize patterns in the output and are familiar with the formats.  

Please use code tags.

---

### Post by alirezas on 2020-02-17
This is what I get running 

```
amin@olafic:~$ inxi -FzSystem:    Host: olafic Kernel: 5.3.0-29-generic x86_64 bits: 64 Desktop: Gnome 3.34.1 
           Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG MAXIMUS XI HERO (WI-FI) v: Rev 1.xx 
           serial: <filter> UEFI: American Megatrends v: 1401 date: 11/26/2019 
CPU:       Topology: 8-Core model: Intel Core i9-9900K bits: 64 type: MT MCP L2 cache: 16.0 MiB 
           Speed: 800 MHz min/max: 800/5000 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
           5: 800 6: 800 7: 801 8: 800 9: 800 10: 800 11: 800 12: 800 13: 800 14: 800 15: 800 
           16: 800 
Graphics:  Device-1: Intel UHD Graphics 630 driver: N/A 
           Device-2: NVIDIA TU102 [GeForce RTX 2080 Ti Rev. A] driver: N/A 
           Display: x11 server: X.Org 1.20.5 driver: fbdev,nouveau unloaded: modesetting,vesa 
           resolution: 3440x1440~89Hz 
           OpenGL: renderer: llvmpipe (LLVM 9.0 256 bits) v: 3.3 Mesa 19.2.8 
Audio:     Device-1: Intel Cannon Lake PCH cAVS driver: snd_hda_intel 
           Device-2: NVIDIA TU102 High Definition Audio driver: snd_hda_intel 
           Device-3: Logitech G933 Wireless Headset Dongle type: USB 
           driver: hid-generic,snd-usb-audio,usbhid 
           Sound Server: ALSA v: k5.3.0-29-generic 
Network:   Device-1: Intel Wireless-AC 9560 [Jefferson Peak] driver: iwlwifi 
           IF: wlo1 state: down mac: <filter> 
           Device-2: Intel Ethernet I219-V driver: e1000e 
           IF: eno2 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 1.36 TiB used: 13.80 GiB (1.0%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO Plus 500GB size: 465.76 GiB 
           ID-2: /dev/sda vendor: Samsung model: SSD 860 EVO 1TB size: 931.51 GiB 
Partition: ID-1: / size: 456.94 GiB used: 13.80 GiB (3.0%) fs: ext4 dev: /dev/nvme0n1p3 
Sensors:   System Temperatures: cpu: 33.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 0 
Info:      Processes: 397 Uptime: 7h 55m Memory: 15.48 GiB used: 1.97 GiB (12.7%) Shell: bash 
           inxi: 3.0.36
```

---

### Post by alirezas on 2020-02-17
I see I have issues with video card drivers, even though everything is updated and upgraded to the latest version.  No matter what the video cards are not working properly even thought it shows the driver is installed to latest.

---

### Post by TheFu on 2020-02-17
Please use *_code tags_*. Too hard to read.

---

### Post by alirezas on 2020-02-17
```
 amin@olafic:~$ inxi -FzSystem:    Host: olafic Kernel: 5.3.0-40-generic x86_64 bits: 64 Desktop: Gnome 3.34.1 
           Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG MAXIMUS XI HERO (WI-FI) v: Rev 1.xx 
           serial: <filter> UEFI: American Megatrends v: 1401 date: 11/26/2019 
CPU:       Topology: 8-Core model: Intel Core i9-9900K bits: 64 type: MT MCP L2 cache: 16.0 MiB 
           Speed: 800 MHz min/max: 800/5000 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
           5: 800 6: 800 7: 801 8: 800 9: 800 10: 800 11: 800 12: 800 13: 800 14: 800 15: 800 
           16: 800 
Graphics:  Device-1: Intel UHD Graphics 630 driver: N/A 
           Device-2: NVIDIA TU102 [GeForce RTX 2080 Ti Rev. A] driver: N/A 
           Display: x11 server: X.Org 1.20.5 driver: fbdev,nouveau unloaded: modesetting,vesa 
           resolution: 3440x1440~89Hz 
           OpenGL: renderer: llvmpipe (LLVM 9.0 256 bits) v: 3.3 Mesa 19.2.8 
Audio:     Device-1: Intel Cannon Lake PCH cAVS driver: snd_hda_intel 
           Device-2: NVIDIA TU102 High Definition Audio driver: snd_hda_intel 
           Device-3: Logitech G933 Wireless Headset Dongle type: USB 
           driver: hid-generic,snd-usb-audio,usbhid 
           Sound Server: ALSA v: k5.3.0-40-generic 
Network:   Device-1: Intel Wireless-AC 9560 [Jefferson Peak] driver: iwlwifi 
           IF: wlo1 state: down mac: <filter> 
           Device-2: Intel Ethernet I219-V driver: e1000e 
           IF: eno2 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 1.36 TiB used: 13.30 GiB (1.0%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO Plus 500GB size: 465.76 GiB 
           ID-2: /dev/sda vendor: Samsung model: SSD 860 EVO 1TB size: 931.51 GiB 
Partition: ID-1: / size: 456.94 GiB used: 13.29 GiB (2.9%) fs: ext4 dev: /dev/nvme0n1p3 
Sensors:   System Temperatures: cpu: 34.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 0 
Info:      Processes: 408 Uptime: 3m Memory: 15.48 GiB used: 1.57 GiB (10.2%) Shell: bash 
           inxi: 3.0.36 



```

---

### Post by CelticWarrior on 2020-02-17
> Device-2: NVIDIA TU102 [GeForce RTX 2080 Ti Rev. A] driver: **N/A**

^^^This is probably the main problem. So, install Nvidia drivers (via Additional Drivers) if not installed alreadyand disable Secure Boot.

---

### Post by TheFu on 2020-02-17
The CPU, RAM, SSDs and that GPU should make for a crazy fast box. Sometimes people will have the same complaint but running an N270 Atom CPU from 2010 with 2GB of RAM, slow HDD.  That isn't the issue here.

My first stop would be to see if there are any UEFI/BIOS updates available for the system.  My Asus MB has a way to do that directly from the BIOS without hunting for drivers or anything.

Next I'd look for the *  systemd-analyze critical-chain* output and disable all the stuff that isn't needed for boot.  Slow network startup for a desktop can be avoided by forcing a static IP and using a wired network connection.  That Intel NIC is excellent. Don't enable both wifi and wired network adaptors at the same time.

The GPU driver issue probably isn't related to startup, but who knows?  Definitely worth having the nvidia driver if you went to the effort to have that GPU.

```
Graphics:  Device-1: Intel UHD Graphics 630 driver: **N/A **
           Device-2: NVIDIA TU102 [GeForce RTX 2080 Ti Rev. A] driver: **N/A** 
           Display: x11 server: X.Org 1.20.5 driver: **fbdev**,nouveau unloaded: modesetting,vesa 
           resolution: 3440x1440~89Hz 
           OpenGL: renderer: **llvmpipe** (LLVM 9.0 256 bits) v: 3.3 Mesa 19.2.8
```
The system is using software for all GPU stuff. This isn't good.  I understand that having 2 GPUs makes for complications. I've never had to deal with that nor do I use non-LTS releases.  With an LTS release, getting the nvidia GPU driver should be easy.
[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)  This system might need the newer release.  IDK. Newer isn't usually better, IME.

To get more details on the GPU and drivers, typicial commands are:
```
sudo lshw -C video
lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
egrep -i driver /var/log/Xorg.0.log

```
Don't know if the order of the driver listed matters above: fbdev,nouveau
**llvmpipe** is known to be very slow.

To get the nvidia driver installed, 
```
sudo ubuntu-drivers autoinstall
``` 
If that doesn't work, more detailed instructions: [https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-19-10-eoan-ermine-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-19-10-eoan-ermine-linux)
GPU drivers are one of the few types where a reboot is needed.

---

### Post by alirezas on 2020-02-17
unfortunately the nvidia drivers are not installing.  I tried both graphical and from command line. for some reason it is not using nvidia.

---

### Post by alirezas on 2020-02-17
```
 amin@olafic:~$ sudo apt install nvidia-driver-440Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-driver-440 is already the newest version (440.59-0ubuntu0~0.19.10.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amin@olafic:~$ nvidia-settings


ERROR: NVIDIA driver is not loaded




ERROR: Unable to load info from any available system




(nvidia-settings:6960): GLib-GObject-CRITICAL **: 21:11:50.989: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 21:11:50.994: PRIME: No offloading required. Abort
** Message: 21:11:50.994: PRIME: is it supported? no



```

---

### Post by TheFu on 2020-02-17
> **TheFu said:**
> GPU drivers are one of the few types where a reboot is needed.

Did you reboot after the driver install?

I don't know how to force the nvidia GPU to be used rather than the iGPU from the Intel CPU. Sorry.

---

### Post by alirezas on 2020-02-18
I got it fixed and now loads in 2.3 seconds.  In bios I turned of fast boot and also the UEFI changed it from Windows OS to other OS.  Then I purged all the Nvidia drivers and reinstalled everything from shell.  The system updated to latest video driver and tested it a few times and now the load time 2.3 seconds.

Thanks for the help everyone

---

### Post by CelticWarrior on 2020-02-19
Changed from "Windows OS" to "Other OS" is what did it in the end. That setting merely disables Secure Boot, exactly what I suggested (and you ignored) some posts ago.

Keep in mind that Secure Boot prevents unsigned drivers from loading.

---

