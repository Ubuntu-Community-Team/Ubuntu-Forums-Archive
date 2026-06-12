---
title: "Tether Linux to Droid without the net"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by Eragon615 on 2011-12-02
So I recently installed Ubuntu on my computer in order to create a chrootable image to run for my Android tablet. I like the operating system, but I realized soon that if you don't have internet that it doesn't do much. Most installers use the apt-get command and since I have no internet I basically have a stock OS. I was interested in tethering my Droid thunderbolt to it, but all the guides use internet to set up the files! This is a desktop, so I can't just take it to a Starbucks. Anyone help me out?

---

### Post by waynefoutz on 2011-12-02
easytether is the only one in the Android market with an Ubuntu/Debian client.

[http://www.mobile-stream.com/easytether/android.html]("http://www.mobile-stream.com/easytether/android.html")

Install it on your phone, then install the .deb file on your computer. Connect the two, open up a terminal and type

```
easytether connect
```

then just minimize the terminal window, don't close it. Pretty easy.

---

### Post by Eragon615 on 2011-12-02
Great! Dunno how I managed to not find this with all the searching I did... Only one problem. The easy tether site gives me a deb. Which you need the net to download, right? I'll search for source, but can anyone offer advise? I'm still real new to Linux, so please be patient.

---

### Post by waynefoutz on 2011-12-04
> **Eragon615 said:**
> Great! Dunno how I managed to not find this with all the searching I did... Only one problem. The easy tether site gives me a deb. Which you need the net to download, right? I'll search for source, but can anyone offer advise? I'm still real new to Linux, so please be patient.

you should be able to download the .deb with your phone, then transfer it over from the microsd card to your computer with the usb cable.

---

### Post by Dubslow on 2011-12-04
> **waynefoutz said:**
> you should be able to download the .deb with your phone, then transfer it over from the microsd card to your computer with the usb cable.

That's how I did it, in fact it gave me instructions where to find the .deb in the phone's memory.

---

### Post by Eragon615 on 2011-12-04
That's exactly what I did. But the .Deb install button is greyed out and won't let me click it. Since it was such a small file and said Ubuntu software center,I assumed it download from the net.   So any idea why my .Deb doesn't wanna work? It says don't install software except from trusted sources, but there's no buttons or anything to confirm that I trust it. Hmm.

---

