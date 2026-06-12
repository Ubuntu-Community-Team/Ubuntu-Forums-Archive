---
title: "HOWTO: Compat-Wireless &amp; Fixing the ath9k ndiswrapper module problem..."
date: 2009-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Crafty Kisses on 2009-08-07
So I've seen a lot of problems on the installation of the **compat-wireless package** for some reason, so I thought I'd just give a quick howto on how to do this. This may be basic, but some new users may love this.

1) **[SIZE="5"]The essentials:[/SIZE]**

So the first thing you're going to need in order to complete the installation of the compat-wireless package is the "build-essential" package. So if you want you can run in the terminal:
```
sudo apt-get install build-essential
```

Now time after time I always see people saying "I have no working connection to begin with, how do I get the build-essential package installed?" So here's what you can do, create a symlink and mount your .iso of Ubuntu (Ubuntu CD) and run these commands in order:
```
sudo mount -o loop cd.iso /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom -m add
sudo apt-cdrom add
```
Then once you have ran those commands in order, you need to run:
```
sudo aptitude update
sudo aptitude install build-essential
```
So now that you have build-essential installed, you can continue with the compilation of compat-wireless.

2) **[SIZE="5"]The build-essential package with a netbook[/SIZE]**

I'm also seeing this tricky issue/situation where people are wanting build-essential and they don't have a net connection on both ends ethernet and wireless, now as you may know a lot of netbooks don't have a CD drive by default unless you buy the external drive. (Some of the newer netbooks might have CD drives). So I think I may have found a solution, a time consuming solution but it works none-the-less. So first you need to grab the build-essential deb package from [**here.**]("http://ftp.debian.org/debian/pool/main/b/build-essential/") You obviously need to get to a computer that has a working net connection and put these files on a flash drive. Now once you have done that you need to hunt down the dependencies, but I've taken the liberty and done that myself, so these are the dependencies you need for 32-bit:
```
binutils_2.18.1~cvs20080103-0ubuntu1_i386.deb
perl-modules_5.8.8-12_all.deb
build-essential_11.3ubuntu1_i386.deb
bzip2_1.0.4-2ubuntu4_i386.deb cpio_2.9-6ubuntu1_i386.deb
cpp_4.2.3-1ubuntu3_i386.deb
cpp-4.2_4.2.3-2ubuntu7_i386.deb
dpkg-dev_1.14.16.6ubuntu3_all.deb
g++_4.2.3-1ubuntu3_i386.deb
g++-4.2_4.2.3-2ubuntu7_i386.deb
gcc-4.2_4.2.3-2ubuntu7_i386.deb
gcc-4.2-base_4.2.3-2ubuntu7_i386.deb
libbz2-1.0_1.0.4-2ubuntu4_i386.deb
libc6_2.7-10ubuntu3_i386.deb
libc6-dev_2.7-10ubuntu3_i386.deb
libgcc1_4.2.3-2ubuntu7_i386.deb
libgomp1_4.2.3-2ubuntu7_i386.deb
libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb
libtimedate-perl_1.1600-9_all.deb
linux-libc-dev_2.6.24-19.36_i386.deb
lzma_4.43-12ubuntu1_i386.deb
make_3.81-3build1_i386.deb
patch_2.5.9-4_i386.deb
```
Now once you have all the dependencies taken care of, you can now stick your flash drive in your netbook and mount the flash drive. Now depending on what kind of flash drive you have they will usually auto mount, but if they don't you are going to have to find the mount point of your flash drive. So run in a terminal:
```
sudo fdisk -l
```
Then you need to look for your flash drive, so for example let's say the flash drive is **/dev/sdg1**, now in order to mount /dev/sdg1 you need to run:
```
mount /dev/sdg1
```
Then from there you can copy and access your files you need to compile build-essential on your netbook. Now let's go ahead and start with the compilation of compat-wireless.

3) **[SIZE="5"]Compilation of compat-wireless:[/SIZE]**

