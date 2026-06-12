---
title: "A few things that work better in Windows"
date: 2010-01-07
forum: Recurring Discussions
---

### Post by Bartender on 2010-01-07
Don't get me wrong, I've been an Ubuntu fan since Breezy, and finally running 9.04 as our default OS on the main PC (we're on dial-up so that explains a lot of things), but I wanted to comment on a few things that I either can't do in Linux at all or they don't work as well.  This is not an indictment of Linux by any means, just a brief note to suggest that having one copy of Windows available to you is not a bad idea.

#1.  Downloaded an employment application.  It was a Word file, with the little interactive windows so that you can enter your data and print it.  I started Ubuntu 9.04, then tried using OpenOffice to fill it out.  OO couldn't do it.  Couldn't even display the document clearly.  It was a mess of lines and boxes.
The original file was on a thumbdrive.  I re-booted the PC and went into XP.  Within XP I was able to use OpenOffice to fill out the application without any trouble.  I would have expected OO to work as well or better in Linux than Windows!  Perhaps the Windows version is newer and that explains the difference...

#2.  I wanted to update my wife's Sansa Fuze.  Of course Sansa's updater application only works in Windows.

#3.  I've been ripping some DVD's and audiobooks (using Ubuntu, Handbrake, and RubyRipper) to a 1TB Seagate HDD plugged into a Vantec dock.  The HDD is formatted in NTFS because I want interoperability.  I decided one day to check fragmentation and it was a mess.  Used XP to defrag.  As far as I know there is no defrag app in Linux.  Probably because defragmentation isn't really an issue with Linux file systems.

#4.  .pdf editing.  I bought a copy of the Foxit upgrade that allows you to edit .pdf's.  Much cheaper than the full Adobe program.  Of course, the Foxit upgrade is a Windows app so I gotta go there to use it.  I've read posts describing Linux-based .pdf editors but all of them were primitive and unusable.  One of them refused to recognise Shift + J key so I couldn't make a capital "J"!  I tried a different keyboard, same problem.

#5.  Dial-up.  No more needs to be said ;)

That's all I can think of right now.  To be fair, Ubuntu does things that Windows won't, so as I said this is not Linux-bashing.  What tasks have you found that are either much harder or impossible in Ubuntu?

---

### Post by fancypiper on 2010-01-07
> **Bartender said:**
> #3.  I've been ripping some DVD's and audiobooks (using Ubuntu, Handbrake, and RubyRipper) to a 1TB Seagate HDD plugged into a Vantec dock.  The HDD is formatted in NTFS because I want interoperability.  I decided one day to check fragmentation and it was a mess.  Used XP to defrag.  As far as I know there is no defrag app in Linux.  Probably because defragmentation isn't really an issue with Linux file systems.
NTFS defrag is on the way and it should be available in ntfsprogs.

[http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

---

### Post by Bartender on 2010-01-07
Thanks for the info!  That would be great to strike one item off the list :)

---

### Post by Objekt on 2010-01-07
People still use dialup?

The thread starter is not wrong, but since I learned how to run a virtual Windows XP machine via Virtualbox, I have had almost no need to boot my actual Windows XP install.  I even have my Windows-only printer hosted on the virtual XP machine, and shared with the Windows machines on my home network.

One thing I can't do on a virtualized Windows XP machine is play Windows-only games.  One is Oblivion.  Its graphics demands simply cannot be done in virtualization, and it doesn't work quite right in WINE, so when I want to play I have to reboot into Windows XP.

NTFS volume maintenance is the other exception, as the thread originator notes.  Occasionally I will neglect to properly unmount an NTFS volume when running Windows.  Ubuntu wisely refuses access to an improperly-closed NTFS volume, so I must reboot into Win XP to do a chkdsk /f.

I haven't encountered the author's problems with documents in OO, but perhaps it's because I rarely ever work with Microsoft Office-generated documents.  It is probable that the document would be identically accessible in both Windows and Linux, given the latest version of OpenOffice.

---

### Post by SecretCode on 2010-01-07
> **Objekt said:**
> People still use dialup?

People still use dialup in Africa ... but in the US? :o I'm astonished. (OK, maybe not; America's big and there are lots of rural areas. Bartender, can you get broadband in your area at all?)

