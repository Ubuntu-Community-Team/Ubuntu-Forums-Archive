---
title: "Can I upgrade to 64-Bit from 32-Bit"
date: 2011-05-21
forum: Recurring Discussions
---

### Post by fritz269 on 2011-05-21
Can I upgrade 11.04 to 64 bit or do I have to do a fresh install?

---

### Post by wildmanne39 on 2011-05-21
> **fritz269 said:**
> Can I upgrade 11.04 to 64 bit or do I have to do a fresh install?

Hi, installing natty it is better to do a clean install., as for from 32 bit 2 64 not sure, I have ran 64 for a long time and can not remember but again I just installed natty a few weeks ago and it just failed as an upgrade.):P

---

### Post by Frogs Hair on 2011-05-21
You will need to do a clean installation because that is not an upgrade to new release as far as I know. Even with an upgrade to a new release you will be offered  a 32 bit version if that is what you are running.

---

### Post by tgm4883 on 2011-05-21
You cannot change from 32-bit to 64-bit (or vice versa) without a reinstall

---

### Post by TAspr on 2011-05-21
How much memory do you have?

---

### Post by tgm4883 on 2011-05-22
> **TAspr said:**
> How much memory do you have?

No amount of memory will allow him to move from a 32-bit to 64-bit OS without reinstallation. If he has a 64-bit capable CPU he should use it.

---

### Post by TAspr on 2011-05-22
Well, I guess my point is, is that if you have less than 4GB, there would be no benefit of going 64 bit, but if he has more than that, the go for it.

---

### Post by Paqman on 2011-05-22
> **TAspr said:**
> my point is, is that if you have less than 4GB, there would be no benefit of going 64 bit

Common misconception.

32-bit Ubuntu these days can address more than 4GB of RAM (albeit not as efficiently as 64-bit), so memory size is a non-issue. The real reason to use 64-bit is that it makes your processor faster. For some types of job it's a very significant speed boost.

---

### Post by Swagman on 2011-05-22
> **Paqman said:**
> Common misconception.

32-bit Ubuntu these days can address more than 4GB of RAM (albeit not as efficiently as 64-bit), so memory size is a non-issue. The real reason to use 64-bit is that it makes your processor faster. For some types of job it's a very significant speed boost.

I'm running a Phenom II x4 965 with 4gb ram on 32 bit.

PAE kernel does weird things to my system.

---

### Post by tgm4883 on 2011-05-22
> **TAspr said:**
> Well, I guess my point is, is that if you have less than 4GB, there would be no benefit of going 64 bit, but if he has more than that, the go for it.

Right, no benefit. Except better number crunching and such. I guess since PAE is around everyone can stop making 64-bit OS's.

---

### Post by fritz269 on 2011-05-22
Ok well, I have an Intel Celeron 900 that supports both 32 and 64 bit (had Win 7 Ultimate running 64 bit bual boot) with 4 gigs of ram, though the system only reads 3.8 and it should read at least 3.94 gigs. I am getting some screen flickers such as the screen resolution being smaller but after a few min it fixes itself or when I scroll across the icons on the bar to the right the decription stays up on the screen. Some booting problems every now and then where I have to hold the power down to shut off and wait about 10 seconds before I reboot and it works fine. I was hoping that the 64 bit would fix the issues. I did do an upgrade from 10.10 to 11.04 both 32 bit ( I have only a 10.10 install disk atm). In case you want the specs for my Laptop its a Toshiba Satellite C655-S5049. It came with 2 gigs of Ram but I maxed it at 4 gigs. What do you guys think. I have only been running it a couple of weeks and have all my important stuff backed up so I can do a fresh install if I need to though I do not have internet at home and would have to download 11.04 64gig install disk at like starbucks or something.

---

### Post by TAspr on 2011-05-23
If all you do is want to upgrade, I would stick to 32bit, but if you feel the need to go 64, then all the power to you, but I do not think on a system with those specs that you would see a noticible  difference.

---

### Post by philinux on 2011-05-23
Bit old but still valid as an indication.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by fritz269 on 2011-05-23
> **philinux said:**
> Bit old but still valid as an indication.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)


Thanks for the link, though I did not see it until after I decided to change to 64-bit. Installed last night and so far(only 3 boots so far) the issues I had seem to have disappeared. I did have  one boot just boot into the desktop with only the background and had to restart. I was not really going for performance boost, I was more going for reliability. I guess I will use it on and off today and see how it goes but so far it seems to be pretty stable. 

