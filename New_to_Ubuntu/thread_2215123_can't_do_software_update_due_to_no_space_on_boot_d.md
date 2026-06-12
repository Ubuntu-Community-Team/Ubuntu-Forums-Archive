---
title: "can't do software update due to no space on boot drive"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by lizpy66 on 2014-04-04
not sure if this is the right place to post so sorry if it is.

Software updater notified me of updates so I checked what would be updated and accepted but it said I can't due to the boot drive not having enough space so how would I grab my free memory,about 80 left, to put there for future updates? atleast 500mb, I just don't want to lose anything while doing this

Any help is appreciated just try to explain in layman terms

---

### Post by 23dornot23d on 2014-04-04
Type lowercase DF into a terminal .... and post back the results ..... please 
(as it will just show the use and space on the mounted drives)

Then maybe we can go from there.

> 
**df**


_______________________________________________

[I]Just as an example below - on my machine it gives information back like this - where it
show the percentages used of each of the parts of your disk - one will be 100% full probably.[/I]

> 
keith@keith-laptop:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda10      81303280 46600740  30549452  61% /
none                   4        0         4   0% /sys/fs/cgroup
udev             2005356       12   2005344   1% /dev
tmpfs             403728     1244    402484   1% /run
none                5120        0      5120   0% /run/lock
none             2018640      100   2018540   1% /run/shm
none              102400       20    102380   1% /run/user
/dev/sda9       95989516 77031500  14058896  85% /media/keith/ac525382-a418-48f1-8cac-73fa86d18bc2
keith@keith-laptop:~$ 



---

### Post by ibjsb4 on 2014-04-04
Sounds like old kernels.  How do you like the command line :)

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by lizpy66 on 2014-04-04
old kernals? what? sorry new linux user and also I'm on UEFI system if that matters. here are the results Mr. 23 

larry@larry-HP-Pavilion-g6-Notebook-PC:~$ df
Filesystem                  1K-blocks      Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root 303206784 222748672  65032988  78% /
none                                4         0         4   0% /sys/fs/cgroup
udev                          1707908         4   1707904   1% /dev
tmpfs                          343680      1236    342444   1% /run
none                             5120         0      5120   0% /run/lock
none                          1718396       768   1717628   1% /run/shm
none                           102400        84    102316   1% /run/user
/dev/sda2                      241965    169826     59647  75% /boot
/dev/sda1                      497696      3376    494320   1% /boot/efi
larry@larry-HP-Pavilion-g6-Notebook-PC:~$

---

### Post by ibjsb4 on 2014-04-04
Step #4 should tell the story.

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9]
```

---

### Post by 23dornot23d on 2014-04-04
Nothing obvious there ..... so one more command nice and easy again (DF -I ) lowercase 


[SIZE=4]**df -i**
[/SIZE]
will give an output similar to this one

```

keith@keith-laptop:~$ df -i
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda10     5177344 1515215 3662129   30% /
none            211086       2  211084    1% /sys/fs/cgroup
udev            204445     573  203872    1% /dev
tmpfs           211086     630  210456    1% /run
none            211086       2  211084    1% /run/lock


```

The command also posted will give something like this ..... its to see if a lot of old kernels have been left on the system
basically looking for old things to clear away

```

keith@keith-laptop:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9]
linux-headers-2.6.35-2
linux-headers-2.6.35-2-generic
linux-headers-2.6.38-16
linux-headers-2.6.38-16-generic
linux-headers-3.2.0-59
linux-headers-3.2.0-59-generic
linux-headers-3.5.0-46
linux-image-2.6.35-2-generic
linux-image-2.6.38-16-generic
linux-image-3.13.0-11-generic
linux-image-3.2.0-59-generic
linux-image-3.5.0-46-generic
linux-source-2.6.38
keith@keith-laptop:~$ 



```

---

### Post by lizpy66 on 2014-04-04
here you go and thanks for the help in advance

Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 19267584 522482 18745102    3% /
none                          429599      2   429597    1% /sys/fs/cgroup
udev                          426977    544   426433    1% /dev
tmpfs                         429599    588   429011    1% /run
none                          429599      2   429597    1% /run/lock
none                          429599     24   429575    1% /run/shm
none                          429599     38   429561    1% /run/user
/dev/sda2                      62496    269    62227    1% /boot
/dev/sda1                          0      0        0     - /boot/efi
larry@larry-HP-Pavilion-g6-Notebook-PC:~$

---

### Post by 23dornot23d on 2014-04-04
one more command - slightly longer - soon have you upto speed with the command line
this just lists the kernels in the boot directory .... similar to the long line from the other post
but less threatening .......... ls (LS) just lists things ...... /boot/ is just the area we are looking in.

**ls /boot/**

Will give an output like this

```

