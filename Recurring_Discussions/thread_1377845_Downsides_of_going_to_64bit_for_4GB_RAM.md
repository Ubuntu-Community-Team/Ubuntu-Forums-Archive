---
title: "Downsides of going to 64bit for 4GB RAM?"
date: 2010-01-10
forum: Recurring Discussions
---

### Post by usererror on 2010-01-10
I now have 4GB of RAM in my PC, up from 1.5GB.  If I want to utilize the full 4GB I understand that I have to install the 64bit Edition of Ubuntu.

What are the pitfalls of doing so?  Will all basic functions still work like flash player, java, firefox, etc?

In the past I have used Windows 64 bit editions and it was very frustrating to have seperate folders for 32bit vs 64bit applications.

The extra RAM would be helpful for running my virtualbox sessions.

Thanks for any input or advice into this area!

---

### Post by NoaHall on 2010-01-10
Everything will work fine. The flash player is better than the 32 bit version, but it's in a alpha(2) right now. Java is a bit hit and miss for me anyway.

---

### Post by Mike'sHardLinux on 2010-01-10
I honestly don't think there are any [serious] pitfalls of going 64bit any more. I use flash, java, adobe acrobat reader, etc..... They all work without any extra work. 

There are some software, that are not already available compiled for 64bit, such as ZSnes, and the Lightscribe software. Luckily, it is simple to use --force-architecture to install the 32bit .debs with dpkg. 

I also have been able to use all the software I have had installed with WINE since I was using 32bit Ubuntu. I didn't have to do anything to it when I made the switch. It just continues to work, only with the newer WINE. 

That's all I can think of at this time.

---

### Post by oldos2er on 2010-01-10
If you want 64-bit flash, you will need to install it manually as it is not in the repositories. See [http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html)

---

### Post by Manyette on 2010-01-10
However, if you load 32 bit version, you can have the hernel with the pae,
(physical address extension) which will allow access to most all of your 4 gigs, even in 32 bit mode, if you are worried about 64 bit.

---

### Post by NoaHall on 2010-01-10
> **Manyette said:**
> However, if you load 32 bit version, you can have the kernel with the pae,
(physical address extension) which will allow access to most all of your 4 gigs, even in 32 bit mode, if you are worried about 64 bit.

Using PAE isn't really a good idea. Slows things down a lot.

---

### Post by usererror on 2010-01-10
Thanks for the responses, Looks like I'll be putting on the 64bit version.

---

### Post by 73ckn797 on 2010-01-10
> **NoaHall said:**
> Using PAE isn't really a good idea. Slows things down a lot.


Sped thing up for me using PAE kernel.

---

### Post by Manyette on 2010-01-10
> Using PAE isn't really a good idea. Slows things down a lot. 

Works for me.  No slower than the normal 32 bit code.  I will probably go to 64 bit when Lyric becomes asvailable, because I suspect many of the current problems will be gone by then.

---

### Post by 73ckn797 on 2010-01-10
> **Manyette said:**
> ot. 

Works for me.  No slower than the normal 32 bit code.  I will probably go to 64 bit when Lyric becomes asvailable, because I suspect many of the current problems will be gone by then.


I was using 64bit on desktop but felt things were lagging a little. Went to 32bit with PAE kernel and system runs great. Sees all 6GiB of RAM.

I will likely go back to 64bit later.

---

### Post by happyhamster on 2010-01-10
Phoronix presented some 32bits, 32bits-PAE and 64bits Ubuntu kernel-benchmarks just a while ago:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by steveneddy on 2010-01-10
If one has 64 bit hardware they should run 64 bit software.

Everything works better in 64 bit.

I've been on 64 bit since Edgy or Feisty.

---

### Post by Manyette on 2010-01-10
If you say so, but "happyhamster"'s post about phoronix benchmarks seems to disagree with you, unlessl you're running the Apache server!

---

### Post by happyhamster on 2010-01-10
> **Manyette said:**
> If you say so, but "happyhamster"'s post about phoronix benchmarks seems to disagree with you, unlessl you're running the Apache server!
Err, basically every single benchmark in that series of tests is in favour of 64-bits. Exception is the first test: all results are equal there (the video card is the bottleneck I presume), and the Apache and Postmark tests: 64 bits has an enormous advantage there (some bug I presume).

Still, what I mean to say is: 64-bits is the way to go.

---

### Post by Manyette on 2010-01-10
Well, you are correct for the more advanced user.  But for us newbies, that first test covers most of what we normally do and use.  Not knocking 64 bit usage at all.  My laptop is a core duo which is a 64 bit machine, and I will be happy to go that route when it gets to be mainstream.  Just don't want to go with Alpha software right now.  Hoping to do that with Lyric when the end of April rolls around.

---

