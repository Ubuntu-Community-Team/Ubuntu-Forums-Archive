---
title: "Adding a new HDD"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by fletcham on 2008-10-14
Hello,

I have been using ubuntu for nearly a year now, and love it!! 

I mainly use my pc for media and the 500Gb HDD that I started with now only has 5Gb free. I am going to buy a 1Tb HDD this week but am unsure how to install it. My technical computer knowledge is VERY limited! 

Im sure I will be able to connect it with no problems but am unsure what I would need to do from there so that I am able to just boot up as usual and access all the info on either hard drive.

Any info or directions would relly be appreciated.

Thanks in advance

Fletch ::popcorn:

---

### Post by fletcham on 2008-10-14
Hello,

I have been using ubuntu for nearly a year now, and love it!! 

I mainly use my pc for media and the 500Gb HDD that I started with now only has 5Gb free. I am going to buy a 1Tb HDD this week but am unsure how to install it. My technical computer knowledge is VERY limited! 

Im sure I will be able to connect it with no problems but am unsure what I would need to do from there so that I am able to just boot up as usual and access all the info on either hard drive.

Any info or directions would relly be appreciated.

Thanks in advance

Fletch ::popcorn:

P.S. I was also thinking about dual booting with XP as I could do with it for a very small no. of things. This is not urgent but would it make sense to do it at the same time as adding the HDD. And if so, how?

Thanks Again :):):):)

---

### Post by bumanie on 2008-10-14
You will have to format the drive and add a filesystem - ext3 is a native linux filesystem and then add it to /etc/fstab for it to automount etc.

---

### Post by overdrank on 2008-10-14
Threads merged :)

---

### Post by Dr Small on 2008-10-14
It depends on what type of hard drive you get and what type of connections you have on your motherboard. If the new hard drive is SATA, and your motherboard supports SATA, then all you need to do is plug in the SATA cable from Hard drive to Motherboard, plugin the SATA power (from the Power Supply) and then mount it to the case.

If the new drive is SATA and your motherboard only accepts PATA (Parallel ATA), then you would need to buy an adapter. Before you buy anything, see what your motherboard accepts. PATA connections are a long row of 2 wide pins. SATA is a small corner looking connection. And the motherboard should have some labels of some sort beside the connection.

Edit: Thanks Overdrank :)

Edit2: For further reference:

SATA:
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

PATA:
[http://en.wikipedia.org/wiki/AT_Attachment](http://en.wikipedia.org/wiki/AT_Attachment)

---

### Post by fletcham on 2008-10-14
Thanks for the advice, great stuff.

Dr Small - my current hard drive is sata and my motherboard does accept it. So if i just connect it all up it should work fine yeah? 

Would it be like have a memory of 1500Gb (1Tb HDD + 500Gb HDD) or would they be totally separate so I would have to save some media to one and some to another, if you see what I meean. As in, Could I access all of the media through one folder on my desktop.

Sorry if Im asking daft questions but just want to be sure before I buy it as Im weighing up just getting an external hard drive,

Thanks again for you advice :popcorn::):popcorn:

---

### Post by fletcham on 2008-10-14
bump

---

### Post by handydan918 on 2008-10-14
> **fletcham said:**
> Thanks for the advice, great stuff.

Dr Small - my current hard drive is sata and my motherboard does accept it. So if i just connect it all up it should work fine yeah? 
Yeah, as far as the physical connections go. It will require some formatting.
> 

Would it be like have a memory of 1500Gb (1Tb HDD + 500Gb HDD) or would they be totally separate so I would have to save some media to one and some to another, if you see what I mean. As in, Could I access all of the media through one folder on my desktop.
You could do this either way, actually. If you wanted to have the whole 1.5TB size available, you could, say, symlink to it. There are really a lot of options here.
> 


Sorry if Im asking daft questions but just want to be sure before I buy it as Im weighing up just getting an external hard drive,Personally, I would prefer an internal,  unless you specifically need portability, or something. Externals seem to be a wee bit problematic, as well as being more expensive, generally.
> 


Thanks again for you advice :popcorn::):popcorn:

---

