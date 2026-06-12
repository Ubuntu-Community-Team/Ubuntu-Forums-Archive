---
title: "Ubuntu (11.10) and disk encryption"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Jeinhor on 2011-10-04
Hi there,

Some questions on LVM and encrypted volumes, and if my current setup is a good one:
[LIST=1]
[*]Do I have to use LVM with encrypted volumes?
[*]Will it be messy to upgrade to newer versions of Ubuntu when having encrypted file systems?
[*]Any performance difference?
[/LIST]

This is how I configured it:
[LIST=1]
[*]Boot using the alternate install CD
[*]Chose "Manual partitioning"
[*]Created the partitions as I normally would, one for /, one swap and one /data
[*]Chose "Configure encrypted volumes"
[*]"Create encrypted volumes"
[*]Ticked all partitions except /boot
[*]Chose a passphrase for all three partitions
[*]Installed the rest as I normally would
[/LIST]

A few things strike me as strange:
[LIST=1]
[*]Shouldn't it be possible to create an encrypted volume using the whole drive first, and add the partitions later on, all on the same encrypted drive?
[*]Should I really enter one passphrase for each encrypted partition?
[/LIST]

Any suggestions, tips, ideas and answers are welcome!

Thanks in advance!

EDIT: And just as I wrote this the installation failed with "Installation step failed", "The failing step is: Select and install software". I'm not sure if it has anything to do with my encrypted filesystem setup, might also be a problem with Ubuntu Oneiric Beta 2. Anyone seen something similar?

---

### Post by Jeinhor on 2011-10-04
I think I did two things wrong:

[LIST=1]
[*]I got hold of a alternate install CD with MAC-support, which might not work good on a PC (?, atleast not for me...))
[*]I did the whole encryption thing wrong... this is how you should do it: [http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)
[/LIST]

---

### Post by Jeinhor on 2011-10-05
With the new .ISO (ubuntu-11.10-beta2-alternate-amd64.iso) and the correct way of doing encryption from the blog post in my last post, I still get a "Installation step failed", "The failing step is: Select and install software".

Anyone else have this problem with the alternate install CD and Ubuntu 11.10 Beta 2?

EDIT: Monologue FTW :)

---

### Post by Elfy on 2011-10-05
Thread moved to Ubuntu +1 (Oneiric Ocelot). Please used Development forums for dev versions

---

### Post by meznaric on 2011-10-05
I have the same issue. After the error came up I continued with the GRUB install. Boot fails. However, the recovery console is accessible. Tried apt-get install ubuntu-desktop and ended up with "installation impossible" because of the dependencies. It all traces back to compiz-main-plugins package having no installation candidates. I will now try to manually download this package from the website, put it onto a usb stick and install it manually before trying the apt-get install ubuntu-desktop again.

---

### Post by HalfEmptyHero on 2011-10-05
I haven't been able to use the Alternate Install cd for the past few releases, not sure why. Instead, I have been doing it manually from the normal desktop cd. There's a good tutorial [here]("http://www.infosecramblings.com/backtrack/backtrack-5-bootable-usb-thumb-drive-with-full-disk-encryption/") for it. It's meant for backtrack 5, which is based off of Ubuntu, and it is meant for encrypting a live usb so there may be a thing or two you need to tweak, such as adding an encrypted ram partition. To do this, at the part where it says **lvcreate -n root -l 100%FREE vg** change it to **lvcreate -n root -L 10000M** **vg** where 10000 is the size you want your root partition. This way you can do **lvcreate -n swap -L 4000M** **vg** and then **lvcreate -n home -l 100%FREE vg** if you want a separate home partition. In the tutorial is says you need to create a 500MB boot partition, but I've always gotten away with using a 200MB one without any problems. For the swap when it comes to formatting the partition you use mkswap instead of mkfs.ext4.

If you decide to try this, let me know if you need any help. You can also check the man pages for lvcreate, cryptsetup, etc.

---

### Post by meznaric on 2011-10-05
The attempt with adding the package manually failed. It created a lot of conflicts which failed to resolve because I am installing from a usb stick. If you have an actual CD though it may well work. It's worth a try. I am going to burn myself a CD and try that as well.

---

