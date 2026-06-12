---
title: "Problem with Ubuntu/Kubuntu dual boot"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by SilverGoldBronze on 2008-07-31
So I decided to try out Kubuntu as an alternative to Ubuntu, I needed to install to use other programs I need, so I installed Kubuntu. Now the problem here is I had a broken Windblows already, so I deleted Windblows with gParted from my 7.10 Live CD, (8.04 is being lent to friend). I installed Kubuntu and noticed that Windblows is still on GRUB and Kubuntu isn't. Kubuntu is where Windblows was. Trying to boot Windblows gives me an error, so I wanted to know: How do I add Kubuntu as a boot choice and get rid of Windows as a boot choice? This may or may not be relevant, but I got an error while installing Kubuntu saying that there was a buffer malfunction or something. Do I just reburn the Kubuntu ISO? By the way, the ISO I downloaded is KDE 4 Remix~

---

### Post by Cygnus on 2008-07-31
You should not have to dual boot between ubuntu and kubuntu, as I unserstand it you can install the kde packages on an ubuntu install or the gnome packages on a kubuntu install, then you can just switch at the login screen. ( I have not tried this however. )

---

### Post by SilverGoldBronze on 2008-07-31
It's not the whole whether or not I should dual boot, it's how do I?

---

### Post by vikram on 2008-07-31
When you login to Ubuntu you can choose your session type as either GNOME or KDE or others if you have them installed. 

If you choose to have Kubuntu on another disk and it is already installed try editing GRUB in your Ubuntu installation.

see
[http://ubuntuforums.org/showthread.php?t=263704](http://ubuntuforums.org/showthread.php?t=263704)

basically edit  /boot/grub/menu.lst. copy the Ubuntu configuration, give it another name say Kubuntu and change (hd0,0) to whatever your windows disk/partition was.

this may also help
[http://www.gnu.org/software/grub/manual/html_node/Configuration.html](http://www.gnu.org/software/grub/manual/html_node/Configuration.html)

---

### Post by neurostu on 2008-07-31
Dual booting is simple.

Create two / partitions, one for each version of linux
create a home partitoin
create a swap partition

Install Ubuntu to one of the / partitions
install Kubuntu to the other / partition

The second install will also install GRUB to work with both installations.


Honesetly though it is a waste of time to dual boot Ubuntu and Kubuntu because you are running the same OS with a different GUI.

I can understand that you want to learn how to do this... but dual booting linux is really only useful when you want to run a different distro of linux (like debian, gentoo, CentOS, etc)

---

### Post by markbuntu on 2008-07-31
Ok, since nobody actually answered your question yet, I will give you some help. You can boot into any operating system from grub by using the chainloader option. All you need to know is the drive/partition where the other os boot sector is and then you can add these lines to /boot/grub/menu.lst after the regular lines:

```

#chainloader for kbuntu
root   (hd0,0)
chainloader   +1

```

Grub will hand over the boot to that drive/partition, no questions asked. You can change the (hdx,x) to your drive/partition.

You can go here to learn more about grub:


[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm).

---

### Post by SilverGoldBronze on 2008-08-01
Thanks, that worked marvelously~

---

