---
title: "Cross compiling for mac os x on linux"
date: 2008-06-23
forum: Programming Talk
---

### Post by publicv on 2008-06-23
Hi,
I have a c program I'd like to compile for mac os x.  Sadly I don't have a mac, but a mac user have told me that my program compiles without a problem on his mac.

I've been cross compiling for windows using mingw, but there seems to be no such package for mac os x as well, and nothing I've found on the web was very helpful thus far.

Can anyone here guide me to an easy to follow tutorial/howto?

---

### Post by publicv on 2008-06-24
In case anyone else comes across the same problem, a possible solution is available here:

[http://www.sandroid.org/imcross/](http://www.sandroid.org/imcross/)

---

### Post by WitchCraft on 2009-03-05
> **publicv said:**
> In case anyone else comes across the same problem, a possible solution is available here:

[http://www.sandroid.org/imcross/](http://www.sandroid.org/imcross/)


wow, excellent. /thanked

---

### Post by publicv on 2009-03-05
It's actually not that great at all, it's quite cumbersome.

Additionally, there is no way to actually test it without a mac since there is nothing equivalent to wine for mac os x, and surprisingly enough my fairly portable c program was actually performing differently on a mac than on linux.

I have decided to simply forgo mac support and only provide builds for linux&windows.

It really seems almost as if Apple is actively trying to dissuade people from porting software to mac os x.

---

### Post by uljanow on 2009-03-06
Too bad that vmware images of Mac OS X which are available on the web are not legal.;)

---

### Post by jackmcslay on 2009-03-06
> **publicv said:**
> (...)

I have decided to simply forgo mac support and only provide builds for linux&windows.

It really seems almost as if Apple is actively trying to dissuade people from porting software to mac os x.it's quite understandable there is no wine equivalent for Mac OS (what are you going to run? GarageBand?). 
The best choices are 
a) use platform-independent languages
b) ensure your software runs perfectly on Wine, without needing additional DLLs
c) this:
> **uljanow said:**
> Too bad that vmware images of Mac OS X which are available on the web are not legal.;)

---

### Post by WitchCraft on 2009-03-12
> **publicv said:**
> It's actually not that great at all, it's quite cumbersome.

Additionally, there is no way to actually test it without a mac since there is nothing equivalent to wine for mac os x, and surprisingly enough my fairly portable c program was actually performing differently on a mac than on linux.

I have decided to simply forgo mac support and only provide builds for linux&windows.

It really seems almost as if Apple is actively trying to dissuade people from porting software to mac os x.

Well, they are not trying to dissuade you from porting software to the Mac, they are simply trying to force you to buy a Mac and pay double the amount of money which you would compared to buying a Dell PC/Notebook at the same performance level.

But YES, their policy has exactly this effect, and it's at the same time the reason why Apple failed in the past, and it also is the reason why Apple will fail in the future.

However, there is OSx86, which is a hack for MacOS X to run on Intel PCs.
That project has a legality as well as a network and graphics card driver problem, but else, it's the solution to your problem. If you do it to develop & test Software, I for my part call this 'fair use'.

Also, starting on Leopard, programs developped for Apple undergo a CODESIGNING process...

---

### Post by del_diablo on 2009-06-30
> **WitchCraft said:**
> Well, they are not trying to dissuade you from porting software to the Mac, they are simply trying to force you to buy a Mac and pay double the amount of money which you would compared to buying a Dell PC/Notebook at the same performance level.

The shame is that the competitors notebooks are inferior hardware wise, they do not deliver. Consider the battery time and display, along with the weigth and material. They do not get you that, Apple does however.
Software wise: If you buy a Mac, you get OS upgrades for the 3 first years along with quite the amount of decent software on in the package.

---

