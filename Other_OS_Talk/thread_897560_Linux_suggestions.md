---
title: "Linux suggestions"
date: 2008-08-22
forum: Other OS Talk
---

### Post by mangurt on 2008-08-22
Greetings all;

I received a phone call from my parents last night.  They currently have 2 windows based computers (both dells).  One laptop and one tower.  I was over at their house last week, and had to go through and clean up their computer because of spyware/malware.  They said that they were thinking about getting a Mac because they heard that Mac's don't have that sort of problem.  I told them that a pretty true statement, but I don't have those sorts of problems either because I run linux.  Anywho, they looked at a Mac yesterday, and saw how much one was, and called me up and asked if I could install linux on their computers.  I said Yes, but warned them that linux is not windows, and it will take some time to get use to it.

Here's my dilemma;
1)  Their tower is on dial-up.  The only time I use dial up is when I go to their house....I'm going to guess that dial-up should not be a problem with linux, but what I am worried about is big updates.
2)  Wi-fi:  The laptop has a wi-fi card, and my parents are at the point where they are going to travel around, and would like to use the laptop via wi-fi.  I really don't play around with wi-fi because my system is wired into my router.
3)  Computer use:  My parents are very, very, very computer illiterate (so much so that I believe that's on of the main reasons why they had so many spyware/malware stuff on their system).

I'm trying to think of what linux distro would be the easiest for them to use.  The primary use of the computers are basic internet use (email and web browsing) and light office stuff (word and excel documents).  My gut would say that I should toss a form of KDE on so it's "familiar" to them.  I currently have 3 computers all running some version of linux (Fedora, linux mint 4.0 kde, and my system where I bounce around between hardy heron, UE 1.8, Fedora, or some other disto [I like checking things out].

What I am looking for is some suggestions on what I should toss on the system.  I doubt either computer will really be updated that much unless I am there....unless I show my parents how to do that.

My thought are between PClinuxOS2007, Kubuntu, and Fedora KDE.

Anyone have any other ideas or suggestions on which one I should go with?
Thanks

---

### Post by livestockPimp on 2008-08-22
well for your dilemmas,
1) dialup works fine on ubuntu, I wouldnt be doing any updates but for a general use PC they most likely wont need the latest anything. just have the CD there for installing packages for new things they want to use.

2)the wifi card could be compatible, there are ALOT that are a real pain to get working, I would look at the chipset and google it.

As for the version to use I would stick to the latest ubuntu release, they seem to have most stuff working with the hotplug drivers so it should be easy to get it working and cds, flash drives, ect all auto-mount. There are other distros I use for different purposes but ubuntu is one of the most user friendly ones.

---

### Post by eldragon on 2008-08-22
i would definately consider downloading MANY MANY MANY useful apps and have a dvd repository ready for them

whenever you get home, take with you a cd with all updates too :D

---

### Post by mangurt on 2008-08-22
I was thinking about that.  I would have the computer at my house to do the initial install, and I have broadband, so that would be fine.  As for the updates, I figure I could dump them on a thumb drive before I go up there.

---

### Post by _duncan_ on 2008-08-22
> Their tower is on dial-up. The only time I use dial up is when I go to their house....I'm going to guess that dial-up should not be a problem with linux, but what I am worried about is big updates.

You may have to rethink that. If the modem you have happens to be an internal "winmodem" finding the appropriate driver for it could be a bit of a problem. This type of modem are "incomplete" modems that relies on the operating system to do part of the work of a complete hardware modem. And, as the name implies, most manufacturers of these "winmodems" assume that the users are using a variant of the Windows OS.

There are equivalent linux drivers for selected "winmodems" but not all winmodem chipsets are supported. Also, most of these drivers require compilation from source, and may require recompilation with each kernel upgrade. Something you can't expect your parents to do on their own.

It's a lot easier though if your parents' tower happens to use an external serial hardware modem since these don't require drivers to work in linux.

The 2nd link on my sig (Dial-Up Modem Wiki) has a wealth of info on getting dial-up to work in ubuntu. Might be worth your while to browse through it to get an overview of the process.

---

### Post by zmjjmz on 2008-08-22
If the wi-fi card doesn't work (assuming it's PCMCIA) you could get a DWL-G650 wifi card from Amazon for like 15$.

