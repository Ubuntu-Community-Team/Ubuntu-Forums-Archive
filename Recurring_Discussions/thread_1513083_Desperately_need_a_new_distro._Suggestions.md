---
title: "Desperately need a new distro. Suggestions?"
date: 2010-06-18
forum: Recurring Discussions
---

### Post by kaldor on 2010-06-18
I'm driven nuts with most distros right now. What ever happened to "just working" with Linux?

openSUSE: had to fight with everything again, package management too slow (took me an hour to install google chrome- no exaggeration), had to fight to get wireless to work, and sound was messed up a bit on Java.

Ubuntu: Ubuntu's a mess right now. It's not anywhere near as good as it used to be. Nothing but issues starting at 9.10, and 10.04 is a total failure. I had to quickly install Lucid because Debian screwed up on me and now my laptop overheats all the time and is too slow to work with. Feels like I'm running Vista on 512 MB of RAM. Mic and cam stop working too. Endless problems, too much work to fix everything that shouldn't need to be messed with. 

Debian: Tried Debian "stable" but it wasn't stable. Kept aborting the nvidia graphics installation, repositories corrupt, Skype was buggy and had fonts that were unreadable.

Fedora: an update crashed my system.

and so on...


Can anyone recommend a path? I am at the point where I just want to use my computer. I'm sick of having to fight with every single distro I try. It wasn't like this at all back on Gutsy, Hardy, Intrepid. I may just have to downgrade and keep it that way until I can afford another Mac (sadly).

While I love Linux, I'm starting to find too many issues with such simple tasks. I run into a problem on Ubuntu version x, then on the next version those problems are fixed at the cost of stuff not working that was fine before. 

Edit: It's not that I can't fix things, it's that I am sick of fixing things. When I installed Gutsy everything worked flawlessly and I had absolutely no problems. Now I feel like all I am doing is fighting to get everything to work. Java won't work on Chrome in Lucid when it was fine on SUSE and 9.10. Mic and cam stopped working. Flash is choppy. Java applets have no sound. Tried playing Runescape once with a friend and firefox crashed and I needed to type commands to make it work again.. then I loaded runescape and within 5 minutes the screen went white. A game I used to play on WINE now crashes on bootup. Booting the OS takes too long, about 20 seconds longer than previous versions. Icons on the top panel often get messed up and unusable.

I'm losing it :)

---

