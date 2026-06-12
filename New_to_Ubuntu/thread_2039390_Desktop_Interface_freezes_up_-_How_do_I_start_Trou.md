---
title: "Desktop Interface freezes up - How do I start Troubleshooting?"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by henrypootel on 2012-08-08
I have this problem where after running for a period of time (seems random, but is usually about 30 minutes to an hour), the GUI on my system just completely stops responding. I can move the mouse cursor, but it won't interact with anything, and nothing responds to keyboard commands.

The only way for me to get back up and running is to restart the machine, where i get another period of tie before it happens again.

I have tried several different ubuntu flavours, and they all do it - I've checked standard ubuntu in 32 and 64-bit varieties, xubuntu 64, gnome-shell remix 32 & 64 bit, and now Voyager 64 (xubuntu based). All of them have the problem. I also briefly tried out the new Fedora and didn't encounter the problem (but didn't like Fedora at all), nor do i encounter it in my other partition running Arch.

What I want to know is, how do I start troubleshooting for this? is there some log that I should look at? Also, has anyone else had a similar experience?

I am not an absolute beginner, but i've not done a lot of actual troubleshooting in Linux, so i'm not sure how to start out.

The system is a Sony Vaio Z1 - it's running an i7 with 8GB of memory on a FakeRAID array of 4 SSDs. the graphics is a dual-system, intel GMA and nVidia 330. I have tried both in ubuntu and they both have the problem still, so it doesn't seem related to that.

It's also worth noting that i regularly use Windows 7 on this machine as well and it runs fine, so it doesn't seem to be any underlying hardware problem.

---

### Post by acimi66 on 2012-08-08
Do You have a launchpad account?
it might be a good place to start in terms of getting help and narrowing down the problem.    [https://launchpad.net/](https://launchpad.net/)

It might help if you can add info from the log files. this guy has a nice tutorial on locating them.

[http://www.ghacks.net/2009/02/16/learning-linux-log-files/](http://www.ghacks.net/2009/02/16/learning-linux-log-files/)

I hope that helps.

---

### Post by henrypootel on 2012-08-08
that looks good - thanks, I'll start there.

---

### Post by megamister on 2012-08-08
I just started having the same type of issues and have been troubleshooting it for a week now. What I have found out is there are vid card driver issues with some of the newer drivers. I was using an old AGP ATI 9600, on 10.04 Server with Kubuntu, now most of the new versions are not working with my server box. I got a unusual freezeup when I went to reboot my server. It kept hanging on the loading screen. So I thought good point to upgrade. Several installs later, and hours of searching. I found a different Nvidia 6600GT to throw in. Ok great at least I can get a live CD working. But some versions are working better than others. But there is something going on. Many people are having black screens and lockups starting more with 12.04. I have tried Linux Mint, and Kubuntu and it appears to be the same or very similar with both. With the ATI vid card, I couldn't load any live CD or run anything until I swapped cards.

Some versions I could get to load by setting "nomodeset" from the GRUB menu screen and press F6.Or you can press "e" at the Grub load screen and type it in after "quiet screen" then press CTRL-X to continue loading. Some would load and just get a freeze requiring reboot. Linux Mint 13 was running good but then would start freezing for 10 sec, then ok for 5 sec and cycle like that then would freeze everything on the desktop. So far I have had the greatest success with Kubuntu 12.10. But still have gotten an error at times saying something like Neavou errors loading...line 1 then same but line 2...and everything is frozen and resorts to a black screen freeze. 

All I'm saying is...I think there are some major graphic issues right now.

---

