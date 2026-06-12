---
title: "Upgrading to Hardy broke the sound on my wine. HELP!"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Captain Oblivious on 2008-05-04
I had gutsy, and upgraded to hardy. Under Gutsy, the sound would usually work under wine. Now it seems wine doesn't have the right sound drivers. How do I install the correct drivers, and where can  get them.
The sound works great when I'm not using wine.
If it helps, the computer I am using is a Dell Ispiron e1505.

I am a complete noob at installing stuff on linux, so detailed step-by-step instructions are necessary.

---

### Post by daengbo on 2008-05-04
Open Applications > Wine > Configure Wine
Go to the Audio tab and look for the correct plugin to use, probably ESD, PulseAudio, or ALSA (only if the first two don't exist).

I'm sorry I can't be more detailed in my answer, but I'm on vacation and in an internet cafe, so I can't check the menus.
[http://www.winehq.org/site/docs/wineusr-guide/config-wine-main](http://www.winehq.org/site/docs/wineusr-guide/config-wine-main)

---

### Post by peitschie on 2008-05-04
Hi,

The reason the sound broke when upgrading is because Hardy now uses PulseAudio as the default audio driver rather than Alsa.  This allows greater flexibility... but unfortunately wine doesn't support PulseAudio natively, and Hardy isn't set up to create a fake Alsa card by default.

Follow the instructions listed here (to make Alsa output to PulseAudio, then set up Wine (type in 'winecfg and go to the Audio tab') to use the Alsa output driver:

Instructions: [http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_the_ALSA_PulseAudio_plugin](http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_the_ALSA_PulseAudio_plugin)

Post back how you went :-)

---

### Post by Captain Oblivious on 2008-05-05
> **peitschie said:**
> Hi,

The reason the sound broke when upgrading is because Hardy now uses PulseAudio as the default audio driver rather than Alsa.  This allows greater flexibility... but unfortunately wine doesn't support PulseAudio natively, and Hardy isn't set up to create a fake Alsa card by default.

Follow the instructions listed here (to make Alsa output to PulseAudio, then set up Wine (type in 'winecfg and go to the Audio tab') to use the Alsa output driver:

Instructions: [http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_the_ALSA_PulseAudio_plugin](http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_the_ALSA_PulseAudio_plugin)

Post back how you went :-)

I must be doing something wrong, because I can't seem to get past the first line.

```
user@user-laptop:~$ pacman -Sy pulseaudio
The program 'pacman' is currently not installed.  You can install it by typing:
sudo apt-get install pacman
bash: pacman: command not found
user@user-laptop:~$ sudo apt-get install pacman
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
user@user-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
user@user-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
user@user-laptop:~$ 

```

I can only guess that it is related to my inability to add or remove any applications. (upgrading broke that too) System Monitor says I have 4 MB left on my boot partition. Is it because that's not enough room?

Oh, the error I get when trying to add or remove applications is
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by Oldsoldier2003 on 2008-05-05
> **Captain Oblivious said:**
> I must be doing something wrong, because I can't seem to get past the first line.

```
user@user-laptop:~$ pacman -Sy pulseaudio
The program 'pacman' is currently not installed.  You can install it by typing:
sudo apt-get install pacman
bash: pacman: command not found
user@user-laptop:~$ sudo apt-get install pacman
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
user@user-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
user@user-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
user@user-laptop:~$ 

```

I can only guess that it is related to my inability to add or remove any applications. (upgrading broke that too) System Monitor says I have 4 MB left on my boot partition. Is it because that's not enough room?

Oh, the error I get when trying to add or remove applications is
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

```
sudo dpkg --configure -a
``` should fix that problem (the dpkg error). pacman isnt a ubuntu command, the tutorial is for another linux distribution.

---

### Post by Captain Oblivious on 2008-05-05
> **Oldsoldier2003 said:**
> ```
sudo dpkg --configure -a
``` should fix that problem (the dpkg error). pacman isnt a ubuntu command, the tutorial is for another linux distribution.

```
user@user-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
user@user-laptop:~$ 
```

---

### Post by peitschie on 2008-05-05
Oh.  Thats nasty!

How big is your drive?  Can you paste the output of the following commands please?
```

sudo fdisk -l
df -h
mount

```

This will tell us some info about your hard drives and partition setup which may be useful.  

Sorry about the link. I was intending for you only to follow the steps that the page linked to directly (i.e., configuring the Alsa PulseAudio plugin)!  My apologies for not making that more specific :)

---

### Post by Oldsoldier2003 on 2008-05-05
sudo apt-get clean
sudo rm -rf /tmp *
then clear your firefox cache
empty the trash bin and root trash bin
delete unnnecessary logs from /var/log
delete thumbnials form your .thumbnails dir in ~

after doing all this try running sudo dpkg --configure -a again

---

### Post by peitschie on 2008-05-05
You may want to hold off on running the "sudo apt-get clean" command however!  This will remove all cached packages, and from the sounds of things you were interrupted mid-install.  If you removed the cached packages you may need to download them again from the net (depending on how you upgraded).  If your internet bandwidth is very precious to you I would suggest not running apt-get clean yet.

---

### Post by Captain Oblivious on 2008-05-05
> **peitschie said:**
> Oh.  Thats nasty!

How big is your drive?  Can you paste the output of the following commands please?
```

sudo fdisk -l
df -h
mount

```

This will tell us some info about your hard drives and partition setup which may be useful.  

Sorry about the link. I was intending for you only to follow the steps that the page linked to directly (i.e., configuring the Alsa PulseAudio plugin)!  My apologies for not making that more specific :)