Note: RAM went from 3.8 to 3.7, im sure not a big difference but I found it strange. Also, during installation, I chose to do manual install and selected 10 gig swap file and it seemed to have the same issues as before. The 32-bit system had 9.5 gig swap file so I just copied the same as  before. 
 However, on the 64-bit installation, I let the system choose the swap file and it chose 3.9 gigs. Now I am wondering if the swap file had something to do with the performance issues I was having? Usually, more is better, right?

---

### Post by PhilGil on 2011-05-23
> **fritz269 said:**
> However, on the 64-bit installation, I let the system choose the swap file and it chose 3.9 gigs. Now I am wondering if the swap file had something to do with the performance issues I was having? Usually, more is better, right?
The traditional rule-of-thumb is to have the same amount of swap as RAM, and that is what the installer chose. However, even that is way more swap space than is typically necessary on a modern computer with 2+ GB of RAM. Making the swap partition larger than 4GB is a waste of disk space and won't do anything to improve performance.

---

### Post by eltonw on 2011-05-23
> **fritz269 said:**
> Can I upgrade 11.04 to 64 bit or do I have to do a fresh install?
Does your machine have an AMD processor? The 64-bit is for machines that have an AMD CPU. If it yours is an Intel, you will not get any benefit by installing the 64-bit version.

---

### Post by u.rusty on 2011-05-23
> **Paqman said:**
> [...] The real reason to use 64-bit is that it makes your processor faster. [...]

I can't understand how it could make the processor faster. I can see how using a 64bit as opposed to a 32 bit operating system might make the processor work more efficiently and getting more work done in a given amount of time, but not speeding it up. Switching from 32bit to 64bit OS won't increase the clock speed.

---

### Post by u.rusty on 2011-05-23
> **eltonw said:**
> Does your machine have an AMD processor? The 64-bit is for machines that have an AMD CPU. If it yours is an Intel, you will not get any benefit by installing the 64-bit version.

Is that to say that I get no benefit from running Ubuntu 64 bit, rather than 32 bit, on my Intel 64 bit quad core processor?

---

### Post by Megaptera on 2011-05-23
> **eltonw said:**
> Does your machine have an AMD processor? The 64-bit is for machines that have an AMD CPU. If it yours is an Intel, you will not get any benefit by installing the 64-bit version.

From answer #2 here [http://ubuntuforums.org/showthread.php?t=1763487](http://ubuntuforums.org/showthread.php?t=1763487)
"You should use the amd64 version. The name "amd64" is just a "historical artifact" but works fine on Intel chips too."

So which answer is correct please?
Thanks.

---

### Post by fritz269 on 2011-05-23
Yes I have an intel Celeron 900 64 bit. 
The way to think of a CPU is 32 and 64 bit is this( I think), the cpu can handle processing 64 bits of information at the same time it would take a 32 bit processor 64 bits. In other words, more information should be process thus improving the performance.

And no, it will not improve clock speed, which is not what I was looking for. I was looking for efficiency and stabilty  which seems to have been achieved. 

Can someone explain to me the swap file? What exactly does it accomplish?

Edit: Ok, based on what I read, this might have been the reason why I was having performance issues. I read that using a large swap file slows down your system. Is this correct?

---

### Post by PhilGil on 2011-05-23
Swap functions as temporary system memory when you run low on RAM. It also stores your system state when you hibernate your machine.

You can view the amount of data stored in swap using the Gnome System Monitor. On my system with 2 GB of RAM I rarely see more than 15-20mb of swap space used, even if my machine has been running for days.

---

### Post by philinux on 2011-05-23
> **eltonw said:**
> Does your machine have an AMD processor? The 64-bit is for machines that have an AMD CPU. If it yours is an Intel, you will not get any benefit by installing the 64-bit version.

This is not true at all. It's just a historical nomenclature.

---

### Post by AgentZ86 on 2011-05-23
> **fritz269 said:**
> Can I upgrade 11.04 to 64 bit or do I have to do a fresh install?

I would say no, but not 100% sure

However, if you have a 32bit machine this is a definite no.

---

