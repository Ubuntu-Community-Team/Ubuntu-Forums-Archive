---
title: "How To Check Graphics Board Memory"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by pdrollins on 2014-02-27
Hi! I'm trying to figure out how much memory my graphics card has in an Acer Aspire ONE Netbook with an Intel GMA 945 Chipset Famliy. What do I punch in to terminal and where does it say how much?

Thanks in advance!

---

### Post by Frogs Hair on 2014-02-27
Grapics chips unlike cards don't normally have dedicated memory and work with installed ram. You can check free memory with the following command. ```
free  
```


Edit: [Intel 945G chipsets]("https://en.wikipedia.org/w/index.php?title=Intel_945G_chipsets&action=edit&redlink=1"). The processor includes a 400 MHz 256-bit core, supporting up to  10.6GB/s memory bandwidth with DDR2-667 system RAM, up to 224MB max.  video memory through DVMT scheme, 1.6GPixels/s and 1.6GTexels/s fill  rate, a max. resolution of 2048x1536 for both analog and digital  displays, 2 SDVO ports for flat-panels and/or TV-Out via ADD2 cards or  media expansion cards.

---

### Post by deadflowr on 2014-02-27
How's this old command work for you?
```
grep -i memory /var/log/Xorg.0.log
```

---

### Post by Frogs Hair on 2014-02-27
> **deadflowr said:**
> How's this old command work for you?
```
grep -i memory /var/log/Xorg.0.log
```

I get no output but added some info above.

---

### Post by kostkon on 2014-02-27
Yes, usually the onboard intel gma cards use around 250 to 512mb of system ram.

In my case, I get this in dmesg
```
agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
```

---

### Post by tgalati4 on 2014-02-28
If you boot into BIOS, there is normally a setting where you can change how much RAM is set aside for video RAM.  Try different settings to see if it makes a difference.

---

