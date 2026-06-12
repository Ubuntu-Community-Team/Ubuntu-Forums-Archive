---
title: "Ubuntu 8.04 slower than XP on the same box, hmm..."
date: 2008-07-05
forum: Recurring Discussions
---

### Post by komputes on 2008-07-05
I was confronted by a windows XP user who informed me that Windows works faster than Linux. I have tested two similar Dell XPS m1330, one with Ubuntu and another with Windows to see how they compared when it came to speed.

-Firefox Web Page Loading Time: Same

-Flash Web Page Resources:
XP Memory: 65MB
Linux Memory: 45MB
XP CPU: 16%
Linux CPU: 9%

-Wifi signal strength: Same
-File copy speed (7GB): 
NTFS -> NTFS: 5 Min
ext3 -> ext3: 8 min

-Firefox Load Time: XP is a millisecond faster

-Full Geekbench Benchmark results:
Linux: [http://browse.geekbench.ca/geekbench2/view/67132](http://browse.geekbench.ca/geekbench2/view/67132)
XP: [http://browse.geekbench.ca/geekbench2/view/67133](http://browse.geekbench.ca/geekbench2/view/67133)

-All I have to say:
Interesting...

---

### Post by Darkade on 2008-07-05
XP is also faster to boot in a fresh install

---

### Post by mingle on 2008-07-05
Hi,

This is my second go at trying to replace XP with Linux (I previously tried Kubuntu 7.10, but was put off by the difficulties I had trying to get simple stuff done and the apps I needed installed.)

I now have a clean install of Ubuntu 8.04, with all the current system updates set up on my Compaq D515 desktop.

I have it dual-booting with Win XP SP3 on another partition.

I've been disappointed (and a bit surprised!) that Ubuntu is noticeably slower and more sluggish at comparable tasks when compared to XP. I haven't actually timed anything yet.

One direct comparison was to run Firefox 3.0 on both machines and visit a few websites. The screen update under Ubuntu is definitely slower. And on one website (the "In The Night Garden" childrens pages on the abc.net.au website) which is very flash-intensive Firefox on Ubuntu positively crawls... 

I have all of the eye candy turned OFF in both Ubuntu and XP.

The spec of the machine are:

P4 1.8GHz
512MB RAM
40GB HDD
Intel 82845 integrated GFX controller

I'm using the correct Linux GFX driver for the Intel 845 too...

Surely Ubuntu should run better than this?

What can I tweak to improve the performance of Ubuntu?

Cheers,

Mike.

---

### Post by powerpleb on 2008-07-05
> **mingle said:**
> 
I have all of the eye candy turned on in both Ubuntu and XP.


Does XP have any eyecandy comparable to that of Ubuntu? (ie compiz)

---

### Post by sdennie on 2008-07-05
> **mingle said:**
> 
I've been disappointed (and a bit surprised!) that Ubuntu is noticeably slower and more sluggish at comparable tasks when compared to XP. I haven't actually timed anything yet.


Humans are very bad at objectively comparing software speeds without a timer.  Everyone gets caught in the trap of "It feels slower" but, often once you measure things, it turns out that it's just "Not faster".

> 
One direct comparison was to run Firefox 3.0 on both machines and visit a few websites. The screen update under Ubuntu is definitely slower. And on one website (the "In The Night Garden" childrens pages on the abc.net.au website) which is very flash-intensive Firefox on Ubuntu positively crawls...


The flash part isn't surprising.  Flash is closed source and not well optmized for linux.  Having said that, I've recently installed Flash 10 and noticed a dramatic decrease in CPU usage.  If you want to try that out, this guide looks like it will probably work: [http://rockmanx.wordpress.com/2008/06/01/install-flash-ubuntu-hardy-heron/](http://rockmanx.wordpress.com/2008/06/01/install-flash-ubuntu-hardy-heron/) 

> 
I have all of the eye candy turned on in both Ubuntu and XP.


This is apples and oranges.  The "eye candy" in Ubuntu will probably include compiz whereas the "eye candy" on XP might anti-alias some fonts if you are lucky.  On more recent cards (at least nvidia cards) compiz makes the desktop more responsive but, on older cards, may decrease the performance of the machine.  Try going to System->Preference->Visual Effects and select "None" and see if that helps a bit.

---

### Post by mingle on 2008-07-05
Oops!

I meant to say I have all the eye candy turned OFF in both XP and Ubuntu...

---

### Post by sdennie on 2008-07-05
> **mingle said:**
> Oops!

I meant to say I have all the eye candy turned OFF in both XP and Ubuntu...

That makes a bit of a difference.  :)

I would still try Flash 10 and see if that helps.  It's still beta but, it did seem to drastically reduce CPU usage for me.

---

### Post by barbedsaber on 2008-07-05
My only suggestion is that a program regularly goes zombie, or somthing, and eats all your ram, leaving you swapping. When you boot, run the following in a terminal ```
top
```
and then do some normal things that ubuntu seems to choke on. While you are doing these, post the output of the top command.

---

### Post by KamalGurung on 2008-07-05
I recently Installed WindowsXP in my Intel Celeron 2 Ghz 1 GB Ram and I also noticed that Ubuntu runs slower in comparison to WindowsXP. But I like the Ubuntu gui very much. But installing new softwares is a pain in ubuntu. Asking too much dependencies :D

---

### Post by mingle on 2008-07-05
Flash 10.0 is a little bit snappier than 9, but it still lags behind the XP version...

Also, my boot times for Ubuntu is 1'06" compared to 50" for XP (an that's running anti-virus/anti-spyware...

Any easy way to improve the boot times?

Are there any patches/libraries or drivers that can speed up Ubuntu?

I know that XP is (although I've had zero stability issues with it in over 5 years!) not exactly a 'lightweight' or compact OS, but it seems that Linux (as a desktop alternative) is just as unwieldy and creaky...

Correct me if I'm wrong, but in Ubuntu, first you load the basic Linux OS, then X-windows, the the windows manager (Gnome).

Is that why it takes so long to get to a working desktop?

After my try with 7.10, 8.04 is getting there, but it still can't replace my XP box... Maybe in Ubuntu 9.x?

Cheers,

Mike.

---

### Post by dcstar on 2008-07-05
> **Darkade said:**
> XP is also faster to boot in a fresh install

How about 3 months after install, or after you have installed the (virtually mandatory) AV package?      ;-)

Seriously, just because you get a login screen with XP doesn't mean it has fully "booted", it just means that the login screen is presented well before numerous other Windows processes have completed loading - as you find out if you try to log in to XP straight away and find the system still busy doing other things.

In my experience the Ubuntu login appears at the end of the boot sequence when most other Linux processes actually have loaded, and the system is virtually available at full speed at that moment.

---

### Post by wariskampar on 2008-07-05
Same issue here. XP is definitely faster to boot up than Hardy Heron. I have tried profiling and preload with no noticeable improvement. In my case, boot stuck at "ata2:PATA max UDMA/100...." and "ata1.00: configured for UDMA/100". It really piss me of because I don't find reliable solution

---

### Post by sdennie on 2008-07-05
> **wariskampar said:**
> Same issue here. XP is definitely faster to boot up than Hardy Heron. I have tried profiling and preload with no noticeable improvement. In my case, boot stuck at "ata2:PATA max UDMA/100...." and "ata1.00: configured for UDMA/100". It really piss me of because I don't find reliable solution

I've never understood peoples obsession with boot times.  If it takes 30 seconds to boot XP and 60 seconds to boot Ubuntu (an extreme case), after an hour of using the machine, that 30 second difference represents less than 1% of the time you've been using the machine.

Think about it this way: If you spend 1 hour optimizing your boot time and it makes your machine boot 10 seconds faster, it will take you 360 boots to recuperate that time.

---

### Post by muteXe on 2008-07-05
just switch on your machine and go make a cuppa tea.  you wont notice then :)

---

### Post by KIAaze on 2008-07-05
Is it only the internet that's slower or is it all apps?
Because I've heard of slow internet problems being caused by Ubuntu using IPv6 by default instead of IPv4.
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)
[http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html](http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html)

I have a PC with approximately the same specs (448MB of RAM and P4 2.4GHz) and Ubuntu runs as well/bad as XP. (internet speed same on both)

---

