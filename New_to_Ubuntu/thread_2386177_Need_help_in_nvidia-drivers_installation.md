---
title: "Need help in nvidia-drivers installation"
date: 2018-03-01
forum: New to Ubuntu
---

### Post by dsfx3d on 2018-03-01
Hi,

I'm fairly new to ubuntu and can't figure out how to properly install nvidia-drivers on my system.

I'm running Ubuntu 16.04.03 on hp-pavilion 15 | geforce 740m

I've tried many ways for installing gpu drivers but they never work; this is what i've done:

**0. Disabled nouveau**

**1. Installation from terminal**:
tried installing from terminal but the system boots in low graphic mode. I purged nvidia-* to fix that, then tried lspci to check VGA compatible controllers

lspci returned something like this:

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
.
.
.
0a:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)

```

I assumed that maybe my graphic card doesn't support VGA display and that's why low graphics mode, so I googled again and downloaded a runfile from nvidia
[B]
2. Manual Installation
[/B]
stopped lightdm > switched to tty > started the runfile with option '--no-opengl-files' > the drives installed and I rebooted. 
after reboot i tried nvidia-detector, it returns none. I thought maybe the drivers weren't installed so I opened Software and Updates >> Additional Drivers: it said the device is using alternative drivers and 'continue using manually installed drivers' was selected.

I'm confused please help with the installation

---

### Post by Bashing-om on 2018-03-01
,dsfx3d; Hello - Welcome to the forum.

Are you making this install of a driver more difficult than it is ?
Is this a EFI system that requires disabling 'secure boot' in the firmware to permit 3rd party software installation ?

At this point we clean up the system and get ready to install the correct driver:
per nvidia the driver you want is the 390 version:
[http://www.nvidia.com/download/driverResults.aspx/130646/en-us](http://www.nvidia.com/download/driverResults.aspx/130646/en-us)

Note nvidia's advise here:
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


the 390 version driver is in our repo:
> 
sysop@x1604:~$ apt list nvidia-390
Listing... Done
nvidia-390/xenial 390.25-0ubuntu0~gpu16.04.1 amd64
sysop@x1604:~$ 


Cleanup : - we start here - post back - Between code tags - the outputs of terminal commands :
```

sudo find / -name "NVIDIA-Linux-*"
dpkg -l | grep -i nvidia*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

once cleaned up and ready, we install the correct driver .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-01
Thanks for replying,