### Post by PhilGil on 2011-05-23
> **fritz269 said:**
> Ok, based on what I read, this might have been the reason why I was having performance issues. I read that using a large swap file slows down your system. Is this correct?
I'm not sure about that. I think the size of your swap area is more of an issue in Windows, which by default uses a swap file rather than a swap partition. It makes sense that it would take longer to read and write to a large file vs a small file.

It certainly is possible to fine tune your Linux swap. Size, location of  the partition on disk, how "swappy" you want your system to be can all be adjusted. Someone with more experience than I will need to chime on on whether it's really worth your time. I've never noticed a problem following the swap partition size = system RAM rule.

---

### Post by tgm4883 on 2011-05-23
> **eltonw said:**
> Does your machine have an AMD processor? The 64-bit is for machines that have an AMD CPU. If it yours is an Intel, you will not get any benefit by installing the 64-bit version.

You are 100% completely incorrect. Please do not spread bad information.

---

### Post by Paqman on 2011-05-23
> **u.rusty said:**
> I can't understand how it could make the processor faster. I can see how using a 64bit as opposed to a 32 bit operating system might make the processor work more efficiently and **getting more work done in a given amount of time**, but not speeding it up. Switching from 32bit to 64bit OS won't increase the clock speed.

Which, subjectively at least, is faster. A lot of things determine the overall speed of your processor, of which frequency is just one.

---

### Post by oregonbob on 2011-05-23
If you are running less than 4GB just stay with 32bit. One thing not pointed out yet is that most programs run more stable/better in 32bit. 64bit has many bugs and glitches. Just try out flash 64bit and you'll learn :)  

In addition some applications still don't offer 64bit versions.

---

### Post by Paqman on 2011-05-23
> **oregonbob said:**
> If you are running less than 4GB just stay with 32bit. One thing not pointed out yet is that most programs run more stable/better in 32bit. 64bit has many bugs and glitches. Just try out flash 64bit and you'll learn :)

I've been running 64-bit for years, and that's not been my experience at all.

> 
In addition some applications still don't offer 64bit versions.

Nor this, either. I think I found one program once that didn't offer a 64-bit version. That's it. Everything else is available.

---

### Post by Lateralis on 2011-05-23
> **oregonbob said:**
> If you are running less than 4GB just stay with 32bit. One thing not pointed out yet is that most programs run more stable/better in 32bit. 64bit has many bugs and glitches. Just try out flash 64bit and you'll learn :)  

In addition some applications still don't offer 64bit versions.

Its not been pointed out yet because it is simply untrue.  I use 64-bit Ubuntu on my desktop at home, have done for several years, and everything works fine, including Flash.  I also have not come across a program in recent history that does not have a 64-bit version, although there was one program a few years ago that I wanted but was only 32-bit.  Fortunately, there are often ways around such things...  

So, unfortunately, I couldn't disagree more with you.

---

### Post by fritz269 on 2011-05-23
Yes, I am familiar with the 64-bit architecture. I had been running Win 7 64 bit for a while and I now that alot of programs are supporting 64 bit as this is the direction that we are heading as programs get bigger and require faster processing. 

I have been running the 64 bit version of 11.04 all day and I have notices a significant improvement in the stabilty and processing. Thanks everyone for the input. I think I am marking this solved.

---

### Post by tgm4883 on 2011-05-23
> **oregonbob said:**
> If you are running less than 4GB just stay with 32bit. One thing not pointed out yet is that most programs run more stable/better in 32bit. 64bit has many bugs and glitches. Just try out flash 64bit and you'll learn :)  

In addition some applications still don't offer 64bit versions.

I'll just agree with everyone else here that your statement is false. Flash works fine on my 64-bit system.

---

### Post by u.rusty on 2011-05-24
> **Paqman said:**
> Which, subjectively at least, is faster. A lot of things determine the overall speed of your processor, of which frequency is just one.

Granted, I would say that, subjectively, running a 64 bit processor with a 64 bit OS rather than a 32 bit OS is faster. But, the actual speed of the processor is determined by the frequency. That doesn't mean that it can't operate more, or less efficiently. It just means that the actual speed that it operates is determined by the frequency. Of course, the frequency can be changed, but that doesn't happen by switching from a 32 bit OS to a 64 bit OS.

Anyway, I concede that your main point is correct. I'm really splitting hairs.

> **tgm4883 said:**
> I'll just agree with everyone else here that  your statement is false. Flash works fine on my 64-bit system.

