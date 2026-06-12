---
title: "Problem with nvidia drivers, can't pass through the login screen!"
date: 2017-10-27
forum: New to Ubuntu
---

### Post by pukiking- on 2017-10-27
Ever since I tried installing Linux on my laptop I've had problems because of integrated and dedicated graphic card. First I couldn't even get into instalation, later I found out that I need edit something at startup and put "nomodeset" before "quiet splash". My laptop is working extremly slow, and I was trying to find a solution to the problem with drivers. I followed the steps on this youtube video [https://youtu.be/cVTsemATIyI](https://youtu.be/cVTsemATIyI) , but instaled the driver for my graphic card ([http://us.download.nvidia.com/XFree86/Linux-x86_64/384.90/NVIDIA-Linux-x86_64-384.90.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/384.90/NVIDIA-Linux-x86_64-384.90.run))
Now after following these steps and installing it succesfully, I get to the Login screen, write the password and it puts me back to the login screen again. 

I have ASUS K550V laptop.
Procesor intel i7
Graphics:
Nvidia 950m
Intel 530 HD
8GB RAM...

Thanks in advance!

Edit: tried repeating the process. On the instalation it tells me "The distribution-provided pre-install has failed. Continue the instalation?", so I guess drivers can't even get installed properly.

---

### Post by Bashing-om on 2017-10-27
pukiking-; Hello

Well, this is a fine mess :)

Look:
[http://www.nvidia.com/download/driverResults.aspx/123918/en-us](http://www.nvidia.com/download/driverResults.aspx/123918/en-us)
where nvidia advises " do not do this" :
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


So now the questions to begin the clean up and install the proper graphic's driver.
Gain a console interface; at the login screen key combo ctl+alt+F2. Login here with username and pass word - there will be no response to the screen when password is entered . do the pass word carefully and blindly .
Please post the outputs - Between Code tags - of terminal commands:
```

[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"
lsb_release -a
uname -r
sudo find / -name "NVIDIA-Linux-*"
dpkg -l | grep -i nvidia*
lspci -k|grep -iEA5 'vga|3d'

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Get the driver installed - ain't nothing but a thing

Just to learn how

---

### Post by pukiking- on 2017-10-27
@Bashing-om ty for reply
Here it goes
```
 Installed in Legacy mode

No LSB modules are aviable
Distributor ID: Ubuntu
Description: Ubuntu 17.04
Release: 17.04
Codename: zesty

4.10.0-37-generic

find:'/run/user/112/gvfs': Permission denied
/home/nikola/Downloads/NVIDIA-Linux-x86_64-384.90.run
/home/nikola/Downloads/NVIDIA-Linux-x86_64-375.39.run

ii bbswitch-dkms                         0.8-4ubuntu1                           amd64       Interface for toggling the power on NVIDIA Optimus video cards

00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
              Subsystem: ASUSTeK Computer Inc. HD Graphics 530
              Kernel driver in use: i915
              Kernel modules: i915
00:04.0 Signal processing controler: Intel Corporation Skylake Processor Thermal Subsystem (rev 07)
               Subsystem: ASUSTeK Computer Inc. Skylake processor Thermal Subsystem
--
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce 950M] (rev a2)
              Subsystem: ASUSTeK Computer Inc. GM107M [GeForce 950M]
              Kernek driver in use: nvidia
              Kernel modules: nvidia, noveau, nvidia_drm, nvidia
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter
              Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter 
```
[IMG]http://www.dodaj.rs/images/TeIw2.jpg[/IMG]

---

### Post by Bashing-om on 2017-10-27
pukiking-; Hummm ...

According the the ' dpkg -l | grep -i nvidia* ' output the driver did not install . Likely a good thing as we do not care about installing from OEM .

Let's clean up and have the system install the proprietary driver from our software repository.

Boot into the firmware settings and disable secure boot !

from the F2 console run:
```

cd Downloads
./ NVIDIA-Linux-x86_64-375.39.run --uninstall
./ NVIDIA-Linux-x86_64-384.90.run --uninstall
sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf 
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall
cd

```
Reboot at this time and advise on the effects :
```

sudo dpkg -l | grep -i nvidia*

```

An advisory " libEGL.so.1 is not a symbolic link" ? IF so and you want we can also correct that .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by pukiking- on 2017-10-28
[IMG]http://www.dodaj.rs/images/Tq1dn.jpg[/IMG]
No file xorg.conf , as you can see on the picture, should I remove the ones with simulare name or just go to the next step?

---

### Post by Bashing-om on 2017-10-28
pukiking-; Hey ...

Go on to the next step . 
In hybrid graphics that file is required but the installer will make up a new one - If things go right .

[INDENT][INDENT]there is that process
[/INDENT][/INDENT]

---

### Post by pukiking- on 2017-10-29
So the drivers seem to be working, and have been installed properly.
[IMG]http://www.dodaj.rs/images/TRPyY.jpg[/IMG]

I have few more problems on Ubuntu, like it working pretty slowly (if needed I will dual boot just to check if it is about hardware or OS, but I'm pretty sure it's OS)
Also the problem with wireless connection. It works perfectly for stuff  like terminal and on console run.

Do I need to open a new thread for that?

---