### Post by sayakb on 2008-07-05
Actually its not Ubuntu, its gnome. Gnome is slightly heavier on machines. For PCs having 1GB+ RAM, you can install preload:
```
sudo apt-get install preload
```
Preload will cache the most executed programs by you (just like prefetch in Windows)
You may also try a different Window manager like Openbox. Configure Openbox to use Nautilus and you'll notice the drastic improvement in performance.
Configuring Openbox: [http://thelastknowngod.homelinux.com/?q=node/10](http://thelastknowngod.homelinux.com/?q=node/10)
Also, you may other DEs like XFCE, and WMs like Enlightment.

---

### Post by zakirs on 2008-07-05
use synaptic .. why do uneed to take care of dependencies it takes care of all the stuff> But installing new softwares is a pain in ubuntu. Asking too much dependencies 

---

### Post by mempman on 2008-07-05
I agree with you, XP is faster than linux.  But thef fact is 99% of current hardware on the market is biased for windowsXP.  The fact that linux, which get practically no support from hardware manufacturers-can compete neck2neck with XP is remarkable.

Hardware manufacturer bias or not, many tests do not test for system stability; however, if they did, we all know who would win hands down.

---

### Post by barbedsaber on 2008-07-05
> **zakirs said:**
> use synaptic .. why do uneed to take care of dependencies it takes care of all the stuff

yeah, I think you would be thinking of red hat, that has dependency issues, but synaptic should handle all dependency.

---

### Post by misfitpierce on 2008-07-05
From fresh install to now over 8 months same install Ubuntu has been faster. All hardware is different but for me Ubuntu has dominated the speed of XP even on boot. I have not used windows for a long time now but as I recall over a year ago when opening Opera on windows i'd wait almost 20 seconds at times. On Ubuntu its literally blink of an eye.

---

### Post by mingle on 2008-07-05
Hi,

I've also tried installing on two other machines (an IBM R51 Thinkpad and a HP D530 desktop) and in both cases XP is smoother and faster in operation.

True, boot times don't REALLY affect the use of the system, but I reckon they are indicative of the relative performance of the OS - as has been shown on the three boxes I've tried Ubuntu 8.04 on.

The other killer (and this is THE main reason I can't switch to Linux) is that there are many apps that I need to use on a daily basis and these just aren't available on Linux.

I haven't tried to use Wine yet, but how much latency does it introduce the the windows apps it runs?

Cheers,

Mike.

---

### Post by Bosconian on 2008-07-05
Have to agree I am afraid. I am dual booting XP and Ubuntu and XP is annihilating Ubuntu for speed.

Flash player is a joke but I am finding that is just one example. Flash player runs perfectly in XP but in Ubuntu it is unwatchable.

---

### Post by Canis familiaris on 2008-07-05
> **mingle said:**
> Hi,

I've also tried installing on two other machines (an IBM R51 Thinkpad and a HP D530 desktop) and in both cases XP is smoother and faster in operation.
Yes the Windows boots up faster but the experience is smoother in Ubuntu. Most applications launch up in a snap, while in Windows, they dont.


> **mingle said:**
> 

True, boot times don't REALLY affect the use of the system, but I reckon they are indicative of the relative performance of the OS - as has been shown on the three boxes I've tried Ubuntu 8.04 on.

No boot times are not really indicative of relative performance of the OS. 

> **mingle said:**
> 
The other killer (and this is THE main reason I can't switch to Linux) is that there are many apps that I need to use on a daily basis and these just aren't available on Linux.

I haven't tried to use Wine yet, but how much latency does it introduce the the windows apps it runs?


You could try Virtualbox.

---

### Post by Canis familiaris on 2008-07-05
> **Bosconian said:**
> 
Flash player is a joke but I am finding that is just one example. Flash player runs perfectly in XP but in Ubuntu it is unwatchable.
The fault lies with Adobe.

---

### Post by Canis familiaris on 2008-07-05
> **Bosconian said:**
> Have to agree I am afraid. I am dual booting XP and Ubuntu and XP is annihilating Ubuntu for speed.

In what respect? A FRESH INSTALL OF XP with no Office, no Antivirus, no Spyware remover, no 3rd party firewall is definitely faster than Ubuntu but when you install these important stuff XP will get slower.
Also as time passes XP gets slower. Ubuntu remains the same.

---

### Post by hyper_ch on 2008-07-05
btw, win XP was released in 2001.... Ubuntu Hardy in 2008... you should compare VISTA and Hardy

---

### Post by Bosconian on 2008-07-05
> **hyper_ch said:**
> btw, win XP was released in 2001.... Ubuntu Hardy in 2008... you should compare VISTA and Hardy


Yeah a 2001 OS looks better and performs better than a 2008 OS. Says it all really. Sorry but it does.

---

### Post by Xerp on 2008-07-05
I've found Ubuntu boots loads faster than XP. One trick that XP uses is to display the desktop before it is actually ready to use. It gives the illusion of a fast boot, but its just that - an illusion. I'm sure anyone that has used Windows has found this really annoying. You're half way through navigating the "start" menu and suddenly - ping! Its gone. To be a fair and accurate test you need to stop timing when the desktop is ready to use - this means letting ALL the "systray" icons load. I'm pretty sure you'll find, like me, that Windows XP takes 2-3 times longer than Ubuntu to get ready.

As for performance of the Flash player in Firefox on Ubuntu and Firefox on Windows XP, again I've found Ubuntu comes in not only way smoother and faster, but also with some tricks up its sleeve. One such example is when watching Flash full screen. I use the BBC iPlayer a lot, and when you click their "full screen" icon the quality is noticable poorer. In Windows XP the frames also skip and the thing just jitters along. In Ubuntu I can use the zoom feature of Compiz. This means I get full screen flash, scaled nicely and really, really smooth. 

My girlfriend uses Facebook a lot too, and play some Flash-based brain game. She won't play it on Windows because she can't get a good score using it.

I used both XP and Ubuntu extensively on a daily basis, and for getting things done fast Ubuntu wins hands down every time for me. It has a more cohesive desktop and productivity enhancing features that just leave Windows gasping for breath. As for Vista... well... that thing just pains me. Applications become unresponsive and crash almost like clockwork - even things like Microsoft Outlook. I get 2 or 3 random blue screens a month. Its just not worth using.

---

### Post by Bosconian on 2008-07-05
> **Anurag_panda said:**
> The fault lies with Adobe.


Each to their own but I personally don't care whose fault it is. XP performs better and where the fault lies is of no consequence to me.

I am an end user who is uninterested as to why something performs better in one or the other, only the fact that one does perform better than the other. You can blame Santa Claus for all I care.

---

### Post by edm1 on 2008-07-05
> **mingle said:**
> The spec of the machine are:

P4 1.8GHz
512MB RAM
40GB HDD
Intel 82845 integrated GFX controller

I'm using the correct Linux GFX driver for the Intel 845 too...


With specs like that you should really be looking at xubuntu if speed is what you're after. On my laptop with similar specs i do use gnome but 512mb RAM nearly doesn't cut it. XFCE will be ALOT faster than xp on that machine.

---

### Post by hyper_ch on 2008-07-05
> **Bosconian said:**
> Yeah a 2001 OS looks better and performs better than a 2008 OS. Says it all really. Sorry but it does.

well, use DSL ;) a 2008 OS that outperforms XP by far ;) but for a comparison you should have equal straws ;)

---

### Post by ixus_123 on 2008-07-05
If you are dual booting I assume XP is on the first partition of the disk?  This the inside of the disc is quicker to access then the outside so that could have a small effect on perceived speed (like opening windows etc)

What file systems are you using?  A FAT XP would also likely feel faster than EXT3 linux.  This is becuase EXT3 journals but is also more robust.  NTFS copares better to EXT3.

What are you using to measure this speed?  Boot up times dont really count for much in my book. Windows is a pain because it will let you log in before starting a whole bunch of services so you can add that on to the boot time.


I am not championing either camp, I'm no fanboy - I like MS, Mac and Linux -thay all have their uses for me.

If you want to compare speed a few things you may want to try are

ripping mp3s from a CD

ripping a DVD to mpg4

creating a large file - say an 8GB disk image file, time how long it takes windows and linux to copy it to another disk and also how long it takes to delete it.

You could use web browser tests.  Wired.com or other complex sites are good to us for page load times - dont forget to empty your browser cache first.  You can also download webpages to test browsers so that your connection doesn't sku the results.

You might want to turn off file previews for Ubuntu to speed up the file browsing experience.  so that you get an icon for jpegs rather than a thumbnail or preview of a text document.

---

### Post by Canis familiaris on 2008-07-05
> **hyper_ch said:**
> well, use DSL ;) a 2008 OS that outperforms XP by far ;) but for a comparison you should have equal straws ;)

Yeah! So does Puppy Linux.

EDIT: And Xubuntu too!

---

### Post by Bog_Warrior on 2008-07-05
I Dual boot on a Gateway with 512 RAM and there is no doubt that I have found Ubuntu faster.  Even if it weren't faster for me it is undeniably more stable and free.  I paid over $100 for Windows XP Home (Crap version of XP at best) and have had nothing but crash after crash and annoyingly slow performance.  

As I said, even if Ubuntu was slower, I would go with slow and steady over faster and unstable.

My two cents, of course.  Use what you want.

---

### Post by Canis familiaris on 2008-07-05
> **Bosconian said:**
> Each to their own but I personally don't care whose fault it is. XP performs better and where the fault lies is of no consequence to me.

I am an end user who is uninterested as to why something performs better in one or the other, only the fact that one does perform better than the other. You can blame Santa Claus for all I care.

