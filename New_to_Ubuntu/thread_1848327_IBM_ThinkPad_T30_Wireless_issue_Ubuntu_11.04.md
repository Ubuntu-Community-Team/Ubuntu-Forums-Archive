---
title: "IBM ThinkPad T30 Wireless issue Ubuntu 11.04"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by Bach.Greenville IT on 2011-09-22
Ok all, 
This is *rather *urgent...
I am the IT head for BACH.greenville ([bachgreenville.com]("http://www.bachgreenville.com")) and am an absolute noob. :p
New company, no experience, but quite a few contacts who got me started.
I received some old laptops to distribute at will, and because they were old, I decided not to use the HATED windows. I put Ubuntu 10.04 on one, and then upgraded to .10, and then to 11.04, I loved the new UI, and proceeded to do the same on the rest of the laptops. (Dell Latitude D610, IBM ThinkPad T30, and IBM ThinkPad T23.) The Dell and the T30 have wireless integrated in them, and I solved the Dell wireless issue (I will post a solution to that in another thread) but when upgraded on the T30, the wireless is finding my home router, but is refusing to connect. (That's the real issue.) I am supposed to release this laptop tonight, and don't want to do that with the wireless unusable.  
Here is the lspci network info...

~$ lspci | grep Network
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

I hope that helps. 
Please post your answers like a Progressive Taxi, I have some experience with ubuntu, and terminal, but not much. Thanks!

---

### Post by wolfen69 on 2011-09-22
Can I ask why you installed 10.04 and then upgraded twice to 11.04? You could have just installed 11.04 to start with.

---

### Post by Bach.Greenville IT on 2011-09-22
Well, no reason actually, but I did end up reinstalling 11.04 because of upgrade errors.

---

### Post by wolfen69 on 2011-09-22
Are you seeing available wireless networks?

---

### Post by Bach.Greenville IT on 2011-09-22
Yes, I just can't connect. When I select "2WIRE174" it gives me the authentication dialogue, but I have no WPA encryption option.
Here is what I have:
None
WEP 40/128-bit Key (HEX or ASCll)
WEP 128-bit Passphrase
LEAP
Dynamic WEP (802.1x)

In Network Connections, I can select "Wireless" and then "Edit" and THEN I have WPA, but it doesn't make a difference if I select them and save, or not. 

Thank you so much for your help!

---

### Post by Bach.Greenville IT on 2011-09-22
I just logged out, and then back in, rechecked, and now it says... Wireless Networks, device not ready. Ugggh! This is horrible! Sorry for being such an idiot.

---

### Post by wolfen69 on 2011-09-22
It could be that your computer is using an oddball wireless card, and it is just not supported in ubuntu. I would download 11.10 beta (daily build) and try the live cd to see if you can get wireless. Sometimes hardware support changes from release to release. Here it is: [http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.iso)

---

### Post by Bach.Greenville IT on 2011-09-22
Thanks! I am Burning the CD now. Will let you know how it went.

---

### Post by Bach.Greenville IT on 2011-09-22
Nope, Thanks for the suggestion, but just keeps not connecting, and then bringing up the authentication dialogue, (and yes, I am positive the key is right, I checked it at least 3 times. And I am using the Dell right beside it on the same network with the same key.) Any other suggestions? Should I upgrade anyways?

---

### Post by wolfen69 on 2011-09-22
I believe you need to do:
```
sudo apt-get install linux-wlan-ng-firmware linux-wlan-ng hostap-utils
```
Then reboot.

---

### Post by Bach.Greenville IT on 2011-09-24
Alright. Thank you. I will do that as soon as I get the chance, but for now (because I can't access the computer anymore) I will have to say it is just unusable. Which will be alright for now. Thank you very much for your help. You seem very knowledgeable and I appreciate it exceedingly. Look for my solution to the Dell Latitude D610 Wireless Solution in 11.04, and 11.10 soon.

---

