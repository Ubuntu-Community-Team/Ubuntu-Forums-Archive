---
title: "no disk space; ubuntu on chromebook"
date: 2014-10-22
forum: New to Ubuntu
---

### Post by hannah7 on 2014-10-22
Hi everyone

Forgive me for being a total beginner! So I've installed Ubuntu 12.04 onto my Chromebook via Crouton, and the only programs I've installed are Chromium and Eclipse then Oracle JDK 8 and the Android SDK. I got half way through installing some of the packages on the SDK Manager when it told me I had no disk space left! Surely having only installed 4 things I have a bit more to spare?? The SDK is saved in my Downloads folder at the moment (where I apparently have 245.8MB left) and when I tried to copy into a new folder in /opt or /usr/local, both times again these folders said they had no space left. Please tell me I'm doing something wrong and that I can actually install more than a measly browser, IDE, JDK and the Android SDK!? I know Chromebooks don't have a lot of space but it seems crazy I've ran out already! :)

Thanks!

Hannah

---

### Post by Mike_Walsh on 2014-10-22
Hallo, Hannah.

I must confess, I'm quite surprised, upon Googling 'Chromebook Specifications', to discover that they appear to come with an average of only 16 GB of storage (usually an SSD, I believe?)

That said, I'm running an entire operating system (Xubuntu 14.04, one of the Ubuntu derivatives) from a 16 GB flash drive. I have three browsers installed, Wine (for running Windows programs, of which I use a couple), a couple of dozen programs, loads of desktop widgets, a 'swap' space of 3 GB......and the drive is STILL less than 60% full.

So, I would be surprised if you actually needed the entire SSD (or anywhere NEAR the whole thing) for a 'productive' system. I'm still fairly new to Linux myself, but something's not right there.

My  Ubuntu desktop install, with over 180 apps in total, is only occupying 22.5 GB of a 160 GB hard drive!

How did you install 12.04 to your Chromebook? Did you use the 'install alongside Chrome' option.....or did you opt to replace Chrome with 12.04? If you've installed alongside Chrome, then, allowing for at least 2-3 GB of 'swap' space, that alone would account for nearly 9 GB of your total of 16 GB.

Let us know which model of Chromebook you're using, please; that will allow us to see what your specs are.

With limited storage space, it might be an idea to consider using one of the lighter 'flavours' of Ubuntu, such as Xubuntu or Lubuntu (both of which I use myself). I have a very old Dell laptop, with a 20 GB hard drive; it runs 32-bit Lubuntu, and the result is a very nice little system, which happily does everything I ask of it. :)

Regards,

Mike.

---

### Post by yancek on 2014-10-22
You can find out how large each partition is, how much of it is used and how much free from a terminal with:  df -h

---

### Post by Bucky Ball on 2014-10-22
... or you can open Gparted and have a look with a GUI ...

---

### Post by hannah7 on 2014-10-23
Hi everyone,

Yes, Mike, mine does indeed only come with 16GB SSD. I do run it 'alongside' Chrome, so I switch back and forth, as opposed to 'instead of.' Would you suggest in that case installing Xubuntu or Lubuntu?

Yancek/Bucky Ball, these are the results from df -h:

