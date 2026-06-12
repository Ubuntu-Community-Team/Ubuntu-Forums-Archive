---
title: "Uable to successfully burn a playable DVD Ubuntu 12.04 LTS"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by mdavis1231 on 2012-10-25
I'm having a problem.  I am unable to successfully burn a playable DVD in 12.04 LTS.  I've tried Nero Linux 4, K3b, Brasero, and Gnomebaker.  None of the DVD's will play.  Does anyone know if this is a common problem with 12.04 LTS, or are there some libraries that I'm missing?  HELP!!! :confused:

---

### Post by will1982 on 2012-10-25
> **mdavis1231 said:**
> I'm having a problem.  I am unable to successfully burn a playable DVD in 12.04 LTS.  I've tried Nero Linux 4, K3b, Brasero, and Gnomebaker.  None of the DVD's will play.  Does anyone know if this is a common problem with 12.04 LTS, or are there some libraries that I'm missing?  HELP!!! :confused:

Try burning them slower.

---

### Post by squakie on 2012-10-25
You may need to install libdvdread4 and then run a script contained within that to install libdvdcss (I think that's the name).

---

### Post by mdavis1231 on 2012-10-26
> **will1982 said:**
> Try burning them slower.

Thanks for the suggestion!  I tried this, still didn't work.

---

### Post by mdavis1231 on 2012-10-26
> **squakie said:**
> You may need to install libdvdread4 and then run a script contained within that to install libdvdcss (I think that's the name).

I've made sure that libdvdread4 and libdvdcss2 are both installed.  DVD's will play fine...I'm just unable to burn an .iso to DVD in any Ubuntu compatible DVD burning application whatsoever.

---

### Post by mdavis1231 on 2012-10-26
Can someone please just confirm for me that they _**are**_ able to burn .iso to DVD in Ubuntu 12.04 LTS, and what program you are using to do so?

I'm thinking that I might be needing reinstall Ubuntu 12.04 LTS.  

Thanks!

---

### Post by 25tom on 2012-10-26
Make sure you've got the package 'dvdauthor' installed, just to check. From the sound of what you've been doing it should already be automatically  installed, however. Hope this helps :)

---

### Post by mdavis1231 on 2012-10-26
> **25tom said:**
> Make sure you've got the package 'dvdauthor' installed, just to check. From the sound of what you've been doing it should already be automatically  installed, however. Hope this helps :)

'dvdauthor' is in fact already installed.  It's looking more and more like I need to reinstall Ubuntu 12.04 LTS.

---

### Post by mike acker on 2012-10-26
> **mdavis1231 said:**
> Can someone please just confirm for me that they _**are**_ able to burn .iso to DVD in Ubuntu 12.04 LTS, and what program you are using to do so?

I'm thinking that I might be needing reinstall Ubuntu 12.04 LTS.  

Thanks!

:confused: ISO 

the only time i have burned ISO image is to create a bootable CD.  which certainly would not play in a media player...

take care with these burners to select the right burn format: Audio CD is one thing, Video DVD another, ISO another.  on K3b I would select 'new video DVD project', load my material and then select burn.   "burn image" i would think is for ISO -- to make the disk bootable.  I only just started using K3b but this worked for CD/audio .  

looks like xfburn comes as the pre-installed burner on 12.04  .    i looked at it; it looks pretty good but i still miss CDBurnerXP and MusicBee

CDBurnerXP is easier to understand but we don't have that

---

### Post by mdavis1231 on 2012-10-26
It seems that apparently this is a problem in Ubuntu 12.04 LTS.  I have Ubuntu Ultimate Edition 3.4 installed on my laptop, which is built on Ubuntu 12.04 LTS.  I have the same problem there...I download a video (.avi, .flv, etc.), use DeVeDe to create an .iso image, then use Nero Linux 4 to burn the .iso image to DVD.  Again, I am unable to play the DVD.  This worked perfectly in 10.04 LTS.

---

### Post by mdavis1231 on 2012-10-27
> **mdavis1231 said:**
> It seems that apparently this is a problem in Ubuntu 12.04 LTS.  I have Ubuntu Ultimate Edition 3.4 installed on my laptop, which is built on Ubuntu 12.04 LTS.  I have the same problem there...I download a video (.avi, .flv, etc.), use DeVeDe to create an .iso image, then use Nero Linux 4 to burn the .iso image to DVD.  Again, I am unable to play the DVD.  This worked perfectly in 10.04 LTS.

