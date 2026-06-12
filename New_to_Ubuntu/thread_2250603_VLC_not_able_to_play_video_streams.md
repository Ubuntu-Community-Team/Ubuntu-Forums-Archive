---
title: "VLC not able to play video streams"
date: 2014-10-29
forum: New to Ubuntu
---

### Post by Harshal_patel on 2014-10-29
Hi,

I am streaming a video using ffmpeg command and trying a local loopback and play the video on VLC player. I have Ubuntu 14.04 installed on my server.

ffmpeg command that I am using to send video file is:
./ffmpeg -re -i /root/test_file.y4m -c:v libx264 -f:v mpegts -r:v 30 -s:v 1280x720 -b:v 1000k [udp://127.0.0.1:8090]("http://127.0.0.1:8090")

On the VLC player, I am using command:
vlc -vvv udp://127.0.0.1:8090
 
I verified the port is open with iptables and netstat.

VLC player is not playing any video and log file is not showing any activity.

Harshal Patel
HPC Systems Engineer
Signalogic Inc.

---

### Post by Alireza_Zamani on 2014-10-30
install media codec :

> [FONT=Ubuntu Mono]sudo apt-get -y install w32codecs ubuntu-restricted-extras    (32bit)
[/FONT][FONT=Ubuntu Mono]sudo apt-get -y install w64codecs ubuntu-restricted-extras    (64bit)[/FONT]

> [FONT=Ubuntu Mono]sudo apt-get -y install ubuntu-restricted-extras[/FONT]

---

### Post by FakeOutdoorsman on 2014-10-30
> **Alireza_Zamani said:**
> install media codec :

Unfortunately this will not do anything for this issue, but it will install many additional packages.

The OP is using ffmpeg, which is not provided by Ubuntu 14.04, so it was likely downloaded or compiled (unknown at this point since the console output was not included), and the suggested packages will not affect it in any way.

---