Use what you find better suited for you. 
Windows may be the BEST FOR YOU.
Me? Linux is BEST FOR ME.

---

### Post by kansasnoob on 2008-07-05
I've had just the opposite experience. 7.10 was fine but 8.04 is just downright snappy! Both were certainly faster than a fresh install of XP, and I do dual boot with XP just as a matter of preference.

I'm too much of a nOOb to know why Ubuntu might be slower for you. I know I "unticked" Bluetooth device management and Hotkeys management in System . Administration > Services. More should perhaps come to mind. I've come to prefer Totem so I install all Totem, and always ALL Gstreamer, all Sun-Java6 (except -doc and -source), and after installing the Medibuntu repo I install acroread, non-free-codecs, and flashplugin-nonfree.

And, as I read someone else say, using Synaptic pretty well solves any dependency issues, but I still like to:

```
sudo apt-get -f install
```

after modifying a fresh install or upgrade just to resolve any unmet dependencies.

I also use Abiword & Gnome Office rather than Open Office just as a matter of personal preference but I suspect it's much lighter weight.

As far as puter specs I'm just running a PC2500E VIA mainboard w/embedded 1500 MHZ C7 proc, so it's hardly a high spec job, and I started with 512 mb RAM which was a bit slow so I upgraded to 2gb of RAM for about $40.

It might be interesting to look at System > Administration > System Monitor (pretty sure it's installed by default) and see what things look like:

[ATTACH]76477[/ATTACH]

[ATTACH]76478[/ATTACH]

---

### Post by kansasnoob on 2008-07-05
Now for a personal rant:

Speaking of speed, I'm far from a techie but somehow the task has fallen to me to work on many seniors computers so I install a lot of Windows and/or Ubuntu. I can normally do a complete Ubuntu install including modifications in just over one hour. Windows on the other hand normally takes anywhere from 4 to 8 hours by the time I install all of the AV, firewall, print drivers, photo editing software, etc, etc.

Worse yet, when the IT stores run out of XP OEM and retail versions it's all gonna be Vista and only Ultimate will be downgradable to XP. I just bought a 3-pack of XP Home OEM versions just because they're soon to be no more at an individual cost of about $80 each! That's a load of cash for most seniors on fixed incomes!

End rant .............. sorry.

---

### Post by Darkade on 2008-07-05
> **dcstar said:**
> How about 3 months after install, or after you have installed the (virtually mandatory) AV package?      ;-)

Seriously, just because you get a login screen with XP doesn't mean it has fully "booted", it just means that the login screen is presented well before numerous other Windows processes have completed loading - as you find out if you try to log in to XP straight away and find the system still busy doing other things.

In my experience the Ubuntu login appears at the end of the boot sequence when most other Linux processes actually have loaded, and the system is virtually available at full speed at that moment.

True, XP is faster to boot, however ubuntu gives you a Desktop enviroment faster

---

### Post by mikjp on 2008-07-05
> **Anurag_panda said:**
> In what respect? A FRESH INSTALL OF XP with no Office, no Antivirus, no Spyware remover, no 3rd party firewall is definitely faster than Ubuntu - - 

And compromised before you have time to install a firewall and download antivirus software.

---

### Post by mikjp on 2008-07-05
> **mingle said:**
> Any easy way to improve the boot times?


Turn off the boot splash screen by editing the /boot/grub/menu.lst, and you'll see where the time is being spent. After that it should be possible to tweak the booting, turn off the unnecessary services etc.

---

### Post by onyxbits on 2008-07-05
> **mingle said:**
> 
What can I tweak to improve the performance of Ubuntu?


I'm currently writing an article about [tuning linux]("http://www.onyxbits.de/node/46") in general. It's a work in progress, but maybe you find some tweaking tips there.

---

### Post by bodhi.zazen on 2008-07-05
Wow this is a long thread ....

It is true if you do a fresh install of Windows XP and Ubuntu, XP will initially run faster. XP also runs faster after a reboot.

But over time the performance of XP will degrade. It will run slower and slower, eventually slower then Ubuntu.

You can, for a time, increase performance by rebooting.

Eventually XP will slow down or fragment or corrupt or any other number of various deaths.

Ubuntu will not do any of this, it will keep on running and running.

If you are new to Linux I suggest you avoid the various "performance tweaks" , Ubuntu is already optimized. Most of the "performance tweaks" are, IMO, over rated and you can also degrade performance.

Now, with that said, if you know your hardware and you know what you are doing you can improve performance somewhat. Just be sure you know what the default settings are before you change them ...

Just keep in mind:

1. As vor indicated "perfomance" is very subjective.

2. If you are looking at "Benchmarks" make sure they use a number of tests. Benchmarks often measure time of performing repetitive tasks that most desktop users do not do (benchmarks do not measure for example time of google searches).

You might want to look at this link for additional suggestions :

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by Canis familiaris on 2008-07-05
Well said bodhi.zazen

---

### Post by HappyHenry on 2008-07-05
> **bodhi.zazen said:**
> Wow this is a long thread ....

It is true if you do a fresh install of Windows XP and Ubuntu, XP will initially run faster. XP also runs faster after a reboot.

But over time the performance of XP will degrade. It will run slower and slower, eventually slower then Ubuntu.

You can, for a time, increase performance by rebooting.

Eventually XP will slow down or fragment or corrupt or any other number of various deaths.

Ubuntu will not do any of this, it will keep on running and running.

If you are new to Linux I suggest you avoid the various "performance tweaks" , Ubuntu is already optimized. Most of the "performance tweaks" are, IMO, over rated and you can also degrade performance.

Now, with that said, if you know your hardware and you know what you are doing you can improve performance somewhat. Just be sure you know what the default settings are before you change them ...

Just keep in mind:

1. As vor indicated "perfomance" is very subjective.

2. If you are looking at "Benchmarks" make sure they use a number of tests. Benchmarks often measure time of performing repetitive tasks that most desktop users do not do (benchmarks do not measure for example time of google searches).

You might want to look at this link for additional suggestions :

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

I quote because I wanted to show support for this statement as being true for me as well. I have used Ubuntu for five years (still consider myself a noob, cause im lazy :) ) I've used windonts for over 13 years. Many reformats and reistall of windots left me drooling in the corner mumbling something about virus,firewall or simply repeating dll dll dll For my sanity and so my family didn't commit me, i dont use windonts any longer.

On such a night, after fresh install of windonts, i searched the web for sanity and found Ubuntu. The first few installs were a little ruff because of my ignorance but today with Hardy everything is a breeze! I have never found a web site with support and people for windonts that could even come close to the friendly comprehensive community found here.

_Windonts running faster after fresh install is not windonts_. Windonts doesn't show its true self until you do your "143 security updates, 3sp packages, 2473 optional updates found" install the ever needed anti virus' Then try timing your reboot. Do a fresh install of Ubuntu hardy do the updates, no antivirus needed and reboot to time it. This is a more fare comparison. IF, i doubt it, they are still comparable, give windonts a couple months to bloat your system and ....we all know, any Ubuntu/Linux will run circles around any version of windonts.

I dont mean to sound as if im attacking **any person**. I am venting at the *idea* that windonts even compares to Linux/Ubuntu in the performance arena.

_On a more personal note_; A look around the forums and you should find all the help you need to get a Ubuntu system running how you want. doing the "top" command in a terminal (It will show everything running in your system) and posting it with your hardware specs would be a great start. . The absolute beginers forum is great. I hope my venting about windonts/Linux wasnt taken personal. 

I've built dozens of computers and installed different windonts and Linux distros. Windows simply does not come close to Ubuntu or any Linux distro in the performance arena.

---

### Post by phread59 on 2008-07-05
I'll stick my coupla pennies in here.  I do have a fresh install of XP Pro 64 bit and a recent install of Ubuntu 8.04.  My experiences have not been the same though.  I built this machine myself and it has the following:

Intell Core 2 Duo 6550 2.33 ghz processor
4 gig of Patriot 800hz 64 bit memory
Asus P5N-E SLI mother board w/1066 front side bus
Windows is on an 80 gig ATA drive
Ubuntu is on an320Gig SATA 2 drive

And the boot times are way slower on Windows.  I had the drives reversed before.  Even With Ubuntu on the ATA drive it still booted faster.  Speed was only marginally faster with Windows before adding the ususal software it needs.  Ubuntu was then about the same.  And Ubuntu is the 32 bit version!  All in all Ubuntu is about the same using either IE or Firefox in Windows.  Now I did not tune Windows any.  So this is just my opinion only.  No stopwatches were used.  Just day to day use impressions.  If speed is paramout I would add my reccomendations of a lighter desktop.  They are in the repositorys and are easy to install.  When booting the Option button in the lower left will give you access to any and all desktops you have loaded.  Try one out and see the difference.  Also try Opera.  The newest version flat out sings.  You should find significant speed with the new desktop and Opera.

