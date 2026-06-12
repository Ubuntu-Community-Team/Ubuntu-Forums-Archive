---
title: "[SOLVED] Hardware compatibility"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by utnubuuser on 2008-11-28
Hello --  Reading Gnu/Linux reviews I keep coming across references to hardware issues.  I'm wondering if anyone, (preferably someone with a bit of history in Gnu/Linux), can answer a question that keeps cropping up in my mind.

Statements like "Hardware compatibility isn't the issue it once was with linux", or "hardware compatibility has come a long way in linux".

I've only found Ubuntu since Feisty Fawn, (which is still my favourite), so I'm obviously new to Linux/Gnu, and haven't experienced "hardware issues", though I've installed to several different machines. 

I'm quite familiar with the forums and have read plenty about Video card driver problems, and wireless driver problems, but those are the only "hardware issues" I'm familiar with. Period.

My question is this:  Historically, has Linux had other "hardware compatibility issues", or are these kinds of remarks exclusively about the wifi, video card and occasional printer driver problems? 

Thanks

ps. If your wondering why I wrote "Linux/Gnu" instead of the customary "Gnu/linux, it's because I like to think Gnu's got Linux behind it.  Go ahead and correct me if I'm wrong.

---

### Post by halitech on 2008-11-28
I can't go back as far as some probably can but my first foray into linux was back in 2001 and Redhat 6 (I think) and that experience drove me back to windows for another 5 years when I found Ubuntu. Back then (I know I sound like an oldtimer with saying that) I had problems getting my video set up, no sound for 3 weeks (sound blaster card), no hope on the printer (lexmark) or scanner(acer scsi 610) and even configuring my nic was murder (ISA card). After 2 months I said blow this and reinstalled windows 2k and was up and running in a few hours. Do I blame this on linux? not at all. Today I can do a fresh install on even a lowly P200 and be up and running in less time then my old windows installs used to. 

Even today, the compatibility problems are not really the fault of linux but the companies that are making the hardware that refuse to give out specs or build their own drivers to make it easier to install in linux. But to answer your question, yes, setting up hardware back even 5 years ago was alot more troublesome and more likely to be more then just wireless (basically non-existant 5 years ago), printers and video cards.

---

### Post by utnubuuser on 2008-12-02
Thanks halitech

I figured it was mostly a wifi, and video card thing.  I just wondered if there had been other compatibility issues. 
I'm of the understanding that the linux kernel surpasses most operating systems insofar as hardware recognition and compatibility are concerned.

---

### Post by gTinker on 2008-12-02
[QUOTE=utnubuuser]
My question is this:  Historically, has Linux had other "hardware compatibility issues", or are these kinds of remarks exclusively about the wifi, video card and occasional printer driver problems?[/QUOTE] 

Well, in the past the issues were mostly video and sound cards (sound card issues used to be a biggie) and printers. But where do the issues arise? Most of the time they come from new hardware, hardware for which driver modules have not yet been developed or, sometimes a buggy new driver. In the far past, hardware manufacturers often didn't share their hardware "secrets" like how to make a new piece of equipment work, thus open source developers had to reverse engineer in order to produce driver modules. This is less true today (only somewhat less). They always did though, produce Windows drivers, that was the bulk of the market. Many, perhaps still most, hardware issues come about because the hardware is newer than the hardware driver modules in the kernel. The issue comes up on Windows systems too, it's just that most people get their Windows computers with the operating system already installed and the drivers loaded by someone else and any new hardware that they add usually has a driver disk with it.

[QUOTE=utnubuuser]
ps. If your wondering why I wrote "Linux/Gnu" instead of the customary "Gnu/linux, it's because I like to think Gnu's got Linux behind it.  Go ahead and correct me if I'm wrong.[/QUOTE]

Well, Linux is the kernel. It isn't necessary to run the Linux kernel with GNU software and the kernel isn't much use without the software to run. There is probably a reason that developers choose to call it GNU/Linux and there probably is a case to be made for standardisation when we use terms but I do follow your logic and in the open source world we are free to choose how to use things and how to think. My personal preference is the customary way, GNU with Linux behind it, GNU/Linux. Sometimes things are just a matter of point-of-view and perception.

---

### Post by utnubuuser on 2008-12-02
Hey - gTinker  -- Thanks.