### Post by Shakz on 2010-06-18
[http://linuxmint.com/](http://linuxmint.com/)

It just works.

---

### Post by kaldor on 2010-06-18
> **Shakz said:**
> [http://linuxmint.com/](http://linuxmint.com/)

It just works.

Had sound issues related to Pulseaudio on the last version. Does Mint 9 mess anything up at all?

Edit: Sorry if I am coming across as pissy tonight, but I feel like using my laptop is such a bloody chore tonight. Nothing but annoyances for the last hour.

---

### Post by Timmer1240 on 2010-06-18
> **Shakz said:**
> [http://linuxmint.com/](http://linuxmint.com/)

It just works.

Thats what ide suggest too Im using Karmic Koala its working great for me I dont wanna upgrade either its just too damn good!

---

### Post by wilee-nilee on 2010-06-18
Your problems are probably hardware issues, and maybe some user experience stuff, can you post your computer specs. Include the graphic chip/card info.
```
lspci
``` in the terminal will give a lowdown.

---

### Post by kaldor on 2010-06-18
> **wilee-nilee said:**
> Your problems are probably hardware issues, and maybe some user experience stuff, can you post your computer specs. Include the graphic chip/card info.
```
lspci
``` in the terminal will give a lowdown.

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

Like I said before, these issues only sprouted beginning after 8.10. I never had to configure anything before. I just want to know why Lucid is especially annoying. I can't really be the only person finding these bugs. It's just not usable for me anymore and I don't have the time/patience to switch to another more advanced distro.

---

### Post by 23dornot23d on 2010-06-18
> **Shakz said:**
> [http://linuxmint.com/](http://linuxmint.com/)

It just works.

+1 also this one is very good ..... new one to me but it will soon become 
popular [Zorin 3]("http://distrowatch.com/table.php?distribution=zorin") ...... 

I run quite a few distro's Mint 8 and Mint 9 too ..... But **Zorin 3 ** will soon be taking the lead as my
main and best Distro ...... 

It works straight off picks up all hardware and its a very productive environment and
runs extremely quickly for me .....

Its quickly coming up the ranks in Distro Watch too .....

---

### Post by kamaboko on 2010-06-18
if 8.10 worked, then go back to it.

---

### Post by kaldor on 2010-06-18
> **kamaboko said:**
> if 8.10 worked, then go back to it.

That's just the thing, I may have to. I just hate using outdated software.

---

### Post by mdtimepc on 2010-06-18
I have tried my share of distros and although I am happy wth 10.04 now I would recommend MEPIS as a very stable OS to try. Based on Debian and it just works with very few problems. I used it in between 9.10 and 10.04. 9.10 gave lots of sound issues for me and MEPIS was a very nice distro. KDE desktop though. Find it at [http://mepis.org](http://mepis.org) and a very friendly and helpful user forum at [http://mepislovers.org](http://mepislovers.org) - Enjoy!!

---

### Post by stmiller on 2010-06-18
I want to like Fedora, but their no-commercial software policy bites for desktop users.

No mp3, dvd, nvidia or ATI video drivers, flash, etc. 

I know all are available via third party repos and random hacks but bleh.

If it wasn't for those things I'd recommend Fedora.

---

### Post by FuturePilot on 2010-06-18
> **kamaboko said:**
> if 8.10 worked, then go back to it.

8.10 is no longer supported.

---

### Post by wilee-nilee on 2010-06-19
This
```
VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
```
Is a known problem, your hardware is a little outdated probably. 

If you were specific about the problems, maybe you have been, and I missed it you could most likely tweak the box to run Lucid with no problems. I have found Maverick to be a good distro even though it is in development, It out of the box had my ati graphic card working. I don't know if this is due to the distro just defaulting to the generic driver as I don't use that laptop much it is just a backup.

---

### Post by FuturePilot on 2010-06-19
> **wilee-nilee said:**
> This
```
VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
```
Is a known problem, your hardware is a little outdated probably. 

If you were specific about the problems, maybe you have been, and I missed it you could most likely tweak the box to run Lucid with no problems. I have found Maverick to be a good distro even though it is in development, It out of the box had my ati graphic card working. I don't know if this is due to the distro just defaulting to the generic driver as I don't use that laptop much it is just a backup.

I have that same exact card in my laptop and it works perfectly fine with the Nvidia driver. I doubt that is the problem.

---

### Post by WinterRain on 2010-06-19
> **kaldor said:**
> 
Edit: It's not that I can't fix things, it's that I am sick of fixing things.

Sounds like your computer isn't as linux compatible as you thought. If it was, you would not be experiencing any issues. *Every* distro works perfectly on my computer. The main reason it works so well for me, is because I built my pc knowing I would be mainly using linux on it. I suggest you do the same, or buy one with linux preinstalled. Why people choose to struggle with OS's is beyond me. I make life easy for myself by buying linux compatible hardware and *never* have any problems. Everything literally works perfect. I see other people still have not learned this yet. 

If I were you, I would give up linux until you got another more compatible computer. Quit trying to fit a square peg into a round hole, and use whatever OS works on it, even if that is windows. Good luck to you.

---

### Post by witeshark17 on 2010-06-19
I agree, hardware issues seem to be involved.

---

### Post by kaldor on 2010-06-19
> **WinterRain said:**
> Sounds like your computer isn't as linux compatible as you thought. If it was, you would not be experiencing any issues. *Every* distro works perfectly on my computer. The main reason it works so well for me, is because I built my pc knowing I would be mainly using linux on it. I suggest you do the same, or buy one with linux preinstalled. Why people choose to struggle with OS's is beyond me. I make life easy for myself by buying linux compatible hardware and *never* have any problems. Everything literally works perfect. I see other people still have not learned this yet. 

If I were you, I would give up linux until you got another more compatible computer. Quit trying to fit a square peg into a round hole, and use whatever OS works on it, even if that is windows. Good luck to you.

The fact is that it *was* compatible with things. It seems like the problems aren't hardware, but bugs with software. I had no problems in the past like I do now. 

I refuse to go back to Windows though; I have no interest in using it. I just want my old good Linux experiences back!

---

### Post by 23dornot23d on 2010-06-19
I run around [16 Operating Systems]("http://sites.google.com/site/23dornot23d/") on one Laptop ..... using 2 USB drives
The only one giving me any problems at the moment is the Lucid Lynx one 
Then after upgrading .... to 10.10 Maverick the same problem

Try **Zorin** ..... and do not be put off by the comments that its been made easy for Windows users ...... its been made easy to use for all users ..... and it works well ........

---

### Post by kamaboko on 2010-06-19
> **kaldor said:**
> That's just the thing, I may have to. I just hate using outdated software.

it's just software.  trust me, when you're on your death bed you won't be thinking about linux.  load it up, and get on with more important things in life.

---

### Post by wilee-nilee on 2010-06-19
The hardware problems are because the manufactures don't write drivers for open source basically.

Really if your tired of tweaking you might find a Linux that works and stick with it or just go MS or Apple. Getting tired of a distro and wanting the latest release and not wanting to do the work to make it work makes no sense, it isn't a magic box. Buy a syatem76 or a computer with Ubuntu or build one that is compatible.

---

### Post by juancarlospaco on 2010-06-19
*Layer 8 Problem*

---

### Post by proggy on 2010-06-19
When i started using Linux quite a few years ago I got lucky all my hardware was detected mostly because i`d buy used IBM machines which loved Linux for some reason.  And there wasn`t that many computer manufacturers i believe like there is today, and just look at graphic cards new ones are released almost very week so its getting harder all the time for every Linux distros.

---

### Post by Shazzam6999 on 2010-06-19
No offense, but if you're not willing to spend a little time tinkering with Linux then maybe Linux is not the OS for you? Linux is trying to support every piece of hardware by every corporation ever made and it's just not realistic to assume all of these things are going to function out of the box. Sure Pulse may not work immediately, tinker with the setting, make a forum post, try Alsa. There's plenty of fixes online to get Runescape to work well; wine tends to take some playing around with, but winehq does an excellent job documenting fixes on a countless amount of programs. Windows isn't for everyone, OS X isn't for everyone, Linux isn't for everyone, BSD isn't for everyone; thankfully we're all blessed with options.

I don't believe there's any reason to recommend a distro because I imagine you'll encounter similar problems in every one of them.

---

### Post by kaldor on 2010-06-19
> **Shazzam6999 said:**
> No offense, but if you're not willing to spend a little time tinkering with Linux then maybe Linux is not the OS for you? Linux is trying to support every piece of hardware by every corporation ever made and it's just not realistic to assume all of these things are going to function out of the box. Sure Pulse may not work immediately, tinker with the setting, make a forum post, try Alsa. There's plenty of fixes online to get Runescape to work well; wine tends to take some playing around with, but winehq does an excellent job documenting fixes on a countless amount of programs. Windows isn't for everyone, OS X isn't for everyone, Linux isn't for everyone, BSD isn't for everyone; thankfully we're all blessed with options.

I don't believe there's any reason to recommend a distro because I imagine you'll encounter similar problems in every one of them.

I used to have no problems tinkering and I love tinkering with my laptop; but I can't stand having to "fight" like I do these days. Maybe Maverick will be the way it used to be for me, but I don't know.

---

### Post by wilee-nilee on 2010-06-19
> **FuturePilot said:**
> I have that same exact card in my laptop and it works perfectly fine with the Nvidia driver. I doubt that is the problem.

Yes it works for you but this is one older bug report. I suspect that a experienced user can get it to work.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/363135](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/363135)

The it works for me, you know the drill right.;)

---

### Post by Shazzam6999 on 2010-06-19
> **kaldor said:**
> I used to have no problems tinkering and I love tinkering with my laptop; but I can't stand having to "fight" like I do these days. Maybe Maverick will be the way it used to be for me, but I don't know.

I feel the same way and I use Arch actually. It can be obnoxious to get working at first, particularly if you're not familiar with it. However, once the system is set up it requires little to no maintenance. Although, the same could be said of any rolling release type distro. I know with Ubuntu my Broadcom wireless card used to work out of the box and apparently 10.04 broke it. So, I don't know what to tell you, but good luck with whatever you go for :).

---

### Post by capricornus on 2010-06-19
When I read the original question, I thought about hardware too. I test a lot of distro's on 6 pc's in the house, and Lynx is - till today - the only one that performs on a 10 year old laptop, a Bestbuy EeePc, a recent giant laptop and 3 desktops with DualCore cpu's.
A collegue of mine presented me an even older laptop (mid '90-ies) that he couldn't handle anymore. I had to go back in my OS-collection and see, with Wolvix Hunter, it revived and even ran OfficeXP thru CrossOver/Wine.
So think about hardware. A blown capacitor could trick you nastily. And think about older software when it gets you where you want to go.

---

### Post by ronnielsen1 on 2010-06-19
Lots of it depends on the computer. I've had computers that loved ubuntu 10.04 and others that preferred Mepis or Linux Mint (Haven't seen any that preferred suse) It seems to me that some computers just run certain distros better. I love ubuntu 10.04 when it's running right but I've seen alot of issues on other computers

---

### Post by Stancel on 2010-06-19
The upgrades are optional. Lucid did not work for me either, I couldn't maintain an Internet connection. But instead of changing distros I just dusted off my 9.04 Live CD and installed it.

---

### Post by cb951303 on 2010-06-19
what you need to do is to check the hardware compatibility before buying the hardware not switching distros

---

### Post by seenthelite on 2010-06-19
If Fedora 13 was working before the update problem, my suggestion is to give it another go. These things happen and solutions are available _[here]("http://forums.fedoraforum.org/")_

---

### Post by snowpine on 2010-06-19
Usually "the problem is between the keyboard and the chair" as they say. You will learn more by sticking with one distro and troubleshooting your problems than by briefly experimenting with a dozen distros. Just my 2 cents. :)

Ubuntu is a fast-moving distro (releases every 6 months) and if you've spent much time on these forums, you've doubtless read lots of "intrepid/jaunty/karmic/lucid is the worst release EVER... updates broke my video/wireless/webcam/etc." testimonials. I guess maybe regressions like that are part and parcel of Ubuntu's "bleeding edge" development model, I don't know. Anyhow, if you're of the "install it once and forget about it" mentality then you probably would be best with either a rolling release distro (Arch, Sidux, etc.) or an enterprise distro (Red Hat--expensive and not the latest software, but great hardware support and a 7-year life cycle). Ubuntu releases too often to be a "I just want it to work" distro over the long haul, in my opinion; I consider Ubuntu to be more of a "showcase for the latest Linux innovations" distro IMHO. ;)

---

### Post by MisfitI38 on 2010-06-19
I use Arch.
I have rarely, if ever, recommended it on these forums. However, it might just give you what you are looking for in this case because its installation procedure is a well documented step-by-step method.
You will be able to get the system working 'a little at a time' until you have a fully usable and custom system.
If there are any showstoppers along the way, they must be addressed before moving on to the next step, affording you some assurance of functionality before continuing.

You may have tried it before and hated it, I don't know-- it's not for everyone and some Ubuntu users truly dislike Arch and its methodology.
However, with an open minded approach, you might actually find what you are looking for here.
Good luck wherever you end up.
Enjoy.

---

### Post by ubunterooster on 2010-06-19
using > **ubunterooster said:**
>  I have Mint on my  SSD

(in case you wondered the 2TB drive is: Ubuntu  10.04, Ubuntu10.10, Mandriva, PCLOS, Fedora, Slitaz, Igelle, Arch,  Gentoo, and may later grow)

---

### Post by Linuxforall on 2010-06-19
What an irony that Mint and Zorin are Ubuntu to the core with different wrapper and nothing more, all files, structure and everything else is same but somehow placebo effect here works so well, it Ubuntu don't work, MINT will, LOL! Anyways considering your situation, I would suggest you switch to offerings from MS.

---

### Post by kelvin spratt on 2010-06-19
> **MisfitI38 said:**
> I use Arch.
I have rarely, if ever, recommended it on these forums. However, it might just give you what you are looking for in this case because its installation procedure is a well documented step-by-step method.
You will be able to get the system working 'a little at a time' until you have a fully usable and custom system.
If there are any showstoppers along the way, they must be addressed before moving on to the next step, affording you some assurance of functionality before continuing.

You may have tried it before and hated it, I don't know-- it's not for everyone and some Ubuntu users truly dislike Arch and its methodology.
However, with an open minded approach, you might actually find what you are looking for here.
Good luck wherever you end up.
Enjoy.

+1 i'm no geek and Arch is stable light on resources with the best support and Wiki

---

### Post by mamamia88 on 2010-06-19
i haven't read the entire thread but has anyone suggested sabayon?  it worked right out of the box with all my drivers.

---

### Post by Penguin Guy on 2010-06-19
Dual boot between 8.10 and a newer version. When a new version of Ubuntu comes out I always dual boot between the new one and the old one incase I change my mind. If a version of Ubuntu is particularly bad, I may skip it altogether. Don't worry, you're just having an unlucky streak, you may find that 10.10 works flawlessly for you.

---

### Post by stuman on 2010-06-19
The "problem" with Ubuntu is when an "upgrade" ceases to support the hardware that has been running flawlessly.  Is Canonical not interested in backward compatibility?  

I am running 8.04 now on my Toshiba A135 and dread having to leave Ubuntu.  I tried 9.04 but had to go back since my critical e-mail software...Evolution...ceased working.  The "new" data structures behind it kept locking up.  I can't even get 10.04 to boot from cd on my old desktop, where I would like to try it out before clobbering my mission critical main computer.  I use Windows in VM's when I have to for client compatibility things, but haven't used it as the main os for years...it is just a bit disheartening that things are degrading with each new release, instead of improving.

> **Shazzam6999 said:**
> No offense, but if you're not willing to spend a little time tinkering with Linux then maybe Linux is not the OS for you? Linux is trying to support every piece of hardware by every corporation ever made and it's just not realistic to assume all of these things are going to function out of the box. Sure Pulse may not work immediately, tinker with the setting, make a forum post, try Alsa. There's plenty of fixes online to get Runescape to work well; wine tends to take some playing around with, but winehq does an excellent job documenting fixes on a countless amount of programs. Windows isn't for everyone, OS X isn't for everyone, Linux isn't for everyone, BSD isn't for everyone; thankfully we're all blessed with options.

I don't believe there's any reason to recommend a distro because I imagine you'll encounter similar problems in every one of them.

---

### Post by 23dornot23d on 2010-06-19
> **Linuxforall said:**
> What an irony that Mint and Zorin are Ubuntu to the core with different wrapper and nothing more, all files, structure and everything else is same but somehow placebo effect here works so well, it Ubuntu don't work, MINT will, LOL! Anyways considering your situation, I would suggest you switch to offerings from MS.

What is even more of an irony is that the hardware picks up first time in Zorin and Mint.

What also is an Irony is that the two Distro's above have also included the codecs and added extras for video and flash to work straight off.

The final thing is that they are developed to suit people that want to use there OS for work
as opposed to tinkering with it all the time .....

and the final thing they have their  origins based on Ubuntu and [I]Debian .....

UBUNTU Maverick ..... is next ......
At present it still removes my sound .... where none of the above do ......
This happened in Lucid it also happened in Jaunty .... but thats not really the issue ....

I see comments that the USER may have a hardware problem or it may be a User problem or that the is trying too many distributions to focus on one ...... 

Maybe there is a problem with Lucid .....

There is a deeper problem ..... people that use one system alone blindfold themselves
from the reality that other people can take this system ... refine it and make it better.

and the music played on ...... :guitar: .......... as the system continued to get more
and more users highlighting similar things ......... that could be improved ...

To help the majority of people ....... using UBUNTU .... 

and most of all LINUX **USERS** 


[/I]

---

### Post by wojox on 2010-06-19
I dual boot Ubuntu 10.10 Gnome and openSUSE 11.2 KDE. Never had a problem, Try using the CLI to download and install. Are you wireless?

---

### Post by WinterRain on 2010-06-19
> **kaldor said:**
> The fact is that it *was* compatible with things. 

Believe it or not, hardware can degrade over time. Some computers last for many years, and others start acting funky after only a couple years or less. I strongly suggest getting a new computer if you can.

---

### Post by Timmer1240 on 2010-06-19
If you end up buying a computer Ide get one from system 76 Im hearing really good things about em and prices are ok too!

---

### Post by WinterMadness on 2010-06-19
Sometimes your issues may be related to the quality of the ISO

In any event, try mandriva

---

### Post by kingrobdun on 2010-06-19
I recommend Red hat and fedora. If you keep on having problems, you might need a new computer.

---

### Post by Ewingo401 on 2010-06-19
PCLinuxOS is very good about "just working".

---

### Post by Dustin2128 on 2010-06-19
I actually *did* have similar problems; If I were you I'd swap to a minimalist distro like arch or a purist distro like slack. Not a problem since I swapped to slackware 13.1.

---

### Post by Primefalcon on 2010-06-19
My advice use what works for you, Linux IMO is the best choice but if your hardware is not supported and you cant get supported hardware, use what works, aka Windows (you prob got a copy with your computer anyhow)

---

### Post by MasterNetra on 2010-06-19
> **MisfitI38 said:**
> I use Arch.
I have rarely, if ever, recommended it on these forums. However, it might just give you what you are looking for in this case because its installation procedure is a well documented step-by-step method.
You will be able to get the system working 'a little at a time' until you have a fully usable and custom system.
If there are any showstoppers along the way, they must be addressed before moving on to the next step, affording you some assurance of functionality before continuing.

You may have tried it before and hated it, I don't know-- it's not for everyone and some Ubuntu users truly dislike Arch and its methodology.
However, with an open minded approach, you might actually find what you are looking for here.
Good luck wherever you end up.
Enjoy.

Arch Makes up for its trouble freeness (post installation) with its time consuming installation. Its most certainly not for newcomers or those who just want to install with little input as possible. Too much work personally involved in its installation, which is probably the main reason it won't hit the big time. Arch is indeed for geeks and tinks.

---

### Post by snowpine on 2010-06-19
> **MasterNetra said:**
> Arch Makes up for its trouble freeness (post installation) with its time consuming installation. Its most certainly not for newcomers or those who just want to install with little input as possible. Too much work personally involved in its installation, which is probably the main reason it won't hit the big time. Arch is indeed for geeks and tinks.

You can do an Arch install in an afternoon. Make a pot of coffee, carefully follow the instructions in the Arch Beginner's Guide, and you'll be fine. It really is not as scary as you think. Whether or not the process is *enjoyable* depends on your personality. Some people like driving stick and some prefer automatic. :)