According to this: [https://unix.stackexchange.com/questions/148356/how-to-know-if-im-booting-using-uefi](https://unix.stackexchange.com/questions/148356/how-to-know-if-im-booting-using-uefi)
I'm using BIOS and I do require to disable secure boot, or no GRUB on boot


This is different then yours:
```

dsfx3d@dope-pc:~$ apt list nvidia-390
Listing... Done
nvidia-390/unknown 390.30-0ubuntu1 amd64
dsfx3d@dope-pc:~$ 

```

why the 'unknown' and:
```

dsfx3d@dope-pc:~$ sudo find / -name "NVIDIA-Linux-*"
find: ‘/run/user/1000/gvfs’: Permission denied
/home/dsfx3d/Software/nvdia/NVIDIA-Linux-x86_64-390.25.run
^C

dsfx3d@dope-pc:~$ dpkg -l | grep -i nvidia*
ii  bbswitch-dkms                              0.8-3ubuntu1                                 amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcupti-dev:amd64                         7.5.18-0ubuntu1                              amd64        NVIDIA CUDA Profiler Tools Interface development files
ii  libcupti-doc                               7.5.18-0ubuntu1                              all          NVIDIA CUDA Profiler Tools Interface documentation
ii  libcupti7.5:amd64                          7.5.18-0ubuntu1                              amd64        NVIDIA CUDA Profiler Tools Interface runtime library



```

---

### Post by Bashing-om on 2018-03-01
dsfx3d; Well ..

Maybe you do not see the 390 driver because you are not updated ?
My system: running the 384 version driver -
> 
sysop@x1604:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	[color=green]Ubuntu 16.04.4 LTS[/color]
Release:	16.04
Codename:	xenial
sysop@x1604:~$ 

sysop@x1604:~$ dpkg -l | grep -i nvidia*
ii  bbswitch-dkms                               0.8-3ubuntu1                               amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-384                                384.111-0ubuntu0.16.04.1                   amd64        NVIDIA CUDA runtime library
ii  nvidia-375                                  384.111-0ubuntu0.16.04.1                   amd64        Transitional package for nvidia-384
ii  nvidia-384                                  384.111-0ubuntu0.16.04.1                   amd64        NVIDIA binary driver - version 384.111
ii  nvidia-opencl-icd-384                       384.111-0ubuntu0.16.04.1                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             390.25-0ubuntu0~gpu16.04.1                 amd64        Tool for configuring the NVIDIA graphics driver
sysop@x1604:~$



Let's do this:

Do make sure that secure boot is disabled

and 
run:
```

cd /home/dsfx3d/Software/nvdia/
sudo ./NVIDIA-Linux-x86_64-390.25.run --uninstall
sudo apt purge nvidia*
sudo rm /etc/X11/Xorg.conf
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```

Where here I am not sure that the purge of nvidia will also remove the libcupti packages - play this by ear.

reboot to see the effect .

If the driver installs we will leave CUDA for a new thread .

[INDENT][INDENT][INDENT]maybe Yes[/INDENT][/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-01
It didn't worked, the drivers installed but system rebooted in low graphics mode so had to purge the drivers to rollback

---

### Post by Bashing-om on 2018-03-01
dsfx3d; Well -

> **dsfx3d said:**
> It didn't worked, the drivers installed but system rebooted in low graphics mode so had to purge the drivers to rollback

Without the logs from that bad install, and see the files that were or were not installed - I do not know what else to do.


[INDENT][INDENT]sometimes I just can not know
[/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-01
how to get the logs

---

### Post by Bashing-om on 2018-03-01
dsfx3d; 

> 
how to get the logs


We do not now as they are gone with the reboot.

If you want, we can  start this process all over ,, and in small steps, showing what results at each step .. then we look at the logs .

show us now the results of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo lshw -C display

```

Then we see what is to be done next.

[INDENT][INDENT][INDENT]seek and ye shall find[/INDENT][/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-01
logs of each command are in attached text files 

[ATTACH]278733[/ATTACH]
[ATTACH]278734[/ATTACH]
[ATTACH]278735[/ATTACH]

---

### Post by QIII on 2018-03-02
Hello!

Many of our users (myself included) are not inclined to directly open files attached directly in the body of a post.  There is no way for anyone to know if something malicious may be contained in them.

It is much better to use [https://paste.ubuntu.com/](https://paste.ubuntu.com/) and post the URLs.  Would you please do that?

Thanks.

---

### Post by dsfx3d on 2018-03-02
Apologies, didn't knew that.

apt update log:
[https://paste.ubuntu.com/p/tNzs62tbDh/](https://paste.ubuntu.com/p/tNzs62tbDh/)

apt upgrade log:
[https://paste.ubuntu.com/p/wmVRXPgpB4/](https://paste.ubuntu.com/p/wmVRXPgpB4/)

lshw log:
[https://paste.ubuntu.com/p/NkBYkN9vrP/](https://paste.ubuntu.com/p/NkBYkN9vrP/)

---

### Post by Bashing-om on 2018-03-02
dsfx3d; Hummm ...

I am UNdecided on a best means to proceed. 
Presently there is no driver installed to support nvidia and I have no real idea yet why not .

A good possibility is the existence of the CUDA PPA in conflict with the nvidia driver .
What is your use case for CUDA, can we not purge it ?

also you have the out of train repo security.ubuntu.com/ubuntu/trusty in your source list . I have no idea what might have resulted with that source enabled . Why is this done ?
Then too are the missing signing keys for PPAs, at some point will have to be dealt with.

All I know to do is back up 3 yards and
[INDENT][INDENT]punt again
[/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-05
as I said I'm fairly new to ubuntu and CUDA I intend to use for GPU acceleration for deep learning and I can purge it for now.
I've tried reinstalling but the same source list show up with the same missing keys

---

### Post by Bashing-om on 2018-03-05
dsfx3d; Well,

The missing keys I am not concerned with at this time . The main issue to focus on is the graphic's driver.

I have not worked with " [http://developer.download.nvidia.com/compute/cuda/](http://developer.download.nvidia.com/compute/cuda/) ,,,, " . It may take a bit to learn how to purge that 3rd party software.

Let's see what the sources are:
post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

With the thought to revert that cuda to what is in our repo - If nvidia does not give us a clean way to remove -; and then we purge that to get a clean slate to install a graphic's driver.

[INDENT][INDENT][INDENT][INDENT]just what I think
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-06
> **Bashing-om said:**
> dsfx3d; Well,

The missing keys I am not concerned with at this time . The main issue to focus on is the graphic's driver.

I have not worked with " [http://developer.download.nvidia.com/compute/cuda/](http://developer.download.nvidia.com/compute/cuda/) ,,,, " . It may take a bit to learn how to purge that 3rd party software.

Let's see what the sources are:
post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

With the thought to revert that cuda to what is in our repo - If nvidia does not give us a clean way to remove -; and then we purge that to get a clean slate to install a graphic's driver.[INDENT][INDENT][INDENT][INDENT]just what I think
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


cat -n /etc/apt/sources.list :
[https://paste.ubuntu.com/p/g4kkHbSTvS/](https://paste.ubuntu.com/p/g4kkHbSTvS/)

tail -v -n +1 /etc/apt/sources.list.d/*
[https://paste.ubuntu.com/p/m7VYfkv8m4/](https://paste.ubuntu.com/p/m7VYfkv8m4/)

---

### Post by Bashing-om on 2018-03-06
dsfx3d; Hey ,,,

Look'n now to see if I can find a way forward .

[INDENT]back soonest
[/INDENT]

---

### Post by Bashing-om on 2018-03-06
dsfx3d; Well !

nvidia says  the UNinstaller is included:
[http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html](http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)

```

sudo /usr/local/cuda-X.Y/bin/uninstall_cuda_X.Y.pl

```

so what is the file name we need for the x.y --- 
```

ls -al /usr/local/cuda-*

```

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-06
> **Bashing-om said:**
> dsfx3d; Well !

nvidia says  the UNinstaller is included:
[http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html](http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)

```

sudo /usr/local/cuda-X.Y/bin/uninstall_cuda_X.Y.pl

```

so what is the file name we need for the x.y --- 
```

ls -al /usr/local/cuda-*

```
[INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]


there's no cuda-* like directory in /usr/local/ :mad:

---

### Post by Bashing-om on 2018-03-06
dsfx3d; Ouch !

Well. we know that cuda is broke !

Back to the drawing board .. not even going to attempt a reversion to the repo cuda .

Let's try this approach:
[https://askubuntu.com/questions/530043/removing-nvidia-cuda-toolkit-and-installing-new-one](https://askubuntu.com/questions/530043/removing-nvidia-cuda-toolkit-and-installing-new-one)

The 1st answer,  where the goal is to completely remove CUDA .

[INDENT]maybe still
[INDENT][INDENT]not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2018-03-06
What is your kernel version?

run

```
uname -r
```

and post the output.

You may be hit by this [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1750937"). If confirm that this is the case you can either log into the previous kernel or get a newer one by going HWE (we can discuss these options if indeed it is a kernel problem)

Incidentally, you don't need to blacklist nouveau if you install the Nvidia driver from .deb or the repository.

---

### Post by dsfx3d on 2018-03-06
> **Bashing-om said:**
> dsfx3d; Ouch !

Well. we know that cuda is broke !

Back to the drawing board .. not even going to attempt a reversion to the repo cuda .

Let's try this approach:
[https://askubuntu.com/questions/530043/removing-nvidia-cuda-toolkit-and-installing-new-one](https://askubuntu.com/questions/530043/removing-nvidia-cuda-toolkit-and-installing-new-one)

The 1st answer,  where the goal is to completely remove CUDA .
[INDENT]maybe still[INDENT][INDENT]not so yes
[/INDENT]
[/INDENT]
[/INDENT]


done

---

### Post by dsfx3d on 2018-03-06
> **monkeybrain20122 said:**
> What is your kernel version?

run

```
uname -r
```

and post the output.

You may be hit by this [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1750937"). If confirm that this is the case you can either log into the previous kernel or get a newer one by going HWE (we can discuss these options if indeed it is a kernel problem)

Incidentally, you don't need to blacklist nouveau if you install the Nvidia driver from .deb or the repository.

output

```
4.13.0-36-generic
```

---

### Post by Bashing-om on 2018-03-06
dsfx3d; HoKay -

Let's look now at what is installed - see what else is to be cleaned up :
```

dpkg -l | grep -i nvidia*
lsmod | grep nvidia
ls -al /etc/X11/xorg.conf

```

[INDENT][INDENT]holding my breath\
[/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2018-03-06
Looks like you have optimus (two gpus') and your machine is now using the intel card.[COLOR=#000000] From your lshw log

 ```

         * -display 
```[/COLOR]```
description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:b5000000-b53fffff memory:c0000000-cfffffff ioport:6000(size=64) memory:c0000-dffff
  *-display UNCLAIMED
       description: 3D controller
       product: GK208M [GeForce GT 740M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128)
```

There are various tutorials on the internet regarding how to configure Nvidia driver in the presence of Optimus (most involve bumblebee) But since I have not had any experience with Optimus I wouldn't recommend any in case it messes you up further. Sorry have to wait for someone else to advise you.

An easy thing that I do know how to fix is the numerous gpg errors when you run update or install. 
```
sudo add-apt-repository ppa:nilarimogard/webupd8 
sudo apt-get update
sudo apt install launchpad-getkeys
```

Then run
```
sudo launchpad-getkeys
```

You don't need launchpad-getkeys to correct the problem, you can do it manually if you remember the command (or look it up) but since you have so many of them it is a lot easier.

---

### Post by dsfx3d on 2018-03-06
> **Bashing-om said:**
> dsfx3d; HoKay -

Let's look now at what is installed - see what else is to be cleaned up :
```

dpkg -l | grep -i nvidia*
lsmod | grep nvidia
ls -al /etc/X11/xorg.conf

```[INDENT][INDENT]holding my breath\
[/INDENT]
[/INDENT]


```

dpkg -l | grep -i nvidia*
lsmod | grep nvidia

```
both returns nothing on terminal

and xorg.conf does not exist in /etc/X11/

---

### Post by Bashing-om on 2018-03-06
dsfx3dl Wonderful :)

OK, once again - with feeling :

secure boot disabled in the firmware ->
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

reboot to see the effect.

[INDENT][INDENT]could be, naybe[/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-06
> **Bashing-om said:**
> dsfx3dl Wonderful :)

OK, once again - with feeling :

secure boot disabled in the firmware ->
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

reboot to see the effect.
[INDENT][INDENT]could be, naybe[/INDENT]
[/INDENT]


Ok I did this, nvidia was installed but still I was booting in Low Graphics mode. So I purged nvidia* and autoremoved
now I'm in a login loop and only guest account works.
I tried with gdm3 but still can't log in 
also, the PATH env var is set but have to explicitly call ```
 source /etc/environment
``` every time I boot for terminal to pickup binaries.

4uck3d up :mad:

---

### Post by Bashing-om on 2018-03-06
dsfx3d; Yuk ...

With out the command outputs and the current logs of that boot... not a thing I can do ..

My crystal ball range is not that far .

As to:
> 
I tried with gdm3 but still can't log in 


Do "you" have the authority to access your desktop ?

what shows:
```

ls -al .ICEauthority .Xauthority

```

[INDENT][INDENT]many times, I just do not know
[/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-06
yes I can access desktop through tty

---

### Post by dsfx3d on 2018-03-06
> **Bashing-om said:**
> dsfx3d; Yuk ...

With out the command outputs and the current logs of that boot... not a thing I can do ..

My crystal ball range is not that far .

As to:


Do "you" have the authority to access your desktop ?

what shows:
```

ls -al .ICEauthority .Xauthority

```
[INDENT][INDENT]many times, I just do not know
[/INDENT]
[/INDENT]


I have full access, its just that the GUI isn't working for my account. but its working for guest

```

-rw------- 1 dsfx3d dsfx3d 16108 Mar  7 06:00 .ICEauthority
-rw------- 1 dsfx3d dsfx3d   104 Mar  7 06:23 .Xauthority

```

---

### Post by Bashing-om on 2018-03-06
dsfx3d; Well,

Not an authorization issue as you are authorized.

And, as the guest account is valid, must be a config issue in your personal account .
What is the desk top ?
```

ls -al /usr/share/xsessions
env | grep XDG_CURRENT_DESKTOP

```


[INDENT][INDENT]which way did he go George
[/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-06
> **Bashing-om said:**
> dsfx3d; Well,

Not an authorization issue as you are authorized.

And, as the guest account is valid, must be a config issue in your personal account .
What is the desk top ?
```

ls -al /usr/share/xsessions
env | grep XDG_CURRENT_DESKTOP

```

[INDENT][INDENT]which way did he go George
[/INDENT]
[/INDENT]


```

ls -al /usr/share/xsessions

total 24
drwxr-xr-x   2 root root  4096 Mar  7 06:15 .
drwxr-xr-x 316 root root 12288 Mar  7 06:33 ..
-rw-r--r--   1 root root   207 Aug 22  2016 gnome.desktop
-rw-r--r--   1 root root   204 Aug 22  2016 ubuntu.desktop

```

env | grep XDG_CURRENT_DESKTOP returned nothing

---

### Post by Bashing-om on 2018-03-06
dsfx3d; Welp ...


GUI can be with knotty issues, and I am not the most knowledgeable in this area .

You could try resetting lightdm and the 'greeter' by logging in to a virtual terminal (Ctrl-Alt-F1...F6) and then doing
```

sudo service gdm3 stop ##(if gdm3 DE is active) else stop lightdm
sudo dpkg-reconfigure lightdm 
sudo dpkg-reconfigure unity-greeter 
sudo service lightdm start

```

If that doesn't help, you could consider removing any saved user-sessions by deleting ~/.dmrc

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-07
> **Bashing-om said:**
> dsfx3d; Welp ...


GUI can be with knotty issues, and I am not the most knowledgeable in this area .

You could try resetting lightdm and the 'greeter' by logging in to a virtual terminal (Ctrl-Alt-F1...F6) and then doing
```

sudo service gdm3 stop ##(if gdm3 DE is active) else stop lightdm
sudo dpkg-reconfigure lightdm 
sudo dpkg-reconfigure unity-greeter 
sudo service lightdm start

```

If that doesn't help, you could consider removing any saved user-sessions by deleting ~/.dmrc
[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


nothing worked

could it be due to unset PATH variable on start up

---

### Post by jgw on 2018-03-07
I have found that if you follow the directions in one of the links below you will get it:
[http://www.exegetic.biz/blog/2017/10/ubuntu-nvidia/](http://www.exegetic.biz/blog/2017/10/ubuntu-nvidia/)
[http://www.exegetic.biz/blog/2017/10/ubuntu-nvidia/](http://www.exegetic.biz/blog/2017/10/ubuntu-nvidia/)

Basically, they tell you how to determine the right driver from nvidia and then tells you howto install the said driver into your system so you can run with it.  
I did this and got the latest driver but found that it would not handle my 4k tv set so I dropped back to the 340 driver which worked.  (sometimes you have to muck around to get one that works for YOU)

---

### Post by dsfx3d on 2018-03-07
> **Bashing-om said:**
> dsfx3d; Welp ...


GUI can be with knotty issues, and I am not the most knowledgeable in this area .

You could try resetting lightdm and the 'greeter' by logging in to a virtual terminal (Ctrl-Alt-F1...F6) and then doing
```

sudo service gdm3 stop ##(if gdm3 DE is active) else stop lightdm
sudo dpkg-reconfigure lightdm 
sudo dpkg-reconfigure unity-greeter 
sudo service lightdm start

```

If that doesn't help, you could consider removing any saved user-sessions by deleting ~/.dmrc
[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


I checked my .xsessions-error and it read errors like 
ls: command not found
cat: command not found
.
.

maybe I should try fixing the PATH not set, do you have any suggestions

---

### Post by dsfx3d on 2018-03-07
> **jgw said:**
> I have found that if you follow the directions in one of the links below you will get it:
[http://www.exegetic.biz/blog/2017/10/ubuntu-nvidia/](http://www.exegetic.biz/blog/2017/10/ubuntu-nvidia/)
[http://www.exegetic.biz/blog/2017/10/ubuntu-nvidia/](http://www.exegetic.biz/blog/2017/10/ubuntu-nvidia/)

Basically, they tell you how to determine the right driver from nvidia and then tells you howto install the said driver into your system so you can run with it.  
I did this and got the latest driver but found that it would not handle my 4k tv set so I dropped back to the 340 driver which worked.  (sometimes you have to muck around to get one that works for YOU)

Thanks for the suggestion I'll try this once I fix the login loop problem

---

### Post by Bashing-om on 2018-03-07
dsfx3d; Yeah ..

Let's do get the environmental paths correct.
what shows:
```

sudo -l -U dsfx3d
sudo sh -c 'echo $PATH'
getent passwd dsfx3d
echo $PATH

```

see what we can learn.

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-07
> **Bashing-om said:**
> dsfx3d; Yeah ..

Let's do get the environmental paths correct.
what shows:
```

sudo -l -U dsfx3d
sudo sh -c 'echo $PATH'
getent passwd dsfx3d
echo $PATH

```

see what we can learn.
[INDENT][INDENT][INDENT]we can do that
[/INDENT]
[/INDENT]
[/INDENT]


fixed it....
idk when I edited my .profile and removed $PATH from it. everything's working fine now except the nvidia driver

---

### Post by Bashing-om on 2018-03-07
dsfx3d; 

Post #36 ??

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by dsfx3d on 2018-03-07
> **dsfx3d said:**
> I checked my .xsessions-error and it read errors like 
ls: command not found
cat: command not found
.
.

maybe I should try fixing the PATH not set, do you have any suggestions

> **Bashing-om said:**
> dsfx3d; 

Post #36 ??
[INDENT][INDENT][INDENT]we can do that
[/INDENT]
[/INDENT]
[/INDENT]


forget that, can you help with the drivers now

---

### Post by Bashing-om on 2018-03-07
dsfx3d;

I say again, if you can activate the GUI in the guest session, it is not a driver issue but a config issue in your account .

---

### Post by dsfx3d on 2018-03-09
> **Bashing-om said:**
> dsfx3d;

I say again, if you can activate the GUI in the guest session, it is not a driver issue but a config issue in your account .

 GUI thing i fixed, I was asking about the driver installation

---