And I will also add this.  Use what you like.  But I will also point out the need to defrag the Windows HD and clean the registry and run virus and adware scans, all unnescessary in linux.  Try to enjoy the freedom of having 2 OS's and use what suites you best be that Winows or Linux.

Mark Sahuman

---

### Post by komputes on 2008-07-05
Actually these were both standard installations off the disk of XP (SP2) and the 8.04 release. So both machines were new. They both got to the login screen at virtually the same time and with automated login they also got to the desktop at virtually the same time. No doubt XP creates a ton of startup services with every app you install which boats your system and gives you access to your apps much slower but this can always be turned off in 'msconfig'. 

I had to abandon the OOo and zip compression tests because it would not compress a 7GB folder to zip, only tar.gz and OOo crashed (I think this is a bug they have released a fix for, but remember - no updates).

The thing I hate about XP is the fact that you sometimes need to tell it to shut down multiple times and even at that it takes forever. In Ubuntu only gnome integrated apps (like gedit) can ask you if you want to save or cancel logout procedure, which I find very nice. Usually, I want the computer to be off as fast as possible. (Oh no, Bill Lumburg is coming and it's Friday! :lolflag: )

What troubles me is the speeds of the benchmark tests Ubuntu vs XP on the same hardware. I'm not one of those freaks that will compile everything on the specific computer in order to be use at maximum efficiency, but I mean should it be this far apart? I'm also concerned that the same 7Gb  folder took more time to copy on ext3 than NTFS. Although Ubuntu is more accurate in guessing how long it will take to complete.

---

### Post by Powerman2442 on 2008-07-05
> **dcstar said:**
> How about 3 months after install, or after you have installed the (virtually mandatory) AV package?      ;-)

Seriously, just because you get a login screen with XP doesn't mean it has fully "booted", it just means that the login screen is presented well before numerous other Windows processes have completed loading - as you find out if you try to log in to XP straight away and find the system still busy doing other things.

In my experience the Ubuntu login appears at the end of the boot sequence when most other Linux processes actually have loaded, and the system is virtually available at full speed at that moment.

True that. Vista doesn't even connect to my wireless network until after I sign in. When I sign in on Ubuntu it is already connected. Not to mention no AV for Ubuntu. YAY!

So in theory since Linux uses less of your hardware (CPU, RAM, etc.) and it runs about the same speed. If it were to use at much CPU power or RAM as XP wouldn't it end up performing better?

---

### Post by sdennie on 2008-07-05
There was another thread similar to this yesterday.  I don't know why people insist on comparing Ubuntu 8.04 to XP.  One OS is 7 years old and no longer ships on computers while the other OS is a few months old.  Compare Ubuntu 8.04 to Vista and see what the tests say.

---

### Post by theshadowwithanmp5n on 2008-07-05
HERE'S HOW IT WORKS
when windows loads up, it doesn't finish loading until well after you log in.
that's how it is on all windows systems around now.

when ubuntu loads, it waits until everything related to the system is loaded to show the login screen. afterwords, depending on who logs in, it loads all the personal stuff.

---

### Post by bodhi.zazen on 2008-07-05
> **vor said:**
> There was another thread similar to this yesterday.  I don't know why people insist on comparing Ubuntu 8.04 to XP.  One OS is 7 years old and no longer ships on computers while the other OS is a few months old.  Compare Ubuntu 8.04 to Vista and see what the tests say.

Threads merged and further mored to "recurring discussions" as :

1. Neither thread is a support request

2. I think as vor pointed out, it is a recurring discussion.

