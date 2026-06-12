---
title: "whats all these loops"
date: 2019-04-06
forum: New to Ubuntu
---

### Post by gary171261 on 2019-04-06
Hi fairly new so sorry if question is stupid.
when i type lsblk in terminal i get all this.
oop0                   7:0    0  34.6M  1 loop  /snap/gtk-common-themes/818
loop2                   7:2    0    91M  1 loop  /snap/core/6350
loop3                   7:3    0 140.7M  1 loop  /snap/gnome-3-26-1604/82
loop4                   7:4    0  14.8M  1 loop  /snap/gnome-characters/206
loop5                   7:5    0  35.3M  1 loop  /snap/gtk-common-themes/1198
loop7                   7:7    0    13M  1 loop  /snap/gnome-characters/139
loop8                   7:8    0  1008K  1 loop  /snap/gnome-logs/57
loop9                   7:9    0 143.5M  1 loop  /snap/gnome-3-28-1804/23
loop10                  7:10   0  53.7M  1 loop  /snap/core18/782
loop11                  7:11   0     4M  1 loop  /snap/gnome-calculator/352
loop13                  7:13   0  14.5M  1 loop  /snap/gnome-logs/45
loop14                  7:14   0  89.3M  1 loop  /snap/core/6673
loop15                  7:15   0   2.3M  1 loop  /snap/gnome-calculator/260
loop16                  7:16   0 140.7M  1 loop  /snap/gnome-3-26-1604/74
sda                     8:0    0   2.7T  0 disk  
&#9500;&#9472;sda1                  8:1    0     1M  0 part  
&#9500;&#9472;sda2                  8:2    0   732M  0 part  
&#9492;&#9472;sda3                  8:3    0   2.7T  0 part  
  &#9492;&#9472;sda3_crypt        253:0    0   2.7T  0 crypt 
    &#9492;&#9472;ubuntu--vg-root 253:1    0   2.7T  0 lvm   /
sdb                     8:16   1  57.3G  0 disk  
&#9492;&#9472;sdb1                  8:17   1  57.3G  0 part  
sr0                    11:0    1     2K  0 rom   

Sda i understand but what are these loops. I can not open them or delete them.
I mean as far as i can tell there not doing any harm. 
But i would love to know were they came from and how do i get rid of them.:confused::confused:
cheers
newbie

---

### Post by VMC on 2019-04-06
One explanation:
[https://askubuntu.com/questions/906581/what-is-dev-loopx](https://askubuntu.com/questions/906581/what-is-dev-loopx)

---

### Post by deadflowr on 2019-04-07
Those are all snap packages, mounted on the system as block devices as VMC pointed out in the link provided.
You can remove them without any harm to the system using the snap commands.

basic snap commands include
```
snap help
snap list
sudo snap install <snap-package-name-here>
sudo snap remove <snap-package-name-here>
```

Since you only have the three default snaps that now ship with Ubuntu you can, if you want, replace those with the older debian-based apt packages.
Those packages are gnome-logs, gnome-characters, and gnome-calculator.
(The other snaps are theme and other underlining pieces that make the snaps work right.
The core snap being the snap linchpin as all snaps rely on that. And without it snaps cannot run.)

You can learn more here:
[https://docs.snapcraft.io/snap-documentation/3781]("https://docs.snapcraft.io/snap-documentation/3781")

---

### Post by oldfred on 2019-04-07
Some more info on snaps.
They are improving loading time.

       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

### Post by gary171261 on 2019-04-07
Thanks everyone and i get the subtle message look things up before asking question.
I totally agree.
But thanks anyway and a lesson learnt.
cheers
sepp

---

### Post by RedDirtDog on 2019-04-08
> **gary171261 said:**
> Hi fairly new so sorry if question is stupid.
cheers
newbie

I am a firm believer in "the only stupid question is the one you don't ask".  Your question (and yeah lol i guess you should have searched first) prompted answers which have helped me locate a problem I didn't realise i had :p

---

