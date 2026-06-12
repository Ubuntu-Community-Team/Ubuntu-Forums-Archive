---
title: "RAID on Ubuntu"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by lile001 on 2011-10-13
I have had a complete failure in getting a RAID drive to work under Ubuntu, and finally gave up as you can see [here]("http://ubuntuforums.org/showthread.php?t=1164640")

Well, fast forward a couple years.  My Ubuntu computer is 2 years old, and working fine.  I will probably buy a new computer this year.  

Almost every computer that I have owned has died because of hard drive failure, which is why I insist on RAID. My oldest computer (6 years) is starting to fail, one of the RAID drives has bit the dust, but no big deal!  It is a RAID array, redundant!  I have plenty of time to get the last few files off of the old dog before it finally bites the dust.  It is my last Windows computer, which is the only reason I keep it around. OH that I would have the luxury under Ubuntu, next time around!  I never want to have another computer without RAID. 

In the previous attempt, some folks said "RAID is no big deal! Easy!"  I could never get it to work.  In some cases, people said that there was certain hardware that was easier to install, or was installed at the Bios level and invisible to the operating system (I suppose).  No specifics were given though. 

I would like to build a new machine with a RAID drive, and dual windows/Linux boot.  I am not an expert at Ubuntu, in fact I am pretty lame. I can usually get through these installation issues, with a lot of help,  if they are not too damn complex.   But I make a living with my computer, and I need it to be rock solid reliable, and occasionally have to run Windows software (as little as possible) that won't work under WINE.  

How would you proceed?  Usually I just buy a Dell.  What specific hardware would you use?  Can you recommend specific hardware that has been successful on RAID? Which brand and model of drive would work with RAID?  Which brand and model of computer might work best for RAID?  How can I make this process as painless as possible, given my lack of expertise?

---

### Post by moldaviax on 2011-10-13
Hi

I would recommend reading the following link if you haven't already. 

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

The last ubuntu machine I had to setup we used a software raid. There are discussions of the pros and cons around the web.

regards

M.

---

### Post by lile001 on 2011-11-01
> **moldaviax said:**
> Hi

I would recommend reading the following link if you haven't already. 

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)


M.
The article says:
There are three ways to create RAID: 

[LIST=1]
[*]Software-RAID: Where the RAID is created by software. 
[*]Hardware-RAID:  A special controller used to build RAID. Hardware RAID is generally  faster, and does not place load on the CPU, and hardware RAID can be  used with any OS 
[*]FakeRAID:  Since RAID hardware is very expensive, many motherboard manufacturers  use multi-channel controllers with special BIOS features to perform  RAID. This is a form of software RAID using special drivers, and it is  not necessarily faster than true software RAID. Read [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") for details. 
[/LIST]
I want hardware raid, so I can turn it on and it just works.  Last time through, nobody bothered to tell me there was a software RAID, as is typical with these forums often N00Bs are directed to the most difficult and geeky solution first.   Fakeraid was a complete failure, the instructions quickly lapsing into complete gibberish after the fourth line.   As soon as something goes wrong with that gibberish gobbeldygook that Ubuntu geeks seem to think is so damn simple, I'm on my own with no help and no idea what to do next.  Typically the instructions say "Easy! Just type in FOO XyCBfh5856&&^&^ Fix_Hard_Drive 7454jhasdksdfh"  and when I do that I get "Error:  You have just launched a nuclear missile at Moscow.  Abort/Retry/Continue?"  Sorry about the rant, these forums are often not too beginner-friendly.  


Where to start?  What hardware RAID controllers have  been shown to work with Ubuntu?  I don't want another situation like last time where I pay for RAID and it fails to work on UBUNTU.  I would like to pay for it and have it actually work.  Any experience out there?

---

### Post by lile001 on 2011-11-02
Well, it seems there is no help for the beginner here.  I have found one hardware RAID controller, and a review comment by some guy who said it worked on Ubuntu, however reading between the lines that guy looks like quite a wizard.  
**[SIZE=2][B]3Ware 9650SE-2LP-SGL, Half-Length, Low Profile, Internal SATA II  Hardware RAID Controller Cardm, PCI Express x1, 2 port w/ 3Gb/sec, RAID  0, 1, JBOD and Single Disk- Single**[/SIZE][/B]

This hardware controller sells for $170.  You can find them from $39 to $2000.  I don't really have any way to know if the $39 one is useless or a good deal, nor why someone pays $2000 for one.  Perhaps it is really robust?  For server farms?  

I'd sure like to hear from anyone with experience with a hardware RAID controller, so I can know that I have half a chance.

---

### Post by lile001 on 2011-11-02
Seeing only one response (thanks!) on the beginner thread, and then having a long conversation with myself,  I am going to close this thread and open a new one on the hardware forum.

---