keith@keith-laptop:~$ ls /boot/
3.5.0-46                      initrd.img-3.5.0-46-generic
abi-2.6.35-2-generic          memtest86+.bin
abi-2.6.38-16-generic         memtest86+.elf
abi-3.13.0-11-generic         memtest86+_multiboot.bin
abi-3.13.0-12-generic         System.map-2.6.35-2-generic
abi-3.2.0-59-generic          System.map-2.6.38-16-generic
abi-3.5.0-46-generic          System.map-3.13.0-11-generic
config-2.6.35-2-generic       System.map-3.13.0-12-generic
config-2.6.38-16-generic      System.map-3.2.0-59-generic
config-3.13.0-11-generic      System.map-3.5.0-46-generic
config-3.13.0-12-generic      vmcoreinfo-2.6.35-2-generic
config-3.2.0-59-generic       vmcoreinfo-2.6.38-16-generic
config-3.5.0-46-generic       vmlinuz-2.6.35-2-generic
grub                          vmlinuz-2.6.38-16-generic
initrd.img-2.6.35-2-generic   vmlinuz-3.13.0-11-generic
initrd.img-2.6.38-16-generic  vmlinuz-3.13.0-12-generic
initrd.img-3.13.0-11-generic  vmlinuz-3.2.0-59-generic
initrd.img-3.13.0-12-generic  vmlinuz-3.5.0-46-generic
initrd.img-3.2.0-59-generic
keith@keith-laptop:~$ 


```

---

### Post by lizpy66 on 2014-04-04
abi-3.11.0-12-generic	      lost+found
abi-3.11.0-14-generic	      memtest86+.bin
abi-3.11.0-15-generic	      memtest86+_multiboot.bin
abi-3.11.0-17-generic	      System.map-3.11.0-12-generic
abi-3.11.0-18-generic	      System.map-3.11.0-14-generic
config-3.11.0-12-generic      System.map-3.11.0-15-generic
config-3.11.0-14-generic      System.map-3.11.0-17-generic
config-3.11.0-15-generic      System.map-3.11.0-18-generic
config-3.11.0-17-generic      vmlinuz-3.11.0-12-generic
config-3.11.0-18-generic      vmlinuz-3.11.0-14-generic
efi			      vmlinuz-3.11.0-14-generic.efi.signed
grub			      vmlinuz-3.11.0-15-generic
initrd.img-3.11.0-12-generic  vmlinuz-3.11.0-15-generic.efi.signed
initrd.img-3.11.0-14-generic  vmlinuz-3.11.0-17-generic
initrd.img-3.11.0-15-generic  vmlinuz-3.11.0-17-generic.efi.signed
initrd.img-3.11.0-17-generic  vmlinuz-3.11.0-18-generic
initrd.img-3.11.0-18-generic  vmlinuz-3.11.0-18-generic.efi.signed
larry@larry-HP-Pavilion-g6-Notebook-PC:~$ 


thanks for the simple advice :)

---

### Post by 23dornot23d on 2014-04-04
Your welcome - but the thing is I am not seeing anything that is taking all your space up there .......

You do have some old kernels that can be removed .... but the file system seems to be showing you
have room to work in.

We can just clear some things up ......

> 
[B]sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update[/B]


See if they allow for the system to update ..... ok .........

let me know what you get back when running them though - its clearing out old packages used for upgrades and installs
that you already have on your system ...........

Then the 3rd command just updates your listings ..... for the lists of new packages ......

A full explanation is here too .... just so you can be sure of what is happening 

[http://askubuntu.com/questions/3167/what-is-difference-between-the-options-autoclean-autoremove-and-clean](http://askubuntu.com/questions/3167/what-is-difference-between-the-options-autoclean-autoremove-and-clean)

---

### Post by lizpy66 on 2014-04-04
yeah I noticed I wasn't getting exactly what you wanted, not sure why

that seemed to do the trick :D thanks so much

---

### Post by 23dornot23d on 2014-04-04
Yep psychic world this computer world business ...... we know what we are thinking ....... but we do not
always see what others see ...... but have an idea of where they are heading ;)

Glad you are sorted .... but we only cleared a small amount out - so it may happen again in the future.


mark it as solved once you are happy its working ok ......... cheers .......
> 
lbjsb4 seemed to have the better link to how to deal with the situation
Sounds like old kernels.  How do you like the command line [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

[http://tuxtweaks.com/2010/10/remove-...h-one-command/]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/")



Think I may have missed the full reason the boot was full here ....... as there is a better explanation here
and some of the things that can go wrong when removing kernels .... seems sda2 was smallish

/dev/sda2                      241965    169826     59647  75% /boot

But not 100 % full as I was expecting ........ the link below does give an explanation though about it ......

[http://askubuntu.com/questions/263363/how-can-i-remove-old-kernels-install-new-ones-when-boot-is-full](http://askubuntu.com/questions/263363/how-can-i-remove-old-kernels-install-new-ones-when-boot-is-full)

---

### Post by mörgæs on 2014-04-05
Both of you, please use CODE (not QUOTE) tags when posting terminal output.

---

