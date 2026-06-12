---
title: "Duplicate sources"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by the_blue_box on 2011-09-29
Hi all

When ever I run ```
sudo apt-get update
``` all is fine until the end when it says...

```
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/restricted amd64 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/main amd64 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/universe amd64 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/restricted i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/universe i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

``` 

Why is this happening?
I'm running 11.10 beta2 64bit

Any help would be great.

[COLOR="Navy"]The Blue Box[/COLOR]

---

### Post by dino99 on 2011-09-29
> **the_blue_box said:**
> Hi all

When ever I run ```
sudo apt-get update
``` all is fine until the end when it says...

```
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/restricted amd64 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/main amd64 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/universe amd64 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/restricted i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com/ubuntu/ oneiric/universe i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

``` 

Why is this happening?
I'm running 11.10 beta2 64bit

Any help would be great.

[COLOR="Navy"]The Blue Box[/COLOR]

amd64 is 64 bits, while i386 is 32 bits
if you open your eyes you will see that you have mixed them (bad idea, but you can thanks Oneiric to be clever enough to warn you)

---

### Post by the_blue_box on 2011-09-29
Well I didn't mix them intentionally

How would I go about fixing this then?

---

### Post by dino99 on 2011-09-29
sudo gedit /etc/apt/sources.list

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

