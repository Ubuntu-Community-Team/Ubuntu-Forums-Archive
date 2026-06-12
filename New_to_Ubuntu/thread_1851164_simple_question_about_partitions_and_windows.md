---
title: "simple question about partitions and windows"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by josephmills on 2011-09-27
Hi there I would first like to thank you for reading this you ROCK. 
So I have to use windows for some things. :( I have not used windows in about 4 years or so. I used gparted to make three partitions. One for ubuntu one for swap and one for windows 7 . 
I installed windoz and now I cant get even see grub. I am guessing that i have to boot a live cd? then mount it or something like that. could some one please walk me though this. Or some links I have been googling but have found nothing. 
Thanks,
The man that misses his ubuntu ;)

---

### Post by garvinrick4 on 2011-09-27
find your linux install
```
sudo fdisk -l
```Lower case L
I will use sda5 in this u[COLOR=Red]se your own.[/COLOR]
Use live cd (install cd using Try Ubuntu) and copy and paste these one at a time.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo reboot.
```
Boot into Ubuntu and:
```
sudo update-grub
```

---

### Post by josephmills on 2011-09-27
Yea that did the trick thanks so much! 
[spoiler]


[img]http://img546.imageshack.us/img546/1587/screenshotfj.png[/img]


[/spoiler]

---

### Post by garvinrick4 on 2011-09-27
Good, now mark this Thread as Solved please, so others may benefit with same.
Upper right in Thread Tools to Solved. You have a nice day.

---

### Post by josephmills on 2011-09-28
8 hours later and I can not take windoz anymore. I got the blue screen of death after installing a bunch of different drivers for it. my sound also did not work I manged to find the driver for that. I thought that when I paid 162.00 usd that I was getting software that worked out of the box. This is not the case I can not believe how many hours I put into that. I will keep winoz 7 on a box that I dont use. then I will put that box in the closet and let it stay there until it gathers dust or until I want to get frustrated. I just cant believe that something that costs that much money has all them bugs. I Never installed any thing that was a torrent or some crazy link as I felt like I was already "out in the open" All things that I downloaded where from nvidia and dell and windows and I still got the blue screen of death. I am never ever going to try to go back to windoz ever again. not only is gnu/linux free as in price but also gives me a mind set. I mean I spent hours trying to figure out what my soundcard was. When I finally gave up and booted 11.04 again and did a lspci -nn then rebooted windows to go get the driver. How does this happen ? how can ubuntu sound and works out of the box and and the nvidia card is 3x easier to handle. How does this happen that over 80% of the world is using an os that gets the blue screen of death within 8 hr ? I mean every one is paying for the software. And you have no options to change the source even If I or you could. What is the world coming to when I have to go out and spend 162.00 usd and get nothing but trouble. Yet I can go and download ubuntu for free get 5 gigs of online storage a (in my opinion) more user friendly os  And most of all a piece of mind. I would like to thank you all so much for whatever kinda energy that you may have put into the open source/free software scene. I am converted and am never going to go back. thanks for reading my rant ):P

joseph

---

### Post by Phateless on 2011-09-28
> **josephmills said:**
> 8 hours later and I can not take windoz anymore. I got the blue screen of death after installing a bunch of different drivers for it. my sound also did not work I manged to find the driver for that. I thought that when I paid 162.00 usd that I was getting software that worked out of the box. This is not the case I can not believe how many hours I put into that. I will keep winoz 7 on a box that I dont use. then I will put that box in the closet and let it stay there until it gathers dust or until I want to get frustrated. I just cant believe that something that costs that much money has all them bugs. I Never installed any thing that was a torrent or some crazy link as I felt like I was already "out in the open" All things that I downloaded where from nvidia and dell and windows and I still got the blue screen of death. I am never ever going to try to go back to windoz ever again. not only is gnu/linux free as in price but also gives me a mind set. I mean I spent hours trying to figure out what my soundcard was. When I finally gave up and booted 11.04 again and did a lspci -nn then rebooted windows to go get the driver. How does this happen ? how can ubuntu sound and works out of the box and and the nvidia card is 3x easier to handle. How does this happen that over 80% of the world is using an os that gets the blue screen of death within 8 hr ? I mean every one is paying for the software. And you have no options to change the source even If I or you could. What is the world coming to when I have to go out and spend 162.00 usd and get nothing but trouble. Yet I can go and download ubuntu for free get 5 gigs of online storage a (in my opinion) more user friendly os  And most of all a piece of mind. I would like to thank you all so much for whatever kinda energy that you may have put into the open source/free software scene. I am converted and am never going to go back. thanks for reading my rant ):P

joseph

As someone who is just getting started in Linux I have to say that was SO entertaining to read! Lol.  :)

---

