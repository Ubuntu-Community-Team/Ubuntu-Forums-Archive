---
title: "[SOLVED] Problems while dual booting 32 bit and 64 bit Ubuntu 8.04"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by _r_a_V_a_n_ on 2008-07-17
I installed 32 bit Hardy making partitions for /boot (100mb), swap space  and / (~35GB... /dev/sda6). It was up and running and successfully updated the patches for the system.

Then, I went ahead with the installation of the 64 bit Hardy keeping the /boot and swap space common and a new partition for / (again ~35GB... /dev/sda7). Again... this installation also went smoothly and was successful in updating patches for the system.

Now... before I had started the installation for 64bit Hardy, I had took a backup of the /boot/grub folder. After the installation, when I viewed the menu.lst file, the entries for the 32bit partition was missing (as expected). I took the entries from the backed up file and pasted in the new menu.lst and rebooted.

Upon rebooting, when i selected 32 bit... the XServer wont start up, and it landed me in the shell prompt. I typed in 'exit', and the xserver started up and the login screen came up. But... the mouse wouldnt work and the resolution was maxxed out at 800*600 with a crappy color mode :confused: The 64 bit OS still does work smoothly though, but I want the 32 bit to be up and running :(

Anyone faced such a problem before? Can anyone help me out of this mess?

---

### Post by Elfy on 2008-07-17
Maybe it would have been better to have seperate /boot partitions, but not completely sure - can you boot whichever works and then post both the menu lists.

---

### Post by Inxsible on 2008-07-17
You cannot have the same boot partition for different OSes. The boot partition is where the info about the kernel is stored. And 32 bit and 64 bit kernels are different. When you installed the 64 bit, i think the 32 bit kernel info was overwritten.

Every OS you install should have different partitions of everything. Swap is the only partition that you can re-use between OSes.

---

### Post by Elfy on 2008-07-17
Thought so, but wasn't sure enough to say so :)

@Inxsible - Would the easiest thing be to reinstall the 32bit?

---

### Post by Inxsible on 2008-07-17
> **forestpixie said:**
> Thought so, but wasn't sure enough to say so :)

@Inxsible - Would the easiest thing be to reinstall the 32bit?Yes....and this time create a separate boot partition. :)

also @OP : it is also advisable to create a separate home partition. Read into it. That way, if and when you re-install an OS, you don't lose all your user settings.

---

### Post by Elfy on 2008-07-17
> Yes....and this time create a separate boot partitionGuessed that would be the answer ;) - the only things I've bveen involved in have had /boot that were too small, then not booting once there was a new kernel.

Personally I've only ever bothered with a /home

One more piece of the puzzle :)

---

### Post by Inxsible on 2008-07-17
> **forestpixie said:**
> Guessed that would be the answer ;) - the only things I've bveen involved in have had /boot that were too small, then not booting once there was a new kernel.

Personally I've only ever bothered with a /home

One more piece of the puzzle :)When I started out with linux, all I had was root, home and swap....But over time I have come to realize that it does help if you make dedicated partitions for /boot, /var,/home,/root and swap of course... those are the partitions I always make now, when I install any linux distro.

---

### Post by Elfy on 2008-07-17
I soon learnt to have a seperate /home :)

I have looked into the /boot, /var eg - not convinced yet though. I can understand the argument for servers - I think ;) 

Thanks for the info - I guess the OP will find out more than expected as well.

---

### Post by markbuntu on 2008-07-17
A side note here. You cannot share /home partitions between different operating systems/distributions. If you want to save your personal data create a separate partition called data or personal or something and mount it under /home. 

The /home directory contains config files which will cause you all sorts of interesting problems if you share them between different operating systems.

---

### Post by bodhi.zazen on 2008-07-17
Just for a little clarification ...

It gets a little complicated when you start making your partition scheme more and more complicated.

Rather then a /boot partition you can have a grub partition.

There are a number of how-to's, like these :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

When sharing partitions between distros, don't. Any shared partition such as /var /usr /bin all that will be re-formatted and over written by the new installation.

/home is a bit of an exception. You need to take care, but most modern distros will not over write /home. You can share /home, best to use a unique username, and thus a unique /home/user for each distro. This avoids a number of confilcts.

I suggest you use a /data partition. Keep all the system/config/".dot" files for each distro in each distro's /home.

You can then either link or mount --bind directories from /data to /home

ie ln -s /media/Tao/music ~/music
mount --bind /media/Tao/music ~/music 

I usually mount my /data partition be editing fstab POST-INSTALL of a new distro (lessens the chance of having the data partition formatted "accidently" ie by hitting the wrong mouse button).

---

### Post by _r_a_V_a_n_ on 2008-07-17
> **Inxsible said:**
> You cannot have the same boot partition for different OSes. The boot partition is where the info about the kernel is stored. And 32 bit and 64 bit kernels are different. When you installed the 64 bit, i think the 32 bit kernel info was overwritten.

Every OS you install should have different partitions of everything. Swap is the only partition that you can re-use between OSes.


Yup... you were right :)

Anyways, I resolved the problem without having to reinstall the OS.

I was able to load the 32 bit OS in 800*600 mode. I created a sub directory (boot64) inside the boot folder and copied the files under boot (excluding the subdirectories grub and lost+found) into it. Reinstalled the kernel, modified corresponding entries in menu.lst (including the UUIDs and kernel references of 64bit pointing it to the new boot64 folder) and voila... I have dual boot for 32 bit and 64 bit using the common boot partition ;)

Another thing to note here is that... when I installed the 64bit, the UUID for the /boot folder was changed. This caused problems while booting up the 32 bit as the entries in the /etc/fstab file were linking to the old UUID of the /boot folder. Corrected the same and then landed with the 800*600 resolution which now... whew... is fixed!

Thanks guys for your help. You rock! :guitar:

---

