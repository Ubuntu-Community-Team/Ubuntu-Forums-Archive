---
title: "[SOLVED] Lost all administative privileges but cannot get into grub loader to edit ch"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by rjimcpherson on 2008-08-21
Hi all,

I'm very new to linux and this is my first post in this forum. First off,
had it not been for the excellent support of this forum, I think I might have tucked my tail between my legs and whimpered back to Windows. Thanks to each and every one of you for both submitting even the simplest of questions and also to those who respond with clear simple answers without a snotty RTFM attitude. You have made my Ubuntu experience just fabulous these last couple of months. I've decided to make the switch permanently.

Secondly,let's get straight to my problem. I'm not sure if this is pertinent so I'll list it just in case it is. I purchased a Dell inspiron 1420n with Ubuntu 7.10 pre-installed. I've since upgraded successfully (thanks to this forum) to Ubuntu 8.04.

I was experimenting the other day trying to install and configure Samba to create a network share for my Windows network (wife and kid still using Windows XP) when something got munged up with my Ubuntu privileges. I looked this problem up in the forums and it sounds like it has already been addressed and marked as resolved ([http://ubuntuforums.org/showthread.php?t=334981](http://ubuntuforums.org/showthread.php?t=334981)) but unfortunately, I am having trouble booting into grub to fix this problem.

I had previously installed an app called 'Startup Manager' and set the timeout in the bootloader menu to 0 seconds. No matter how quickly I hit the ESC key on bootup, it bypasses the menu options and boots straight into my screwed up installation. I have spent a HUGE amount of work installing Sun VirtualManager (xVM version) to install XP Pro so that I can login to my Company's VPN to work from home on my laptop and I would hate to have to do a complete re-install of everything I've done so far.

Anyway, the instructions from the previous post ([http://ubuntuforums.org/showthread.php?t=334981](http://ubuntuforums.org/showthread.php?t=334981)) do not work for me because I don't know how to reboot into recovery mode because my machine does not give any delay to get into the bootloader menu. Here is the information that this other post recommended (the info from the /etc/hosts and /etc/homename files:

ramcpher@dell-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	dell-desktop.example.com	dell-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
ramcpher@dell-desktop:~$ cat /etc/hostname
dell-desktop
ramcpher@dell-desktop:~$ 

The /etc/hosts file seems to have changed my host from one IP to a different one and replaced the hostname 'dell-desktop' to dell-desktop.example.com. I can't change it because I have no admin privileges (sudo, su, sudo -i, etc. don't work at all and the admin apps will start to launch and then quit).

I hope this is enough info. Thanks in advance.

rjimcpherson

---

### Post by bobnutfield on 2008-08-21
If you have a live cd, you can boot to the live cd and mount your Ubuntu partition, and change the /etc/hosts and /etc/hostname to reflect the same name.  Just navigate your way to the /etc directory and open gedit to make the changes.

---

### Post by sdennie on 2008-08-21
One thing you could would be to boot from the LiveCD and then mount your linux partition from there to work on it.  Bring up a terminal from the LiveCD and then type:

```

sudo fdisk -l

```

Identify which partition is your root partition and then do, for example:

```

sudo mkdir /mnt/root
sudo mount /dev/sda1 /mnt/root
cd /mnt/root

```

From there you can work on your install however you see fit.

---

### Post by kellemes on 2008-08-21
Startup your (screwed up) Ubuntu install and get to console, or startup a terminal..
Now edit /boot/grub/menu.lst using your preferred editor like so..
(don't know what editor you prefer so replace "vim" with the one you want, could be "gedit" if you're working from X)
```

sudo vim /boot/grub/menu.lst
```

Now find the line with "timeout" and edit it to include the amount of seconds.
for 30 secnds it should be..
```
timeout 30
```

---

### Post by louieb on 2008-08-21
> **rjimcpherson said:**
> ... No matter how quickly I hit the ESC key on bootup, it bypasses the menu options and boots straight into my screwed up installation. 
1st to get it so you can boot to recovery mode Boot with the Ubuntu Live CD.
When you get the desktop open the run dialog by pressing **Alt+F2** 

now start Nautilus```
 gksudo nautilus  
```You should now be able to open and edit /boot/grub/menu.lst.

the two lines you want to check are **hidden menu and timeout**.
They should look something like this.
 
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu


```Reboot and you should get the grub menu and be able to boot recovery mode and fix your admin privlages so you can use sudo.
Good Luck.

---

### Post by rjimcpherson on 2008-08-21
Wow!!! You guys are quick. 

kellemes: I can't use the sudo command. I get the following error:

ramcpher@dell-desktop:~$ sudo vim /boot/grub/menu.lst
>>> sudoers file: syntax error, line 11 <<<
>>> sudoers file: syntax error, line 26 <<<
sudo: parse error in /etc/sudoers near line 11


However, the live cd sounds like a great idea. I'm downloading one right now and will post my results ASAP. Thanks!

rjimcpherson

---

### Post by rjimcpherson on 2008-08-21
This worked! First I did what vor suggested:

>sudo fdisk -l

and chose my root partition

>sudo mkdir /mnt/root 
>sudo mount /dev/sda1 /mnt/root *in my case, it was sda3
>cd /mnt/root

Then I followed kellemes instructions:

>sudo vim /boot/grub/menu.lst

and changed the timeout to 30.

Then I made the changes to the hosts file like bobnutfield suggested.

Finally, I had to edit the sudoers file using visudo until it parsed correctly.

Thank you to all of you who responded. Excellent work! I will mark this thread as closed.

rjimcpherson

---

### Post by sdennie on 2008-08-21
I'm glad to hear you are back up and running.  It's also nice to hear that you were able to take a mix of advice from people and fix your machine.

---

### Post by kellemes on 2008-08-22
> **vor said:**
> (..)  It's also nice to hear that you were able to take a mix of advice from people and fix your machine.

Indeed a good example of how one should use the support given.
Well done.

---

