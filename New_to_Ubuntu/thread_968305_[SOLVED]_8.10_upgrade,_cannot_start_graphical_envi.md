---
title: "[SOLVED] 8.10 upgrade, cannot start graphical environment"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by ZOOstation on 2008-11-02
Immediately after upgrading from 8.04 to 8.10, it doesn't load the graphic interface. I'm basically in "DOS" - a black screen with a terminal prompt. Occasionally, by trying to run in other modes, I've been given this message:
```
Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be
disabled. Please restart GDM when
the problem is corrected.
```

HELP!

---

### Post by Sand Lee on 2008-11-02
OK, I probably won't be able to solve this myself, but what is the output of ```
tail -15 /var/log/syslog
```

---

### Post by ZOOstation on 2008-11-02
syslog:
```
Nov 2 16:25:14 Lappy kernel: [ 480.276770] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 2 16:25:14 Lappy kernel: [ 480.276778] Bluetooth: BNEP filters: protocol multicast
Nov 2 16:25:14 Lappy bluetoothd[6004]: bridge pan0 created
Nov 2 16:25:14 Lappy kernel: [ 480.340596] Bridge firewalling registered
Nov 2 16:25:15 Lappy kernel: [ 480.340854] pan0: Dropping NETIF_F_UFO since no NETIF_F_CSUM feature.
Nov 2 16:25:15 Lappy kernel: [ 480.353222] Bluetooth: RFCOMM socket layer initialized
Nov 2 16:25:15 Lappy kernel: [ 480.353250] Bluetooth: RFCOMM TTY layer initialized
Nov 2 16:25:15 Lappy kernel: [ 480.353254] Bluetooth: RFCOMM ver 1.10
Nov 2 16:25:15 Lappy anacron[6134]: Anacron 2.3 started on 2008-11-02
Nov 2 16:25:15 Lappy anacron[6134]: Normal exit (0 jobs run)
Nov 2 16:25:15 Lappy /usr/sbin/cron[6177]: (CRON) INFO (pidfile fd = 3)
Nov 2 16:25:15 Lappy /usr/sbin/cron[6178]: (CRON) STARTUP (fork ok)
Nov 2 16:25:15 Lappy /usr/sbin/cron[6178]: (CRON) INFO (Running @reboot jobs)
Nov 2 16:25:21 Lappy gdm[6067]: CRITICAL: gdm_config_value_get_bool: assertion 'value->type == GDM_CONFIG_VALUE_BOOL' failed
```

---

### Post by Sand Lee on 2008-11-02
Doing a little google searching on the last line of your syslog, led me to these links.
[Someone with the same problem]("http://ubuntuforums.org/showthread.php?t=828108")
[Possible fix]("http://ubuntuforums.org/showthread.php?t=599620"), [here]("http://ubuntuforums.org/showpost.php?p=3690958&postcount=10")

---

### Post by ZOOstation on 2008-11-02
A strange new twist: "sudo" no longer works. I'm given the response:
```
sudo: /etc/sudoers is not a regular file
```
I don't know what I've done to cause that, all I've done besides turn the laptop on and off is try the tools in recover mode. Some of them do stuff, some of them don't, nothing seems to help.

Unfortunately, I can't try out the possible fix above without it.

---

### Post by Sand Lee on 2008-11-03
What's your output of:
```
echo $PATH && ls -l /usr/bin/sudo && ls -l /etc/sudoers 
```

I hope you weren't typing the outputs by hand, but if you are run this and upload the "debug" file from your home folder.
```
echo $PATH > debug && ls -l /usr/bin/sudo >> debug && ls -l /etc/sudoers >> debug
```

[A related page]("http://www.gratisoft.us/pipermail/sudo-users/2003-August/001703.html")

---

### Post by ZOOstation on 2008-11-03
Yes, I'm writing out all these outputs myself. I was using another computer to get online in the first place. Now I'm booting 8.10 off a cd to go online and correspond, then rebooting without the disc to mess with things. Seriously, booting from the hard disk brings me to a black screen with a terminal prompt, and now I can't get root access.

"echo $PATH && ls -l /usr/bin/sudo && ls -l /etc/sudoers" gives me:
```
/usr/local/sbin:/user/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
-rwsr-xr-x 2 root root 115136 2008-09-01 09:17 /usr/bin/sudo
lrwxrwxrwx 1 root root 39 2008-11-02 02:18 /etc/sudoers -> /usr/lib/jvm/java-6-sun/jre/bin/java_vm
```

---

### Post by Sand Lee on 2008-11-03
That's a bummer :(. 
On the bright side, it looks like we've discovered why you keep getting the sudo error! 
The last line shows that your sudo file isn't a file at all, it's a link to java_vm?

From here what you can try is to boot from the liveCD and copy it's /etc/sudoers file to your hard drive (/media/disk/etc/). Hopefully the following command will work after you mount your HD on the liveCD, (the output should let you know)```
sudo cp -v /etc/sudoers /media/disk/etc/sudoers
```

---

### Post by Sand Lee on 2008-11-03
Alternatively, it that file doesn't work you could try using my sudoers file. Maybe you have a flash drive to bring it over to the upgraded machine? 

Also this is a pretty weird situation your PC's in, has anything unusual been installed or anything weird happen to your computer? Then again, this could just be a bug in the Upgrade..

---

### Post by ZOOstation on 2008-11-03
```
ubuntu@ubuntu:~$ sudo cp -v /etc/sudoers /media/disk/etc/sudoers
`/etc/sudoers' -> `/media/disk/etc/sudoers'
cp: not writing through dangling symlink `/media/disk/etc/sudoers'
```

