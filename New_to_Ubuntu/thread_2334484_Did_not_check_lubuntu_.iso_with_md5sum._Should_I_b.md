---
title: "Did not check lubuntu .iso with md5sum. Should I be worried?"
date: 2016-08-19
forum: New to Ubuntu
---

### Post by dragonegg on 2016-08-19
I recently downloaded Lubuntu 16.04.1 from [here]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") and installed it on my laptop. Only afterwards did I see that the help page recommends checking .iso file for authenticity and safety by using the md5sum command and comparing the hash. So I checked a .iso that was of the same kind and downloaded around the same time as the one that I installed, and the hash matched.

Should I be worried that I originally neglected to check the file? Nobody would want to hack me but I'm still paranoid about security issues.

---

### Post by RobGoss on 2016-08-19
It is always good to check the md5sum this guide might help you understand about it a bit more [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) I can't speak for others but I never had any problems with any of the Ubuntu downloads what so ever

---

### Post by grahammechanical on 2016-08-19
One purpose of the md5sum is to verify that the ISO image has not been corrupted during the download process or during the burning of the image to the DVD/USB memory stick. A corrupted ISO image might just be the reason for the live session failing to load or a broken installation.

Another purpose is to verify that the ISO image is authentic. But if the same web site that is providing the ISO image is also providing the md5sum then everything comes down to whether you trust that particular web site

It is like someone phoning and pretending to be your bank. They provide a phone number so that you can verify that the caller really is from your bank but when you phone that number you do not get through to the bank but to another criminal who pretends to be the bank.

If you cannot trust the Lubuntu/Ubuntu download site then the fact that the md5sums match is no guarantee that the ISO image does not contain malicious software.

I trust the Ubuntu download site. I have never had malicious code installed on my machine either by running a Ubuntu live session or by installing Ubuntu or any of its flavours.

Regards

---

### Post by RobGoss on 2016-08-19
> 

I trust the Ubuntu download site. I have never had malicious code installed on my machine either by running a Ubuntu live session or by installing Ubuntu or any of its flavours.

Regards


I second that it has always worked for me hands down

---

### Post by yetimon_64 on 2016-08-19
> **grahammechanical said:**
> One purpose of the md5sum is to verify that the ISO image has not been corrupted during the download process or during the burning of the image to the DVD/USB memory stick. A corrupted ISO image might just be the reason for the live session failing to load or a broken installation. ...

This is what I see the main purpose of the md5 is for OP. Not so much a check for malicious code as such; as grahammechanical goes on to note the same site supplying the download also supplies the md5 checksum for the file, meaning the md5 is not such a good idea for checking for such threats anyhow.

> Should I be worried that I originally neglected to check the file? If the installation is working smoothly, no not a worry in my opinion. 

> ... I never had any problems with any of the Ubuntu downloads what so ever          Same here OP when using the ubuntu.com images; I have been using various ubuntu and xubuntu images, including alternate and mini images with ubuntu, for the last 8-9 years now. No problems with malware etc, only one or two (of many) downloads corrupted (during the download process), which by the way were picked up by md5 checks then re-downloaded without any further problems.

---

### Post by nexhuntr on 2016-08-20
Not checking the ISO has been a big pain in my backside. I downloaded right off of the website and got two very corrupted ISO files that didn't pass md5sum. But one passed the check disc integrity option on boot once. It took three torrent downloads to get one to pass the md5sum, and another five more to pass two disc integrity and two md5sum. I went all hard core on getting a stable installer USB

---

### Post by coldraven on 2016-08-20
If you choose to download using the torrent option then the iso is automatically checked.
Go here, click on a distribution, the scroll down to see all the options.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

