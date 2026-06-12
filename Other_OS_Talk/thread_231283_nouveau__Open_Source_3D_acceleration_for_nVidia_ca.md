---
title: "nouveau : Open Source 3D acceleration for nVidia cards"
date: 2006-08-07
forum: Other OS Talk
---

### Post by Luk8 on 2006-08-07
[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

Does anyone here know about this project and can comment on it ? What are the chances we will have an open source 3d accelerated driver for nvidia ?

---

### Post by pay on 2007-02-17
Ubuntu is supporting the project > *"We will actively support Nouveau and other efforts to develop free software drivers that enable the requisite functionality. I am happy for folks working on these efforts to contact me directly or to follow the community channels in Ubuntu. Either way, we will provide financial and development support for those groups and will integrate their work as soon as it does the necessary hardware magic. Proprietary drivers are not the preferred solution and will be eliminated once the community delivers a free alternative."*

---

### Post by tommcd on 2007-02-18
Here are some preliminary tests of the nouveau driver:
[http://www.phoronix.com/scan.php?page=article&item=614&num=1](http://www.phoronix.com/scan.php?page=article&item=614&num=1)
[http://www.phoronix.com/scan.php?page=article&item=634&num=1](http://www.phoronix.com/scan.php?page=article&item=634&num=1)

---

### Post by rai4shu2 on 2007-02-18
If it properly supports the thermal monitor in my 7600GT then I'll use it now. I don't really give a damn about 3D.

---

### Post by manmower on 2007-02-18
I think success is quite probable for this project as it seems very well organized, and has already generated enough publicity to attract the attention of testers and developers alike. By the way, anyone with nVidia graphics cards (using the proprietary driver) can help them out by running the reverse engineering tool REnouveau and mailing them the log it generates. Details are [here](http://ubuntuforums.org/showthread.php?t=357369).

---

### Post by neighborlee on 2007-06-14
> **manmower said:**
> I think success is quite probable for this project as it seems very well organized, and has already generated enough publicity to attract the attention of testers and developers alike. By the way, anyone with nVidia graphics cards (using the proprietary driver) can help them out by running the reverse engineering tool REnouveau and mailing them the log it generates. Details are [here](http://ubuntuforums.org/showthread.php?t=357369).

Nvidia wont directly suppport the project nor stop it , which says to me there are legal ramifications making that impossible for them to do so ; plus I also suggest that users who really want OSS 3d drivers to consider intel.  Intel chips atm may not power some high end games but I suspect intel will likely start producing said cards soon to bolster their sales a bit ;)

I dont want to sound negative but I tend to think that my decisions to use a driver wont be just because it is 'OSS', but more likely be cause its produced by people who KNOW the hardware best and have been producing drivers for it for a very longtime now.  I think free software ( someday even hardware , but not likely our lifetime ) IS a wonderful time as it evens the playing field for those less fortunate than others, but honestly I dont blame nvidia for trying to make a buck while staffing  itself with well paid and no doubt truly amazing coders to produce products that clearly do the job.  IF there are security related issues ( or any issues period) with the drivers and they are not being address and this can all be verified then yes that would be truly sad because linux deserves better, but atm I dont see anyone pushing that instead we see alot of FUD in the form 'it must be oss or bust' , mentality and Im just not about that , though in general terms I respect it . 

HOnestly I think too that until ubuntu came along with its enhancemnets that linux wasn't taken all that seroiusly, but now with the crash handler and relatively easy to install out of box codecs its cert. better today..but I suspect pclos is   creeeping up fast because all a user has to do to have most of this work out of the box is install the livecd and your done...I know yes its all about patents , but tell that to windows users trying to convert to linux without the impending hastles it brings ;)..like it or 'not' at the end of the day either someone  finds linux too much hastle for various software or hardware reasons or  they have no such needs and find it a acceptable learning curve...make no mistake though, its no accident we dont have the amazing game and app support we could if the OS were as easily used as windows is,- though its clear ubuntu is making the best strides on that front, minus what I consider a mistake to actively support RE'ing. ( that is just me and apparantly nvidia isn't worried about it per se, as likely they know they produce the  best drivers , and I suspect that may be true for  quite sometime to come and well if yo hate non oSS so bad why not , - to coin a phrase from linus ; 'just use intel' )

cheers
nl

---

### Post by tommcd on 2007-06-15
> **rai4shu2 said:**
> If it properly supports the thermal monitor in my 7600GT then I'll use it now. I don't really give a damn about 3D.

Just out of curiosity, if you don't care about 3D, why are you running a high end card like the 7600GT? I do care about 3D, and I only have a nvidia 6200 in this box. It doesn't need a fan. Doom3, quake4, nexuiz, and sauerbraten run just fine. Yes, I run them at low resolutions and without AA and AF, but you really don't need a high powered card that runs near the boiling point  in linux.

---

