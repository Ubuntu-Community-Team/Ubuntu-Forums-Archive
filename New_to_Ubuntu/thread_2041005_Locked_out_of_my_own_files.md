---
title: "Locked out of my own files"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by WiredTired on 2012-08-11
Are the devs wondering why most home Linux users give up? Getting locked out of files on your own system while you are logged in may be an understandable cause for most people who aren't Linux devs! 

What happened when I tried to access the folder /var/run/tor is I saw a big x on that folder, and there are no right-click options for me to take back permission for these files. Why should this be an issue when I am already logged in anyway? NOBODY should ever be subjected to such harassment by their own computer, when the system knows exactly who you are!  Please help me fix this situation if you can, and devs please fix the problem so that future generations don't get waylaid by such crap while trying to help raise the Linux home user community above 2%!

---

### Post by WiredTired on 2012-08-11
Hi, I was trying to **ls** to a folder under 

/var/run 

so that I could modify a file in it according to instructions, but the point is that I got a "permission denied" error just for trying to ENTER that folder! 

Since I cannot sudo the ls command (yes, I tried that), and there are no right-click options which aren't also disabled (I tried getting there in Terminal first), I don't know what I'm supposed to do, but I need to get control back of files on my own computer if I'm going to keep using Linux - please help! How do I force it to acknowledge me as the owner, and why isn't it enough when I happen to be logged in?

---

### Post by Peripheral Visionary on 2012-08-11
Some files are system files and you need to be "root" (Administrator) in order to have access to them.

Some files default to "owner access only" on new installations, and you need to be root to access them and modify them.

Try opening a terminal and typing
```
sudo nautilis
```
 to open your file manager as root. You'll be asked for your root password (the one you used when you installed Ubuntu). Once in there, you can change "permissions" for the files you'd like to have access to when you are not logged in as root.
[B]
Ubuntu does not automatically log you in as Administrator the way that Windows does. [/B]That's not a bad thing!  It is one of the reasons that Linux is so resistant to malware. You have to enter your root password and deliberately do something lame in order to be affected by much malware on Ubuntu.

---

### Post by phrak on 2012-08-11
wouldn't 
```
gksudo nautilis
```
be the correct command?

'sudo' would work, but i thought the appropriate usage for running graphical sudo commands was 'gksudo'

also, he's on xfce... so probably should use pcmanfm instead of nautilis.

---

### Post by wildmanne39 on 2012-08-11
Hi, if you are going to use thunar as root you should do it this way:
```
gksu thunar
```
to keep root from possibly taking ownership of nautilus.
Thanks

---

### Post by phrak on 2012-08-11
> **wildmanne39 said:**
> Hi, if you are going to use nautilus as root you should do it this way:
```
gksu thunar
```
to keep root from possibly taking ownership of nautilus.
Thanks

I was close, drawback to doing very little in X I suppose...

---

### Post by phrak on 2012-08-11
first, ls is for listing files, not changing directories.. that's 'cd'

second, you don't have to cd to the file to edit it...

also, what are you trying to edit it in (with)?


As was explained in your other thread, you don't automatically have admin rights in linux (hence the sudo command)..  I'm not sure why you can't cd to a /var/ directory though.

---

### Post by wildmanne39 on 2012-08-11
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by phrak on 2012-08-11
Also, a link to whatever guide you are following would help us understand better what you're trying to do.

---

### Post by uRock on 2012-08-11
> **phrak said:**
> Also, a link to whatever guide you are following would help us understand better what you're trying to do.

The OP was following the directions [here]("http://ubuntuforums.org/showthread.php?t=2040807") for getting Tor running. I ran the commands without any issue on my system.

OP, can you copy and paste the output of the terminal after attempting to run the **cd /var/run/tor** command?

---

### Post by cryptotheslow on 2012-08-11
What permissions does /var/run have on your system?