> **Bartender said:**
> #5.  Dial-up.  No more needs to be said ;)
What's better for dialup in Windows?

---

### Post by Zoot7 on 2010-01-07
Ubuntu (or whatever distro) is all very well and good and there's advantages tenfold in using it over Windows, but there are just some things that you need Windows for, like it or lump it.
In my case it's Games, Home Recording, and some Engineering applications that are Windows only.

---

### Post by meho_r on 2010-01-07
I do everything better on Linux than on Windows, except gaming :)

#1 Strange. May be a version issue.

#2 Just a reminder that when buying a device, you should check if Linux is supported.

#3 Well, ntfs isn't a Linux filesystem, so it shouldn't be a surprise that there is no defrag for it. If you want portability and use ntfs, then simply defrag it from the other computer which has Windows on it.

#4 There are still no good pdf editors for Linux, but many work fine with wine (e.g. [Infix PDF Editor](http://www.iceni.com/infix.htm); you should try Foxit, it may work /Foxit viewer does/). But, on the other hand, you should know that pdfs aren't meant to be edited...

#5 Shipit.

---

### Post by fancypiper on 2010-01-07
> **SecretCode said:**
> What's better for dialup in Windows?Support for non-modems (winmodems), I would wager.  My first hoop jump to Linux, I had to spend $14 for a real modem.  Much less than the Microsoft license, though, so Linux still rules when cost of ownership is considered.

---

### Post by cariboo on 2010-01-07
If your modem is supported, it takes very little time to set them up. [This]("help.ubuntu.com/community/DialupModemHowto") helped me, when I set up a fax server a couple of months ago.

---

### Post by Methuselah on 2010-01-07
> **fancypiper said:**
> Support for non-modems (winmodems), I would wager.  My first hoop jump to Linux, I had to spend $14 for a real modem.  Much less than the Microsoft license, though, so Linux still rules when cost of ownership is considered.

Could you recommend one/some fancypiper?
I was thinking of getting one for fax.

---

### Post by Bartender on 2010-01-07
I was afraid my message would be misinterpreted.  I'm not bitching about Linux!  

But I always cringe when a newb comes on, and people say, go for it, you'll never look back, etc.

I'm trying to be zen-like about the situation.  Like a leaf in the wind or whatever.  Accepting that I still need Windows for some things.

Regarding Secret Code's question about dial-up in Windows...first off, trying to get connected is a miserable experience, what with all those winmodems.  I have 3 or 4 USR externals and I'm not afraid to use them.  Do a search for "Bartender" and "dial-up" ;)

Then there's the issue of the huge downloads that Ubuntu sends out on a regular basis.  I cannot download 40+ MB updates on dial-up.  Not gonna happen.  For the most part, Windows security updates are annoying but manageable.  However, I recently discovered the Package Download Script in Synaptic, and that's been a lifesaver.  

As to dial-up in the U.S., there are several countries that have better coverage.  I live on a rural road, only about 4 miles from town and the Qwest switching station.  I talked to some Qwest employees recently.  They said it would cost Qwest over a half a million $ to run DSL up our road and they won't do it unless a lot more people move in.  I talked with a Comcast installer.  He said Comcast is less likely to come up the valley than Qwest.  From what I've seen and heard, satellite is over-priced, unreliable, and in some cases not much faster than dial-up.

---

### Post by fancypiper on 2010-01-07
I bought a serial port modem. Those should be real modems, just check the specs and avoid any that are winmodems.

I first got Linux on dial up (I am in the boonies and there is only one ISP that serves my area), don't all real geeks suffer through dial up? :D

