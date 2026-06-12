---
title: "Display issue with Ubuntu Cinamon on Alienware m16"
date: 2024-01-27
forum: New to Ubuntu
---

### Post by brad-s144 on 2024-01-27
Hello,

I have a new Alienware m16 laptop I am dual-booting with Ubuntu Cinamon 22.04 and Windows 11. AMD Ryzen 7 7745HX processor, and NVIDIA GeForce RTX 4060 GPU.

I have an issue where the screen will start to flicker, then become pixilated. Shortly after this starts to happen, the system will freeze up and I have to shut down by holding the power button.

I am using the recommended video driver ("nvidea-driver-535 (proprietary, tested)") but I have tried several others that appear in updates, including Nouveau.

The issue seems to occur at random (as far as I can tell) and has not happened in Windows. I ran the Dell Diagnostics hardware scan without finding any issues.

I am completely new to Linux (beyond a bit of experience with a Raspberry Pi).

Thanks in advance for any help/guidance anyone can provide.

---

### Post by MAFoElffen on 2024-01-27
From what I have seen, this has been reported a lot in Linux (not just Ubuntu) for AMD Ryzen 7 7745HX CPU's...

Example:
[https://www.google.com/search?q=AMD+Ryzen+7+7745HX+CPU+linux+flickering+freezing&client=ubuntu-sn&hs=TCJ&sca_esv=2bfb49782b222571&channel=fs&sxsrf=ACQVn0_FoMxJ4-mJdXm1j1dKkqFbfnxkNQ%3A1706405938851&ei=MrC1ZcLRM8DO0PEP4q-D-Aw&ved=0ahUKEwjCss---f6DAxVAJzQIHeLXAM8Q4dUDCBA&uact=5&oq=AMD+Ryzen+7+7745HX+CPU+linux+flickering+freezing&gs_lp=Egxnd3Mtd2l6LXNlcnAiMEFNRCBSeXplbiA3IDc3NDVIWCBDUFUgbGludXggZmxpY2tlcmluZyBmcmVlemluZ0i7U1C-BVifSnABeAGQAQCYAXmgAeIRqgEEMjQuMrgBA8gBAPgBAcICChAAGEcY1gQYsAPCAgYQABgWGB7CAgUQIRigAcICBRAhGKsC4gMEGAAgQYgGAZAGCA&sclient=gws-wiz-serp](https://www.google.com/search?q=AMD+Ryzen+7+7745HX+CPU+linux+flickering+freezing&client=ubuntu-sn&hs=TCJ&sca_esv=2bfb49782b222571&channel=fs&sxsrf=ACQVn0_FoMxJ4-mJdXm1j1dKkqFbfnxkNQ%3A1706405938851&ei=MrC1ZcLRM8DO0PEP4q-D-Aw&ved=0ahUKEwjCss---f6DAxVAJzQIHeLXAM8Q4dUDCBA&uact=5&oq=AMD+Ryzen+7+7745HX+CPU+linux+flickering+freezing&gs_lp=Egxnd3Mtd2l6LXNlcnAiMEFNRCBSeXplbiA3IDc3NDVIWCBDUFUgbGludXggZmxpY2tlcmluZyBmcmVlemluZ0i7U1C-BVifSnABeAGQAQCYAXmgAeIRqgEEMjQuMrgBA8gBAPgBAcICChAAGEcY1gQYsAPCAgYQABgWGB7CAgUQIRigAcICBRAhGKsC4gMEGAAgQYgGAZAGCA&sclient=gws-wiz-serp)

A lot of those issues seemed to be resolved with this CPU and NVidia by installing the 6.5-0 OEM kernel Series.
RE: [https://ubuntuhandbook.org/index.php/2023/09/linux-kernel-6-5-is-ready-to-install-in-ubuntu-22-04-lts/](https://ubuntuhandbook.org/index.php/2023/09/linux-kernel-6-5-is-ready-to-install-in-ubuntu-22-04-lts/)

Try it and see if it helps.
```

sudo apt update
sudo apt install linux-oem-22.04d
sudo reboot

```
If not, then you can switch back by doing
```

sudo apt install --install-recommends linux-generic-hwe-22.04
sudo reboot

```
Easy enough to try and test to see if it helps, right?

---

### Post by brad-s144 on 2024-01-28
Thanks for the suggestion, I'll give that a shot.

---

### Post by brad-s144 on 2024-01-28
Unfortunately, that did not seem to solve the problem. Any other suggestions?

---

### Post by MAFoElffen on 2024-01-28
Can you post the error it is displaying? I just noticed the NVidia...

Plus the output of this:
```

uname -r
gcc --version
nvidia-smi

```

---

### Post by brad-s144 on 2024-01-29
There isn't really an error message - but here is a more detailed description:
1) The screen starts to flicker.
2)  Shortly thereafter, the application window will become pixilated and semi-transparent (the desktop is visible through it). This usually starts in a single window, if I switch to a different one it is usually (briefly) OK.
3) The same thing happens to other open windows.
4) The entire screen becomes pixilated, and progresses to either a black screen or a couple of large blocks of solid colours. At this time, the keyboard and mouse become unresponsive and I have to power down by holding the power button.

