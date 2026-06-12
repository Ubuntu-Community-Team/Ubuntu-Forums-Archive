---
title: "No network function at all on a Dell Inspiron 6400"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by m9365428 on 2008-05-05
Hey I'm working on a friends Dell Inspiron 6400 with a Broadcom BCM94311MCG WiFi card and an unknown LAN adapter, neither of witch work and his os is Ubuntu 8.04.
I could probably fix the problem with a tutorial but all the ones I find have to have the internet to work (i.e. they use apt-get or some software that he doesn't even have installed.) For the love of God does anyone know a fix that can be followed by a green-horn that does not require a bloody internet connection.(I'm posting on my windows machine and not his Linux one)

:x I mean really if they have a problem with their network systems they probably need a fix that doesn't use the internet on their machine at least.
Speedy response please finals coming.
M

---

### Post by RequinB4 on 2008-05-05
If they say "wget url" you can copy and paste "url" in a working internet browser to download the file.  you can put it on a flash drive or CD

If they say "sudo apt-get install x" go to packages.ubuntu.com and search for x.  download the .deb (make sure to check you have all the required dependancies listed) and transfer it by any means.  Easiest way to install is to double click the file.

---

### Post by m9365428 on 2008-05-06
O:)Sweet thanks for the timely response. I thought I could download the source files for the program on another computer but I didn't know here to find them. Thanks I will try it out and let you know if it works.
M

---

### Post by m9365428 on 2008-05-10
Well I tried transferring the needed files on a thumb drive but no go. the bloody thing is still busted.
All I get is that a lib is missing and I can't get it from anywhere.
So I give up on the wireless. IF ANYONE KNOWS how to fix a Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) _***WITHOUT***_ the internet let me know because if I can't get this guy some kind of internet within the next week my Uncles shotgun is looking kinda frindly.
](*,)M

---

### Post by inportb on 2008-05-10
What's missing?

---

### Post by esteckis on 2008-05-10
Ok, I have a Dell 6400 and the wireless works fine for me that was in the system already Restricted driver Broadcom B43.  I really suggest that you skip the wireless at first and use Ethernet to see if Ubuntu needs to download any restricted drivers.   Second, if the wireless is encrypted, WEP or WPA even though you set it up, ID name and password, you still will not be able to connect. Apparently (this is what happened to me) I could not connect and shut down the system. I restarted the system 1 hour later and logged on, suddenly a keyring window opened up and asked for my password, I entered the password and it allowed the wireless connection.

There is also this post for a BCM4401

[http://ubuntuforums.org/showthread.php?t=786954&highlight=BCM4401](http://ubuntuforums.org/showthread.php?t=786954&highlight=BCM4401)

---

### Post by m9365428 on 2008-05-10
> **esteckis said:**
>  I really suggest that you skip the wireless at first **_and use Ethernet _**to see if Ubuntu needs to download any restricted drivers.   [http://ubuntuforums.org/showthread.php?t=786954&highlight=BCM4401](http://ubuntuforums.org/showthread.php?t=786954&highlight=BCM4401)

There in lies the problem he has **_*NO NETWORKING CAPABILITY AT ALL*_**:mad:. I don't even think the modem works(note can't try it thanks to phone not dialing outside of campus).
](*,)](*,)](*,)](*,)](*,)
NO LAN
NO WI-FI
probably NO MODEM (see above)

It might help if I clarify that his lan is not even showing up under manual configuration of networking. The computer just flat does not see it. I'm starting to wonder if it is an integrated part of the wi-fi. :-k
M

---