For a long time, I wasn't reachable except through knocking at the door, the internet or snail mail.

---

### Post by Bartender on 2010-01-08
Have you moved on from dial-up?  Our main PC has a serial port, but I've used the old USR's successfully on PC's that didn't by using a Sabrent USB-to-serial cable.  Just had to change one setting - the modem was found at /tty/ACM0 instead of tty/S0 or S1.

I should have mentioned a post or two ago that Microsoft now has boxed me in.  Windows Update is insisting that I need to download the .net framework update (60+MB) before installing the routine XP security updates.  I suspect they're lying to me.  I haven't figured out a way to download the damned .net framework update to a thumbdrive so I'll probably just haul the whole danged rig over to a friend's house where I can borrow some broadband.

---

### Post by meho_r on 2010-01-08
You don't have to update everything on Ubuntu, and I'm not sure if security updates are that big (40+ MB). Just tick off any regular application updates and install only security related ones. But, even without any updates done you'll probably do fine (unlike on Windows where you have to do Windows security updates + regular AV updates + Antispyware updates etc.).

---

### Post by anaconda on 2010-01-08
#1. office 2007 works flawlessly in wine (well. word and  excel anyway)

#5. What is wrong with dialup? I use a dialup (3G-modem) connection and it works very well.

---

### Post by caravel on 2010-01-08
> **Bartender said:**
> #5.  Dial-up.  No more needs to be said ;)
Old fashioned 56K dial up works fine - you just need a proper external RS232 modem and not a winmodem (some winmodems do work as well though).

---

### Post by murderslastcrow on 2010-01-08
For the next few months, the iPod Touch, iPhone, and Nano 5G work won't be in official packages yet, so those are some iPods that won't work just yet. This is the biggest issue for my friends, really.

You do have to remember that there are so many more benefits to using Linux, even if not everything works just as it would in Windows (thank goodness it's not the same XD).

But one more thing I think deserves to be pointed out is that things work well for Windows because of the people who create iPods, Netflix, Office applications, etc. It's not because Microsoft put any effort at all into making these things work. It's the people who make the technology locking it into one OS due to thinking it really doesn't matter.

It also means that open source developers have put in a RIDICULOUS amount of work making drivers and compatibility for all of these formats, devices, databases, etc.

And really, if we're going to make an open source solution to getting drivers and stuff working anyway, why not just release a driver? When Linux gets a bit more official support in the coming years, I can see the focus going far more into improving the applications, rather than just trying to make things work all the time.

Then again, it's pretty awesome now. :3 It'll only get better, so you just have to look forward to the day that you might not need a VirtualBox for anything. I've finally reached that day and it's quite liberating.

---

### Post by Bartender on 2010-01-08
> **anaconda said:**
>  What is wrong with dialup? I use a dialup (3G-modem) connection and it works very well.

Let me ask you, what kind of speeds you get?  I've seen a cell-based modem clip right along with a good signal.  Traditional phone-line dial-up is not the same thing!

---

### Post by HappyFeet on 2010-01-08
> **anaconda said:**
> 
#5. What is wrong with dialup? I use a dialup (3G-modem) connection and it works very well.

3G modem is not traditional dial-up. Good luck trying to surf multimedia rich web sites with dial up. Back in the day, web sites were much simpler, and  dial up got the job done. Not so anymore.

---

### Post by hashimoto on 2010-01-09
> **Bartender said:**
> 
#2.  I wanted to update my wife's Sansa Fuze.  Of course Sansa's updater application only works in Windows.


I have a Sansa Fuze and it's firmware can be updated without windows by simply copying the new FW in the device and rebooting it. More here: 

[http://ubuntuforums.org/showthread.php?t=1370738](http://ubuntuforums.org/showthread.php?t=1370738)

---

### Post by Bartender on 2010-01-09
Thanks for the link!!

Since our main PC is a dual-boot I'll probably just stick with updating the Fuze via XP.  Simpler that way.  But will definitely print that out and keep it for future reference!

---

### Post by gabo.cr on 2010-01-09
That's why I keep Windows in VirtualBox "just in case".
But I don't really use it, I guess I'm lucky.
;)

---

### Post by running_rabbit07 on 2010-01-09
> **Bartender said:**
> As to dial-up in the U.S., there are several countries that have better coverage.  I live on a rural road, only about 4 miles from town and the Qwest switching station.  I talked to some Qwest employees recently.  They said it would cost Qwest over a half a million $ to run DSL up our road and they won't do it unless a lot more people move in.  I talked with a Comcast installer.  He said Comcast is less likely to come up the valley than Qwest.  From what I've seen and heard, satellite is over-priced, unreliable, and in some cases not much faster than dial-up.

Is mobile broadband an option?

---

### Post by juancarlospaco on 2010-01-09
OpenOffice can Edit PDF directly...
:)