### Post by oldos2er on 2010-01-10
Flash is the only alpha software I'm aware of on 64-bit Ubuntu, and in my experience it has been more stable than 32-bit flash run with nspluginwrapper. For most software in the repositories, 32- and 64-bit are at the same version.

---

### Post by Manyette on 2010-01-10
As an old OS/2 programmer, I thank you for the update.  I was u;nder the impression that there was more than flash that was a problem.  Especially if you read some of the problems that folks are having, according to some forum posts.  But I still want to wait for Lucid before I make the change.  But thanks for the information.

---

### Post by dcstar on 2010-01-11
> **oldos2er said:**
> Flash is the only alpha software I'm aware of on 64-bit Ubuntu.......

64-bit Flash is **not** "Alpha" software, Adobe moved it to Pre-release status a while ago:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Things change a lot in the 64-bit world, people who do not pay attention keep repeating all sorts of now inaccurate information which does little to give people a realistic view of the current situation.

I almost feel like throwing up when I still see things in the forums like "I used 64-bit 2/3/4 years ago and it was rubbish - stay away from it..." or quote some link from some benchmark done 18 months ago - all of this is basically out of date and useless.

---

### Post by sliketymo on 2010-01-11
It's only the folk's that are having problems that post for help in help forums.It is my understanding that there were so few 64-bit specific problems,that the forum mod's did away with the seperate 64-bit specific thread.That aught to tell you something.

---

### Post by hawthornso23 on 2010-01-11
No reason not to go 64 bit now IMO. Mine works fine.

Only problem I've ever had with 64 bit is a missing library.

To be specific be specific the 32 bit version of libstdc++.so.5  
which should reside in /usr/lib32 was inexplicably dropped from 
Karmic. This can cause some 32 bit binaries to stop working. 

However the fix is not hard - just manually download and install the 
missing library.

---

### Post by JoelOl75 on 2010-01-11
> **Manyette said:**
> Not knocking 64 bit usage at all.  My laptop is a core duo which is a 64 bit machine, and I will be happy to go that route when it gets to be mainstream.

The COre Duo is NOT a 64 bit machine.  A Core 2 Duo is.

---

### Post by cascade9 on 2010-01-11
> **dcstar said:**
> 64-bit Flash is **not** "Alpha" software, Adobe moved it to Pre-release status a while ago:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Things change a lot in the 64-bit world, people who do not pay attention keep repeating all sorts of now inaccurate information which does little to give people a realistic view of the current situation.

I almost feel like throwing up when I still see things in the forums like "I used 64-bit 2/3/4 years ago and it was rubbish - stay away from it..." or quote some link from some benchmark done 18 months ago - all of this is basically out of date and useless.

Yay. +1

I get a bit sick of people stating '64 bit this/that' and using data that is years out of date. 

> **Manyette said:**
> Well, you are correct for the more advanced user.  But for us newbies, that first test covers most of what we normally do and use.  Not knocking 64 bit usage at all.  My laptop is a core duo which is a 64 bit machine, and I will be happy to go that route when it gets to be mainstream.  Just don't want to go with Alpha software right now.  Hoping to do that with Lyric when the end of April rolls around.

64bit IS 'mainstream' now. 

I agree with oldos2er as well, I've found 64bit flash is more stable etc than 32bit.

---

### Post by hobo14 on 2010-01-11
> **Manyette said:**
> Well, you are correct for the more advanced user.  But for us newbies, that first test covers most of what we normally do and use.  Not knocking 64 bit usage at all.  My laptop is a core duo which is a 64 bit machine, and I will be happy to go that route when it gets to be mainstream.  Just don't want to go with Alpha software right now.  Hoping to do that with Lyric when the end of April rolls around.

Not being belligerent or rude here, just genuinely curious: what will you consider "mainstream"?

I'd personally consider them mainstream now; it's actually not easy to find a new 32 bit machine these days (except netbooks).

---

### Post by Manyette on 2010-01-11
> The COre Duo is NOT a 64 bit machine. A Core 2 Duo is.
Well, that may be what you believe, however the machine is clearly labelled Core Duo and 64 bit.  It came with Win 7 64 bit, and hwinfo also identifies it as such.

---

### Post by Manyette on 2010-01-11
> I'd personally consider them mainstream now; it's actually not easy to find a new 32 bit machine these days (except netbooks).
Well, to me, mainstream means that the Ubuntu front page automatically downloads by default the 64 bit version, but I don't intend to wait that long.  As I said, I intend to go to 64 bit when lucid arrives. I prefer to do a fresh install, as opposed to an upgrade, and it just seems to me that a new version is the time to do that.  I appreciate that you guys are advocates for 64 bit, and I'm not disagreeing with you, I just feel it's easier to wait for the new version before converting.

---

### Post by oldos2er on 2010-01-11
> **dcstar said:**
> 64-bit Flash is **not** "Alpha" software, Adobe moved it to Pre-release status a while ago:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)


 Ok, it was alpha until last month. My bad.

