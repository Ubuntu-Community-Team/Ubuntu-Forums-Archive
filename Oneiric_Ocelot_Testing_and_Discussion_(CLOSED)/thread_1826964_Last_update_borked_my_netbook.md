---
title: "Last update borked my netbook"
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 1/0 on 2011-08-17
I updated yesterday and now I cannot start x, nor get the network started... 

Booting stops at checking battery status. Alt + F1 gets me to shell but wired and wireless internet is down. Nothing seems to have installed improperly. Also, it won't power down properly when shut down.

Ideas on what to do?

---

### Post by dino99 on 2011-08-17
yeah shutdown is irritating: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

from recovery mode, try:

sudo dpkg-reconfigure -phigh -a
( wait it end by itself, can be long, dont stop it)

---

### Post by rbrick49 on 2011-08-17
> **1/0 said:**
> I updated yesterday and now I cannot start x, nor get the network started... 

Booting stops at checking battery status. Alt + F1 gets me to shell but wired and wireless internet is down. Nothing seems to have installed improperly. Also, it won't power down properly when shut down.

Ideas on what to do?see if your bootloader is installed I lost mine this morning also. mine stopped at checking battery status also. I installed the boot loader all was ok again

---

### Post by dino99 on 2011-08-17
> **rbrick49 said:**
> see if your bootloader is installed I lost mine this morning also. mine stopped at checking battery status also. I installed the boot loader all was ok again

sudo initramfs -u -k should do the trick

---

### Post by 1/0 on 2011-08-17
> **dino99 said:**
> from recovery mode, try:

sudo dpkg-reconfigure -phigh -a

That seems to have taken care of the power down issue. Thanks!

> **rbrick49 said:**
> see if your bootloader is installed I lost mine this morning also. mine stopped at checking battery status also. I installed the boot loader all was ok again

Well lightdm is installed, just as light-dm-greeter, if that's what you meant. Or is it grub?

> **dino99 said:**
> sudo initramfs -u -k should do the trick

Can't find initramfs... Initramfs-tools is installed though.

I'm a bit puzzled as what to do, especially since the network is down... (Yes I can connect with other devices)

---

### Post by 1/0 on 2011-08-17
> **1/0 said:**
> That seems to have taken care of the power down issue. Thanks!

Oops. Seems I was a bit too fast on cheering. It seems to power down from rescue mode but not normal mode...

---

### Post by dino99 on 2011-08-17
my bad,

sudo update-initramfs -u -k

---

### Post by rbrick49 on 2011-08-17
> **1/0 said:**
> That seems to have taken care of the power down issue. Thanks!



Well lightdm is installed, just as light-dm-greeter, if that's what you meant. Or is it grub?



Can't find initramfs... Initramfs-tools is installed though.

I'm a bit puzzled as what to do, especially since the network is down... (Yes I can connect with other devices)
yes I meant grub it went out the window somehow I reintalled it everything was ok then

---

### Post by jnguyen on 2011-08-17
Hi All,

I have network issue this morning too and restarted laptop didn't help, somehow I have one extra wired network (Auto eth0 & Auto eth2). So I removed Auto eth2 and disconnect Auto eth0 and reconnect than problem solved. This approach worked for me, hope it will help someone else too.
jvn

---

### Post by 1/0 on 2011-08-17
> **dino99 said:**
> my bad,

sudo update-initramfs -u -k

That worked but sadly no change...

> **rbrick49 said:**
> yes I meant grub it went out the window somehow I reintalled it everything was ok then

Well, grub is there when I boot but when I do *sudo apt-get install grub2*, it says it want's to install grub2. The thing is, it can't get the files needed since the network is down... Should I get the file manually?

> **jnguyen said:**
> Hi All,

I have network issue this morning too and restarted laptop didn't help, somehow I have one extra wired network (Auto eth0 & Auto eth2). So I removed Auto eth2 and disconnect Auto eth0 and reconnect than problem solved. This approach worked for me, hope it will help someone else too.
jvn

I don't seem to have more networks installed than before but thanks anyway!

---

### Post by zekopeko on 2011-08-17
I'm also suffering exactly the same problems. If only I could get the network working I could update.

---

### Post by 1/0 on 2011-08-17
> **zekopeko said:**
> I'm also suffering exactly the same problems. If only I could get the network working I could update.

Good to know I'm not alone...

---

### Post by frup on 2011-08-17
You can get a temporary wired connection set up with:

sudo ifconfig eth0 192.168.2.15 netmask 255.255.255.0
sudo route add default gw 192.168.2.1 eth0

just change the ips of the gateway and your machine to match your routers set up.