I've found the answer.  DeVeDe 3.21, which is the version that comes with Ubuntu 12.04 LTS, and is the software that I use to create .iso files, is faulty.  So it isn't Ubuntu 12.04 LTS or any of the DVD burning software that's causing the problem.  I've downloaded DeVeDe 3.23.0 deb package from [http://www.digital-digest.com/software/download.php?sid=1107&ssid=0&did=24](http://www.digital-digest.com/software/download.php?sid=1107&ssid=0&did=24), and it's working perfectly now.  I guess the deb package will have to do until they either update to DeVeDe 3.23.0 in Ubuntu 12.04 LTS, or create a PPA for it.

---

### Post by mike acker on 2012-10-27
> **mdavis1231 said:**
> It seems that apparently this is a problem in Ubuntu 12.04 LTS.{snip}.

I don't think so pard: I'm running 12.04 LTS and so far every burner I tried worked perfect: the CD's play in my car

I've settled on K3b as my choice of a DVD/ISO/CD burner. Remember it is critical to properly direct the program: a CD/Audio project is what you want for your car; Burning [an ISO] image.... is what you do to create a bootable medium -- for installing an O/S

another thing to check on though: I have a brand new ANSUS CD/DVD RW drive installed in my new U-box.  my U-box found it and associated the proper driver to it.  So there you have 2 components to check: is the drive any good, and is it associated with the proper driver ?   

I would try creating a data project -- just copy a .txt file over to a CD and then read it back.  this should tend to verify that the drive and driver are OK

---

### Post by mdavis1231 on 2012-10-27
> **mike acker said:**
> I don't think so pard: I'm running 12.04 LTS and so far every burner I tried worked perfect: the CD's play in my car

I've settled on K3b as my choice of a DVD/ISO/CD burner. Remember it is critical to properly direct the program: a CD/Audio project is what you want for your car; Burning [an ISO] image.... is what you do to create a bootable medium -- for installing an O/S

another thing to check on though: I have a brand new ANSUS CD/DVD RW drive installed in my new U-box.  my U-box found it and associated the proper driver to it.  So there you have 2 components to check: is the drive any good, and is it associated with the proper driver ?   

I would try creating a data project -- just copy a .txt file over to a CD and then read it back.  this should tend to verify that the drive and driver are OK

Please see the above post where I verified that it wasn't a problem with Ubuntu 12.04 LTS, that it was a problem with DeVeDe 3.21.0-1.  Upgrading to a newer version of DeVeDe solves the problem.

---

### Post by mdavis1231 on 2012-10-28
> **mdavis1231 said:**
> I've found the answer.  DeVeDe 3.21, which is the version that comes with Ubuntu 12.04 LTS, and is the software that I use to create .iso files, is faulty.  So it isn't Ubuntu 12.04 LTS or any of the DVD burning software that's causing the problem.  I've downloaded DeVeDe 3.23.0 deb package from [http://www.digital-digest.com/software/download.php?sid=1107&ssid=0&did=24](http://www.digital-digest.com/software/download.php?sid=1107&ssid=0&did=24), and it's working perfectly now.  I guess the deb package will have to do until they either update to DeVeDe 3.23.0 in Ubuntu 12.04 LTS, or create a PPA for it.

UPDATE:  I found today that the fault actually somehow lies with 'ffmpeg', not DeVeDe 3.21.0.   Updating 'ffmpeg' by adding '**ppa:jon-severinsson/ffmpeg' **to Software Sources ([https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric](https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric)), will correct the problem, and DeVeDe 3.21.0 will work correctly.

---

### Post by mdavis1231 on 2012-11-06
> **mdavis1231 said:**
> UPDATE:  I found today that the fault actually somehow lies with 'ffmpeg', not DeVeDe 3.21.0.   Updating 'ffmpeg' by adding '**ppa:jon-severinsson/ffmpeg' **to Software Sources ([https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric](https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric)), will correct the problem, and DeVeDe 3.21.0 will work correctly.

I hope that this post has helped. :)

---

### Post by andrew.46 on 2012-11-10
To burn an iso to dvd perhaps something like the following will help:

```
growisofs -dvd-compat -Z /dev/dvd=my_iso.iso
```

You will of course need to change the name of the iso file to reflect the name of *your* file and perhaps alter your dvd path....

---

### Post by vegas89 on 2012-11-10
I installed devede video creator, you will find it in the ubuntu software center. You can then convert your video's to an ISO format that you can then burn to a dvd.  I have done it and it works great!

---