---

### Post by oldos2er on 2010-01-11
> **Manyette said:**
> As an old OS/2 programmer, I thank you for the update.

 Maybe someday if you're bored, you could whip up a Linux DE identical to OS/2's WPS!  :)

---

### Post by Manyette on 2010-01-11
> 
The COre Duo is NOT a 64 bit machine. A Core 2 Duo is.
Joel0175,my humble apologies. It is a core 2 duo, please blame it on my cataracts and the #&@&@#@ printer who used blank on dark blue!

---

### Post by Manyette on 2010-01-11
> Maybe someday if you're bored, you could whip up a Linux DE identical to OS/2's WPS! 
Well Ann, not a bad idea at all, but after 20 years of retirement, I'm not sure I'm capable of programming my way out of the proverbial bag.  Besides, if i WAS capable, i'd probably want to go full Object oriented!L [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by philinux on 2010-01-11
> **oldos2er said:**
> Ok, it was alpha until last month. My bad.

It's been pre release for about 9 months. That version last month was just another refresh.

Also this is a better benchmark article.
[http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

There have been no downsides for me.

---

### Post by sanderj on 2010-01-11
> **happyhamster said:**
> Phoronix presented some 32bits, 32bits-PAE and 64bits Ubuntu kernel-benchmarks just a while ago:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

Very informative. Thank you.

My conclusion after only looking at the diagrams:
1) 32-bit PAE has the same speed as 32-bit. So it's safe to deploy if you have got more than 3GB RAM
2) 64-bit offers speed improvements over 32-bit, so it's useful to use 64-bit

FWIW: I use 64-bit Ubuntu since summer 2007 without problems; flash and java work out-of-the-box.

---

### Post by usererror on 2010-01-12
I have installed the 64bit Ubuntu on a AMD Turion X2 64bit laptop I have.

I have also installed the Flash Player that was posted here, and it works, a bit choppy at the adobe.com website when playing something but it works.

