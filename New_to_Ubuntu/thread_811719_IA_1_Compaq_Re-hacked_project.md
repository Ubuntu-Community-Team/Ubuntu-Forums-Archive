---
title: "IA 1 Compaq Re-hacked project"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by yogo on 2008-05-29
I have had an IA1 collecting dust for many years, since they first came out. Never have I used this machine, other than I recall it had a bad firmware update from Compaq back years ago.

Anyways, I was looking at an eeecPC on Newegg and that got me thinking why not play around with hacking my dust collecting IA1.  A little Windex and it looks bran new. So I went to the guides that have been around for centuries and soon found out I had one of the unhackable ones. After a couple of hours unsuccessful last night, I started this morning and finally got into BIOS. I had put in what I thought was new batteries in the keyboard last night but put in another set today just to make sure.

So now when in BIOS, it shows my boot order as Floppy, which I assume is my compact flash card. I have no other choices for boot order so again I assume my sansdisk no longer works.

So here is what I would like to do, put Linux on it ?? Jailbait?? not really but probably for trial. I only have two compact flash cards from back in the day, one is 16mb and the other is 128.  DSL would be nice for the 128 but I will have to find that one.

Something I thought of but probably next to impossible is, I would like to be able boot from USB but I imagine that would mean flashing the BIOS to add booting from USB as an option.

So as I have it with BIOS set to boot from Floppy, if I have a bootable CF card, will it then boot?

PS. I swear I am not blind, but I could not see inside that second whole on the motherboard cover for the life of me. Man that was eye straining!

Thanks for all suggestions and advice on a formerly hot project that is now DOA.

---

### Post by wolfen69 on 2008-05-29
if it is showing floppy as first boot device in BIOS, then it means floppy, not sd card. your computer will not boot from flash card. a bios update will not change anything. does it have a cd rom? if so, you could boot to floppy first, then to DSL. go to the DSL homepage for more info on different boot methods.

---

### Post by yogo on 2008-05-29
> **wolfen69 said:**
> if it is showing floppy as first boot device in BIOS,

I think you are wrong there...? It has no Floppy and none of these units ever came with a Floppy, so I think that does mean compact flash in this case.

I included this link as it shows what this unit is.

[http://realprogrammers.com/hack/IA-1/disassembly.html](http://realprogrammers.com/hack/IA-1/disassembly.html)

Also I was not sure where to place this thread here so I figured this was the best place,mods feel free to move it if suited better elsewhere.

We are talking a machine that was built back in 2000 so I think the BIOS means CF in replace of Floppy.

ETA

I found this in one of the many a guides out there. I will keep trying and see if I get other boot options.

[FONT=Verdana][SIZE=3] In the change Boot sequence screen, I've seen a case where only A: was shown and a case where only A: and C: were shown. If this happens, repeat the previous steps until A:, C: and D: are there.[/SIZE][/FONT]

---

### Post by yogo on 2008-05-29
Patience is a virtue at times. I stuck with it, on and off  and in and out of BIOS about three times and I now have it set to boot D first, then C second so I should be good to go, now all I have to do is either flash the sansdisk with a bootable new image of just make a bootable CF.

---

### Post by yogo on 2008-05-29
I have put DSL on a compact flash card but need  to get it ironed out. I did it via Pendrive Linux, but the method was designed for XP so I may need to do some tweaking. I am out to get a new card reading as two I have have troubles with CF.

Most tutorials are written for Windows so I may have to resort, I have a dual boot, almost never use XP but for this it may work better.

Tips, suggestions are welcome.

---

### Post by yogo on 2008-05-29
Well it was easier than I thought, this took all but a couple of seconds, I read so many tutorials and so many had troubles in so many different ways that I was not expecting this to go so easy, now I no longer have a project.

Screenshot attached with DSL running.

---