### Post by jinksys on 2009-06-30
> **WitchCraft said:**
> Well, they are not trying to dissuade you from porting software to the Mac, they are simply trying to force you to buy a Mac and pay double the amount of money which you would compared to buying a Dell PC/Notebook at the same performance level.
Are you from the past?  Today you can pick up a 13" Macbook Pro for $1199, sure there are cheaper 13" laptops, but show me one with a glass multi-touch pad, sensor-driven illuminated keyboard, alluminum unibody enclosure, and OSX (or Windows even) for a lower price.  There are always going to be cheaper laptops, cars, and homes, but is the cheapest always the best? edit: (Don't forget the 7 hour battery life)

> 
Also, starting on Leopard, programs developped for Apple undergo a CODESIGNING process...

Starting with Leopard, all of APPLE'S software (GarageBand, iTunes, etc) are signed.  Codesigning of third party software is OPTIONAL and at the discretion of the developer. 

---
To the OP:  I develop for the mac (and unix in general) exclusively, if you need someone to compile a build, or help maintain a mac build, I wouldn't mind helping your project.

---

### Post by soltanis on 2009-06-30
At the expense of breaking up this Mac vs. Anti-Mac argument, if your application compiles for the Mac and Mac users really want to use it, you should bring someone on board who has a Mac to build/maintain packages for your software for Macs.

Or at the very least ask the guy who compiled it to submit the binary so that something can be available.

---

### Post by jinksys on 2009-06-30
> **soltanis said:**
> 
Or at the very least ask the guy who compiled it to submit the binary so that something can be available.

Mac apps generally come in Bundles, and it's important to distribute your app and its resources in a properly formatted and structured bundle so that OS X can properly assess what your app can/can't do.  For non-gui apps, bundles aren't normally used since they are essentially folders on the command line.

---

### Post by WitchCraft on 2009-07-08
> **jinksys said:**
> 

Starting with Leopard, all of APPLE'S software (GarageBand, iTunes, etc) are signed.  Codesigning of third party software is OPTIONAL and at the discretion of the developer. 


BUT, not having your application signed won't be good, because you'll have problems whenever you access a device driver directly, or your application otherwise requires root privileges.

Of course, you're never going to realize this as long as you only develop on your computer, but as soon as you deploy your application, you'll start receiving complaints over the application not working...

And, well 7 hours battery life and an illuminated keyboard as well as less weight and 3 years free updates may be what you want, but I want a cheap laptop with much RAM & a fast processor, and at least 3+ USB ports.

And I need a decent screen, that is to say exactly 15", not less, and not more.
(Since I need to see what I type, but don't want to buy a larger rucksack)

Everything else is (although nice to have) redundant, and just adding to the price, and nothing to my needs.

I also want as few updates as possible (but as many as necessary), and certainly not 3 years every day.
Besides, Windows/Linux updates are always free, and not just 3 years long, so I fail to see the point in this argument (only 3 years? Actually that's an argument against - but never mind so much logic)...

I want a secure operating system - that is to say certainly not Mac OS X, and Vista/XP neither.

I want the system to follow established standards ("Big Blue" IBM instead of Mac, little USB plugs instead of huge  FireWire crap, compatible hardware from every vendor, not just Apple), and at the very least device drivers for Linux and Windows.

---

### Post by jinksys on 2009-07-08
> **WitchCraft said:**
> BUT, not having your application signed won't be good, because you'll have problems whenever you access a device driver directly, or your application otherwise requires root privileges.

Of course, you're never going to realize this as long as you only develop on your computer, but as soon as you deploy your application, you'll start receiving complaints over the application not working...


Great googly-moogly.  First off, this is 100% false.  I don't know where you get your information, but I suggest you stop referencing it.  If an application needs to gain root access, (or any level of access that the user can provide credentials for), the application simply asks for permission from the Security Server Daemon.  This is done with a simple AuthorizationCreate call.  If the Server Daemon requires a password, it will prompt the user for one in a standard dialog box.  This happens routinely when a user installs a software package or wants to change a system setting that has been locked.  It's simple stuff.  Take a look for yourself. 
[Authorization Services.]("http://developer.apple.com/documentation/Security/Conceptual/authorization_concepts/01introduction/introduction.html#//apple_ref/doc/uid/TP30000995-CH204-TP1")

> 
I want the system to follow established standards (IBM instead of Mac, little USB plugs instead of big FireWire crap, compatible hardware from every vendor, not just Apple).

I am typing this on a 13" Macbook that is connected to a MICROSOFT mouse via USB, 
that prints to a Dell (lexmark) laser printer via USB, 
that syncs and interfaces with my LG enV phone using Bluetooth,
that puts apps on my Texas Instruments graphing calculator over USB,
has a built in SD card reader, 
takes input from my Digitech guitar pedal over USB, 
talks to my Roomba via bluetooth, 
and surfs the internet over 802.11G wifi.  

So, who's standards are we ignoring again?

):P

---

### Post by WitchCraft on 2009-07-11
> **jinksys said:**
> Great googly-moogly.  First off, this is 100% false.  I don't know where you get your information, but I suggest you stop referencing it.  If an application needs to gain root access, (or any level of access that the user can provide credentials for), the application simply asks for permission from the Security Server Daemon.  This is done with a simple AuthorizationCreate call.  If the Server Daemon requires a password, it will prompt the user for one in a standard dialog box.  This happens routinely when a user installs a software package or wants to change a system setting that has been locked.  It's simple stuff.  Take a look for yourself. 
[Authorization Services.]("http://developer.apple.com/documentation/Security/Conceptual/authorization_concepts/01introduction/introduction.html#//apple_ref/doc/uid/TP30000995-CH204-TP1")



I am typing this on a 13" Macbook that is connected to a MICROSOFT mouse via USB, 
that prints to a Dell (lexmark) laser printer via USB, 
that syncs and interfaces with my LG enV phone using Bluetooth,
that puts apps on my Texas Instruments graphing calculator over USB,
has a built in SD card reader, 
takes input from my Digitech guitar pedal over USB, 
talks to my Roomba via bluetooth, 
and surfs the internet over 802.11G wifi.  

So, who's standards are we ignoring again?

):P

Wow, yea I know Microsoft mouses work on BSD Unix (actually, does the mouswheel work now?), but try a GDI printer or the Casio Classpad 300 Calculator (which is better than TI, but less standard) or a Kodak digital camera or or or...

Or try to access the proc filesystem. Or try an application that depends on GDB on Leopard. Or try an application that depends on a flawless g++ compiler, or try an application that needs the ptrace interface (anti digital rights missmanagement software), or try to run Macros in Microsoft Office, etc, etc., etc....

---

### Post by Lothar Behrens on 2012-06-24
Is there actually any one doing actively cross compile?

It's not because I didn't have a mac, I have two - a mac Mini (PPC) with Leopard and a  MacBook with Snow Leopard :-)