### Post by Jeinhor on 2011-10-05
> **forestpiskie said:**
> Thread moved to Ubuntu +1 (Oneiric Ocelot). Please used Development forums for dev versions

Woops. Thanks for moving it for me.

> **meznaric said:**
> I have the same issue. After the error came up I continued with the GRUB install. Boot fails. However, the recovery console is accessible. Tried apt-get install ubuntu-desktop and ended up with "installation impossible" because of the dependencies. It all traces back to compiz-main-plugins package having no installation candidates. I will now try to manually download this package from the website, put it onto a usb stick and install it manually before trying the apt-get install ubuntu-desktop again.

I also booted the recovery console and tried to apt-get, ended up where you did. How did you find it traced down to compiz-main-plugins? Also, why can't you (we) download the missing through the recovery console?

> **HalfEmptyHero said:**
> I haven't been able to use the Alternate Install cd for the past few releases, not sure why. Instead, I have been doing it manually from the normal desktop cd. There's a good tutorial [here]("http://www.infosecramblings.com/backtrack/backtrack-5-bootable-usb-thumb-drive-with-full-disk-encryption/") for it. It's meant for backtrack 5, which is based off of Ubuntu, and it is meant for encrypting a live usb so there may be a thing or two you need to tweak, such as adding an encrypted ram partition. To do this, at the part where it says **lvcreate -n root -l 100%FREE vg** change it to **lvcreate -n root -L 10000M** **vg** where 10000 is the size you want your root partition. This way you can do **lvcreate -n swap -L 4000M** **vg** and then **lvcreate -n home -l 100%FREE vg** if you want a separate home partition. In the tutorial is says you need to create a 500MB boot partition, but I've always gotten away with using a 200MB one without any problems. For the swap when it comes to formatting the partition you use mkswap instead of mkfs.ext4.

If you decide to try this, let me know if you need any help. You can also check the man pages for lvcreate, cryptsetup, etc.

I might try this, I'll post here with info if I do. Thanks for sharing!

> **meznaric said:**
> The attempt with adding the package manually failed. It created a lot of conflicts which failed to resolve because I am installing from a usb stick. If you have an actual CD though it may well work. It's worth a try. I am going to burn myself a CD and try that as well.

Why would it make a difference installing from a CD? I do not have that option (no CD-drive in this small HTPC-box).



Do anyone know if it would be possible to install an earlier alpha and then do apt-get (dist?)upgrade to the newest beta from there?

Also, does this only affect installation performed on encrypted drives, or why isn't the forum flooded with this problem? :P

---

### Post by nrundy on 2011-10-05
Isn't the default LIVE CD supposed to have the ability to do full-disk-encryption now with 11.10? 

[http://brainstorm.ubuntu.com/idea/24712/](http://brainstorm.ubuntu.com/idea/24712/)

Is the alternate-cd still required for full-disk encryption?

---

### Post by Jeinhor on 2011-10-06
I think I tried with the live CD. Or is the live CD different from the desktop CD? They both start a live Ubuntu, right? Perhaps anyone else can shed some light?

I figured out a way of installing it with encryption, but it's not very neat: install with the alternate CD from Ubuntu 11.04 (do NOT tick ubuntu-desktop when asked, otherwise you'll get the same failure as with 11.10). It will install successfully, but I had problems booting so I went into recovery mode. There it booted "normally", so I chose "Continue with normal boot". I then performed an upgrade to latest 11.10 beta 2, and now it boots normally (I have some graphics problems though, but I think it's unrelated and will post about it in another thread). I'm not sure if the upgrade to beta 2 installed ubuntu-desktop for me, but I guess that's a simple apt-get after (or before?) the upgrade to beta 2. 

What do you think, this method any good?

EDIT: Nope, ubuntu-desktop were not installed when upgrading to 11.10 beta 2. I installed it manually now (after upgrading to beta 2). I'll see tonight if that solves my graphic related issues, I only have ssh access right now.

EDIT2: This method worked. However, I messed it up somehow when I tried to install post-release updates version of the proprietary nVidia graphics drivers, so now I'm back to unencrypted. After the installation of the graphic drivers, I got an error at boot (something about crypt setup), and even though I entered the correct passphrase I couldn't boot.

---

