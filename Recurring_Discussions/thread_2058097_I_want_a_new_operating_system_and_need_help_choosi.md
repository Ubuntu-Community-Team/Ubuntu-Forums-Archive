---
title: "I want a new operating system and need help choosing one."
date: 2012-09-14
forum: Recurring Discussions
---

### Post by tahdas on 2012-09-14
Hi, 
I recently got a free computer from a church school and I got hooked up to the Internet. It's slow and still use window XP I'm looking to change operating systems and thinking about a Linux based OS. I want s,etching uncommon but not completely ubscure. I want something free.
I'm sorry if this the wrong section to post in.
Thanks,
tahdas

---

### Post by Bucky Ball on 2012-09-14
Welcome.

What do you want to do with the computer? Your needs partly dictate which OS is best. That and the specs of your machine (please supply). You are on a Ubuntu forum so you will get advice mostly about Ubuntu and its derivatives here. If you want to know more about what's out there try Distrowatch:

[http://distrowatch.com/](http://distrowatch.com/)

There are literally hundreds of Linux distros. Ubuntu is one of the best supported with one of the liveliest, robust and most helpful communities. I advise diving in and doing some research on Linux, Open Source and what it's all about. All Linux OSs are free (as is knowledge, or it should be). That is part of the ethos/idea.

PS: Descriptive thread titles will yield more help and support. You can change by editing the first post then clicking 'Go Advanced'. ;)

---

### Post by tahdas on 2012-09-14
> **Bucky Ball said:**
> What do you want to do with the computer? Your needs partly dictate which OS is best. That and the specs of your machine (please supply). You are on a Ubuntu forum so you will get advice mostly about Ubuntu and its derivatives here. If you want to know more about what's out there try Distrowatch:

