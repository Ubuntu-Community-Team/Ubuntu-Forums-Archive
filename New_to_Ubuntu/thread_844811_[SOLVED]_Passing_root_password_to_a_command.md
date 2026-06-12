---
title: "[SOLVED] Passing root password to a command"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Inxsible on 2008-06-29
I have a cronjob which does my apt-get update && apt-get upgrade using the following in the crontab```
30 03 */3 * * apt-get -qy update >> ~/cronlog 2>&1; apt-get -qy upgrade >> ~/cronlog 2>&1
```This requires super user privileges, however I am not in sudoers and I don't plan to be in it either - but I am the only user on the computer.

Can I somehow pass the root password to that command so that it will update my computer?

---

### Post by kool_kat_os on 2008-06-29
when setting the crontab...use the user option....and then use root as the user...

```
-u root
```

```
crontab -u root file
```


OR

log on as root in the terminal and set it when you are logged in as root(i think)

---

### Post by Inxsible on 2008-06-29
When I do a ```
crontab -e 
``` as root, it opens the same crontab file that i made with my username :(

---

### Post by kool_kat_os on 2008-06-29
type in this to go to root's crontab:

```
crontab -u root -e
```

and then type in this to remove your exisiting crontab

```
crontab -u yourusername -r
```

---

### Post by Inxsible on 2008-06-29
Alright Cool !!

I got a different crontab and it gives me a log file. But the commands didnt work. This is what I got in my cronlog file that I had created.```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  cpp epdfview ffmpeg g++ gcc gstreamer0.10-ffmpeg libavcodec51 libavdevice52
  libavformat52 libcupsimage2 libcupsys2 libggi-target-x libggi2 libx11-6 vlc
  vlc-nox
The following packages will be upgraded:
  acpi aptitude ca-certificates gcc-4.3-base grub grub-common hal initscripts
  klibc-utils libavutil49 libcaca0 libcdaudio1 libcdio7 libcdparanoia0
  libcucul0 libcurl3 libcurl3-gnutls libedit2 libfreetype6 libgcc1 libgii1
  libgii1-target-x libhal-storage1 libhal1 libhunspell-1.2-0 libidn11
  libio-socket-ssl-perl libiso9660-5 libklibc libnss3-1d libogg0 liboil0.3
  libperl5.10 libpopt0 libsm6 libsox-fmt-alsa libsox-fmt-base libsox0
  libsplashy1 libstdc++6 libswscale0 libtiff4 libvlc0 libx11-data libxft2
  libxrender1 manpages mime-support mplayer perl perl-base perl-doc
  perl-modules psutils python-gobject rar rtorrent sox sysv-rc sysvinit
  sysvinit-utils traceroute vim-common vim-tiny vorbis-tools wdiff wget
  wpasupplicant x-ttcidfont-conf x11-apps xserver-xorg-core
  xserver-xorg-video-intel xserver-xorg-video-s3
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-voodoo
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
81 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
Need to get 0B/42.6MB of archives.
After this operation, 594kB of additional disk space will be used.
dpkg: `ldconfig' not found on PATH.
dpkg: `start-stop-daemon' not found on PATH.
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
dpkg: 4 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```Note that when I ran the command apt-get upgrade in a terminal as root, everything worked. So why are the paths not set when running it from the crontab?

---

### Post by kool_kat_os on 2008-06-29
try a simpler command first...see if it works...:)

---

### Post by Inxsible on 2008-06-29
well I am guessing that cron did its job by initiating the command on time.

however, for some reason, some PATHs are not set thereby making it unable to update the system. However, everything works when i manually become a root in the terminal and issue the same commands

---

### Post by kool_kat_os on 2008-06-29
oh well....thats all i know :-)

i just got the answer for your question off of this page
[http://www.ss64.com/bash/crontab.html](http://www.ss64.com/bash/crontab.html)

---

### Post by Victormd on 2008-06-30
I have a simpler question...
I have a script that uses SUDO and I would like not to have to type the password (not that it's a big deal but I'm just thinking ahead)
can I embed the password in the script so that I can run it and when it asks for my password the script will retrieve it from an internal variable or something?

---

### Post by kool_kat_os on 2008-06-30
i already answered that question...but oh well...here i go:)

```
crontab -u root -e
```
and place your crontab there...and it wont ask you for a password anymore :-)

---

### Post by Victormd on 2008-06-30
Not the same question... I don't think... :)

I'm not using crontab or anything like that (don't even know what it is - maybe I should be using it... hehehe)

Let's say, a simple
```
sudo apt-get update
```
will ask for the password. If I include this command in a script, how can I have the script automatically retrieve my password from a variable inside the script so I don't have to type it in?

---

### Post by kool_kat_os on 2008-06-30
uh....maybe run the script as root?

---

### Post by Inxsible on 2008-06-30
> **kool_kat_os said:**
> oh well....thats all i know :-)

i just got the answer for your question off of this page
[http://www.ss64.com/bash/crontab.html](http://www.ss64.com/bash/crontab.html)
do you mean I should use /usr/bin/apt-get upgrade as my command?

I will try that and see

---

### Post by kool_kat_os on 2008-06-30
uhh...sure...i dont know:)

---

### Post by Victormd on 2008-06-30
> **kool_kat_os said:**
> uh....maybe run the script as root?

I know that... :)
I'm just wondering if I can do it any other way.

---

### Post by Inxsible on 2008-06-30
Sweet !!

using /usr/bin actually worked !!!.

Now I have my own update-manager  in my minimal install ;-)

---

### Post by kool_kat_os on 2008-06-30
ohhh...well...thats all i know....:)

---

### Post by dfreer on 2008-06-30
> **Victormd said:**
> Let's say, a simple
```
sudo apt-get update
```
will ask for the password. If I include this command in a script, how can I have the script automatically retrieve my password from a variable inside the script so I don't have to type it in?

Well, I don't know on how to get the script do it. But what you can do is this:
Edit the sudoers file with visudo and add that command to your username to work without entering a password. Example:
```

**username**  ALL = (ALL) NOPASSWD: **/path/to/your/script**,

```

I think that's right, anyways.

---

### Post by kool_kat_os on 2008-06-30
> **Inxsible said:**
> Sweet !!

using /usr/bin actually worked !!!.

Now I have my own update-manager  in my minimal install ;-)

what was your crontab...i would like it have it if possible :-)

did you do it in root or in your user name?

---

### Post by Inxsible on 2008-06-30
> **kool_kat_os said:**
> what was your crontab...i would like it have it if possible :-)

did you do it in root or in your user name?
Sure this is my crontab. I had to do it as root, since I do not want to be in sudoers. In fact I dont even have sudo installed.
```
30 03 */3 * * /usr/bin/apt-get update >> /dev/null && /usr/bin/apt-get -qy upgrade >> /home/USERNAME/cronlog 2>&1
45 03 */3 * * /usr/bin/apt-get autoclean >> /home/USERNAME/cronlog 2>&1
00 04 */3 * * /usr/bin/apt-get -qy autoremove >> /home/USERNAME/cronlog 2>&1
```So this will issue these commands every 3 days to update, upgrade autoclean and autoremove at the specified times.

---