---

### Post by admiralspark on 2010-06-19
Well, there are pro's and con's to everything. 

My recommend? You said basically that the 5 biggest distro's didn't work for you. Everyone is recommending the big, mainstream stuff, and so I'll jump off my Mint stage and onto another: Puppy Linux.

Not exactly a 'normal' distro, puppy linux in it's entirety does not exceed 60mb (and 128mb for the newest, which when you look at what comes with it is amazing). Puppy is the _**ONLY**_ distro that I have ever used that worked on every computer I tried it on, with zero hardware issues. OpenSUSE failed me with it's screwed-up permissions and sound issues OOTB, Ubuntu 10.04 refuses to work with this crappy intel 8xx card (which had no problems in 9.10, 9.04, 8.04.....) and even Mint 8 (9.10-based) had to have permissions changed for my only account so that I could file-share. 

Puppy Linux, well, just works.

When I installed it to my USB (it's live and dedicated, so it will remember and save all changes you make), it worked right out of the box. It seems to support all manner of odd hardware, including being the ONLY linux distro that worked with my broadcomm 4318 wireless in the ol' Compaq right away. It has like 40 million 'wizards' that guide you through setting everything up, step-by-step, in a simple and easy-to-understand way. It's not only small but feature-packed: there is NOTHING that the big distro's can do that it can't, especially with the new Puppy 5.0 (which is based on the applications of ubu 10.04-it downloads them from the repo, recompiles, and installs a now lightweight version of the same programs). It's clean, clear and easy to navigate, and will work on any computer you use it on--for example, I can boot it on my laptop here, install some programs and tweak my wireless settings, shutdown/unplug, move to and boot it on the ol' Dell desktop, and it automatically loads the right drivers for the Dell instead of this IBM laptop and remembers all the wireless settings, plus my programs/documents et all still work. 

/end_puppy_advertisement.

Oh, and puppy is even easy to compile in, which is just super for the source-junky like me. Everything is graphical, no crawling around a terminal like I have to on the big distros. 

I haven't tried Compiz in Puppy yet, because I haven't looked into it much yet, but I hear even that works. And wine apparently works fine also. 

Try it. It will probably take you 5 minutes to download and 30 seconds to put on a USB with unetbootin, and it just works. :-)