---

### Post by Sand Lee on 2008-11-03
well then do a ```
sudo cp /media/disk/etc/sudoers /media/disk/etc/sudoers.old

```
then follow up with a ```
sudo rm /media/disk/etc/sudoers
```
then retry the other cp command.

---

### Post by ZOOstation on 2008-11-03
Hmmm, I did all of the above, and it worked (by which I mean it didn't give any errors). Sudo is restored, but I tried the sudo dpkg-reconfigure advice from the other thread and it didn't fix my problem.

Here's my new syslog:
```
Nov  3 03:08:36 Lappy ntpd[8369]: frequency initialized -24.487 PPM from /var/lib/ntp/ntp.drift
Nov  3 03:08:36 Lappy ntpd[8369]: getaddrinfo: "::1" invalid host address, ignored
Nov  3 03:08:36 Lappy anacron[8390]: Anacron 2.3 started on 2008-11-03
Nov  3 03:08:36 Lappy anacron[8390]: Normal exit (0 jobs run)
Nov  3 03:08:36 Lappy /usr/sbin/cron[8433]: (CRON) INFO (pidfile fd = 3)
Nov  3 03:08:36 Lappy /usr/sbin/cron[8434]: (CRON) STARTUP (fork ok)
Nov  3 03:08:36 Lappy /usr/sbin/cron[8434]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Nov  3 03:08:38 Lappy ntpd_initres[8378]: couldn't resolve `ntp.ubuntu.com', giving up on it
Nov  3 03:10:01 Lappy /USR/SBIN/CRON[8623]: (root) CMD (if [ -x /usr/bin/gsmsmsrequeue ]; then /usr/bin/gsmsmsrequeue; fi)
Nov  3 03:10:01 Lappy /USR/SBIN/CRON[8638]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

Also of interest, one of the messages while booting is:
```
*Not Starting GNOME Display Manager (gdm); it is not the default display manager.
```

---

### Post by Sand Lee on 2008-11-03
> **ZOOstation said:**
> ```
*Not Starting GNOME Display Manager (gdm); it is not the default display manager.
```

Google is an excellent resource to use when troubleshooting. Search the message above and it will lead you to a link (the first one) which has a fix that worked for the user.

---

### Post by kansasnoob on 2008-11-03
I've not personally done this but it comes from a trusted source:

[http://ubuntuforums.org/showthread.php?t=950851](http://ubuntuforums.org/showthread.php?t=950851)

---

### Post by ZOOstation on 2008-11-03
I was just about to post and say I'd googled the GDM problem and fixed it!
But that didn't solve the lack of GUI either.
Here are some other solutions I found to people with similar problems, and their effects (or lack thereof) on my situation:

```
me@Lappy:~$ sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
cp: cannot stat 'etc/X11/xorg.conf_backup': No such file or directory

me@Lappy:~$ sudo /etc/init.d/gdm restart
*Stopping GNOME Display Manager... [OK]
*Starting GNOME Display Manager... [OK]

me@Lappy:~$ sudo startx
X: warning; process set to priority -1 instead of requested priority 0
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server.
xinit: No such process (errno 3): Server error.
```

---

### Post by ZOOstation on 2008-11-05
Okay, tried doing a little research and got nothing. kansasnoob, thanks for the tip but it didn't seem to help.

So, if GDM is running fine but I still have no gui, it must be a problem with the xserver, correct? I've read there are compatibility issues between X and ATI graphics cards -- mine is an ATI Mobility Radeon X600 -- so I uninstalled and reinstalled the fglrx packages (fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx).

It also suggested the package libamdxvba1. This brought about a strange result:
```
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  libamdxvba1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 412kB of archives.
After this operation, 1376kB of additional disk space will be used.
Err http://archive.ubuntu.com intrepid/multiverse libamdxvba1 2:8.543-0ubuntu4
  Could not resolve 'archive.ubuntu.com'
```
Now, looking for libamdxvba1 in Symantec while booting from CD, it doesn't seem to exist. But that's not the error I'm being shown. Instead I seem to have trouble connecting to the archive.

This has also been a recurring problem when attempting sudo apt-get update:
```
Err http://archive.ubuntu.com intrepid Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://security.ubuntu.com intrepid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com intrepid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists...
```
It goes on and on, and ultimately doesn't seem to update anything at all. Ironically, it tells me to solve the problem using sudo apt-get update. >_<

Any further ideas sparked by all this blind doodling? I'm getting really effing sick of not being able to run my computer like normal, but I'll do anything to avoid installing clean off the disc (I'm under the impression that'll wipe out my old files, which I never seem to back up in time for a major problem like this).

---

### Post by Sand Lee on 2008-11-05
Wait so GDM - the graphical user login - comes up, but when you login it sends you to an X session?
I'm not exactly sure where you can go from here. If you have a flash drive you can dl the libamdxvba1 package and put it in your home folder, then booting it regularly, you can run sudo dpkg -i libamdxvba1*

---

### Post by ZOOstation on 2008-11-05
No, I don't get a graphical login either. No graphical anything. It's just that it tells me GDM is working fine.

---

### Post by ZOOstation on 2008-11-06
Maybe this is a forum faux pas, but I'm gonna start this dialogue over in a new thread, in order for new viewers to easily ignore the other things that we've handled along the way. I'll put a link to the new one after I start it.

*EDIT: [New!]("http://ubuntuforums.org/showthread.php?t=972674")*

---

