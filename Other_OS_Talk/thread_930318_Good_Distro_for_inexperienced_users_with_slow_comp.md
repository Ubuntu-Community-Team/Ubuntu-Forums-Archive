---
title: "Good Distro for inexperienced users with slow computers?"
date: 2008-09-25
forum: Other OS Talk
---

### Post by Misterbadexample on 2008-09-25
Title to this thread might seem a little weird, but I am serious.

I'm repurposing old hardware into internet machines with various linux distros. They work just fine for me, but my ultimate goal is to give these machines away to community centers or to worthy people in need of internets. I would like this to evolve into a charity operation at some point.

But, I've not had success in finding the right Linux distro. Ubuntu is one of the easiest for "normies" to use, but it runs like aaaaaasssssss on this old hardware.

I like Puppy and I seem to remember trying TinyMe, which seemed very similar to puppy. They have the speed I would want on that hardware, but they are a little daunting for the average user. I would have to mess around with the settings to simplify the user experience--take off all the scary settings icons and name the shortcuts something like, "Word Processing" and "Connect to the Internet".

What is a good middle ground here? If I was more adept, I could probably create an install CD with of Puppy (or something similar) with everything set up comfortably for the user.

Does anyone know any distros or tools or tutorials that might help me?

---

### Post by doorknob60 on 2008-09-25
Specs please?

---

### Post by starcannon on 2008-09-25
[Xubuntu]("http://www.xubuntu.org/")(medium), [Fluxbuntu]("http://fluxbuntu.org/")(very lightweight)

Both are excellent; Xubuntu is very easy to use, Fluxbuntu has a bit of a learning curve learning to work with Rox, but once you get it figured out, well, it rocks :guitar:

---

### Post by John164918a on 2008-09-25
You could try Xubuntu maybe. Apparently its designed for older computers. It uses Xfce instead of GNOME as a desktop manager.

---

### Post by John164918a on 2008-09-25
Jinx!:guitar:

---

### Post by Misterbadexample on 2008-09-25
X86 Architecture. That's about all I can say, since I won't have control over specs of PCs I get in the future.

I need something that is light enough to be speedy on PCs that were probably put together for Windows 98--so, roughly 10 year old hardware, some newer.

---

### Post by mike1234 on 2008-09-25
Maybe substitute "casual" for "dumb". :)  I think about all mainstream distros are getting a little porky. I never tried lighter versions. My Dell Server is made to run hard 24/7. 

M.

---

### Post by snowpine on 2008-09-25
I would recommend being somewhat selective and limiting your project to pentium 3 with 256mb of ram or better. Xubuntu will run well on those specs and has excellent support here on the forums. Personally I am running Crunchbang on an old laptop with those specs and it is an interesting alternative to Xubuntu for those who like to tinker. For slightly slower computers, I can say a lot of good things about Fluxbuntu and of course Puppy seems very popular.

---

### Post by zmjjmz on 2008-09-25
Hm, pretty simple actually.
Find a simple IceWM based Debian distro (or just Debian itself) and then edit the menu files to the point of insanely easyness.
Then, remaster it to a LiveCD and use that LiveCD (after making multiple backups of it, of course) to install that distro on other computers.
And when you do that, could you give me an .iso?
I'm going to be starting a similar project.

---

### Post by Misterbadexample on 2008-09-25
> **starcannon said:**
> [Xubuntu]("http://www.xubuntu.org/")(medium), [Fluxbuntu]("http://fluxbuntu.org/")(very lightweight)

Both are excellent; Xubuntu is very easy to use, Fluxbuntu has a bit of a learning curve learning to work with Rox, but once you get it figured out, well, it rocks :guitar:

@John & Starcannon: I've personally used Xubuntu, which didn't work out so well for me, as it was on my PPC machine. It didn't take too well to it and it ran pretty pokey. OSX Tiger and OpenSUSE both run very well on it. I'm thinking it had more to do with the community port of Hardy to PPC, than Xubuntu.

I had used Zenwalk on a computer I built from hardware I found in the trash. It worked pretty okay for a while, but I got pretty frustrated with it eventually. I bring this up because Zenwalk uses Xfce.

