---
title: "Setting up an internet connection"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by RickXX on 2008-05-21
Hey guys,

Maybe I should start with introducing myself and give some background information. I am Rick, 18 years old and writing this new thread in Holland because i'm Dutch. That could declare the not-very-good-english in my post.

I just said goodbye to Windows and installed Ubuntu on my system. No dual boot, just Ubuntu. The instal worked out perfectly. Ubuntu is up and running on my system except the Internet. I'm can't establish an internet connection. My internet worked fine on Windows and also in the demo of Ubuntu. So the cable works fine.

I have no experience with Linux or Ubuntu what so ever so I'm now arriving at a point where I simply just don't know what to do. I have a AMD Athlon 64 bit, Ati Radeon 6600, 512 mb memory. I also installed the Athlon64 bit version of Ubuntu. I'm using version 8.04, the hardy heron released in April '08. 

I think that my problem has anything to do with my network card. I've got a Marvell Yukon Lan-Driver, cable connected. I did some search work and I noticed more people had a similiar problem in combination with this network card. I didn't find a solution in my search results, or a solution that I can understand. 

I hope someone knows the awnser to my question and can help me continue to discover the world of Linux.

Thanks in advance!

RickXX

---

### Post by shifty_powers on 2008-05-21
can you post the ooutput of

```
lspci
```

---

### Post by digitalvectorz on 2008-05-21
You can possibly try to install/download the drivers from

[http://www.marvell.com/drivers/search.do;jsessionid=Tt5jL0hQG1pBrv5RW2QdyrQ8J1JWLCSR6M4dL4xKSHwscKzJmWQs!-1828401091](http://www.marvell.com/drivers/search.do;jsessionid=Tt5jL0hQG1pBrv5RW2QdyrQ8J1JWLCSR6M4dL4xKSHwscKzJmWQs!-1828401091)

I haven't tested them, fyi.

If you get it from another location, copy the downloaded file (should be install_v10.60.2.3.tar.bz2 as the filename) then copy it onto your linux box via USB or something.  If it shows up in the GUI, then you should be able to select a folder and extract the contents to whichever folder you specify.  Then if there is an install or readme file, just type

```

cat <install_or_readme_filename>

```

and it should give you instructions on how to install it.

Hope that helps

---

### Post by RickXX on 2008-05-21
Well guys, yelled to early. I'm now typing this post at a Ubuntu system! This solution worked for me, I typed sudo dhclient in the terminal. It is said it changes the network settings back to automatic.

Shifty_powers. Thanks for your VERY fast respond. I appreciate it very much I only guess that lspci is not necessary anymore :).

edit; digitalvecorz, also thank you for your time!

---

### Post by shifty_powers on 2008-05-21
heh, well i used this forum at first, so i know how nice it is to have a fast response ;)

---

### Post by pdtpatrick on 2008-05-21
Yes - people in these forums are sooo quick! its amazing .. lol

---

