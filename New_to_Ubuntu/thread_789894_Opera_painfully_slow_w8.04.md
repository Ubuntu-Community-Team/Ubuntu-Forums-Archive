---
title: "Opera painfully slow w/8.04?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by rivercitybuntu on 2008-05-10
I'm an almost n00b -- on my second Ubuntu install, ever.

I wanted to use Opera instead of Firefox, but it's running very, very slow. I tried Opera 9.27 and 9.50b2, but they both take so long to load pages that it's not worth it.

I looked around here and the Opera forums and tried everything suggested.

Is it just me, or is there a conflict between Hardy and Opera?

---

### Post by tjwoosta on 2008-05-10
i am using opera 9.50 beta2 right now, and it works great

its definatly the fastest browser ive found for ubuntu, way faster then firefox 3 beta 5


with firefox 3 i took the acid 3 test and scored a 75 and none of the bars were color, but with opera i took the test and got 82 with all but two bars in color

---

### Post by Go_Bucks on 2008-05-10
I have it installed as a backup in case something on a page doesn't work right in Firefox (of course, it usually won't work right in Opera either). Anyway, this is the first I have looked at it since I upgraded and I must say that it is so slow as to be unusable.

---

### Post by tjwoosta on 2008-05-11
really?  

what are you guys scoring for the acid 3 test with each?

[http://acid3.acidtests.org/]("http://acid3.acidtests.org/")

---

### Post by nynoah on 2008-05-11
speaking of opera...where do I get the 64 bit version of 9.50b2  I had the beta one in 64bit but can not find the beta 2 to use that.  This was back in October for the beta 1.

---

### Post by Go_Bucks on 2008-05-11
> **tjwoosta said:**
> really?  

what are you guys scoring for the acid 3 test with each?

[http://acid3.acidtests.org/]("http://acid3.acidtests.org/")

I just scored a 46 with Opera. Not a big deal as I never use it.

The image also looked nothing like the reference image (no colored boxes).

EDIT: Got a 71 with Firefox 3.

---

### Post by tjwoosta on 2008-05-11
> speaking of opera...where do I get the 64 bit version of 9.50b2 I had the beta one in 64bit but can not find the beta 2 to use that. This was back in October for the beta 1.

here is where i got mine
[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/]("ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/")

the .deb is the one you want

> I just scored a 46 with Opera. Not a big deal as I never use it.

The image also looked nothing like the reference image (no colored boxes).

EDIT: Got a 71 with Firefox 3.

hmm...

---

### Post by nynoah on 2008-05-11
NICE.....thanks.  They seem to hide the 64 bit version.  I had the older version that I got from this link.  

[ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)

I will try yours.  I hate to put the 32 bit version on my computer when I know there is a 64 bit version out there.

---

### Post by nynoah on 2008-05-11
Got it up and running on the Beta2.  Seems to fly real fast for me.  I will try that test.......

71/100 firefox 3
78/100 opera 64bit beta2
71/100 firefox 2
71/100 swift fox 64bit
71/100 Epiphnany

---

### Post by tjwoosta on 2008-05-11
well ive just researched the forums a bit and it seems that alot of people have been having problems with opera 32bit, but so far everyone that posts about 64bit opera seems to love it

so im guessing that the problem is only with the 32bit version for some reason

---

### Post by tjwoosta on 2008-05-11
> 
Got it up and running on the Beta2. Seems to fly real fast for me. I will try that test.......

71/100 firefox 3
78/100 opera 64bit beta2
71/100 firefox 3
71/100 swift fox 64bit
71/100 Epiphnany

awesome!

glad to help

---

### Post by nynoah on 2008-05-11
I would just like to say that there is a HUGE noticeable difference in the speed of the 64bit opera.  This thing runs fast

---

### Post by rivercitybuntu on 2008-05-12
so, to recap:
It sounds like at least some people who have tried 32-bit Opera with 8.04 Hardy are having performance issues...but not 64-bit?

I'm not in a position to invest in a new machine just now, but I do like the features in Opera. Any tips on fixes/workarounds?

---

### Post by zvacet on 2008-05-13
[Here]("http://operawiki.info/Opera")

---

### Post by conorsulli on 2008-06-29
I have the same problem and the release version of ffox crashes the whole time. I'm really starting to find ubuntu 8.04 unusable..... shocking actually considering the basic apps i use on it.

---

### Post by rburkartjo on 2008-06-29
yes i also have the 9.50 version of opera on ubuntu 8.04 (not the beta) and it is not slow/cheesemaker

---

### Post by rosswmcgee on 2008-06-29
Have the same problem, quit using it.

---

### Post by benign on 2008-07-03
I'm using 8.04 64bit with Opera 9.5 64bit, with a score of 83 on the Acid test. In Firefox 3, I got a 71.

I'm still having problems with the non-free flash plugin tho. It seems as if I close opera while a flash is playing, the system freezes up and uses 100% of one of the cores. Opera also tends to use almost 2x as much memory as firefox 3...

---

### Post by popeyeray on 2008-07-04
I have installed Opera Version 9.51 Build 2061 did uname -a found I had 64 bit and then downloaded from ftp site. I noticed I had to open terminal then do a sudo -s -H, chmod +x on the deb file, then finally a dpkg -i opera_9.51.2061.gcc4.qt3_amd64.deb. I always prefer to restart even though it may not be necessary and now I have a lightning fast browser, no problems whatsoever. It's all here if you need a guide.
[http://ubuntu-tutorials.com/2007/02/03/installing-opera-on-ubuntu/]("http://ubuntu-tutorials.com/2007/02/03/installing-opera-on-ubuntu/")
8-[

---

### Post by sports fan Matt on 2008-07-04
It does seem to lag by a few seconds in rendering this forum.

---

### Post by dizee on 2008-07-04
opera was slow for me and firefox wasn't because my dns settings were not configured correctly. check them in network manager (or you can look at the file /etc/resolv.conf) - if they say 192.168.1.254 that could be the problem.

for a test try using the opendns settings instead (use network manager to add these):
208.67.222.222
208.67.220.220

---

