---
title: "how much ram will 11.04 support?"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by pcrussell50 on 2011-09-22
i am thinking of building a new box that will not have any other OS'es on it besides ubuntu or xubuntu.  it will run the lastest version of ubuntu or xubuntu, each time the new release comes out.

in any event, might as well suit up with all the memory the OS can use, because this will be for my mother, (she uses only ubuntu or xubuntu in boxes i build for her), and she keeps them for a long time, because she does not do anything demanding.  but a reasonably fast processor and good amount of ram, will keep successive ubuntu releases happy for as many years as possible.  i just don't want to get a bunch of memory that ubuntu won't see.

i'm not averse to going with 64 bit, either.

thanks.

-peter

---

### Post by papibe on 2011-09-22
If you do the installation with a wired connection to the Internet, and you have more than 3Gb of RAM installed, your kernel will be upgrade to a special one called [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension").

Physical Address Extension (PAE) is a hardware extension provided by the x86 processors to access more than 4Gb of RAM. 

The 32bit version of Ubuntu, as most modern Linux distribution, takes full advantage of this feature allowing the OS to access of up to 64 GB of RAM.

I hope this answer some of your concerns,
Regards.

---

### Post by mutley89 on 2011-09-22
Assuming a 64 bit processor, the practical limit is either the motherboard or your wallet.  This page suggests a 1TB limit:
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by seawolf167 on 2011-09-22
If you have a 64bit capable machine, take advantage of it and install the 64bit (x86_64) version of Ubuntu. It will support more RAM than you could ever afford to put in your computer :P I highly suggest not using PAE and using the "real" 64bit addressing unless you have an existing 32bit install on a 64bit capable machine that you cannot upgrade for some reason.

---

### Post by jerome1232 on 2011-09-22
I can't agree more with "go 64-bit"

The advantageous just outweigh the quickly drying up disadvantageous. That being said, unless your mother is into transcoding hd video or something, she'll probably never feel a difference between 32 and 64 bit.

---

### Post by Immolatus on 2011-09-22
32 bit kernel --> 6gigs.
64 bit kernel --> 12 I think.

---

### Post by seawolf167 on 2011-09-22
> **Immolatus said:**
> 32 bit kernel --> 6gigs.
64 bit kernel --> 12 I think.

Ummm, try again...

32bit addressing has a total of 2^32=4,294,967,295 addresses, which is essentially 4GB, though you will "lose" some to the system addressing, making useable limit usually around 3.5GB or so (very roughly)

64bit addressing has a total of 2^64=18,446,744,073,709,551,616 addresses, which makes the usable limit roughly 18 exabytes*.

*However, AMD64 architecture actually uses 52bits only (lol) for addressing, making the useable limit a "mere" 4,000 TB - something I'm ***100% ****sure ***I'll never see (personally) in my lifetime!

---

### Post by philinux on 2011-09-22
The only time I've seen more the 1 gig used on my box is when I'm using virtualbox. My rig has 2gig mem and I've been using the 64 bit version for years.

---

### Post by LowSky on 2011-09-22
> **seawolf167 said:**
> 
*However, AMD64 architecture actually uses 52bits only (lol) for addressing, making the useable limit a "mere" 4,000 TB - something I'm ***100% ****sure ***I'll never see (personally) in my lifetime!

 '640K of memory should be enough for anybody.' -- supposedly spoken by Mr. Bill Gates in 1981 (he has denied it but the quote is very popular). Right now 4GB is common place on low end machines.

My first PC back in 1994 had 4MB of RAM not even 20 years later I have 12_GB_ in my desktop machine. Math says in 20 years I'll have Terabytes of RAM.

---

### Post by necromonger on 2011-09-22
I run 12 gig's on 64 bit with no problem.

---

### Post by seawolf167 on 2011-09-22
> **LowSky said:**
> '640K of memory should be enough for anybody.' -- supposedly spoken by Mr. Bill Gates in 1981 (he has denied it but the quote is very popular). Right now 4GB is common place on low end machines.

My first PC back in 1994 had 4MB of RAM not even 20 years later I have 12_GB_ in my desktop machine. Math says in 20 years I'll have Terabytes of RAM.

Terabytes I can see, but 4 Petabytes? IMHO not for anything but a supercomputer setup 60 years down the road. Though yes I agree that given enough time everything can be proven wrong - now lets just wait for the invention of an oracle machine to solve those pesky NP-Hard and NP-Complete problems :P

---

