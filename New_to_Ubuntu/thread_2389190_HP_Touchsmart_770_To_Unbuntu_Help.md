---
title: "HP Touchsmart 770 To Unbuntu Help"
date: 2018-04-12
forum: New to Ubuntu
---

### Post by dragooness on 2018-04-12
Warning, I am a technical moron with NO experience with the OS.

The computer had nothing but issues with windows 7, a friend told me to try this. I made a USB version, and decided to do a test run before install. The graphis are.. odd. Odd colors, very hard to read and a line down the screen at one place.

This is the 64 bit installation of 16.04 LTS.
Has NVIDIA GeForce Go 7600 graphics card.

Other than the screen, touchscreen and mouse/keyboard works. Can someone please help me?

---

### Post by mörgæs on 2018-04-13
Hi, welcome to the fora.

Please copy ```
sudo lshw -C video
``` and paste it to the command line, run it and post the results here in CODE tags.

---

### Post by dragooness on 2018-04-13
hope this is right, cant really see.
```

ubuntu@ubuntu:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: G73M [GeForce Go 7600]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:24 memory:f7000000-f7ffffff memory:d0000000-dfffffff memory:f6000000-f6ffffff ioport:ec00(size=128) memory:c0000-dffff
ubuntu@ubuntu:~$ sudo lshw - C video


```

---

### Post by mörgæs on 2018-04-13
You are using the open source *nouveau* driver which normally is working fine. 

However, I know of many examples of Geforce 6xxx-cards which work better given the closed source *Nvidia* drivers. Since your card is close to I think it's worth a test.

You could try to see under Additional / Restricted drivers if anything is available for your card. Only this approach to begin with; don't download stuff manually.

---

### Post by oldfred on 2018-04-13
That is an older video card/chip. Be sure to only install the correct video driver or else you can make things worse.
And if incorrect one installed, you must totally purge incorrect one or you get conflicts as new one does not delete old one.

Based on this, it looks like all the 7600 series use the 304.xx series of legacy drivers.
 Legacy drivers by GPU model 
[URL="http://www.nvidia.com/object/IO_32667.html"]http://www.nvidia.com/object/IO_32667.html
[/URL]
 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Only install from Ubuntu repository, not directly from nVidia.
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
#in terminal type:
ubuntu-drivers devices

---

### Post by dragooness on 2018-04-13
Terminal gave me a preferred driver type how do I go about getting that installed? Well, it gave me two lines called driver

xserver-xoro-video-nouvaeu - distro free builtin
nvidia-304 - distro non-free recommended 

Also my wireless keyboard will not work, but the mouse will.

---

### Post by oldfred on 2018-04-13
If from terminal and not gui.

 sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by dragooness on 2018-04-13
Got this
```

dragooness@dragooness-RN635AA-ABA-IQ770:~$ sudo ubuntu-drivers autoinstall
[sudo] password for dragooness: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Depends: dkms but it is not installable
              Depends: lib32gcc1 but it is not installable
              Recommends: nvidia-settings (>= 331.20) but it is not installable
              Recommends: libcuda1-304 but it is not going to be installed
              Recommends: nvidia-opencl-icd-304 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
dragooness@dragooness-RN635AA-ABA-IQ770:~$ 

```

---

### Post by oldfred on 2018-04-13
I am using 16.04, but not any nVidia, but have dkms installed?

What does this show?
sudo apt install dkms

```
fred@Z170N:~$ sudo apt install dkms
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.2.0.3-2ubuntu11.5).
```

---

### Post by dragooness on 2018-04-14
```

dragooness@dragooness-RN635AA-ABA-IQ770:~$ sudo apt install dkms
[sudo] password for dragooness: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 72 not upgraded.
Need to get 66.3 kB of archives.
After this operation, 265 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 dkms all 2.2.0.3-2ubuntu11.5 [66.3 kB]
Fetched 66.3 kB in 4s (13.9 kB/s)
Selecting previously unselected package dkms.
(Reading database ... 211203 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.5_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.5) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up dkms (2.2.0.3-2ubuntu11.5) ...
dragooness@dragooness-RN635AA-ABA-IQ770:~$ 

```

I will try the other command again

Edit : Its installation something, cant tell what.

Edit 2 : It ran, rebooted. Graphics is fixed, but now theres another issue. The mouse moves, it can not select anything nor will hovering over an icon get a result. The touchscreen has the same issue

---

### Post by dragooness on 2018-04-17
Bump

---

### Post by oldfred on 2018-04-17
Now a touch screen issue.
Better to start new thread and put model & issue in title and those that may know more about those type of issues should help.

---