```
user@user-laptop:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7        1222     9767520   83  Linux
/dev/sda3            1223        8760    60548985   83  Linux
/dev/sda4            8761        9546     6313545    5  Extended
/dev/sda5            9422        9546     1003968   82  Linux swap / Solaris
/dev/sda6            8761        9421     5309419+  83  Linux

Partition table entries are not in disk order

Disk /dev/mmcblk0: 62 MB, 62390272 bytes
8 heads, 32 sectors/track, 476 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         475       60784    6  FAT16
user@user-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  3.8G  5.0G  44% /
varrun                502M  108K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   64K  501M   1% /dev
devshm                502M   12K  502M   1% /dev/shm
lrm                   502M   38M  464M   8% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1              46M   40M  3.9M  92% /boot
/dev/sda3              57G   49G  5.5G  90% /home
/dev/sda6             5.0G  2.5G  2.4G  51% /var
user@user-laptop:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /boot type ext3 (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sda6 on /var type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
user@user-laptop:~$ 
```

---

### Post by peitschie on 2008-05-05
Oh.  I see your problem:
```

/dev/sda1              46M   40M  3.9M  92% /boot

```

You have almost no space left on your boot partition.  Do you have the Hardy Live CD handy?  What you need to do is to resize your boot partition to probably around 60-70mb.  Note this is a little higher than you might need, mine is only 50Mb, but resizing takes a while so better safe than sorry.

You can do this using the Live CD's Partition Editor (its in system utilities or something like that).  You should be able to resize one of the other partitions on that drive (e.g., /home) WITHOUT losing the data.  Check the prompts carefully though .  If you have any data that is important, back it up before proceeding just in case.

---

### Post by Captain Oblivious on 2008-05-05
> **peitschie said:**
> Oh.  I see your problem:
```

/dev/sda1              46M   40M  3.9M  92% /boot

```

You have almost no space left on your boot partition.  Do you have the Hardy Live CD handy?  What you need to do is to resize your boot partition to probably around 60-70mb.  Note this is a little higher than you might need, mine is only 50Mb, but resizing takes a while so better safe than sorry.

You can do this using the Live CD's Partition Editor (its in system utilities or something like that).  You should be able to resize one of the other partitions on that drive (e.g., /home) WITHOUT losing the data.  Check the prompts carefully though .  If you have any data that is important, back it up before proceeding just in case.

I borrowed a Gutsy Live CD to install, and upgraded to Hardy via the update notifier thing. Would it work if I re-borrowed the Gutsy CD to partition it?

---

### Post by Oldsoldier2003 on 2008-05-05
try getting a  [GParted Live CD]("http://gparted-livecd.tuxfamily.org/"). Its a handy thing to have anyways :)

---

### Post by daengbo on 2008-05-05
You probably have several kernels in your /boot partition. You can remove the old ones to make more space.
> dpkg -l|grep kernel

will find older kernels for you. After that, you can use the package name in 
> sudo dpkg -r <package name>
That should free up enough space to install the new kernel, after which you will be able to clean up better. Be careful not to remove the kernel you are currently running.

---

### Post by daengbo on 2008-05-05
You probably have several kernels in your /boot partition. You can remove the old ones to make more space.
> dpkg -l|grep kernel

