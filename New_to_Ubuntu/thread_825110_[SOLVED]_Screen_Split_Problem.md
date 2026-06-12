---
title: "[SOLVED] Screen Split Problem"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Techpenguin on 2008-06-10
Hi Everyone. I am Having a problem with an 8 year old Dell Inspiron 5000e. The screen looks like this when I boot it up.

[http://ubuntuforums.org/attachment.php?attachmentid=73585&stc=1&d=1213133161](http://ubuntuforums.org/attachment.php?attachmentid=73585&stc=1&d=1213133161)

I have tried changing the screen resolution and refresh rate. Neither work. Is it because of the ATI card in the computer, or something else? should I just install and older distro?

P.S. If anyone read the post by elvatonadam, I tried the solutions from there.

---

### Post by gr4nf on 2008-06-10
So it opens the file browser by itself when you boot up, or did you open it and it does that to it?

Either way, it looks like your computer is having trouble running gnome. Do you know how much RAM you have? Any other specs?

---

### Post by Techpenguin on 2008-06-10
I have either 256 or 512 mb of RAM , I opened the file by myself to illustrate the problem, and no, it happened before I opened it. sorry, no other specs.

---

### Post by gr4nf on 2008-06-10
If it is in fact 256mb, that may well be too little. You might try an old version of Xubuntu, or Debian, which is very similar to Ubuntu, but tends to be easier when it comes to Sys Reqs.

---

### Post by Techpenguin on 2008-06-10
Thanks. I had 8.04 xubuntu on the laptop at one point, but I had the same problem.

---

### Post by gr4nf on 2008-06-10
Really? if even xubuntu didnt work well, it might be a fried RAM card. Is your RAM split between two different cards? If so, one of them might be bad.

Also, RAM is cheap these days. You can pick up 2 gigs for 50 dollars. Upping your system to a gig of RAM would be easy.

---

### Post by lavinog on 2008-06-10
what video driver is in use
what ati video card do you have?
If ram is suspected run memtest+
I suspect the video card...the older ati cards don't have very good support with the newer drivers

---

### Post by gr4nf on 2008-06-10
To find out all this hardware information, run top, or htop. To run the latter of the two, you must first:
```
sudo apt-get install htop
```

---

### Post by lavinog on 2008-06-10
also 256mb is not alot but you should still be able to run ubuntu...it will run slow but it should still run...I ran it on 128mb before.
you may want to switch to xfce.

---

### Post by lavinog on 2008-06-10
> **gr4nf said:**
> Really? if even xubuntu didnt work well, it might be a fried RAM card. Is your RAM split between two different cards? If so, one of them might be bad.

Also, RAM is cheap these days. You can pick up 2 gigs for 50 dollars. Upping your system to a gig of RAM would be easy.

older ram is more expensive...also some dell systems during that time used rombus ram which last time I checked it was $300 to upgrade to 512mb on my brothers dell.

---

### Post by gr4nf on 2008-06-10
> older ram is more expensive
only if you buy it from a consumer store. If you have a friend throwing away an old computer, or a school nearby with some fried ones, you could probably get a hold of some old 512 cards for free.

---

### Post by Techpenguin on 2008-06-10
Thanks you guys, um I can't get htop, the internet isn't working on it, keeps asking for WEP pass repeatedly. It's a laptop, so it might be hard to up the RAM. I think it might be the RAM because I saw it had 512 mb a while ago, but now memtest says 256... so either one is wrong or RAM got fried.

---

### Post by gr4nf on 2008-06-10
When it asks for a WEP password, thats the wireless router asking for the WiFi password. Is it your network? If so, try your wifi password. If it is, but you dont know the password, then you have a very large problem. You should call the people who sold you it and ask what the password would be.

---

### Post by Techpenguin on 2008-06-10
I know the password, it's just that whenever I enter it I hit connect and a minute later it pops back up and asks for the pass again. I've tried the pass in 128 bit passcode, and 64-128 bit hex. it's supposed to be hex but the same thing happens to both.

---

### Post by Techpenguin on 2008-06-10
Hey Everyone! So, I found one of my older CD's with Ubuntu 6.06 and I installed that and I now have a fine working Ubuntu Laptop!
Cheers!

---

