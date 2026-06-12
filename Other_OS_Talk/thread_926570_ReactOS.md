---
title: "ReactOS"
date: 2008-09-22
forum: Other OS Talk
---

### Post by dodle on 2008-09-22
I'm not sure if this OS complies with the Other OS Talk forum, but I was curios what people thought about it.  I've been following it a little bit, and maybe considering contributing to it.  Does it seem like something worth putting time into, or will this thing be virtually diminished in a couple of years?  Again, I'm just wondering what people think of it.

---

### Post by chungy on 2008-09-22
Well, ReactOS is trying to do to Windows what GNU did to proprietary UNIX.  It's certainly a noble goal, and something that I think is quite worthy.

I used to follow the project closely a few years back, they never ceased to make new progress every single month, it was quite fascinating.  Of course, their development has picked up since then (still fairly small, however), and you can probably expect a whole lot more than what I experienced years ago.

Windows NT is a large beast, and I think the largest problem in making an operating system based on its design, is the security aspect.  It stems from OS/2 and MS-DOS, it was designed as a single-user operating system, or AT MOST a file/print server sitting in a closet, with no outside world access to worry about.  Before Windows NT 4.0, security was a low-priority because its target audience did not need a high-security operating system.  Microsoft is still struggling to make it secure while remaining backwards compatible (and now they've announced that Windows (NT) 7 will be the very last version, ditching it for a better design), and well.... I probably don't need to tell you how little success they've had. 

ReactOS could probably implement something like a chroot, where a dumb legacy application would be fooled into thinking it has the entire filesystem at its command, and possibly registry too.  In reality, it should be confined to "C:\users\mike\dumbapplication\chroot".  All this is hypothetical thinking though... ReactOS is really trying to get an operating system compatible with Windows before trying to put security into the core (which is probably easier than doing a secure OS by design AND try to be compatible with Windows at the same time); they don't even have a multi-user system worked out yet.

Yes, it could definately use help, and I definately think it's a worthy goal.  The world needed to be freed from proprietary UNIX in the early 80s (which was solved by GNU and BSD), just as much as it needs to be freed from proprietary Windows today.

---

### Post by worx101 on 2008-09-22
My honest opinion is that it will disappear in a couple of years.

It has been around awhile though, even so i think it might be an overly ambitious project as their progress is too slow for window's release cycle. 

Would rather use wine.

Just my opinion.

---

### Post by Greyed on 2008-09-22
> **chungy said:**
> ReactOS could probably implement something like a chroot, where a dumb legacy application would be fooled into thinking it has the entire filesystem at its command, and possibly registry too.  In reality, it should be confined to "C:\users\mike\dumbapplication\chroot".

*snippage*

> The world needed to be freed from proprietary UNIX in the early 80s (which was solved by GNU and BSD), just as much as it needs to be freed from proprietary Windows today.

True.  But you realize that what you describe in the first quoted paragraph has been addressed by the very force mention in the second quoted paragraph.  On my system my dumb_legacy_app lives in...

~/.wine/C/Program Files/Dumb Legacy App/

The base OS is most often a mature, security-conscious, multi-user OS.  I think their efforts would be better directed in getting WINE as far and as fast as possible than reinventing a wheel thrice over.

---

### Post by worx101 on 2008-09-22
> **Greyed said:**
> I think their efforts would be better directed in getting WINE as far and as fast as possible than reinventing a wheel thrice over.

My opinion exactly

---

### Post by chungy on 2008-09-22
> **Greyed said:**
> The base OS is most often a mature, security-conscious, multi-user OS.  I think their efforts would be better directed in getting WINE as far and as fast as possible than reinventing a wheel thrice over.

Wine and ReactOS don't cancel each other out, and their FAQs clearly explains the relationship (including how both projects are benefiting each other, instead of meaningless competition): [http://www.reactos.org/en/about_userfaq.html](http://www.reactos.org/en/about_userfaq.html)

It's fine you like Wine, I like it too.  I personally wouldn't ever run ReactOS as my main operating system, but I imagine some people would once it's ready.  Operating systems interest me a lot, and my personal preference isn't hindering me trying out other ones (hey, if you really want, you can compile ReactOS from comfy Ubuntu, seriously!).

---

### Post by Greyed on 2008-09-22
> **chungy said:**
> Wine and ReactOS don't cancel each other out, and their FAQs clearly explains the relationship (including how both projects are benefiting each other, instead of meaningless competition): [http://www.reactos.org/en/about_userfaq.html](http://www.reactos.org/en/about_userfaq.html)

The fact only states that ReactOS addresses Windows drivers whereas WINE doesn't.  Which is pretty much a "well, duh!" statement since drivers = hardware = purview of the kernel, not WINE.  Once you jump that hurdle you realize their claim that ReactOS has a greater chance of compatibility (in regards to hardware drivers) falls flat since Linux, according to many people with far more experience in that area than me, supports more hardware.  IE, if Linux supports it, WINE supports it.  Pushing on that edge to move the stragglers who publish their spec only for Windows and not Linux into doing just that would be far more productive in the long run than reinventing the wheel thrice over.

---

### Post by dodle on 2008-09-22
I'm wondering if it's going to be worth it to keep developing wine and ReactOS if Windows is going to drop NT.  Maybe I just don't understand how things work.  Will Windows OSes still be backward compatible?

---

### Post by Greyed on 2008-09-22
From what I have read, no.  Microsoft has been trying for ages now to drop backwards compatibility and Vista+1 is when they are going to try (again) to do that.  

On the other hand XP has support through to, what, 2014?

---

### Post by smoker on 2008-09-22
> Why don't you help the Wine project instead?  Actually we work very closely with the Wine project. Wine probably has a lot more in common with ReactOS than with Linux. The Wine project has the goal of implementing the entire windows API on top of WineServer. There are only a few WINE dlls that cannot be used in ReactOS. These are NTDLL, USER32, KERNEL32, GDI32, and ADVAPI. The rest of WINE's DLLs can be shared with ReactOS. We have several developers in both the WINE and ReactOS projects that work on cross-compatibility issues between the two projects. It is our view that Linux + Wine can never be a full replacement for Microsoft(R) Windows(R). ReactOS has the potential for a much higher degree of compatibility - especially for Microsoft(R) Windows(R) drivers - which WINE does not address.
[http://www.reactos.org/en/dev_faq.html](http://www.reactos.org/en/dev_faq.html)

whatever anyone thinks of reactos, i'm sure the devs are doing a great service to both projects. also, it is not always about the final goal. i'm sure it is a great educational project for the individuals working on it, so even if, in the long run, reactos doesn't come to much, the learning gained in the working of the project may benefit the wider community in the future. :-)

---

### Post by chungy on 2008-09-22
> **Greyed said:**
> Once you jump that hurdle you realize their claim that ReactOS has a greater chance of compatibility (in regards to hardware drivers) falls flat

And what about all the Windows software that expects full access to hardware?  Sure, it's hypothetically possible to emulate that scenario, but Wine doesn't support it and it's unlikely to at any time.  This even ties into special dongles that software sometimes require, and install a special driver in order to talk to it.  The Wine project has actually stated that the most that can ever be expected with drivers is support for USB device drivers within Wine (libusb allows you to control USB stuff entirely in user space), but that doesn't do a whole lot if you require serial or parallel ports, or SCSI ports, or anything else.

---

### Post by the_darkside_986 on 2008-09-22
Even when (and _if_) Windows NT and win32 subsystem compatibility is dropped in a Windows release, ReactOS will still be relevant because there will still be a huge number of Win32 apps needing a native environment to fully function. Sure, MS would probably have an older Windows version in an virtualized environment, but that doesn't always work, look at their MSDOS emulator--it can't run Elder Scrolls II 100% properly like FreeDOS or Windows 98 (and below) can.

Actually, I can't imagine why Microsoft would completely drop NT altogether, the Win32 subsystem and all its ugliness, perhaps, but not the full NT OS itself.

---

### Post by Greyed on 2008-09-22
> **chungy said:**
> And what about all the Windows software that expects full access to hardware?

By the time NT is dropped most of anyone who would be using such hypothetical hardware would have moved on to the later version of Windows (which ReactOS is not addressing) or hopefully, Linux or OSX will have gained enough popularity, moved to another OS which again ReactOS does not address.

---

### Post by Junkieman on 2008-09-23
Judging from experience, win32 apps will be around for quite a while still. Unfortunately. But ive been following ReactOS on and off, and must say i was very impressed when they pushed through the refactoring period. Its a great project. 

Go for it, i would if i could! :)

---

### Post by Bungo Pony on 2008-09-23
Compatibility is all that Windows has going for it. If MS were to garbage everything and start from scratch, it would make people think "Well, if I'm going to start fresh, why don't I try something different?" Microsoft have painted themselves into a corner. If they drop all backwards compatibility, they risk losing most of their existing customers. If they continue to support backwards compatibility, they limit their growth and their OS becomes more unstable.

ReactOS is their biggest enemy, moreso than Apple or Linux. If MS drops their backwards compatibility, people could start developing for ReactOS instead and keep the backward compatibility. If MS continues to support backwards compatibility, people could switch over to ReactOS and quit paying MS for their garbage OS.

---

### Post by dodle on 2008-09-24
Is there any python used in ReactOS?

---

### Post by Greyed on 2008-09-24
Highly doubtful since they're basically creating an OS from scratch.  That's generally the domain of C/ASM.

---

### Post by cmat on 2008-09-24
Microsoft is not going to drop NT or even Win32 support over one release. If they do they are going to bring the industry down with them. Not to mention Vista is a Frankenstein's monster of every other Windows version dating back to 3.11. I don't think Microsoft is committed to rewriting Windows from scratch let alone changing core features.

---

### Post by Greyed on 2008-09-24
> **cmat said:**
> Microsoft is not going to drop NT or even Win32 support over one release. 

[http://www.sitepoint.com/blogs/2008/04/08/microsoft-to-follow-apples-lead-on-backwards-compatibility/](http://www.sitepoint.com/blogs/2008/04/08/microsoft-to-follow-apples-lead-on-backwards-compatibility/)

---

### Post by cmay on 2008-09-25
my brother installed it on a virtual box. i have it on a older computer. i was trying to install some development tools like devcpp which is one program i sometimes miss in linux. but its too unstable. but however the stable version i hope that will come out of the next release will be great i think. it has the windows switcher and the package manager system from we know from linux and that i think is wonderful. something i really would have liked in windows xp back when i was using that. i think it is a project that may end up with succes in time since people like my brother that has lots of commercial games for windows will want it as replacement for the next line of microsoft products maybe. my brother will soon buy a asus eee pc with ubuntu in it and leave his stationary as gaming pc and unconnected to internet just to use for gaming. then use ubuntu for all other things .so i hope reactOS could soon be stable enough for those people who have a lot of commercial programs  to benefit from for free.

---

### Post by smartboyathome on 2008-09-25
ReactOS is going along great, especially if you try the QEMU or VMWare preloaded images. Still has a long way to go, but it has come so far already!

---

### Post by dodle on 2008-09-26
I installed it on VirtualBox, but it crashed.  Does it have a browser pre-loaded?

---

### Post by smartboyathome on 2008-09-26
> **dodle said:**
> I installed it on VirtualBox, but it crashed.  Does it have a browser pre-loaded?

No, you install Firefox via Download > Firefox.

---

### Post by cmat on 2008-09-26
> **smartboyathome said:**
> ReactOS is going along great, especially if you try the QEMU or VMWare preloaded images. Still has a long way to go, but it has come so far already!

I've done this, the whole ISO was less than 30MBs. Now that's light weight.

---

### Post by Thelasko on 2008-09-26
I tried it a few months back, and I tried it again yesterday.  Seeing it's based on Wine, I'm wondering if installing some MS software, similar to what Winetricks does, will help things.

So far, I installed the MSCoreFonts and I'm trying to figure out what to do next.  Perhaps the colorprofile or fontfix.  The thing that annoys me the most is that copy and paste don't appear to work.

---

### Post by dodle on 2008-09-26
I hope they do something with the file manager.  That thing drives me crazy.

---

### Post by Thelasko on 2008-09-26
> **dodle said:**
> I hope they do something with the file manager.  That thing drives me crazy.
I loaded up [this guy]("http://sourceforge.net/projects/xenon-portable/") and it's much better.  There is still something fundamentally wrong with the way the OS renders.

---

### Post by lisati on 2008-09-28
> **dodle said:**
> I installed it on VirtualBox, but it crashed.

Hmmm, might give that a try (since it doesn't recognize the SATA drive in my laptop)

---

### Post by lisati on 2008-09-28
> **lisati said:**
> Hmmm, might give that a try (since it doesn't recognize the SATA drive in my laptop)

Gave it a try in a virtualbox - it crashed with a BSOD after failing to install a driver for a "mass storage media" (perhaps the SATA drive in the machine I normally use for Ubuntu) - according to the Reactos forums a driver for SATA drives is in testing.

Don't forget it's still Alpha.

---

### Post by RealG187 on 2008-09-28
This makes me really confused. So windows is a ripoff of NT? Which came first, NT or Windows?

And if Unix is proprietary, then wouldn't linux be infringing on it?

---

### Post by Le-Froid on 2008-09-28
> **RealG187 said:**
> This makes me really confused. So windows is a ripoff of NT? Which came first, NT or Windows?

And if Unix is proprietary, then wouldn't linux be infringing on it?

NT is from windows. Windows NT includes Windows NT 3.1, 3.5, 3.51, 4.0, Windows 2000, Windows XP, Windows Vista, and soon Windows 7.

ReactOS is trying to copy WinNT so you can run windows programs on a free operating system.

Also, UNIX is its own OS. Linux is *UNIX-like*, meaning it doesn't use any UNIX code but it functions a lot like UNIX does.

---

### Post by Thelasko on 2008-09-29
> **Thelasko said:**
> I loaded up [this guy]("http://sourceforge.net/projects/xenon-portable/") and it's much better.  There is still something fundamentally wrong with the way the OS renders.

Update on that.  It worked for a while, but eventually the regular file manager simply quit working.  If I tried to use it, it would BSOD on me.  I couldn't even save anything.

I finally decided to delete my ReactOS VM.  It still has a *LONG* way to go.

---

### Post by RealG187 on 2008-09-29
> **Le-Froid said:**
> NT is from windows. Windows NT includes Windows NT 3.1, 3.5, 3.51, 4.0, Windows 2000, Windows XP, Windows Vista, and soon Windows 7.

ReactOS is trying to copy WinNT so you can run windows programs on a free operating system.

Also, UNIX is its own OS. Linux is *UNIX-like*, meaning it doesn't use any UNIX code but it functions a lot like UNIX does.

Windows 95/98 aren't NT, but 3.1, 3.5(1), and 4.0, which are older, are? Who made NT and what is it? I always thought it meant "**N**e**t**work"...

Isn't Unix just a prompt, like Linux is (and there are Desktop Environments build around it)? Wouldn't DIS be "Unix Like"

What about Mac OS, does it use Unix code, or does it just function a lot like Unix too?

---

### Post by btmiller on 2008-09-29
> **RealG187 said:**
> Windows 95/98 aren't NT, but 3.1, 3.5(1), and 4.0, which are older, are? Who made NT and what is it? I always thought it meant "**N**e**t**work"...

Isn't Unix just a prompt, like Linux is (and there are Desktop Environments build around it)? Wouldn't DIS be "Unix Like"

What about Mac OS, does it use Unix code, or does it just function a lot like Unix too?

Microsoft made Windows NT. They hired Dave Cutler, who had designed VMS for Digital Equipment Corp. (DEC), to develop a brand new operating system from the ground up (this was the late '80s IIRC, after the partnership with IBM to create OS/2 was abandoned -- even then Microsoft saw the limits of what they could do with MS-DOS). As far as I know, NT was originally supposed to mean New Technology, but any more I don't think it stands for anything.

Unix is certainly not "just a prompt" -- it is (or was) a full-fledged operating system! The prompt is just the shell, e.g. bash, csh, etc. Unix was originally developed at Bell Labs in the 1960s and 1970s, but due to the antitrust agreement at the time Bell gave out the code to a number of institutions, including U. California Berkeley, from which BSD was born. A number of commercial companies got licenses from which sprang various proprietary Unices.

Linux was designed to work-like Unix (i.e. it aimed for compliance with the POSIX standard). Linux has never been officially certified as a Unix by the Open Group (which owns the Unix trademark) and as such is called a Unix-like system. The BSDs are similar. There is no original Unix code in Linux. Mac OS X is based largely from FreeBSD except it uses the Mach microkernel, from what I understand. The thing is, Apple actually paid the money to get Open Group certification for OS X 10.5, so OS X is officially a Unix.

---

### Post by Le-Froid on 2008-09-29
> **RealG187 said:**
> Windows 95/98 aren't NT, but 3.1, 3.5(1), and 4.0, which are older, are? Who made NT and what is it? I always thought it meant "**N**e**t**work"...

Isn't Unix just a prompt, like Linux is (and there are Desktop Environments build around it)? Wouldn't DIS be "Unix Like"

What about Mac OS, does it use Unix code, or does it just function a lot like Unix too?

1 - Windows 95 / 98 were versions of MS-DOS, just with an added GUI to it. (The last MS-DOS product was Windows ME)

2 - NT is just one of Microsoft's products. MS chose to name it Windows NT because they could use it to represent "New Technology" and to pun VMS, by incrementing each letter by 1 (VMS->WNT).

3 - UNIX and Linux with no GUI are basically prompts like you see in a terminal (although they function the same as they would with a GUI). A GUI is just an extension to the OS. Anything that works close to the way UNIX does is considered "UNIX-like"

4 - Mac OS X is under the same OS family as UNIX - Apple payed a lot of money for OS X to become "UNIX certified". It is based off of a Darwin core ( Darwin is a form of BSD ). They do release parts of their OS on their website - anything they made thats entirely theirs they keep closed source.

edit: @above - Linux was built originally to be Minix-like, but as development progressed they became more and more like UNIX. Also OS X is based from Darwin - not FreeBSD

---

### Post by btmiller on 2008-09-29
> **Le-Froid said:**
> 
edit: @above - Linux was built originally to be Minix-like, but as development progressed they became more and more like UNIX. Also OS X is based from Darwin - not FreeBSD

Linus Torvalds used Minix to build Linux, but the OSes were not very similar. Minix is a microkernel whereas Linux uses a monolithic kernel (later extensible with modules). Linus used Minix because it was a convenient development platform, but there is little influence from Minix on the design of Linux (look up the Tanenbaum-Torvalds debate for more information about the disagreement between Linus and Andy Tanenbaum [creator of Minix]) about how an OS should be structured).

And Darwin incorporates code from various other Unix projects, including FreeBSD (see [the Wikipedia entry]("http://en.wikipedia.org/wiki/Darwin_(operating_system)")). One thing I forgot was the connection with NEXTSTEP (a proprietary Unix). Steve Jobs went to foiund NeXT after he was fired from Apple and NEXTSTEP was their Unix.

---

### Post by Thelasko on 2008-09-30
> **Le-Froid said:**
> 1 - Windows 95 / 98 were versions of MS-DOS, just with an added GUI to it. (The last MS-DOS product was Windows ME)

Partially correct, versions prior to Windows 95 was just a GUI on top of DOS (3.11, etc.).  Windows 95-ME was actually integrated with DOS.  Basically this meant that DOS was designed around Windows instead of the other way around.  The most notable difference was that you could no longer exit Windows and work in DOS after Windows 95.  Closing Windows meant you had to completely reboot the computer because the two were extremely dependent on each other.  Once you rebooted you could enter MS-DOS "mode".

Although the 9x family was based on DOS, I don't think "MS-DOS, just with an added GUI to it" is accurate.

---

### Post by RealG187 on 2008-09-30
SO anything under Mac OS X 10.5 is not unix cerified. And OS X 10.5 is only unix certified because Apple paid them?

How could Steve jobs get fired from Apple when he owns it?

How come the people who own Unix call them selves the "Open group" when Unix is proprietary?

Can I see a screenshot of Unix?

---

### Post by zmjjmz on 2008-09-30
> **RealG187 said:**
> SO anything under Mac OS X 10.5 is not unix cerified. And OS X 10.5 is only unix certified because Apple paid them?

How could Steve jobs get fired from Apple when he owns it?

How come the people who own Unix call them selves the "Open group" when Unix is proprietary?

Can I see a screenshot of Unix?

1. Yep. This is probably another reason why Linux isn't UNIX certified. It means basically nothing, and it's mostly about trademarks.
On the other hand, what's more important is POSIX compliance, which Linux has.
2. Because he doesn't own it. It's a publicly traded company, and the shareholders thought he was an ******* and kicked him out.
3. Marketing?
4. Uh, sure? Not much to see, probably just a prompt. Of course, an OS is more than its screenshot.

---

### Post by lisati on 2008-09-30
> **RealG187 said:**
> Windows 95/98 aren't NT, but 3.1, 3.5(1), and 4.0, which are older, are? Who made NT and what is it? I always thought it meant "**N**e**t**work"...

Isn't Unix just a prompt, like Linux is (and there are Desktop Environments build around it)? Wouldn't DIS be "Unix Like"

What about Mac OS, does it use Unix code, or does it just function a lot like Unix too?

> **Thelasko said:**
> Partially correct, versions prior to Windows 95 was just a GUI on top of DOS (3.11, etc.).  Windows 95-ME was actually integrated with DOS.  Basically this meant that DOS was designed around Windows instead of the other way around.  The most notable difference was that you could no longer exit Windows and work in DOS after Windows 95.  Closing Windows meant you had to completely reboot the computer because the two were extremely dependent on each other.  Once you rebooted you could enter MS-DOS "mode".

Although the 9x family was based on DOS, I don't think "MS-DOS, just with an added GUI to it" is accurate.

... which goes some way towards explaining why a 16-bit "rough and ready system cleanup tool" I threw together under 98SE correctly distinguished between running from MS-DOS mode or in a DOS box under windows (thus being able to initiate a 32-bit GUI-based equiavalent) but couldn't do so when I moved to XP.

(apologies to anyone who might want the source.....it's long disappeared in the midst of the run of muck-ups that make for a great learning experience)

---

### Post by chungy on 2008-10-01
> **Thelasko said:**
> Partially correct, versions prior to Windows 95 was just a GUI on top of DOS (3.11, etc.).  Windows 95-ME was actually integrated with DOS.  Basically this meant that DOS was designed around Windows instead of the other way around.  The most notable difference was that you could no longer exit Windows and work in DOS after Windows 95.  Closing Windows meant you had to completely reboot the computer because the two were extremely dependent on each other.  Once you rebooted you could enter MS-DOS "mode".

Although the 9x family was based on DOS, I don't think "MS-DOS, just with an added GUI to it" is accurate.

Actually, Windows 95 and 98 both had an "Exit to DOS" option right under Start->Shut Down.  Windows Me hid the ability to exit to DOS, but there is a workaround for that: [http://www.geocities.com/mfd4life_2000/](http://www.geocities.com/mfd4life_2000/)

Windows 9x/Me took more control of hardware than Win1.x-3.x did, though hard disk control and filesystem support was still the role of MS-DOS... our opinions obviously differ, but I still think Windows 95/98/Me are basically GUI additions for MS-DOS.

---

### Post by Junkieman on 2008-10-01
> **RealG187 said:**
> Can I see a screenshot of Unix?

not to change topic, but to put it all into perspective...

how about a [mind map of distributions]("http://linuxhelp.blogspot.com/2006/04/mind-map-of-linux-distributions.html"), or if you prefer a [timeline of distributions]("http://futurist.se/gldt/") :)

---

### Post by Thelasko on 2008-10-01
> **chungy said:**
> Actually, Windows 95 and 98 both had an "Exit to DOS" option right under Start->Shut Down.  Windows Me hid the ability to exit to DOS, but there is a workaround for that: [http://www.geocities.com/mfd4life_2000/](http://www.geocities.com/mfd4life_2000/)
It wasn't "Exit to DOS" it was "Restart in MS-DOS mode"  [From Wikipedia:]("http://en.wikipedia.org/wiki/Windows_9x#Overview")
> When Windows 95 started up, MS-DOS was loaded, processed CONFIG.SYS file, launched COMMAND.COM, and ran AUTOEXEC.BAT and finally ran WIN.COM. The WIN.COM program used MS-DOS to load the virtual machine manager, read SYSTEM.INI, load the virtual device drivers, and then turn off any running copies of EMM386 and switch into protected mode. Once in protected mode, the virtual device drivers (VxDs) transferred all state information from MS-DOS to the 32-bit file system manager, and then shut off MS-DOS. These VxDs allow Windows 9x to interact with hardware resources directly, as providing low-level functionalities such as 32-bit disk access and memory management. All future file system operations would get routed to the 32-bit file system manager.[
DOS was just a bootstrapper.  Although the 9x family contained some elements of DOS, it was a separate operating system.  Because DOS was still on the system, you could reboot into it.

---

### Post by Eisenwinter on 2008-10-26
I have installed ReactOS 0.3.6 alpha on a virtual machine.

It works pretty well, but has some display glitches, even within the "native" programs which came with the OS itself.

But I have to say, overall it works well, it only took about 45 minutes until it crashed ;)

---

