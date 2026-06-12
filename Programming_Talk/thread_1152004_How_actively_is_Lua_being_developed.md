---
title: "How actively is Lua being developed?"
date: 2009-05-07
forum: Programming Talk
---

### Post by Portmanteaufu on 2009-05-07
I stumbled upon Lua a little bit ago and I must say I really like the idea of it. Adding a scripting interface to just about anything seems worth it to me. :D

I know it's used extensively in a few programs (e.g. World of Warcraft and Adobe Lightroom), but it seems like every time I find a library for it or an article about it it's from two years ago or more. Is it still going strong? If I take the time to learn it and add it to all my code is it going to go belly-up the next day?

Thanks!

---

### Post by crazyfuturamanoob on 2009-05-07
Almost all recent games can be scripted with lua. Some random lua-scriptable games: Left4Dead (and other Source games), Cortex Command, BZFlag, Toribash, Spring, Crysis, Neverwinter Nights.

---

### Post by Portmanteaufu on 2009-05-07
Thanks for the reply! I was hoping that someone might have some insight into its actual development, though, rather than other projects in which it's used. It looks as though the current edition (5.1) was released a few years ago in 2006.

I'd be especially appreciative if anyone could tell me whether the elementTree project (the Lua one, not the Python one) was still moving forward. I can't seem to find much information there either.

---

### Post by jimi_hendrix on 2009-05-08
well the thing with lua is that i think it is designed to be embedded, not to make apps...so you wont find many apps around made solely with it

correct me if i am wrong

---

### Post by ibuclaw on 2009-05-08
> **jimi_hendrix said:**
> well the thing with lua is that i think it is designed to be embedded, not to make apps...so you wont find many apps around made solely with it

correct me if i am wrong

I do know of one game - [Mexican Motor Mafia]("http://www.scienceoftomorrow.com/mmm_main.htm") (it's a non-free game that you have to pay for, so don't get your hopes up ;)) - where the entire game scenario/AI/gameplay/maps is written solely in lua (using dds images and ogg sound files), and can be modded per-say to add "in-game" features.

Infact, the only part of it that isn't lua are the binary executable wrapper, graphics engine, and fmod library, which is most likely in C++...

---

### Post by asm_Coty on 2009-05-08
PSP homebrew apps are coded with Lua :)

---

### Post by crazyfuturamanoob on 2009-05-09
> **asm_Coty said:**
> PSP homebrew apps are coded with Lua :)

Nah, they're coded in C/C++.

There is a Lua interpreter for PSP which can execute Lua scripts/apps.

---

### Post by samjh on 2009-05-09
Lua is still under active development.  New point releases are coming out every several months.  Although 5.1 was released in 2006, the latest point release, 5.1.4 was releated last year.

It has become very mature, and the language does what it intended to do extremely well.  Improvements are now incremental.  Don't break it if it ain't broke... :)

---

### Post by Portmanteaufu on 2009-05-11
> **samjh said:**
> Lua is still under active development.  New point releases are coming out every several months.  Although 5.1 was released in 2006, the latest point release, 5.1.4 was releated last year.

It has become very mature, and the language does what it intended to do extremely well.  Improvements are now incremental.  Don't break it if it ain't broke... :)

Ahh, great to hear! Thanks!

---

