---
title: "update manager wants to install BIND program??"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Sonoran Desert Rat on 2012-09-14
Anyone know what the program BIND is and what it does? I am on a personal laptop. It says it's an important update but it's for servers? I don't want to open a "back door". Please and help? 

Thanks ahead!

---

### Post by oldos2er on 2012-09-14
If you have bind installed, let Update Manager update it (it might be installed by default, I don't know). If it's not installed it won't be updated.

---

### Post by 2F4U on 2012-09-14
The bind program is used for DNS resolution and is a de facto standard in Linux/UNIX systems.

[http://en.wikipedia.org/wiki/BIND](http://en.wikipedia.org/wiki/BIND)

---

### Post by Sonoran Desert Rat on 2012-09-14
> **oldos2er said:**
> If you have bind installed, let Update Manager update it (it might be installed by default, I don't know). If it's not installed it won't be updated.

Ok, I updated. Thanks!

---

### Post by Sonoran Desert Rat on 2012-09-14
> **2F4U said:**
> The bind program is used for DNS resolution and is a de facto standard in Linux/UNIX systems.

[http://en.wikipedia.org/wiki/BIND](http://en.wikipedia.org/wiki/BIND)

Do I need this for my Internet connection? I don't personally know much about servers and have never used one...that I know of. :confused: My Internet connection is weird and I don't understand it at all. :( I've been looking too.

---

### Post by marinara on 2012-09-16
theoretically, you don't need it.  however, I don't know how to remove it, or what removing it will do.  expecially since it's included by default in ubuntu

---

### Post by oldos2er on 2012-09-16
> **Sonoran Desert Rat said:**
> Do I need this for my Internet connection? I don't personally know much about servers and have never used one...that I know of. :confused: My Internet connection is weird and I don't understand it at all. :( I've been looking too.

What exactly does "weird" mean?

On 12.04, bind9-host and libbind9-80 appear to be installed by default (on the desktop version, not server). I'd be very careful about removing them. They don't take up much disk space, 175 kB and 102 kB respectively.

Edit: Also, if you remove a package that affects networking, a simple **sudo apt-get install bind9-host** might not work to fix the problem. Installing packages on an offline computer certainly is possible, but is not the easiest thing to do for a person new to Linux.

---

### Post by Sonoran Desert Rat on 2012-09-16
I think my Internet is running on it. I don't have wireless and when I shut networking off I don't get Internet at all. So I updated and am keeping it. 

Weird is normal because if your normal then your weird because in the end, no one is normal. :D ...and yes, I spelled it badly. ;)

---

### Post by oldos2er on 2012-09-17
> **Sonoran Desert Rat said:**
> I don't have wireless and when I shut networking off I don't get Internet at all. 

I don't have wireless either (wired desktop). How exactly do you shut off networking? What you've said in the quote sounds like it's working as designed.

---

### Post by Sonoran Desert Rat on 2012-09-17
I have a "Wired Network Connection"  symbol on the right end of my taskbar I can click into.

---

### Post by oldos2er on 2012-09-17
Ok. It seems then that everything's working as it should.

---

### Post by Sonoran Desert Rat on 2012-09-17
I had advice on this forum to turn networking off because I don't need it as this is a personal, home laptop. I was trying to figure out how to do that but it looks like I can't because that is how I connect to the Internet.

---

