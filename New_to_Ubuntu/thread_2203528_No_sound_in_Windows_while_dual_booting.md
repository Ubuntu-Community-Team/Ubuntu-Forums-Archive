---
title: "No sound in Windows while dual booting"
date: 2014-02-03
forum: New to Ubuntu
---

### Post by matt53 on 2014-02-03
So I just got my computer dual booting windows 7 and ubuntu. I'm a first time user of Ubuntu, and I'm loving it so far, but for some reason, I have been unable to get sound working in Windows 7. I have no probelm with sound in Ubuntu, but when I switch over to Windows, I get nothing. The weird part is that Windows sound did work through the HDMI, but when I used the HDMI in Ubuntu, it stopped working in windows. I have tried installing every driver under the sun for Windows and have gotten nowhere. is there something ubuntu does that stops other operating systems from using audio or something? Once again, I don't know much about Ubuntu, but I would really like get both operating systems working.

Thanks for you help!
Matt

---

### Post by gerowen on 2014-02-03
> **matt53 said:**
> So I just got my computer dual booting windows 7 and ubuntu. I'm a first time user of Ubuntu, and I'm loving it so far, but for some reason, I have been unable to get sound working in Windows 7. I have no probelm with sound in Ubuntu, but when I switch over to Windows, I get nothing. The weird part is that Windows sound did work through the HDMI, but when I used the HDMI in Ubuntu, it stopped working in windows. I have tried installing every driver under the sun for Windows and have gotten nowhere. is there something ubuntu does that stops other operating systems from using audio or something? Once again, I don't know much about Ubuntu, but I would really like get both operating systems working.

Thanks for you help!
Matt

Check your sound devices in the Control Panel and make sure it's working properly.  If you go to the Control Panel and set it to display as "Small Icons" instead of categories, then click the "Sound" icon, you should have the option to switch between sound devices, just make sure you're set to the correct one.

---

### Post by matt53 on 2014-02-04
It's kind of weird. In windows, my speakers don't even show up. The HDMI does, but doesn't play, then I have an S/PDIF device that also shows up even though I don't have anything connected to it. None of them make sound. I had this machine using only windows for a while, and it all worked then so I know its not a driver issue (because I had all the drivers backed up, and I'm using the same one). I figured it must be something weird with how Ubuntu handles audio.

---

### Post by Mark Phelps on 2014-02-04
> I have been unable to get sound working in Windows 7.

Then ... I would post the concern in a Win7 forum -- sevenforums.com is a good place to start.

---

### Post by matt53 on 2014-02-04
i did and the people over there all said to come over here because it probably had something to do with linux not "letting go" of the hardware. I guess the answer I'm getting is "no dice" haha. Thanks anyway!

---

### Post by oldfred on 2014-02-04
Does a full power down and reboot then work with Windows? If a laptop you may have to remove battery & hold power key to dissipate capacitors.

My old XP motherboard would not give sound after every audio driver update unless I unplugged speakers from motherboard & replugged them in. It was somehow software configured and wanted to know which port really was speakers.

---

### Post by matt53 on 2014-02-06
> **oldfred said:**
> Does a full power down and reboot then work with Windows? If a laptop you may have to remove battery & hold power key to dissipate capacitors.

My old XP motherboard would not give sound after every audio driver update unless I unplugged speakers from motherboard & replugged them in. It was somehow software configured and wanted to know which port really was speakers.

I have seen that suggested in a few other threads, but it doesn't seem to work for me. I have tried powering up with the speakers in, powering up then plugging them in. I'm starting to think i may just need different speakers for linux and windows, which seems kind of silly.

Edit: I should add that my mother board is somewhat old. I got it in ~2009, so I'm not sure if that would affect things, but it may. I am planning on upgrading my hardware some time within the next few months.

---

### Post by Vladlenin5000 on 2014-02-06
What motherboard exactly? 
2009 isn't that old but it may have some "bug" in the handling of onboard or other devices for which may or may not have been release a BIOS update already. Also the "plug&play OS yes/no" setting might have something to do with it.

---