Here on Ubuntu (I'd have thought Xubuntu is the same) it is a symlink to /run with open permissions for all:

```

crypto@ubulaptop1204:~$ ls -al /var/run
lrwxrwxrwx 1 root root 4 Aug 11 19:56 /var/run -> /run

```And for /run:
```

crypto@ubulaptop1204:~$ ls -al / | grep run
drwxr-xr-x  22 root   root     760 Aug 11 21:04 run

``````

crypto@ubulaptop1204:~$ ls -al /run
total 88
drwxr-xr-x 22 root       root         760 Aug 11 21:04 .
drwxr-xr-x 25 root       root       36864 Aug 11 17:41 ..
-rw-r--r--  1 root       root           5 Aug 11 21:03 acpid.pid
srw-rw-rw-  1 root       root           0 Aug 11 21:03 acpid.socket
-rw-r--r--  1 root       root           5 Aug 11 21:03 atd.pid
drwxr-xr-x  2 avahi      avahi         80 Aug 11 21:03 avahi-daemon
drwxr-xr-x  2 clamav     root          60 Aug 11 21:03 clamav
drwxr-xr-x  2 root       root          60 Aug 11 21:04 console
drwxr-xr-x  2 root       root          60 Aug 11 21:04 ConsoleKit
-rw-r--r--  1 root       root           5 Aug 11 21:03 console-kit-daemon.pid
-rw-r--r--  1 root       root           5 Aug 11 21:03 crond.pid
----------  1 root       root           0 Aug 11 21:03 crond.reboot
drwxr-xr-x  3 root       lp           120 Aug 11 21:03 cups
drwxr-xr-x  2 messagebus messagebus    80 Aug 11 21:03 dbus
drwxr-xr-x  2 root       root          40 Aug 11 21:03 initramfs
drwx--x--x  3 root       root          60 Aug 11 21:03 lightdm
-rw-r--r--  1 root       root           5 Aug 11 21:03 lightdm.pid
drwxrwxrwt  3 root       root          60 Aug 11 21:04 lock
-rw-r--r--  1 root       root         110 Aug 11 21:03 motd
drwxr-xr-x  2 root       root          60 Aug 11 21:03 mount
drwxr-xr-x  3 root       root         120 Aug 11 21:03 network
-rw-r--r--  1 root       root           0 Aug 11 21:03 network-interface-security
-rw-r--r--  1 root       root           3 Aug 11 21:03 NetworkManager.pid
-rw-r--r--  1 root       root        2197 Aug 11 21:03 nm-dhclient-wlan0.conf
drwxr-xr-x  4 root       root          80 Aug 11 21:03 pm-utils
drwxr-xr-x  2 root       root          40 Aug 11 21:03 pppconfig
drwxr-xr-x  3 root       root         100 Aug 11 21:03 resolvconf
-rw-r--r--  1 root       root           4 Aug 11 21:03 rsyslogd.pid
srw-rw-rw-  1 root       root           0 Aug 11 21:03 sdp
drwxr-xr-x  2 root       root          80 Aug 11 21:03 sendsigs.omit.d
drwxrwxrwt  2 root       root         220 Aug 12 00:01 shm
drwxr-xr-x  7 root       root         180 Aug 12 00:02 udev
drwxr-xr-x  2 root       root          60 Aug 11 21:03 udev-configure-printer
drwx------  2 root       root          40 Aug 11 21:04 udisks
-rw-r--r--  1 root       root           4 Aug 11 21:03 upstart-socket-bridge.pid
-rw-r--r--  1 root       root           4 Aug 11 21:03 upstart-udev-bridge.pid
-rw-rw-r--  1 root       utmp        3840 Aug 12 03:11 utmp
drwxr-x---  2 root       root          60 Aug 11 21:03 wpa_supplicant

```
I can ls and cd into them all without elevating privilege from a standard user at all.

From the sound of it you've messed up the ownership or privileges on either the symlink or /run itself.

Check your ownerships and perms against the above (a fairly un-meddled Ubu12.04 install). You'll probably find something blatantly wrong.


*edit to add - * Generally on this forum bumping threads after less than 24 hours is considered impolite. As would be duplicating a question in another section within that time. Nothing to get wound up about, the regulars are used to having several pages of unread threads to get through. It's just busy - but you won't be overlooked if you end up on page 5 after a few hours :D

---

### Post by WiredTired on 2012-08-11
> **phrak said:**
> Also, a link to whatever guide you are following would help us understand better what you're trying to do.
At first I was hesitant to post too much info, out of concern that it would sidetrack the issue, which is that I am denied permission to access my own folders/files and it is NOT a sudo control issue. Now four people decided it's that anyway, which it isn't. Now that it's come to this, I would love to post what another forum staff member posted (unfortunately I never got the source for that), and was then destroyed by Yosemite Sam's over-zealous thread-"merging". Because of this I cannot post what the guy with the Tigger avatar posted, but I can show you verbatim the output of the command which I was trying to run (don't know how to copy text from the Terminal):

cd /var/run/tor:  Permission denied 

I did say "ls" earlier - sorry, but I somehow doubt  the sudo command would recognize this one either). The colon after /tor was added by the system after I attempted to execute it, and the rest was the system's response. What happened is not that I was denied permission to perform operations on a file, I was denied permission to so much as enter the folder which contained a file which I need access to, and this is where sudo didn't help me!

I checked to verify that the folder /tor was indeed under /var/run, in Thunar, and attempted to access it (denied).  I actually did think of using gksudo on Thunar (maybe this is what some here were trying to say), but my understanding so far of Linux is that no graphical interface is recognized as more powerful than the command line - therefore, if the command line I'm given won't change it for me, then why should I expect Thunar at any permissions level to help me? At this point, I'd like to review those commands which were posted here, but they're gone now!

---

### Post by uRock on 2012-08-11
> **WiredTired said:**
> At this point, I'd like to review those commands which were posted here, but they're gone now!

You mean the ones in this thread, [http://ubuntuforums.org/showthread.php?p=12165158#post12165158](http://ubuntuforums.org/showthread.php?p=12165158#post12165158)

---

### Post by cryptotheslow on 2012-08-11
OK - so the problem is with /var/run/tor which if it is the same as Ubuntu is effectively a symlink to /run/tor

What are the ownership and permissions on that directory?

In a pinch use su - to get root:

```

crypto@ubulaptop1204:~$ sudo su -
[sudo] password for crypto: 
root@ubulaptop1204:~# 

```From there you should be able to nano, pico, vi or whatever file you need to edit.

I understand your frustration, but this is not the place to vent it :D

---

### Post by WiredTired on 2012-08-11
> **cryptotheslow said:**
> What permissions does /var/run have on your system?

Here on Ubuntu (I'd have thought Xubuntu is the same) it is a symlink to /run with open permissions for all:

```

crypto@ubulaptop1204:~$ ls -al /var/run
lrwxrwxrwx 1 root root 4 Aug 11 19:56 /var/run -> /run

```And for /run:
```

crypto@ubulaptop1204:~$ ls -al / | grep run
drwxr-xr-x  22 root   root     760 Aug 11 21:04 run

``````

crypto@ubulaptop1204:~$ ls -al /run
total 88
drwxr-xr-x 22 root       root         760 Aug 11 21:04 .
drwxr-xr-x 25 root       root       36864 Aug 11 17:41 ..
-rw-r--r--  1 root       root           5 Aug 11 21:03 acpid.pid
srw-rw-rw-  1 root       root           0 Aug 11 21:03 acpid.socket
-rw-r--r--  1 root       root           5 Aug 11 21:03 atd.pid
drwxr-xr-x  2 avahi      avahi         80 Aug 11 21:03 avahi-daemon
drwxr-xr-x  2 clamav     root          60 Aug 11 21:03 clamav
drwxr-xr-x  2 root       root          60 Aug 11 21:04 console
drwxr-xr-x  2 root       root          60 Aug 11 21:04 ConsoleKit
-rw-r--r--  1 root       root           5 Aug 11 21:03 console-kit-daemon.pid
-rw-r--r--  1 root       root           5 Aug 11 21:03 crond.pid
----------  1 root       root           0 Aug 11 21:03 crond.reboot
drwxr-xr-x  3 root       lp           120 Aug 11 21:03 cups
drwxr-xr-x  2 messagebus messagebus    80 Aug 11 21:03 dbus
drwxr-xr-x  2 root       root          40 Aug 11 21:03 initramfs
drwx--x--x  3 root       root          60 Aug 11 21:03 lightdm
-rw-r--r--  1 root       root           5 Aug 11 21:03 lightdm.pid
drwxrwxrwt  3 root       root          60 Aug 11 21:04 lock
-rw-r--r--  1 root       root         110 Aug 11 21:03 motd
drwxr-xr-x  2 root       root          60 Aug 11 21:03 mount
drwxr-xr-x  3 root       root         120 Aug 11 21:03 network
-rw-r--r--  1 root       root           0 Aug 11 21:03 network-interface-security
-rw-r--r--  1 root       root           3 Aug 11 21:03 NetworkManager.pid
-rw-r--r--  1 root       root        2197 Aug 11 21:03 nm-dhclient-wlan0.conf
drwxr-xr-x  4 root       root          80 Aug 11 21:03 pm-utils
drwxr-xr-x  2 root       root          40 Aug 11 21:03 pppconfig
drwxr-xr-x  3 root       root         100 Aug 11 21:03 resolvconf
-rw-r--r--  1 root       root           4 Aug 11 21:03 rsyslogd.pid
srw-rw-rw-  1 root       root           0 Aug 11 21:03 sdp
drwxr-xr-x  2 root       root          80 Aug 11 21:03 sendsigs.omit.d
drwxrwxrwt  2 root       root         220 Aug 12 00:01 shm
drwxr-xr-x  7 root       root         180 Aug 12 00:02 udev
drwxr-xr-x  2 root       root          60 Aug 11 21:03 udev-configure-printer
drwx------  2 root       root          40 Aug 11 21:04 udisks
-rw-r--r--  1 root       root           4 Aug 11 21:03 upstart-socket-bridge.pid
-rw-r--r--  1 root       root           4 Aug 11 21:03 upstart-udev-bridge.pid
-rw-rw-r--  1 root       utmp        3840 Aug 12 03:11 utmp
drwxr-x---  2 root       root          60 Aug 11 21:03 wpa_supplicant

```I can ls and cd into them all without elevating privilege from a standard user at all.

From the sound of it you've messed up the ownership or privileges on either the symlink or /run itself.

Check your ownerships and perms against the above (a fairly un-meddled Ubu12.04 install). You'll probably find something blatantly wrong. 

I don't think I made any changes using whichever commands you just used -  which are they anyway (I don't see any commands printed, only the  output which I think lists file permissions the right way).


What's blatantly wrong is my file permissions specific to the /tor folder

/var/run/tor

It's a for-linux program which I have been trying to setup with  Vidalia ( a graphical interface for Tor). I can run Vidalia, but I get  the error that Tor has suddenly stopped, which led to a whole day being  wasted chasing tutorials which didn't solve my problem, or didn't anticipate that my /tor folder would be locked. Again, most of my folders under /var/run are browsable, but not /tor, and I'm wondering why this is, but maybe if I can figure out how to use it I'll be able to change my file permissionsI may be able to fix my permissions issue the right way.

EDIT: After looking at my permissions through gsudo Thunar, I see that the "owner" is debian-tor, and no means of changing the permissions through Thunar is offered.

> **cryptotheslow said:**
> 
*edit to add - * Generally on this forum bumping threads after less than 24 hours is considered impolite. As would be duplicating a question in another section within that time. Nothing to get wound up about, the regulars are used to having several pages of unread threads to get through. It's just busy - but you won't be overlooked if you end up on page 5 after a few hours :D

Back five pages is further than I would expect, and then the last thing I would want to do is give you guys too much to go through. 

I don't want to be a pain, but it's really too bad that a few "regulars", or even paid staff members here feel they are burdened to answer everybody's questions, which the entire user community once participated in doing. Maybe they still would if it wasn't expected of you, and then so much complaining from you guys that you are "burdened" leads to actions being taken which are making web forums everywhere much less friendly than they used to be. I hate to sound ungrateful, and I'm sorry, but this is not a good trend! There's nothing friendly at all, and it sure doesn't make a healthy learning environment where snarling web moderators intimidate newbies who are just trying to get answers for their questions (or a solution for buggy software).

---

### Post by cryptotheslow on 2012-08-11
Firstly, as far as I know - no-one here is paid. It's a community forum.

Secondly, I included the commands I used in my replies.

To summarise:

```

crypto@ubulaptop1204:~$ ls -al /run
crypto@ubulaptop1204:~$ ls -al / | grep run
crypto@ubulaptop1204:~$ ls -al /var/run

```

To summarise further:
```

ls -al /run
ls -al / | grep run
ls -al /var/run

```

Post back the results you get from those ^^^ commands and we can help you sort out your pickle.

---

### Post by WiredTired on 2012-08-11
> **cryptotheslow said:**
> What permissions does /var/run have on your system?

Here on Ubuntu (I'd have thought Xubuntu is the same) it is a symlink to /run with open permissions for all:

```

crypto@ubulaptop1204:~$ ls -al /var/run
lrwxrwxrwx 1 root root 4 Aug 11 19:56 /var/run -> /run

```And for /run:
```

crypto@ubulaptop1204:~$ ls -al / | grep run
drwxr-xr-x  22 root   root     760 Aug 11 21:04 run

``````

crypto@ubulaptop1204:~$ ls -al /run
total 88
drwxr-xr-x 22 root       root         760 Aug 11 21:04 .
drwxr-xr-x 25 root       root       36864 Aug 11 17:41 ..
-rw-r--r--  1 root       root           5 Aug 11 21:03 acpid.pid
srw-rw-rw-  1 root       root           0 Aug 11 21:03 acpid.socket
-rw-r--r--  1 root       root           5 Aug 11 21:03 atd.pid
drwxr-xr-x  2 avahi      avahi         80 Aug 11 21:03 avahi-daemon
drwxr-xr-x  2 clamav     root          60 Aug 11 21:03 clamav
drwxr-xr-x  2 root       root          60 Aug 11 21:04 console
drwxr-xr-x  2 root       root          60 Aug 11 21:04 ConsoleKit
-rw-r--r--  1 root       root           5 Aug 11 21:03 console-kit-daemon.pid
-rw-r--r--  1 root       root           5 Aug 11 21:03 crond.pid
----------  1 root       root           0 Aug 11 21:03 crond.reboot
drwxr-xr-x  3 root       lp           120 Aug 11 21:03 cups
drwxr-xr-x  2 messagebus messagebus    80 Aug 11 21:03 dbus
drwxr-xr-x  2 root       root          40 Aug 11 21:03 initramfs
drwx--x--x  3 root       root          60 Aug 11 21:03 lightdm
-rw-r--r--  1 root       root           5 Aug 11 21:03 lightdm.pid
drwxrwxrwt  3 root       root          60 Aug 11 21:04 lock
-rw-r--r--  1 root       root         110 Aug 11 21:03 motd
drwxr-xr-x  2 root       root          60 Aug 11 21:03 mount
drwxr-xr-x  3 root       root         120 Aug 11 21:03 network
-rw-r--r--  1 root       root           0 Aug 11 21:03 network-interface-security
-rw-r--r--  1 root       root           3 Aug 11 21:03 NetworkManager.pid
-rw-r--r--  1 root       root        2197 Aug 11 21:03 nm-dhclient-wlan0.conf
drwxr-xr-x  4 root       root          80 Aug 11 21:03 pm-utils
drwxr-xr-x  2 root       root          40 Aug 11 21:03 pppconfig
drwxr-xr-x  3 root       root         100 Aug 11 21:03 resolvconf
-rw-r--r--  1 root       root           4 Aug 11 21:03 rsyslogd.pid
srw-rw-rw-  1 root       root           0 Aug 11 21:03 sdp
drwxr-xr-x  2 root       root          80 Aug 11 21:03 sendsigs.omit.d
drwxrwxrwt  2 root       root         220 Aug 12 00:01 shm
drwxr-xr-x  7 root       root         180 Aug 12 00:02 udev
drwxr-xr-x  2 root       root          60 Aug 11 21:03 udev-configure-printer
drwx------  2 root       root          40 Aug 11 21:04 udisks
-rw-r--r--  1 root       root           4 Aug 11 21:03 upstart-socket-bridge.pid
-rw-r--r--  1 root       root           4 Aug 11 21:03 upstart-udev-bridge.pid
-rw-rw-r--  1 root       utmp        3840 Aug 12 03:11 utmp
drwxr-x---  2 root       root          60 Aug 11 21:03 wpa_supplicant

```I can ls and cd into them all without elevating privilege from a standard user at all.

From the sound of it you've messed up the ownership or privileges on either the symlink or /run itself.

Check your ownerships and perms against the above (a fairly un-meddled Ubu12.04 install). You'll probably find something blatantly wrong. 

I don't think I made any changes using whichever commands you just used -  which are they anyway (I don't see any commands printed, only the  output which I think lists file permissions the right way).


What's blatantly wrong is my file permissions specific to the /tor folder

/var/run/tor
It's a for-linux program which I have been trying to setup with  Vidalia ( a graphical interface for Tor). I can run Vidalia, but I get  the error that Tor has suddenly stopped, which led to a whole day being  wasted chasing tutorials which didn't solve my problem, or didn't anticipate that my /tor folder would be locked. Again, most of my folders under /var/run are browsable, but not /tor, and I'm wondering why this is, but maybe if I can figure out how to use it I'll be able to change my file permissions[I]It's a for-linux program which I have been trying to setup with  Vidalia ( a graphical interface for Tor). I can run Vidalia, but I get  the error that Tor has suddenly stopped, which led to a whole day being  wasted chasing tutorials which didn't solve my problem, or didn't  anticipate that my /tor folder would be locked. Again, most of my  folders under /var/run are browsable, but not /tor, and I'm wondering  why this is, but maybe if I can figure out how to use 
[/I].
> **cryptotheslow said:**
> 
*edit to add - * Generally on this forum bumping threads after less than 24 hours is considered impolite. As would be duplicating a question in another section within that time. Nothing to get wound up about, the regulars are used to having several pages of unread threads to get through. It's just busy - but you won't be overlooked if you end up on page 5 after a few hours :D

Back five pages is further than I would expect, and then the last thing I would want to do is give you guys too much to go through. 

I don't want to be a pain, but it's really too bad that a few "regulars", or even paid staff members here feel they are burdened to answer everybody's questions, which the entire user community once participated in doing. Maybe they still would if it wasn't expected of you, and then so much complaining from you guys that you are "burdened" leads to actions being taken which are making web forums everywhere much less friendly than they used to be. I hate to sound ungrateful, and I'm sorry, but this is not a good trend! There's nothing friendly at all, and it sure doesn't make a healthy learning environment where snarling web moderators intimidate newbies who are just trying to get answers for their questions (or a solution for buggy software).

---

### Post by cryptotheslow on 2012-08-11
I give up for now, this endless merging of threads is confusing the hell out of this topic. It would help if there weren't so many threads.

It's a simple ownership / permissions problem WiredTired.

---

### Post by uRock on 2012-08-12
> **WiredTired said:**
> EDIT: After looking at my permissions through gsudo Thunar, I see that the "owner" is debian-tor, and no means of changing the permissions through Thunar is offered.

Which is why I gave you the commands to change the ownership of said file in your other thread.

---

### Post by nothingspecial on 2012-08-12
We'll leave this one here.

Continue here [http://ubuntuforums.org/showthread.php?p=12165158#post12165158](http://ubuntuforums.org/showthread.php?p=12165158#post12165158)

Closed.

---