I have found this doc, [http://java.sun.com/javase/6/webnotes/install/jre/install-linux-64.html#requirements](http://java.sun.com/javase/6/webnotes/install/jre/install-linux-64.html#requirements) saying that there is no 64bit web plugin for Java.  Is that true?  I'm assuming then i can't use websites that rely on a Java plug in, that would be a big bummer.  Or can I install the 32bit Java web plugin?

I do not know what PAE is, and if it's not in the Repo's I dont think I am gonig to attempt it, unless I have to.

Thanks!

---

### Post by Manyette on 2010-01-12
PAE is Physical Address Extension, and if you have more than a couple of gigs of memory, it shouldl install automatically on install.  It allows access to your higher memory.  It works well

---

### Post by cascade9 on 2010-01-13
> **Manyette said:**
> Well, to me, mainstream means that the Ubuntu front page automatically downloads by default the 64 bit version, but I don't intend to wait that long. 

That is going to be a long time IMO. I would guess that the ubuntu page wont go to 'default to 64bit' for years yet, if anything its more likely to start using some sort of questionnaire instead, or use a '4GB or less- go use this link', '4GB+, use this link'. 

Just to avoid 'average uses' (whoever they are) getting frustrated because hey have the wrong install disc. 

> **Manyette said:**
> PAE is Physical Address Extension, and if you have more than a couple of gigs of memory, it shouldl install automatically on install.  It allows access to your higher memory.  It works well

IMO, PAE should be used in only 2 uncommon occasions- 32bit only systems with 4GB+ of RAM, and people who are running a 32bit OS on 64bit capable systems who have upgraded to 4GB+ after installing the 32bit version. Everyone else should just use what their system supports.

---

### Post by sanderj on 2010-01-13
> **Manyette said:**
> PAE is Physical Address Extension, and if you have more than a couple of gigs of memory, it shouldl install automatically on install. 

Well, that would be nice, but alas it's not the case; you have to install the PAE kernel by hand.

---

### Post by hawthornso23 on 2010-01-13
> **usererror said:**
> 

I have found this doc, [http://java.sun.com/javase/6/webnotes/install/jre/install-linux-64.html#requirements](http://java.sun.com/javase/6/webnotes/install/jre/install-linux-64.html#requirements) saying that there is no 64bit web plugin for Java.  Is that true?  I'm assuming then i can't use websites that rely on a Java plug in, that would be a big bummer.  Or can I install the 32bit Java web plugin?

Thanks!

There are so many versions of Java floating around who can keep track? However I've got a 64 bit system and have never had trouble using Java on websites. So whatever version it is that comes installed as standard on a 64 bit system manages to do the job, no problem.

---

### Post by Cheesemill on 2010-01-13
> **cascade9 said:**
> That is going to be a long time IMO. I would guess that the ubuntu page wont go to 'default to 64bit' for years yet, if anything its more likely to start using some sort of questionnaire instead, or use a '4GB or less- go use this link', '4GB+, use this link'.

The download page currently checks what OS you're running and defaults to 32-bit if you're running a 32-bit OS and 64-bit if you're running a 64-bit OS.
Anyone who has a new machine running Window 7 x64 will automatically be offered the 64-bit download.

---

### Post by sanderj on 2010-01-13
> **cascade9 said:**
> 
IMO, PAE should be used in only 2 uncommon occasions- 32bit only systems with 4GB+ of RAM, and people who are running a 32bit OS on 64bit capable systems who have upgraded to 4GB+ after installing the 32bit version. Everyone else should just use what their system supports.

<OLD I would say: always use the PAE-kernel unless the CPU doesn't support it. /OLD>

<NEW EDIT:
I would say: **the 32-bit CD should** always use the PAE-kernel, unless the CPU doesn't support it.
/NEW /EDIT>


Reason:
PAE has no negative effects, and thus is 'harmless' if not used.
PAE has the postive effect of making memory above the 3.2 GB barrier accessible & usable.

---

### Post by Manyette on 2010-01-13
> Well, that would be nice, but alas it's not the case; you have to install the PAE kernel by hand. 
Well, it installed it automatically on my 4 gig laptop, and I took a couple of days before I noticed the kernel was different from the one on my 32 bit laptop.

---

### Post by Manyette on 2010-01-13
> I have found this doc, [http://java.sun.com/javase/6/webnote...l#requirements](http://java.sun.com/javase/6/webnote...l#requirements) saying that there is no 64bit web plugin for Java. Is that true? I'm assuming then i can't use websites that rely on a Java plug in, that would be a big bummer. Or can I install the 32bit Java web plugin?
I have just gone from 32 bit to 64 bit, and all the "standard" usages "just worked", as advertised.  I still have not been able to get Skype loaded, and am having trouble with LaCie lightscribe, although I know others have made them work.  But all the other things, such a Adobe worked just fine. But those two may cause me to go back to 32 bit the way things are going right now!

---

### Post by sanderj on 2010-01-13
> **Manyette said:**
> Well, it installed it automatically on my 4 gig laptop, and I took a couple of days before I noticed the kernel was different from the one on my 32 bit laptop.

Very interesting, as I still see a lot of posts saying "Ubuntu only 3GB of my 4GB". That should not occur anymore if PAE is installed automagically.

Can you post the "uname -a" output? It's plain Ubuntu?

---

### Post by Manyette on 2010-01-13
Hi All, Yes, it was standard Ubuntu download of Karmic.  I cannot post what you want, because as I said in an earlier post, I've just loaded the 64 bit version of Karmic.  However, I can tell you that the system monitor showed 3.8 gigs of memory.  I assume that the remaining 0.2 gigs was allocated to video and such.  Don't know if that will help you or not.

---

### Post by sanderj on 2010-01-13
> **Manyette said:**
> Hi All, Yes, it was standard Ubuntu download of Karmic.  I cannot post what you want, because as I said in an earlier post, I've just loaded the 64 bit version of Karmic.  However, I can tell you that the system monitor showed 3.8 gigs of memory.  I assume that the remaining 0.2 gigs was allocated to video and such.  Don't know if that will help you or not.

Well, I guess now I have to delete my 64-bit Ubuntu, and install 32-bit Ubuntu on my 4GB machine to see what happens ... ;-)

---

### Post by cascade9 on 2010-01-13
> **sanderj said:**
> I would say: always use the PAE-kernel unless the CPU doesn't support it.

Reason:
PAE has no negative effects, and thus is 'harmless' if not used.
PAE has the postive effect of making memory above the 3.2 GB barrier accessible & usable.

So 64bit is harmfull? LOL 

I said what I did about 'everybody who is 64bit compatible should use it' because all the major problems with 64bit are gone now. It gives you a sizeable performance increase in any number crunching tasks, and even on 'normal' tasks its got an edge on PAE. 

See the benchmarks in the posts by philinux and happyhamster. 

Why anybody without some 'special' needs would install 32bit to run PAE if they can use 64bit is beyond me. Its not 2004 anymore, 64bit is very good. (as for 'special' needs...I dont know of any. but I'm sure that somebody, somewhere, has a reason to run 32bit with PAE) 

Why stick with a hack when there is a better solution?

---

### Post by sanderj on 2010-01-13
> **cascade9 said:**
> So 64bit is harmfull? LOL 

I said what I did about 'everybody who is 64bit compatible should use it' because all the major problems with 64bit are gone now.
<snip>


Oops, a misunderstanding: I meant the **32-bit install** should install PAE by default. I will EDIT my post.

And it's a fact that ubuntu.com still offers 32-bit as default. The 64-bit version is even quite hard to find. I guess ubuntu/canonical has it's reason for that.
As long as 32-bit is default, I would say 32-bit PAE should be default.

FYI: I'm on 64-bit since the summer of 2007, and I've never experienced any 64-bit problems.

---

### Post by usererror on 2010-01-13
PAE must have auto-installed as those have said here because the System Monitor shows 3.9GiB of memory and a 9.4GiB swam partition.

My Kernel version is also: 2.6.31-17-generic-pae

Now since I just bought a Core 2 Duo processer and those here have said that is a 64bit processor I guess I should re-do my install with the 64bit Ubuntu.  I didn't know the Core 2 Duo was a 64bit processor.

---

### Post by cascade9 on 2010-01-13
> **sanderj said:**
> Oops, a misunderstanding: I meant the **32-bit install** should install PAE by default. I will EDIT my post.

And it's a fact that ubuntu.com still offers 32-bit as default. The 64-bit version is even quite hard to find. I guess ubuntu/canonical has it's reason for that.
As long as 32-bit is default, I would say 32-bit PAE should be default.

FYI: I'm on 64-bit since the summer of 2007, and I've never experienced any 64-bit problems.

No problem, I was being....heh heh...something. 

Yeah, ubuntu still has 32bit as default because it works fine on all x86 machines. I think they take the opinion that if you know enough to know you want 64bit, your smart enough to find it. 

They really dotn want to alienate users by making 64bit default, and having cries of 'why isnt this working', gnashing teeth over the issue, driving away potential users,  bad press over the issue, etc. Understandable really. 

Thats why I think it will be a long, long wait, if ever, till ubuntu defaults to 64bit. 

Maybe when 128bit machines hit the market, in numbers, they will change then.

---

### Post by Cheesemill on 2010-01-13
> **sanderj said:**
> And it's a fact that ubuntu.com still offers 32-bit as default. The 64-bit version is even quite hard to find. I guess ubuntu/canonical has it's reason for that.
As long as 32-bit is default, I would say 32-bit PAE should be default.

I guess you missed my post:
> **Cheesemill said:**
> The download page currently checks what OS you're running and defaults to 32-bit if you're running a 32-bit OS and 64-bit if you're running a 64-bit OS.
Anyone who has a new machine running Window 7 x64 will automatically be offered the 64-bit download.

---

### Post by cascade9 on 2010-01-13
> **Cheesemill said:**
> The download page currently checks what OS you're running and defaults to 32-bit if you're running a 32-bit OS and 64-bit if you're running a 64-bit OS.
Anyone who has a new machine running Window 7 x64 will automatically be offered the 64-bit download.

Maybe on windows. 64bit linux here, and it still gives me the 32bit installer when I hit the 'download ubuntu' button on the main page.

---

### Post by Cheesemill on 2010-01-13
> **cascade9 said:**
> Maybe on windows. 64bit linux here, and it still gives me the 32bit installer when I hit the 'download ubuntu' button on the main page.

Odd. On my 64-bit Ubuntu it defaults to the 64-bit download.

---

### Post by cascade9 on 2010-01-13
I'm not using 64bit ubuntu (debian squeeze here)

It would be interesting to see if it works with other distros, or if it just works on windows/ubuntu. I'm guessing only windows/ubuntu. I'll have to see if it goes to that page on win XP64. :)

---

### Post by sgage on 2010-01-13
I have been running 32-bit Ubuntu on my current machine since Hardy, but finally decided to go with 64-bit for Karmic. I have had no problems with anything, and it is perceptibly faster on many things, less noticable on others.

I have not experienced any incompatibilities or instabilities whatsoever. I think 64-bit computing comes of age with Karmic. I would recommend that anyone with a 64-bit processor and lots of RAM give it a try.

My machine is not exactly high-end: I have a Pentium Dual Core E2180 (2 GHz), 4 GB RAM, and NVIDIA GeForce 8500 GT graphics. System Monitor shows 3.9 GiB available RAM. Karmic runs like a dream on this rig.

---

### Post by Manyette on 2010-01-13
Probably because it has sensed that that is what is already installed!

---

### Post by Matt_Johnson on 2010-01-13
No downsides at all, Infact it will even run better then 32 bit cause it will read all 4gb of your ram!

---

### Post by sanderj on 2010-01-13
> **cascade9 said:**
> Maybe on windows. 64bit linux here, and it still gives me the 32bit installer when I hit the 'download ubuntu' button on the main page.

Exactly: I booted 64-bit Ubuntu, went to ubuntu.com, and still get 32-bit Ubuntu offered as download. See screendump.

FYI: my User Agent is "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.3) Gecko/20091020 Ubuntu/9.10 (karmic) Firefox/3.5.3"

So: Ubuntu.com defaults to 32 bit.

---

### Post by Slim Odds on 2010-01-13
> **Matt_Johnson said:**
> No downsides at all, Infact it will even run better then 32 bit cause it will read all 4gb of your ram!

No, it reads all 8GB of my RAM  :P

But seriously, I totally agree with some of the previous posts about people having fears about problems that no longer exist.

I've been using 64 bit since 8.10 and it's fabulous!!.

My personal, anecdotal opinion is that it is much more stable than the already very stable 32 bit version.

If you have a 64 bit machine, it's a waste not to use it.

---

### Post by Manyette on 2010-01-14
Hi All, Well, I bit the bullet and went to Karmic 64.  Got everything working except for LaCie Lightscribe.  All the "howto's" are outdated or refer to libs that have changed.  Has anyone gotten it to work recently?  Sure could use some help getting it working.

---

### Post by cascade9 on 2010-01-14
> **Manyette said:**
> Hi All, Well, I bit the bullet and went to Karmic 64.  Got everything working except for LaCie Lightscribe.  All the "howto's" are outdated or refer to libs that have changed.  Has anyone gotten it to work recently?  Sure could use some help getting it working.

I havent tried it myself, but theres instructions here- 

> [SIZE=2]sudo apt-get install ia32-libs
sudo dpkg -i --force architecture lightscribe-1.18.6.1-linux-2.6-intel.deb        
sudo dpkg -i --force architecture lightscribeApplications-1.18.6.1-linux-2.6-intel.deb
sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/
sudo ldconfig[/SIZE][http://www.lightscribe.com/discussionBoards/index.aspx?g=posts&t=2724](http://www.lightscribe.com/discussionBoards/index.aspx?g=posts&t=2724)

Of course, you'll need the installer- 

[http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372)

Currently at version "lightscribe-1.18.10.2-linux-2.6-intel.deb" so maybe the problem is gone. I'd try with the the standard installer 1st, and if (when?) that fails mod the commands above. 

BTW, you will also need the labeling software, its up here- 

[http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1374](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1374)

---

### Post by Manyette on 2010-01-14
Thanks Cascade9, I'll try that and get back to you.  I've tried the standard installer with no success.  Hope this will work.  I already have most of the templates and such since I had it working before I went to 64 bit.

---

### Post by Manyette on 2010-01-14
Oooppsss!  Looked closer and those are for lightscribe, which is pretty much useless.  I'm trying to get LaCie working.  That's where I've been having the problem, but I thank you anyway.

---

### Post by cascade9 on 2010-01-14
LaCie lightscribe is just a lightscribe DVD burner in an external USB box, right? It should work with the lightscribe software. *confused* If it doesnt LaCie shouldnt be calling it lightscribe IMO. 

Odd that they have software on their site for linux though- 

[http://www.lacie.com/us/products/product.htm?pid=10803](http://www.lacie.com/us/products/product.htm?pid=10803)

Bet its 32bit :|

---

### Post by Manyette on 2010-01-14
The Lightscribe software is only capaboe of the simplest labels,m at least under linux.  Basially one line at top and one at bottom.  The LaCie lightscribe software can print on the entire disk, and accepts any jpg or png image, instead of just text.  And lightscribe is the drive technology, so why not call it lightscribe.  It may be 32 bit, probably is, but it's better than nothing, and better than a very simplo 2 line text in small print..

---

### Post by cascade9 on 2010-01-14
> **Manyette said:**
> The Lightscribe software is only capaboe of the simplest labels,m at least under linux.  Basially one line at top and one at bottom.  The LaCie lightscribe software can print on the entire disk, and accepts any jpg or png image, instead of just text.  And lightscribe is the drive technology, so why not call it lightscribe.  It may be 32 bit, probably is, but it's better than nothing, and better than a very simplo 2 line text in small print..

Sometimes, you just have to look around to find software that does what you want it to-


> Lacie LightScribe Labeler for Linux (4L) lets you use LightScribe direct-disc labeling technology with your Linux system. Now you can burn professional, silkscreen-quality labels directly onto CDs and DVDs using the same laser that burns data on discs. It's easy; just burn data as usual, flip the LightScribe disc over, reinsert it into the drive and burn a precise, iridescent label of your own design.

User Benefits:

 - User-friendly interface: 3-step labeling process
 - Import photos and etch them directly onto CD/DVDs
 - Perfect complement to K3b - CD/DVD Kreator

 [http://linuxappfinder.com/package/lightscribelabeler](http://linuxappfinder.com/package/lightscribelabeler)

That will let you use images, etc. Its just 32bit as well, btu you should be able to get it going with 64bit. Maybe you would do best to start a thread on lightscribe here (or even check to see if there is one).

---

### Post by Manyette on 2010-01-14
Gee, I thought that was what I was saying :=P.  But the posts on the subject are outdated due to lib upgrades and such.  I guess I'll just drop it for a while until someone more knowledgeable than this newbie can figure it out, or LaCie updates their linux software.  It's not like its a terrible loss.  I still have marker pens! :-)

---

### Post by JDorfler on 2010-01-14
*For 64-bit

sudo dpkg --force-architecture -i lightscribe-1.18.4.1-linux-2.6-intel.deb

sudo dpkg --force-architecture -i lightscribeApplications-1.10.19.1-linux-2.6-intel.deb

sudo dpkg --force-architecture -i 4l_1.0-r6_i386.deb

*Fix the missing liblightscribe.so.1 error

sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/

sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/

sudo ldconfig

*For 32-bit

sudo dpkg -i lightscribe-1.18.4.1-linux-2.6-intel.deb

sudo dpkg -i lightscribeApplications-1.10.19.1-linux-2.6-intel.deb

sudo dpkg -i 4l_1.0-r6_i386.deb

*Fix the missing liblightscribe.so.1 error

sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/

sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/

sudo ldconfig

*For full labeler

Type: Application
Name: Lightscribe
Command: sudo 4L-gui
Comment: Label a disc with Lightscribe

---

### Post by Manyette on 2010-01-14
Well, I failed on the first line.

> sudo dpkg --force-architecture -i lightscribe-1.18.4.1-linux-2.6-intel.deb

> dpkg: error processing lightscribe-1.18.4.1-linux-2.6-intel.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lightscribe-1.18.4.1-linux-2.6-intel.deb

Am I missing a repo?

---

### Post by cascade9 on 2010-01-14
> **Manyette said:**
> Well, I failed on the first line.

Am I missing a repo?

If your trying to run a newly downloaded installer, the command is 

sudo dpkg --force-architecture -i lightscribe-1.18.10.2-linux-2.6-intel.deb

The newer install is a different version, so the older version number wont work. You will also need to be in the directory where its been downloaded to. 

> **Manyette said:**
> Gee, I thought that was what I was saying :=P. But the posts on the subject are outdated due to lib upgrades and such. I guess I'll just drop it for a while until someone more knowledgeable than this newbie can figure it out, or LaCie updates their linux software. It's not like its a terrible loss. I still have marker pens! :-)

Doh, wrong link....bah, its 4AM, time for sleep.

---

### Post by JDorfler on 2010-01-14
> **cascade9 said:**
> If your trying to run a newly downloaded installer, the command is 

sudo dpkg --force-architecture -i lightscribe-1.18.10.2-linux-2.6-intel.deb

The newer install is a different version, so the older version number wont work. You will also need to be in the directory where its been downloaded to. 



Doh, wrong link....bah, its 4AM, time for sleep.

Sorry I forgot to explain that for you guys.  Make sure the deb file is in your home directory, then change the install file name to what you need it to be.  I haven't updated to the latest and greatest stuff due to the older stuff has always been stable and working for me.

---

### Post by Manyette on 2010-01-14
Another failure.

 > sudo dpkg --force-architecture -i lightscribe-1.18.10.2-linux-2.6-intel.deb
dpkg: error processing lightscribe-1.18.10.2-linux-2.6-intel.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lightscribe-1.18.10.2-linux-2.6-intel.deb

This is the kind of thing I've been running into all along.  I think I'll just give up on it for a while.  (The marker pen still jworks.  :-)  Thanks anyway, I do appeciate all the help.

---

### Post by cascade9 on 2010-01-15
No problem...I just wonder, did you actually have the package? and were you in the same directory. Because that 'No such file or directory' makes me think that you dont have the package, or your not in the right dir.

---

### Post by d3v1150m471c on 2010-01-15
A little off topic but if you are looking to speed up your computer then look into howto's for vm.swappiness and vm.vfs_cache_pressure. You can adjust these and see massive improvement. I've messed around with these a lot and are fairly familiar with what works and what doesn't. For more info feel very free to drop me a private message as I am on these forums all the time.

---

### Post by Manyette on 2010-01-15
I probably don't understand what package you are referring to.  And undoubtedly that's part (if not all) of the problem.  Do I have the LaCie package?  Yes.  What other package do I need?  This is now just curiosity, because it has gotten to be not worth the effort any longer.  When I have to spend days just trying to find out how to do an install, it just isn't worth it.  I do thank you for all your attempts to help this idiot, but time to "call in the dogs"!

---

### Post by d3v1150m471c on 2010-01-15
these aren't packages. these are sysctl configurations that decide how your computer uses ram, swap space, and how it caches information to be used.

---

### Post by d3v1150m471c on 2010-01-15
I altered this script to so everyone on newer versions of ubuntu can use it. It should have read and write permissions to change it to your liking. **do not use this if you have less than 1gb of ram...** I encourage anyone who uses it to read the script. A: to learn what exactly it does and B: know that i'm not making something malicious on your system.

1. Extract the file and save it to your home folder.
2. Create a custom application launcher in your panel and name it utweak.
3. Set the command for the application launcher to: 
          gnome-terminal -e ./utweak
4. Click to run utweak.
5. Enjoy.

I encourage you to play around with this.... cache pressure and swappiness can be 0-100.
The less cache pressure, the more aggressively your computer will store data in your Ram so it can access it faster. The less swappiness, the more your system will rely on its Ram and less on the swap space. This is good because Ram is much faster than your hard drive's swap space when accessing information. I left it at 10 because your system does need computer swap space. Especially for stuff like hibernating and the like. I did leave the cache pressure @ 0... you may want to change this because it will fill up the Ram with cache information really quick...I've never had any trouble with this but for some users it may be a problem.

[B]This will not make any permenant alterations to your system.

[/B]You can check your current settings with these two commands :
sysctl -q vm.swappiness
sysctl -q vm.vfs_cache_pressure

---

### Post by Mike'sHardLinux on 2010-01-17
> **Manyette said:**
> I probably don't understand what package you are referring to.  And undoubtedly that's part (if not all) of the problem.  Do I have the LaCie package?  Yes.  What other package do I need?  This is now just curiosity, because it has gotten to be not worth the effort any longer.  When I have to spend days just trying to find out how to do an install, it just isn't worth it.  I do thank you for all your attempts to help this idiot, but time to "call in the dogs"!

No offense, but having read this whole thread so far, the problems you are having are due to not paying attention.

I made the 3rd post in this thread, and had already mentioned that you need to use --force-architecture with dpkg for 32-bit packages like LaCie Lightscribe. 

> **Manyette said:**
> Well, I failed on the first line.

```
dpkg: error processing lightscribe-1.18.4.1-linux-2.6-intel.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
lightscribe-1.18.4.1-linux-2.6-intel.deb 
```



Am I missing a repo?

This error you are now getting is obviously due to either the name of the package is not exactly what you think it is, or you are not in the same directory where the package is located....or, you forgot to download the package....

---

### Post by Manyette on 2010-01-17
Yes you did mention it back then.  But the post where I listed the output was not in a reply to you, but to someone else.  I did try all the variations suggested, including that one.  None workedm, before I gave it up as a bad job.

---

### Post by d3v1150m471c on 2010-01-17
> **Matt_Johnson said:**
> No downsides at all, Infact it will even run better then 32 bit cause it will read all 4gb of your ram!

Something doesn't sound right if ubuntu is using up all 4gb's of your RAM. I am running a toshiba l305 on a 32 bit processor with 4gb's of RAM. The most I ever see my ram climb up to is 25%. 25% being actively used and at that I have my system to run rather aggressively from RAM. You may want to see if something weird is consuming it and/or adjust your settings.

PS. I may have read your post wrong as well. Not entirely sure if you're saying it's consuming all your resources or if it processes your ram better.

---

### Post by bodhi.zazen on 2010-01-17
> **usererror said:**
> I now have 4GB of RAM in my PC, up from 1.5GB.  If I want to utilize the full 4GB I understand that I have to install the 64bit Edition of Ubuntu.

What are the pitfalls of doing so?  Will all basic functions still work like flash player, java, firefox, etc?

In the past I have used Windows 64 bit editions and it was very frustrating to have seperate folders for 32bit vs 64bit applications.

The extra RAM would be helpful for running my virtualbox sessions.

Thanks for any input or advice into this area!

64 bit Ubuntu has been around for long enough and discussed enough that this qualifies as a recurrent discussion.

---

### Post by blueshiftoverwatch on 2010-01-17
> **usererror said:**
> What are the pitfalls of doing so?
Someone may have already posted this, I didn't go through all 8 pages of posts. But the only real problem I've had with 64 bit Linux is that 32 bit emulators won't work. Compiling them from source doesn't help matters any either.

---

### Post by usererror on 2010-01-21
Since this thread and the responses, I've made the plunge and put 64bit on both my amd 64bit laptop and my intel core 2 duo desktop (which i did not know was also 64bit). 

so far everything has actually been great.  even flash playing is far superior.  I am quite happy.  thanks for the advice.

---

### Post by carjack on 2010-01-22
> **usererror said:**
> Since this thread and the responses, I've made the plunge and put 64bit on both my amd 64bit laptop and my intel core 2 duo desktop (which i did not know was also 64bit). 

so far everything has actually been great.  even flash playing is far superior.  I am quite happy.  thanks for the advice.


You are a legend in the making sir, These type of posts I love to read.

---

### Post by usererror on 2010-01-23
> **carjack said:**
> You are a legend in the making sir, These type of posts I love to read.

Ha! that made me laugh.  Again though, this 64bit thing has been a great experience.  It beats the Windows 7 64bit experience.

EDIT:  Found my first "pitfall" the amazon mp3 downloader does not have a 64bit client for Ubuntu.  Had to use my VM of Windows.

Also found there is no 64bit Linux Citrix Client, which I use for work...also using windows VM for that...

---