---

### Post by Bartender on 2010-01-09
Not with the .pdf's on this part of the planet :)  

I've tried several times.  OpenOffice brings up a window asking about ASCII settings or something like that, then opens up a window full of gobbledy-gook.

I've checked on mobile broadband.  Verizon claims we're within their 3G network.  $60/month, with a 5GB/month cap.  I don't know how often I'd be bumping up against that 5GB cut-off.  

I'm unemployed right now.  Can't justify $60/month internet.

---

### Post by judge jankum on 2010-01-09
Welllllllllll let's see....my spouse says I pull my hair out better in Windows" Also I can cuss much louder (you know hit those higher notes) much better.....LOL!!!

---

### Post by running_rabbit07 on 2010-01-10
> **Bartender said:**
> I'm unemployed right now.  Can't justify $60/month internet.

I know your pain. Been unemployeed for a long time myself. If it weren't for the GIBill paying me for school, I'd have sunk a long time ago.

---

### Post by stalkingwolf on 2010-01-10
The last time I had to set up dialup was on an everex Lw something stepnote.
I had installed 8.04 had a USB modem took me 15 minutes from start to being connected.
A Lot faster and easier than on windows the last time I did it there.

---

### Post by samh785 on 2010-01-12
> **Bartender said:**
> 
#5.  Dial-up.  No more needs to be said ;)
Back when I lived in the hills of Tennessee I used ubuntu 7.04 as my main computer, which included accessing the internet via a Dial-Up connection. I was using an external modem that cost me around 15 dollars. I'm sure that if back in 2007 this wasn't a problem, then it isn't one now. :P

---

### Post by thiebaude on 2010-01-12
For me I'am not sure if something works better in Windows since i don't even have Windows on my computer.

---

### Post by HappyFeet on 2010-01-12
> **Bartender said:**
> 
I'm unemployed right now.  Can't justify $60/month internet.

ATT has high speed for $20 a month, and you don't need phone service through them either.

---

### Post by studmf on 2010-01-12
Virus

---

### Post by Bartender on 2010-01-12
> **samh785 said:**
> I was using an external modem that cost me around 15 dollars. I'm sure that if back in 2007 this wasn't a problem, then it isn't one now.

If you're saying that dial-up is "possible", yes I agree.  

However, it sure isn't easy.  Especially for someone migrating from that other OS, where modems just worked and you didn't have to know anything about how or why they worked.

Happyfeet, is [this]("http://www.att.com/gen/general?pid=6431") what you're referring to?  DSL simply can not be done at our address without about a half million $ in new equipment installed partway up the road, between Qwest's main switching facility in town and our house.

studmf is right.  Maybe I should add that to the original list.  Viruses (virii?) do work better in Windows.

---

### Post by Objekt on 2010-01-12
More people are still using dialup than I thought.  I do empathize with those whom Qwest and Comcast don't deem it necessary to offer broadband.  Until last Saturday, I was stuck with Qwest 1.5 Mbit ADSL.  Qwest simply wouldn't sell me anything faster, presumably because they don't feel like upgrading their vintage 1992 infrastructure.  It's been that way for the last 4 years, with no sign of change.

