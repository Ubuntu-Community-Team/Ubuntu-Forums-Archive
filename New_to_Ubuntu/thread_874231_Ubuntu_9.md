---
title: "Ubuntu 9"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by seramai on 2008-07-29
I thought it was due out at the end of July.

Also, what is the Ubuntu program used to talk to routers.  

I am new to Ubuntu and am about ready to load it on my laptop and I want to use it to talk to Cisco routers.

In other words, what is the Ubuntu equivalent of Hyperterminal?

Thank you,

seramai

---

### Post by Sef on 2008-07-29
>  Ubuntu 9
I thought it was due out at the end of July.


There is no such thing as ubuntu 9.  The next update is Intrepid Ibex, 8.10, which is due out 30 Oct 08.

---

### Post by AndyCooll on 2008-07-29
And you can usually talk to your router via a web interface, e.g typing the IP address of your router into your web browser (typically it is 192.168.1,1 or similar).

:cool:

---

### Post by halitech on 2008-07-29
> **seramai said:**
> I thought it was due out at the end of July.

Also, what is the Ubuntu program used to talk to routers.  

I am new to Ubuntu and am about ready to load it on my laptop and I want to use it to talk to Cisco routers.

In other words, what is the Ubuntu equivalent of Hyperterminal?

Thank you,

seramai

the normal release dates are in April and October of each year and the first number represents the year (ie 8.04 - 2008 release year, April release)

Are you referring to having it get an IP address or do you actually program it through hyperterminal in windows? If its a telnet connection, the terminal will allow you to do that.

---

### Post by jlenain on 2008-07-29
Hello seramai,

In fact the version number for Ubuntu just tells you the year/month of issue, so 8.04 means it was released on April 2008, so Ubuntu 9.xx would be released... in 2009 ! As simple as that !
In fact, if I understood well, Ubuntu releases occur twice a year, just following the Gnome releases.

Cheers

---

### Post by bodhi.zazen on 2008-07-29
The numbering system for Ubutnu releases is year.date

2008 = 8

Releases are scheduled every 6 months , so next release if 8.10 :twisted:

---

### Post by seramai on 2008-08-01
Thank you all.  I sure got schooled.

---

### Post by Mike'sHardLinux on 2008-08-01
Cisco routers aren't like the typical netgear home router. Some newer equipment often come with a web interface, though. But it's still a whole different animal. But when you are learning Cisco, you generally focus on commandline.

Hypterminal is a basic old fashioned comm program. While some comm programs, like Procomm, can do telnet, that is not the same thing.

Two comm programs in Linux you can use to talk your Cisco equipment are minicom and seyon. They are in the repos.

Seramai, are you taking Cisco classes? I am also learning Cisco. Very interesting stuff.

I just found cutecom, also in the repos. If you are used to hyperterminal, try cutecom.

---

### Post by fwre01 on 2008-08-01
yeah, Cisco is a whole different kettle of fish, i use minicom to console into Cisco equipment. What model routers are u using?

---

### Post by Mike'sHardLinux on 2008-08-01
fwre01, nice to chat with another cisco head. :guitar:

I am using 2501, 2611xm, and 3640 at home. All I can afford. At school we are learning on 2811 and 2620. At work is where the real fun is!! I log into Cisco, Juniper, and Vanguard routers all day troubleshooting WANs. I am learning a lot, but still so much more to learn.

---

### Post by fwre01 on 2008-08-02
yeah i dont think theres many cisco ppl hang out here (or at least i havent bumped into them.)  I havent even heard of vangaurd routers!! whats the Cisco course your learning atm? Im just finishing up my CCNP

---

### Post by seramai on 2008-08-03
Two comm programs in Linux you can use to talk your Cisco equipment are minicom and seyon. They are in the repos.

What are repos?

Seramai, are you taking Cisco classes? 

Yes.

I am also learning Cisco. Very interesting stuff.

---

### Post by CatKiller on 2008-08-03
> **seramai said:**
> What are repos?

[Repositories]("https://help.ubuntu.com/community/Repositories").

---

### Post by wirelessmonkey on 2008-08-04
I use gtkterm, as it's quicker to configure than minicom on new setups, and much easier to assign a tty to my keyspan usb/serial adapter.

---