will find older kernels for you. After that, you can use the package name in 
> sudo dpkg -r <package name>
That should free up enough space to install the new kernel, after which you will be able to clean up better. Be careful not to remove the kernel you are currently running.

---

### Post by peitschie on 2008-05-05
> **Captain Oblivious said:**
> I borrowed a Gutsy Live CD to install, and upgraded to Hardy via the update notifier thing. Would it work if I re-borrowed the Gutsy CD to partition it?

The Gutsy Live CD should also work just fine.  

The other suggestion about removing old kernels is also a good one, though I suspect it might be a little problematic as with the dpkg system currently still trying to install packages, I suspect you can't remove the old kernels until all the packages have successfully installed... which of course you can't do until you have enough room to install them...  I'd still recommend resizing the partition a bit to help future-proof your system a little better;)

---

### Post by daengbo on 2008-05-05
Removing packages using apt-get doesn't work, but I've used dpkg to unfsck systems quite a few times, so it should work as long as nothing has changed in the last year or so (which it shouldn't have).

---

### Post by Captain Oblivious on 2008-05-10
> **peitschie said:**
> Hi,

The reason the sound broke when upgrading is because Hardy now uses PulseAudio as the default audio driver rather than Alsa.  This allows greater flexibility... but unfortunately wine doesn't support PulseAudio natively, and Hardy isn't set up to create a fake Alsa card by default.

Follow the instructions listed here (to make Alsa output to PulseAudio, then set up Wine (type in 'winecfg and go to the Audio tab') to use the Alsa output driver:

Instructions: [http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_the_ALSA_PulseAudio_plugin](http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_the_ALSA_PulseAudio_plugin)

Post back how you went :-)

Okay, so I finally got 
> sudo dpkg --configure -a
to work and am trying to configure that file. The problem is I can't find /etc/rc.conf or /etc/asound.conf. I think I found the etc folder, but those files don't seem to be in it.:( Am I looking in the right place?
I apologize for asking such stupid questions. Must be frustrating for you to have to keep answering things I should know, but I'm really not very experienced with this whole Ubuntu thing.

---

### Post by peitschie on 2008-05-10
I would never feel offended by these questions.  As long as your learning and not just lazy I have all the time in the world ;) (metaphorically speaking lol).

I'll rephrase whats on the website to make it a little clearer for your :)
Put the following lines in ~/.asoundrc (~ = your home directory)
```

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

See if that helps fix your sound issue.  I will warn you however that pulseaudio doesn't exactly work well with wine at the moment (see [http://www.pulseaudio.org/ticket/198](http://www.pulseaudio.org/ticket/198))

An alternative setup to try is [http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/](http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/)

Best of luck and don't forget to tell us how your experience goes :)

---

### Post by Captain Oblivious on 2008-05-10
```
user@user-laptop:~$ cd .asoundrc
bash: cd: .asoundrc: No such file or directory
```

---

### Post by peitschie on 2008-05-10
Sorry... .asoundrc refers to a file you need to create in your home directory if it doesn't already exist.

So for example, you might open a terminal and enter:
```

gedit ~/.asoundrc &

```

This will open a new Gedit session editing ~/.asoundrc.  The & sign tells the command line to put the task in the background (a different topic for later discussion if you want :))

---

### Post by Captain Oblivious on 2008-05-11
Okay, that was weird. It plays sound with Firefox, but the same sound repeating over and over again, so I took it out.

Still, can't get the voice in Ventrilo to work at all though, but that's probably a completely different problem.

**Update:**
Some of the sounds in Firefox still seem to work after removing those lines. I remember there being music when I visited that same site with Windows before, but that music's still gone. Strange. Could it have been the update I let Ubuntu do this morning? Ventrilo's hasn't changed though.

---

### Post by peitschie on 2008-05-11
The repeating sound... is it the original sound or does it sound like an echo?  This audio business is always annoying to try and work out.  What other applications work with sound currently?

---

### Post by Captain Oblivious on 2008-05-11
> **peitschie said:**
> The repeating sound... is it the original sound or does it sound like an echo?  This audio business is always annoying to try and work out.  What other applications work with sound currently?

Exactly the same sound. It's like a clock ticking.
Oh, and Firefox's sound just suddenly stopped again.

---

### Post by peitschie on 2008-05-12
Hey... I just noticed this on the forums.  Give it a check out and see if any of those steps help :-)

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Don't give up just yet!

---

