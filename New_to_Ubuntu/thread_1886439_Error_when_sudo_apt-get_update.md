---
title: "Error when: sudo apt-get update"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by gannon5197 on 2011-11-24
Hi there! Yet another noob here. I came to ubuntu because I wanted to start building for android. I came across a bit of a problem: I added this: sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" and all went well. Then when I added: sudo apt-get update, i got this error: 
```
E: Malformed line 6 in source list /etc/apt/source.list (dist parse)
E: The list of sources could not be read.
```
That was odd. So I went to ubuntu software center and it wouldn't let me open it. Weird again? So I went to update manager from the applications and got the same exact error message as above. 
Here is my source.list if you guys need it:
```
# /etc/apt/sources.list

deb http://archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/oneiric-updates main restricted universe multiverse
deb http://archive.canonical.com/lucis partner
deb-src http://archive.canonical.com/lucis partner
deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner
deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner
```

---

### Post by snowpine on 2011-11-24
It's "lucid" not "lucis." :)

You can fix the file with your favorite text editor, for example:

```
gksu gedit /etc/apt/sources.list
```

---

### Post by gannon5197 on 2011-11-24
Fixed that and still same error...

---

### Post by dwasifar on 2011-11-25
You are missing a space between the URL and the word "lucid" in line 6 and 7.

You also don't need to have the same pair of repos repeated three times.  Once each will suffice.

---

### Post by gannon5197 on 2011-11-25
Okay. THANK YOU. I worked!

---

### Post by ExileAmongYou on 2011-11-25
I just checked my sources.list, and mine reads:
```
deb http://archive.canonical.com/ubuntu oneiric partner
```

...so maybe try 
```
deb http://archive.canonical.com/ubuntu lucid partner
```
instead of what you've got.

---

### Post by lolpenguin on 2011-11-25
> **ExileAmongYou said:**
> I just checked my sources.list, and mine reads:
```
deb http://archive.canonical.com/ubuntu oneiric partner
```

...so maybe try 
```
deb http://archive.canonical.com/ubuntu lucid partner
```
instead of what you've got.

Don't change it. The difference between oneiric and lucid is the OS version, so if you make it oneiric you will recieve packages from 11.10 instead of your version (10.04).

---

### Post by oklokl on 2011-11-25
bug
rebooting..

removal -> control panel menu  -> source edit 
sudo apt-get update --fix-missing

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric](http://ubuntuguide.org/wiki/Ubuntu:Oneiric)

---

