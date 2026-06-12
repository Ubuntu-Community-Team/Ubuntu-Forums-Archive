---
title: "Nothing later than 10.04 works"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by misterz on 2012-06-28
Hello,
On my system (AMD Sempron 2800+) nothing beyond 10.04 works. That is, when I install versions beyond that, the screen doesn't the icons, drop downs, etxc... There's background but nothing clickable. What's wrong?
-Mark

---

### Post by mapes12 on 2012-06-28
Are you doing a clean fresh install and overwriting 10.04?

---

### Post by BBQdave on 2012-06-28
> **misterz said:**
> Hello,
On my system (AMD Sempron 2800+) nothing beyond 10.04 works.

On my Dell Inspiron 1100 (1 GHz Celeron with 1 gig of ram), everything beyond 10.04 was buggy too. I switched to Debian 6, a great solid distro which I used for a good while then recently switched to Fedora 16 Xfce.

I would suggest having as much ram as possible on your old system, and then try Debian 6 or Fedora 16 Xfce :D

---

### Post by Enigmapond on 2012-06-28
If 10.04 worked well the 12.04 would work too. Do a fresh install of 12.04 and I think the issues will resolve.

---

### Post by kd5mkv on 2012-06-28
Maybe a desktop  issue, Unity started after 10.4. I am waiting until the end of 10.4 support on 2013 to change my version. Have you tried to run gnome,kde versions of Ubuntu. Try forums or google for the instructions to
install Ubuntu with another desktop environment. I tried 12.04 and couldn't
get a single program to run, beacause unity had problems running on my machine.

---

### Post by BBQdave on 2012-06-28
> **Enigmapond said:**
> If 10.04 worked well the 12.04 would work too. Do a fresh install of 12.04 and I think the issues will resolve.

On my hardware, the latest Ubuntu (s) were buggy, in particular the video.

**Debian 6** with backports is a good option for solid performance and if your are coming from Ubuntu 10.04, Debian 6 will be familiar.

For modern applications and solid performance, I would recommend **Fedora 16 Xfce**. Again, a familiar DE if you are coming from Ubuntu 10.04.

I have my older notebook (dell inspiron 1100), which was my work horse for a good while, as a secondary machine now. My new notebook is a Toshiba C655, and testing Gnome 3 (Unity) was buggy. I landed on F16 Xfce which is a nice blend of Gnome and Xfce 4.8.

Maybe down the road as Gnome 3 becomes more stable (hopefully with the release Debian 7) it will be a more viable choice.

---

### Post by mapes12 on 2012-06-28
If Unity doesn't work for you there are loads of other Desktop environments to choose from. Google is your friend. Here's a good guide from a well trusted source:-

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

---

### Post by misterz on 2012-06-29
> **mapes12 said:**
> Are you doing a clean fresh install and overwriting 10.04?

Yes. I've both arrived at versions greater than 10.04 by upgrading as well as fresh installing from a CD.

---

### Post by mastablasta on 2012-06-29
AMD Sempron 2800+ is only the CPU but the troubles might come from GPU. what are your system specs? you might have encountered a known bug.

---

### Post by mojo risin on 2012-06-29
I havent tried Fedora yet, but I know that dedoimedo.com wasnt impressed by the recent release-- if you want xfce Xubuntu had a much better performance.

---

### Post by misterz on 2012-06-30
> **mastablasta said:**
> AMD Sempron 2800+ is only the CPU but the troubles might come from GPU. what are your system specs? you might have encountered a known bug.

Would you tell me where in the program I can go to get a thorough listing of the hardware's specs so I can answer your question? Thx!

---

### Post by misterz on 2012-07-01
> **mastablasta said:**
> AMD Sempron 2800+ is only the CPU but the troubles might come from GPU. what are your system specs? you might have encountered a known bug.

Can you tell me where/how to get complete system info for you?

---

### Post by Dedoimedo on 2012-07-02
Did you try running lspci?
Try with lspci -v first, as root.
Dedoimedo

---

### Post by kansasnoob on 2012-07-02
> **misterz said:**
> Would you tell me where in the program I can go to get a thorough listing of the hardware's specs so I can answer your question? Thx!

I typically just use the following commands,

General CPU info:

```
cat /proc/cpuinfo | head -10
```

Graphics chip info:

```
lspci | grep VGA
```

Memory info:

```
free -m
```

Audio info:

```
lspci | grep Audio
```

Network info:

```
lspci | grep Ethernet
```

---

