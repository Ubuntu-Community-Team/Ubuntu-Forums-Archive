---
title: "Lots of problems :( (inc. firefox being strange)"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by SuperT on 2008-07-15
Ok, well i have played with Ubuntu before but only just decided i would make the switch on my main computer. I still need Windows so i decided i would set up a dual boot on my Acer Laptop. Unfortunately i did not want to repartition as it was a bad time to do so as i have alot of files that are impraticle to back up at this time and i heard about Wubi on another forum (probably my first mistake). So I installed Wubi and it was all going excellently until i was in the add and remove programs thing and was going through the lists deciding what would be useful things to install. I clicked apply but it came to an error and froze when it was downloading Java Runtime from memory (or something to that effect) so after a few minutes i had to use the force exit to exit it. I then tryed to re install it and fix it and eventually i got it to work pretty easily but now i have noticed a number of problems.

In Firefox:
It is not recording history.
I cannot use the back button.
When i click tools>addons it just closes

To complicate things more one of the other things i installed was ad blocker plus.

Anyway, as i was unable to resolve this i devided to uninstall all the java things and ad block plus. I successfully uninstaller ad blocker plus but i had to go into synaptic package manager to uninstall some of the java stuff it said. So i did that but after i uninstaller the stuff it froze and ever since whenever i have tried to use a software manager tool it has just said:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
So i ran dpkg --configure -a but i got this:
> dpkg: failed to write status record about `xulrunner-1.9' to `/var/lib/dpkg/status': No space left on device


Stupidly i only allowed 6 gig i think on Wubi so i figured i must have run out of space. I then read that you could use Lubi to resize it so i went to install Lubi but i just get an error saying:
> Only one software management tool allowed to run at a time.

I have tried rebooting to no avail and have not been able to find any solutions on the net :(

Can anyone tell me how to fix it or atleast where i went wrong for next time :confused:. It is a real pain not being able to go back in firefox :(

Edit: I just realized AMSN isn't working either :(
Edit: It isn't saving any of my taskbar changes when i reboot?

---

### Post by hyper_ch on 2008-07-15
make a real install and not a wubi one and assign enough diskspace to it ;)

---

### Post by SuperT on 2008-07-15
Yes well i should have done that in the first place, i have done it before, i just couldn't be bothered backing up all my files :( I am not entirely sure that that caused the problem in the first place though and i don't want this to happen when i do install i proper one on its own partition.

---

### Post by hyper_ch on 2008-07-15
well, you just run out of space... post the output of

```

df -l

```

---

### Post by SuperT on 2008-07-15
Sure, here it is:
> Filesystem           1K-blocks Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       1453224   1453216         0 100% /
varrun                  512884       124    512760   1% /var/run
varlock                 512884         0    512884   0% /var/lock
udev                    512884        64    512820   1% /dev
devshm                  512884        12    512872   1% /dev/shm
lrm                     512884     39760    473124   8% /lib/modules/2.6.24-19-generic/volatile
/host/ubuntu/disks/usr.disk
                       3875344   2448936   1231096  67% /usr
overflow                  1024        48       976   5% /tmp
gvfs-fuse-daemon       1453224   1453216         0 100% /home/tim/.gvfs


---

### Post by hyper_ch on 2008-07-15
Well, 1.5 GB isn't much space that you gave to Ubuntu ;)

and it's better to use [noparse]```

```[/noparse] brackets around outputs/config files stuff than [noparse]> [noparse].

I'd say delete that wubi install and make a new, bigger one or make a real install... assign it at leat 6 GB so that you actually do have some free space.

---

### Post by SuperT on 2008-07-15
Really, i only gave it 1.5gig? I am sure i selected 6gig, anyway, thats a bummer. I guess i will have to put off my Ubuntu switch for a bit longer :( So do you think its because i have run out of space that all that other stuff isn't working (i used it fine for about 2 days before it started playing up)?

---

### Post by hyper_ch on 2008-07-15
actaully it created two disks... one root / and one /usr... the root is full and that's causing the problems.

---

### Post by SuperT on 2008-07-15
I think i have fixed it, i cleared enough space to run that thing then went from there. I have increaced it to 10gig and i think all my problems are solved. 
Is this better?
```
Filesystem           1K-blocks Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       1453224    918928    461056  67% /
varrun                  512884       116    512768   1% /var/run
varlock                 512884         0    512884   0% /var/lock
udev                    512884        64    512820   1% /dev
devshm                  512884        12    512872   1% /dev/shm
lrm                     512884     39760    473124   8% /lib/modules/2.6.24-19-generic/volatile
/host/ubuntu/disks/usr.disk
                       3875344   2449128   1230904  67% /usr
gvfs-fuse-daemon       1453224    918928    461056  67% /home/tim/.gvfs
/dev/sdb1              1012464    997408     15056  99% /media/TIMSUSB
/dev/sda2             47042880  41669568   5373312  89% /media/ACER_

```
Can you point out what is what in that?
Thanks for your help btw, it has been great :):KS

---

