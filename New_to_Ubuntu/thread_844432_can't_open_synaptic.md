---
title: "can't open synaptic"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by konos on 2008-06-29
i get the following message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can anyone please tell me what to do..
thank you in advance

---

### Post by Marshal0505 on 2008-06-29
it says:

you must manually run 'dpkg --configure -a' to correct the problem

try running that one in a terminal :p

---

### Post by Bodsda on 2008-06-29
As Marshal0505 says, simply run

```
dpkg --configure -a
```

if you get a 'permission denied error, then run

```
sudo dpkg --configure -a
```

---

### Post by Elfy on 2008-06-29
Almost right - you need to run it as root :)

```
sudo dpkg --configure -a
```

---

### Post by sayakb on 2008-06-29
Do:
```
sudo dpkg --configure -a
```

EDIT: People are fast here.. :o

---

### Post by Elfy on 2008-06-29
@bodsda - cool, a new name in BT - unless I haven't seen you before of course :D

---

### Post by konos on 2008-06-29
thank you!!

---

### Post by RobJN on 2008-07-03
I have a very similar problem:

When I try to install anything under Add/Remove Applications I get the error when I click Apply Changes:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


As suggested I have run:

sudo dpkg --configure -a

But get this response:

Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1



Can anyone help someone trying to make the switch from Windows

RobJN

---

### Post by drs305 on 2008-07-03
> **RobJN said:**
> I have a very similar problem:
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

**gzip: stdout: No space left on device**
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1

Can anyone help someone trying to make the switch from Windows

RobJN

If you have a small /boot partition it is possible it is full of old kernels. Look in synaptic at "linux-image ..." and see how many old kernels you have. You may need to delete some of the older ones to make room for the newer ones on your /boot partition. 

If you have been running a specific kernel for a while it would be safe to remove the older ones. You can always reinstall them if needed but keep at least one previous kernel if your /boot size allows.

---

### Post by RobJN on 2008-07-03
Yes I have been reading around some other posts and had worked out that was the problem.  Shame really as I was recommended that 50mb /boot would be fine.

However I cannot get into the synaptic manager to do this as the first error stops me.  that is:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


How can I clear my /boot in a different way.
btw this is a fresh install of ubuntu, the only thing i did was install updates after first time boot.
oh and clearly i'm a noob

---

### Post by drs305 on 2008-07-03
> **RobJN said:**
> Shame really as I was recommended that **50mb /boot** would be fine.

How can I clear my /boot in a different way.
btw this is a fresh install of ubuntu, the only thing i did was install updates after first time boot.
oh and clearly i'm a noob

that is almost certainly the problem. 

try booting from grub into the recovery mode and select 'Drop to root shell prompt'

find the existing kernels on your machine:
```
**find /boot -iname vmlinuz***
```
you should see several results like: 
/boot/vmlinuz-2.6.24-17-generic
/boot/vmlinuz-2.6.24-18-generic

Determine which kernel you are currently using:
```
uname -r
```
Remove some of the older ones - make sure you don't delete the one you are currently using (for example)
```
rm /boot/vmlinuz-2.6.24**-17-generic**
```
Reboot:
```
shutdown -r now
```

Consider making the boot partition larger if possible  ;-)

---

### Post by Elfy on 2008-07-03
I've seen half a dozen or more of these - all saying they read to have /boot of 50Mb :( and all end up in exactly the same place having todo the same thing. Love to know if they all been to the same place :)

---

### Post by rxtx on 2008-07-03
/boot = biiiig. Having such a small area set aside for this mount point is never a good idea.

Maybe ```
sudo apt-get clean
``` will free some more space if you're THAT desperate.

---

### Post by RobJN on 2008-07-03
Thanks everyone, all that is very useful.  I went with resizing the partition as I prefer long time fixes to something quick and easy but not long lasting.

Yeah I'll have a look through my firefox history to see if I can find the page recommending 50mb as this does seem to have caught a lot of people out.

Edit: found it.  [http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/)
I've posted a comment so hopefully that will get through.  I'll stick to these forums and the community docs from now on as google searches pull up a lot of old (i.e pre 8.04) or badly advised information

Thanks again

---

### Post by lisati on 2008-08-16
Also see [http://ubuntuforums.org/showthread.php?t=891493](http://ubuntuforums.org/showthread.php?t=891493)

---

