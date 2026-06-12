---
title: "HOW TO: Install .ipa's on you iPhone/iPod Touch"
date: 2010-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Gonz_91 on 2010-03-03
Hello everyone!

A few days ago, I decided to move back into Ubuntu, and was immediately stomped: I couldn't install any .ipa's I obtained, since I didn't have iTunes!
Well, after some snooping around, I solved this issue, and wrote up a small tutorial, which I will write out here, more elaborately.

So, people who like to keep .ipa backups of their apps, read on!

[COLOR="Red"]Requirements:[/COLOR]
1. iPhone/iPod touch running:
  1.1. Jailbreak (I won't need to explain this here. I highly recommend GeoHot's utility, though: [blackra1n]("http://blackra1n.com/"))
  1.2. OpenSSH: this you can easily install on a jailbroken device, simply search for it on Cydia/Icy/Rock.
  1.3. Installous: this one is rather tricky. [Source.]("http://hackulo.us/forums/index.php?/topic/651-hackulous-announces-first-official-application-installous/") Needless to say, I don't approve of piracy, but totally recommend the use of this program to install .ipa's you already have, acquired, for instance, through iTunes.

2. Ubuntu desktop (I'm running 9.10 at the moment, but that's irrelevant) running:
  2.1. sshfs: this should come already installed with your OS; at least it did in mine. If it doesn't, it should be in the repos (ALT + F2: synaptic).
 2.2. Fuse: should also come as default.

Now that we got all that out of the way, on to the tutorial itself:

[COLOR="Red"]STEP 1:[/COLOR]
 Connect both your iDevice and computer to the same network. I highly recommend using a standard router, since Ad-Hoc seems quite complicated (didn't manage it myself).

[COLOR="Red"]STEP 2:[/COLOR]
First off, lets mount your device as a file system, using sshfs:
 ```
sshfs root@<yourdevice'sIP>:/ mountpoint
```
In my case, this would be:
 ```
sshfs root@192.168.0.102:/ ~/pod
```
Since my iPod's IP on the network is 192.168.0.102.
You will be prompted for root password, which by default is "alpine".
I highly recommend you change this, since it's a vulnerability. Also, you shouldn't leave SSH on when not using it. (look for SBSettings on the Cydia/Icy/Rock repos).

[COLOR="Red"]STEP 3:[/COLOR]
 Now that you have your device mounted on the mountpoint of your choice, point your file browser to it (I'm using GNOME's Nautilus).
 You should now see some folders, typical in the root of a UNIX file system (such as usr, var, etc...).
 Using good old drag'n'drop, place your .ipa's in:
 ```
mountpoint/var/mobile/Lybrary/Downloads
```
 (Case sensitive)

 Not that your .ipa's are in place, you can unmount the device, using Fuse:
 ```
fusermount -u mountpoint
```
 
 In my case this would be
 ```
fusermount -u ~/pod
```

[COLOR="Red"]STEP 4:[/COLOR]
 Now, to do the actual installation, fire up Installous on your iDevice, tap "Downloads", and all your -ipa's should be there. Tap once to install.


[COLOR="Red"]ALTERNATE METHOD:[/COLOR]
 As I later found out, you can use Nautilus to direclty SSH into something. On your desktop, CTRL+L, then type

```
ssh:<yourdevice'sIP>
```
then login as root.

I never tested this method thoroughly, but it should work, and has the advantage of simplicity.


Presto!


[COLOR="Red"]Observation:[/COLOR]
When you install apps using installous, Apple won't send you updates for them. This might come to be a problem. A little workaround I'd use is have iTunes installed in a Windows virtual machine, get your app updates from there, and install them on your device using Installous.
You don't need to uninstall the apps before updating, just do as before, and Installous should update them without further hassle.

---

### Post by tora201 on 2010-05-05
Cheers for that. Very easy and simple solution!

---

### Post by Quiane on 2010-05-24
Great tutorial, and something i hadn't thought of! Cheers!

---

### Post by cenkozan on 2010-11-14
OR, you can easily download iFile from Sinful Repo from Cydia, and put your ipa's in var/mobile/library/downloads.

---

### Post by boblemur on 2011-01-08
Would just like to add the fact that the folder is different now. Or at least it was a different folder on my iPhone 3g.

new directory was:

```
/private/var/mobile/Documents/Installous/Downloads/
```

---