I need to automate the build in a CI environment (Hudson). If I can cross compile, I only need one build server doing the stuff (Mac, Win, Linux and Solaris are my targets). It would me save much manual work if I am able to get as much binaries as I can get from one build server.

All that should run in a virtual machine. This virtual maching also then would be my developer box where I could test before checkin.

Thanks, Lothar

---

### Post by LordDelta on 2013-05-13
Bump (not sure what the thread necromancy rules are on the forum, but)

Btw, I found this here:

[http://www.nathancoulson.com/proj_cross.php#x86_64-apple-darwin10](http://www.nathancoulson.com/proj_cross.php#x86_64-apple-darwin10)

Not sure if this went very far though.

Personally I don't have much of a use for one and don't care too much either way, however I don't have direct access to my Mac targets, and it would just be nice to be able to target them in something other than HTML5.

Could clang achieve this? Call me diehard, I prefer gcc but it looks like the llvm might be able to work a related brand of magic to that of Java:

[http://wiki.osdev.org/LLVM_Cross-Compiler](http://wiki.osdev.org/LLVM_Cross-Compiler)

Also (don't laugh, I've seen/heard people consider weirder):

[http://docwiki.embarcadero.com/RADStudio/XE2/en/BCCOSX,_the_C%2B%2B_Cross_Compiler_for_OS_X](http://docwiki.embarcadero.com/RADStudio/XE2/en/BCCOSX,_the_C%2B%2B_Cross_Compiler_for_OS_X)

Though you'd have to run wine to get this working on a linux box <_< >_>.

Anyone have experience with any of these? The first sounds long and tedious, I'd rather it just existed in a package (which it doesn't seem to) =/

---

