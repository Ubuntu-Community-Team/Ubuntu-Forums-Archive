---
title: "How to get online with command line?"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by Mariane on 2012-04-04
Hi, 

My computer failed after an upgrade to 11.10. 
I get grub and I can select the option in recovery mode "drop to root shell with networking". But it does not network. 

I plugged in the network cable because wired interface is often more easy to configure than wifi interface and tried again. Still not online. 

I would like to try some of the advice given in this thread:
[http://ubuntuforums.org/showthread.php?t=1951848](http://ubuntuforums.org/showthread.php?t=1951848)
because it worked. 

But I need to go online for that. Please tell me what I can type in the root shell to tell the computer "go online".

I tried:
```

sudo ifconfig eth0 up

```

But all I got was:
[ 242.912127] r8169 0000:08:00.0: eth0: unable to load firmware patch rtl_nic/rt18168d-1.fw (-2)
[ 242.920343] r8169 0000:08:00.0: eth0: link down
[ 242.920452] r8169 0000:08:00.0: eth0: link down
[ 242.920972] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by lkraemer on 2012-04-04
Mariane,
Assuming that you have a Wired Ethernet connection to the WAN.......
and assuming your system has booted such that the Networking has been
setup, and you're not just at a Grub Menu or Prompt........

If you know the routers essid (ssid) and the correct <interface>,
shown by using the command:
```

iwconfig

```
And your choices should be something like wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and wlan0
sudo iwconfig wlan0 essid "Airlink"

To verify that your connection and working use:
```

ping -c 3 www.google.com

```
or
```

ping -c 3 74.125.224.241
ping -c 3 8.8.8.8

```

[B]But, I'd think it would be much easier to boot a LiveCD of your installed
Version of Ubuntu, then chroot to your existing system to repair what is
messed up.
[/B]
I'm not an expert on using chroot, but searches of the Forum should locate
a HOWTO: to assist you.  Or use Google to search for HOWTO: Chroot

REF's:
[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)
Read the section under RECOVERY
Now, you just need the proper steps to complete the task.......

[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)
[http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html)
[http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)
[http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation)

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)
Search for ChRoot .................

