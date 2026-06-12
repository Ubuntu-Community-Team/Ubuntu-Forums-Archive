---
title: "Playing VCD Videos"
date: 2008-07-01
forum: Philippine Team
---

### Post by ache109 on 2008-07-01
Guys,

Please help me naman,

I'd having a hard time on playing .dat files on ubuntu.. (even on vbox via WMA). It states na the "file format is not supported". I tried to install VLC but no luck. But nung naka XP pa ako ok naman nagpeplay naman..
ano kaya ito???

---

### Post by wersdaluv on 2008-07-01
> **ache109 said:**
> Guys,

Please help me naman,

I'd having a hard time on playing .dat files on ubuntu.. (even on vbox via WMA). It states na the "file format is not supported". I tried to install VLC but no luck. But nung naka XP pa ako ok naman nagpeplay naman..
ano kaya ito???

Tuwing may ganyan kang issue, try Synaptic. :)

---

### Post by pendletone on 2008-07-01
Teka ano ibig mong sabihin nung sinabi mong "i tried to install vlc but no luck"?

You mean nde mo ma-install yung VLC, or nde gumagana yung VCD sa VLC?

---

### Post by ache109 on 2008-07-01
> **pendletone said:**
> Teka ano ibig mong sabihin nung sinabi mong "i tried to install vlc but no luck"?

You mean nde mo ma-install yung VLC, or nde gumagana yung VCD sa VLC?

yah, hindi gumagana ung VCD sa VLC.. Pero on the mpegs.. it's ok naman...

---

### Post by Samhain13 on 2008-07-01
VCD? Sa VLC:

1. File > Open
2. Punta ka sa Disc tab.
3. Tapos yung "Disc Type", "VCD" dapat.
4. Dun sa ibaba, "Customise", may makikita kang ganito: "vcdx:///dev/scd0". Tanggalin mo yung **x** dun sa "vcdx" para maging "vcd://"... lang siya.
5. Click OK.

Kung tumatalon-talon yun sound, balikan mo yung steps 1-4. Pero i-check mo yung "Stream/Save" tapos punta ka sa "Settings...". I-check mo yung "Play Locally". Click "OK", tapos "OK" ulit.

So far, lahat ng VCD ko dito gumagana sa ganiyang paraan. Pero nung huli ko itong ni-share, may hindi daw gumagana. Subukan mo na lang. :)

---

### Post by pendletone on 2008-07-01
Pinili mo ba yung **VCD option** nung sinubukan mong i-open yung VCD mo via Open Disc from the File menu?

As an alternative, try opening your disc in VLC thru the terminal:

```
vlc vcd:///dev/dvd
```

If all else fail, try using MPlayer instead. Ok rin yan.

---

### Post by Samhain13 on 2008-07-13
Ha! I remember reading this thread and have I got an alternate solution for you. It may not be to your liking though as it requires you to rip your VCD. Hehehe! But if you're willing to try, here's something that I wrote in my journal:

[http://www.abcruz.com/?args=Journal/The_Memphis_Report/2008-07-13_Ripping_VCDs_with_VLC.xhtml](http://www.abcruz.com/?args=Journal/The_Memphis_Report/2008-07-13_Ripping_VCDs_with_VLC.xhtml)

---

### Post by kabotage on 2008-07-30
> **Samhain13 said:**
> VCD? Sa VLC:

1. File > Open
2. Punta ka sa Disc tab.
3. Tapos yung "Disc Type", "VCD" dapat.
4. Dun sa ibaba, "Customise", may makikita kang ganito: "vcdx:///dev/scd0". Tanggalin mo yung **x** dun sa "vcdx" para maging "vcd://"... lang siya.
5. Click OK.

Kung tumatalon-talon yun sound, balikan mo yung steps 1-4. Pero i-check mo yung "Stream/Save" tapos punta ka sa "Settings...". I-check mo yung "Play Locally". Click "OK", tapos "OK" ulit.

So far, lahat ng VCD ko dito gumagana sa ganiyang paraan. Pero nung huli ko itong ni-share, may hindi daw gumagana. Subukan mo na lang. :)

salamat sir.. pero tumatalon prin yung audio. :confused:

---

### Post by initial_m on 2008-07-30
Dag dag lang mga parekoy, ung sa prob ko naman DVD, im using totem, di gumagana ung menu ng DVD's ko, ewan ko kung bakit..any suggestions/ideas mga bros will be highly appreciated...:KS

---

### Post by Samhain13 on 2008-07-30
> **kabotage said:**
> salamat sir.. pero tumatalon prin yung audio. :confused:

Yun nga ang hindi ko naiintindihan eh. Sa Gutsy, hindi naman ganiyan. Kaya ang ginagawa ko ngayon, rip to mpeg muna para local file ang papanoorin ko. :confused:

---

### Post by king leoric on 2008-07-31
Alternative ko sa VLC ay MPlayer. Works like a charm than VLC. sa experience ko lang yun ha. pero para sa akin ay Mplayer talaga. Can play .dat file din ng vcd

---

### Post by Samhain13 on 2008-07-31
> **kabotage said:**
> salamat sir.. pero tumatalon prin yung audio. :confused:

Heto, follow up. Nakuha ko yung idea galing dito:
[http://ph.ubuntuforums.com/showthread.php?p=4844334#post4844334](http://ph.ubuntuforums.com/showthread.php?p=4844334#post4844334)

Patayin mo yun PulseAudio sa System Monitor, and if you follow the steps that I give in the post that you quoted, hindi na tatalon-talon yung sound. Kakagawa ko lang so alam kong gumagana (sa box ko, at least). :guitar:

---

### Post by kabotage on 2008-08-01
> **Samhain13 said:**
> 
Patayin mo yun PulseAudio sa System Monitor, and if you follow the steps that I give in the post that you quoted, hindi na tatalon-talon yung sound. Kakagawa ko lang so alam kong gumagana (sa box ko, at least). :guitar:

haha.. worked like a champ! :guitar:

---

### Post by Samhain13 on 2008-08-01
Nice, nice! :D

---

