---
title: "Just Upgraded my RAM, but..."
date: 2014-04-24
forum: New to Ubuntu
---

### Post by joelorenzo on 2014-04-24
Hey guys,
I just upgraded my RAM on my Toshiba Satellite from a 2 gig config to a 3 gig one, BUT I keep getting random pixelation scrambles on my screen. Is this a result of say a bad RAM card, did I screw this up, or is it something else entirely. 

(Ignore my Economics Homework :guitar: )

Any and all advice is mucho appreciated-o

Cheers,
Joe

---

### Post by jbaerboc on 2014-04-24
I wouldn't see how ram could impact screen drawing. Only thing I can think of is the video card was bumped, cable was bumped, or something like that.

---

### Post by coldcritter64 on 2014-04-24
> _*keep getting*_ random pixelation
By "keep getting", does than mean you had that problem before upgrading your RAM as well _*or*_ has it started since upgrading ? 

That looks more like a graphics issue to me than a ram issue. What graphics card / drivers are you using ?

Edit: if this started with the ram upgrade, check the seating of your graphics card/cabling now, as jbaerboc alludes to.

---

### Post by joelorenzo on 2014-04-25
Roger that, to clarify: this started to happen AFTER ram card upgrade. Will check on graphics card/cable and report back. 
As far as graphics go; I'm running Mobile intel GM45 express chipset x86/mmx/sse2 (if that helps, cause i dont know)

---

### Post by 5-tim on 2014-04-25
It could be bad memory, or poorly seated memory, as that video card uses system memory for Video memory.  Try reseating it, and if that doesn't help, remove it.  If that does help, it's probably bad memory.  If that doesn't, you managed to knock a cable loose or there;s something else wrong with your monitor or video card (Perhaps you banged it too hard while having the laptop upside down?)

---

### Post by sudodus on 2014-04-25
Run ***memtest*** from the grub menu to check the memory. It should run for hours without a single error. If you don't see the grub menu during a normal boot, press a shift key during boot to make it appear.

---

### Post by WoodenWalker on 2014-04-25
Does memory not often need to go in pairs? Ex. If you have one 2G stick you would need to pair it with another 2G stick with the same specs. Correct me if I am wrong someone, that's how we always do it at work, so I'm curious now.

---

### Post by mcduck on 2014-04-25
> **WoodenWalker said:**
> Does memory not often need to go in pairs? Ex. If you have one 2G stick you would need to pair it with another 2G stick with the same specs. Correct me if I am wrong someone, that's how we always do it at work, so I'm curious now.

It's not a requirement, you can install just one stick, but you get better performance from using two smaller memory modules than one big one since the memory controller on modern CPU's usually has two (or more separate memory channels it can use).

So, both a single 2GB module or two 1GB modules are fine, but using the two modules on different memory channels gives twice the bandwidth between CPU and memory.

---

### Post by WoodenWalker on 2014-04-25
Oh okay. Thanks for the clarification. I figured it had something to do with most systems being dual channel now, but my knowledge of hardware is kinda lacking. Lol. I was just confused about how OP went from 2G ram to 3G ram. Sounded kinda strange to me.

---

### Post by trag on 2014-04-25
with two unequal sized sticks of ram the larger of the two must be placed into a specific slot,I think I'm correct on this point.

---

### Post by jbaerboc on 2014-04-27
> **5-tim said:**
> It could be bad memory, or poorly seated memory, as that video card uses system memory for Video memory.  Try reseating it, and if that doesn't help, remove it.  If that does help, it's probably bad memory.  If that doesn't, you managed to knock a cable loose or there;s something else wrong with your monitor or video card (Perhaps you banged it too hard while having the laptop upside down?)

Good point, I didn't think of that possibility for the OP.

---

### Post by moshefeit on 2014-04-27
Maybe CAS Latency problem?

[http://www.hardwaresecrets.com/article/Understanding-RAM-Timings/26/3](http://www.hardwaresecrets.com/article/Understanding-RAM-Timings/26/3)

?

---

