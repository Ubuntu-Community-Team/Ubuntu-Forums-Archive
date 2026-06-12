---
title: "update manager interrupted"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by mickeyd1965 on 2008-08-14
Hi Everyone,
To start with, everytime i try to use the screensaver program the whole computer freezes. It's stuck on 10 minutes then goes to a screensaver which freezes the computer. This happened during an update which caused an error message to be displayed. it told me to run 'dpkg and "configure a " , Which means nothing to me. It then displayed the line,     
                     E;_cache->open()
 Can anyone help me or am i going to have to become a computer expert in order to use Ubuntu. I'm not a complete moron, i do have some intelligence, but unfortunately it isn't with computers.

Thanks 
m

---

### Post by kaboodle_fish on 2008-08-14
All you need to do is open a terminal and paste the dpkg etc in and press Enter
 
You will need to close Synaptic before running it though
 
edit: Believe me, you do not need to be any sort of computer expert to use Ubuntu.

---

### Post by bryncoles on 2008-08-14
this happened to me once too, when i was starting out! it can be confusing. what you need to do is open a terminal (applicattions, accessories, terminal) type in 'sudo', then a space, then the command exactly as it appears in your error message. press return and it'll ask for your password. when you type it, nothing will be displayed on screen. dont worry thats normal, just type your password and press return. ubuntu will then magically fix its update manager problem and you'll be good to go again!

hope that helps!

*edit for clarity*

close update manager and any instance of synaptic you have running, open the terminal and type / cut and paste:

```
sudo dpkg --configure -a
```

type in your password (which wont appear on screen for security reasons) press return, done!

---

### Post by iaculallad on 2008-08-14
Open your terminal:

```
sudo dpkg --configure -a
```

---

### Post by bryncoles on 2008-08-14
> **kaboodle_fish said:**
> edit: Believe me, you do not need to be any sort of computer expert to use Ubuntu.

+1. its a different OS is all. once you get used to the way it does things, it starts to seem as intuitive and sensible as any other system. and once you get to configuring it to your preferences, it seems even more intuitive! 

hope you enjoy your stay here!

---

### Post by mickeyd1965 on 2008-08-14
Thanks guys. It worked. Can anyone tell me how to fix the screensaver program.

m

---

### Post by tangibleorange on 2008-08-14
> **mickeyd1965 said:**
> Thanks guys. It worked. Can anyone tell me how to fix the screensaver program.

m

Go into synaptic, search for 'gnome-screensaver' (without the quotes), and mark it for re-installation. hopefully that will fix the problem.

---

### Post by eluis.c on 2008-08-14
i had the same problem but when i run "sudo dpkg --configure -a" it froze at this part:

Generating locales...
   en_AU.UTF-8...

---

### Post by Ryadt on 2008-08-14
> **eluis.c said:**
> i had the same problem but when i run "sudo dpkg --configure -a" it froze at this part:

Generating locales...
   en_AU.UTF-8...

Can you post the whole output?

---

### Post by eluis.c on 2008-08-14
now it got frozen in this part:

Setting up language-pack-en-base (1:7.10+20080205) ...

---

### Post by eluis.c on 2008-08-14
should i reinstall ubuntu?

---

### Post by Elfy on 2008-08-14
> should i reinstall ubuntu?shouldn't be necessary, there has been a bug in it I think - this should help I think [http://ubuntuforums.org/showthread.php?p=5570250](http://ubuntuforums.org/showthread.php?p=5570250) particularly post 15

---

### Post by ShelJ on 2008-08-14
Hi, 

I'm having the same problem, however ```
sudo dpkg --configure -a

``` doesn't work.  This is what I get instead:

```
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-20-rt (2.6.24-20.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-20-rt

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-20-rt
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-20-rt (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-20-rt

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-20-rt
dpkg: subprocess post-installation script returned error exit status 1

```

And, the problem persists.  i tried making sure that all Synaptic programs were closed, but nothing helps.  Any advice?  

Thanks.

---

### Post by Elfy on 2008-08-15
> gzip: stdout: No space left on deviceYou've run out of room - open a terminal and run

```
df -h
```

---

### Post by ShelJ on 2008-08-15
> **forestpixie said:**
> You've run out of room - open a terminal and run

```
df -h
```


Thanks,
 I think that I see the problem, my boot /dev/sda1 is full:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ShelJ-root
                      225G   45G  170G  21% /
varrun                685M  244K  685M   1% /var/run
varlock               685M     0  685M   0% /var/lock
udev                  685M   76K  685M   1% /dev
devshm                685M     0  685M   0% /dev/shm
/dev/sda1             236M  234M     0 100% /boot

```How do I correct this? This is a new problem to me, since my weekly update last week.

---

### Post by Elfy on 2008-08-15
Indeed - easiest way would be to unistall old kernels, but doubt if that will work at the moment. I would resize it as I'm not sure that moving old kernels out of the way would be a good idea for the grub update, I have some kernel.bak files - maybe they could be moved - not sure though.

I doubt if you would need to resize it by much - 10-15Mb at the most.

Edit follow this thread - it deals with exactly the same scenario -

[http://ubuntuforums.org/showthread.php?t=890931](http://ubuntuforums.org/showthread.php?t=890931)

Run this command to find out what you have installed in the way of kernels.

```
dpkg --get-selections | grep linux
```

---

### Post by ShelJ on 2008-08-17
As I was trying to find a way to increase this partiton, I found that I had to resize my LUKS partition, and in doing so I accidentally erased everything.  So, I'm forced to reistall Ubuntu, thanks for your help anyways.

---

### Post by dmakane on 2008-08-17
That's doig he same ting or me with he lines:

Setting up language-pack-fr-base (1:7.10+20080205) ...
Generating locales...
  fr_BE.UTF-8... 

Going nowhere then...

Michel

---

