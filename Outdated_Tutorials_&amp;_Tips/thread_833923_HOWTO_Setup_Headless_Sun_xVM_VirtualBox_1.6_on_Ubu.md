---
title: "HOWTO: Setup Headless Sun xVM VirtualBox 1.6 on Ubuntu Server 8.04"
date: 2008-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by kcnnc on 2008-06-19
The steps are not too difficult but I did have to find a few places for information. Search on the forum turn up nothing on this subject so hopefully this HOWTO would be helpful to someone out there.

Note: This is not using the OSE version.

Background:
VirtualBox has a very good GUI running on the host to manage guest OS. However when running a server, we typically do not want to run X on it. Fortunately VirtualBox has commandline tools to manage guest systems. It also provides the VirtualBox Remote Desktop Protocol (VRDP) to allow connection to the guest remotely. 

Clarification of terms used:
Host - refers to the machine we are trying to install VirtualBox.
Guest - the VirtualBox guest system that is setup on the host.
Remote - the PC that we are working on to connect to the host via SSH.

This setup was done on a fresh install of Ubuntu Server 8.04 with openssh-server installed.

All the following steps are done by SSH into the host from a remote (I'm using Windows for now).

**[COLOR="Blue"]1. Get required packages [/COLOR]**
Download the Ubuntu package for VirtualBox from 
[http://www.sun.com/software/products/virtualbox/get.jsp](http://www.sun.com/software/products/virtualbox/get.jsp)

Use
```
wget "download link here" -O virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb
```

We are using the non-OSE version here.

The manual from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) is also very useful.

**[COLOR="Blue"]2. Installation[/COLOR]**

```
sudo dpkg -i virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb
```

This will generate a bunch of dependencies. Fix them with
```
sudo apt-get -f upgrade
```

**[COLOR="Blue"]3. Decide on user, disk files location[/COLOR]**
First decide which user you want to run VirtualBox. Add this user to the *vboxusers* group.
```
sudo usermod -a -G vboxusers vboxuser
```

By default VirtualBox creates the directory *.VirtualBox* on the user home directory and put all the config and disk file there.
In my setup I put the disk files in /var/vbox as I had created a large partition for this purpose.

**[COLOR="Blue"]4. Install a guest OS[/COLOR]**
You will need an iso for the guest OS install CD. Copy or download it to the host.
For example we will just use ubuntu-8.04-server-i386.iso

-create a vm
```
VBoxManage createvm -name ubuntu -register
```

-config vm
```
VBoxManage modifyvm ubuntu -memory "256MB" -acpi on -boot1 dvd -nic1 nat
```

-create a disk
```
VBoxManage createvdi -filename "/var/vbox/ubuntu.vdi" -size 5000 -register
```

-add disk to vm
```
VBoxManage modifyvm ubuntu -hda "/var/vbox/ubuntu.vdi"
```

-register an install iso
VBoxManage registerimage dvd /var/vbox/ubuntu-8.04-server-i38.iso

-mount iso on vm
```
VBoxManage modifyvm ubuntu -dvd /var/vbox/ubuntu-8.04-server-i38.iso
```

-start the vm with port
```
VBoxHeadless -startvm ubuntu -p 3389 &
```
If you are running just 1 guest, the *-p 3389* is optional. For more than 1 guest, it has to listen to different port.

**[COLOR="Blue"]5 Connect from remote[/COLOR]**
Since my desktop is still Windows, I use Remote Desktop Connection. (On XP, Start>All Programs>Accessories>Communications)

For Mac, use [http://www.microsoft.com/mac/products/remote-desktop/](http://www.microsoft.com/mac/products/remote-desktop/)
Ubuntu, look at [http://ubuntuforums.org/showthread.php?t=824710](http://ubuntuforums.org/showthread.php?t=824710)

Just fill in the IP of your host (or IP:port if not the default) and you should see the Ubuntu installation waiting for you.

Other useful commands:
```
VBoxManage controlvm ubuntu poweroff
VBoxManage controlvm ubuntu reset
```

**Getting Ubuntu Server to run in VirtualBox**
After installation and restarting, you may find that the boot up hang with this error

This kernel requires the following features not present on the CPU: 0:6

To fix this, do the following:
1. Reset the guest
2. Hit F12 to choose to boot from the CD. (It goes by pretty quickly, reset again if you miss it.)
3. Select Rescue a broken system
4. After going through the install screens you will get a command prompt. Select to run it on the root system.
5. Install the virtual linux-virtual kernel
```
apt-get install linux-virtual

```
6. Reboot and this should fix the restart.

**Upgrading kernel**
If the kernel on the host is upgraded, the VirtualBox kernel module need to be re-compiled. Do the following steps:
1. apt-get install make gcc linux-headers-2.6.24-19-server (other kernel header, check *uname -a*)
2. /etc/init.d/vboxdrv setup
It should recompile the VirtualBox module and everything should be working again.

---

### Post by singh.gurjeet on 2008-09-06
A great help!!! Thanks.

Here's a small suggestion though.

In the 'Getting Ubuntu Server to run in VirtualBox' section, you do not need to go to lengths to fix this error! Especially, you do not wish to change kernel of your "server" system, because the default kernel that comes with 'Ubuntu Server' edition is configured specially for server purposes.

I also learnt it the hard way, so here it goes:

With the guest shutdown, in the GUI, select your VM; Click 'General' on the right-hand side, and shoose the 'Advanced' tab. Check the 'PAE/NX' check-box, and restart your guest. You should be up and running with the default kernel of 'Ubuntu Server'.

The problem here is that the Server edition's kernel assume that the box has 'PAE' support, whereas it is disabled by default in the VirtualBox.

HTH.

---

### Post by kcnnc on 2008-09-16
Yes I forgot that enable PAE also fixes it. This was the solution I first found while searching for the problem. Later I found out that there is a kernel specially built for virtual client and thought this might be the "right" thing to do.

Tell you the truth, I did it the lazy way too.

The command to do this for those using the commandline is:
```
VBoxManage modifyvm ubuntu -pae on
```

---

### Post by stromdal on 2008-09-17
Thanks singh.gurjeet for providing me with the simple solution to getting Ubuntu Server up and running under VirtualBox!

Thanks also to kcnnc for creating this apprehensive guide to setting up VirtualBox from CLI. I've just started exploring VirtualBox and I'm running it on a Ubuntu Desktop for now but will probably migrate to Server before deploying it, so this guide will come in handy within short.

---

### Post by Predatorian on 2011-02-05
Hello, i know this post is a bit old, and i had to adapt the commands a bit to make them work with the updated version of VirtualBox. but when i execute:

```
vboxmanage modifyvm ubuntu_server_10.04 --memory "256MB"
```

i get this error

```
VBoxManage: error: --memory: RTGetOpt: Command line option has argument with bad format.
```

i have no idea what this means.

---