I haven't been able to spot a pattern, but it usually seems to be after a few hours of using the computer - as little as a few minutes after re-booting to as long as a day so far. Is there a log file that would show anything helpful?

The output you requested::
```

brad@brad-Alienware-m16-R1-AMD:~$ uname -r
6.5.0-15-generic

brad@brad-Alienware-m16-R1-AMD:~$ gcc --version
gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
Copyright (C) 2021 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

brad@brad-Alienware-m16-R1-AMD:~$ nvidia-smi
Sun Jan 28 22:42:07 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.154.05             Driver Version: 535.154.05   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 4060 ...    Off | 00000000:01:00.0 Off |                  N/A |
| N/A   37C    P0              N/A /  90W |      8MiB /  8188MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      1483      G   /usr/lib/xorg/Xorg                            4MiB |
+---------------------------------------------------------------------------------------+


```

---

### Post by MAFoElffen on 2024-01-29
Dang. Everything looks good with that.

I know, from being a certified Dell, Lenovo and HP Warranty Tech, that the Dell Alienware machines have Dell Diagnostics in the UEFI BIOS... What does the extended tests on that Display and Graphics Card say?

---

### Post by brad-s144 on 2024-01-29
I ran the extended test and it said there were no issues. I don't recall the exact message, would it be useful to re-run it and post the message here?

---

### Post by brad-s144 on 2024-01-29
Not sure if it is helpful, but I've attached a couple of screenshots of what the it looks like once it starts acting up.

---

### Post by ActionParsnip on 2024-01-30
Also make sure you have the latest BIOS. This may help

---

### Post by MAFoElffen on 2024-01-30
Hmmm.

Looking into this. I would file a Bug Report with NVidia on the driver.

First thin they are going to ask you. Is to ensure your BIOS image is up to date. On the AlienWare laptops, they makde this easy in the AlienWare Control Center (On the Windows side Dell AlienWare Maintenance Utilities)...

Next, before you file a Bug Report on it to them, do this and post the output within code tags:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list
grep .  /sys/module/nvidia/version
grep . /proc/driver/nvidia/version

```
From the list of drives it provides, try each of the drivers and see if any of them change the problem in any way. That will narrow down if it might be a driver issue with one version, all versions, or maybe something in the hardware. From what you said, that doesn't happen in Windows, so most likely not the hardare, but rather a driver issue.

On Drivers, even with the saem version, sometimes they have differnt versions of that driver:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ apt list nvidia-driver-535*
Listing... Done
nvidia-driver-535-open/jammy-updates,jammy-security 535.154.05-0ubuntu0.22.04.1 amd64
nvidia-driver-535-server-open/jammy-updates,jammy-security 535.154.05-0ubuntu0.22.04.1 amd64
nvidia-driver-535-server/jammy-updates,jammy-security 535.154.05-0ubuntu0.22.04.1 amd64
nvidia-driver-535/jammy-updates,jammy-security 535.154.05-0ubuntu0.22.04.1 amd64

```
Try all the versions of those also.

Between installing a version, I recommend as NVidia does, to uninstall the previous version befrom installing another:
```

sudo apt remove --purge nvidia* libnvidia*

```

---

### Post by brad-s144 on 2024-01-30
I did update everything with the Alienware Control Centre, but I will run it again.

