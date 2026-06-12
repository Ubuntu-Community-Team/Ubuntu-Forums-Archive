---
title: "Update problems - boot partition size?"
date: 2014-10-13
forum: New to Ubuntu
---

### Post by hatfield2 on 2014-10-13
Hello all

I've had Server 14.04 installed for a couple of months.  Daily aptitude updates and aptitude upgrades have been problem free until a few days ago when I've started getting error messages which finish with a message that errors were encountered while processing linux-image-extra-3.13.0-37-generic; linux-image-generic and linux-generic.

The first part of the terminal read out is as follows
   ```
xxxxx@xxxxxx:~$ sudo dpkg --configure -a  

 Setting up linux-image-extra-3.13.0-37-generic (3.13.0-37.64) ...  
 Running depmod.  
 update-initramfs: deferring update (hook will be called later)  
 initrd.img(/boot/initrd.img-3.13.0-37-generic 
 ) points to /boot/initrd.img-3.13.0-37-generic  
  (/boot/initrd.img-3.13.0-37-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.13.0-37-generic.postinst line 491.  
 vmlinuz(/boot/vmlinuz-3.13.0-37-generic 
 ) points to /boot/vmlinuz-3.13.0-37-generic  
  (/boot/vmlinuz-3.13.0-37-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.13.0-37-generic.postinst line 491.  
 Examining /etc/kernel/postinst.d.  
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic  
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic  
 update-initramfs: Generating /boot/initrd.img-3.13.0-37-generic  
 
  gzip: stdout: No space left on device  
  E: mkinitramfs failure cpio 141 gzip 1  

```

Whilst searching on the web for the gzip error I came across some posts which suggested thet my boot partition may be too small - df gives the following:
```

xxxxx@xxxxxx:~$ df
Filesystem                  1K-blocks    Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root [151392436 3410288]("tel:151392436 3410288") 140268768   3% /
none                                4       0         4   0% /sys/fs/cgroup
udev                          [1021556]("tel:1021556")       4   [1021552]("tel:1021552")   1% /dev
tmpfs                          206320     548    205772   1% /run
none                             5120       0      5120   0% /run/lock
none                          [1031584]("tel:1031584")       0   [1031584]("tel:1031584")   0% /run/shm
none                           102400       0    102400   0% /run/user
/dev/sda1                      240972  240693         0 100% /boot
```

My current kernel is:
```
xxxxx@xxxxxx:~$ cat /proc/version
Linux version 3.13.0-37-generic  (buildd@roseapple) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) )  #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014
```
but there appear to be the following kernels on the system:
```
xxxxx@xxxxxx:~$ dpkg -l 'linux-image-*' | grep '^ii'
ii  linux-image-3.13.0-24-generic       3.13.0-24.47                  i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-30-generic       3.13.0-30.55                  i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-32-generic       3.13.0-32.57                  i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-33-generic       3.13.0-33.58                  i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic       3.13.0-34.60                  i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic       3.13.0-35.62                  i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-36-generic       3.13.0-36.63                  i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-37-generic       3.13.0-37.64                  i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic 3.13.0-24.47                  i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic 3.13.0-30.55                  i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                  i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic 3.13.0-33.58                  i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic 3.13.0-34.60                  i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic 3.13.0-35.62                  i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic 3.13.0-36.63                  i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
```


[LIST]
[*]Can I remove the 24, 30, 32, 33, 34, 35 and 36 ones? Or should I leave #36 but remove all the others?
[*]What size should the boot partition be?  I can't remember whether I messed about with the partitions when I installed 14.04 or whether I just accepted the defaults.#-o
[*]Do I need to worry about the following messages?:
[/LIST]
 ```
 initrd.img(/boot/initrd.img-3.13.0-37-generic 
 ) points to /boot/initrd.img-3.13.0-37-generic  
  (/boot/initrd.img-3.13.0-37-generic) -- doing nothing at  /var/lib/dpkg/info/linux-image-extra-3.13.0-37-generic.postinst line  491.  
 vmlinuz(/boot/vmlinuz-3.13.0-37-generic 
 ) points to /boot/vmlinuz-3.13.0-37-generic  
  (/boot/vmlinuz-3.13.0-37-generic) -- doing nothing at  /var/lib/dpkg/info/linux-image-extra-3.13.0-37-generic.postinst line  491.  
```