About the Gnu/Linux... you're probably right, standardization is important. 
Been researching the marketing end of things lately, which is why all the questions.
Something I've noticed when promoting Ubuntu to friends and neighbors is that as soon as you mention that it's a Linux based OS, a mental barrier goes up.
Linux has considerable history, some good some not.  Mostly, I think, the average computer user equates Linux with system administration, the command line and hence, unfamiliar territory.  Like it's beyond their basic point and click skill level.(Which is too bad considering what a great tool/application the shell really is - I personally think it could be one of Linux's main selling points, -and I'm a CL noob).
One of the things I like about Ubuntu is that it's not promoted as "linux".  It's Ubuntu, nothing more nothing less.  The fact that it's linux under the hood  isn't hidden, but it's not the main focus.  - which is a better way of promoting it. (if that's a concern at all).
Windows doesn't advertise the fact that it's MS-Dos based or whatever.  Doesn't make sense to.   
Anyway, thanks again.

---

### Post by cmay on 2008-12-02
> Windows doesn't advertise the fact that it's MS-Dos based or whatever.  Doesn't make sense to.   i think after  windows xp they only use dos as a primtive bootloader. the shell in windows vista is being promoted as a powershell which has got a lot more unix like fetaures added to it for some reason. but this only makes sence to people who want to script and automate things. it just proves the command line days are not over yet.

---

### Post by gTinker on 2008-12-03
[QUOTE=utnubuuser]
Linux has considerable history, some good some not.[/quote] 

We'll have to agree to disagree on this point, for me it is all good.

[QUOTE=utnubuuser]
One of the things I like about Ubuntu is that it's not promoted as "linux".  It's Ubuntu, nothing more nothing less.  The fact that it's linux under the hood  isn't hidden, but it's not the main focus.  - which is a better way of promoting it. (if that's a concern at all).[/quote]

Well, I say Debian and Slackware and Mandrake(now Mandriva) too, no need to mention the kernel. Most users have very little concern with anything except that when they click on an icon the Internet opens up for them or when they push send, their email goes. Most of the other distros aren't promoted as much as Ubuntu, nor do they have an angel with deep pockets. In fact, there are still GNU/Linux users around that are against "promoting" Linux at all, because they get tired of the noobie questions. Thankfully there is room for all opinions and freedom of choice. In my opinion, that is a better way of promoting an alternative OS to Windows users, emphasis on freedom and choice.

---

### Post by hyper_ch on 2008-12-03
well, webcams are still problematic although in 8.10 or rather the kernel used by it, introduced support for a few new webcams...

I also read here that Creative Labs Soundcards can have issues...

---

### Post by scorp123 on 2008-12-03
> **utnubuuser said:**
>  Statements like "Hardware compatibility isn't the issue it once was with linux", or "hardware compatibility has come a long way in linux".  Yes, it has dramatically improved to the point where it's now the other way around: now I always have hardware issues with Windows (... just try and install Windows 2003 Server OS on a machine that has brand-new SAS controllers !!!! With Linux: you pop-in the CD and it will just boot, no problem whatsoever :D )

> **utnubuuser said:**
>  My question is this:  Historically, has Linux had other "hardware compatibility issues"  Yes. Plenty. SCSI controllers for example. It was back in 1999 and we had one of those Adaptec 29xxx-something controllers to which our RAID5 disks were connected. One fine day the controller got fried and we had to replace it ... and it would not work for some odd reasons. Turned out that the new one we had was a slightly different model with a slightly different firmware and the old Linux 2.0.xx and brand-new 2.2.xx kernels back then would not recognise it. But getting support was easy: You'd rush to the IRC channels of the kernel dev team and tell folks there about this new SCSI controller and its new PCI ID which it had. 24 hours later we downloaded a patch written by Linus himself and we were back in business.

That was the cool thing back then ... there were hardly any companies or bigger organisations back then that would back you. And we didn't feel it's needed. You got troubles ... you go to the IRC channels and talk to the devs directly. Some gurus on those IRC channels might be rude to you (especially if you asked things which they regarded as being "stupid questions"), ridicule you, ignore you or start flame arguments ... but that was part of the culture. And as you can see getting my a$$ kicked on IRC didn't kill me, I am still alive. I can't help but laugh when I see complaints of present-day noobs who complain about how they got treated on IRC or on the forums ... Holy moly ... That's all harmless compared to what us early noobs had to go through :D  And we're still alive. And we still use Linux. Seems like we had thicker skins back then? :D

