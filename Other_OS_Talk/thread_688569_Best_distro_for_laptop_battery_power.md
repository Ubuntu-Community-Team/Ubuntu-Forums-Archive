---
title: "Best distro for laptop battery power"
date: 2008-02-05
forum: Other OS Talk
---

### Post by Pogeymanz on 2008-02-05
As far as I can tell, Ubuntu cannot suspend a laptop correctly. This is an important feature for people on the move. I have also heard people complain about battery life from Ubuntu when compared to Windows XP. ( I wouldn't know because my battery failed some time ago)

I know that comparing XP and Gutsy isn't fair because Gutsy is so much newer than XP; I'm just saying I'd like similar battery life.

Are there any distros that are known for being good for laptops in these two areas (sleep mode and battery life)?

---

### Post by smartboyathome on 2008-02-05
I think Arch has sleep mode working, and since it is light it should take up less processing power and give you a better battery life. It is harder to set up though.

---

### Post by Sunflower1970 on 2008-02-05
I think it depends on the kernel....The Feisty kernel would not suspend my laptop (Thinkpad R40) so I upgraded to the Gutsy kernel and all has been fine...(Laptop still uses Feisty...Am waiting for Hardy to do a clean install on it...) I don't know about battery life since the battery is old and doesn't really keep a  charge for long anyway...

---

### Post by fwojciec on 2008-02-05
In my experience the best results are achieved when you set up powersaving manually.  This is the combination of apps/solutions I use:

- Openbox as the WM; main advantage here is that it has no power saving integrated therefore I'm free to set it up the way I want it and nothing interferes with my setup.
- Laptop-mode-tools; takes care of switching CPU governors, dimming screens, managing hard drive powersaving features (I actually switch that feature off completely), readahead, auto-hibernating when battery is low, etc.
- preload; buffers commonly used apps in memory which minimizes hd use.  I'm not sure if there is any tangible benefit to using it though...  I guess it doesn't hurt.
- uswsusp to suspend and hibernate -- this is always tricky to set up as it is highly hardware dependent; I use it in conjunction with my own scripts which unload modules and daemons so that the laptop can resume cleanly; I also need some vbetool tricks to make sure that the screen works after resume; the reason I use uswsusp is because "s2both" command writes the image to disk and then suspends to memory -- that way if the battery runs out while the laptop is suspended I can still resume using the image that was written to the disk. 
- get rid of compositing (disable it in xorg.conf) -- it eats processing power and therefore also battery, it often interferes with suspend in my experience (it also looks tacky, IMO, but that's a personal preference).
- conky -- for reporting stuff such as battery life, cpu governor being used, etc.
- acpid -- for triggering suspend when I close the laptop lid.
- some custom scripts + keybindings -- to do things like switch cpu governors in case I want something other that what laptop-mode-tools uses by default.

As far as distro is concerned -- it doesn't really matter that much, the configuration is more important.  I use Arch Linux, not because it is somehow more energy efficient than other distros but because it has very simple/transparent design and doesn't try to do anything automatically so I can set everything up the way I like it myself.  Automated "just works" solutions never worked for any of the laptops I've used.

It took a lot of experimenting to learn how to set everything up the way I like it but it was definitely worth it.  Once you learn it it takes about 5 minutes to implement everything on a new install (you can recycle scripts and config files).  The laptop I use right now has better battery life in linux than when I had windows installed on it.

If you really want a distro that does everything automatically you'll probably have to try out a lot of different ones before you find one that works reasonably well with your hardware -- I'd go for the big names first: ubuntu, fedora, opensuse, mandriva.

---

### Post by mips on 2008-02-06
> **smartboyathome said:**
> I think Arch has sleep mode working, and since it is light it should take up less processing power and give you a better battery life. It is harder to set up though.


I use Klaptop on Arch and my battery life is pretty good on my hp nx6110.

---

### Post by lespaul_rentals on 2008-02-06
Windows XP.  I hate to admit it, but it's fact.

---

### Post by syga on 2008-10-23
> **lespaul_rentals said:**
> Windows XP.  I hate to admit it, but it's fact.

I also find XP better on battery power and it also runs cooler on my laptop.

My fan turns on about once per hour on XP and about every 10 - 15 minutes with Linux. My hard drive also cycles a lot more with Linux for some reason. In a quiet room, it's really annoying. 

I would really like to use Linux all the time, but I don't like how its taxing my hardware. 

I've experimented with different distros and get the same results.

---

### Post by basenvironment on 2008-10-23
debian
no problems with battery life on my thinkpad r61e
no idea about suspend, dont bother with it

---

