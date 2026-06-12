---
title: "Ubuntu speed from external ssd"
date: 2015-12-06
forum: New to Ubuntu
---

### Post by jamesmck on 2015-12-06
If I have a full install of 14.04.3 on an external SSD (USB 3.0) will it be _almost_ as fast as an install on the primary HDD?

---

### Post by RobGoss on 2015-12-06
Hello and welcome to the forum. I'm not expert but I've been using Ubuntu for sometime now and from my experience I believe you will only get the full potential of Ubuntu on a live machine and not a SSD. The SSD are not really made to be used as a full blown machine that will give you the fastest processors and everything you need to keep things running smoothly. 

I hope this will help you with your decision

---

### Post by Bucky Ball on 2015-12-06
Welcome.

@RobGoss: Apologies, but need to clarify and possibly correct. Perhaps my reading of 'SSD' is incorrect. ;)

@jamesmck: If you are talking about using a solid state drive (SSD) externally using USB3 then yes, quite capable of running an OS and that would run faster than a HDD in or out of your machine. Doubtful the experience would be discernible from running Ubuntu from an internal HDD or SSD. 

Take note that this would only apply to USB3 speeds (or eSATA) and an SSD. It is really more about the transfer rate of the drive and the connection type, but that is another story and you can work those details out with a bit of research if you're inclined. 

If you do some searching there is a LOT of information about SSD vs HDD and the various configurations, external/internal. Same for USB and SATA speeds. You should be able to find anything you want to know about them quickly.

(PS: When you say 'primary hard disk drive' you are meaning an internal HDD?)

---

### Post by jamesmck on 2015-12-06
> **Bucky Ball said:**
> Apologies, but need to clarify and possibly correct. If you are talking about using a solid state drive (SSD) then yes, they are more than capable of running an OS via USB 3 and that would run faster than a HDD in or out of your machine. Doubtful the experience would be discernible from running Ubuntu from an internal HDD or SSD. 
(PS: When you say 'primary hard disk drive' you are meaning an internal HDD?)

Thanks for the reply.  Yes, I meant the internal HDD.  I will do some searching for other threads.  The external SSD I have in mind is only 64GB, if this matters.  Any suggestions for partitioning?

---

### Post by Bucky Ball on 2015-12-06
Size is irrelevant. Same speeds apply.

As for partitioning, we have absolutely no detail of your intentions so hard to advise. Again, best to do a bit of research on that and get some ideas then post a new thread specifically about that, perhaps when you have the hardware and are ready to go (it is off-topic here). In the meantime, you are going to at least need these two partitions for an install of Ubuntu:

/ = your OS and personal data if you decide to store it there (not the greatest option)
/swap = like a pagefile in Windows. 2Gb or the size of your installed RAM for hibernation.

Some folk prefer to live without a /swap (caveat: you must have one to hibernate). They are exceptions and it is still rule of thumb to include one.

[This link]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") may be a place to start. :)

---

