---
title: "[SOLVED] GRUB adds more kernels after update"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by reg4c on 2008-08-16
Hey, 

perhaps this question has been answered but after a while of Googling I've decided to post.

Here is the thing:
After each update [sudo apt-get upgrade] I get a new entry in GRUB menu. 
So, when I installed Hardy I had a total of 7 entries: 3 Hardy [normal, recovery, memtest], divider and three for Windows [recovery, vista, built-in XP].
Now, a few months after that I have like 13 entries: the same three for Windoze, while Hardy adds each kernel update as a new entry; 16, 19, 21 and 24. 

Should I just remove the entries from menu.lst or is there a better way to do it?

Ow, and could someone point to a tutorial on how to make wireless on Acer Aspire 5920G work with Hardy. I tried lots of things but they just made matters worse.

Thanks
Regac

---

### Post by freesitebuilder on 2008-08-16
[http://ubuntuforums.org/showthread.php?t=861509](http://ubuntuforums.org/showthread.php?t=861509) has info on editing grub.

---

### Post by kansasnoob on 2008-08-16
The safest and simplest way to deal with that is installing Startup Manager.

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

If you click on the advanced tab it will ask you how many kernels to keep. I leave mine on (2) just in case a new kernel would result in some sort of "breakage".

It's an all around handy tool! You can even change which OS boots by default, change the "timeout", etc.

---

### Post by elmoosecapitan on 2008-08-16
So Ubuntu is really terrific and allows you to access/use previous kernel versions in the event of some catastrophic incident in which your computer crashes and burns because it doesn't like the kernel. Kernel upgrades don't happen all the time, but when they do, GRUB gives the option of which kernel the user wants to run; as well as a recovery mode version. Generally, the most updated kernel is the most secure and efficient version and thus is intended to be used. You don't have to delete the previous ones, they take up negligible room, but you can. (I don't delete them so I don't remember, sorry).


In regards to your second question, you are better off posting that in a new post or else it won't get seen by people who the answer.

cheers

---

### Post by bhadotia on 2008-08-16
If you don't like the many options presented to you  in your boot screen you can just put a '#' in front of the entries corresponding to the options you don't want in the menu.list file. There is no need to delete(uninstall) the previous versions of the kernel. This will make your boot screen cleaner without the need of uninstalling the kernels.

Regarding the second question make a new thread with the output of the command : 
```
lspci
```

Good luck ;-)

---

### Post by asmoore82 on 2008-08-16
You can simply remove the older kernels in apt/Synaptic.

---

### Post by Too Late on 2008-08-16
In the /boot/grub/menu.lst file there's a section like this:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```
The last line has the information which is read by update-grub.

---

### Post by reg4c on 2008-08-23
I thank everyone who replied.
So basically I either have to remove then from Synaptic or just comment them out.

Thanks a lot.
Cheers

---