Also, dial-up should be fine for their usage, just preinstall Abiword and Gnumeric (much more lightweight than OpenOffice.org) and FF3 (with adblock and easylist and noscript to prevent unwanted items from eating bandwidth) and Thunderbird.

---

### Post by mangurt on 2008-08-22
Here's the plan for what I would have installed before they even got the computer:

FF3 with ad-block plus, flash and java
Thunderbird
MP3 codex and DVD codex
Picasa for their photos (they use it in windows)

Thanks for all the suggestions, and keep them coming...

---

### Post by zmjjmz on 2008-08-22
Specs?

---

### Post by mangurt on 2008-08-22
I have no idea what the specs are.  The computers are their house right now (which is about 150 miles away from my house).  I will be getting the computers in a week or so.  Just want to get some ideas and really think this out...

---

### Post by 4Orbs on 2008-08-22
> Specs?

Agreed, the specs of your parents computers should be a major factor in your choices. If the computers are a bit low on resources (512MB ram or less, 1.6 ghz cpu or less) it might be best to forget about anything with Compiz or other dazzling effects. They can create problems if a screensaver kicks in while effects are enabled. Since you are going to perform the initial setup, pre-installed codecs and plugins are not an issue... but they sure make for quicker installation and setup.

I personally prefer the Xfce versions of most distros. Maybe not as pretty as their Gnome or KDE counterparts, but more satisfying in the long run. And a bit safer for a wider range of computers.

---

### Post by mangurt on 2008-08-22
The only reason why I was thinking for KDE is it's so damn close to windows in look that it would not be that hard of a change for them.  I did this with my wife, and now she loves KDE (with no eye candy).  I've never played around with Xfce, so I really don't want to go down that road.

---

### Post by Twitch6000 on 2008-08-22
> **mangurt said:**
> The only reason why I was thinking for KDE is it's so damn close to windows in look that it would not be that hard of a change for them.  I did this with my wife, and now she loves KDE (with no eye candy).  I've never played around with Xfce, so I really don't want to go down that road.

XFCE is like Gnome And KDE combined(at least for me) ,but light and has its own feel aswell.

Now for problem.

I would suggest getting over there with these four distros and try each one out.
I would also suggest putting it on the laptop only since it is their main use.Then just cleaning the windows machine.

Bring over Damn Small Linux,PCLinuxOS08minime,Xubuntu or Kubuntu 8.0.1,and last ,but not least Fedora8 or 9.

One of these will make them happy and surely meet their needs.
The programs I suggest installing-
Any driver installing helper.
Thunder Bird
Open Office Full Client(I know it will take space,but it will meet any needs they have).
Then a few games they might like.
Codecs
Adblock Plus

After that they should be set and ready to go.


Now for the windows machince if they already have an anti virus run it and clear out whats possible.

Then burn a better anti spyware and anti spyware to disc.

I suggest Bitdefender 10 and Spybot.

Install Them to their computer wipe out all their maleware and then defrag their computer.

They should be fine then.

I suggest keeping windows on the main machine so they don't have to leave windows cold turkey and can have something to resort to when having Linux troubles.

---

### Post by mangurt on 2008-08-22
Those are some good suggestions.  I cleaned out their system with sypbot and hijack this.  They are running Norton security system (which I think is the devil).  I did the complete defrag of the hard drive, and the system is running better.  I think my parents are looking for something they don't have to worry about.....they want to be able to get online, check their email, look for some maps, and call it a day.
Keep the suggestions rolling though....I like the

---

### Post by malspa on 2008-08-22
As for the dial-up issue, definitely consider the external serial modem.  Otherwise you'll be in for lots of hassles trying to get winmodems to work, if you can get them to work at all.

For me, after getting an external serial modem, it's a lot easier to set up dial-up with KDE distros than in GNOME.

Finally, consider Mepis.  I've had a lot of success on various machines with that one. PCLinuxOS might work out well, too.  Both are pretty good KDE distros.

---

### Post by liquidfunk on 2008-08-22
Whichever distro you choose, have a look at XPDE:

[http://www.xpde.com/]("http://www.xpde.com/")

---

