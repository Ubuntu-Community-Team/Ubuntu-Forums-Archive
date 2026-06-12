---
title: "lubuntu on USB-Stick"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by cheatos on 2012-01-28
Hi,

I have installed lubuntu on a 4GB USB-Stick and it works really fine, although I just have 1.1GB left, still it's worth it, as I use this stick really just to get work done.

What is concerning me is the fact, that I have used the Stick a few times on my laptop now, but when I rebooted to Windows what is on the HDD of the laptop my Outlook.pst data was missing. Fortunately I had an actual version on my desktop, but this really scared me, because when I can accidently delete my .pst-data, maybe I can also corrupt my entire Windows system.
(I didn't remove the .pst data manually by entering the Windows filesystem with pcman or so, it was just gone after a reboot)

So, can this really happen or was it just me being stupid and having forgotten something?

Thanks fopr any help

---

### Post by 2F4U on 2012-01-28
I would consider it highly unlikely that Ubuntu mounted your Windows partition and deleted your Outlook data automatically. Then why just Outlook and not other data? It is, however, true, that you can loose data if you are uncaring. Linux is able to read and write ntfs partitions and can therefore do harmful things. BUT, this doesn't happen automatically, its almost always the user who is responsible for any damage.

---

### Post by WasMeHere on 2012-01-28
Hi cheatos,

I agree with ***2F4U*** that it is very unlikely, that the system itself would erase files on partition, that belongs to another OS, that is not used.

Have you checked that your hard disk drive is good, that there are no bad sectors (with a bad magnetic layer)? If it is fairly new, you can check with the S.M.A.R.T. information using the disk analyzing tool, ***palimpsest***

Another possible cause of such problems is if there has been a bad shutdown event, when the drive caching did not have time to write back to the disk before it stopped (for example a power failure, or that the system was locked by some infinite loop).

And after all, everybody makes mistakes, and sometimes we do not even notice it. So it is a good habit to backup the data at regular intervals.

---

### Post by cheatos on 2012-01-28
Thank you very much for your quick responses.
I was also thinking, that it is very unlikely, that ubuntu will delete random files, but I couldn't find anything I might have done wrong, wouldit be safer to add another user to my lubuntu install on the usb-stick, which then won't be able to mount the ntfs-partition (if this is possible) or would it already be enough to add a user without root privileges, as atm I'm using the usual admin user on the USB-Stick.

---

### Post by WasMeHere on 2012-01-28
Why are you running Lubuntu live from a stick instead of installing Lubuntu?

---

### Post by cheatos on 2012-01-28
Because I want to be able to carry it with me, without having my laptop with me, i.e. when I'm staying with my girlfriend and she has a really old laptop, so that I can just plug the USB-Stick in and get the best out of it.
Furthermore my HDD on my own laptop is fairly full and I don't want to delete any of the file systems content as I still use it.

---

### Post by sudodus on 2012-01-28
> **cheatos said:**
> Because I want to be able to carry it with me, without having my laptop with me, i.e. when I'm staying with my girlfriend and she has a really old laptop, so that I can just plug the USB-Stick in and get the best out of it.
Furthermore my HDD on my own laptop is fairly full and I don't want to delete any of the file systems content as I still use it.
I am thinking in the same way. Have a look at my solution
[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

---

### Post by cheatos on 2012-01-28
@sudodus: Don't you have just a usual liveUSB? And furthermore I can't directly see in what way you restricted your user not to do anything to Windows partitions on the computer you're using it on. Could you explain this a little more? (Sorry I'm still pretty new to linux and don't really understand what is going on in the terminal, although I started to work my way through to installing and updating of software already...)

Still I have to say thank you for any input!

---

### Post by Rodney9 on 2012-01-28
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by WasMeHere on 2012-01-28
> **cheatos said:**
> @sudodus: Don't you have just a usual liveUSB? And furthermore I can't directly see in what way you restricted your user not to do anything to Windows partitions on the computer you're using it on. Could you explain this a little more? (Sorry I'm still pretty new to linux and don't really understand what is going on in the terminal, although I started to work my way through to installing and updating of software already...)

Still I have to say thank you for any input!
I have what is called a persistent live system, so that I can create a normal user (not only ubuntu) and select password and install some favourite software. And it is not wiped at reboot or power off (hence persistent).

But you have to be patient at poweroff and let the system write all cached data to the usb stick. If you pull it before it is finished, the casper-rw file will be corrupt, and you have to start with a new one (the regular live boot properties will survive).

---

### Post by sudodus on 2012-01-28
Many people use persistent live systems, as you can see :-)

Recently I learned there is also the possibility to have a casper-rw partition instead of a file, and it can be bigger than 4GB which is max in a FAT32 filesystem. This is a good idea with the new, fast and big USB sticks.

---

### Post by cheatos on 2012-01-29
Okay, so when I now want to make a persistent system, what actually is the casper-rw file or partition? Never heard of it...

---

### Post by I2k4 on 2012-01-29
I've been experimenting with persistent Live USB (generally 4GB thumb drive with 2.5GB Persistence) for about a year, on several Ubuntu, Lubuntu and Mint distros.  My experience has been they work great for a few weeks and then all screw up in some way, e.g. suddenly fail to find the computer's HDD, or suddenly come up with weird password requirements.  

I've been dual booting Lubuntu 10.10 on my netbook HDD for a while, and knock wood so far so good, much more stable.  For me the persistent Live USB is the best way to learn the OS, but not to invest a whole lot of time in it as a dependable solution. I'm still playing Mint via Persistent Live on my main laptop, but looking to install on the hard drive eventually.

That said, the fool proof official Step guide is here - use Show Me How:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

But at Step 2 on the PenDrive you'll find a setting for Persistence - you can set Persistence for all the space on the thumb drive over 1.5GB.

---

### Post by sudodus on 2012-01-30
> **cheatos said:**
> Okay, so when I now want to make a persistent system, what actually is the casper-rw file or partition? Never heard of it...

1. I suggest that you use the link suggested by *I2k4*. Post back here to let us know your results. If it does not work with your computer, we can suggest other methods.

2. casper-rw is a file or partition, where to store additional data to the USB boot drive. It has a filesystem that is mounted so that it is overlayed with the original file system, and it contains installed programs, tweaks and personal files. You can find additional information browsing the internet.

3. I agree with *I2k4 *that a persistent system is mainly for testing. Once you feel comfortable with it, you should install the system to the internal drive, HDD or SSD. But it can also be used to carry your computer environment on a small flash drive so that you can borrow almost any computer and run it.

4. I think there are a couple of reasons why it fails easily:

- when shutting down, you do not allow it to write cached data to the flash drive. I try to first log-out and wait until the light emitting diode indicates that it has finished. Then I shut-down and wait again.

- if you fill the casper-rw file or partition, so there is no room to write all the cached information.

5. A persistent live system cannot update the kernel, which is an important drawback.

---

### Post by cheatos on 2012-01-30
Hi,

thanks for your explanations, I will stick to my full install for a while as I have now tried it at my girlfriends laptop and it worked just fine, all data still there ;)
I will soon make another user just as on my desktop which needs to mount the HDD manually (hope this will work just as easy as in ubuntu)

I have recently bought a 16GB USB-Stick, maybe I'll try the persistence mode on this one and post any results here.

Thanks to all your help, I'll still read the stuff about casper -rw file, might be pretty interesting and useful at some point.

I'll still mark this as solved though.

---

### Post by KBD47 on 2012-01-30
I've had great luck doing full installs to a usb stick, it's like your own portable hard drive that you can carry in your pocket. My experience is that you need at least a 16gig stick with a swap partition along with ext4 partition. When installing you select 'something else', chose the usb stick ext4 partition, and make sure you install grub to the stick.
KBD47

---

### Post by cheatos on 2012-01-31
Hi, one more question I still have, how can I get to the GRUB config fiel?
Because sometimes the laptop just gives me some weird stuff like GRUB could not be found or something at startup, maybe I can find something out in the config file?

@KBD47: Well, I only had the 4GB one, and it was pretty hard to find an iso which didn't need more than 4GBs, but I found one made by some lubuntu user.

---

### Post by sudodus on 2012-01-31
Have a look at the following link

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by cheatos on 2012-01-31
Thank you, I'll be reading more, when I reproduced the errors.
Probably will be returning here then ;)

---

