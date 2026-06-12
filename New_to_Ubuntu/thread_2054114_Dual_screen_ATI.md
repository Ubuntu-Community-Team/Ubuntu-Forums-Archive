---
title: "Dual screen ATI"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by ecoh419 on 2012-09-06
Hello all

Here's my problem

I have two screens..... one is a 22"led monitor and the other a 42 inch led tv. In windows 7 I run xbmc on the second monitor. I'm trying to mimic the same function in setting xbmc to display on the tv only.

So I installed the latest x64 linux drivers from ATI. I configured (using the catalyst control panel) using single display (multi desktop)

I then got a white screen with black x so I enable xinerama. with xinerama enable I got the displays to work correctly, however I received an error when I tried to enter display settings to change the launcher location.... the error message was " "randr extension not present ="

So I tried to install libxandr2 using terimal and this command 

sudo apt-get --reinstall install xserver-xorg libxrandr2 x11-xserver-utils

after the packages installed I rebooted and I still get the error message

I'm at a loss now because I can't find a solution for the randr error message.

I'f my specs are important amd athx2 6400+ ghz 8 gigs ram radeon hd6950

---

