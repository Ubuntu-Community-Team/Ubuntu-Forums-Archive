---
title: "Gaming on Ubuntu"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by nlraley on 2008-08-26
How is gaming on Ubuntu?  I am strongly thinking about swapping over to Ubuntu as being my main OS, and was wandering how its holding up with the newer games, especially DX10 games.

Can you run these games alright in WINE?

Or would it be possible to virtualize Vista or XP and run the games on the virtualization without taking a huge hit in the performace?  Or are there no virtualization programs out there that will load the drivers and actually use my system's actual hardware?  

I know Virtual PC replicates "junk" bare minimum drivers in order to fully function and you aren't actually using your hardware to its full extent.  Does VM Ware or the Sun xVM actually set up your right hardware through the virtualization?

Is this a possibility or am I going to be stuck having to dual boot?

---

### Post by Crafty Kisses on 2008-08-26
A lot of games can run good in Wine, like Counter-Strike and WoW, it just depends on what you play.

---

### Post by starcannon on 2008-08-26
There is no DX10 for Linux; however, some games are able to be played using wine, or cedega. That  said, there is a performance hit; for now, if one of your important uses is gaming, I would suggest either dual booting or sticking with windows. High end gaming hasn't made it here or to Mac yet, I have faith it will arrive eventually though.

GL and have fun.

---

### Post by halitech on 2008-08-26
Frozen Bubble2 works like a charm ;)

---

### Post by Crafty Kisses on 2008-08-26
I really don't like Cedega. I'd rather just use Wine.

---

### Post by Separ on 2008-08-26
Wine will not run DX10 but there are a lot of games that work really well. Most Steam games work perfectly for me after a bit of tweaking to the wine registry and winecfg.

Have a look at the [Wine AppDB]("http://appdb.winehq.org") to see what will work and what won't.

---

### Post by starcannon on 2008-08-26
> **Codename said:**
> I really don't like Cedega. I'd rather just use Wine.

Thats fine, I use both, depends on the game. Eventually I want to buy a copy of CrossOver as well.

---

### Post by Crafty Kisses on 2008-08-26
Yeah, CrossOver seems to work well with a lot of games.

---

### Post by nlraley on 2008-08-26
Is virtualizing Windows going to be a possibility?  Or are you going to run into problems with the drivers it tries to install as its bare minimum to run?

---

### Post by nlraley on 2008-08-26
Oh, and you mentioned WoW.  Would I be able to max out my settings with that with no problems or am I going to have to tone everything down considerably if I'm using Ubuntu and Wine.

---

### Post by starcannon on 2008-08-26
A virtual machine is just what it sounds like, so it has virtual guts, including a virtual video card. You can get games to install, but running them... well... lets just say the framerates leave something to be desired.

It'd be great if the virtual machine folks could get the actual hardware to pass through to the VM but it must be a very technically difficult task as I am not aware of anyone having done it yet.

Anyway, short answer, virtualization is not in my opinion a good way to try to do gaming. HOWEVER, you could run Ubuntu in a Virtual Machine on your windows desktop, you won't have all the trick compiz effects though, for reasons already mentioned.

---

### Post by Separ on 2008-08-26
> **nlraley said:**
> Oh, and you mentioned WoW.  Would I be able to max out my settings with that with no problems or am I going to have to tone everything down considerably if I'm using Ubuntu and Wine.

Depending if your video card can cope with max settings :p

Works on max for me in wine with a 9600GT at around 80-90FPS.

See the [WowWiki]("http://www.wowwiki.com/Linux/Wine#Configuration") for tips on improved frame rates with opengl.

---

### Post by nlraley on 2008-08-26
What about addons?  Are they going to be screwed?

---

### Post by nlraley on 2008-08-27
Just to keep you guys updated, my programming instructor suggested I try out VM Ware, he seems to think it will let me select my appropriate hardware and therefore not be loading up the bare minimum drivers that the virtualization software uses to reference back to the main os.  

He seems to believe, but isn't positive, that VM Ware allows a certain level of abstraction that will allow you to set up the appropriate hardware of your system and run the drivers meant for the hardware.

I'll keep you guys posted on how it works once I finish downloading Ubuntu again.  64-bit wouldn't install of Virtual PC b/c of them loading up these raw drivers, and wasn't detecting my processor as actually being 64-bit.  So I'm downloading it again and going to give VM Ware a shot.

Anyone have any of the input on addons in WoW yet?  Know a few have said they have ran it on Wine, but how well does it play with all of my addons?  Or am I going to have to try to recompile them?

---

