---
title: "MD5sum failed"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by Steelmesh on 2012-02-21
I can't seem to get a iso file with the correct md5sum for Ubuntu server 10.04 lts.  I am having freezing issues while in command prompt, probably 12 times in a row and I gaveup.  Trying to reinstall with correct MD5sum iso CD, however, can't find a good version of it.  Where should I download it from?

I'm using winmd5sum to check it.

---

### Post by Frogs Hair on 2012-02-21
You probably have the links already . The only thing I can suggest is burring the cd at at a slower speed if that is storage device you have chosen. 

If using a usb you will have to wait for some one with more experience with them.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Steelmesh on 2012-02-21
> **Frogs Hair said:**
> You probably have the links already . The only thing I can suggest is burring the cd at at a slower speed if that is storage device you have chosen. 

If using a usb you will have to wait for some one with more experience with them.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

What about the iso being wrong before burning? Am I supposed to check md5 on the CD after burning? I'm really new at this...

---

### Post by Steelmesh on 2012-02-21
> **Frogs Hair said:**
> You probably have the links already . The only thing I can suggest is burring the cd at at a slower speed if that is storage device you have chosen. 

If using a usb you will have to wait for some one with more experience with them.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Reading through that stuff again, I found this page [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) to download the torrent...we'll see.

---

### Post by raja.genupula on 2012-02-21
yes you should do Checksum to ISO  before going to Burn it . if you burn an ISO which have wrong Checksum , then installation will be failed or your system not going to work properly .

---

### Post by Frogs Hair on 2012-02-21
> **Steelmesh said:**
> What about the iso being wrong before burning? Am I supposed to check md5 on the CD after burning? I'm really new at this...

That is possible that the download is corrupt , but unlikely . Especially if ISO files were download on different days . Corruption is more likely occurs in coping process .

If you have access to another computer try creating the disk / usb from there . If it works then you will be closer to finding out what the problem is . [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ussndmac on 2012-02-21
You should check the md5sum on the iso after download.

You can check the md5sum on the CD or DVD, but simply running md5sum against the CD/DVD won't work.

See:

[http://unix.stackexchange.com/questions/3792/calculate-md5sum-of-a-cd-dvd](http://unix.stackexchange.com/questions/3792/calculate-md5sum-of-a-cd-dvd)

[http://twiki.org/cgi-bin/view/Wikilearn/CdromMd5sumsAfterBurning](http://twiki.org/cgi-bin/view/Wikilearn/CdromMd5sumsAfterBurning)

[http://www.brunolinux.com/01-First_Things_To_Know/Md5sum_of_Burned_CDs.html](http://www.brunolinux.com/01-First_Things_To_Know/Md5sum_of_Burned_CDs.html)

---

### Post by Steelmesh on 2012-02-22
What is with this MD5 stuff, I am downloading stuff onto my **other computer** and still keep getting ISO with non-matching MD5.  I initially downloaded desktop weeks ago and one of those files is right, I'm trying to load server so that one doesn't help.  Will Ubuntu support me, should I contact them?

---

### Post by Frogs Hair on 2012-02-22
I can't explain why you have so many failures . You can ask at the link. [http://askubuntu.com/questions/ask](http://askubuntu.com/questions/ask)

---

### Post by mastablasta on 2012-02-22
> **Steelmesh said:**
> What is with this MD5 stuff, I am downloading stuff onto my **other computer** and still keep getting ISO with non-matching MD5. I initially downloaded desktop weeks ago and one of those files is right, I'm trying to load server so that one doesn't help. Will Ubuntu support me, should I contact them?
 
 
you are losing packets in connection or oyu have some errors on your hard disk. md5sum check only tells you if the file you downloaded is exactly the same (bit by bit) as the one that is on Ubuntu server.

---

### Post by Steelmesh on 2012-02-22
> **Steelmesh said:**
> What is with this MD5 stuff, I am downloading stuff onto my **other computer** and still keep getting ISO with non-matching MD5.  I initially downloaded desktop weeks ago and one of those files is right, I'm trying to load server so that one doesn't help.  Will Ubuntu support me, should I contact them?

I also did a torrent download yesterday, was still bad.

---