[http://distrowatch.com/](http://distrowatch.com/)

There are literally hundreds of Linux distros. Ubuntu is one of the best supported with one of the liveliest, robust and most helpful communities.

 I want to be able to game (I'm not a big gamer but when I want to play a game I want it to work!), write, serf the web, video edit,  photo edit.  By the way the computers a dell (no pun intended).I dont know were to find the specs. As you can tell I'm not a person who knowns alot about computers!
Thanks
Tahdas

---

### Post by Bucky Ball on 2012-09-14
Which games? If they are Windows games chances are they won't work in Ubuntu and if they do you are going to need to install Wine to do it, and there's no guarantee they will work with that either. Thoroughly check this:

[http://www.winehq.org/](http://www.winehq.org/)

The rest is easy and no problem (depending on how pro you want to go with your video editing but there are apps out there, Kino and Openshot to name a couple). 

Write: Openoffice or Libreoffice (also contains Draw, spreadsheet, presentation, etc)
Photo edit: The Gimp; brilliant!
Surf Web: Any number of browsers but Firefox is the default.

These apps will work in many Linux distros (and Win and Mac), not just Ubuntu and derivatives. 

If you look in System Monitor you will see the Ubuntu version, processor and amount of RAM. You can also open a terminal (Applications>Accessories>Terminal) and paste this in:
```

sudo lspci
```That will show you what's in the box. ;)

---

### Post by tahdas on 2012-09-15
> **Bucky Ball said:**
> Which games? If they are Windows games chances are they won't work in Ubuntu and if they do you are going to need to install Wine to do it, and there's no guarantee they will work with that either. Thoroughly check this:

[http://www.winehq.org/](http://www.winehq.org/)

The rest is easy and no problem (depending on how pro you want to go with your video editing but there are apps out there, Kino and Openshot to name a couple). 

Write: Openoffice or Libreoffice (also contains Draw, spreadsheet, presentation, etc)
Photo edit: The Gimp; brilliant!
Surf Web: Any number of browsers but Firefox is the default.

These apps will work in many Linux distros (and Win and Mac), not just Ubuntu and derivatives. 

If you look in System Monitor you will see the Ubuntu version, processor and amount of RAM. You can also open a terminal (Applications>Accessories>Terminal) and paste this in:
```

sudo lspci
```That will show you what's in the box. ;)

I'll mostly be playing online stuff, lots of minecraft! I would probably download chrome. For writing I'll use google docs and will probably upgrade when I download a new OS.
Like I said I'm a complete noob and was unable to follow you derections. If you could tell me exactly wre to go from the start button. Remember I'm using windows XP.
Thanks so much with out you smart nerds (is that term ok? I meen no disrespect by it) I'd would be lost.
Thanks again, 
tahdas

---

### Post by cortman on 2012-09-15
Someone seriously needs to write a "What distro should I use" sticky/wiki/blog post... hm, challenge accepted?

To OP; Lubuntu, Bodhi LInux, or Crunchbang.

---

### Post by Wim Sturkenboom on 2012-09-15
In WinXP, right click 'my computer'and choose 'properties'. It will tell you the processor (e.g. Intel Celeron @1.4GHz, AMD Athlon ...) and the amount of ram (e.g. 512MB).

That will (more or less) define the capabilities of the machine.

Next click on the tab 'device manager' and click on VGA (or something like that); this will tell you the video chipset (something like ATI ..., nVidia ... or Intel ...).

> 
If you look in System Monitor you will see the Ubuntu version, processor and amount of RAM. You can also open a terminal (Applications>Accessories>Terminal) and paste this in:

Just to make sure for OP; you need to boot from a live CD or USB (or have linux installed). A good choice for a live CD / USB for now would be lubuntu.

> 
I want s,etching uncommon but not completely ubscure. I want something free.

You're on the wrong forum as Ubuntu is not really uncommon :) But you're welcome to the club anyway and we will try to advice to get you the best solution.

---

### Post by apochry on 2012-09-15
I'd say you should try Ubuntu, or maybe Xubuntu if the your box is weaker. But check the hardware first, seriously.
Than make yourself a live cd or usb and try Ubuntu or what you've chosen. The live cd/usb will let you try the distro (not at full speed, though) without making any changes to the existing setup on your laptop. 
how to make live USB --> [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Good luck!

- Christo

---

### Post by snowpine on 2012-09-15
You should keep XP and set up a "dual boot" with Linux. This will allow you to boot into Windows to play Windows games and use Windows apps, or boot to Linux to play Linux games and Linux applications. 

I do not recommend that a first-time Linux user wipe a working Windows install; just in case you don't like Linux, it will be good to have the fallback.

---

### Post by tahdas on 2012-09-15
> **Wim Sturkenboom said:**
> In WinXP, right click 'my computer'and choose 'properties'. It will tell you the processor (e.g. Intel Celeron @1.4GHz, AMD Athlon ...) and the amount of ram (e.g. 512MB).

That will (more or less) define the capabilities of the machine.

Next click on the tab 'device manager' and click on VGA (or something like that); this will tell you the video chipset (something like ATI ..., nVidia ... or Intel ...).


Just to make sure for OP; you need to boot from a live CD or USB (or have linux installed). A good choice for a live CD / USB for now would be lubuntu.


You're on the wrong forum as Ubuntu is not really uncommon :) But you're welcome to the club anyway and we will try to advice to get you the best solution.

Thanks I'm not curently at my house so I can't check but I will when I come home. 
Isn't there more uncommon Ubuntu variants? Here's a couple a that caut my eye: zorin I'd like to no more about this one, epidemic this one is probably the name that got me, Crunch bang I'd like to know more about this one to, or maybe just classic Ubuntu. Like I said theese are the ones the caught my I'd like something good but not overused.
So give OS options or sugestion if u can.
Thanks
tahdas

---

### Post by Bucky Ball on 2012-09-15
Best way to find out more is to visit their homepages and check out their forums. For instance:

[http://zorin-os.com/](http://zorin-os.com/)

Remember: The more obscure the less support generally. Crunchbang seems quite popular, Zorin gets used, Epidemic I've never heard of, but that means nothing. There's a lot of distros out there. ;)

One fairly common philosophy around here is whatever works for the user. It is a matter of finding the distro and flavour that suits the way you work (and that may be XP for some) and works ok with your machine specs. The other option is to customise an existing distro to something you like. Xubuntu is great for this. Or you can try a minimal install and install ONLY the apps you want, nothing else, and this includes the desktop environment. It's up to you. 

Of course, this means you need to do a fair amount of playing around before you know what you want. List what you need then research if the distro can deliver. Horses for courses ...

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by snowpine on 2012-09-15
Why do you want an "uncommon" operating system instead of a popular operating system with a large friendly community to help answer your questions? Visit Zorin forums and CrunchBang forums and see for yourself whether they are as active as this forum. :)

---

### Post by vasilbelarus on 2012-09-15
You should try Ubuntu first. It`s simple and very user-frendly and at the same time works stable.
Read documentation before install any OS. Good luck.

---

### Post by QIII on 2012-09-15
I'm going to echo two things I've seen in the thread:

1.  Use what works for you.
2.  Try different Linux distributions.

I am not an Ubuntu apologist, so I won't say you should use it.  It may not be what you want.  I will suggest trying it.

Although it is very slow, a Live CD wlll at least give you the opportunity to poke around and see if any particular distribution is even attractive to you.

A virtualization solution (such as Virtual Box) will allow you a speedier experimental environment, but you machine has to support virtualization and the "hardware" you would be using is the hardware abstraction layer provided by the virtualization package.

Dual booting is a great option provided you have the disk space and you are careful not to ruin your Windows installation.

Ubuntu also provides what is known as the Wubi option, which, although not intended to be a permanent solution, might be a less "dangerous" option than dual booting right away.

Try a lot of Linux distributions.  What is best for you is what is best for YOU and you should give yourself the opportunity to discover what that is.

---

### Post by jayboe on 2012-09-15
Just putting my two cents in, but I would suggest a windows user coming in with a Mint distro being that it has a windows kinda look and feel to it... albeit that Ububuntu is far superior in my humble opinion even though Mint is built off of Ubuntu. It also covers all your codecs included for playing a variety of movies and what not. It was a pleasant transition for my girlfriend coming into the Linux community although she is serious about playing web-based games which may prove to be a bit of a hassle from time to time when you have issues with trying to get all your bases covered with plugins, but it is all achievable with a little patience and perseverance.... I am Ubuntu all the way but I would suggest an older version of Mint... like Mint 13 especially since you are on a 'puter that is still running XP :(. They don't even provide updates anymore unless you have some military edition or something.
    Just be sure to partition about 10G if you can spare it before attempting to install a dual boot. It is relatively easy to install most linux distros and on minimal drive space.... hope my bud light two cents helps... :)

---

### Post by GreatDanton on 2012-09-15
Unless he posts his computer configuration, you can't suggest him which Os to use. Since the computer was made for win xp, I would go with Xubuntu 12.04 LTS or Lubuntu 12.04.

And btw, Linux Mint 13 is the latest release =).

Regards.

---

### Post by Bucky Ball on 2012-09-15
*Moved to **Recurring Discussions***

---

### Post by jayboe on 2012-09-15
> **GreatDanton said:**
> Unless he posts his computer configuration, you can't suggest him which Os to use. Since the computer was made for win xp, I would go with Xubuntu 12.04 LTS or Lubuntu 12.04.

And btw, Linux Mint 13 is the latest release =).

Regards.

Sorry, your right. I was thinking Mint 11, and yeah if his puter can handle crappy XP it should be ok with Mint 11 unless there is some incompatible hardware which is rare in the Linux world from what I have learned so far... I'm still a noob myself, but stay so exited with all the stuff I learn on a day to day basis... :)

---

### Post by Mikeb85 on 2012-09-15
I'd go with Ubuntu, and dual boot it next to Windows.  This is the easiest introduction to Linux there is.

---

### Post by tahdas on 2012-09-15
System: Microsoft Windows XP Professional Version 2002 Service pack 3 Registered to: desktop 55274-640-0999985-23510 Computer Intel(R) Pentium(R) 4CPU 2.40GHz 2.39GHz, 504 Mb of RAM

Hope this is the write info and i din't give TMI. 
I have written down a list of want i want from my OS:
I want it to be fast or fastish. when i play a game such as minecraft i want it to run smoothly and not glitch up and freeze all the time. I dont't want it to be main stream. I want it to be a little advanced so it looks like im smarter the=an i am.
thanks
tahdas

---

### Post by Bucky Ball on 2012-09-16
With 512Mb of RAM (even though it shows 504, that's what it is) you are limited. You will need to go for a lightweight distro as Ubuntu will be problematic. Try Xubuntu and if you have problems installing from the desktop version try the alternate.

You need the i386 32bit (for 32bit processors) Xubuntu Desktop. You can try it from the CD to see how it runs. 

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

The torrent is the best way. Lubuntu should also be okay. Crunchbang is lightweight and should be fine. There's PuppyLinux and a heap of others. Later you could make your own blend with the minimal install, using the lightest and only the things you need.

You could give straight Ubuntu a try if you like, it says 512 is the minimum, but don't like the chances, slightly better using the alternate ISO. The experience once installed though may be poor, especially with a few apps running. You could pretty much forget Kubuntu. Nightmare ride.

Perhaps someone who has these same specs might chime in ...

---

### Post by claracc on 2012-09-16
> **tahdas said:**
> System: Microsoft Windows XP Professional Version 2002 Service pack 3 Registered to: desktop 55274-640-0999985-23510 Computer Intel(R) Pentium(R) 4CPU 2.40GHz 2.39GHz, 504 Mb of RAM

Hope this is the write info and i din't give TMI. 
I have written down a list of want i want from my OS:
I want it to be fast or fastish. when i play a game such as minecraft i want it to run smoothly and not glitch up and freeze all the time. I dont't want it to be main stream. I want it to be a little advanced so it looks like im smarter the=an i am.
thanks
tahdas

With this small ram is very difficult to run games as minecraft smoothly. It does depend on RAM and CPU.

To play videogames I recommend you stay with win xp. As it has been said you can install a light distro as lubuntu 12.04 alongside your winxp os(dual boot).

The lubuntu box is vey low resources consumming and you can surf the web, doing office tasks and play music at a reasonable speed in old computers. But for running snappy videogames you'll need a powerfull machine.

---

### Post by whatthefunk on 2012-09-16
Id go with Lubuntu for that system.  Minecraft will probably be choppy...

---

### Post by Wim Sturkenboom on 2012-09-16
I'm not a gamer, so can't advise from that perspective.

> **Bucky Ball said:**
> With 512Mb of RAM (even though it shows 504, that's what it is) you are limited.
Probably 8MB for an integrated video so it actually is 504MB ;)

---

### Post by Bucky Ball on 2012-09-16
> **Wim Sturkenboom said:**
> 
Probably 8MB for an integrated video so it actually is 504MB ;)

That would account for it. ;)

---

### Post by houseworkshy on 2012-09-16
Now you know how much ram you have this thread could be very useful
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
EDIT I've just noticed how old that thread is.  So search for the names in it ( without version numbers ) and see what they require now.
Once  you have the names of the various operating systems which will fit try  searching around for details on them.  If you want to see them in action  search for them on youtube.
Also check that they are at your level  and search for things like +installing +( whatever name it is ).  Duel  booting is a very good idea so also take a look at +"duel booting" +XP  +( whatever name it is)
As a beginner search with +beginner or +easy or +first or +"entry level" may turn up a bit.
You  know what you want so just imagine someone has got it and work out what  kind of words and phrases they might use to describe it.
The site distrowatch.com has an advanvced search so using that could be handy too. 

When  you find something which might do download the iso and burn it, with  the slowest speed your burner allows, onto write only media. Then try a  live session.  A live session runs from the cd/dvd drive and won't  change your system.  The phrase used to describe a disc like that is  "live CD" or live "dvd".  Some don't work like that so, as you don't  know about linux yet don't try anything which isn't "live" or you could  end up starting a complicated install which you don't understand and  can't back out of. 

Also don't bother with operating system which  can only just run.  You want some space for the programs too.  I'd want  to leave at least half or that ram for doing things on top of the  operating system.  Graphics are particulary expensive in ram so,  rendering, and high end games are going to struggle.  Minecraft is going  to be pushing it, find out how much it needs and if that plus the  operating system is more than 512 it won't go.
As you have xp  installed you may need to make room for whatever you choose so read, or  watch, up on how it's done.  I just searched for "duel booting XP and"  on youtube there are a lots of videos on it.  Just slap the name of  whatever OS you find after that search phrase. Get the preparitory  knowlage first.  And back up all your important files before doing  anything.
XP online nowadays, as the support is negligable, isn't a  good idea.  So getting something which is supported is a very good  idea.  There are plenty of linux distros which use very little ram and  are fully supported.  Make sure the one you get is supported,  on  distrowatch.com use the advanced search to make sure you are only  looking at "active" projects.
This is the search page, [http://distrowatch.com/search.php](http://distrowatch.com/search.php)
You'll want to check "begginers" "live medium" "active" "i366" ( probably )
It doesn't seem to have a box for "light" or "lite" so you'll need to read up.  For 512ram the graphic user interphases  KDE and Unity are probably too big.  There are a lot of desktop enviroments around 
[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)
Have a look at that first, if you see one you like which is called lite or light then that may help to narrow down the search.
 Avoid "barebones" versions which though very small usually expect you  to know what you are doing, often all with typing and no grapic  manager.  They are really only a base for building something on.
The smallest one I know which has a decent gui is Slitaz.
Spend a few hours reading or watching videos before doing anything.  That's looks like a lot of post but don't be put off, many distributions make it very easy indeed.

---

### Post by tahdas on 2012-09-16
Ok guys im a little confused, but here is what i understand:
My computer is crap it has no room on so what ever i download its still gonna be slow. If i disside that is till want a new OS i should go with something light weight. So here are what i thinks my options are: Just keep XP. Download Zorin or something similar Lite it requires 678 MB as opposed to the regular 1.1 GB and i thinks its duel boot. Download Xubuntu Lubuntu or something similar. Buy another computer (like a mac!) off eBay and mess with that.
Would resetting my computer to Factory settings give it more room?
The long thing that houseworkshy wrote confused me a little bit, but i appreciate u guys writing pages of help!
Thanks 
Tahdas

---

### Post by snowpine on 2012-09-16
Sounds like a good plan to upgrade your hardware so that you can play Minecraft and other games with good performance. 

If you decide to use Ubuntu as the operating system on your new computer, you may find these links helpful:

[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)
[http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

---

### Post by jrog on 2012-09-16
OP, is this computer your primary computer? Sorry if you already said that and I missed it, but I'm trying to figure out whether this is a computer that you are simply playing around with or it is a computer that you will be relying on for your regular day-to-day usage.

---

### Post by joco1500 on 2012-09-16
For your use, i would suggest Joli os.

its based on Ubuntu and it makes your computer look like a tablet.

it is completely cloud operating so it is always connected to the Internet.

it also has a "app store" that you can download games and things of tat sort.

it also comes pre installed with Google chrome.

---

### Post by tahdas on 2012-09-16
> **jrog said:**
> OP, is this computer your primary computer? Sorry if you already said that and I missed it, but I'm trying to figure out whether this is a computer that you are simply playing around with or it is a computer that you will be relying on for your regular day-to-day usage.
Nope i have an ipad and my parents both have acomputer and my sister has laptop adn an ipod and my mom also  has a ipod and an smart phone! so if it messs up its no bigy.
Joli cloud looks cool but can i install games that are not from there app store?

---

### Post by jrog on 2012-09-16
> **tahdas said:**
> Nope i have an ipad and my parents both have acomputer and my sister has laptop adn an ipod and my mom also  has a ipod and an smart phone! so if it messs up its no bigy.
Joli cloud looks cool but can i install games that are not from there app store?
Okay, well, as others have said, your computer's specs are going to make it near-impossible to play recent computer games, though you will be able to play around with basic stuff. 

As far as distributions that are likely to work well with your computer and your goals, I would guess that [Lubuntu]("http://lubuntu.net/") would be the best. [Xubuntu]("http://xubuntu.org/") should also work well, though it is a bit "heavier" than Lubuntu; Lubuntu would probably allow you to do a bit more. [Crunchbang]("http://crunchbanglinux.org/") would work well and is probably even lighter than Lubuntu (not sure), but it may be a little bit more difficult for you to use than either Lubuntu or Xubuntu. You might also check out [Puppy Linux]("http://www.puppylinux.org") (or a derivative, [Macpup]("http://macpup.org/")), though I don't like these nearly as much as Lubuntu/Xubuntu. Finally, if -- and only if -- you really want to tinker around with your system and learn Linux at the risk of breaking things (or never having them work in the first place), you could look into [Arch Linux]("http://www.archlinux.org/"). Arch is *really *good, IMO, but at your level of computing knowledge at the moment, it will have a very steep learning curve.

So:

1. [Lubuntu]("http://lubuntu.net/")
2. [Xubuntu]("http://xubuntu.org/")
3. [Crunchbang]("http://crunchbanglinux.org/")
4. [Puppy]("http://www.puppylinux.org")/[Macpup]("http://macpup.org/")
5. [Arch Linux]("http://www.archlinux.org/")

Check out the linked websites for details.

---

### Post by tahdas on 2012-09-16
So with this computer i won't be able to game at all??? Damn! I might have to bye another older computer of eBay. See theres a lot of computers in my house but i can't really game  on any of them, On my dads computer i can play some online stuff but download never work. I cam use my sisters but i cant game on it and my moms is a Mac end off story. So i got this computer so i can play games, not a lot of games but ones i cant play on my dads.
So i guess  i'll down Crunch Bang. 
Wait a minute! Can i make a computer? Using spare parts from this one and buying totaled ones of ebay? Is that  hard?  Then i can mess with it and temperamental with it. Can you guys point me towards a computer building website? 
I'm sorry im kinda rambling. Better stop know.
Thanks
tahdas

---

### Post by snowpine on 2012-09-16
There are LOTS of games that will run well on a Pentium 4 with 504mb RAM!

My personal favorite is Dungeon Crawl:

```
sudo apt-get install crawl
crawl
```

Every game has its own hardware requirements, and these are independent of the operating system. In other words switching to CrunchBang will not magically allow your computer to play a game that won't run on Lubuntu. For example here are the Minecraft requirements: [http://www.minecraftwiki.net/wiki/Hardware_performance#Hardware_requirements](http://www.minecraftwiki.net/wiki/Hardware_performance#Hardware_requirements)

---

### Post by jrog on 2012-09-16
> **tahdas said:**
> So with this computer i won't be able to game at all??? Damn! I might have to bye another older computer of eBay. See theres a lot of computers in my house but i can't really game  on any of them, On my dads computer i can play some online stuff but download never work. I cam use my sisters but i cant game on it and my moms is a Mac end off story. So i got this computer so i can play games, not a lot of games but ones i cant play on my dads.
So i guess  i'll down Crunch Bang. 
Wait a minute! Can i make a computer? Using spare parts from this one and buying totaled ones of ebay? Is that  hard?  Then i can mess with it and temperamental with it. Can you guys point me towards a computer building website? 
I'm sorry im kinda rambling. Better stop know.
Thanks
tahdas
Can you give an example of the sort of game you'd like to be able to play?

---

### Post by jrog on 2012-09-16
> **snowpine said:**
> Every game has its own hardware requirements, and these are independent of the operating system. In other words switching to CrunchBang will not magically allow your computer to play a game that won't run on Lubuntu.
Not entirely true, because there are cases where a game requires XXX amount of free RAM, and the user has that much RAM on the system, but too much is being used by the OS for the game to run smoothly. An OS that uses less RAM may allow the game to run better.

---

### Post by snowpine on 2012-09-16
> **jrog said:**
> Not entirely true, because there are cases where a game requires XXX amount of free RAM, and the user has that much RAM on the system, but too much is being used by the OS for the game to run smoothly. An OS that uses less RAM may allow the game to run better.

I've never played Minecraft before, so if you think it will run on CrunchBang with the OP's specs, then I defer to your experience.

---

### Post by tahdas on 2012-09-16
I'm going to install Crunch Bang because i think less people use it and it looks a little advanced.
I want to play online Flash games (which arent currently working). I don't really have a good example but thing i curently have installed are: Spelunky, Minecraft, Super Box Crate, And Steam (Which isnt a game).

---

### Post by snowpine on 2012-09-16
> **tahdas said:**
> I want to play online Flash games (which arent currently working). 

Here are the [Adobe Flash minimum hardware requirements for Linux]("http://www.adobe.com/products/flashplayer/tech-specs.html"): 

> 

    2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks
    Red Hat® Enterprise Linux® (RHEL) 5.6 or later (32 bit and 64 bit), openSUSE® 11.3 or later (32 bit and 64 bit), or Ubuntu 10.04 or later (32 bit and 64 bit)
    Mozilla Firefox 4.0 or Google Chrome
    512MB of RAM; 128MB of graphics memory


I would say your current hardware is borderline for playing Flash games in Linux.

Any game you want to play, just Google its hardware requirements and compare against what you have.

---

### Post by tahdas on 2012-09-16
> **snowpine said:**
> Here are the [Adobe Flash minimum hardware requirements for Linux]("http://www.adobe.com/products/flashplayer/tech-specs.html"): 



I would say your current hardware is borderline for playing Flash games in Linux.

Any game you want to play, just Google its hardware requirements and compare against what you have.

So should i get another computer? Buy something cheap off ebay? Can i make a Computer? should i buy parts and upgrade this computer?

---

### Post by snowpine on 2012-09-16
> **tahdas said:**
> So should i get another computer? Buy something cheap off ebay? Can i make a Computer? should i buy parts and upgrade this computer?

I bet if you ask on the Minecraft forums, people can recommend a new computer that will be good for playing Minecraft. :)

---

### Post by jrog on 2012-09-16
> **tahdas said:**
> I'm going to install Crunch Bang because i think less people use it and it looks a little advanced.
I want to play online Flash games (which arent currently working). I don't really have a good example but thing i curently have installed are: Spelunky, Minecraft, Super Box Crate, And Steam (Which isnt a game).
You should be able to play online Flash games okay, I think. Based on quick Googling, your system meets the requirements for Spelunky and perhaps for Super Crate Box, though I don't know whether they will play well on Linux -- you may have to use Wine (basically a software layer that lets you run Windows programs) to play them, which would very likely mean you'd need more RAM at least for Super Crate Box (though you'd probably be okay for Spelunky). Your system does not meet the requirements for Minecraft, and Steam is unfortunately not yet available for Linux, so you couldn't use that regardless.

---

### Post by tahdas on 2012-09-16
> **snowpine said:**
> I bet if you ask on the Minecraft forums, people can recommend a new computer that will be good for playing Minecraft. :)

There3 probably going to say alien ware and that's above my budget, besides i don't want a computer exclusively for gaming i just want ti to run games well when i want to play them. 
Does anyone know about building a computer? 
Thanks guys for all your advice,
tahdas

---

### Post by PaulInBHC on 2012-09-16
There are websites like PC Mechanic with How To articles on building computers. You need to do a lot of reading first.

Things like RAM have different types, SDRAM, DDR, DDR2, DDR3 and they won't plug in to a motherboard with the wrong slot. Same with CPUs. There are different pins on different CPUs.

---

### Post by tahdas on 2012-09-16
> **jrog said:**
> You should be able to play online Flash games okay, I think. Based on quick Googling, your system meets the requirements for Spelunky and perhaps for Super Crate Box, though I don't know whether they will play well on Linux -- you may have to use Wine (basically a software layer that lets you run Windows programs) to play them, which would very likely mean you'd need more RAM at least for Super Crate Box (though you'd probably be okay for Spelunky). Your system does not meet the requirements for Minecraft, and Steam is unfortunately not yet available for Linux, so you couldn't use that regardless.

Ok so i should install crunch bang or Lubuntu or Xubuntu (Pick one for im indecisive)? And i'll have to wait on minecraft right? Steam isnt essential.

---

### Post by jrog on 2012-09-16
> **tahdas said:**
> Ok so i should install crunch bang or Lubuntu or Xubuntu (Pick one for im indecisive)? And i'll have to wait on minecraft right? Steam isnt essential.
If I were forced to choose, I'd say Lubuntu.

---

### Post by tahdas on 2012-09-16
Ok i looked around ebay and found this: [http://www.ebay.com/itm/Dell-OptiPlex-760-Desktop-2-80-GHz-2-GB-RAM-80-GB-HDD-/150902286898?pt=Desktop_PCs&hash=item23227a2a32](http://www.ebay.com/itm/Dell-OptiPlex-760-Desktop-2-80-GHz-2-GB-RAM-80-GB-HDD-/150902286898?pt=Desktop_PCs&hash=item23227a2a32)
I'm wondering if this would work for what i want? I can keep my current computer as a test subject *laughs evilly*.
So will the computer linked meet my needs?

---

### Post by jrog on 2012-09-16
> **tahdas said:**
> Ok i looked around ebay and found this: [http://www.ebay.com/itm/Dell-OptiPlex-760-Desktop-2-80-GHz-2-GB-RAM-80-GB-HDD-/150902286898?pt=Desktop_PCs&hash=item23227a2a32](http://www.ebay.com/itm/Dell-OptiPlex-760-Desktop-2-80-GHz-2-GB-RAM-80-GB-HDD-/150902286898?pt=Desktop_PCs&hash=item23227a2a32)
I'm wondering if this would work for what i want? I can keep my current computer as a test subject *laughs evilly*.
So will the computer linked meet my needs?
Based on a very quick look (so don't just take my word for it), yes, it looks like it would.

---

### Post by tahdas on 2012-09-16
So should I just keep XP and wait for a new computer? Oh and can you run adobe after affects or other adobe prodoucts on Linux or Ubuntu based OSs? I'm waiting for you guys to tell me what to do.

---

### Post by PaulInBHC on 2012-09-16
Optiplex are generally business boxes. Note the video ram at 8mb is probably onboard video chip. If you can add a video card later it might work for you. Can't tell from the description what it has for open card slots.

---

### Post by tahdas on 2012-09-16
> **PaulInBHC said:**
> Optiplex are generally business boxes. Note the video ram at 8mb is probably onboard video chip. If you can add a video card later it might work for you. Can't tell from the description what it has for open card slots.

Well the one linked is now out of the question my very tipytop bid would be $50. I'm not sure what brand  i want but i'm thinking an older dell. The one my family had lasted a long time. I'm thinking i'll get a laptop and a desktop and experiment with the laptop.
Also what  how much ram should i have and how much memory. Give me numbers please!
Thanks
tahdas

---

### Post by PaulInBHC on 2012-09-16
Very few games take advantage of multi cores. A single core will do since you are price conscious. At least 2ghz. For RAM, 2gig minimum. Video, 512mb not shared.

Best is to find a box near you, start it up, right click the My Computer icon and click properties. That will show you the CPU and RAM. Right click the desktop and check properties to see if you can tell anything about the video.

---

### Post by Bucky Ball on 2012-09-17
> **tahdas said:**
> Ok guys im a little confused, but here is what i understand:
My computer is crap it has no room on so what ever i download its still gonna be slow. If i disside that is till want a new OS i should go with something light weight. So here are what i thinks my options are: Just keep XP. Download Zorin or something similar Lite it requires 678 MB as opposed to the regular 1.1 GB and i thinks its duel boot. Download Xubuntu Lubuntu or something similar. Buy another computer (like a mac!) off eBay and mess with that.
Would resetting my computer to Factory settings give it more room?
The long thing that houseworkshy wrote confused me a little bit, but i appreciate u guys writing pages of help!
Thanks 
Tahdas

You don't need to faff about with any of this. Just buy more RAM. Find out how much your machine can take then load it up, or just add another 512 to get it to a gb. Make sure you have 15Gb of free space on a drive (less will do depending) and install whatever Linux you want. 1Gb would be enough to get Ubuntu and probably Kubuntu cranking (I've tried both on my old P4 with 1Gb and all good). ;)

---

### Post by jrog on 2012-09-17
> **Bucky Ball said:**
> You don't need to faff about with any of this. Just buy more RAM. Find out how much your machine can take then load it up, or just add another 512 to get it to a gb. Make sure you have 15Gb of free space on a drive (less will do depending) and install whatever Linux you want. 1Gb would be enough to get Ubuntu and probably Kubuntu cranking (I've tried both on my old P4 with 1Gb and all good). ;)
^ This is probably your best option right now, OP; good advice. Did you (OP) mention what kind of computer this is that you have, exactly? If you can do that, someone here can help you determine what kind of RAM you would need to buy, how much the machine can handle, etc.

---

### Post by tahdas on 2012-09-18
I have a dell. i looking around eBay though. Highest bidder on like 3 macs right now. Hope i win!
Thanks guys!

---

### Post by DeezyFaReal on 2012-09-19
**Here are some Links**
**[SIZE=2]News on Linux and Free and Opensource software[/SIZE]**
[Linux Journal | The Original Magazine of the Linux Community]("http://www.linuxjournal.com/") 
[Linux.com | The source for Linux information]("http://www.linux.com/") 
[Linux.org | Resource for Linux | How to Linux guide | What is Linux]("http://www.linux.org/")
[Slashdot: News for nerds, stuff that matters]("http://slashdot.org/") 
[Full Circle Magazine]("http://fullcirclemagazine.org/")
[TuxRadar Linux]("http://www.tuxradar.com/")
Advice and Help for People new to Linux
[tuXfiles - the Linux newbie help files, tutorials, and tips]("http://www.tuxfiles.org/")

Here's one more link to an article
[http://www.tuxradar.com/content/best-distro-2011](http://www.tuxradar.com/content/best-distro-2011)

---

### Post by Bucky Ball on 2012-09-19
[COLOR=Purple]:cool: When thread solved *mark as 'Solved' from 'Thread Tools' at top right.*[/COLOR]

---

### Post by jrog on 2012-09-19
> **tahdas said:**
> I have a dell. i looking around eBay though. Highest bidder on like 3 macs right now. Hope i win!
Thanks guys!
We'd need you to be more specific than "I have a Dell" if you want help selecting a RAM upgrade, assuming you do decide to go that route. What model of Dell, for example? 

And again, I want to emphasize that a RAM upgrade may be much more cost-effective than buying something off of eBay. It might end up costing you around $20 or so.

---

### Post by tahdas on 2012-09-19
> **Bucky Ball said:**
> [COLOR=Purple]:cool: When thread solved *mark as 'Solved' from 'Thread Tools' at top right.*[/COLOR]

I don't think this is quite solved. But i will mark anyway!;)
A
nd i think i'm happy with something off eaby i'll only be spending $20.00-$75.00 on a new computer and it might be a mac! But if this fails i'll come back here with the information (if i can figure out how to find it;))
Thanks!
Edit: Deezy im looking at your links! thanks again! And how do i mark this solved?

---

### Post by DeezyFaReal on 2012-09-19
Thanks for looking at the links
If I were you I wouldn't mark your thread as solved yet, but if you want to use "Thread Tools" which is at the top.

---

### Post by tahdas on 2012-09-23
Ok guys I bought a computer off eBay and it should be here by the 28 (Looper!). It has 4GB of RAM, and it looks like its pretty good it's a dell ( we're rolling the deeeep). Any way I'll have a few more questions when it comes.

---

### Post by Bucky Ball on 2012-09-23
***Thread Closed***


Glad you got it sorted. Please mark as 'Solved' and post a new thread regarding any new problems with a descriptive title and in the appropriate forum. Hopefully they'll be few. 

Good luck with Ubuntu and the new machine. ;)

---

