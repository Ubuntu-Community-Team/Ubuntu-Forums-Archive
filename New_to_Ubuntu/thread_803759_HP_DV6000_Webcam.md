---
title: "HP DV6000 Webcam"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-05-22
i was wondering if someone could help me install my built in webcam in my DV6000 hp laptop. its the only thing that isnt working on my laptop at current so it would be great if i could get it to work. if you need me to paste some data just let me no what you want and ill do it-im new to ubuntu so i may need step by step guide...thanks in advance!

---

### Post by spiderbatdad on 2008-05-22
You might try googling Microdia for a driver.
Also in this thread, the guy got his built in hp cam working:[http://ubuntuforums.org/showthread.php?t=698049](http://ubuntuforums.org/showthread.php?t=698049)

---

### Post by betterthanjordan79 on 2008-05-22
> **spiderbatdad said:**
> Also in this thread, the guy got his built in hp cam working:[http://ubuntuforums.org/showthread.php?t=698049](http://ubuntuforums.org/showthread.php?t=698049)

Just tried this but it said "No camera, or no compatible camera found"

...any other ideas...

---

### Post by ubernuber on 2008-05-22
I would also like to know about this. I just installed ubuntu 8.04 on my dv9000 and my webcam doesn't work :(

---

### Post by Inxsible on 2008-05-22
My built in camera only works with Ekiga. I did get it to work with Kopete once, but it was too iffy and it worked when it wanted to and didn't most of the time.

I just gave up on it. However, Skype does make use of the webcam pretty nicely and the best part is I didnt have to do anything for it to work :)

Unfortunately, that's the most I can offer right now.

---

### Post by betterthanjordan79 on 2008-05-22
ok well thanks to every1 for ur input anyways!

---

### Post by linuxwizard on 2008-05-22
betterthanjordan79

Post the results of the command > lsusb

If I remember right on the HP DV6000, HP uses 2 different  webcams on that model.

---

### Post by betterthanjordan79 on 2008-05-23
it said 
"Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd"

---

### Post by linuxwizard on 2008-05-23
betterthanjordan79

This is the driver you need for your webcam > [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) > your cam > Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd" > is listed as supported > [http://wiki.mediati.org/Supported_Devices](http://wiki.mediati.org/Supported_Devices)

---

### Post by ericson578 on 2008-07-28
I have an hp Pavillion dv9000

lsusb output was: "Bus 007 Device 002: ID 04f2:b023 Chicony Electronics Co., Ltd"

I followed the directions at this location: [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

And now my webcam works in cheese (but still not in flash on firefox 64)

Hope that helps someone :)

---

### Post by ericson578 on 2008-07-30
doah, after a reboot mine is no longer working either. I tried running the modprobe command again but no luck.

---

### Post by Swiekvor on 2009-01-03
tried all, doesn't work, got also dv6000. please help

---

### Post by Swiekvor on 2009-01-03
ok, cheese works now
thx

---

### Post by Kristopher on 2009-01-07
This got my webcam to work also under skype, but not cheese :(

The Ubuntu packages could be downloaded by adding the Arakhnê.org package source into your /etc/apt/sources.list file.
The line to add is:
deb [http://download.tuxfamily.org/arakhne/ubuntu](http://download.tuxfamily.org/arakhne/ubuntu) distname universe

where distname must be replace by one of the supported distributions, one of:
intrepid-arakhne
hardy-arakhne
gutsy-arakhne
feisty-arakhne
The packages are signed by a GPG public key. You must add this key into your apt key list to avoid warnings. To proceed use one of the following methods:
1.Download the public key from the download area and add it into the apt key list: 
wget -q [http://download.tuxfamily.org/arakhne/public.key](http://download.tuxfamily.org/arakhne/public.key) -O- | sudo apt-key add -
2.Import the public key into your local key repository: 
$> gpg --keyserver [www.keyserver.net](www.keyserver.net) --recv-keys 0xBA62BC7E
or 
$> gpg --keyserver keyserver.mobrien.net --recv-keys 0xBA62BC7E
Add the imported public key into the apt key list: 
$> gpg --export -a 0xBA62BC7E | sudo apt-key add -
3.Import the public key into your local key repository: 
$> gpg --keyserver keyserver.mobrien.net --recv-keys 0xBA62BC7E
the imported public key into the apt key list: 
$> gpg --export -a 0xBA62BC7E | sudo apt-key add -

---

### Post by sam-bo on 2010-08-27
I have a dv9000 and the internal webcam is not functional.  Since skype is defaulted through /dev/video1 and not changeable, my usb webcam deosnt appear in skype.  However, cheese and webcam studio both use the usb cam.  how do I go about booting the internal webcam off of /dev/video1?

thanks,

sam-bo

---