> **utnubuuser said:**
>  or are these kinds of remarks exclusively about the wifi, video card and occasional printer driver problems?  It seems. I hate to quote this guy (I personally don't like him and his approach which says that "binary kernel drivers are 'illegal' ...) but Greg Kroah-Hartmann (= one of the Linux kernel developers!) once claimed that "No OS supports more hardware than Linux". .... And he's right. It's a fact. Linux runs pretty much anything and on anything. Coffee machines, wrist watches, TV sets, video recorders, exotic embedded controllers, hyper-modern SATA and SAS disk controllers... it's all supported these days. Out of the box. It's amazing. At work it doesn't matter how brand-new the SUN servers are which we get. Being SUN partners we sometimes even get pre-production / early-access / prototype machines which nobody else has yet ... and guess what: You can pop-in the most recent Ubuntu Live CD and the thing will just work, out of the box. No matter how brand-new or how much of a prototype that machine is.  Windows on the other hand on these same machines is a damn sad story .... :D

---

### Post by utnubuuser on 2008-12-04
gTinker  --  lol 

I suppose I should've said "perceived as good, or perceived as not so good.

And yes, you're right.  The freedom inherent in Free software is awesome.

---

### Post by utnubuuser on 2008-12-04
Sali Scorp123

Thanks -- great information.

Seems to support the idea that the kind of statements I was referring to are ill-founded.
I've used computers for work and play since the early eighties, and as far as I can remember, there were always hardware compatibility issues amongst all the systems.  Mac/Apple was so proprietary that if it wasn't made by Apple, it just wasn't going to be usable on an Apple system, and they charged "through the nose" in those days.  Same for the Windows environment, nothing but hardware issues all throughout the late eighties and early nineties.

I'm starting to think my  original question has more to do with a perception-phenomenon specific to Linux, or Gnu/linux operating systems.  
It seems that Linux is, and I'm seriously generalizing now, perceived as a very elite environment.
A common recurrence in most of the comparisons drawn between Linux/Free and proprietary systems is an exceptionally high level of expectation of Free software.
Any problems or shortcomings in Gnu/Linux systems  seem to be given an disproportionate level of significance compared to how the same shortcomings are viewed when they occur in proprietary systems.  
It really is some kind of social-phenomenon. An anti-stigma.  I don't know if it's simply because Gnu/Linux is free, (in either sense of the word), or because the public perception of Linux has been that it's a "Professional" system, requiring an inordinate amount of skill and knowledge.

Anyways...

thanks

---

### Post by utnubuuser on 2008-12-04
Hello hyper-ch 

Wie gehts, wie stehts?

> well, webcams are still problematic although in 8.10 or rather the kernel used by it, introduced support for a few new webcams...

Isn't it amazing how quickly the Linux kernel and Gnu/Linux are progressing in that regard though?

I'm using an IBM x31 Thinkpad (from 2004), and at Ubuntu 7.04, it was as though I'd installed a "generic" operating system, - though it was possible to tweak and customize my configuration files to get all the little bells and whistles functioning properly, it wasn't that way "out-of-the-box".  Now, with 8.04, and 8.10, Ubuntu on my laptop feels as though it's made specifically **for** this equipment. - Better than the OEM OS that came with the computer.

---

### Post by scorp123 on 2008-12-04
> **utnubuuser said:**
>  Seems to support the idea that the kind of statements I was referring to are ill-founded.  It depends highly on what hardware you are talking about. If it's some standard piece of equipment that adheres to certain standards and/or adheres to standards appropriate for its device class then there should be no problem. It should just work "out of the box".

Really problematic is hardware that does not adhere to standards, e.g. where the hardware producer thought it's "funny" to come up with something of their own. Motherboards come to mind that do some funky job when it comes to ACPI, despite ACPI being a standard ... except there are few hardware makers that implement it rather poorly. And there is hardware which is just a real sorry excuse for even being called "hardware" ... WinModems come to mind: those are no real modems. Windows has to emulate the modem in software. And if already that wasn't sad enough (as far as I remember it wasn't really stable at all) people would then blame Linux if those pseudo-modems would not work under Linux.

And then there is hardware such as various WiFi chipsets for which you need to load a firmware into the chipset at boot time ... and if that firmware happens to be regarded as being a "trade secret" you have to resort to funny constructs such as "ndiswrapper" which has to load the firmware off the windows driver you supply it with.

So yes, there might be hardware issues with certain types of hardware. But it's usually with vendors who "don't play nice". As (prospective) Linux user you're unlikely to run into hardware issues if you use Google and do some minimum research before buying hardware. Shouldn't be too hard.

> **utnubuuser said:**
>  Same for the Windows environment, nothing but hardware issues all throughout the late eighties and early nineties.  Yes, especially with ISA cards: you had to figure out the right base address (which hopefully wasn't used by anything else in your system) and the right IRQ (which hopefully wasn't occupied already) and then manually set jumpers or dip switches. Take "SoundBlaster" sound cards for example: you had to figure out a base address (e.g. 220h), you had to figure out a MIDI base address (e.g. 330h), you had to figure out an IRQ (e.g. IRQ5) and then maybe another one for the joystick port (IRQ11?). Too bad if you had more than one component that wanted to use the same resource ... that's when things would start getting "funny". The problem was universal, and not limited to Windows, Linux or any other OS at that time.

> **utnubuuser said:**
>  I'm starting to think my  original question has more to do with a perception-phenomenon specific to Linux, or Gnu/linux operating systems.  See above. At some point vendors started to produce "designed for Windows" hardware. They would enter into deals with Microsoft so that drivers for specific pieces of hardware would be included on the Windows 9x installer CD's ... for a price. If you refused to accept the conditions that Microsoft set you would all of a sudden have certain difficulties: the drivers for your hardware was not included on those Microsoft Windows installer CD's and for some odd reason your drivers were never signed (looks like Microsoft blatantly refused to certify certain drivers of certain vendors??) making you look bad in front of your (potential) customers. I have had hardware like that. Network cards for example. Scanners. SCSI cards. USB-Ethernet dongles .... and lots of other things. Under Windows XP it would say "driver not signed - don't install this!" whereas under Linux the same hardware would just work out of the box without any need for interaction or intervention from my part.

I think those Microsoft policies where they started forcing hardware vendors under their thumb were a mistake. I think that this was the moment where vendors (of desktop hardware) started to understand that a monopoly was not such a good idea after all and that it might be better if they opened up their specs ... ultimately: Why does a hardware vendor have to care about what OS his customer is running? If the hardware design is sane and reasonable it should run no matter what OS is thrown at it.

That's what I loved so much about Hewlett-Packard. I worked there 2000-2007. In mid-2000 HP announced that it would from now on regard Linux as being a **"strategic target OS"**. That's like receiving knighthood from the Queen of England. Linux wasn't "just some OS by some Finnish student" anymore. Now it was a "strategic target". It was "knighted". "Sir Linux" from now on. It wasn't a "nobody" anymore. It got noticed and now it mattered. It mattered enough so that lots of money was poured in. Linux wasn't just "hip" anymore, it had become a serious business. Divisions were setup and people were hired to cater to this new strategy (that's how I got my job there ...). And as far as I can tell they have lived up to this (e.g. paying developers full-time so they would do the porting of the Linux kernel to the IA-64 platform! Or their awesome Linux-compatibility when it comes to their printers!) and I wish more vendors would take this approach.

> **utnubuuser said:**
>  It seems that Linux is, and I'm seriously generalizing now, perceived as a very elite environment.  Maybe in the early 90's. But now? :D  Come on, Linux was never ever sooooo easy to use like today. My wife is a total noob and totally untalented when it comes to using computers but even she has no problems whatsoever getting around Ubuntu's GNOME desktop, reading e-mails, exchange baby pictures with her friends on Facebook, chat and do phone calls via Skype, and so on.

Some people regard Linux as being "hard" because it's different. Linux is not Windows. Therefore it must be "hard" because it does things differently. Unfortunately there are too many people out there who have this IMHO downright silly mindset ... and then they try out Linux and they are bound to be disappointed. So to them anyone mastering Linux just even a slight bit is "elite" or "elitist".

Back in the days where you'd need to manually download source code and manually patch and compile every and each of your binaries and write each config file line by line yourself ... yes, maybe it was "elitist" back then. But was DOS back then so different? I don't think so. 

A standard MS-DOS installation back in those days offered nothing "out of the box", you'd have to write files such as **CONFIG.SYS** and **AUTOEXEC.BAT** yourself if you wanted a sane DOS environment (e.g. with tricks like **DOS=HIGH,UMB** ... and other tweaks) and you'd spend hours trying to find the right order by which device drivers would need to be loaded for the optimum memory loadout. Load stuff in the wrong order and ... ooooops ... your lower 640K were totally full, meaning that no other MS-DOS program would able to start. But if you found the right order and if you were able to push all those drivers into the "Upper Memory Block" (UMB) you'd end up with a system with up to 635K low-mem free. Oh man when I think of this .... 635K of memory to work with :D  And today people complain about 2GB of RAM not being "enough". Anyway ... back in those days you would be regarded "elite" in MS-user circles if you were able to tweak their MS-DOS installations in such ways.

The difference back then between MS-DOS and Linux was only minimal. Both were text-based systems (with the GUI being an extra you'd need to start by hand, either via "win" for Windows 3.x on MS-DOS or "startx" on Linux) where you'd use the command line a lot and spend hours and hours tweaking some config files.

What really was different about the two was the obviousness by which Linux seemed many times more powerful. It was really obvious to anyone who was used to the MS-DOS command line. And Linux was able to see the whole of your addressable memory ... "Wooooot? No 640K barrier????" :D

> **utnubuuser said:**
>  Any problems or shortcomings in Gnu/Linux systems  seem to be given an disproportionate level of significance compared to how the same shortcomings are viewed when they occur in proprietary systems.  Exactly!

> **utnubuuser said:**
>  I don't know if it's simply because Gnu/Linux is free ...  That's a mixed bag I'd say. Some people simply seem not to understand that Linux is not Windows, never was meant to replace Windows and never will be just "another Windows". Other people have the approach "you get what you pay for" ... so if it's free it "can't be worth much". And then others think that the world is just waiting for them to convert and so they drown the forums with all kind of questions and then react in aggressive ways if they are not getting the kind of support they think they are entitled to. These kinds of users will most likely never be happy with Linux no matter how easy Linux has become. For them it will always be "too hard" and they will always identify "showstoppers" and then write nonsense as to "why Linux will never replace Microsoft!" ... Like it matters? It doesn't.

Regards. :)

---

### Post by gTinker on 2008-12-04
[QUOTE=utnubuuser]
I'm using an IBM x31 Thinkpad (from 2004), and at Ubuntu 7.04, it was as though I'd installed a "generic" operating system, - though it was possible to tweak and customize my configuration files to get all the little bells and whistles functioning properly, it wasn't that way "out-of-the-box".  Now, with 8.04, and 8.10, Ubuntu on my laptop feels as though it's made specifically **for** this equipment. - Better than the OEM OS that came with the computer.[/QUOTE]

Yes, open source developers work very hard to deal with issues, especially issues on commonly used hardware. They probably work longer hours than most paid developers would for a large corporation and very few of the Debian developers (who we have to acknowledge as the source of much of what we enjoy in Ubuntu) are paid for their developing. It's a totally different world than one based on profit and proprietary secrets.

It's actually not surprising that some culture of elitism could develop but it's not as apparent as in the past and I agree with scorp123 that in the past a flame suit was often needed. That was true even before IRC, newsgroups were often filled with very intelligent geeks who did not suffer fools gladly. The thing is, if one could take the heat, one could learn from people who knew and the important thing was gaining the knowledge, not how nice one was treated. A few people were driven away but the ones who stayed were forced to push themselves to new heights. I believe most teachers like working with the motivated student who does their 'homework'. Today there is some backlash, and forums often promote being nice over 'kicking someone in the *ss to get them started'. It's a better way to attract market share for those who value that and it really doesn't hurt those who don't. Noobie to expert ratio is definitely affected though.

Mostly users just want it to work when they click. They are the ones who need help. Users who dig into their systems and track down and fix or work around issues are always going to be in the minority, Ubuntu is doing a good job serving that need of the regular user, not perfect yet, but working on it. Don't lose sight of the fact that we mostly see people who need help here, there is a huge base of people for whom Ubuntu 'works right out of the box' and who don't upgrade just because something newer is available.

---

### Post by scorp123 on 2008-12-04
> **gTinker said:**
>  newsgroups were often filled with very intelligent geeks who did not suffer fools gladly. The thing is, if one could take the heat, one could learn from people who knew and the important thing was gaining the knowledge, not how nice one was treated. A few people were driven away but the ones who stayed were forced to push themselves to new heights.  Exactly. And ultimately it paid off if you persisted, regardless of how you were treated. All it took was a slightly thicker skin and a certain stubborness. The stuff you could learn from all those uber-geeks was well worth taking a bath in flames :D

---

### Post by utnubuuser on 2008-12-04
Wow!

> Some people regard Linux as being "hard" because it's different. Linux is not Windows. Therefore it must be "hard" because it does things differently. Unfortunately there are too many people out there who have this IMHO downright silly mindset ... and then they try out Linux and they are bound to be disappointed. So to them anyone mastering Linux just even a slight bit is "elite" or "elitist".

Back in the days where you'd need to manually download source code and manually patch and compile every and each of your binaries and write each config file line by line yourself ... yes, maybe it was "elitist" back then. But was DOS back then so different? I don't think so.


Hey just to be clear, I never meant to imply that Linux had an elitist culture, only that I wondered if that was part of the *the general public-perception*.  
- Based on my experience with the Gnu/Linux community, it's anything but elitist.
You may have noticed that I stated "An anti-stigma", by which I was trying to suggest that maybe a portion of the public's perception was, or is, that Gnu/Linux is something uber-geeks can use and understand, but not the average yokel. (which is mostly complimentary to uber-geeks).  Again, regardless of whether or not such feelings have merit.

> So yes, there might be hardware issues with certain types of hardware. But it's usually with vendors who "don't play nice". As (prospective) Linux user you're unlikely to run into hardware issues if you use Google and do some minimum research before buying hardware. Shouldn't be too hard.
This point about vendors "not playing nice" Gnu/Linux users are very well aware of, but it's not exactly common knowledge amongst non-free software user/buyers.

> there is a huge base of people for whom Ubuntu 'works right out of the box' and who don't upgrade just because something newer is available.
I'll count myself in here. Ubuntu has done very well by my hardware (or vice-versa), and though I'm now starting to move up to 8.04 and 8.10, I'm one of the ones who's wishing Feisty was an LTS.  That release is just dynamite on my gear.
But to reiterate, I'm mostly looking for the reasons behind what I consider to be un-founded and ill-conceived deragatory statements about Linux operating systems.
I'll give you an example: A Sidux review by Susan Linton on Linux.com ([http://www.linux.com/feature/149400]("http://www.linux.com/feature/149400")) (second last pargraph)
> Hardware compatibility isn't the issue it once was in Linux. Most common hardware is automatically detected and configured for users these days, and I found this to be true with Sidux.
Now I think she was trying to point out that "hardware is automatically detected and configured for users these days", but instead raises a red flag by saying  "Hardware compatibility isn't the issue it once was in Linux".  - The effect of this, intentional or otherwise, is to cast doubt and fear. 
 To you and me who already know that hey you **might** have to  install a wifi driver, or that Lexmark printer might not "play nice" is no big deal, but to someone who's never used Linux, it makes all the difference.
Those kinds of statements are enough for turn away any prospective new user who doesn't consider her/himself proficient with computers, and reinforces misguided views.
And really, I was only trying to find out if there was any basis to them.
I've gotten a much more precise account of where that line of thinking originates, (thanks to the responses), and though I suspected that any real "hardware issues" are something foisted on the kernel by vendors who, as has been stated, "don't play nice", there is also an aspect to these "issues" which psychologists call "transferral", where a problem I might be having, I'm likely to accuse you of having, if you follow.

Anyways, thanks for the awesome responses, - you've more than answered my question.
I'm going to keeping this thread as unsolved for now, if that's ok, because I think the answers you've given might be very worthwhile reading for other forum members.

Thanks again.

TSCHÜSS

---