Oh, and going back to an earlier version of a distro is okay, because at least then stuff will work.

---

### Post by ubunterooster on 2010-06-19
Assuming you just want to try something new: [http://www.igelle.com/](http://www.igelle.com/)

It does not use the gnome, kde/ xfce/ fluxbox/...desktop. It uses the Esther Desktop, brand new idea, fast, not based on anything else. [Sarcasm]And most importantly, I like it [/sarcasm]

---

### Post by Timmer1240 on 2010-06-19
System 76 sounds like you need some newer hardware too!

---

### Post by wojox on 2010-06-20
> **ubunterooster said:**
> Assuming you just want to try something new: [http://www.igelle.com/](http://www.igelle.com/)

It does not use the gnome, kde/ xfce/ fluxbox/...desktop. It uses the Esther Desktop, brand new idea, fast, not based on anything else. [Sarcasm]And most importantly, I like it [/sarcasm]

Very interesting link. :p

---

### Post by HappinessNow on 2010-06-20
[PC-BSD]("http://www.pcbsd.org/") (not Linux but you wouldn't know it) :p

---

### Post by joshmuffin on 2010-06-20
+1 linux mint - I have been trying to find problems and I can't

---

### Post by Linuxforall on 2010-06-20
> **23dornot23d said:**
> What is even more of an irony is that the hardware picks up first time in Zorin and Mint.

What also is an Irony is that the two Distro's above have also included the codecs and added extras for video and flash to work straight off.

The final thing is that they are developed to suit people that want to use there OS for work
as opposed to tinkering with it all the time .....

and the final thing they have their  origins based on Ubuntu and [I]Debian .....

UBUNTU Maverick ..... is next ......
At present it still removes my sound .... where none of the above do ......
This happened in Lucid it also happened in Jaunty .... but thats not really the issue ....

I see comments that the USER may have a hardware problem or it may be a User problem or that the is trying too many distributions to focus on one ...... 

Maybe there is a problem with Lucid .....

There is a deeper problem ..... people that use one system alone blindfold themselves
from the reality that other people can take this system ... refine it and make it better.

and the music played on ...... :guitar: .......... as the system continued to get more
and more users highlighting similar things ......... that could be improved ...

To help the majority of people ....... using UBUNTU .... 

and most of all LINUX **USERS** 


[/I]

Including codecs is done automatically when you play a movie in Ubuntu but that don't make the hardware in Zorin or MINT work, its Ubuntu that does make it work there as well.

---

### Post by Dekrus on 2010-06-20
How about Crunchbang Linux? It'll be lovable to be on your PC.

---

### Post by smellyman on 2010-06-20
> **ubunterooster said:**
> Assuming you just want to try something new: [http://www.igelle.com/](http://www.igelle.com/)

It does not use the gnome, kde/ xfce/ fluxbox/...desktop. It uses the Esther Desktop, brand new idea, fast, not based on anything else. [Sarcasm]And most importantly, I like it [/sarcasm]

I like Igelle and I applaud anybody who innovates as much as they have....

---

### Post by t1nm@n on 2010-06-20
hey man... debian lenny is the most stable version i've seen so far...even challenging ubuntu.

problems like drivers and stuff are well documented through out the internet...

how ever if you want simplicity i suggest

Zenwalk 

crunchbanglinux

---

### Post by t1nm@n on 2010-06-20
AROS (this is an amiga based OS) by my specs it is no where near as mature as linux but its a good vm tryoutand i love it...

ReactOS.:KS

Hymera.

---

### Post by Shining Arcanine on 2010-06-20
> **kaldor said:**
> That's just the thing, I may have to. I just hate using outdated software.

If you dislike outdated software so much, then you are using the wrong distribution. Using Ubuntu Linux guarentees that you are using outdated software, because it is a static distribution. You would be happier with a rolling distribution like Gentoo Linux:

[http://www.gentoo.org/](http://www.gentoo.org/)

Gentoo Linux is always up to date if you use software from its testing tree:

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=3#doc_chap1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=3#doc_chap1)

Some other options for rolling distributions are Sidux Linux and Arch Linux.

[http://www.sidux.com/](http://www.sidux.com/)
[http://www.archlinux.org/](http://www.archlinux.org/)

They both differ from Gentoo Linux in that they are binary distributions, but that has the advantage of quicker installation times, with the disadvantage of losing the ability to control how things are compiled on a system-wide basis and also the ability to fix things with ease when they core library updates break binary compatibility. It is a double-edged sword.

At the same time, I think that your issue is that  your hardware is failing. Computer hardware is known as memoryless in statistics, which means that if it is working, it has the same chance it had of failing that it had on day 1. It has likely encountered such a failure.

> **kaldor said:**
> The fact is that it *was* compatible with things. It seems like the problems aren't hardware, but bugs with software. I had no problems in the past like I do now. 

I refuse to go back to Windows though; I have no interest in using it. I just want my old good Linux experiences back!

Wanting good experiences might mean you would prefer an OS where all development is done within a single tree. Here are some suggestions:

[http://www.freebsd.org/](http://www.freebsd.org/)
[http://www.dragonflybsd.org/](http://www.dragonflybsd.org/)

Since all of the development for every piece of software on the system is done in-house, you get a higher quality result. Software developed by third parties is available via ports in FreeBSD and since DragonFlyBSD is a fork of FreeBSD, I assume that is true for it as well.

---

### Post by SunnyRabbiera on 2010-06-20
Wait for openSUSE 11.3 out in a few weeks, it may work better then 11.2

---

### Post by Shining Arcanine on 2010-06-20
> **SunnyRabbiera said:**
> Wait for openSUSE 11.3 out in a few weeks, it may work better then 11.2

The release candidate is already out. Assuming he were to use that, when the final version is released, he could just upgrade via the OpenSUSE package manager. There would be no need to wait.

The original poster said that he wants "up to date" software, so my recommendation is that he use a rolling distribution.

---

### Post by SunnyRabbiera on 2010-06-20
> **Shining Arcanine said:**
> The release candidate is already out. Assuming he were to use that, when the final version is released, he could just upgrade via the OpenSUSE package manager. There would be no need to wait.

The original poster said that he wants "up to date" software, so my recommendation is that he use a rolling distribution.

True, though RC's can be buggy sometimes when updating to main.

---

### Post by ssri on 2010-06-20
> **Shining Arcanine said:**
> Some other options for rolling distributions are Sidux Linux and Arch Linux.

[http://www.sidux.com/](http://www.sidux.com/)
[http://www.archlinux.org/](http://www.archlinux.org/)

They both differ from Gentoo Linux in that they are binary distributions, but that has the advantage of quicker installation times, with the disadvantage of losing the ability to control how things are compiled on a system-wide basis and also the ability to fix things with ease when they core library updates break binary compatibility. It is a double-edged sword.

I cannot speak for sidux, but if you want to compile everything a la gentoo in arch, then there is abs and makepkg.  If you want to set your CFLAGS, then you can edit /etc/makepkg.conf.  Arch gives users the freedom to either quickly install pre-compiled packages through pacman (like apt-get), build them from sources or both.  The nice thing is that you can manage them all from pacman.

---

### Post by Shining Arcanine on 2010-06-20
> **ssri said:**
> I cannot speak for sidux, but if you want to compile everything a la gentoo in arch, then there is abs and makepkg.  If you want to set your CFLAGS, then you can edit /etc/makepkg.conf.  Arch gives users the freedom to either quickly install pre-compiled packages through pacman (like apt-get), build them from sources or both.  The nice thing is that you can manage them all from pacman.

Compilation is a second class citizen on Arch Linux. You cannot arbitrarily flip on and off entire program features and have the package manager automatically take care of things for you like you can on Gentoo Linux. For that, you need USE flags, which do not exist on Arch Linux.

---

### Post by kaldor on 2010-06-21
I am on Windows 7 right now. I decided to give it a spin. Decided to give it an actual test run since I haven't used it on my own yet.

The verdict...

Not for me. I tried it with an open mind, but it really isn't for me. I pirated it to try it out (oh no!) but not like I'm gonna keep it. 

I know about Gentoo etc but I read that it's possible to mess up and I don't feel like spending a huge lot of time configuring everything. 

But, if it's a case where once I set it up I'm good to go, I'll go for Gentoo. How well would it support my laptop? It's an HP Pavilion dv2700 Entertainment Notebook with 2 GB RAM and Nvidia geforce 8400m graphics.

---

### Post by NightwishFan on 2010-06-21
This may not be of much help and I may have mentioned this previously, but be sure to check if the issue is known upstream. Ubuntu actually tends to be quite conservative with some things but problems still occur.

---

### Post by note32 on 2010-06-21
if its hardware your worried about why don't you try out Mandriva fantastic distro

---

### Post by ubunterooster on 2010-06-21
I liked mandriva; If only it did not make the speakers start an awful screech whenever on, I might be using that. Don't get me wrong, it's pretty and great and I want to try the next version, but I am skeptikal of it's ability to detect my hardware

---

### Post by 2cute4u on 2010-06-21
> **23dornot23d said:**
> +1 also this one is very good ..... new one to me but it will soon become 
popular [Zorin 3]("http://distrowatch.com/table.php?distribution=zorin") ...... 

I run quite a few distro's Mint 8 and Mint 9 too ..... But **Zorin 3 ** will soon be taking the lead as my
main and best Distro ...... 

It works straight off picks up all hardware and its a very productive environment and
runs extremely quickly for me .....

Its quickly coming up the ranks in Distro Watch too .....

Zorin is pretty solid, but it's ugly as ****, and the default user interface is a bit disorienting.  If you've used Linux enough to how to modify things, this is a good choice, but I'd never recommend it to a beginner.

---

### Post by NightwishFan on 2010-06-22
I took a look at zorin and it gave me a chuckle. :D

---

### Post by dzon65 on 2010-06-22
I always have slitaz lying around.It has never failed.Besides,the whole tryout will take you 20 minutes.That is download,burn and install.The xorg version only needs some xorg config editing.The xvesa version works out of the box.

---

### Post by mister_p_1998 on 2010-06-22
> **stuman said:**
> 

I am running 8.04 now on my Toshiba A135 and dread having to leave Ubuntu.  .

At last! someone who feels the same way as me... I run Hardy on my main machine at home, and only upgraded to that when Dapper expired. It works flawlessly and is working 18 hours a day merrily running its cron jobs to its hearts content. I installed Lucid on my work machine when Intrepid expired and its been a lot of hair-pulling for things that worked fine on Intrepid. What worries me more is that Lucid is an LTS! OK be cutting edge if you must with six-monthly releases, but it fails to inspire me with confidence when an LTS version falls over straight out of the box. I'm hoping they fix all these bugs when Hardy expires, otherwise I may have to consider running my outdated Hardy without security updates... at least it still works! On the same topic, I was wondering if I could switch my repos over when Hardy expires after its three-year run and use the server version for security updates, is that workable?
Steve

---

### Post by jwbrase on 2010-06-22
> **kaldor said:**
> The fact is that it *was* compatible with things. It seems like the problems aren't hardware, but bugs with software. I had no problems in the past like I do now. 

I refuse to go back to Windows though; I have no interest in using it. I just want my old good Linux experiences back!

How long ago did you buy it? Old machines are only going to be compatible with new software for so long. 

Also, regarding your comments on wanting the latest versions of various software, do keep in mind that "stable" and "up to date" often go against each other, as there hasn't been time yet to work all the bugs out of the very newest stuff.

---

### Post by 2cute4u on 2010-06-22
> **mister_p_1998 said:**
> At last! someone who feels the same way as me... I run Hardy on my main machine at home, and only upgraded to that when Dapper expired. It works flawlessly and is working 18 hours a day merrily running its cron jobs to its hearts content. I installed Lucid on my work machine when Intrepid expired and its been a lot of hair-pulling for things that worked fine on Intrepid. What worries me more is that Lucid is an LTS! OK be cutting edge if you must with six-monthly releases, but it fails to inspire me with confidence when an LTS version falls over straight out of the box. I'm hoping they fix all these bugs when Hardy expires, otherwise I may have to consider running my outdated Hardy without security updates... at least it still works! On the same topic, I was wondering if I could switch my repos over when Hardy expires after its three-year run and use the server version for security updates, is that workable?
Steve

If you think about it, 10 years from now Hardy will still run as well on your current machine, as it does now.  I don't think it really makes that much difference that they will stop officially supporting it, just make sure you have a dvd or something with everything in the repository.

---

### Post by squiddy on 2010-07-01
try arch. thumbup for arch.

---

### Post by dE_logics on 2010-07-02
For a bit experienced user, Sabayon is the best.


That's an admin's word who has served many PCs.

---

### Post by shane2peru on 2010-07-17
> **dE_logics said:**
> For a bit experienced user, Sabayon is the best.


That's an admin's word who has served many PCs.

Thank you!!!  I accidentally stumbled across this thread, trying to continue tweaking my Ubuntu install so that it doesn't overheat.  Long story short, I installed Sabayon, today, very very impressed as a first impression.  No overheating!  Many distro's don't even make it through the install process before overheating.  Very impressed with Sabayon.

Shane

---

### Post by jerenept on 2010-07-17
yay Sabayon! it is the only ditro that I stayed withfor more than 10 mins.

Definitely recommended.
Using now.

---

### Post by Shining Arcanine on 2010-07-17
> **shane2peru said:**
> Thank you!!!  I accidentally stumbled across this thread, trying to continue tweaking my Ubuntu install so that it doesn't overheat.  Long story short, I installed Sabayon, today, very very impressed as a first impression.  No overheating!  Many distro's don't even make it through the install process before overheating.  Very impressed with Sabayon.

Shane

My recommendation is Gentoo Linux, although since Sabayon Linux is based on Gentoo Linux, it should be good too. I am glad to hear that you are happy with Sabayon.

---

### Post by shane2peru on 2010-07-20
> **Shining Arcanine said:**
> My recommendation is Gentoo Linux, although since Sabayon Linux is based on Gentoo Linux, it should be good too. I am glad to hear that you are happy with Sabayon.

I have always liked Gentoo, and always hated the complex setup, and compiling time.  Great distro though.

Shane

**EDIT:**  And probably one of the best documented distros around.

---

