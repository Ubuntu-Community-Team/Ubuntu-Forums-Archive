---
title: "Can't view files"
date: 2021-05-30
forum: New to Ubuntu
---

### Post by pennsylvaniadutch on 2021-05-30
I'm fairly new to Ubuntu and I'm using 20.04 version. I had problems, so I copied all of my important files to an external disk, reinstalled Ubuntu but now I can't read the files. I can see the name, but nothing else. The folders say empty too.

---

### Post by TheFu on 2021-05-30
Which program are you expecting to access these files?  
Can you use a different program? Does that work?
Can you use a terminal and see the files?
What is the file system type?  **df -Th** will show that. Stripe out the lines that aren't for this specific filesystem, please.

A system summary will help.  **inxi -S** is the command that will tell us some minimal information about the environment. Or **inxi -bz** if you want to share a little more information, but the first command would be fine.

Are you familiar with Unix file/directory permissions?
Are you familiar with Snap package constraints?
If the external disk is not using a native Linux file system, file permissions are the likely problem. NTFS, exFAT, FAT32 all will cause this issue. There are solutions, workarounds and complete "fixes." available, but each has pros/cons.  

So, please try to answer each of the questions above. If you don't understand the question, ask. Someone can try to explain why we ask.

---

### Post by pennsylvaniadutch on 2021-06-03
> Which program are you expecting to access these files? I'm using "Files"

> Can you use a different program? Does that work? I don't know what other program to use.

> Can you use a terminal and see the files? I opened a terminal, did a cd Documents, did a find . but it returned no results.

> What is the file system type?  **df -Th** will show that. Stripe out the lines that aren't for this specific filesystem, please.
I did a df -Th and this is the results. I have no idea what this all means. (I truly am a Newbie)
```
$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.7G     0  1.7G   0% /dev
tmpfs          tmpfs     344M  1.9M  342M   1% /run
/dev/nvme0n1p5 ext4       74G   13G   58G  18% /
tmpfs          tmpfs     1.7G     0  1.7G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/loop1     squashfs  256M  256M     0 100% /snap/gnome-3-34-1804/36
/dev/loop2     squashfs   55M   55M     0 100% /snap/core18/1880
/dev/loop3     squashfs  277M  277M     0 100% /snap/gimp/372
/dev/loop4     squashfs   66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop0     squashfs  163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop5     squashfs  219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop6     squashfs   52M   52M     0 100% /snap/snap-store/518
/dev/loop7     squashfs   63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop8     squashfs   33M   33M     0 100% /snap/snapd/11841
/dev/loop10    squashfs   56M   56M     0 100% /snap/core18/2066
/dev/loop9     squashfs   33M   33M     0 100% /snap/snapd/12057
/dev/loop11    squashfs   50M   50M     0 100% /snap/snap-store/467
/dev/nvme0n1p1 vfat       96M   58M   39M  60% /boot/efi
tmpfs          tmpfs     344M   68K  344M   1% /run/user/1000
/dev/sdc       exfat     500G   42G  459G   9% /media/dutch/D8D8-B5C0
```

> A system summary will help.  **inxi -S** is the command that will tell us some minimal information about the environment. Or **inxi -bz** if you want to share a little more information, but the first command would be fine.

```
$ inxi -S
System:
  Host: dutch-Aspire-A515-43 Kernel: 5.8.0-53-generic x86_64 bits: 64 
  Desktop: Gnome 3.36.7 Distro: Ubuntu 20.04.2 LTS (Focal Fossa)
```

---

### Post by TheFu on 2021-06-03
Is this:
```
$ df -Th
Filesystem Type Size Used Avail Use% Mounted on
 /dev/sdc exfat 500G 42G 459G 9% /media/dutch/D8D8-B5C0
```
where you copied or moved all the files?

What that line says is 
**exFAT** is the file system type. That is **not native Linux**. That is a Windows file system. I've never used it and don't know if it is supported by 20.04 automatically or not.  What I mean by that is that drivers may or may not be automatically loaded into the OS to make access to exFAT file systems possible.  If you click on that area in a file manager and it works at all, then exfat support is built-in now.  If it does not work, then you can install the support:
```
sudo apt install exfat-fuse   exfat-utils
```
That should do it. It won't cause harm, at least I don't see why it should.

