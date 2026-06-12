---
title: "HOW-TO: setup IPW3945(coreduo wlan) on custom kernel"
date: 2006-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by iluva on 2006-11-07
as for now, the ip3945-modules is in the linux-restricted-modules pack. so without any self made kernel, you only have to install
```
sudo apt-get linux-restricted-modules-generic
```
which you can also find on the ubuntu cdrom, so u can install your ipw3945 wireless also whithout any internet connection.
let's get to the point ^^
as soon as you compile your own kernel, I did that because i wanted to have the suspend2 patch and raiserfs4 patch included, u don't have any access to linux-restricted-modules because they are compiled against the 
stock-ubuntu-kernel.
as for reference, i took the emission-project kernel, this is a ebuild gentoo kernel project, which works like a charm on my ubuntusystem.
link-to emission kernel project page: [emission]("http://evolution-mission.org/viewforum.php?f=8&sid=7e0b17f801466cd0c548cd3c887e1532")
or you take a vanilla-kernel from [kernel.org]("http://www.kernel.org") and compile this one, i sugest you take a 2.8.18 branch and not the 2.6.19rc's.

1 part, kernel download, parts with a "#" you dont type
```

cd /usr/src
sudo -s #this gives ALL your next commands a root access
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.2.tar.bz2
tar xfzv linux-2.6.18.2.tar.bz2
ln -s  linux-2.6.18.2 linux
cd linux
```

if you want to use the emission-kernels you have to download the 2.6.18(no subversions) kernel.
next step, kernel setup and compiling
```

cp /boot/config-2.6.17-10-generic .config
#the above config file name can change when there will be future kernel apt-get updates
make menuconfig

```
there will be a new frame where you can configure and customize your kernel, if you do a lot of experiments there, the kernel will most probably not boot :D enjoy trying ^^
but assure that some options are set-up as they should be. with the space-key you can change options, (*)=means directly build into kernel, (M) means build as a module and () means not set up at all.
1. go into ->Networking and assure you have everything with "IEEE 80211" set as a module [M]
then go into device drivers -> network device support -> wireless LAN (non -harmradio) and assure that the first one (Wireless Lan Drivers(non-harmradio) and Extensions)is compiled into the kernel [*] and (as for the 2.6.19 kernel) there isn't anything compiled [*]nor[M] with the ipw3945 tag.
then exit the menuconfig and save the config file
3.step is compile the kernel:
```

make
# this will take a long time, depending your machine. but surely take some coffee and go see the sun :D
make modules_install
make install
```

uuuh, kernel is in your bootdirectory and linked with a file called vmlinuz. next step is to make the initrd.img
```

apt-get install initrd-tools
cd /boot
mkinitrd -o initrd.img-2.6.18.2 2.6.18.2

```
#after that you have to edit the grub or lilo config, standard in ubuntu is grub, so we edit the grub config to point on the new kernel
```

vim ./boot/menu.lst  #you can also use nano here, or gedit
#now go under the first entry:
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/sda5 ro
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

#and paste the following section
title           Ubuntu, kernel 2.6.18.2-TEST
root            (hd0,2) #here refere to your entry in the above entry in your menu.lst file
kernel          /vmlinuz root=/dev/sda5 ro #also here refer to your old config, it'll be something like root=/dev/hda1 or so :D
initrd          /initrd.img-2.6.18.2 # also here, refere to the name you have in your initrd.img-VERSION
quiet
savedefault
boot

```

next step is to download everything you need for your ipw3945 driver. you'll need the ieee80211 modules, the ipw3945 driver, the daemon and the firmware file. there are a lot of more recent versions of everything out there, but they don't work together well. i could bring it to work, but just with modifications of the headerfiles and the makefiles, but the following versions work quit good :D so we take those ^^
```

mkdir /usr/src/programs/ipw3945-net -p
cd /usr/src/programs/ipw3945-net
wget http://heanet.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.1.13.tgz
wget  http://superb-west.dl.sourceforge.net/sourceforge/ipw3945/ipw3945-1.0.3.tgz
wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.13.tgz
wget http://bughost.org/ipw3945/daemon/ipw3945d-1.7.18.tgz

```
right now you should reboot into your new kernel. and follow the last steps
```

/usr/src/programs/ipw3945-net
tar xfzv ieee80211-1.1.13.tgz
tar xfz ipw3945-1.0.3
tar xfzv ipw3945-ucode-1.13.tgz
tar xfzv ipw3945d-1.7.18.tgz
cd ieee80211-1.1.13
make
make install
cd ../ipw3945-1.0.3
make
cd ..
cp ./ipw3945-ucode-1.13/ipw3945.ucode /lib/firmware/
#if you have a 32-bit kernel do:
cp ./ipw3945d-1.7.18/x86/ipw3945d /sbin
#if you have a 64-bit kernel do:
cp ./ipw3945d-1.7.18/x86_64/ipw3945d /sbin

```
ok and right now, we want that it starts the daemon on every boot
make a file called ipw3945 in your /etc/modprobe.d/ directory and:
```

touch /etc/modprobe.d/ipw3945
vim /etc/modprobe.d/ipw3945
#here insert those two lines
install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; \
        /sbin/ipw3945d --quiet
remove  ipw3945 /sbin/ipw3945d --kill ; \
        /sbin/modprobe -r --ignore-remove ipw3945
```

i hope, that it works for you :D
cheers, iluva

---

### Post by pakoto on 2006-11-21
This not work for me. I get ERROR: opening /sys/bus/pci/drivers/ipw3945: No such file or directory.

executing "load" command. 

Kernel, ieee an ipw3945 compiled without problems(?)

---

### Post by DarkAngel88 on 2006-11-25
> **pakoto said:**
> This not work for me. I get ERROR: opening /sys/bus/pci/drivers/ipw3945: No such file or directory.

executing "load" command. 

Kernel, ieee an ipw3945 compiled without problems(?)

Same thing here...

Anyone else ?

---

