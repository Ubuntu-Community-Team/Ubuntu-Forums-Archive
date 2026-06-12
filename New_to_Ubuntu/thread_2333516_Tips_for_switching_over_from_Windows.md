---
title: "Tips for switching over from Windows?"
date: 2016-08-10
forum: New to Ubuntu
---

### Post by coppyhop on 2016-08-10
I wanna switch over to Ubuntu as it would serve my (Ancient) Hardware well, the only problem is I like playing games and I have an AMD GPU. I really would like the speed boost from Linux, but it'd mean leaving all of my games behind, simply because they don't support linux, or because the drivers are really bad. I would like to do GPU pass through, but it seems like too much hassle to me (And likely on't work, no iGPU on processor, have to use an 8600GT that HAS to go below my 7970). Dual-booting on this Ancient motherboard sounds like a pain because of three minute boot times. Do you guys have any tips for how to get about this?

---

### Post by wildmanne39 on 2016-08-10
The best version is lubuntu for low resource pc's but if you have to play games that are for windows I recommend staying with windows or dual booting, it does not sound like you have enough resources for virtualbox which will let you run windows inside lubuntu even if the games worked they would play well in windows with that setup.

You could use wine but still resources would probably make the experience bad and it is a hit and miss with a computer with a lot of resources.

---

### Post by coppyhop on 2016-08-10
I have a Xeon x5460, 8GB DDR2, and a 7970. EDIT: I'm gonna give up on the gaming part, I'm gonna focus on a faster workstation.

---

### Post by mastablasta on 2016-08-11
for 7970 i suggest installing the older LTS 14.04 (supported unitl 2019) and adding the AMD drivers. don't upgrade to 16.04 yet  at least not until they improve the opensource radeon drivers. it should work ok and you should be able to run quite a few games via Wine. again, lighter desktop environment (lubuntu, xubuntu) will free up resources for other things.

1. what kind of things do you plan to do on computer besides games?
2. what kind of games are you playing?

3. what kind of tips do you need (software?)? do you have any issues?

You can always run it in live session to see how it will all work. you can't install AMD drivers in live session, not unless you use a "Live USB" with persistence. and even then the experience wont' be on par with the full install. still you can use live session to see if all hardware works reasonably well.

---

### Post by mörgæs on 2016-08-11
There are lots of games available for Gnu/Linux. Maybe not the same as you are used to in Windows, but still lots. Take a look at what Steam has to offer or see the [gaming forum]("https://ubuntuforums.org/forumdisplay.php?f=93").

---

### Post by coldraven on 2016-08-11
Buy a second-hand laptop or netbook and put Linux on it. Use that for surfing and keep your old machine for games only.

---

### Post by SeijiSensei on 2016-08-11
One major difference between Windows and most Linux distributions is how software is distributed.  There are few reasons to install programs on Ubuntu from any place other than the official repositories.  Installing programs directly from third-party sites is largely unnecessary.

---

### Post by Impavidus on 2016-08-11
> **coppyhop said:**
> Dual-booting on this Ancient motherboard sounds like a pain because of three minute boot times.

Dual booting doesn't add to your boot time – apart from the few seconds the grub menu shows. Dual booting only takes extra disk space. But you may prefer dedicated Linux and Windows boxes anyway.

---

### Post by DuckHook on 2016-08-11
> **SeijiSensei said:**
> One major difference between Windows and most Linux distributions is how software is distributed.  There are few reasons to install programs on Ubuntu from any place other than the official repositories.+1> Installing programs directly from third-party sites is largely unnecessary.&#8230;and rather dangerous.

@OP

Please see links in my sig: *Linux is not Windows* and *Security Basics*

---

### Post by kurt18947 on 2016-08-12
I have a desktop using onboard graphics - AMD HD4200. The native radeon driver seems quite stable, better than an Nvidia GT210(?) using Nvidia's drivers. I am not a gamer so don't really stress the video subsystem. If you want to dual boot, you might consider an SSD for a boot/OS drive. That should make a nice difference in boot times. The only caveat I'm aware of with SSD is if someone is using Windows XP. XP doesn't have the 'housekeeping' functions necessary for long happy SSD life. Ubuntu & newer Windows are SSD aware. Interestingly I just installed a Patriot Blast from Microcenter ($44.99 after rebate for 240 GB\\:D/). Patriot offers their SSD software for Windows **and** Linux. How refreshing.

---

### Post by oliver-white73 on 2016-08-12
i used an external ssd drive was really fast but a bit annoying if moving around

---