It sounds like the dialup difficulties under Ubuntu are caused by the usual villain: devices dependent upon drivers, which drivers the manufacturer will never release for Linux.  That is to say Winmodems.  We Linux users are forced to hack together reverse-engineered Linux support for those models where it's possible, or multi-boot Windows, or just buy different hardware.

I'm in the same situation with my Winprinter.  As I mentioned above, I can only access it from a virtual Windows XP machine.  Even then, I cannot print to it from the Ubuntu host OS.  Next time, I'm buying a Postscript-capable printer, so that it is not tied to one OS.

---

### Post by longtom on 2010-01-13
> **samh785 said:**
>  I'm sure that if back in 2007 this wasn't a problem, then it isn't one now. :P

I wouldn't bet on that....not a cent.

---

### Post by lisati on 2010-01-13
> **Bartender said:**
> I'm unemployed right now.  Can't justify $60/month internet.
Ouch! Allowing for exchange rate that's about as much as I'm paying for the basic package for phone line, ADSL2+ internet, and two mobile phones connected. (That's not counting "extras" like calls)
> **HappyFeet said:**
> ATT has high speed for $20 a month, and you don't need phone service through them either.
+1 There are usually options. Good luck!

---

### Post by x33a on 2010-01-13
bsod :D

though, we have got a terminal program named bsod for linux too:

[http://linux.softpedia.com/get/Utilities/bsod-29186.shtml](http://linux.softpedia.com/get/Utilities/bsod-29186.shtml)

---

### Post by Old MW-OS9-68Ker on 2010-06-01
> **Bartender said:**
> Let me ask you, what kind of speeds you get?  I've seen a cell-based modem clip right along with a good signal.  Traditional phone-line dial-up is not the same thing!


I frequently test CDMA EVDO, Rev A data cards and Speedtest.net will regularly show 1.8-2.7Megabits/sec download and .5 Mbit upload for those modems -- that translates roughly to 180-270Kbytes/sec download - not shabby.  These even have a port hole to connect an external antenna to boost reception with a Wilson adapter and antenna.  Verizon and Sprint in Washington likely both have them, and may give a test-ride opportunity for trying it out.

--  The update, for instance for Linux-image-2.6.27-7-generic is 22 Mb, for openoffice-core is 24Mb, and so forth, so actual dialup at, at best 5Kbytes/sec would be possible overnight -- I downloaded Open Office 5.0 and most other software on my '98 box with a dial up and usually felt good about it if I got better than 3.5Kbytes/sec, generally about 1/3 slower was typical.

---

### Post by Old MW-OS9-68Ker on 2010-06-01
> **Bartender said:**
> Let me ask you, what kind of speeds you get?  I've seen a cell-based modem clip right along with a good signal.  Traditional phone-line dial-up is not the same thing!


I frequently test CDMA EVDO, Rev A data cards and Speedtest.net will regularly show 1.8-2.7Megabits/sec download and .5 Mbit upload for those modems -- that translates roughly to 180-270Kbytes/sec download - not shabby.  These even have a port hole to connect an external antenna to boost reception with a Wilson adapter and antenna.  Verizon and Sprint in Washington likely both have them, and may give a test-ride opportunity for trying it out.

--  The update, for instance for Linux-image-2.6.27-7-generic is 22 Mb, for openoffice-core is 24Mb, and so forth, so actual dialup at, at best 5Kbytes/sec would be possible overnight -- I downloaded Open Office 5.0 and most other software on my '98 box with a dial up and usually felt good about it if I got better than 3.5Kbytes/sec, generally about 1/3 slower was typical.

---

### Post by Ms_Angel_D on 2010-06-01
Moved from T&E to avoid Thread closure.

---

