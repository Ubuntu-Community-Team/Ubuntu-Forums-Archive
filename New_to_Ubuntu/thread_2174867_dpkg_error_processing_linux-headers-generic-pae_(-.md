---
title: "dpkg: error processing linux-headers-generic-pae (--configure)"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by zgur on 2013-09-16
Hey,
I need some help and I am an absolute beginner in this. My computer can not find any wireless connections, it suddenly stopped working. At the same time (I dont know if its related) I noticed that the space was full on my computer (partitioned into 4), I cleaned it now but I cant delete any programs because I have to repaire something first (I dont understand what it is but it say so everytime I try). But, I cant repaire this thing because I get this: 

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 621428 files and directories currently installed.) 
Unpacking linux-headers-3.5.0-40 (from .../linux-headers-3.5.0-40_3.5.0-40.62_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-40_3.5.0-40.62_all.deb (--unpack): 
 unable to create `/usr/src/linux-headers-3.5.0-40/arch/m32r/include/asm/sections.h.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-40/arch/m32r/include/asm/sections.h'): No space left on device 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Unpacking linux-headers-3.5.0-40-generic (from .../linux-headers-3.5.0-40-generic_3.5.0-40.62_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-40-generic_3.5.0-40.62_i386.deb (--unpack): 
 unable to create `/usr/src/linux-headers-3.5.0-40-generic/include/config/usb/r8a66597.h.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-40-generic/include/config/usb/r8a66597.h'): No space left on device 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-headers-3.5.0-40_3.5.0-40.62_all.deb 
 /var/cache/apt/archives/linux-headers-3.5.0-40-generic_3.5.0-40.62_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of linux-headers-generic: 
 linux-headers-generic depends on linux-headers-3.5.0-40-generic; however: 
  Package linux-headers-3.5.0-40-generic is not installed. 
 
dpkg: error processing linux-headers-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-headers-generic-pae: 
 linux-headers-generic-pae depends on linux-headers-generic; however: 
  Package linux-headers-generic is not configured yet. 
 
dpkg: error processing linux-headers-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-headers-generic; however: 
  Package linux-headers-generic is not configured yet. 
 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 

Do anyone know what this mean? and how I solve it?

Thank you in advance!!

---

### Post by Impavidus on 2013-09-16
It appears that the partition with /usr/src is full. Best to find out why. See [here]("http://ubuntuforums.org/showthread.php?t=1122670") for the way to troubleshoot this. Report back when you can't solve your problem with the information given there and show us the results from the commands given there (the problem is probably point 6a, 6d or 6f). Better to ask than to guess and cause even more trouble.

Post any output in code tags. This is better readable.

When we've solved the disk space problem we can target the wifi problem.

---

### Post by ibjsb4 on 2013-09-16
Something else to check is your /boot.  It may be full.

> unable to create  `/usr/src/linux-headers-3.5.0-40/arch/m32r/include/asm/sections.h.dpkg-new'  (while processing  `./usr/src/linux-headers-3.5.0-40/arch/m32r/include/asm/sections.h'): [COLOR=#ff0000]No  space left on device [/COLOR]
No apport report written because MaxReports is reached already

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
ls /boot
```

If you have several kernels there, you need to remove the old ones.  If your not sure, please post the output of that command.

There are several ways to remove old kernels.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

One of the easiest ways is with [Ubuntu Tweak]("http://ubuntu-tweak.com/")

---

### Post by zgur on 2013-09-20
Thank you so much for the reply! But I dont really understand the descriptions in the link., and Im afraid of moving the kernel Im using, because I really dont know what Im doing. I tried to download Ubuntu Tweak that you mentioned but the programcentral says that it cant be installed because I have to repair something (as before) first. 
The terminal says:

:~$ ls /boot
abi-3.5.0-17-generic         initrd.img-3.5.0-30-generic
abi-3.5.0-19-generic         initrd.img-3.5.0-31-generic
abi-3.5.0-21-generic         initrd.img-3.5.0-32-generic
abi-3.5.0-22-generic         initrd.img-3.5.0-34-generic
abi-3.5.0-23-generic         initrd.img-3.5.0-36-generic
abi-3.5.0-25-generic         initrd.img-3.5.0-37-generic
abi-3.5.0-26-generic         initrd.img-3.5.0-39-generic
abi-3.5.0-27-generic         initrd.img-3.5.0-40-generic
abi-3.5.0-28-generic         memtest86+.bin
abi-3.5.0-30-generic         memtest86+_multiboot.bin
abi-3.5.0-31-generic         System.map-3.5.0-17-generic
abi-3.5.0-32-generic         System.map-3.5.0-19-generic
abi-3.5.0-34-generic         System.map-3.5.0-21-generic
abi-3.5.0-36-generic         System.map-3.5.0-22-generic
abi-3.5.0-37-generic         System.map-3.5.0-23-generic
abi-3.5.0-39-generic         System.map-3.5.0-25-generic
abi-3.5.0-40-generic         System.map-3.5.0-26-generic
config-3.5.0-17-generic      System.map-3.5.0-27-generic
config-3.5.0-19-generic      System.map-3.5.0-28-generic
config-3.5.0-21-generic      System.map-3.5.0-30-generic
config-3.5.0-22-generic      System.map-3.5.0-31-generic
config-3.5.0-23-generic      System.map-3.5.0-32-generic
config-3.5.0-25-generic      System.map-3.5.0-34-generic
config-3.5.0-26-generic      System.map-3.5.0-36-generic
config-3.5.0-27-generic      System.map-3.5.0-37-generic
config-3.5.0-28-generic      System.map-3.5.0-39-generic
config-3.5.0-30-generic      System.map-3.5.0-40-generic
config-3.5.0-31-generic      vmlinuz-3.5.0-17-generic
config-3.5.0-32-generic      vmlinuz-3.5.0-19-generic
config-3.5.0-34-generic      vmlinuz-3.5.0-21-generic
config-3.5.0-36-generic      vmlinuz-3.5.0-22-generic
config-3.5.0-37-generic      vmlinuz-3.5.0-23-generic
config-3.5.0-39-generic      vmlinuz-3.5.0-25-generic
config-3.5.0-40-generic      vmlinuz-3.5.0-26-generic
extlinux                     vmlinuz-3.5.0-27-generic
grub                         vmlinuz-3.5.0-28-generic
initrd.img-3.5.0-17-generic  vmlinuz-3.5.0-30-generic
initrd.img-3.5.0-19-generic  vmlinuz-3.5.0-31-generic
initrd.img-3.5.0-21-generic  vmlinuz-3.5.0-32-generic
initrd.img-3.5.0-22-generic  vmlinuz-3.5.0-34-generic
initrd.img-3.5.0-23-generic  vmlinuz-3.5.0-36-generic
initrd.img-3.5.0-25-generic  vmlinuz-3.5.0-37-generic
initrd.img-3.5.0-26-generic  vmlinuz-3.5.0-39-generic
initrd.img-3.5.0-27-generic  vmlinuz-3.5.0-40-generic
initrd.img-3.5.0-28-generic


Thanks again :)

---

### Post by zgur on 2013-09-20
I tried 
sudo apt-get autoremove linux-image-3.5.0-17-generic linux-image-3.5.0-19-generic etc. 

But I doesnt work. My terminal is in swedish but Ill try to translate :) I get something like:  

skogsmulle@skogen:~$ sudo apt-get autoremove linux-image-3.5.0-17-generic linux-image-3.5.0-19-generic
[sudo] password for skogsmulle: 
Reading paketlists... Done
Building dependency tree         
Reading stateinformation... Done
You should try "apt-get -f install" to correct these:
The following pakets have depenency that can not be satisfied:
 linux-headers-generic : depended of: linux-headers-3.5.0-40-generic but will not be installed
 linux-image-extra-3.5.0-17-generic : depended of: linux-image-3.5.0-17-generic but will not be installed linux-image-extra-3.5.0-19-generic 
: depended of: linux-image-3.5.0-19-generic but will not be installed 
E: Unsatisfied values/dependencies. Try "apt-get -f install" without paket (or define other solution).
skogsmulle@skogen:~$

I did 6c,6d, 6e and 6f but I dont see any .gz files, and I dont know what the others are, so I didnt remove them. I tried 6a, with the kernels, but it seems like I dont have space enough to install synaptic. And I dont now what the "/usr/src" is, its seems like it contains a lot of "linux headers" and "linux-headers generic", whats that? Can I delete them? (I see them in my disc-analyzer, and there is a "remove"-option) Otherwise, Im a bit scared of resizing my partitions, if that is the alternative. 

I can still not delete any kind of program, it asks me if Im using a third-part program. If I could, I would save a lot of space

---

### Post by Impavidus on 2013-09-20
When you get the package manager working again you can uninstall all packages with version numbers 3.5.0-17 to 3.5.0-37. If you weren't using the latest one you'd know. This will just keep one old version as a backup.

But first your package manager must work again. Try```
df -Th
sudo du --max-depth=2 / | sort -n | tail -n20
```
This should tell more about your partitions, which one is full and where your big directories are. The second command may take some time to run. When you've found a large directory you can try replacing the / in that command with the name of the large directory (including the / at the beginning) and run it again to zero in on the offending directory. If there is one, of course.

Don't bother translating the swedish. We know the column headings well enough to understand anyway.

---

### Post by zgur on 2013-09-20
From the first command:
Filsystem      Typ      Storlek Använt Ledigt Anv% Monterat på
/dev/sda6      ext4        9,8G   8,5G   778M  92%   /
udev           devtmpfs    1,5G   4,0K   1,5G   1%    /dev
tmpfs          tmpfs       597M  1016K   596M   1%   /run
none           tmpfs       5,0M      0       5,0M   0%   /run/lock
none           tmpfs       1,5G   156K   1,5G   1%     /run/shm
none           tmpfs       100M    48K   100M   1%    /run/user
/dev/sda5      ext4         65G    25G    37G  41%    /home
/dev/sda2      fuseblk      69G    48G    21G  71%   /media/skogsmulle/ddrev

From the second, it says I dont have access and that the file or catalog doesnt exists:
(no access)
du: kan inte komma åt &#8221;/run/user/skogsmulle/gvfs&#8221;: Åtkomst nekas
du: kan inte komma åt &#8221;/proc/17122/task/17122/fd/4&#8221;: Filen eller katalogen finns inte
du: kan inte komma åt &#8221;/proc/17122/task/17122/fdinfo/4&#8221;: Filen eller katalogen finns inte
du: kan inte komma åt &#8221;/proc/17122/fd/4&#8221;: Filen eller katalogen finns inte
du: kan inte komma åt &#8221;/proc/17122/fdinfo/4&#8221;: Filen eller katalogen finns inte
141080    /opt/google
181108    /opt/Adobe
230024    /var/cache
268664    /usr/bin
310212    /var/lib
335904    /opt
395112    /home/jon
405084    /boot
575700    /var
1547140    /usr/share
1629428    /usr/src
1814368    /usr/lib
1984040    /lib/modules
2064600    /lib
5340140    /usr
25499412    /home/skogsmulle
25894544    /home
50079608    /media/skogsmulle
50079616    /media
84733436    /
skogsmulle@skogen:~$ 

I dont undestand what this means: "try replacing the / in that command with the name of the large directory  (including the / at the beginning) and run it again to zero in on the  offending directory". I dont think i interpreted it rights but I tried this anyway: sudo du --max-depth=2 /dev/sda6 | sort -n | tail -n20 and got:
0    /dev/sda6

---

### Post by zgur on 2013-09-21
Do you think I can try this?: 
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

---

### Post by Impavidus on 2013-09-21
I meant that is for example /usr/src were very large, you could have tried **sudo du --max-depth=2 /usr/src ...** to find which directory in /usr/src was large.

Your root directory is full. Your root partition isn't particularly large. I usually recommend a larger root partition, but since you already have it like this it's best to keep it this small until you need to reinstall or upgrade to a new Ubuntu anyway. The oversized directories are /usr/src and /lib/modules. Both contain data from each kernel version you have installed, so removing some old kernels should work.

I think that complicated command will try to uninstall old kernels. It's difficult to check, but if you got it from this forum it's probably safe. But as long as your package manager is in an inconsistent state it may not work. In that case, delete some files from /boot, /usr/src or /lib/modules. Only delete files with old version numbers or from directories with old version numbers and make sure you really delete them, not send them to trash. Use the **sudo rm** terminal command or use shift-delete in the graphical file manager. This should give you a GB of extra free space. Next try to repair your package system with **sudo apt-get -f install** and then properly uninstall the old kernel and header packages. Old is anything with version numbers below 3.5.0-38.

Your root partition will remain tight so you'll have to keep an eye on it. Uninstall old kernels and headers after each kernel update. Delete things you don't need anymore.

---

### Post by zgur on 2013-09-22
I dont understand how I should delete the files, and how I can see what size they are. I tried the sudo rm, but it says that the catalog doesnt exists. I tried rm -r -f, but I dont really know what it means and it didnt work. I dont think I have a graphical file manager on my computer, cant find it, so think I have to do it in the terminal.
 
```
skogsmulle@skogen:~$ sudo du --max-depth=2 /usr/src | sort -n | tail -n20
[sudo] password for skogsmulle: 
48648    /usr/src/linux-headers-3.5.0-37/arch
48648    /usr/src/linux-headers-3.5.0-39/arch
48980    /usr/src/linux-headers-3.5.0-25/arch
89856    /usr/src/linux-headers-3.5.0-17
89912    /usr/src/linux-headers-3.5.0-19
89948    /usr/src/linux-headers-3.5.0-22
89948    /usr/src/linux-headers-3.5.0-23
89956    /usr/src/linux-headers-3.5.0-21
89992    /usr/src/linux-headers-3.5.0-30
89996    /usr/src/linux-headers-3.5.0-28
89996    /usr/src/linux-headers-3.5.0-31
89996    /usr/src/linux-headers-3.5.0-36
90000    /usr/src/linux-headers-3.5.0-27
90000    /usr/src/linux-headers-3.5.0-34
90004    /usr/src/linux-headers-3.5.0-26
90004    /usr/src/linux-headers-3.5.0-32
90008    /usr/src/linux-headers-3.5.0-39
90012    /usr/src/linux-headers-3.5.0-37
90524    /usr/src/linux-headers-3.5.0-25
1629428    /usr/src
skogsmulle@skogen:~$ ls /usr/src
bcmwl-5.100.82.112+bdcom        linux-headers-3.5.0-28
linux-headers-3.5.0-17          linux-headers-3.5.0-28-generic
linux-headers-3.5.0-17-generic  linux-headers-3.5.0-30
linux-headers-3.5.0-19          linux-headers-3.5.0-30-generic
linux-headers-3.5.0-19-generic  linux-headers-3.5.0-31
linux-headers-3.5.0-21          linux-headers-3.5.0-31-generic
linux-headers-3.5.0-21-generic  linux-headers-3.5.0-32
linux-headers-3.5.0-22          linux-headers-3.5.0-32-generic
linux-headers-3.5.0-22-generic  linux-headers-3.5.0-34
linux-headers-3.5.0-23          linux-headers-3.5.0-34-generic
linux-headers-3.5.0-23-generic  linux-headers-3.5.0-36
linux-headers-3.5.0-25          linux-headers-3.5.0-36-generic
linux-headers-3.5.0-25-generic  linux-headers-3.5.0-37
linux-headers-3.5.0-26          linux-headers-3.5.0-37-generic
linux-headers-3.5.0-26-generic  linux-headers-3.5.0-39
linux-headers-3.5.0-27          linux-headers-3.5.0-39-generic
linux-headers-3.5.0-27-generic
skogsmulle@skogen:~$ sudo rm linux-headers-3.5.0-17
[sudo] password for skogsmulle: 
Sorry, try again.
[sudo] password for skogsmulle: 
rm: kan inte ta bort ”linux-headers-3.5.0-17”: Filen eller katalogen finns inte
skogsmulle@skogen:~$ 
skogsmulle@skogen:~$ sudo rm -r -f linux-headers-3.5.0-17
skogsmulle@skogen:~$ sudo rm -r -f linux-headers-3.5.0-17/
skogsmulle@skogen:~$ 


```

I appreciate your help although Im asking over and over again because I dont understand much. I really like ubuntu, but its hard when things like this comes up sometimes, and I dont know anything about programming and codes. Thank you!

---

### Post by Impavidus on 2013-09-22
OK. First we have to make sure which kernel you're running. Use the command ```
uname -r
```If this returns something with 3.5.0-37, 3.5.0-39 or 3.5.0-40 you can continue.

Next we'll try to delete some files that you don't need anymore. To begin with delete some old headers. Use```
sudo rm -rf /usr/src/linux-headers-3.5.0-{17,19,21,22,23,{25..28},30,31,32,34,36}{,-generic}
```
Next use```
sudo rm -rf /lib/modules/3.5.0-{17,19,21,22,23,{25..28},30,31,32,34,36}*
sudo rm /boot/*-3.5.0-{17,19,21,22,23,{25..28},30,31,32,34,36}-generic
```

Next repair the package system.```
sudo atp-get -f install
```This should properly install linux-headers-3.5.0-40.

Finally properly uninstall the kernels and headers whose files you already deleted.```
sudo apt-get purge linux-{headers,image}-3.5.0-{17,19,21,22,23,{25..28},30,31,32,34,36}.*
```

---

### Post by ibjsb4 on 2013-09-22
> **zgur said:**
> Do you think I can try this?: 
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

You found that here

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users)

It will remove all but the kernel you are running, which is what you want.

---

### Post by zgur on 2013-09-22
yes thats were I found it, but as Impavidus wrote, it didnt work because something was wrong with package manager, didnt have enough space I think.

But it works now!!!!! :P:P Thank you so much!!

```
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
dkms: removing: bcmwl 5.100.82.112+bdcom (3.5.0-27-generic) (i686)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.112+bdcom
Kernel:  3.5.0-27-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-27-generic/
/usr/sbin/dkms: rad 1616: cd: /lib/modules/3.5.0-27-generic: Filen eller katalogen finns inte
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-3.5.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
Tar bort linux-image-extra-3.5.0-28-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-extra-3.5.0-28-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
Tar bort linux-image-3.5.0-28-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
dkms: removing: bcmwl 5.100.82.112+bdcom (3.5.0-28-generic) (i686)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.112+bdcom
Kernel:  3.5.0-28-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-28-generic/
/usr/sbin/dkms: rad 1616: cd: /lib/modules/3.5.0-28-generic: Filen eller katalogen finns inte
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-3.5.0-28-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
Tar bort linux-image-extra-3.5.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-extra-3.5.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
Tar bort linux-image-3.5.0-30-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
dkms: removing: bcmwl 5.100.82.112+bdcom (3.5.0-30-generic) (i686)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.112+bdcom
Kernel:  3.5.0-30-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-30-generic/
/usr/sbin/dkms: rad 1616: cd: /lib/modules/3.5.0-30-generic: Filen eller katalogen finns inte
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-3.5.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
Tar bort linux-image-extra-3.5.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-extra-3.5.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
Tar bort linux-image-3.5.0-31-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
dkms: removing: bcmwl 5.100.82.112+bdcom (3.5.0-31-generic) (i686)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.112+bdcom
Kernel:  3.5.0-31-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-31-generic/
/usr/sbin/dkms: rad 1616: cd: /lib/modules/3.5.0-31-generic: Filen eller katalogen finns inte
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-3.5.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
Tar bort linux-image-extra-3.5.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-extra-3.5.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
Tar bort linux-image-3.5.0-32-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
dkms: removing: bcmwl 5.100.82.112+bdcom (3.5.0-32-generic) (i686)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.112+bdcom
Kernel:  3.5.0-32-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-32-generic/
/usr/sbin/dkms: rad 1616: cd: /lib/modules/3.5.0-32-generic: Filen eller katalogen finns inte
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-3.5.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
Tar bort linux-image-extra-3.5.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-extra-3.5.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
Tar bort linux-image-3.5.0-34-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
dkms: removing: bcmwl 5.100.82.112+bdcom (3.5.0-34-generic) (i686)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.112+bdcom
Kernel:  3.5.0-34-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-34-generic/
/usr/sbin/dkms: rad 1616: cd: /lib/modules/3.5.0-34-generic: Filen eller katalogen finns inte
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-3.5.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
Tar bort linux-image-extra-3.5.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-extra-3.5.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Tar bort linux-image-3.5.0-36-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
dkms: removing: bcmwl 5.100.82.112+bdcom (3.5.0-36-generic) (i686)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.112+bdcom
Kernel:  3.5.0-36-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-36-generic/
/usr/sbin/dkms: rad 1616: cd: /lib/modules/3.5.0-36-generic: Filen eller katalogen finns inte
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Genererar grub.cfg ...
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-40-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-40-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-39-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-39-generic
Hittade linux-avbildning: /boot/vmlinuz-3.5.0-37-generic
Hittade initrd-avbildning: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
färdigt
Raderar konfigurationsfiler för linux-image-3.5.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
skogsmulle@skogen:~$ 
 
```

and now my wireless internet works as well  :)

---

### Post by Impavidus on 2013-09-22
Always nice to see a problem solved with my help. It makes me feel important.;)

---

