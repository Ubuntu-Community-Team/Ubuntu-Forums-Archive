---
title: "upgrade problem -no space message"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by Rrory on 2014-12-13
Clicked on the software updater and received this: 

*The upgrade needs a total of 79.9 M free space on disk '/boot'. Please free at least an additional 9,109 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.*
 

 Anyway I emptied the garbage and did the sudo apt-get clean and I still get the same message. I checked my disk usage analyser and it says on the " / "   file my usage is 100%. At the same time it says it could not scan the entire file as *Permission Denied * What is that file? Could this be due to my machine coming with WIndows and I created a separate boot (not from the UEFA)  (my laptop now only has Ubuntu)

I'm really mystified. As when I look at the disc usage  7.9 GB/733.8GB  I've only a tiny amount of usage. I don't have any games or films on my computer...Help!
Rory

---

### Post by deadflowr on 2014-12-13
The best possibility is that the boot partition that was created is tiny.
```
df -h
```
will show the sizes of all mounted partitions and their usages.
You'll most likely need to clean up a few older kernels, if you even have any; besides the running kernel the machine uses.
You might luck out if by chance you have more than one kernel on the machine and you try
```
sudo apt-get autoremove
```
which might clear out older not-in-use kernels.
If not, also 
```
ls /boot
```
should show what is in boot, and how many kernels you may have.

(I would not recommend deleting the files from boot directly, but would instead recommend looking for the package name for the files, which in the case of kernels are the linux-image-some-number-here packages. I would also recommend looking for the corresponding linux-headers-some-number-here packages.)

For a clearer response post the output for both the ls /boot, and the df -h commands

---

### Post by Rrory on 2014-12-13
wow thanks:
df  -h command has this:
ilesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  684G  7.4G  642G   2% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.7G  4.0K  1.7G   1% /dev
tmpfs                        334M 1020K  333M   1% /run
none                         5.0M  4.0K  5.0M   1% /run/lock
none                         1.7G   37M  1.6G   3% /run/shm
none                         100M   52K  100M   1% /run/user
/dev/sda2                    237M  157M   68M  70% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi

then ls  /boot  this: when I try and paste it here it wont I get 'blockable items on current page'....but there 4 abi, 4 config, efi, grub,4 initrd, and lost and found if this makes sense...

---

### Post by deadflowr on 2014-12-13
**I will preface this that I have no experience with an efi boot partition so don't know what it entails but**

I've had great success removing old kernels using these commands
First this one
[COLOR=#000000][FONT=courier bold]```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove
```
this first command will do a dry-run and show you what kernels and packages will be remove, a good way tosee and make sure that it does not remove anything by accident.
Then the second command
[/FONT][/COLOR]```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
```Will do the actual package removal.
You can get a breakdown of the command here
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Also to see the current running kernel try
```
uname -r
```
and remember which number it shows, and look over the output from the first command to make sure that that number version is not listed. Which from my own experience, it never has.

Seeing as you have 4 kernel version I would expect 3 to be removable. Which I would guess should free up a little bit of space, or at least a little breathing room.
Hope this helps.
Hopefully someone with more knowledge on efi partitions and the like can give you even better advice, if need be.

---

### Post by Rrory on 2014-12-13
Okay, that was extremely helpful and your instructions were easy to follows. So now I have
dev/sda2                    237M   85M  140M  38% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi


Can I resize my EFI partition?  Have I ruined my laptop?

---

### Post by deadflowr on 2014-12-17
Have you rebooted after the kernel cleanup?
I think that is the most important thing first. To make sure that nothing wrong happened in the cleanup.
Also, I do not know what to do about the efi partition, sorry.

---

### Post by Rrory on 2015-02-25
I eliminated the extra kernals but today when I tried to upgrade I got the message that I had no space. ....I did clean it up a bit but here is my worrying situation

sda 2  size:237 MB  avail: 65 MB  use: 72%
sda1   size: 511MB avail: 508 M    use: 1%/boot/ efi
 
 can I resize the partitions? Do I need to reboot....  Heeelp please

---

### Post by Impavidus on 2015-02-26
This is a recurring problem. Every time after a few kernel upgrades the /boot partition will be full. Try cleaning old kernels again. I always clean old kernels, so I never have more than three installed – and I don't even have a /boot partition to worry about.

If you make your /boot partition bigger, it will take longer before it's full again. But that would probably require shrinking LVM partitions, which is a complication, besides the usual difficulties and risks of partition resizing.

---