---

### Post by Bashing-om on 2014-10-13
hatfield2; Hi !

At 100% capacity I do not know that apt-get has the operating head room, but
try:
```

sudo apt-get autoremove

``` which now has the ability to remove old kernels.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-10-13
And if the autoremove command does not do the job you may have to remove the kernels 3.13.0-24 and up to and including 3.13.0-35 with ```
sudo apt-get purge linux-image-3.13.0-24-generic
```leaving just the last two versions, 36 and 37.

I have looked for a way of removing a range of versions, ie in your case 24 - 35,  to remove them all together but so far not been able to find out if it is possible.  I'm sure there must be a way?  
Anybody know?  
Using **man apt-get** has not helped

---

### Post by hatfield2 on 2014-10-13
Hi Bashing-om and ajgreeny

Thanks for your replies.  Autoremove did the trick and didn't seem to be bothered by my boot partition being at 100% thankfully.  My boot partition is now down to 30% and I'll try and remember to keep an eye on it in for more old kernels building up.  

I've now done another sudo aptitide update and sudo aptitide upgrade and all is well.

Thanks again for the help and comments.

---

### Post by Bashing-om on 2014-10-13
@ajgreeny

Maybe something like:
```

sudo dpkg -P linux-image-3.13.0-{24,30,32,33,34,35}-generic
sudo dpkg -P linux-headers-3.13.0-{24,30,32,33,34,35}
sudo dpkg -P linux-headers-3.13.0-{24,30,32,33,34,35}-generic

```
I have employed in difficult situations, however with the advent of "linux-image-extra" I do not know how these images are utilized ->
And quite frankly I am not sure how to handle the "linux-image-extra" files as to the proper order to remove them.

@hatfield2; If the "autoremove' fails we can try this and play about, see what does work !

[INDENT][INDENT]I am all for correcting my think'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-13
hatfield2; Hey Hey !

> **hatfield2 said:**
> Hi Bashing-om and ajgreeny

Thanks for your replies.  Autoremove did the trick and didn't seem to be bothered by my boot partition being at 100% thankfully.  My boot partition is now down to 30% and I'll try and remember to keep an eye on it in for more old kernels building up.  

I've now done another sudo aptitide update and sudo aptitide upgrade and all is well.

Thanks again for the help and comments.

Quite welcome, pleased to be of some small assistance.
Glad it worked out ! .. Good to know that "apt-get autoremove" was able to function in this situation.

'til the next time
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by Michael_McKenney on 2014-10-13
I wished the auto remove would clean up the unneeded 3.13 files for us.  I leave them so I don't break it again.  I can't find documentation on what to keep.  I wish the files were concurrent full versions instead of delta files.

---

### Post by Bashing-om on 2014-10-13
Michael_McKenney; Hello.

As this thread is solved, and your situation is abnormal I do suggest that you start your own thread. A new thread will garner a wider audience !
In the new thread include the out put of terminal command:
```

dpkg -l | grep linux-

```

I will look for the new thread, and
[INDENT][INDENT][INDENT]we see what we can do
[/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-10-13
> **Bashing-om said:**
> @ajgreeny

Maybe something like:
```

sudo dpkg -P linux-image-3.13.0-{24,30,32,33,34,35}-generic
sudo dpkg -P linux-headers-3.13.0-{24,30,32,33,34,35}
sudo dpkg -P linux-headers-3.13.0-{24,30,32,33,34,35}-generic

```
I have employed in difficult situations, however with the advent of "linux-image-extra" I do not know how these images are utilized ->
And quite frankly I am not sure how to handle the "linux-image-extra" files as to the proper order to remove them.

@hatfield2; If the "autoremove' fails we can try this and play about, see what does work !
[INDENT][INDENT]I am all for correcting my think'n
[/INDENT]
[/INDENT]

Thanks for that info.  I did look at **man dpkg** after **man apt-get** but still did not pick up that detail of using a range of versions.
Very useful!

---

### Post by Bashing-om on 2014-10-13
AJ;

> **ajgreeny said:**
> Thanks for that info.  I did look at **man dpkg** after **man apt-get** but still did not pick up that detail of using a range of versions.
Very useful!
:) just my bit to try and help

---