Fluxbuntu I've heard of but never tried. If I can customize it the way I want it for casual users, it might be a good candidate. There's supposed to be a tool for rolling your Ubuntu settings into a liveCD or install CD. If that will work with Fluxbuntu, I might have a winner. Or at least some manner of temporary solution.

@mike1234: Casual is better, I'll admit, if we're trying to be nice. But I wanted to get across that people I'm looking to help might be completely clueless.

---

### Post by doorknob60 on 2008-09-25
Xubuntu for comps designed for Win98? NO, [Ubuntulite]("http://ubuntulite.tuxfamily.org/") (never tried, but it uses LXDE, a super lightweight DE that I use on my Debian craptop, I recommend it), [Fluxbuntu]("http://fluxbuntu.org/") (Used it, it's pretty good, not the best though), or a Debian installation with LXDE, Xfce, or some other lightweight solution (Debian+Xfce is probably the most feature complete out of what I said, and it's really light too compared to Xubuntu, I recommend trying on 128+ MB of RAM)

---

### Post by zmjjmz on 2008-09-25
> **doorknob60 said:**
> [Fluxbuntu]("http://fluxbuntu.org/") (Used it, it's pretty good, not the best though)

Fluxbuntu is slooooooow on my 400MHz celery with 160MB RAM and a 4GB HDD from 1998 (with Win98 ).

---

### Post by snowpine on 2008-09-25
[QUOTE=Misterbadexample;5857253
Fluxbuntu I've heard of but never tried. If I can customize it the way I want it for casual users, it might be a good candidate. There's supposed to be a tool for rolling your Ubuntu settings into a liveCD or install CD. If that will work with Fluxbuntu, I might have a winner. Or at least some manner of temporary solution.
[/QUOTE]

One thing Fluxbuntu has going for it is there are icons on the desktop for your favorite applications (you can customize them). So it is very obvious how to launch the browser or the file manager for instance. Very kiosk-y.

Remastersys is the utility I think you're thinking of. I had trouble using it with Fluxbuntu in a virtual machine (it actually broke my install :(), but I never delved too deeply into troubleshooting it. Perhaps someone with more knowledge can give you some tips.

I agree that Xubuntu is not as quick as it should be. :) What it does have going for it is that 99% of Ubuntu tips & tutorials will work on it, and that's a large knowledge base.

---

### Post by Misterbadexample on 2008-09-25
> **zmjjmz said:**
> Hm, pretty simple actually.
Find a simple IceWM based Debian distro (or just Debian itself) and then edit the menu files to the point of insanely easyness.
Then, remaster it to a LiveCD and use that LiveCD (after making multiple backups of it, of course) to install that distro on other computers.
And when you do that, could you give me an .iso?
I'm going to be starting a similar project.

How about you do it and give me the iso? Lol

Once I find my solution, I'd be happy to share it with anybody. I'm glad to hear other people are interested in doing this sort of thing--if we can help each other out, I think it would be really great.

@snowpine: Well, it would be smart to limit this project, but beggars can't be choosers. If somebody gives me a seriously terrible machine, I'll have to do something with it. But in reality, I'd bet 90% of the hardware I get is in that range.

@doorknob60: Ah, neat. LXDE is news to me. So is Ubuntulite. I'll have to give these suggestions a whirl, they seem to have a lot of potential.

---

### Post by schauerlich on 2008-09-25
You could build a custom minimal Arch install and make an install CD out of it for all of the rest of your machines.

---

### Post by cardinals_fan on 2008-09-25
I've said it before and I'll say it again: SliTaz!  Complete and satisfying.

---

### Post by zmjjmz on 2008-09-25
> **EDavidBurg said:**
> You could build a custom minimal Arch install and make an install CD out of it for all of the rest of your machines.

Only problem with that is that supposedly Arch is kinda bleeding edge.

Also, dumb users will want to install new apps every so often. gnome-app-install isn't suitable for this because it's too heavy (and drags along a whole bunch of gnome ****), and neither is the KDE counterpart.
Synaptic is worse because it has to parse a larger database, and the package installation is a bit too technical for the users.

---

### Post by snowpine on 2008-09-25
> **cardinals_fan said:**
> I've said it before and I'll say it again: SliTaz!  Complete and satisfying.

+1 slitaz rocks!
Also its Live CD remastering tools are excellent.

---

### Post by starcannon on 2008-09-25
For PPC your best bet is to use a 7.10 ubuntu variant, or wait for 8.10, not sure how much ppc support will be in 8.10, but I did see some in the daily folder. I'm running Xubuntu 7.10 Gutsy Gibbon fine on my Playstation 3 (ppc/cell cpu). Yellowdog linux is supposed to be excellent on ppc as well, worked flawlessly on my Playstation, but I'm an Ubuntu junky and I ended up just ditching Yellowdog and going through the PSUbuntu install process.

[Yellowdog Linux]("http://www.terrasoftsolutions.com/support/downloads/")

GL and have fun.

---

### Post by oldsoundguy on 2008-09-25
You might look into Linux Mint.  I just put it on my Crash Test Dummy (an old and slow celery with only 512 ram and a 40 gb hd!) and was amazed at just what actually loaded without having to jump into add/remove. synaptic or terminal.  It loads up as an internet ready machine without a problem .. not exceptionally fancy, but it works.  I jumped right on line with it on my network without a hitch. It found my D-Link wireless and there I was!
Only issue I had was with an NVida card that did not want to work with any of the driver set-ups .. resident, restricted or Envy .. none worked correctly so I went with the on board display on the Intel board and it worked fine.

---

### Post by cardinals_fan on 2008-09-25
> **oldsoundguy said:**
> You might look into Linux Mint.  I just put it on my Crash Test Dummy (an old and slow celery with only 512 ram and a 40 gb hd!) and was amazed at just what actually loaded without having to jump into add/remove. synaptic or terminal.  It loads up as an internet ready machine without a problem .. not exceptionally fancy, but it works.  I jumped right on line with it on my network without a hitch. It found my D-Link wireless and there I was!
Only issue I had was with an NVida card that did not want to work with any of the driver set-ups .. resident, restricted or Envy .. none worked correctly so I went with the on board display on the Intel board and it worked fine.
Sorry, but 512 MB of RAM isn't that slow.  Give it a shot on a machine with 128 MB and we'll talk.

---

### Post by Misterbadexample on 2008-09-25
> **starcannon said:**
> For PPC your best bet is to use a 7.10 ubuntu variant, or wait for 8.10, not sure how much ppc support will be in 8.10, but I did see some in the daily folder. I'm running Xubuntu 7.10 Gutsy Gibbon fine on my Playstation 3 (ppc/cell cpu). Yellowdog linux is supposed to be excellent on ppc as well, worked flawlessly on my Playstation, but I'm an Ubuntu junky and I ended up just ditching Yellowdog and going through the PSUbuntu install process.

[Yellowdog Linux]("http://www.terrasoftsolutions.com/support/downloads/")

GL and have fun.

OpenSUSE is professionally developed and tested specifically on my model TiPowerbook, so it works quite okay. Ubuntu Gutsy and Hardy both gave a lot of errors and problems on the TiPowerbook. My biggest gripe on openSUSE is programs supporting PPC, which you'd get on any PPC linux.

I would give PPC ubuntu another try before totally casting it away, but the Powerbook doesn't like it.

@zmjjmz: So smart users don't need to install new software? Lol. In my eyes, a lot of the users will be so afraid they're going to break the computer that they won't try to install anything. Or else they'll go out and buy Windows software and try to put it on their Puppy linux computer or whatever and call me when it doesn't work.

---

### Post by MaxIBoy on 2008-09-25
Puppylinux is light and very good for dumb users. I don't use it because the interface is condescending.

---

### Post by KiwiNZ on 2008-09-25
I have changed the title of this thread to one which is more appropriate

---

### Post by Misterbadexample on 2008-09-25
SliTaz looks interesting. I'm downloading images of a lot of these distros to try. I guess I've got some homework to do for this project.

@MaxIBoy: If I'm a dumb user, then I would agree with you. But I'm talking something that can be set up to be easy to use as Mac OSX for people that just want to email stuff and look at Youtube and Wikipedia. Puppy linux certainly is a fast OS, but personally, coming from a background of Windows and Mac OS, settings and customizing doesn't work the way I expect it to, and that'll frustrate any casual (re:dumb) user.

If I was going to talk about a specific user, I would mention my octogenarian grandfather. We named his Wordpad "Typewriter" so he would know what it was. That's the sort of user I'm anticipating. The kind that doesn't know what an "operating system" even is. The kind that gapes at you like a dog that has been shown a card trick when you say, "Linux is an open source OS!"

Anyway, that's who I'm pandering to. I want the solution that presents the least potential problems.

---

### Post by Misterbadexample on 2008-09-25
> **KiwiNZ said:**
> I have changed the title of this thread to one which is more appropriate

Guess that's fine with me, but it seems excessive. I doubt the people I'm specifically talking about could even find this forum and are unlikely to be offended by it.

My purpose was to get people's attention, not make fun of people.

Meh.

---

### Post by oldsoundguy on 2008-09-26
I know of which you speak!  ... I am in the process of building a Mythbuntu Personal Video Recorder (like a TIVO unit) for my handicapped brother .. who has not a CLUE about Linux in any way and really does not care to learn.  He is happy with his XP computer that takes 20 minutes to boot and no longer has a "help and support" and does not do everything it is supposed to do.  So I buried the Gnome desktop behind the "machine" front end so that the only person that can get into it is me to do updates and repairs! IF he starts to show an interest in what makes it tick, I will bring it out front and start some basic instruction.

OH & BTW Cardinals Fan .. a 466 Celeron IS slow (dial up slow) no matter how much memory is on the board since the memory is PC 66! (Why I call the box the "Crash Test Dummy".  If a system will work on it, it will most assuredly work on something faster and bigger! .. but if it crashes, who cares? It becomes NEXT!!!!!)

---

### Post by joninkrakow on 2008-09-26
> **Misterbadexample said:**
> Title to this thread might seem a little weird, but I am serious.


I like Puppy and I seem to remember trying TinyMe, which seemed very similar to puppy. They have the speed I would want on that hardware, but they are a little daunting for the average user. I would have to mess around with the settings to simplify the user experience--take off all the scary settings icons and name the shortcuts something like, "Word Processing" and "Connect to the Internet".

What is a good middle ground here? If I was more adept, I could probably create an install CD with of Puppy (or something similar) with everything set up comfortably for the user.

Does anyone know any distros or tools or tutorials that might help me?

I still say Puppy. I set a couple folks I know up with Puppy and they are both happy--in fact, it's the first computer my Dad (age 78) has understood. He likes the single-click desktop, and Puppy has done what you are saying--labeled things simply, like "browse" or "connect" or "write", etc.

But if you want a more "normal" experience, there's always Puppy with xfce as the desktop environment. xfce is quite simple and easy to learn, and runs just great on Puppy. I use it on an old 366 PII Dell laptop with 160 meg of ram. It's just fine. That said, my dad loves Puppy's default. :-)

-Jon

---

### Post by Misterbadexample on 2008-09-26
> **joninkrakow said:**
> I still say Puppy. I set a couple folks I know up with Puppy and they are both happy--in fact, it's the first computer my Dad (age 78) has understood. He likes the single-click desktop, and Puppy has done what you are saying--labeled things simply, like "browse" or "connect" or "write", etc.

But if you want a more "normal" experience, there's always Puppy with xfce as the desktop environment. xfce is quite simple and easy to learn, and runs just great on Puppy. I use it on an old 366 PII Dell laptop with 160 meg of ram. It's just fine. That said, my dad loves Puppy's default. :-)

-Jon

I still like Puppy. It might work if I can edit settings to clean it up and make it easy. And then make a CD of that install so I can put it on a bunch of machines.

I never thought of XFCE on Puppy. Blows my mind a little.

Bunch of good suggestions, everybody. Keep 'em coming if you have any other thoughts.

---

### Post by mikjp on 2008-09-26
Zenwalk. 

Or some other distro I mention in my blog posting about [lightweight Linux distributions](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html). 

Greetings,

mikko

---

### Post by K.Mandla on 2008-09-26
Moved to Other OS Talk.

---

### Post by joninkrakow on 2008-09-26
> **Misterbadexample said:**
> I still like Puppy. It might work if I can edit settings to clean it up and make it easy. And then make a CD of that install so I can put it on a bunch of machines.

I never thought of XFCE on Puppy. Blows my mind a little.

Bunch of good suggestions, everybody. Keep 'em coming if you have any other thoughts.

Yeah, Puppy is really easy to create derivatives from. There are already bunches. In fact, there may already be one out there that will fit your needs. And you ought to try xfce on Puppy. It's fun. ;-)

-Jon

---

### Post by darrelljon on 2008-09-26
Two Puppy Linux derivatives in particular spring to mind.
[SIZE="4"][Transitions]("http://murga-linux.com/puppy/viewtopic.php?t=28450")[/SIZE]
A Puppy for "Windows" refugees with absolutely no knowledge of Linux. Transitions is built on Fat Free 301. Default Window Manager is JWM, but IceWM is included, with the LookXP and TrueVista themes included. It has OpenOffice.org.
[SIZE="4"][Pupeez]("http://www.murga-linux.com/puppy/viewtopic.php?t=28209")[/SIZE]
Simple, Elegant and Fast"
- Pupeez is aimed to users who just want a linux that works for large percentage of tasks they do everyday.
- Pupeez is aimed at users who just want a media internet PC.
- Pupeez is aimed at 'technophobes', parents and grand parents.
It has Abiword.
Older Puppy Linux derivatives worth looking at IMO are [PuppyPro]("http://bit.ly/3y5O9j") and [XPuppyPro]("http://bit.ly/2mvbY7").

---

### Post by robert shearer on 2008-10-03
And macpup...
[http://www.puppylinux.org/downloads/puplets/macpup-dingo](http://www.puppylinux.org/downloads/puplets/macpup-dingo)

---

### Post by Misterbadexample on 2008-10-19
Wow, thanks guys. Just following up on this thread since I'm on the forum anyway. Tried a lot of these. They all seem like good solutions. I ended up going with Puppy Transitions for the first computer I'm giving away. It is over 11 years old!

Linux Mint was too big for it. I like it though, might put it on better machines. Macpup was good, but I think was just a little too intimidating for these purposes. Slitaz was in French? Guess I downloaded the wrong ISO.

Transitions was nice and friendly, I think the guy I'm going to give it to will like it just fine. The only things I didn't like were:

I can't edit the grub menu.lst without destroying my installation. I edit the file and suddenly puppy won't shut down properly and won't boot back up. I had to Wipe and install twice because of this. All I wanted to do was change the name of the loader from "Linux" to "Press Enter to continue" to make it simple for my user.

Also, Transitions comes with Firefox 2.something installed by default. It's a little too big for this machine to handle. But I was able to download and set Seamonkey to the default browser with no trouble.

Regardless, great response to my question. Gives me good directions to look into for further solutions to this problem.

---

### Post by chris4585 on 2008-10-19
I'm not too sure how well they would run because I don't know the hardware, but I'm planning on making a series of flavours based off of Ubuntu which will try to be easy, fast, and simple.  I'll stay close to this thread.

---

### Post by Misterbadexample on 2008-10-20
> **chris4585 said:**
> I'm not too sure how well they would run because I don't know the hardware, but I'm planning on making a series of flavours based off of Ubuntu which will try to be easy, fast, and simple.  I'll stay close to this thread.

PM me if you ever get something you're happy with and I'll give it a run. All I can say for hardware, is it'll mostly be x86 architecture, abandoned PCs that used to run XP and Win98.

Like I said in my last post, the one I just restored was 11 years old (!) and runs pretty decently with puppy Transitions on it. Although that's about the only OS I could hope to put on that machine, somewhat newer machines might do well to get an Ubuntu OS.

---

### Post by ghodkiller on 2008-10-20
try slackware / debian ...

[Linux Archive]("http://www.linux-archive.org/")

---

### Post by robert shearer on 2008-10-27
> Also, Transitions comes with Firefox 2.something installed by default. It's a little too big for this machine to handle. But I was able to download and set Seamonkey to the default browser with no trouble.


Dillo is a very light browser and works well on Puppies.

---

