---
title: "Lubuntu won't start after boot"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by s1wood on 2013-01-20
My netbook closed down normally yesterday but today it boots as far as the lubuntu logo which then flashes and disappears leaving either a blank screen or a message about 'broken pipe'. No further flashing on the HDD light. I have tried several times.
I can boot Puppy from an SD card without a problem.

Not sure where to go from here, any suggestions?

Susan

---

### Post by sidzen on 2013-01-20
Greetings from 11 hours in the past.
Without hardware specs, it is hard for me to say anything but
try [*peppermint three*]("http://peppermintos.com") !

---

### Post by s1wood on 2013-01-20
I've downloaded Peppermint for fun anyway, but what I was after was a way of salvaging my Lubuntu, Hardware isn't an issue, I've had various forms of Ubuntu on this machine with no problems.

Susan

---

### Post by s1wood on 2013-01-20
Further information: the error message is 
could not write bytes: Broken pipe
This time it did a brief disk check before cutting out so there is life in there somewhere.

Susan

---

### Post by mysteriousdarren on 2013-01-22
did you try starting a different desktop environment?

---

### Post by audiomick on 2013-01-22
> **mysteriousdarren said:**
> did you try starting a different desktop environment?

I'm not sure that the machine is even getting to the login box.

@Susan: is it? Is the breakdown happening before or after the login?

Next thought: can you boot into an earlier kernel? Maybe an update killed it...

---

### Post by s1wood on 2013-01-22
This is now academic since I have lost patience and re-installed, but no, it never got to log-in, just the lubuntu with the dots under it. 

If anyone has an explanation I would like to know it, in case it happens again, but otherwise no need to pursue the matter.

Thanks anyway,

Susan

---

### Post by audiomick on 2013-01-22
> **s1wood said:**
> 
If anyone has an explanation I would like to know it,

The possibilities include

difficulty reading the drive: look for the hard drive utility, and look in there for the button for SMART values. Not sure where that is on Lubuntu. The SMART values are data about the drive that the drive saves about itself. If it is starting to have problems, it might show up there.

Also, if you start to think you have a drive problem, make sure the drive is seated properly, all cables are plugged in right, maybe unplug and re-connect. A bad connection can cause intermittent problems.

Grub got messed up somehow: have a look at boot repair
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
in fact, have a look at that in any case. It is a good tool, and the boot info summary it offers contains lots of useful info about the state of your machine. 

Your file system was somehow corrupted, so that the machine was having trouble reading it. Not sure what to do about that, as I haven't had that sort of trouble, so I wont suggest anything in case I get it wrong.

---