BTW, "Files" isn't the actual name of the program.  It is just what the menu/icon says.  I suspect the actual program name is something like gnome-files or nautilus.  I don't use Gnome3-Ubuntu, so I can't easily check. Sorry.  I prefer a lighter DE. We all have different tastes, which is 100% fine.

As for the attempt at terminal commands, ouch.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) will help to get your shell-fu up to speed.  
```
cd ~/Docu*
find . 
```
will only show which files/directories are in Documents and below. If the files aren't there, then nothing will show up. If you copied them to the external connected partition, run
```
find /media/dutch/D8D8-B5C0
```
to see what is there. With 42G used, it should be a long list.

Anyways, in a file manager, you'll need to go to /media/dutch/D8D8-B5C0 to see any files that were moved/copied to that  location.

---

### Post by Impavidus on 2021-06-03
I assume the files you seek are on your external drive, not in your home directory and therefore not in your Documents directory either. The external drive uses the exfat filesystem (interestingly, it's not partitioned, but has the filesystem directly on the entire drive). I think support for the exfat filesystem isn't installed by default. Try that first:```
sudo apt update
sudo apt install exfat-fuse exfat-utils
```or use your favourite interface to the package manager to install that software. Also make sure all available upgrades have been installed.

BTW, Files is the file manager. It doesn't actually open the files (other than to read magic numbers), but it can guess the file type and guess which application you want to open the file. Then it starts that application and orders it to open the file.

---

### Post by pennsylvaniadutch on 2021-06-04
Like I said, I'm new to Ubuntu. So a lot of things that are said here are over my head. I just try the things suggested.

I tried this...
sudo apt update
sudo apt install exfat-fuse exfat-utils

But I still can't view the file contents. I'm confused, I can see the file folders, but when I open them, they are empty. When I click on a .jpg file, I get the error message, could not load Image, Error interpreting JPEG image file (Not a JPEG file;starts with 0x00 0x00)

---

### Post by TheFu on 2021-06-04
It is very possible that the file is corrupted.

A proper JPEG file should have a proper header. The "**file**" command from a terminal can show that information:

```
$ file some-image.jpg
some-image.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 800x800, segment length 16, baseline, precision 8, 833x1078, components 3
```

We can come at this a different way.  A nice image browser is **geeqie**.  Install that from the repos, then run it and use the upper left text area to look for the files in the directory.  If the storage is mounted, this tool is fairly good at viewing images and it won't have some limitations that Canonical has decided to put into all snap packages.  Oh - and if offered a version of geeqie that has snap anywhere on the page, that's the wrong one. Only install the one that is an APT package - which is what Ubuntu has used since the beginning and what Debian designed in the 1990s.

More and more, Canonical is installing snap packages because they think our desktops are like our phones. Snaps are all bad. If you keep all your data files under your HOME and HOME isn't an NFS or CIFS mount, which is impossible for many people, then snaps can bring great protections to the computer, OS, and other users at a cost of inconvenience, slower startup times, more storage, and  us having to have this conversation about the issues with snap packages.  You can read more [https://snapcraft.io/docs](https://snapcraft.io/docs) - they will highly the good things about snaps, which I have ignored.

And just to be fair, I don't really know which program you are using called "Files" nor whether it is a debian package or a snap package.  If it isn't a snap, then ignore all the snap stuff I've written. It doesn't apply.

---

### Post by scorp123 on 2021-06-04
> **pennsylvaniadutch said:**
>   so I copied all of my important files to an external disk ...

How exactly did you perform the copy? And how did you perform the removal of the disk e.g. when you thought the copying was done? Did you just pull it out ... or did you click an *"Eject"* button somewhere and you waited with the pulling out until the OS told you it was safe to do so?

---

### Post by WA4MOE on 2021-06-08
I too am Pa Dutch, trying to learn Ubuntu and command line. 
Moe G

---