I have to agree with tgm4883, flash works fine on my 64 bit version of Ubuntu also.

---

### Post by philinux on 2011-05-24
Moved to recurring.

---

### Post by oregonbob on 2011-05-26
All these testimonials "I have been running 64 bit for years...blah".

Well I've been running Ubuntu 64 bit for years too. I had plenty of issues. In fact I had an issue today. I wanted to [lightscribe]("http://www.lightscribe.com/support/kb_searchResults.aspx?question=deb+64+bit&imageField.x=22&imageField.y=14&topicid=") some CD's and HP only has Linux software for 32 bit. I've seen this on about all major dists of software, Chrome, flash, and others I've forgotten. Here is quote so typical that I've seen over the "years" I've been running it:

> ANSWER:
At this point, the LightScribe System Software is only available for 32 bit systems. We have not been able to test the 64-bit option so we cannot officially provide support for it but you may be able to research it further.


You must not do as much with your 64 bit as I do with mine that "I have been running for many decades". Ubuntu must agree with me since they recommended staying on 32 bit unless you had a specific reason to change. You must not have followed them either. With Natty they started recommending 64 bit.

---

### Post by tgm4883 on 2011-05-26
> **oregonbob said:**
> All these testimonials "I have been running 64 bit for years...blah".

Well I've been running Ubuntu 64 bit for years too. I had plenty of issues. In fact I had an issue today. I wanted to [lightscribe]("http://www.lightscribe.com/support/kb_searchResults.aspx?question=deb+64+bit&imageField.x=22&imageField.y=14&topicid=") some CD's and HP only has Linux software for 32 bit. I've seen this on about all major dists of software, Chrome, flash, and others I've forgotten. Here is quote so typical that I've seen over the "years" I've been running it:



You must not do as much with your 64 bit as I do with mine that "I have been running for many decades". Ubuntu must agree with me since they recommended staying on 32 bit unless you had a specific reason to change. You must not have followed them either. With Natty they started recommending 64 bit.

Or maybe it's just the user? I mean, I have no issue with flash on my system. Now I don't write lightscribe disks, so I don't have that to check, but I have no issue running flash, chrome, or any other software. You not being able to run the lightscribe software isn't an issue with 64-bit Ubuntu, it's an HP issue.

As for the other issues you have, maybe you just don't know what you are doing? That's fine not everyone is a power user, but don't blame the OS for all of your issues.

---

### Post by oregonbob on 2011-05-26
> **tgm4883 said:**
> Or maybe it's just the user? I mean, I have no issue with flash on my system. Now I don't write lightscribe disks, so I don't have that to check, but I have no issue running flash, chrome, or any other software. You not being able to run the lightscribe software isn't an issue with 64-bit Ubuntu, it's an HP issue.

As for the other issues you have, maybe you just don't know what you are doing? That's fine not everyone is a power user, but don't blame the OS for all of your issues.

Holy cow, I must have jumped into the kiddie corner section of this forum. My bad, thought I was in a tech area.I always forget the social groups chit chat, raw raw hooray Ubuntu!

---

### Post by tgm4883 on 2011-05-26
> **oregonbob said:**
> Holy cow, I must have jumped into the kiddie corner section of this forum. My bad, thought I was in a tech area.I always forget the social groups chit chat, raw raw hooray Ubuntu!

Your lack of an actual response if very reassuring.

---

### Post by wolfen69 on 2011-05-27
> **tgm4883 said:**
> I'll just agree with everyone else here that your statement is false. Flash works fine on my 64-bit system.

+1. 

64bit flash has been near perfect *for me* for the past 2 years. I would never go back to a 32bit OS.

---

### Post by wolfen69 on 2011-05-27
> **tgm4883 said:**
> Right, no benefit. Except better number crunching and such. I guess since PAE is around everyone can stop making 64-bit OS's.

Good one.

I have a (quad core) 64 bit cpu, nice video card, and sata 6 drives. The throughput I experience now is amazing. Every litlle bit helps. Sure, 64bit ubuntu might not matter to everyone, but to dismiss it is just wrong. It was one of the best things I've ever done. (switch to 64bit)

I don't have hard numbers, but it does "feel" faster. YMMV. I think between sata 6 and 64bit, it makes a bit of a difference. But if you only do emails and surfing, then there will probably be no benefit.

---

