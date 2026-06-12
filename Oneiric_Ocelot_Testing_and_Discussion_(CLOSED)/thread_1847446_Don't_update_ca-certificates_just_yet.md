---
title: "Don't update ca-certificates just yet"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-09-20
For me that update removed /usr/lib/x86_64-linux-gnu/libnss3.so which caused wireless to not work.

[https://bugs.launchpad.net/ubuntu/+source/ca-certificates/+bug/855171](https://bugs.launchpad.net/ubuntu/+source/ca-certificates/+bug/855171)

---

### Post by paul_in_london on 2011-09-20
> **MacUntu said:**
> For me that update removed /usr/lib/x86_64-linux-gnu/libnss3.so which caused wireless to not work.

[https://bugs.launchpad.net/ubuntu/+source/ca-certificates/+bug/855171](https://bugs.launchpad.net/ubuntu/+source/ca-certificates/+bug/855171)

Thanks - too late though. Had already updated on 64 bit. Luckily I'm not using wireless! :)

---

### Post by MacUntu on 2011-09-20
> **paul_in_london said:**
> Luckily I'm not using wireless! :)

And I had no network cable. :D I just copied the version at /usr/lib/thunderbird-7.0/libnss3.so to /usr/lib/x86_64-linux-gnu/, rebooted, removed it again and reinstalled libnss3. :D

---

### Post by paul_in_london on 2011-09-20
> **MacUntu said:**
> And I had no network cable. :D I just copied the version at /usr/lib/thunderbird-7.0/libnss3.so to /usr/lib/x86_64-linux-gnu/, rebooted, removed it again and reinstalled libnss3. :D

Glad you're back up and running! :)

---

### Post by sammiev on 2011-09-20
Working here on wireless and just updated about 20 min before reading this.

---

### Post by buntu63 on 2011-09-20
> **paul_in_london said:**
>  *Ain't* using wireless! :)

:p

---

### Post by castrojo on 2011-09-20
Release team and the archive admins are aware, until the bad package is removed from the archive please spread the word about not updating.

---

### Post by grahammechanical on 2011-09-20
It did for me as well. And it removed both wireless and ethernet connections. The network utility will not run and there is no network manager icon in the top panel. The usual commands to activate wireless and ethernet do not work either.

Ah well, it is all part of the fun.

update - From the Launchpad bug report I added this line to the etc/network/interfaces file

> iface eth0 inet inet dhcp

And then the command

```
sudo ifup eth0
```

And I am now on-line but still without the network app indicator but at least I can upgrade the fix.

Regards.

---

### Post by alexvy13 on 2011-09-20
wasn't getting internet wired or wirless, had to do a fresh install.

---

### Post by castrojo on 2011-09-20
Fix is being uploaded now. 

(There's no need to reinstall, you can just boot off the livecd in a little bit and chroot in and do an upgrade)

---

### Post by castrojo on 2011-09-20
"sudo apt-get install --reinstall libnss3:i386 libnss3" outta fix it if this has knocked out your wireless, if someone can confirm that that would be great.

---

### Post by flipper T on 2011-09-20
could you detail how to do this ? currently running off live cd because no wireless or ethernet on 11.10 install

---

### Post by castrojo on 2011-09-20
Ok, so boot off the CD, go into recovery mode, and reinstall the package from the local cache:

sudo dpkg -i /var/cache/apt/archives/libnss3_3.12.9+ckbi-1.82-0ubuntu5_amd64.deb

if you're on amd64

sudo dpkg -i /var/cache/apt/archives/libnss3_3.12.9+ckbi-1.82-0ubuntu5_i386.deb

for i386

---

### Post by Quackers on 2011-09-20
From live cd desktop connect to internet then open a terminal and run the following ```
sudo mkdir /mnt/temp
``` which may or may not report that it already exists.
Then ```
sudo mount /dev/sdXY /mnt/temp
``` change to include your Ubuntu root partition instead of /dev/sdXY
Then ```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
``` Then ```
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
```
Then ```
sudo chroot /mnt/temp
``` At this point the terminal prompt should change to root@ubuntu
You can then ```
apt-get update
apt-get upgrade
``` or at least when the updated packages have arrived.
When finished run ```
exit
```

Then run ```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
``` to unmount what you mounted earlier.

---

### Post by flipper T on 2011-09-20
sorry to be dense but how do i find out what "dev/sdXY" is ?

i have a standard installation ie home not separate partition

also how do i go into recovery mode from live cd ?

---

### Post by Quackers on 2011-09-20
One way is ```
sudo fdisk -l
``` which will give details of your current partition layout. You'll need to work out which is your root partition (you may only have one partition for Oneiric - others will have a root partition and a home partition).
Or via gparted.

You should also see castrojo's last 2 posts as well :-)

---

### Post by grahammechanical on 2011-09-20
It is my guess that "dev/sdXY" represents the partition that 11.10 is installed in. For me that would be sda7 so I would have to type dev/sda7, is my guess. Remember, in Linux things like hard disks and partitions are devices as are lots of other things.

Regards.

---

### Post by flipper T on 2011-09-20
i get:

/dev/sda1   *           1       18936   152096768   83  Linux
/dev/sda2           18936       19458     4191233    5  Extended
/dev/sda5           18936       19458     4191232   82  Linux swap / Solaris

so is it sda1 ?

---

### Post by Quackers on 2011-09-20
castrojo, I ran the ca-certificates updates earlier and when I try to re-install libnss3 it says I currently have the latest version installed.
64 bit system here.

---

### Post by Quackers on 2011-09-20
/dev/sda1 then, yes.

---

### Post by alexvy13 on 2011-09-20
Haha i wish yall had posted that tutorial about 45 minutes ago, I already reinstalled lol

But it's ok, I've been meaning to. I've learned a lot these past couple of weeks and wanted to restart :)

but on a side note, none of my startup application are showing up when i click on startup applications. I saw somewhere a command on how to get it to show back when I first tried out oneiric about a month ago but now I can't find the command, any help?

---

### Post by flipper T on 2011-09-20
following your instructions quackers but get

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
chroot: cannot run command `/bin/bash': Exec format error
```

---

### Post by Quackers on 2011-09-20
alexvy13 have a look in this thread
[http://ubuntuforums.org/showthread.php?t=1795650&highlight=startup+applications](http://ubuntuforums.org/showthread.php?t=1795650&highlight=startup+applications)

---

### Post by Quackers on 2011-09-20
flipper T, is your live cd the same architecture (32 bit/64bit) as your installation?

---

### Post by tista on 2011-09-20
Hi guys,

Thanks for your reports!! :)

Just now I've recovored it by:

* enabling wired connection manually.
* reinstalled libnss3

on my Oneiric, in that time, gnome-shell had been broken in all stuff of shell, even mouse pointer... :/
but unity-2d and/or gnome-fallback may be OK to login with broken ca-certificates!

cheers.

---

### Post by flipper T on 2011-09-20
sorry, no idea

live cd is a old 10.04 lts, how can i tell if 64 bit ?

install is 11.10 64 bit

---

### Post by Quackers on 2011-09-20
It would be advisable to use an 11.10 live cd/usb and it must be 64 bit if your installation is 64 bit. Didn't you install from one?

---

### Post by flipper T on 2011-09-20
mad search now taking place :)

will leave until morning, i think

thx for all help so far

---

### Post by Quackers on 2011-09-20
No problem :-)
Before you finish, run the last command to unmount everything (the for i xxxxx one)

---

### Post by Cenotaph on 2011-09-20
Chrome stopped working as well. Luckily, I'm handy with wpa_supplicant so I can still connect to wifi

---

### Post by flipper T on 2011-09-20
who needs sleep anyway ?

quackers, found 64bit cd, followed instructions, offered 2 upgrades (certificates i think), upgraded, followed rest of instructions, no problem.

booted back into my 11.10 installation, no wireless, no ethernet, no change,

have the corrected updates been released yet or am i doing something else wrong ?

---

### Post by Quackers on 2011-09-20
I'm just finding the same :-(
I think it may be that libnss3 file that MacUntu mentioned in post 1.
I'm going to copy it across from a second install I've got. 
Have you seen the earlier posts by castrojo on page 2 I think? Try those.

---

### Post by Quackers on 2011-09-20
Yes, I'm now back in my borked gnome-shell installation and all is well again :-)
Try those commands given by castrojo in posts 11 and 13 - changing for your architecture if necessary. See if those help.

---

### Post by castrojo on 2011-09-20
The packages have been published and you can grab them both from here (though I think you only need ca-certificates, but it doesn't hurt to install both):

[https://launchpad.net/ubuntu/oneiric/+source/ca-certificates/20110502+nmu1ubuntu3](https://launchpad.net/ubuntu/oneiric/+source/ca-certificates/20110502+nmu1ubuntu3)

[https://launchpad.net/ubuntu/oneiric/+source/ca-certificates-java/20110912ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/ca-certificates-java/20110912ubuntu2)

Here are the direct deb links:

[https://launchpad.net/ubuntu/+source/ca-certificates/20110502+nmu1ubuntu3/+build/2797030/+files/ca-certificates_20110502%2Bnmu1ubuntu3_all.deb](https://launchpad.net/ubuntu/+source/ca-certificates/20110502+nmu1ubuntu3/+build/2797030/+files/ca-certificates_20110502%2Bnmu1ubuntu3_all.deb)

[https://launchpad.net/ubuntu/+source/ca-certificates-java/20110912ubuntu2/+build/2797008/+files/ca-certificates-java_20110912ubuntu2_all.deb](https://launchpad.net/ubuntu/+source/ca-certificates-java/20110912ubuntu2/+build/2797008/+files/ca-certificates-java_20110912ubuntu2_all.deb)

---

### Post by Quackers on 2011-09-20
What about the libnss3.so file that seems to have disappeared from /usr/lib/x86_64-linux-gnu folder?
That .so file was not recovered by running the update and it seems to be that file that borked both gnome-shell and wireless.
Anything on that please?
I've just copied it across from a "backup" installation :-)

EDIT  Or maybe that was caused by the ricotz update?

---

### Post by Quackers on 2011-09-20
flipper T, also have another look at post 3. That's effectively what I have done.

---

### Post by alexvy13 on 2011-09-21
are these updates in the repositories yet? is it safe to update?

---

### Post by Quackers on 2011-09-21
The ca-certificate ones are - or were for me.

---

### Post by tista on 2011-09-21
> **alexvy13 said:**
> are these updates in the repositories yet? is it safe to update?

@alexvy13,

I've updated, and works well.. ;)

regards.

---

### Post by flipper T on 2011-09-21
thx quackers et al

replaced file & now back online in good ol' 11.10 beta

must go to bed

unless you have separate time zone to rest of uk, so should you :)

---

### Post by Quackers on 2011-09-21
That's true but I can sleep during the day :-) 
And will do!

---

### Post by oldos2er on 2011-09-21
> **MacUntu said:**
> And I had no network cable. :D I just copied the version at /usr/lib/thunderbird-7.0/libnss3.so to /usr/lib/x86_64-linux-gnu/, rebooted, removed it again and reinstalled libnss3. :D

This solution worked for me. My connection is wired, though.

---

### Post by flipper T on 2011-09-21
for clarification:

This solution worked for me. My connection is wireless.

---

### Post by cariboo on 2011-09-21
Unsticking this thread, as the issue has been resolved.

---

### Post by Izobalax on 2011-09-21
Hello. 

I am also suffering from having no internet due to this upgrade. I have a wired connection. 

I have attempted to install the debs provided by Jorge Castro by booting into my Windows install, copying the debs onto a USB stick, booting back into my Ubuntu install and then installing the debs. 

However, it still fails as it cannot find libnss3.so

Going from the LP bug report, I attempted the command:

```
sudo apt-get install --reinstall libnss3 libnss3:i386
```

But got this in response:

```
izo@kether-u:~$ sudo apt-get install --reinstall libnss3:i386

[sudo] password for izo: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.

Need to get 1,258 kB of archives.

After this operation, 0 B of additional disk space will be used.

Err http://im.archive.ubuntu.com/ubuntu/ oneiric/main libnss3 i386 3.12.9+ckbi-1.82-0ubuntu5
  
Could not resolve 'im.archive.ubuntu.com'

Failed to fetch http://im.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.12.9+ckbi-1.82-0ubuntu5_i386.deb  
Could not resolve 'im.archive.ubuntu.com'
E: 
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Obviously, no internet means no redownloading of any packages. A catch-22. 

Errr... help?

/izo\

---

### Post by cariboo on 2011-09-21
You can't use apt-get to install a package that you have already downloaded. You need to use the following command:

```
sudo dpkg -i libnss3_3.12.9+ckbi-1.82-0ubuntu5_amd64.deb 
```

of course you have to be in the same directory that the package is located in.

You can also double-click the package, and the Software Center will open and install it.

---

### Post by Izobalax on 2011-09-21
> **cariboo907 said:**
> You can't use apt-get to install a package that you have already downloaded. You need to use the following command:

```
sudo dpkg -i libnss3_3.12.9+ckbi-1.82-0ubuntu5_amd64.deb 
```

of course you have to be in the same directory that the package is located in.

You can also double-click the package, and the Software Center will open and install it.


Yes, but surely, with no working internet, I can't download this libnss package in the first place to install it, can I?

/izo\

---

### Post by flipper T on 2011-09-21
if you have a copy in the thunderbird folder (see early postings) you can gksudo nautilus and copy and paste it to the required folder. no internet needed. reboot then should be ok

---

### Post by Izobalax on 2011-09-21
> **flipper T said:**
> if you have a copy in the thunderbird folder (see early postings) you can gksudo nautilus and copy and paste it to the required folder. no internet needed. reboot then should be ok


I found libnss3.so in the /usr/lib/Firefox-7.0 folder, rather than Thunderbird, and copied it to my /usr/lib/i386-GNU-Linux

Still doesn't work. 

/izo\

---

### Post by Izobalax on 2011-09-21
Fixed now! Via Georgi's solution on my Google+ post here -> [https://plus.google.com/112546833633391090642/posts/QV6P3SSAwMg](https://plus.google.com/112546833633391090642/posts/QV6P3SSAwMg)

Thanks guys for trying to help me out. =]

/izo\

---

### Post by Harry33 on 2011-09-21
> **Izobalax said:**
> I found libnss3.so in the /usr/lib/Firefox-7.0 folder, rather than Thunderbird, and copied it to my /usr/lib/i386-GNU-Linux
Still doesn't work. 
/izo\

So, **if** you have a 32-bit setup,
copy the file libnss3.so into this folder
/usr/lib/i386-linux-gnu

But, if you have a 64-bit setup
copy the file libnss3.so into this folder
/usr/lib/x86_64-linux-gnu

BTW, there is no /usr/lib/i386-GNU-linux folder.

---

### Post by Izobalax on 2011-09-21
> **Harry33 said:**
> So, **if** you have a 32-bit setup,
copy the file libnss3.so into this folder
/usr/lib/i386-linux-gnu

But, if you have a 64-bit setup
copy the file libnss3.so into this folder
/usr/lib/x86_64-linux-gnu

BTW, there is no /usr/lib/i386-GNU-linux folder.


Yes, the first is correct for me, sorry. 

/izo\

---

### Post by Locke_99GS on 2011-09-21
I disabled NetworkManager, then used dhclient to start an eth0 connection, and updated the machine (which brought in the fix, apparently) then restarted to get regular (as regular as nm is, anyways) networking going.

There are easier ways - but I don't think about the easy ways. :)

---

