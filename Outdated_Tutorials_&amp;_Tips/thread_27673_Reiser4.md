---
title: "Reiser4"
date: 2005-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by waster on 2005-04-17
If you want to add the fast new Reiser4 file system, I think the following method works best with Ubuntu:

Do not use mm kernel patches - there are lots of dangerous things, and conflicts with the ubuntu patches.

Instead, go to:
[ftp://ftp.namesys.com/pub/reiser4-for-2.6/](ftp://ftp.namesys.com/pub/reiser4-for-2.6/)

where you can download a single patch file which applies to the linux-source package you can get from the ubuntu repositories.

In my case:
apt-get install linux-source-2.6.11 (this is the ubuntu pre-patched package)
cd /usr/src
tar -xjf linux-source-2.6.11.tar.bz2
wget [ftp://ftp.namesys.com/pub/reiser4-for-2.6/2.6.11/reiser4-for-2.6.11-3.patch.gz](ftp://ftp.namesys.com/pub/reiser4-for-2.6/2.6.11/reiser4-for-2.6.11-3.patch.gz)
gunzip reiser4-for-2.6.11-3.patch.gz
cd linux-source-2.6.11
patch -p1 < ../reiser4-for-2.6.11-3.patch

The patching should all be successful.

make menuconfig

(you might have to install ncurses libs to make this work. These are suggested/recommended by the linux-source package - look in your package manager to work out exactly what you need)

navigate to file systems, and you should see [ ] Reiser4
set it to be compiled as a module.

then exit, saving changes.

make-kpkg

in the parent directory, there should now be a xxxxx.deb kernel package. Install this using

dpkg -i filename

reboot.

this would probably need untold messing around to have a root reiser4 partition. maybe easier to compile not as a module but into the kernel if you do this, to avoid pissing around with initrd.

Now, can anyone tell me what the best setup would be with RAID and reiser4 partitions. Chunk sizes, and block sizes, etc. for shared media patritions?

Cheers,
Jack

---

### Post by TravisNewman on 2005-04-18
I might add to this, that it's still in development to an extent, and that some have complained of instability and corruption from Reiser4.

That said, I haven't seen any at all. I didn't use Reiser 4 for very long, but it seemed to work just fine.

---

### Post by lonblu on 2005-04-20
Sorry, why not to have a package containing a precompiled module for the specific kernel?  :) 
I need to do a lot of work to manually configure the kernel and I'm never sure it has everything I would ever need. 
If I don't filter the .config I need to spend hours for a kernel compilation.
 ](*,) 

So... Why isn't this module available in the apt repositories?
 :grin:

---

### Post by smokeslikeapoet on 2005-04-21
Just a note as I've helped write/edit some Reiser4 howto's for Gentoo. Unless you want to download a developmental version of Grub, only attempt Reiser4 partitions on systems that you have a separate /boot partition and leave the /boot partion as ext2 or ext3. Also there are known problems to exist compiling certain applications on a Reiser4 partion, so you may want to leave yourself a fallback partion with a different filesystem if you are a developer. Also, formatting Reiser4 is always destructive. There are no tools yet to upgrade any filesystem including Reiser 3, a.k.a reiserfs to reiser4, so you may be stuck with a total system reinstall if you plan on moving to this filesystem.

---

### Post by plb on 2005-04-21
I've had no troubles with Reiser4 and I've been using it for about 6 months (boot is reiserfs)

---

### Post by wavex on 2005-04-21
I've used reiser4 with gentoo a few times. 
The first time might system went corrupt after about two weeks of use. This was awhile ago though. 
I'm using it now with a gentoo system. Wish I never did. Stability seems to be there now but the speed is nothing to brag about. 

I prefer xfs myself. Does ubuntu allow xfs installation?

---

### Post by plb on 2005-04-21
[QUOTE=wavex]I've used reiser4 with gentoo a few times. 
The first time might system went corrupt after about two weeks of use. This was awhile ago though. 
I'm using it now with a gentoo system. Wish I never did. Stability seems to be there now but the speed is nothing to brag about. 

I prefer xfs myself. Does ubuntu allow xfs installation?[/QUOTE]

Not sure, but why not just backup your data and slap xfs on it  :wink:

---

### Post by wavex on 2005-04-22
No room to backup.

---

### Post by dejitarob on 2005-04-22
I use reiser4fs on all four of my boxes with no problems at all. I just formatted with it when I installed off the cd though. This is for the latest version?

---

### Post by jobdrb on 2005-04-22
How could I install reiserfs4 on / . ?

Since ubuntu do note offer reiserfs4 support.

Well, I realy apreciate on way to remake the install cd to use reiserfs4, from instalation time.

How could I do this?


[QUOTE=dejitarob]I use reiser4fs on all four of my boxes with no problems at all. I just formatted with it when I installed off the cd though. This is for the latest version?[/QUOTE]

---

### Post by crazy-flash on 2005-05-03
[QUOTE=jobdrb]How could I install reiserfs4 on / . ?[/QUOTE]