[http://fermilinux.fnal.gov/documentation/tips/mount-bind-chroot](http://fermilinux.fnal.gov/documentation/tips/mount-bind-chroot)
[http://www.tuxation.com/chrooting-into-a-linux-environment.html](http://www.tuxation.com/chrooting-into-a-linux-environment.html)

Looks like the **last URL** I found explains in detail what you need to do.
I'd think you will need mount all three as explained in the fermilinux.fnal.gov URL.
```

# mount -o bind /proc /mnt/mylinux/proc/
# mount -o bind /dev /mnt/mylinux/dev/
# mount -o bind /sys /mnt/mylinux/sys

```
 
And by using a LiveCD or LiveDVD you can forget about trying all the commands listed
in the first section of this post.

It should be easy to do.....


lk

---

### Post by Mariane on 2012-04-04
> **lkraemer said:**
> 
Assuming that you have a Wired Ethernet connection to the WAN.......
and assuming your system has booted such that the Networking has been
setup, and you're not just at a Grub Menu or Prompt........


Grub gives me some choices, I select 30.0.0.17 recovery mode, then I go to "drop to root shell with networking". I hope this answers your question. 

> **lkraemer said:**
> 
If you know the routers essid and the correct <interface>,


The router does not tell me any essid but it tells me an ssid, the name we gave when we set up the router. Is it the same thing?

```

iwconfig

```
lo no wireless extensions.
eth0 no wireless extentions

```

iwconfig ie

```
ie No such device

```

iwconfig wlan0

```
wlan0: No such device

```

iwconfig eth0

```
eth0: No wireless extensions.

I have started to download Kubuntu 11.10 amd64, it says it is going to take 3 hours and a half.

---

### Post by lkraemer on 2012-04-04
Mariane,
The very first screen that Grub presents on your display is long before
the initial boot into Linux has progressed far enough to set up your
Networking Interface.  If you haven't seen the long listings of text
scroll across your Display, then you aren't going to be able to enable
Networking.

It's probably best to just Download the LiveCD of your currently installed
Version of Linux, and do the chroot process to repair your system.  Just be
sure to read and UNDERSTAND what the process is, and how to proceed slowly
making sure each command is correctly typed (or Copy & Paste).

lk

---

### Post by Mariane on 2012-04-04
I did see a lot of text scrolling upwards. 

Read chroot, OK, I'll read it. 
Understanding it I cannot promise :)

For the moment I found text such as:

> 
Calls to chroot() do not stack, with additional calls essentially overwriting the existing one. It can only be called by privileged programs and can be trivially bypassed by those who can call it as man 2 chroot describes:

This  call does not change the current working directory, so that after the call '.' can be outside the tree rooted at '/'.  In particular, the superuser  can  escape from a 'chroot jail' by doing 'mkdir foo; chroot foo; cd ..'.

The use of the term "chroot jail" in the manpage is unfortunate as it may help perpetuate a common misconception about chroot(). It often gets mentioned in the same context as the "jail" calls for the BSDs, but it has little in common with them. A BSD jail is a mini-virtualization that partitions a system into multiple virtual systems each of which can have its own root account. chroot() has none of that sophistication. 


:lolflag: 

Your links seem much better. At least the first one: "Recovery : Should a system be rendered unbootable, a chroot can be used to move back into the damaged environment after bootstrapping from an alternate root file system (such as from installation media, or a Live CD)." I can understand. Thanks a lot.

Meanwhile, the download failed. The connection got interrupted for some reason. Maybe the broken computer tried to get online while I was not watching and messed things up. So I'm starting again.

---

### Post by Mariane on 2012-04-05
md5sum and what I see online is the same number. So I'm burning the CD. I again had a surprise: I read that it was advisable to burn it as slowly as possible, so I dutifully triggered the "Speed" menu in K3b. 

The possible speeds are Auto, DAO, TAO and RAW. :lolflag: 

As I had no idea which was the slowest, I left it on "Auto".

---

### Post by lkraemer on 2012-04-05
Mariane,
Typically one tries to burn an ISO at the slowest speed and as:
Disk At Once = DAO   to prevent errors. 

If the MD5SUM is correct you should be fine.

Yes, the first link states exactly what you need to do. And, the last link
tells the steps with a good explaination of the steps.  It shouldn't be a
problem.  The other links contain good information I found during my searches.

I just located another good article on ChRoot and it is located here:
[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

If you scroll down to ChRoot: in the article, this is what you will be doing.
Just copy & Paste to prevent errors.........................................
I'd think that if you skipped Step #3, assuming you don't have RAID, along with
all Steps #9, #10, #11, & #12 you should be at a point where you can get to the
URL you need to repair what is broken.  Then just continue at Step #13 when your
problem is repaired.  

Test your system by rebooting.  Repeat ChRoot Process as necessary.

lk

---

### Post by Mariane on 2012-04-08
Thanks a lot, lkraemer. If I get the hardware of this laptop back in working order I'll come back to your advice and links. 

I know I should burn an iso as slowly as possible, but the possible speeds were listed as  Auto, DAO, TAO and RAW. I had no idea which one of these was the slowest. 

There was something wrong with the battery. The power jack was not making good contact. The computer was plugged into the mains but not charging, and the battery chose to fail during the upgrade, of all times... 

I found a site to help me take it apart:
[http://www.scribd.com/doc/61048900/Taking-Apart-Dell-Vostro-1510](http://www.scribd.com/doc/61048900/Taking-Apart-Dell-Vostro-1510)
and another site to order a power jack from: [http://www.powerjack.us/](http://www.powerjack.us/)

I had to take the laptop completely apart to reach the power jack, whether it will ever work again is anyone's guess. But if the hardware does work again, I'll start on the software... Meanwhile I have to wait until I receive the new power jack.

---