The out put you requested:
```

brad@brad-Alienware-m16-R1-AMD:~$ sudo ubuntu-drivers devices
[sudo] password for brad: 
== /sys/devices/pci0000:00/0000:00:01.1/0000:01:00.0 ==
modalias : pci:v000010DEd000028E0sv00001028sd00000BFDbc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-driver-525 - distro non-free
driver   : nvidia-driver-535-server - distro non-free
driver   : nvidia-driver-545-open - distro non-free
driver   : nvidia-driver-525-server - distro non-free
driver   : nvidia-driver-525-open - distro non-free
driver   : nvidia-driver-535 - distro non-free recommended
driver   : nvidia-driver-545 - distro non-free
driver   : nvidia-driver-535-open - distro non-free
driver   : nvidia-driver-535-server-open - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

brad@brad-Alienware-m16-R1-AMD:~$ sudo ubuntu-drivers list
nvidia-driver-535-server, (kernel modules provided by linux-modules-nvidia-535-server-generic-hwe-22.04)
nvidia-driver-525, (kernel modules provided by linux-modules-nvidia-525-generic-hwe-22.04)
nvidia-driver-545, (kernel modules provided by nvidia-dkms-545)
nvidia-driver-535-server-open, (kernel modules provided by linux-modules-nvidia-535-server-open-generic-hwe-22.04)
nvidia-driver-545-open, (kernel modules provided by nvidia-dkms-545-open)
nvidia-driver-525-server, (kernel modules provided by linux-modules-nvidia-525-server-generic-hwe-22.04)
nvidia-driver-525-open, (kernel modules provided by linux-modules-nvidia-525-open-generic-hwe-22.04)
nvidia-driver-535, (kernel modules provided by linux-modules-nvidia-535-generic-hwe-22.04)
nvidia-driver-535-open, (kernel modules provided by linux-modules-nvidia-535-open-generic-hwe-22.04)
brad@brad-Alienware-m16-R1-AMD:~$ grep .  /sys/module/nvidia/version
535.154.05
brad@brad-Alienware-m16-R1-AMD:~$ grep .  /proc/driver/nvidia/version 
NVRM version: NVIDIA UNIX x86_64 Kernel Module  535.154.05  Thu Dec 28 15:37:48 UTC 2023
GCC version:  gcc version 12.3.0 (Ubuntu 12.3.0-1ubuntu1~22.04) 

```

So far, I have tried "nvidia-driver-525 - distro non-free", "nvidia-driver-535-open - distro non-free", and "xserver-xorg-video-nouveau - distro free builtin", but I have not tried uninstalling first - I'll give it a shot.

I have tried the Nouveau driver without success - wondering if this means the problem isn't with NVidea?

---

### Post by brad-s144 on 2024-01-30
On further bit of info - I am trying the software rendering version of Cinnamon presently. So far (about an hour) I haven't had the problem.

---

### Post by brad-s144 on 2024-01-30
Shortly after posting the last message it happened again, so software rendering does not solve the issue. I'll try updating bios, etc and the different driver versions (and submitting a bug report) when I have a bit of time after work.

Thanks for all of the suggestions.

---

### Post by #&amp;thj^% on 2024-01-30
@ brad-s144 I had others report Driver 545 helped with your same card, but involves a 3rd party PPA
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update  ## for good measure

```
Now before anything else or before install the new driver, you need to remove --purge any current driver:
```
sudo apt autoremove --purge nvidia*
```
This is not necessary but it insures a clean install>>>reboot
Now install the new nvidia driver ie:
```
sudo apt install nvidia-driver-545 nvidia-dkms-545
```
And yes another reboot to the new driver.
Mine is vastly improved:
```
nvidia-smi |grep Driver
| NVIDIA-SMI 545.29.06              Driver Version: 545.29.06    CUDA Version: 12.3  
```
```
Graphics:
  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] vendor: Lenovo
    driver: nvidia v: 545.29.06 arch: Ampere pcie: speed: 5 GT/s lanes: 8 ports:

```

---

### Post by brad-s144 on 2024-01-30
I think the 545 driver might have solved it. I updated and then opened a dozen simultaneous youtube videos playing in different tabs. Every previous time I tried this, I would have the display issues long before I got that far.

So far everything seems to be stable. I'll try using the computer booted into Linux for work for a day or so to be sure, but so far so good!

I assume if it does work out I should edit the original post to add that it is solved?

Thanks for everyone's help, much appreciated!

---

### Post by brad-s144 on 2024-01-30
Apparently I spoke too soon.

Does seem to be much more stable, but it unfortunately crashed again shortly after I posted. I'll take MAFoElffen's advice and try filing a bug report.

---

### Post by #&amp;thj^% on 2024-01-30
Keep us posted
Never mind I just saw this
> **brad-s144 said:**
> Apparently I spoke too soon.

Does seem to be much more stable, but it unfortunately crashed again shortly after I posted. I'll take MAFoElffen's advice and try filing a bug report.
Yep bug-reporting time

---

### Post by #&amp;thj^% on 2024-01-31
Please also check this: [https://forums.developer.nvidia.com/t/are-there-nvidia-drivers-for-the-rtx-4070-for-linux/250726](https://forums.developer.nvidia.com/t/are-there-nvidia-drivers-for-the-rtx-4070-for-linux/250726)
I spoke with a couple of Devs they point out and verified by some users:
> Manually installing the 525 driver and blacklisting nouveau via terminal commands worked fine. using the Ubuntu-drivers method does not work. 

I'm now wondering why we have an Official PPA if they are not providing a correct binary??? (In other words touched by Ubuntu instead of using nVidia )

---

### Post by brad-s144 on 2024-01-31
I'm pretty new to Linux - could you clarify how blacklisting a driver  works? Is that the same purging process as when changing to a different  NVidia version?

I haven't found any difference so far in  installing the drivers with the command line vs the software &  drivers update GUI, but I'll stick with command line going forward just  in case.

I've reached out to NVidia support as well as starting a thread in their forum - I'll update here if I get a solution from them.

---

### Post by MAFoElffen on 2024-01-31
usually if the NVidia drivers are installed, it blacklists the nouveau driver...

You can check the via:
```