you could install ubuntu in a temporary partition on your harddisk and then create your reiser4 partiton and copy all files over. but i would suggest to use ext2 for the boot partition (don't worry ext2 is the fastest fs as far as i know). also i would compile reiser4 directly into the kernel (not as module).

when installing ubunto choose something like:

hda1 -> /boot (ext2)  (64mb should be more than enough)
hda2 -> swap (swap)
hda3 -> fs doesn't matter yet (this will be your reiser4 partiton later)
hda4 -> / (reiserfs)

for the partition table.

after installing, setup your kernel with reiser 4 support
-format hda3 with reiser4
-copy all files from / to hda3 (without the directory you mounted hda3 on or copiing will never stop ;))
-edit /etc/fstab: change the partition for the mount point "/" from  /dev/hda4 to /dev/hda3 and the filesystem from reiserfs to reiser4
-/boot/grub/menu.lst and change the root parameter for the kernel from /dev/hda4 to /dev/hda3.

that should work, but didn't tested it myself...

---

### Post by crazy-flash on 2005-05-03
need to add:
i do not recommend using reiser4 for / , i used it for almost 6 months now and it worked fine since 2 weeks ago, then f up. it was unmountable, not even fsck could help :(

---

### Post by RastaMahata on 2005-05-03
so what's the best filesystem for linux? I used the default :P

---

### Post by crazy-flash on 2005-05-04
[QUOTE=RastaMahata]so what's the best filesystem for linux? I used the default :P[/QUOTE]
dont know , they all have its advantages and its disadvantages . but i think reiserfs (3 not 4) is a good choice for desktop-computers. i use it since 2 years on 2 computers without any problems. ext3 is also ok.

---

### Post by CyBEr-GaNgE on 2005-05-05
](*,) 
Yesterday it was probably too late at night when I decided to dist-uopgrade my warty to hoary, everything went fine.
Then i got a message telling me to read /usr/share/doc/reiserfs4progs/NEWS.debian
I followed the instructions inside the document and... I corrupted my root partition    :-# 
For my luck it was "just" the root, boot and home are ext3.
So, I will install on my / a Hoary, but I don't know if I'll use reiser4 again...

---

### Post by jdong on 2005-05-07
I used to think reiser4 was stable, until in the middle of processing Backports (binary xdeltas of 10GB's worth of 10-20MB files) the process would randomly freeze.

If I copied everything to a non-reiser4 partition, it'd work, so it seems like a random reiser4 bug.

XFS... I just had an xfs partition die on me for no apparent reason (raid5). :(

---

### Post by mimek on 2005-06-15
I've just installed linux-source-2.6.12 (2.6.11.94-1.1), then patched it with reiser4-for-2.6.11-5.patch.gz and configured it with .config from linux-headers-2.6.10-5-686 (after running make menuconfig I've only enabled reiser4 and changed processor to pentium M )

I'm starting to compile and after few minutes I got this error:
fs/reiser4/page_cache.c: In function `set_page_dirty_internal':
fs/reiser4/page_cache.c:468: error: structure has no member named `memory_backed'

Does anybody know how to fix it?

---

### Post by geearf on 2005-06-24
Hello,

isn't there a way to get a kernel binarie for reiser4, cause i compiled the morph-sources patched kernel, and now i have somme errors at startup, but it still boots..
I guess i did something wrong.

Any help appreciated :)

Although booting gentoo to make a reizer partition is such a hassle :(

---

### Post by Manny C on 2005-06-24
For info with regards to the best filesystem:

[http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/#more-235](http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/#more-235)

Hope that helps.

---

### Post by geearf on 2005-06-24
They do not talk about reiser4, so i am not quite sur if it fits here :(


But between the rest, they go for ext3 as i would too, but now that reiser4 is out i wanna try it :)

---

### Post by jdong on 2005-06-24
[QUOTE=mimek]I've just installed linux-source-2.6.12 (2.6.11.94-1.1), then patched it with reiser4-for-2.6.11-5.patch.gz and configured it with .config from linux-headers-2.6.10-5-686 (after running make menuconfig I've only enabled reiser4 and changed processor to pentium M )

I'm starting to compile and after few minutes I got this error:
fs/reiser4/page_cache.c: In function `set_page_dirty_internal':
fs/reiser4/page_cache.c:468: error: structure has no member named `memory_backed'

Does anybody know how to fix it?[/QUOTE]

Umm..... yeah.... applying a 2.6.11 patch to 2.6.12 usually won't be too successful ;)

Wait for Namesys to release 2.6.12 patches.

---

### Post by Crypto on 2005-07-07
[QUOTE=crazy-flash]you could install ubuntu in a temporary partition on your harddisk and then create your reiser4 partiton and copy all files over. but i would suggest to use ext2 for the boot partition (don't worry ext2 is the fastest fs as far as i know). also i would compile reiser4 directly into the kernel (not as module).

when installing ubunto choose something like:

hda1 -> /boot (ext2)  (64mb should be more than enough)
hda2 -> swap (swap)
hda3 -> fs doesn't matter yet (this will be your reiser4 partiton later)
hda4 -> / (reiserfs)

for the partition table.

after installing, setup your kernel with reiser 4 support
-format hda3 with reiser4
-copy all files from / to hda3 (without the directory you mounted hda3 on or copiing will never stop ;))
-edit /etc/fstab: change the partition for the mount point "/" from  /dev/hda4 to /dev/hda3 and the filesystem from reiserfs to reiser4
-/boot/grub/menu.lst and change the root parameter for the kernel from /dev/hda4 to /dev/hda3.

that should work, but didn't tested it myself...[/QUOTE]


Didn't work (for me) .. see [here](http://ubuntuforums.org/showthread.php?t=47034)  :(

---