First thing is first, check what kernel you are using, you should probably be using something newer than **2.6.26** but to make sure run:
```
uname -r
```
Then grab what compat-wireless package that you need depending on the kernel. So now that we got our dependencies and checked our kernel we need to grab the latest version of the compat-wireless package, so you can run in the terminal if you have a newer kernel (2.6.27 and up):
```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30.tar.bz2

```
Now if you have an older kernel (2.6.22 through 2.6.26), you can always grab the **compat-wireless-old** package by running:
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2
```
Once you have grabbed what version you need, you are going to have to untar this, so you can run:
```
tar xvjf compat-wireless-2.6*
```
Then navigate to the compat-wireless folder, so if it saved to your desktop, you would run:
```
cd /home/username/Desktop/compat*
```
Where it says **username** you need to make it your username, remember everything is case sensitive. So once you're in the directory, you can run:
```
make
sudo make install
```
Now if you have another version (older) of compat-wireless conflicting, you can run:
```
make unload
```
Then that will remove the old drivers from the old compat-wireless package. Then if you actually have troubles with the actual new drivers, you can always run:
```
make uninstall
```

So once you have done that, you can finally reboot by running:
```
sudo shutdown -r now
```
Then hopefully once you're back into your desktop the wireless card works perfectly. I'd also like to state when upgrading your kernel, you need to recompile the driver from source anytime you upgrade your kernel. So if you do a kernel upgrade via Synaptic, and you reboot and your wireless isn't working, just try recompiling the driver.

4) **[SIZE="5"]Ndiswrapper problems (loading ath9k module)[/SIZE]**

So I've also seen this problem where people cannot load the ath9k module by running:
```
modprobe ath9k
```
The reason is to my knowledge is of an existing driver causing some sort of conflicts with the blacklist configuration file. So if you run the modprobe command and this error comes up:
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper

```
You can run the following as root:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```
Then try reloading the ath9k module, and it should work to perfection. 

5) **[SIZE="5"]Adding modules to compat-wireless[/SIZE]**

So once you have successfully compiled compat-wireless and you have checked that everything is working correctly, depending on what card you're using you might need to add a module to the modules configuration file:
```
sudo pico /etc/modules
```
Then a text editor should show up, you can use one of your choice (nano, pico, gedit). Then from there you will want to add the driver you are using to the end of the file. So for example if I'm using the ath9k driver so I would add:
```
ath9k
```
Just for another example say I was using the ath5k module, then I would do it very similar just add:
```
ath5k
```
Save the file then exit your text editor, and your card should be up and running. Now if you're not sure what type of Atheros card you have or just a wireless card in general, you can run these commands, and these will tell you more information:
```
lspci
lsusb
lshw -C network
ifconfig
iwconfig
```
Once you know what card you have, you can load the correct **ath** module. Here are some screenshots at the bottom to assist you:

---

### Post by chenxiaolong on 2009-09-22
I just compiled and installed the compat-wireless package because I needed the new b43 driver that has support for the 14e4:4315 wireless card. After I restarted the module didn't load, so I ran sudo modprobe b43 and it says:

```
[sudo] password for chenxiaolong: 
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting pcmcia (/lib/modules/2.6.28-15-generic/kernel/drivers/pcmcia/pcmcia.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/2.6.28-15-generic/updates/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/b43/b43.ko): Invalid module format

```

Do you have any idea why that happens? It compiles and works fine in Fedora, openSUSE, and Sabayon.

---

### Post by Crafty Kisses on 2009-09-23
> **chenxiaolong said:**
> I just compiled and installed the compat-wireless package because I needed the new b43 driver that has support for the 14e4:4315 wireless card. After I restarted the module didn't load, so I ran sudo modprobe b43 and it says:

```
[sudo] password for chenxiaolong: 
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting pcmcia (/lib/modules/2.6.28-15-generic/kernel/drivers/pcmcia/pcmcia.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/2.6.28-15-generic/updates/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/b43/b43.ko): Invalid module format

```

Do you have any idea why that happens? It compiles and works fine in Fedora, openSUSE, and Sabayon.

Well that error usually means the module was built for a different kernel source. I'm guessing you installed a driver previously via Synaptic then compiled the new driver from source, is that correct?

---

### Post by chenxiaolong on 2009-09-23
Actually it was a fresh install with the latest updates. I just downloaded the compat-wireless archive directly from the Linux Wireless page and followed it's instructions.

---

### Post by Crafty Kisses on 2009-09-26
What are the results of the following?
```
depmod -a
```

---

### Post by chenxiaolong on 2009-09-26
There aren't any results or errors.

---

