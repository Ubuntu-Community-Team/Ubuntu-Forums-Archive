---
title: "[SOLVED] how to know computer specs"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by mkarnicki on 2008-06-07
Hi guys,

We recently gave a low-end PC to my grandpas (my grandma uses ubuntu with no hustle! she rocks :D ), and I would like to upgrade her PC's processor, but she lives in another town. Currently she has Pentium II (?) on socket 370 at 800MHz, and 192MB RAM.

How do I get eg. her motherboard model, etc. I have a remote connection to her desktop, which works flawless, so I do have remote access to her computer. Will I find a motherboard model in dmesg dump? Or should I look for it somewhere in the GUI?

Thanks,
Mike

---

### Post by Rhubarb on 2008-06-07
If it's a socket 370 CPU running at 800MHz, it'd have to be a pentium 3 / celeron.
The RAM is most likely PC133 (not sure the max memory + memory slots it has).

You should be able to slot in a P3 1GHz in there without problems (if you can find one).
The motherboard should be able to take 512MB RAM no problems, and it'd have an 8x AGP slot for video card.

I'm not too sure how to find out those specs remotely though.
Good luck ;)

---

### Post by bumanie on 2008-06-07
Not 100% sure, but I guess it would show up in a long list of harware. > sudo lshw

PS: Of course a certain amount of specs are shown via the initial asci script during POST.

---

### Post by Elos on 2008-06-07
tried this when i am using windows last time . not sure if it works in ubuntu, go google cpuz , download it and run , it should show your computer specs

---

### Post by mkarnicki on 2008-06-07
Thank you guys, I appreciate fast response!

**@Rhubarb** She has 128+64 MB SDRAM, but actually my main problem was to check with what processors (and max MHz) is the motherboard compatible

**@bumanie** Thank you! Exactly what I needed.

---

### Post by mkarnicki on 2008-06-07
Thanks to you bumanie I know every detail of that remote PC, thanks !

product: VT82C693A/694x [Apollo PRO133x] (<--- what I needed)
Pentium III 500MHz (dang, I thought it was more!)
320 MB RAM (256+64)

Now I can check how fast (1.0, 1.2 or maybe 1.4?) processor will fit the motherboard. Cheers!

---

### Post by MikeBrown on 2008-11-10
Thanks! I happened to stumble upon this post and was curious about the hardware in my Computer, which is a 4+ year old computer I put Ubuntu 8.10 on tonight to test out. I found your post very helpful, once I realised that was an 'L' not an 'I' in the command. 

Thanks for helping out an Ubuntu n00b!

---

### Post by lisati on 2008-11-10
The following will give some interesting information about your machine's specs:
```
sudo dmidecode
```

---

