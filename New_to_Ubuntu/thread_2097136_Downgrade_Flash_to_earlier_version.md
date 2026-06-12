---
title: "Downgrade Flash to earlier version?"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Swerve1000 on 2012-12-22
Hi,

I have tried to install the latest version of Ubuntu 32bit on my friend's old PC, but due to it's age, the newest version of Flash doesn't work.


How can I downgrade the version to the one which does work? I would like to avoid doing a full reformat if I can.

Many thanks :)

---

### Post by Pjotr123 on 2012-12-22
Don't do that. Adobe Flash Player is one of the most attacked pieces of software on this planet. You do not want to use an insecure version of Flash.

---

### Post by Swerve1000 on 2012-12-22
> **Pjotr123 said:**
> Don't do that. Adobe Flash Player is one of the most attacked pieces of software on this planet. You do not want to use an insecure version of Flash.


Thanks for saying :) I agree, but it's either that, or buy a new PC, which he can't afford.

---

### Post by Pjotr123 on 2012-12-22
There may be sensible alternatives. What are the specs of his computer? Can you supply a hardware list in this fashion:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

---

### Post by Temporarily on 2012-12-22
This problem is a known problem with old CPUs and newer flash player.. the solution is to downgrade the flash player.. but what [Pjotr123]("http://ubuntuforums.org/member.php?u=141824") said , is correct. 

I've keep the old version in my Ubuntu One account .. 11.1 (the newer version of flash is 11.2) for such cases.. 

The only thing you have to do is to copy the libflashplayer.so file to this path /usr/lib/mozilla/plugins/


Download the file from here  => [http://ubuntuone.com/0maDagKUuWihfc8A2ktnlp](http://ubuntuone.com/0maDagKUuWihfc8A2ktnlp)


and apply the commands below.. with order and one at time ( I assume you saved the file to Downloads folder)


```
cd Downloads 
tar xvzf flashplayer11_1r102_63_linux.i386.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```As you can understand this is for i386 (32bit) Operating System.. **If you have 64bit** .. let me know.. and [B]do not apply the commands above.
[/B]
Thank you

---

### Post by ajgreeny on 2012-12-22
See [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796") for details and a download of that version.

The problem seems to be associated with some versions of ATI graphic cards, particularly, in my case, the ATI 9200SE which uses the open source driver.

Make sure you use flashblock and/or noscript as well as this older flash version.

---

### Post by uschmuntu on 2012-12-27
the first response to every forum question is always "you don't want to do that!"

---

