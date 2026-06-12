---
title: "Live CD to Install?"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by DiesMali on 2012-06-25
I'm completely new to Linux. I have an old laptop (Dell Inspiron 8600) and I've finally managed to find a distro. that will load a Live cd (Xbuntu 12.04). I have two questions actually.
1- Just because the Live Cd loads and works (not fully, doesn't see wireless, but I managed a LAN connection), does that mean if I run the install I'll have the same results as I do with running the Live CD?

2- I've never partitioned a drive and would like to know if this is a difficult process, I have about 35-40 GB I could dedicate to the Xbuntu distro. and would really like to test drive it installed. I've seen different opinions on how much space is needed, and wonder if that's enough to install Apache, PHP, MySql, phpMyadmin and still be able to install more software without lagging down the distro. My physical memory on board is 1.5 MB and I run 2 GB's RAM w/1.6 MH Intel CPU. I'm hoping to be able to dual boot over the original XP sp3 OS.

Thanks in advance for any advice.
DM

---

### Post by carl4926 on 2012-06-25
Live CD is a good indicator of how things will work, though a live session is slow compared to a real install. We can probably get your wireless working though.

Here is a little slide show video
[https://dl.dropbox.com/u/10573557/Ubuntu/ub_11.10_slideshow.mkv](https://dl.dropbox.com/u/10573557/Ubuntu/ub_11.10_slideshow.mkv)

VLC will play it

---

### Post by robtygart on 2012-06-25
> 1- Just because the Live Cd loads and works (not fully, doesn't see wireless, but I managed a LAN connection), does that mean if I run the install I'll have the same results as I do with running the Live CD?

Even with the live CD you should be able to access your wireless, in your menu look for "Additional Drivers" and activate it.

---

### Post by carl4926 on 2012-06-25
> **robtygart said:**
> Even with the live CD you should be able to access your wireless, in your menu look for "Additional Drivers" and activate it.

Quite correct

---

### Post by DiesMali on 2012-06-25
Thanks for replies, much appreciated. I'm in the process of installing as we speak, hopefully I'll get the wireless going after a successful ( I hope) install. After working with Win for 20 years, I'm a bit concerned I might be just killing what was a functional(yet slow) laptop, but I'm also excited at the possibilities of learning a new OS.

Wish me luck, am about to "restart now", LOL

Thanks much again for the replies. though I just decided to be brave (or stupid), one must learn somehow.:popcorn:
Time to reboot and enjoy the show.

---

### Post by DiesMali on 2012-06-25
Hmmm, That didn't go as planned. On reboot my machine went straight  to Xbuntu, with no option to load winXP. I set the install to run both, but set Xbuntu to not require log-on. Guess I wont complain, I have 4 other Win machines so it's not like I'll be without the old stand by, LOL

Wow, there's like 170 updates I need to acquire it says. Time for some more :popcorn:

Any idea why I didn't get the option to load windows? BTW, the monitor on the laptop is shot, so I have an old HP monitor hooked up externally and it takes a few extra seconds for that to load I'M sure.

---

### Post by carl4926 on 2012-06-25
Try running this in a terminal
report the output here

```
sudo update-grub
```

---

### Post by carl4926 on 2012-06-25
> **carl4926 said:**
> Try running this in a terminal
report the output here

```
sudo update-grub
```


BUT please do all your updates and reboot First!

---

### Post by DiesMali on 2012-06-25
Running the update now carl, I'll give the terminal a shot once I reboot and then see if I can figure out how to copy and post the results here. Thanks for you assistance, I appreciate it.

---

### Post by carl4926 on 2012-06-25
> **DiesMali said:**
> Running the update now carl, I'll give the terminal a shot once I reboot and then see if I can figure out how to copy and post the results here. Thanks for you assistance, I appreciate it.

You'll find it easiest to use your mouse to copy and paste in a terminal.

You'll find it helpful to install the application 'Synaptic'
From there make sure 'os-prober' is installed, it should be there by default. If it's not, install it and then run update-grub again.

If windows still isn't there, post the out put of
```
sudo fdisk -l
```

---

### Post by DiesMali on 2012-06-25
Weird, I logged out of here on my windows machine and attempted to log in via xbuntu and firefox, it said my password or user name were invalid, but I logged right back in here with no issues.

I ran the sudo update-grub in terminal response below ( I've yet to figure out how you're posting in a "code" area like that. Been a while since I've been on any vboards.

after password entry:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0.25-generic
Found initrd image: /boot/initrd.img-3.2.0.25-generic
Found linux image: /boot/vmlinuz-3.2.0.32-generic
Found initrd image: /boot/initrd.img-3.2.0.23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda2
done

---

### Post by DiesMali on 2012-06-25
It showed the Win partition in the results, but after reboot, still no option to log in to win XP.

I'll try the commands you stated, sorry I'm slow, as I'm bouncing back and forth from maching to machine at the moment. I obviously have a lot to learn, LOL

---

### Post by carl4926 on 2012-06-25
Look for # on the reply tool bar to use code
Place the text in between the tags

I can't recall what you need to do to get the menu at boot
Do you see a menu or does it just boot right to ubuntu?

Try hitting Esc at boot

---

### Post by carl4926 on 2012-06-25
> **carl4926 said:**
> Look for # on the reply tool bar to use code
Place the text in between the tags

I can't recall what you need to do to get the menu at boot
Do you see a menu or does it just boot right to ubuntu?

Try hitting Esc at boot

Or try holding SHIFT as you boot the machine

---

### Post by DiesMali on 2012-06-25
Okay, I think I figured the code block out anyways, and I'm logged in on the distro as well... 

```
-Inspiron-8600:~$ sudo fdisk -1
[sudo] password for : 
fdisk: invalid option -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

-Inspiron-8600:~$ 

```

---

### Post by DiesMali on 2012-06-25
Hmmm, reading through output, and fighting a new environment... My eyes are burning, LOL

I'll try some more tomorrow, installing the synaptic and such, and also holding shift. It has been a long day, but I greatly appreciate your help. I'll get more familiar with the OS tomorrow and be back to attempt more. 

Thanks much carl! Going to call it a night. 2am here :|

---

### Post by carl4926 on 2012-06-25
It's fdisk -l
That's a lower case L not a number 1

---

