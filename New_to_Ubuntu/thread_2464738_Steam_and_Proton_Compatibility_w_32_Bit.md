---
title: "Steam and Proton Compatibility w/ 32 Bit"
date: 2021-07-10
forum: New to Ubuntu
---

### Post by psuedoretropcs on 2021-07-10
Hi all! To make a long story short, I've Googled hi and low for this, and I always end up on forum threads or reddit threads about repositories and the like. But my issue is hopefully a bit simpler.

I'm transitioning all my PCs and laptops to Linux for a variety of reasons. I've run live versions for several weeks on many of them and enjoyed the experience and the pricing.

My place flooded the other day and knocked out my main PC, and I can't replace it that soon. My next most capable desktop is a 32 bit machine. Xubuntu installed like an absolute charm on it. It runs pretty solid all things considered. But I wanted to get some games going, and that's where my problems started.

I know Steam dropped support for 32 but Linux years ago. So the actual Steam app doesn't work well. I quickly found via Google to just access my account via my browser if I wanted to see my library or the store. Cool!

The problem is, in the browser, Steam is telling me that most of my games are incompatible, and if I try to install them via Proton (since many of them are gold or platinum on it that the browser Steam says aren't) it hangs up because Proton is trying to install them through the actual app that can't run. So I can't just install via Proton without the steam app working, but I can't via Steam online either as it says most games won't work.

Is there any easy way around this? Can I somehow trick the steam program? How do I get steam in my browser to agree with proton that I actually do have a lot of games I could run? 

I hope this is clear. Please don't hesitate to ask if not. Thank you for any and all help!

---

### Post by CatKiller on 2021-07-10
It's not entirely clear, no.

The last computers that are really 32-bit-only are ancient, and you wouldn't want to game on them. 

The last release of Ubuntu that provided 32-bit install images was 18.04. Xubuntu 18.04 is no longer supported, since the flavours only get 3 years of support rather than 5.

Steam is a 32-bit application, but it can launch both 32-bit and 64-bit games. In order to do that it needs access to both 32-bit and 64-bit libraries. This isn't *that* big a deal - multiarch is mostly a solved problem - but it nearly caused a falling-out over maintenance, and it's an extra step for users and sometimes gets missed for things like the Nvidia driver packaging. 

If you want to run games from Steam then you pretty much have to use the Steam client. There are quite a lot of games that can be run when the client isn't running, but to download them in the first place you need to go through the client. If you want to run Windows Steam games through Proton (Valve's fork of Wine) then you need to enable it ("use a specific compatibility tool"), either for all titles or for the particular titles you're interested in. ProtonDB is unrelated, and is just a user-submitted independent list. Valve's own compatibility reports are on github, and they have a very short list of officially whitelisted games. 

If you've got Windows games from elsewhere that you're trying to run, there are plenty of Wine helpers, or you can use vanilla Wine. Lutris is pretty easy to use.

---

### Post by ActionParsnip on 2021-07-10
Is the CPU in the system really 32bit? 64bit CPUs have been available on the desktop since the early 2000s. Is the system you are running older than this?

---

### Post by psuedoretropcs on 2021-07-11
> **ActionParsnip said:**
> Is the CPU in the system really 32bit? 64bit CPUs have been available on the desktop since the early 2000s. Is the system you are running older than this?

It is a 32 bit from 2004, yeah. I have a couple modern Chromebooks but I gave away my last couple desktops to family and stuff. I collect 1996-2006 era desktops and laptops and the desktop I have was a beast for it's time, but I'm regretting giving away my 09 and 2015ish era machines now.

> **CatKiller said:**
> It's not entirely clear, no.

The last computers that are really 32-bit-only are ancient, and you wouldn't want to game on them. 

The last release of Ubuntu that provided 32-bit install images was 18.04. Xubuntu 18.04 is no longer supported, since the flavours only get 3 years of support rather than 5.

Steam is a 32-bit application, but it can launch both 32-bit and 64-bit games. In order to do that it needs access to both 32-bit and 64-bit libraries. This isn't *that* big a deal - multiarch is mostly a solved problem - but it nearly caused a falling-out over maintenance, and it's an extra step for users and sometimes gets missed for things like the Nvidia driver packaging. 

If you want to run games from Steam then you pretty much have to use the Steam client. There are quite a lot of games that can be run when the client isn't running, but to download them in the first place you need to go through the client. If you want to run Windows Steam games through Proton (Valve's fork of Wine) then you need to enable it ("use a specific compatibility tool"), either for all titles or for the particular titles you're interested in. ProtonDB is unrelated, and is just a user-submitted independent list. Valve's own compatibility reports are on github, and they have a very short list of officially whitelisted games. 

If you've got Windows games from elsewhere that you're trying to run, there are plenty of Wine helpers, or you can use vanilla Wine. Lutris is pretty easy to use.

Thank you for the response. I'll try to clarify a bit.

I found out that I can access my steam library by running Steam in tiny mode, but it still only lets me download like 10 of my 500 games as it says the rest are incompatible. I can't imagine that that was the case 5 years ago when 32 bit Linux was supported. I guess I'm curious why if I can access my library in small mode, and Proton/forums/etc claim games like Morrowind or Civ IV are compatible, Steam blocks me from downloading them wholesale.

---

### Post by CatKiller on 2021-07-11
> **psuedoretropcs said:**
> I guess I'm curious why if I can access my library in small mode, and Proton/forums/etc claim games like Morrowind or Civ IV are compatible, Steam blocks me from downloading them wholesale.
Those games aren't available for Linux. Proton isn't enabled by default except for whitelisted games: you'd need to enable it yourself.

For best results you're going to want to have Vulkan, which ancient hardware may well not have. I also have no idea if the games you're trying to run are 64-bit (which won't work on 32-bit hardware) or old enough to be 32-bit.

---

### Post by psuedoretropcs on 2021-07-11
> **CatKiller said:**
> Those games aren't available for Linux. Proton isn't enabled by default except for whitelisted games: you'd need to enable it yourself.

For best results you're going to want to have Vulkan, which ancient hardware may well not have. I also have no idea if the games you're trying to run are 64-bit (which won't work on 32-bit hardware) or old enough to be 32-bit.

Awesome, thanks, I'll install Vulkan.

I have Proton enabled for all games in steam play and have restarted my PC a couple times since then. Maybe I'll do a fresh install of Steam too.

---

### Post by mastablasta on 2021-07-12
> **psuedoretropcs said:**
> Awesome, thanks, I'll install Vulkan.

I have Proton enabled for all games in steam play and have restarted my PC a couple times since then. Maybe I'll do a fresh install of Steam too.

we still don't know your system specs. must be Pentium. vulkan works on latest GPU chips. well relatively new ones.

Morrowind works natively in OpenMW.

Civilization 4 works in wine, but you would probably have to install steam through wine and then add Civ4. if you had a GOG version it is not really hard to get it going.

i just retired (maybe only temporarily) a 2004 Single core Athlon. it was a 64 bit CPU and paired with nvidia GT730 it could play some games.

---