mafoelffen@msi-ubuntu:~$ for File in /etc/modprobe.d/*.conf /usr/lib/modprobe.d/*.conf ; do echo ""; echo $File; grep 'nouveau' $File; done

/etc/modprobe.d/alsa-base.conf

/etc/modprobe.d/amd64-microcode-blacklist.conf

/etc/modprobe.d/blacklist-ath_pci.conf

/etc/modprobe.d/blacklist.conf

/etc/modprobe.d/blacklist-firewire.conf

/etc/modprobe.d/blacklist-framebuffer.conf

/etc/modprobe.d/blacklist-modem.conf

/etc/modprobe.d/blacklist-oss.conf

/etc/modprobe.d/blacklist-rare-network.conf

/etc/modprobe.d/dkms.conf

/etc/modprobe.d/intel-microcode-blacklist.conf

/etc/modprobe.d/iwlwifi.conf

/etc/modprobe.d/mdadm.conf

/etc/modprobe.d/nvidia-graphics-drivers-kms.conf

/etc/modprobe.d/vfio.conf

/usr/lib/modprobe.d/aliases.conf

/usr/lib/modprobe.d/blacklist_linux_5.15.0-92-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-6.5_6.5.0-14-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-6.5_6.5.0-15-generic.conf

/usr/lib/modprobe.d/fbdev-blacklist.conf

/usr/lib/modprobe.d/nvidia-graphics-drivers.conf
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off

/usr/lib/modprobe.d/systemd.conf

```
You can see from mine, it found nouveau blacklisted in file /usr/lib/modprobe.d/nvidia-graphics-drivers.conf...

If you do not find it in any, you can either add it to a file in one of those two directories... For example, do the following command:
```

sudo nano /etc/modprobe.d/blacklist-nouveau.conf

```
add the 3 following lines, 
```

blacklist nouveau
options nouveau modeset=0
install nouveau /bin/false

```
Save & exit. Then run the following command
```

sudo update-initramfs -c -k all

```
Or... Add "modprobe.blacklist=nouveau" as a boot parameter to line GRUB_CMDLINE_LINUX_DEFAFAULT of file /etc/default/grub.

---

### Post by brad-s144 on 2024-02-01
Ah, thanks. Looks like I have the same output as you.

NVidia support has got back to me with some followup questions - hopefully they will have a resolution.

---

### Post by #&amp;thj^% on 2024-02-01
> **brad-s144 said:**
> I'm pretty new to Linux - could you clarify how blacklisting a driver  works? Is that the same purging process as when changing to a different  NVidia version?

I haven't found any difference so far in  installing the drivers with the command line vs the software &  drivers update GUI, but I'll stick with command line going forward just  in case.

I've reached out to NVidia support as well as starting a thread in their forum - I'll update here if I get a solution from them.

Good let them help, as I'm on the fence with the Auto-installer from Ubuntu. :)

I was pointing to the binary straight from nVidia.com
MAFoEllfen points to how our or Ubuntu install take care blacklisting  the nouveau driver.

But you are new to Ubuntu so I won't take you down a harder method to install nVidias driver.

I'm watching with a big curiosity now though. :)

---

### Post by brad-s144 on 2024-02-02
I received a response from the NVidia forums: "The internal display is driven by the AMD igpu, the nvidia gpu doing  nothing. kernel 6.5 is known to have some bugs in the amdgpu driver but  currently, on the 6.7.3 kernel, the nvidia driver doesn’t compile. So  you might want to use the liquorix ppa to upgrade the kernel to check  whether your amd gpu functions properly, knowing the nvidia gpu won’t  work."

I'm thinking of trying upgrading Ubunu to v23 over the weekend - any other recommendations? Or is this a bad idea?

---

### Post by #&amp;thj^% on 2024-02-02
AMD what?? I'm not sure I'm buying that:
```
inxi -Gxxz
Graphics:
  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] vendor: Lenovo
    driver: nvidia v: 545.29.06 arch: Ampere pcie: speed: 8 GT/s lanes: 8 ports:
    active: none off: HDMI-A-1 empty: DP-1,DP-2,eDP-1 bus-ID: 01:00.0
    chip-ID: 10de:25e0
  Device-2: AMD Cezanne [Radeon Vega Series / Radeon Mobile Series]
    vendor: Lenovo driver: amdgpu v: kernel arch: GCN-5 pcie: speed: 8 GT/s
    lanes: 16 ports: active: eDP-2 empty: none bus-ID: 05:00.0
    chip-ID: 1002:1638 temp: 33.0 C
  Device-3: Bison Integrated Camera driver: uvcvideo type: USB rev: 2.0
    speed: 480 Mb/s lanes: 1 bus-ID: 1-3:3 chip-ID: 5986:2137
  Display: x11 server: X.Org v: 21.1.11 compositor: kwin_x11 driver: X:
    loaded: amdgpu,nvidia unloaded: modesetting alternate: fbdev,nouveau,nv,vesa
    dri: radeonsi gpu: amdgpu,nvidia,nvidia-nvswitch display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 96
  Monitor-1: HDMI-A-1 mapped: HDMI-1-0 note: disabled model: 32S321 res: N/A
    dpi: 69 diag: 815mm (32.1")
  Monitor-2: eDP-2 mapped: eDP-1 pos: primary model: AU Optronics 0xd1ed
    res: 1920x1080 dpi: 142 diag: 394mm (15.5")
  API: EGL v: 1.5 platforms: device: 0 drv: nvidia device: 2 drv: radeonsi
    device: 3 drv: swrast gbm: drv: nvidia surfaceless: drv: nvidia x11:
    drv: radeonsi inactive: wayland,device-1
  API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: amd mesa v: 23.3.5-arch1.1
    glx-v: 1.4 direct-render: yes renderer: AMD Radeon Graphics (radeonsi
    renoir LLVM 16.0.6 DRM 3.54 6.6.15-1-lts) device-ID: 1002:1638
  API: Vulkan v: 1.3.276 surfaces: xcb,xlib device: 0 type: discrete-gpu
    driver: nvidia device-ID: 10de:25e0

```
> I'm thinking of trying upgrading Ubunu to v23 over the weekend - any other recommendations? Or is this a bad idea? 

Don't chase to just a point release 23.10 stay with the LTS 22.04.

I'm going to call nVidia out on this one. BTW could you include that link from nvidia forums.

---

### Post by #&amp;thj^% on 2024-02-02
There seems to be a lot of talk about open kernel modules vs closed source modules.

But to prove a point I installed the  liquorix kernel with my nvidia driver in place.
```
uname -r
6.7.3-lqx1-3-lqx

```
```
nvidia-smi |grep NVIDIA-SMI
| NVIDIA-SMI 545.29.06              Driver Version: 545.29.06    CUDA Version: 12.3    
```
I see on my end no difference>>>but that don't mean you won't gain from it.

If you want instructions for that kernel just let me know.
NOTE: I won't be responsible if it kills your system, so Have Good Back-ups before.

And who knows when they will release a "hot fix"

---

### Post by brad-s144 on 2024-02-02
> 
BTW could you include that link from nvidia forums

It's at [https://forums.developer.nvidia.com/t/display-issue-with-alienware-m16-with-geforce-rtx-4060-gpu-on-ubuntu-cinnamon/280864](https://forums.developer.nvidia.com/t/display-issue-with-alienware-m16-with-geforce-rtx-4060-gpu-on-ubuntu-cinnamon/280864) Basically just the one answer so far.

> 
If you want instructions for that kernel just let me know.

Yes please!

> 
NOTE: I won't be responsible if it kills your system, so Have Good Back-ups before.

Absolutely. I'm actually waiting to get everything up and running properly before I set everything up on this computer, so no loss yet if things go sideways. I'm actually thinking of wiping everything and reinstalling Linux (maybe a different distro?) if nothing else works.

Appreciate the help I've got so far at this forum. This is beyond my knowledge/what I've been able to google - and I really don't like running sudo commands from random google searches without understanding exactly what they do.

I have a help ticket with NVidia, but so far it's basically just been following a generic script (update/clean install drivers, try different resolutions, refresh rates, etc.) One thing that did come up, if I try to change the resolution from the recommended (and maximum) value of 2560x1600 to any other value, the system locks up completely for about 20 seconds, with the screen looking like the attached image. After that, it resets itself back to 2560x1600. Not sure if that's a helpful symptom?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293381&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2024-02-03
Good Grief that is an ugly mess....yuck.
Ok it's very easy now via:
```
curl -s 'https://liquorix.net/install-liquorix.sh' | sudo bash

```
Stop on any errors it throws and post them here so I can see them.
And reboot, BTW just leave the current nVidia driver installed.
Fingers Crossed

EDIT:
I forgot to add you may need to select Advanced options in grub to boot to the -liquorix kernel.

---

### Post by #&amp;thj^% on 2024-02-03
This helped mine with the nVidia binary from Nividia.com. (Note I've not had any problems on mine) 
Also I'm running all "devel.sources" but not recommended or suggested.
Results:
```
apt list nvidia-driver-545* --installed
Listing... Done

```
Nothing installed from Ubuntu source.
with the driver and new kernel:
```
nvidia-smi |grep -e NVIDIA-SMI -e 0 && uname -r
Sat Feb  3 15:22:35 2024       
| NVIDIA-SMI 545.29.06              Driver Version: 545.29.06    CUDA Version: 12.3     |
|   0  NVIDIA GeForce RTX 3050 ...    Off | 00000000:01:00.0 Off |                  N/A |
| N/A   30C    P0             749W /  60W |      9MiB /  4096MiB |      0%      Default |
|    0   N/A  N/A       942      G   /usr/lib/xorg/Xorg                            4MiB |
6.7.3-3-liquorix-amd64

```

I've actually gained a few "fps"

---

### Post by brad-s144 on 2024-02-03
Well, it upgraded no problem. Currently running version 6.7.3-3, and NVidia driver version 550.40.07. The driver I am using is from the PPA that was recommended a few posts back  (I have tried both the 545 and 550 versions from there).

It now (using the v6.7 kernel) lets me change the screen resolution without any issues, so a definite step forward.

Still have the original issue where everything collapses into a mess of pixels after a while, unfortunately (where "a while" seems to be some time in the range of maybe 15 minutes to a couple of hours).

I have had a response from NVidia - they only offer Windows support; Linux support is through their forum.

I'll have some time to poke away at this tomorrow - I I was thinking I'd go through any log files I can find (or google) to see if I can find anything useful - appreciate any advice/pointers!

---

### Post by #&amp;thj^% on 2024-02-03
> **brad-s144 said:**
> Well, it upgraded no problem. Currently running version 6.7.3-3, and NVidia driver version 550.40.07. The driver I am using is from the PPA that was recommended a few posts back  (I have tried both the 545 and 550 versions from there).

I believe the 550 is using open source modules and closed source modules ie:
```
nvidia-driver-550, (kernel modules provided by nvidia-dkms-550)
nvidia-driver-550-open, (kernel modules provided by nvidia-dkms-550-open)

```
> **brad-s144 said:**
> 
Still have the original issue where everything collapses into a mess of pixels after a while, unfortunately (where "a while" seems to be some time in the range of maybe 15 minutes to a couple of hours).
I'm curious to see which your running though?
> **brad-s144 said:**
> 
I have had a response from NVidia - they only offer Windows support; Linux support is through their forum.

I'll have some time to poke away at this tomorrow - I I was thinking I'd go through any log files I can find (or google) to see if I can find anything useful - appreciate any advice/pointers!

makes you feel like hating nVidia corp....we are low hanging fruit to them.

I suspect this problem you have now will continue until nvidia offers a "hot-fix" sorry to say that.

EDIT: Do you feel like installing the nvidia.run binary from nvidia.com?

Also do you have switchable graphics in  you Bios? If so turn nvidia gpu off. And run off the AMD Gpu.

---

### Post by brad-s144 on 2024-02-04
> 
I'm curious to see which your running though?

I'm currently using the closed source version (although I've tried quite a few different drivers, both open & closed, including Nouveau):
```

brad@brad-Alienware-m16-R1-AMD:~$ nvidia-smi
Sat Feb  3 22:09:56 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.40.07              Driver Version: 550.40.07      CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 4060 ...    Off |   00000000:01:00.0 Off |                  N/A |
| N/A   35C    P8              2W /   90W |       8MiB /   8188MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      1764      G   /usr/lib/xorg/Xorg                              4MiB |
+-----------------------------------------------------------------------------------------+

brad@brad-Alienware-m16-R1-AMD:~$ uname -r
6.7.3-3-liquorix-amd64

```
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293388&stc=1[/IMG]

> 
Do you feel like installing the nvidia.run binary from nvidia.com?

Might as well!
If I recall correctly, I had tried doing this before I posted here. I think I had to (or at least thought I had to) compile the latest version from source to work with my system. I believe it complained about the gcc compiler on my system being a different version than the one used to compile the kernel - this was more or less where I gave up trying to solve it myself.

> 
Also do you have switchable graphics in  you Bios? If so turn nvidia gpu off. And run off the AMD Gpu

It doesn't look like that option is in the BIOS. It looks to me like I can switch between the NVidia and AMD GPS's with prime-select (and I **think** that the 'intel' choice just means 'use the CPU' so will work with amd). At least that will confirm whether or not the issue is with NVidia.

---

### Post by #&amp;thj^% on 2024-02-04
> **brad-s144 said:**
> 
It doesn't look like that option is in the BIOS. It looks to me like I can switch between the NVidia and AMD GPS's with prime-select (and I **think** that the 'intel' choice just means 'use the CPU' so will work with amd). At least that will confirm whether or not the issue is with NVidia.

Dang i forget the gcc issue, but yes for now please try the prime-select option.
Then show to confirm:
```
sudo prime-select intel
[sudo] password for me: 
Info: selecting the intel profile
Updating the initramfs. Please wait for the operation to complete:
Done

```

```
prime-select query
intel

```

Sorry I'm not myself lately but run this from the 6.7.3-3-liquorix-amd64 kernel.

---

### Post by brad-s144 on 2024-02-04
It gave me a warning message when I selected Intel:
```

brad@brad-Alienware-m16-R1-AMD:~$ sudo prime-select intel
[sudo] password for brad: 
Info: selecting the intel profile
Updating the initramfs. Please wait for the operation to complete:
\W: Possible missing firmware /lib/firmware/amd/amd_sev_fam19h_model1xh.sbin for module ccp
Done

```

Regardless, I rebooted and it is now running without NVidia (it was previously 'on-demand'):
```

brad@brad-Alienware-m16-R1-AMD:~$ prime-select query
intel

```

If it does work like this, I will be able to use the computer more-or-less how I had intended - I have some number-crunching software that make heavy use of the GPU but it is Windows only (why I had originally set it up to dual-boot). Although it would of course be nice to eventually get everything running properly in both OSs. 

The other Windows-only software I have to use seems to run fine with WINE, except for one that doesn't connect to the license server. That will likely be my next question when (if) this gets sorted...

---

### Post by brad-s144 on 2024-02-04
Well, I've had the same issue in 'Intel' mode. I'm guessing that means that the issue is with the AMD processor after all.

It looks like there is a driver package for Ubuntu 24.04 dated January 24 on their website - I will try installing that this evening (unless anyone has any different suggestions)

---

### Post by #&amp;thj^% on 2024-02-04
For proof I've seen that CPU just work : [https://forums.linuxmint.com/viewtopic.php?t=406021](https://forums.linuxmint.com/viewtopic.php?t=406021)

And you have already tried linux-oem that reportedly works but not here on yours. Post #2

This is smelling like a hardware issue, or as as already said a bug....
I wish I had more for you but alas I'm stumped...:(

---

### Post by brad-s144 on 2024-02-05
I have sort of resolved the issue.

It seems pretty clearly to be an issue with the on board AMD GPU. I tried several time using the NVidia GPU, the internal AMD GPU, and the "NVidia on demand" setting - the system crashes consistently with either of the settings that include the internal amd GPU but not in "high performance" mode (only using the external NVidia).

I decided to try updating the AMD drivers from their website, which turned out to be a bad idea. I wasn't able to boot into Linux at all after that, - I could get to the recovery menu and the GRUB terminal but nothing I tried got me past that. I tried repairing the installation, but the USB installer that I had used originally didn't even seem to recognize that I had a Linux installation and there was no option to repair it. 

I wiped the Linux partition and installed from scratch. I am getting the same behavior after re-installing, but I have set it to only use the NVidia GPU and everything has been working OK so far today. I'm don't know if this is a hardware issue with the AMD CPU I have or a configuration problem, but for now it is at least working.

In Windows everything seems to work fine - I ran a couple of GPU stress tests and the AMD GPU seemed to work fine. If I ever do have a problem on the Windows side I can see about a warranty replacement/tech support from Dell, but I doubt they will do anything for a non-standard installation.

Not sure if I should edit the subject to solved - doesn't really feel solved, but I guess it is least a work-around.

Thanks again to MAFoElffen and 1fallen for all the pointers.

---

### Post by #&amp;thj^% on 2024-02-05
No I would leave this thread as is, this is more or less a work-around but not a fix.

Nice touch in adding your hardware test as well, this most certainly is a bug or missing feature.

But I'm curious now in which mechanism did you set it to use "NVidia GPU", was it prime-select or Bios?
Yes I remember you saying you could not see a way to solely use one or the other, hence my curiosity.
Thanks

---

### Post by brad-s144 on 2024-02-05
I used prime-select - seems to be working so far!

---

### Post by #&amp;thj^% on 2024-02-07
Nice, I had some feed back from AMD and they are aware of this issue, and are working on it.

It might come in with a kernel update or just a kernel upgrade/feature....That's all I can speak of ATM

---

### Post by brad-s144 on 2024-02-08
That's great news. Hopefully a fix will make it into the new version in April if nothing else.

A bit of an update on my situation in case anyone else runs into it. I was back to using the kernel and drivers that came default with the new installation (so kernel v6.2, NVidia v535 closed source drivers) and using the "performance mode" prime profile, where the built in AMD GPU isn't used). After most of a day's use, the system locked up and was not responsive to keyboard or mouse input. I had to power off to reboot, and then it would not boot up at all. 

Long story short(er), I could only reboot by opening a terminal in the grub menu and completely removing the NVidiea drivers. once rebooted, I could reinstall the NVidiea drivers, but I could not use the "performance mode" prime profile as then it wouldn't reboot with out removing the NVidia drivers in the grub terminal .... And of course if I wasn't using the "performance mode" prime profile I was back to the original problem.

I ended up updating to the liquorix kernel (6.7.4-1-liquorix-amd64) and the beta release NVidia drivers (550.40.07). This seemed to fix the booting issue and i can now boot up with the NVidia driovers loaded. Everything seems to be stable now after a couple of days of use.

---