That with an apt-get solved a very similar problem [http://ubuntuforums.org/showthread.php?t=1826938](http://ubuntuforums.org/showthread.php?t=1826938) for me last night.

---

### Post by 1/0 on 2011-08-18
> **frup said:**
> You can get a temporary wired connection set up with:

sudo ifconfig eth0 192.168.2.15 netmask 255.255.255.0
sudo route add default gw 192.168.2.1 eth0

just change the ips of the gateway and your machine to match your routers set up.

That with an apt-get solved a very similar problem [http://ubuntuforums.org/showthread.php?t=1826938](http://ubuntuforums.org/showthread.php?t=1826938) for me last night.

Sadly I'm not getting a connection up... I adjusted the ip number to 192.168.1.*, since the router is set up that way. Eth0 shows up now though. 

I checked grub2 but the package server says it's a dummy package and has no file... I wonder which file that is messing up here.

---

### Post by dino99 on 2011-08-18
maybe reinstall ubuntu-desktop

---

### Post by 1/0 on 2011-08-18
Dough!! It seems resov.conf was missing:

```
nameserver 192.168.1.1
```

Simple reason but why? It worked fine before the update and I ain't been touching /etc...

A few updates later and the netbook starts alright but now I have no touch pad (or external mouse)...

Also the screen setting is a bit off.

---

### Post by rbrick49 on 2011-08-18
> **1/0 said:**
> Dough!! It seems resov.conf was missing:

```
nameserver 192.168.1.1
```

Simple reason but why? It worked fine before the update and I ain't been touching /etc...

A few updates later and the netbook starts alright but now I have no touch pad (or external mouse)...

Also the screen setting is a bit off.geez I thought I got a bad dose of corrupt yours is worse you can reinstall boot loader from live cd if you have to heres the code 
sudo mount /dev/sdxX /mnt
sudo mount -o bind /dev /mnt/dev 
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
/dev/sdxX is the partition you installed ubuntu on
at root promt grub-install when finished update-grub then reboot 
you can do this from a terminal on a live cd
thanks to caribou for this code

---

### Post by 1/0 on 2011-08-18
> **rbrick49 said:**
> geez I thought I got a bad dose of corrupt yours is worse you can reinstall boot loader from live cd if you have to heres the code 
sudo mount /dev/sdxX /mnt
sudo mount -o bind /dev /mnt/dev 
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
/dev/sdxX is the partition you installed ubuntu on
at root promt grub-install when finished update-grub then reboot 
you can do this from a terminal on a live cd
thanks to caribou for this code

Well the netbook boots fine into 2.6.38-2 and grub seems installed and updates fine. The thing is, when I get to the lightdm login window, the resolution is somewhat wrong and the touch pad is not working. I login and the problems persist. So I can only use the keyboard.

Btw anyone know how to right click anything using the keyboard?


[edit}]Oh; another thing. When I restart lightdm, it's stuck again at checking battery status. If I reboot, it boots but with no touch pad and poor resolution.

Another thing is that there's no sound.[/edit]

---

### Post by m.rankovic on 2011-08-18
> **1/0 said:**
> ...
Btw anyone know how to right click anything using the keyboard?
...


Try this button if you have it on your keyboard.

---

### Post by 1/0 on 2011-08-18
> **m.rankovic said:**
> Try this button if you have it on your keyboard.

Thanks. Anyone know how to access the networks in the bar via keyboard? I can start the network connections but I guess it's only possible to connect (wireless) via the bar.

---

### Post by 1/0 on 2011-08-18
Network went down again now. I get the following:

```
# ifconfig eth0 192.168.1.15 netmask 255.255.255.0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device

```

Also, resolv.conf is yet again missing the nameserver line.

---

### Post by zekopeko on 2011-08-18
> **1/0 said:**
> Network went down again now. I get the following:

```
# ifconfig eth0 192.168.1.15 netmask 255.255.255.0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device

```

Also, resolv.conf is yet again missing the nameserver line.

The ifconfig and route commands fixed it for me but I have yet to be bitten by this problem.

---

### Post by xx58 on 2011-08-18
:rolleyes: If everything works, then make [COLOR=Red]Clonezilla[/COLOR] backup and if something will go wrong, then restore will take only some 7 minutes. Make always backup !!!

---

### Post by 1/0 on 2011-08-18
> **xx58 said:**
> :rolleyes: If everything works, then make [COLOR=Red]Clonezilla[/COLOR] backup and if something will go wrong, then restore will take only some 7 minutes. Make always backup !!!

Yeah, I should do that from now on. Sadly it's always been something not working since that update I did some two days ago. 

Now, no network, no mouse and bad resolution settings. There's probably more I haven't noticed. The question is, when is it too much trouble resolving the issues compared to reinstalling. I really hate doing the Windows way of "solving" problems, i.e. reinstallation.

---

### Post by cariboo on 2011-08-18
You really shouldn't be using Oneiric as your main Installation, it is recommended that you also have a working stable install, just in case things like this happen. Making a backup image of your install doesn't do a lot of good, as things are changing so fast. After being fully up-to-date yesterday, there were another 112 updates waiting for me this morning, and probably more to come today.

---

### Post by 1/0 on 2011-08-19
> **cariboo907 said:**
> You really shouldn't be using Oneiric as your main Installation, it is recommended that you also have a working stable install, just in case things like this happen. Making a backup image of your install doesn't do a lot of good, as things are changing so fast. After being fully up-to-date yesterday, there were another 112 updates waiting for me this morning, and probably more to come today.

Well I've got Oneiric on one of my computers but I guess using Oneiric was a bad idea as it only messes things up. I guess I'll install Natty then.

---