See this post : (scroll up if you missed it :

> Wow this is a long thread ....

It is true if you do a fresh install of Windows XP and Ubuntu, XP will initially run faster. XP also runs faster after a reboot.

But over time the performance of XP will degrade. It will run slower and slower, eventually slower then Ubuntu.

You can, for a time, increase performance by rebooting.

Eventually XP will slow down or fragment or corrupt or any other number of various deaths.

Ubuntu will not do any of this, it will keep on running and running.

If you are new to Linux I suggest you avoid the various "performance tweaks" , Ubuntu is already optimized. Most of the "performance tweaks" are, IMO, over rated and you can also degrade performance.

Now, with that said, if you know your hardware and you know what you are doing you can improve performance somewhat. Just be sure you know what the default settings are before you change them ...

Just keep in mind:

1. As vor indicated "perfomance" is very subjective.

2. If you are looking at "Benchmarks" make sure they use a number of tests. Benchmarks often measure time of performing repetitive tasks that most desktop users do not do (benchmarks do not measure for example time of google searches).

You might want to look at this link for additional suggestions :

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by dcstar on 2008-07-05
> **wariskampar said:**
> Same issue here. XP is definitely faster to boot up than Hardy Heron. I have tried profiling and preload with no noticeable improvement. In my case, boot stuck at "ata2:PATA max UDMA/100...." and "ata1.00: configured for UDMA/100". It really piss me of because I don't find reliable solution

PATA IDE issues are usually related to misconfiguration of the PATA devices you have on the bus - not having Master devices and/or misconfigured Slave devices can cause timeout issues by software that adheres strictly to the ATAPI interface specifications (like Linux/Unix kernels).

Things like Windows do not seem to follow these specs strictly and will work better with misconfigured hardware (why wait the 30 seconds specified for a possible response from a device when 1 second will do 99% of the time........)

Post your specific problem in the appropriate forum and you may get a solution.

---

### Post by dcstar on 2008-07-05
> **komputes said:**
> 
.........
What troubles me is the speeds of the benchmark tests Ubuntu vs XP on the same hardware. I'm not one of those freaks that will compile everything on the specific computer in order to be use at maximum efficiency, but I mean should it be this far apart? I'm also concerned that the same 7Gb folder took more time to copy on ext3 than NTFS. Although Ubuntu is more accurate in guessing how long it will take to complete.

All filesystems are a compromise between performance and reliability.

Choose a Linux filesystem with the same "reliability" as NTFS for any like-to-like comparison, otherwise any so-called benchmark is pretty meaningless.

You can use EXT2 for more performance and less reliability (EXT3 without the journaling), or Reiserfs for it's particular attributes, or choose a filesystem that handles lots of small files well compared with one that works like a rocket with big files.

You may find that NTFS looks faster, but over time in "real life" corrupts files and loses data many more times than EXT3, so which is the "better" filesystem in that case?

Simplistic comparisons in this area can cause people to come to conclusions that may not be much real value to them.

---

### Post by HappyHenry on 2008-07-05
> **dcstar said:**
> 
Simplistic Comparisons In This Area Can Cause People To Come To Conclusions That May Not Be Much Real Value To Them.

Well Said!

---

### Post by komputes on 2008-07-06
> **dcstar said:**
> You can use EXT2 for more performance and less reliability (EXT3 without the journaling), or Reiserfs for it's particular attributes, or choose a filesystem that handles lots of small files well compared with one that works like a rocket with big files.

When I did the test,  the files copied were very few large files (disc images). I am just thinking of copying terrabytes of data from one drive to another and how to save the most time. I will try these suggestions: est2/reiserfs (which FS has best speed performance in Ubuntu?)

I completely understand what you're saying. These benchmarks are simply interesting to look at and no conclusions should be taken from them. As well, these tests do not prove which operating system is better and more reliable. I was simply trying to say that the difference to the user was negligible but in certain geekbench tests the metrics were far apart when compared.

---

### Post by madjr on 2008-07-06
the next Ubuntu 8.10 will work on the boot-up time.

probably even faster than XP.

other distros like **Arch** is already optimized and boot-up in 15 seconds, XP will never boot up so fast.

linux can be optimized endlessly


[http://www.youtube.com/watch?v=oOZoM-AmCSo](http://www.youtube.com/watch?v=oOZoM-AmCSo)

[http://www.youtube.com/watch?v=ug7sVXCyHjk](http://www.youtube.com/watch?v=ug7sVXCyHjk)

[http://www.youtube.com/watch?v=A5h7wtkg4Bc&feature=related](http://www.youtube.com/watch?v=A5h7wtkg4Bc&feature=related)

---

### Post by Bosconian on 2008-07-06
> **madjr said:**
> linux can be optimized endlessly


That isn't a very good statement to make. If that was the case then Linux would eventually boot up instantaneously. I know what you meant though.

---

### Post by madjr on 2008-07-06
> **Bosconian said:**
> That isn't a very good statement to make. If that was the case then Linux would eventually boot up instantaneously. I know what you meant though.

some mini-distros do boot up instantaneously

take a look:
[http://www.splashtop.com/](http://www.splashtop.com/)

it's so lightweight and efficient it already comes embedded in many products including as part of the bios and motherboards

---

### Post by tastefulasever on 2008-07-06
> 
[QUOTE]Quote:
Originally Posted by madjr View Post
linux can be optimized endlessly

That isn't a very good statement to make. If that was the case then Linux would eventually boot up instantaneously. I know what you meant though.[/QUOTE]

Oh I don't know about that.  There is an infinite number of place holders between 0 and 1 (0.000000001, 0.000000001, etc.).  I'm pretty sure software can be optimized endlessly, if we assume that hardware will continue to evolve endlessly.  Always you can attempt to squeeze out another nanosecond.

---

### Post by madjr on 2008-07-06
about flash being slow

flash 10 beta release candidate is out and **WOW**

get it now

[http://www.linuxloop.com/news/2008/07/05/installing-flash-player-10-prerelease-on-linux/](http://www.linuxloop.com/news/2008/07/05/installing-flash-player-10-prerelease-on-linux/)

---

### Post by Saint Angeles on 2008-07-06
> **Bosconian said:**
> Yeah a 2001 OS looks better and performs better than a 2008 OS. Says it all really. Sorry but it does.
looks better? are you out of your mind? do you even want to be taken seriously?

---

### Post by Bosconian on 2008-07-06
> **madjr said:**
> about flash being slow

flash 10 beta release candidate is out and **WOW**

get it now

[http://www.linuxloop.com/news/2008/07/05/installing-flash-player-10-prerelease-on-linux/](http://www.linuxloop.com/news/2008/07/05/installing-flash-player-10-prerelease-on-linux/)


made no difference on my machine. Still screen tearing and dropped frames. XP on the same machines plays it just fine.

By "WOW" did you mean how awful it is :)

---

### Post by LaRoza on 2008-07-06
> **Bosconian said:**
> made no difference on my machine. Still screen tearing and dropped frames. XP on the same machines plays it just fine.

By "WOW" did you mean how awful it is :)

Are you sure it is being used?

And it isn't wise to assume everyone has the same experiences as you, good or bad.

---

### Post by karellen on 2008-07-06
> The flash part isn't surprising. Flash is closed source and not well optmized for linux.
something I come across frequently and I can't understand: isn't Flash closed source on Windows platform too? and Firefox open source too? then why it runs so much better in Windows?...
probably a well trained programmer in Windows software ecosystem could explain this to me

---

### Post by sdennie on 2008-07-06
> **karellen said:**
> something I come across frequently and I can't understand: isn't Flash closed source on Windows platform too? and Firefox open source too? then why it runs so much better in Windows?...
probably a well trained programmer in Windows software ecosystem could explain this to me

Well, optimizing an application for a particular platform is not trivial.  It makes sense for Adobe to optimize flash for Windows as it's the largest user base and so will have the most impact.  You will notice that most proprietary software that exists for both Windows and Linux will run better on Windows for this reason.  Linux support is often an afterthought for proprietary software/drivers but, that's usually not an issue because high quality open source alternatives exist in most cases.

---

### Post by Bosconian on 2008-07-06
> **LaRoza said:**
> Are you sure it is being used?

And it isn't wise to assume everyone has the same experiences as you, good or bad.


Yes it is being used. The about info testifies to that.

I am not assuming. I have seen a lot of people say that 10 is better but still abysmal.

---

### Post by powerpleb on 2008-07-06
It's no suprise to me that XP is faster than Ubuntu. XP is quite old now and was designed to run well on computers that have the minimum specs recommended for an Ubuntu install. It is less flexible, has most of it's software designed and optimised for it and has had years of bugfixes and tweaks to improve it. XP is obsolete, the only reason it can be purchased still is because Vista was such a fiasco. Compare Ubuntu to Vista if you want to be fair. 
Also after a while of use XP slows down considerably more than Ubuntu does. And when you factor in all of the anti-spyware, virus and malware protection that is essential for XP I think you'll find that it slows down a lot.

---

### Post by chrisby on 2008-07-06
I think most people do tests that don't involve any kind of multitasking. I don't have benchmarks here, but I always noticed xp was fast when doing one thing, but became slow and unstable as soon as you start doing multiple things.  

I don't think it is ever fair to compare xp to ubuntu by application, but only by total experience.

---

### Post by Bosconian on 2008-07-07
The other problem of course is that XP does everything you want it to do whereas Ubuntu doesn't.

So far in Ubuntu I cannot:

1. Sync my music with my iPod Touch (not interested in having to hack it, it should work out of the box)

2. Sync my contacts, calendar, task, etc with my PDA (just doesn't work)

3. Watch BBC iPlayer with no screen tearing or dropped frames

4. Actually I won't bother carrying on with my long list of things I can do with XP so simply yet Ubuntu is so inept at.

What is the point of running an OS that I am restricted with what I am allowed to do with it.

---

### Post by sdennie on 2008-07-07
> **Bosconian said:**
> The other problem of course is that XP does everything you want it to do whereas Ubuntu doesn't.

So far in Ubuntu I cannot:

1. Sync my music with my iPod Touch (not interested in having to hack it, it should work out of the box)


Ask the vendor of the hardware to open their proprietary drivers so that they can be adapted for linux.

> 
2. Sync my contacts, calendar, task, etc with my PDA (just doesn't work)


Ask the vendor to open their proprietary drivers so that they can be adapted for linux.

> 
3. Watch BBC iPlayer with no screen tearing or dropped frames


Ask the vendor to open their proprietary software so that they can be adapted for linux.

> 
4. Actually I won't bother carrying on with my long list of things I can do with XP so simply yet Ubuntu is so inept at.


That's fine.  You've probably noticed the trend...  ;)

> 
What is the point of running an OS that I am restricted with what I am allowed to do with it.

The OS isn't restricting you.  The vendors of the hardware/software you want to use are restricting you by not supporting linux well.

---

### Post by Bosconian on 2008-07-07
> **vor said:**
> Ask the vendor of the hardware to open their proprietary drivers so that they can be adapted for linux.



Ask the vendor to open their proprietary drivers so that they can be adapted for linux.



Ask the vendor to open their proprietary software so that they can be adapted for linux.



That's fine.  You've probably noticed the trend...  ;)



The OS isn't restricting you.  The vendors of the hardware/software you want to use are restricting you by not supporting linux well.


Again, it doesn't make any difference to an end user WHY it doesn't work only that it doesn't. The fact is XP does all of those with ease. The reason why that is is unimportant and of no consequence to me the end user.

---

### Post by sdennie on 2008-07-07
> **Bosconian said:**
> Again, it doesn't make any difference to an end user WHY it doesn't work only that it doesn't. The fact is XP does all of those with ease. The reason why that is is unimportant and of no consequence to me the end user.

I disagree.  When an end user understands why their hardware/software doesn't work well on linux, I hope it makes them angry enough to stop buying/"using software" from that vendor and write them polite e-mails about why they have stopped.

10 years ago, I wrote ATI asking if I could get specs on the tv tuner of my graphics card so that I could write a linux driver for it.  They told me to get lost and I have never bought a single piece of ATI hardware since...

---

### Post by Canis familiaris on 2008-07-07
> **vor said:**
> 
10 years ago, I wrote ATI asking if I could get specs on the tv tuner of my graphics card so that I could write a linux driver for it.  They told me to get lost and I have never bought a single piece of ATI hardware since...
ATI was really awful before the takeover of AMD. After the takeover by AMD things have taken over a new leaf.

---

### Post by Canis familiaris on 2008-07-07
> **Bosconian said:**
> Again, it doesn't make any difference to an end user WHY it doesn't work only that it doesn't. The fact is XP does all of those with ease. The reason why that is is unimportant and of no consequence to me the end user.
Because of this attitude only Hardware Manufacturers do not pay proper attention to Linux. If people like you pointed out these flaws to the companies and requested them to rectify the problems then support would have been much better.
Take this case:
The place I live, there Wireless internet sucks. Now since I am an end user should I complain to the providers of the poor service or should I blame wireless technology that the reason why it is not working is unimportant and of no consequence to end user and stop using wireless altogether?
And have you done any effort to rectify those problems? If you indeed dont like Linux and like Windows. Go on and use Windows, nobody is stopping you. But to preach against Linux in a Linux forum where other people know more than you is useless.

---

### Post by joninkrakow on 2008-07-07
> **mempman said:**
> I agree with you, XP is faster than linux.  But thef fact is 99% of current hardware on the market is biased for windowsXP.  The fact that linux, which get practically no support from hardware manufacturers-can compete neck2neck with XP is remarkable.


And yet, I think that to say that XP is faster than Linux is a bit too broad. I have an ancient 366mhz PII that has Win2K on it. Windows is fast enough, but put Puppy Linux on that computer and it _screams_ in comparison to Windows. The _only_ thing Windows can do faster is Flash, but you can't do recent flash in the Explorer that comes with 2k, you need Firefox to do it (who's complaining?)

It would be more to the truth to say that Gnome is slower than XP, and maybe KDE, although, I think that KDE 3.5 tends to be faster than Gnome on my computers. Xfce isn't much faster than Gnome on my older computers, but I bet it's a lot faster on newer computers. Plus, there is LXDE for a desktop environ that is faster than either of the other DE options, and if you are willing to go to a straight window manager, all of them are even faster. And this effects my computer in other areas, like running Firefox 3. It runs better under LXDE than under xfce on my laptop, and even faster under icewm. So, it's not a given that Linux is slower than XP, IMO (with the notable exception of Flash--but I guess we could expect that.)

-Jon

---

### Post by bodhi.zazen on 2008-07-07
Go vor

In the past year I have returned several "minor" pieces of hardware due to a lack of Linux support.

When buying hardware you need to watch compatibility. This is true of any OS. In general Linux has a longer list of hardware compatibility then Windows.

It is frustrating, however, on any OS, if your hardware does not work.

So, you need to do your home work before buying, and this is true of any OS, including Windows and Mac. Linux is no different.

If your hardware does not work, you should contact the manufacturer, not the OS. Microsoft, for example, does not maintain all the various drivers for Windows. Same with Linux.

If your hardware does not work what do you do ? 

[list][*]Download and install the drivers yourself.
[*]Hack the OS to make it work.
[*]Return the item.[/list]

Holds true of any OS. If you do your home work you can usually find compatible hardware for any OS.

---

### Post by BDNiner on 2008-07-07
> **dcstar said:**
>  In my experience the Ubuntu login appears at the end of the boot sequence when most other Linux processes actually have loaded, and the system is virtually available at full speed at that moment.

+1

I find that it takes shorter for windows to get to the login screen when i start both my computers at the same time. but i my linux computer will catch up and even get firefox open to ubuntuforums.com before the XP machine has finished loging in.

---

### Post by ryaxnb on 2008-07-07
> **mingle said:**
> Flash 10.0 is a little bit snappier than 9, but it still lags behind the XP version...

Also, my boot times for Ubuntu is 1'06" compared to 50" for XP (an that's running anti-virus/anti-spyware...

Any easy way to improve the boot times?

Are there any patches/libraries or drivers that can speed up Ubuntu?

I know that XP is (although I've had zero stability issues with it in over 5 years!) not exactly a 'lightweight' or compact OS, but it seems that Linux (as a desktop alternative) is just as unwieldy and creaky...

Correct me if I'm wrong, but in Ubuntu, first you load the basic Linux OS, then X-windows, the the windows manager (Gnome).

Is that why it takes so long to get to a working desktop?

After my try with 7.10, 8.04 is getting there, but it still can't replace my XP box... Maybe in Ubuntu 9.x?

Cheers,

Mike.

Well you could always try running something smaller, for instance loading GNOME takes much longer then loading say jwm with iDesk. You could try Puppy or Vector, they run faster then ****.

---

### Post by komputes on 2008-07-07
> **madjr said:**
> about flash being slow
flash 10 beta release candidate is out and **WOW**

I just tried this and it does fix quite a few flash-related bugs/slowdowns. A few little improvement although it's more CPU intensive but a little less memory intensive than Flash 9 was. I think enough people started complaining that Adobe finally got the point. Can't wait to see the polished version of 10.

---

### Post by ranchero on 2008-07-10
Well, here's my 2 cents (a bit more than 2, I guess :). 
I really wanted to move to Linux from XP. I've tired of viruses, stupid registry and so on.
So step #1. I've built new system - AMD 6000+, 2GB RAM, 160GB Raptor primary HDD, Crosshair MB, ATI All-in-Wonder - just the way I wanted.
Overclocked a bit - from 3000 to 3150 MHz, memory from 800 to 900MHz.
Tested it with XP (32bit) - blazing fast. Start time (from pushing power button to WORKING! fully loaded  desktop) - 20 seconds (no login/password used as I never had it in XP).
I never use firewall or antivirus programs for same reason - don't want to lose performance.
To these who saying XP will lose performance with time...yes, it will, but one can manage to keep it acceptable. There're many tricks to speed up XP, including startup time etc. My previous XP installation was running for about 5 years (!), migrating from one computer to another, I was fighting with it from time to time, of course (viruses, registry cleaning etc.), but still startup time was under 1 min after many years.  But I wanted Linux as it looked better in many ways...
So I said to myself - it's time to switch. 
Downloaded Ubuntu 7.10 (8.04 was already out, so I had hard time finding "old" 7.10 version - a little strange, reminds pushing from XP to Vista...)
I COULD NOT install it at all! I've had all kinds of errors, freezing and crashes, I asked for help - not much help was found...
So I gave up.
In process of installing I've also found that overclocking gives kernel panic and other errors, so it can not be used at all :( (unless you're programmer and know how to deal with these things, I guess - but I'm just advanced user :) ). 
After that I've tried 8.04. Despite of many bugs, it installed right away and worked in some way...showing part of the desktop on my CRT monitor. wireless USB stick DWL 122 seemed to be working but losing connection every 30secs... Somehow I've managed to download driver for videocard and installed it, but I never managed desktop to display properly. I asked for help again, but again I found not much help. 
Why logon screen and desktop have different resolution? Why not to load ATI driver before logon screen - that should solve all the problems? Why there's no friendly setup program, allowing to configure videocard and video settings and KEEP THEM after restart? It seems that many people have same or similar problem as me.
And back to the topic. I've switched from wireless connection (which was unacceptable unstable) to LAN connection. 
But pages in Firefox (not all, but most) loading WAY slower, than in Maxthon (IE 6). I don't know why but this IS the fact. Many pages, which load in Maxthon almost instantly, need 5-10 seconds to load in Firefox , and this is a HUGE difference.
Actually, it's quiet stange - it's waiting these 5-10 secs and than loads page at once.
So I totally gave up and using XP on this computer now. 

Step #2. I've decided to build second system. I bought all-in-one MB ASUS M2NBP-VN CSM, AMD 6400+ CPU (no need for overclocking this time :)), 2 GB RAM. I've connected again that HDD with Ubuntu 8.04 installation :), and after some fighting managed to start Ubuntu without video driver at first, than downloaded Nvidia driver, installed, restarted...guess what?
Exactly same problem - it doesn't work correctly with my CRT, login screen and main desktop have different resolution, in result main desktop not displayed correctly. I have a bit more visual effects working now than on my first system :) but that doesn't help much...I'm not usyng ANY fancy 3d effects at all, just default simple things (fading and such).
And again, I guess, there's not much help I can find ANYWHERE to make things work properly. I've tried everything I could find - manual configuration etc., but there's no good manual to do this, or I didn't find one...
O yea, Firefox is slow as before, it's sooo disappointing if you go directly from Maxthon...
So what should I do - just stick with XP? I hate it, but there's not much of a choice, I guess? Wait another 5 years, may be Linux becomes usable for average user? Or I'm basically doing something wrong and all problems have simple solutions?

PS. BTW, it took less than 20 min to install XP, and many days for Ubuntu with no success still...now that's difference :)

---

### Post by bodhi.zazen on 2008-07-10
LOL ranchero :lolflag:

You need to be fair to yourself. You are obviously a knowledgeable Windows "power user" but it will take time to migrate to a new OS.

Please compare apple to apples and experts to experts.

The "average" Windows user does not edit and clean the windows registry, in fact many windows users make many mistakes.

I am a Linux Power user and I have my system set up just the way I like. When I am not being lazy :twisted: ; I use Arch Linux and it is tweaked for performance, much in the same way you tweak Windows XP.

Trust me it is faster then XP will ever be. And much less resource hungry, leaving resources for applications rather then the core OS.

The question, for someone like you, :

Are you willing to spend the time to learn Linux ? 

I am just pointing out ~ How many months / years did it take you to learn Windows ? Spend those same months / years on Linux and it will pay off in spades.

---

### Post by ranchero on 2008-07-10
I never really "learned" XP. If I had problem, I went to the Internet, and usually solution was found, just google the problem. Never read manual or anything like that.
Not so with Linux - I asked for help here - but no avail. And there're not much other places to go...
There must be section for hardware, where all hardware would be systemized with description (where possible) "for dummies" how to make it work (I'm sure someone out there has same MB as mine and managed to make video to work, so why not to share?).
Otherwise whole thing becomes useless - if I not able to install and run system, how I can learn about it? Installation and making hardware working - most important things, the rest can be figured out slowly. 
Also, I'm not talking about speed of Ubuntu itself, it seems OK (no complains from me :) ), but speed of Firefox, and I see tons of other complains about this, so there's somthing wrong for sure, somthing has to be improved. 
I also don't really like interface of Firefox, I'm extremely happy with old Maxthon (1.6) - and I'm not alone in this too.

---

### Post by bodhi.zazen on 2008-07-10
> **ranchero said:**
> I never really "learned" XP. If I had problem, I went to the Internet, and usually solution was found, just google the problem. Never read manual or anything like that.

Alrighty then, do the same with linux with the same diligence then.

> [Not so with Linux - I asked for help here - but no avail. And there're not much other places to go...
There must be section for hardware, where all hardware would be systemized with description (where possible) "for dummies" how to make it work (I'm sure someone out there has same MB as mine and managed to make video to work, so why not to share?).
Otherwise whole thing becomes useless - if I not able to install and run system, how I can learn about it? Installation and making hardware working - most important things, the rest can be figured out slowly. 
Also, I'm not talking about speed of Ubuntu itself, it seems OK (no complains from me :) ), but speed of Firefox, and I see tons of other complains about this, so there's somthing wrong for sure, somthing has to be improved. 
I also don't really like interface of Firefox, I'm extremely happy with old Maxthon (1.6) - and I'm not alone in this too.First this is one of the most helpful forums around and we have a ton of very experienced users.

I find it hard to believe you can google and learn to edit your windows registry and not search and learn similar information on Linux.

If you do not like firefox, well there are several alternate browsers available ...

Maxthon is nice, I bet you can run that on wine.

Since your google seems to be broken :

[http://www.google.com/search?q=how+to+maxthon+on+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=how+to+maxthon+on+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

From the first link :

> working copy of latest Maxthon 2 in Ubuntu 8.04[http://forum.maxthon.com/viewthread.php?tid=73017](http://forum.maxthon.com/viewthread.php?tid=73017)

Time spent to find an answer : Less then 30 seconds.

---

### Post by Canis familiaris on 2008-07-10
@ranchero:
Use Opera. It is awesome. I use even if Firefox works very well for me.

---

### Post by ranchero on 2008-07-10
I'd prefer to have native Linux program instead of working under Wine and possible have glitches etc.
But Firefox is not the main point, I wish it to become more smooth and customizable that's all.

The main point - I can not configure video properly.
So try do the same - find in 30secs for me solution "how to configure built-in video on ASUS M2NBP-VM CSM to work properly with CRT monitor CM751 in all resolutions and modes (or at least at 1152x864x85Hz)". Or make Wi-Fi D-Link DWL-G122 to work properly and do not lose connection all the time...I know it's a driver's problem, but it doesn't make any difference to me - if I can't fint how to modify/work around than I can not use it, period.
Or how to overclock system 5% (only 5%!!!) and not to have kernel panic and so on...

---

### Post by ranchero on 2008-07-10
I'd be happy to try them all, and also Compiz, Beryl and everything,  but I need to make system working at first. So right now second computer just sitting and waiting for my decision while I'm writing this from XP...


> **Anurag_panda said:**
> @ranchero:
Use Opera. It is awesome. I use even if Firefox works very well for me.

---

### Post by dracule on 2008-07-10
my desktop w/ vista boots faster than my laptop w/ linux

but granted my desktop has 4gb of ram and doesnt have a 5400rpm hdd.

but linux does boot on my machine to a desktop in 50 sec and i just reinstalled XP w/ no programs to be booted up on start up except the core ones, and that takes 1 min 23 sec.

w/ fluxbox it boots in about 45 seconds.

---

### Post by Bosconian on 2008-07-10
> **dracule said:**
> my desktop w/ vista boots faster than my laptop w/ linux

but granted my desktop has 4gb of ram and doesnt have a 5400rpm hdd.

but linux does boot on my machine to a desktop in 50 sec and i just reinstalled XP w/ no programs to be booted up on start up except the core ones, and that takes 1 min 23 sec.

w/ fluxbox it boots in about 45 seconds.


That is one serious dodgy copy of XP then because mine boots in half the time it takes ubuntu. Seriously.

---

### Post by RiceMonster on 2008-07-10
Vista and Ubuntu both took forever to boot up on my laptop. Never had XP on here, so I can say anything about that, but Arch boots up nice and quickly. Way faster than Ubuntu or Vista.

---

### Post by PCMan on 2008-07-13
> **komputes said:**
> I was confronted by a windows XP user who informed me that Windows works faster than Linux. I have tested two similar Dell XPS m1330, one with Ubuntu and another with Windows to see how they compared when it came to speed.
Let me explain this in technical way. I'll give you the reasons.

What you've seen, is a known issue that get neglected by many Linux fans for quite a long time. Many Linux supporters will say, "No, Linux is much better and faster", even they've never use Windows, or they used a poorly-configured one with a bunch of antivirus tools installed.

Windows xp is much faster and performs better in many areas, if properly-configured. Those who say Linux is much faster, please consider the usability. If you only install a window manager and xterm, that will, of course, much faster and smaller, but the usability? OK, usability is not an issue for terminal lovers since command line is the "best" user interface ever. Of course, "ls -l" is always much faster than Windows Explorer.

If you consider the real world use case of general users:

Try to launch nautilus / konquorer, and compare them with Windows Explorer. Windows performs much better here. Although Linux can provide full access to all kinds of protocols...

It's impossible for nautilus to beat Windows explorer. Windows only recognize file types with filename extension while nautilus tends to read the content of every files from your disk one by one, and do complicated magic matching... Excessive disk I/O is a real design flaw of current Linux desktops. (The file explorer in Vista is much slower, though)

Startup time of Firefox 3 is much shorter and RAM consumption is lower in Windows. Also, the stability under Windows is better. This is not only related to Flash plugin. The Flash plugin for Linux is broken. Rendering speed is generally similar under both systems. A even more interesting experiment: Run Windows version of Firefox with wine. Sometimes, it even outperforms the native Linux version. And, surprisingly, flash plugin for Windows works quite well under wine + Firefox win32. Try it yourself since this is really interesting.

Try Microsoft Office, especially Office 2000. It can offer more than OpenOffice.org while still starts in 3 seconds on an old machine (P III 600 + 256 MB RAM). You can try OpenOffice.org on the same machine. Believe it or not, MS Office performs much better than OpenOffice.org and provide better usability. Even the Windows version of OpenOffice.org can beat its Linux version. I've not test it with wine, but under Windows, it's much faster than its Linux version.

GTK+ programs tends to run much faster under Linux rather than Windows. However, this is the problem of gtk+ win32 port, not the OS. Programs offer the same functionality with those gtk+ apps can perform much better under Windows, and this is true.

Start menu loads much faster under Windows. The reason is quite apparent.
Under Windows, all icons for those applications are in "Start Menu" folder. They just "ls" them, and read their contents. It's not flexible, but it works.

Under GNOME/KDE, however, the menu is generated by parsing several xml files located in different directories, merging the rules together. Then, load some definition files for application categories in many different places, and parse them. Then, read the content of over 100 *.desktop files located in different directories, parse them one by one, and extract their content. Then, do some complicated searching/matching for *.desktop files against the previously parsed xml tree. Some application icons requires that you check the existence of the executable binary first, so this adds even more unnecessary disk I/O. Congratulations, you get the menu layout. (At this point, all the icons in the menu are not yet loaded, and you have to load them later)...

Optionally, you can support some legacy specs used previously in some desktops. So you go through the same procedures, parse them, and merge them to the menu. This should be very "fast", too.

This "great design" well explain the poor performance and the poor usability and why it's so difficult for a general user to add an application icon in that menu and why those menu editors are so limited.

You might already noticed. All of those files are located in different directories / partitions. This can greatly impact the performance on hard disks. Besides, 98% of the desktop files are unused translated strings. After parsing a big desktop file of 100 lines, only 4 lines in it are needed by the desktop environment.

Like it or not, there are many design flaws like this in Linux desktops which make it impossible to outperform Windows. The preceding specs I mentioned are still "getting more complicated". This is "awesome", isn't it?

A even better example is the mime-type system currently used. The database is, again, in large xml files (they really love xml much) located at different places. Someone found this performs poorly, so they decided to do some caches, and split them to smaller parts. That's what in your /usr/share/mime. However, someone still found that the performance of those caches are poor, so they, again, make some more compact binary cache for those caches (cache of caches). Then, those binary caches has different versions, and requires very complicated implementation. The data store in it are in opposite byte order to those in Intel i386 PCs (is this due to political reason since I saw no benefit?). So, additional conversion is needed after those caches are loaded. Then, the descriptions of all those mime-types are still in large xml files in different directories...

God, please tell us how to make things faster in this way... Now can you understand how awesome Linux desktop is? I really hate those specs. Someday I'll tell you how they treat your trash can. It's much more complicated then just moving the file to ~/.Trash. It's a long long spec which is not yet fully implemented.

They really work very hard to make things more complicated. If they don't stop this, the Linux desktop will keep getting slower. Since many developers always own the latest machines, performance is not an issue for them. But, it does matters! How can you spread Linux to Windows users if it doesn't do their previous work well, and also performs worse? That's the same problem Vista have. So, they stop selling Win xp, and you'll be forced to buy Vista. Those Linux distros can stop supporting old packages / fixes, and you'll upgrade whether the new versions are better or not. This is not a real solution...

Another reason why Windows should be faster. Windows will optimize the order of programs stored on your disk according to the frequency they are accessed. Some defragmentation and on-disk caches are done automatically to make programs load faster. They did a lot of optimizations for desktop applications while Linux is a general-purpose system, which is not desktop-centric. Windows xp could be a bad server, but its desktop really outperforms Linux ones with the same usability. (Things like icewm and boxes don't provide equivalent usability, so don't do the comparison with them and argue that Linux is faster)

---

### Post by bodhi.zazen on 2008-07-13
> **PCMan said:**
> </clip rant>

Your comparisons are obviously flawed and I will only point out  a few of the glaring.

First, you are comparing an "optimized" installation of Windows, whatever that means, to Ubuntu. Ubuntu too can be optimized, let alone Linux.

Second, you use subjective terms like "usability", whatever that means.

Third, running Windows without antivirus or without a firewall is not exactly realistic either.

Do you have any kind of benchmark to back up your claims ?

How about this : [http://www.viperlair.com/index.php/articles/windows-vista-vs.-windows-xp-vs.-ubuntu-linux.html](http://www.viperlair.com/index.php/articles/windows-vista-vs.-windows-xp-vs.-ubuntu-linux.html)

That is an out of the box comparison of Ubuntu to XP and Vista. Ubuntu compares quite favorably and in most tests out performs both OS.

There are many benchmarks on the web, most comparing out of the box installations. To be honest, I would say the two OS are roughly equal (Windows XP and Ubuntu).

I would love to see a comparison of the OS 18-24 months post install (both with "regular use" and mantance) and both OS with uptimes of over a month. This is because, in my experience, Windows XP deteriorates quite significantly over time, both with fragmentation on the hard drive as well as with longer and longer uptimes.

Even Microsoft concedes this : 

[http://www.viperlair.com/index.php/articles/windows-vista-vs.-windows-xp-vs.-ubuntu-linux.html](http://www.viperlair.com/index.php/articles/windows-vista-vs.-windows-xp-vs.-ubuntu-linux.html)

While the performance of any OS deteriorates over time, Ubuntu does not deteriorate anywhere near the rate of windows XP and keepind Ubuntu clean and up to date is much much easier.

---

### Post by RiceMonster on 2008-07-13
> Startup time of Firefox 3 is much shorter and RAM consumption is lower in Windows. Also, the stability under Windows is better. This is not only related to Flash plugin. The Flash plugin for Linux is broken. Rendering speed is generally similar under both systems. A even more interesting experiment: Run Windows version of Firefox with wine. Sometimes, it even outperforms the native Linux version. And, surprisingly, flash plugin for Windows works quite well under wine + Firefox win32. Try it yourself since this is really interesting.

GTK+ programs tends to run much faster under Linux rather than Windows. However, this is the problem of gtk+ win32 port, not the OS. Programs offer the same functionality with those gtk+ apps can perform much better under Windows, and this is true.

Wait, I don't understand how it's the fault of GTK+ that it's slower on windows, when it's not the fault of firefox that the Linux version is slower, but the fault of Linux? You even said it runs faster in wine. Explain how that's Linux' fault?


When I think about it, Is comparing the speed of Windows XP to Ubuntu 8.04 really fare? Windows XP is seven years old. It makes a lot more sense to compare it to Vista.

---

### Post by YaroMan86 on 2008-07-13
After all my optimizations... I find Ubuntu is still faster than XP, and DEFINITELY faster than Vista (Back when I still ran it.)

Its not as black and white as "optimization."

XP swaps a lot... Ubuntu never swaps on my machine. I don't have anti-virus running on XP yet.

Everything, and I do mean *everything* worked out of the box for me in Ubuntu. With XP, I have to spend 3 hours acquiring drivers and installing them, upgrading to Service Pack 2, etc.

Boot up time is much faster with XP, though. But install time and run speed is nothing compared to my Linux installation.

Then there's the software I need to install, like Firefox. I don't have to fuss with Ubuntu. Meanwhile I have to convince Internet Explorer that YES I do indeed want to install from this exe I downloaded from [www.mozilla.com](www.mozilla.com).

Not to mention the amount of restarts Windows requires. Install a driver, restart. Updates? Restart. Updates for the updater Restart. Majority of my programs installed, restart.

Restarting should also be considered in this metric for speed. Ubuntu only restarts for two things for me: Kernel updates, and kernel mode driver updates. That's it!

It'll just get worse when I make the (Somewhat wise) move of installing anti-virus software.

I don't like this crap saying Windows is faster than Linux, because my experiences indicate to me that this is just not true.

---

### Post by sink on 2008-07-14
My xp is already infected with virus, so I am forced to use ubuntu :(

---

### Post by sdowney717 on 2008-07-14
XP is slower for me. I dual boot sometimes when I run windows, it is horrible slow. Sure you get the login prompt fairly soon, but it is not booted yet.
It takes about 4 times longer than ubuntu.
Makes no sense to me why some say windows is fast unless maybe they have windows loading nothing except itself.

---

### Post by karellen on 2008-07-14
I use Mandriva 2008.1 and Vista on the same rig, and I can say that in terms of speed they are pretty the same, maybe Mandriva has an edge as I run Compiz and 4 desktops. anyway, the ram consumption is higher in Vista, because of prefetching, not that would be a problem

---

### Post by madjr on 2008-07-15
> **sink said:**
> My xp is already infected with virus, so I am **[COLOR="RoyalBlue"]forced[/COLOR]** to use ubuntu :(

you should be happy ubuntu (linux) exists

you would then be "**[COLOR="RoyalBlue"]forced[/COLOR]**" to be looking at the ceiling right now or forced to boot up into a sea of malware

---

### Post by vahnx on 2008-07-19
The definitive answer to this thread is Ubuntu is slower than XP. Not just 8.04, but even on a fresh install of XP + Ubuntu 7.10 w/ updates & drivers, Ubuntu was still noticeably slower on 2 different machines (desktop & laptop).

---

### Post by sdennie on 2008-07-19
> **vahnx said:**
> The definitive answer to this thread is Ubuntu is slower than XP. Not just 8.04, but even on a fresh install of XP + Ubuntu 7.10 w/ updates & drivers, Ubuntu was still noticeably slower on 2 different machines (desktop & laptop).

Thank you for clearing that up.  I was hoping someone would post some very definitive results like this...

---

### Post by madjr on 2008-07-19
> **vor said:**
> Thank you for clearing that up.  I was hoping someone would post some very definitive results like this...

those are not "*definite results*" just because he says so. There's not even a POLL here.

on an olp PC windows XP is kind of faster THE FIRST 2 or 3 WEEKS

anyway, on modern hardware Ubuntu is faster for me (and yes, i also have XP installed, only 3 months and got to reformat it again... :confused:).

---

### Post by david_lynch on 2008-07-19
> **komputes said:**
> 

-File copy speed (7GB): 
NTFS -> NTFS: 5 Min
ext3 -> ext3: 8 min



ext3 has always felt sluggish to me, and I've done a quick and dirty test comparing ext3, reiser and xfs. Both xfs and reiser blow the doors off of ext3 - I simply timed the copy of a dvd image to each type of file system:

[B]
copy to ext3:
real    7m52.656s
user    0m0.268s
sys     0m20.870s

copy to xfs:
real    3m40.490s
user    0m0.213s
sys     0m12.132s

copy to reiser:
real    3m23.966s
user    0m0.226s
sys     0m19.417s 
[/B]

So, bottom line, if you'd tested using a filesystem other than ext3, linux would have come out appreciably faster than expee.

---

### Post by KIAaze on 2008-07-21
That's interesting.
Then why is ext3 used by default?
Are XFS and ReiserFS not stable enough yet? Do they fragment?
What are the pros and cons of each system?

---

### Post by tdrusk on 2008-07-21
> **KIAaze said:**
> That's interesting.
Then why is ext3 used by default?
Are XFS and ReiserFS not stable enough yet? Do they fragment?
What are the pros and cons of each system?
look at all the features
[http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=220529437#Features](http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=220529437#Features)
:P

---

### Post by madjr on 2008-07-21
> **tdrusk said:**
> look at all the features
[http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=220529437#Features](http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=220529437#Features)
:P

OMG someone added "*murders your wife under*" comparison :o

---

### Post by KIAaze on 2008-07-21
I had looked at that page before posting, but from those tables, I see no reason why one should be used instead of the other, except maybe because of all the unclear parts (question marks) like XIP.

But I googled a bit and this thread has some interesting info:
[http://www.linuxforums.org/forum/linux-newbie/34792-reiserfs-vs-ext3.html](http://www.linuxforums.org/forum/linux-newbie/34792-reiserfs-vs-ext3.html)

> Because it is a tried-and-true and extremely well-tested filesystem. The recovery tools for it are quite good, and since it has been around for so long (ext3 is just the ancient ext2 filesystem with journaling tacked on) it is very well documented and therefore easy to work with.

Having said that, I have seen somewhat of a trend recently among the "desktop" distros to move toward reiserfs. ext3 just has the inertia within the community to keep its spot as the de facto default.
> Moving large numbers of small files has traditionally been where reiserfs shines; on the other side of things, you have xfs, which is especially good at moving very large files.

---

