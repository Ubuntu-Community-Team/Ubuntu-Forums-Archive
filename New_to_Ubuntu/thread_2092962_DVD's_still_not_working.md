---
title: "DVD's still not working"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Riffraffs on 2012-12-09
Hello all and HELP!
I thought I'd give ubuntu a try  ( I last tried Linux with red hat 10 when that came out), so far mostly good, I got it to see all of my hardware (that was some task) and set-up auto mount for my network drives on my server.
I've had a few little issues due to the hardware but nothing too hard that a half hour on the web hasn't been able to sort (well all but running 2 Logitech G-series controllers at the same time)
but DVD's thats a problem,
I have got XBMC to see the movies on the server but fails to play them, I have tried a disk into the pc and tried Mplayer,Xine & movieplayer, all give me nothing or just sound

Yes i have downloaded the 4 programs and followed the steps on [https://help.ubuntu.com/12.10/ubuntu-help/video-dvd-restricted.html]("https://help.ubuntu.com/12.10/ubuntu-help/video-dvd-restricted.html")

which states > Install libdvdnav4, libdvdread4, gstreamer0.10-plugins-bad, and gstreamer0.10-plugins-ugly.

If you would like to play encrypted DVDs (see the legal note above), open the Dash and launch a Terminal.

Type the following into the screen which appears, then press Enter:

sudo /usr/share/doc/libdvdread4/install-css.sh

Enter your password to complete the installation.

Xine shows the errors of video_decoder can't raise nice priority by 1: operation not permitted
video_decoder can't raise nice priority by 2: operation not permitted 

all I would like is to pick a DVD stored on the server from a menu like in XBMC and play it, am I missing something? 
please any help would be appreciated

---

### Post by NM5TF on 2012-12-09
have you tried the VLC player...it seems to solve most
DVD issues for me...

I believe it's in the software center...

Tommy

---

### Post by Riffraffs on 2012-12-09
tried and failed,
in the open disk menu I have tried to open the shared folder, failed- nothing happens
/dev/cdrom
/dev/cdrw
/dev/dvdrom
/dev/dvdrw
/dev/sg0
/dev/sg1
/dev/sg2
/dev/sg3
/dev/sg4
/dev/sg5
/dev/sr0
/dev/sr1
/media/<user>/<diskname>
all leave me with a blank screen
even open file and selecting one of the .vob files has no results

---

### Post by gandaran on 2012-12-09
> sudo /usr/share/doc/libdvdread4/install-css.sh
did this command install libdvdcss2? if you not sure try adding the [medibuntu repository]("http://www.medibuntu.org/repository.php") then install libdvdcss 2
```
sudo apt-get install libdvdcss2
```

---

### Post by Riffraffs on 2012-12-09
I was sure it did but I have now done as you said, and then 
> riff@Monolith:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2012-12-09 19:00:37--  [http://packages.medibuntu.org/dists/quantal/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/quantal/free/binary-amd64/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7955 (7.8K) [application/octet-stream]
Saving to: `/tmp/dvdcss-Y3OJqv/Packages'

100%[======================================>] 7,955       --.-K/s   in 0.03s   

2012-12-09 19:00:38 (252 KB/s) - `/tmp/dvdcss-Y3OJqv/Packages' saved [7955/7955]

--2012-12-09 19:00:38--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_amd64.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 40506 (40K) [application/octet-stream]
Saving to: `/tmp/dvdcss-Y3OJqv/libdvdcss.deb'

100%[======================================>] 40,506       224K/s   in 0.2s    

2012-12-09 19:00:38 (224 KB/s) - `/tmp/dvdcss-Y3OJqv/libdvdcss.deb' saved [40506/40506]

(Reading database ... 199028 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.12-0.0medibuntu1 (using .../dvdcss-Y3OJqv/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.12-0.0medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
riff@Monolith:~$ 

for libdvdread2, 3 & 4 (call me paranoid)
> sudo apt-get install libdvdcss2
returns with
> 0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

same situation HOWEVER SMPlayer now works! shame I get no menus so TV show disks don't work as well
But its a start.

---

### Post by monkeybrain2012 on 2012-12-09
> **Riffraffs said:**
> I was sure it did but I have now done as 


same situation HOWEVER SMPlayer now works! shame I get no menus so TV show disks don't work as well
But its a start.

If you install Smplayer from rvm's ppa and mplayer from the MOTU ppa it does support menus.[https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa)
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

---

### Post by Riffraffs on 2012-12-09
mplayer still gives sound but no video
SMplayer has the menu option grayed out even the shortcut (shift + enter) fails to do anything

---