[FONT=arial](precise)gy13her@localhost:~$ sudo df -h[/FONT]
[FONT=arial][sudo] password for gy13her: [/FONT]
[FONT=arial]df: `/mnt/stateful_partition': No such file or directory[/FONT]
[FONT=arial]df: `/usr/share/oem': No such file or directory[/FONT]
[FONT=arial]df: `/mnt/stateful_partition/encrypted': No such file or directory[/FONT]
[FONT=arial]df: `/home/chronos': No such file or directory[/FONT]
[FONT=arial]df: `/run/debugfs_gpu': No such file or directory[/FONT]
[FONT=arial]df: `/home/.shadow/9acfd5662b56ad479da9edf711067f7e98f58183/mount': No such file or directory[/FONT]
[FONT=arial]df: `/home/chronos/user': No such file or directory[/FONT]
[FONT=arial]df: `/home/user/9acfd5662b56ad479da9edf711067f7e98f58183': No such file or directory[/FONT]
[FONT=arial]df: `/home/chronos/u-9acfd5662b56ad479da9edf711067f7e98f58183': No such file or directory[/FONT]
[FONT=arial]df: `/home/root/9acfd5662b56ad479da9edf711067f7e98f58183': No such file or directory[/FONT]
[FONT=arial]df: `/run/crw': No such file or directory[/FONT]
[FONT=arial]Filesystem                                                    Size  Used Avail Use% Mounted on[/FONT]
[FONT=arial]rootfs                                                         11G  9.7G  298M  98% /[/FONT]
[FONT=arial]/dev/root                                                      11G  9.7G  298M  98% /[/FONT]
[FONT=arial]devtmpfs                                                      938M     0  938M   0% /dev[/FONT]
[FONT=arial]tmp                                                           940M  176K  939M   1% /tmp[/FONT]
[FONT=arial]run                                                           188M   20K  188M   1% /run[/FONT]
[FONT=arial]shmfs                                                         940M   26M  914M   3% /dev/shm[/FONT]
[FONT=arial]/dev/sda1                                                      11G  9.7G  298M  98% /home[/FONT]
[FONT=arial]/dev/mapper/encstateful                                        11G  9.7G  298M  98% /var[/FONT]
[FONT=arial]media                                                          11G  9.7G  298M  98% /media[/FONT]
[FONT=arial]/dev/sda1                                                      11G  9.7G  298M  98% /usr/local[/FONT]
[FONT=arial]none                                                          940M     0  940M   0% /sys/fs/cgroup[/FONT]
[FONT=arial]none                                                          938M     0  938M   0% /dev/pstore[/FONT]
[FONT=arial]/dev/sda1                                                      11G  9.7G  298M  98% /[/FONT]
[FONT=arial]devtmpfs                                                      938M     0  938M   0% /dev[/FONT]
[FONT=arial]shmfs                                                         940M   26M  914M   3% /dev/shm[/FONT]
[FONT=arial]tmp                                                           940M  176K  939M   1% /tmp[/FONT]
[FONT=arial]tmpfs                                                         188M   20K  188M   1% /run[/FONT]
[FONT=arial]tmpfs                                                         5.0M     0  5.0M   0% /run/lock[/FONT]
[FONT=arial]run                                                           940M  564K  939M   1% /var/host/dbus[/FONT]
[FONT=arial]run                                                           940M  564K  939M   1% /var/host/shill[/FONT]
[FONT=arial]run                                                           940M  564K  939M   1% /var/host/cras[/FONT]
[FONT=arial]/dev/mapper/encstateful                                       3.1G   45M  3.1G   2% /var/host/timezone[/FONT]
[FONT=arial]/dev/root                                                     1.2G 1001M  204M  84% /lib/modules/3.8.11[/FONT]
[FONT=arial]run                                                           940M  564K  939M   1% /var/host/udev[/FONT]
[FONT=arial]media                                                         940M     0  940M   0% /var/host/media[/FONT]
[FONT=arial]/home/.shadow/9acfd5662b56ad479da9edf711067f7e98f58183/vault   11G  9.7G  298M  98% /home/gy13her/Downloads[/FONT]
[FONT=arial]none                                                          940M     0  940M   0% /sys/fs/cgroup[/FONT]

Even I can see that some of these directories are at 98%...but so many are at 0% and 1% also I was rather hoping there was a bit more space to give! :)

Thanks,

Hannah

---

### Post by Bucky Ball on 2014-10-23
Yes, Xubuntu or particularly Lubuntu are lighter. A minimal install and just add what you are going to use along with a lightweight desktop environment (xfce4 or lxde, though there are lighter) lightest.

Please use [code] tags when posting code. Neater and easier to read. Thanks. ;) (See the last link in my signature for how.)

---

### Post by Elfy on 2014-10-23
Installing a stock anything isn't going to make a huge amount of difference to disk usage.

Try running 

```
sudo du -h --max-depth=1 /
```

---

### Post by jdeca57 on 2014-10-23
I searched 'crouton disk space requirements' and found this link:
```

https://github.com/dnschneid/crouton/issues/403

```
Depending on what you installed earlier it seems that on a 16 GB machine you should have access to several GB making your installation entirely possible. The disk space problems seems to have it's origin in chromeos and the way crouton is installed, not so much in Ubuntu. By the way, you can also consider later versions of Ubuntu since they may be better adapted to recent kernels since the chroot environment runs on the chromeos kernel.

---

### Post by stalkingwolf on 2014-10-23
for my reading chromeos can take as much as 9.6 gb of disk space and 12.04 from 4 to 6 gb  that would mean only about 1.5 gb left for extras. and as i recall there is a bit knocked off for the system so you cant totally max the drive out.

---

### Post by hannah7 on 2014-10-24
Ok, Elfy, this is the output from sudo du -h --max-depth =1/

```

[FONT=arial]1.1M	./.local[/FONT]
[FONT=arial]24K	./.compiz-1[/FONT]
[FONT=arial]2.6M	./.eclipse[/FONT]
[FONT=arial]4.0K	./.gvfs[/FONT]
[FONT=arial]12K	./.gnome2[/FONT]
[FONT=arial]12K	./.dbus[/FONT]
[FONT=arial]36K	./.pki[/FONT]
[FONT=arial]516K	./.android[/FONT]
[FONT=arial]29M	./.config[/FONT]
[FONT=arial]176K	./.gconf[/FONT]
[FONT=arial]36K	./.pulse
[/FONT]
[FONT=arial]6.7G	./Downloads[/FONT]
[FONT=arial]4.0K	./Desktop[/FONT]
[FONT=arial]84K	./.fontconfig[/FONT]
[FONT=arial]30M	./.cache[/FONT]
[FONT=arial]6.8G	.

```

Any further ideas? I'm leaning towards installing Lubuntu instead, although the online material on doing that for Chromebooks seems pretty sparse as I'd want to do it without a USB stick if possible.

Thanks

Hannah[/FONT]

---

### Post by oldrocker99 on 2014-10-24
The SSD that came with your Chromebook is on a removable circuit board. You can, for ~$100, insert a 128GB (largest at this time, apparently) SSD. Look it up on just how with your Chromebook.

I use an Acer C7 (which came with a 360 GB drive (for $200!) with Chrubuntu, saving 12 GB for ChromeOS. You might want to look for a C7 on Ebay or elsewhere.

---

