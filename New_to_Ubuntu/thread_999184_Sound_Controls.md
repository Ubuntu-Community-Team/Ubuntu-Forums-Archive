---
title: "Sound Controls"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Stormspace on 2008-12-01
I'm running 8.04 currently as my primary desktop at home. It's great! I do have one noobish issue that I hope someone here can help me with. 

My Sound Blaster Live! value card works fine in that digital sound goes to the speakers where I can then control the volume from the pot on the speakers. However none of the system controls will allow me to adjust the volume. How do I fix this? I've tried changing the defaults in the sound settings but nothing works.

---

### Post by gettinoriginal on 2008-12-09
Do you have alsa installed ??  Try here and good luck :p

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by Stormspace on 2008-12-09
```
user@mpc-ubuntu:~$ sudo apt-get install alsa
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
user@pc-ubuntu:~$ 
```

I guess you want me to install from source?

---

### Post by gettinoriginal on 2008-12-09
Well, from that post, it appears you already have it. Try typing alsamixer in a terminal and see what settings you get, you can increase it if need be.

---

### Post by redseventyseven on 2008-12-09
No, that means it's already installed OK.

Sound is still a slightly thorny issue in Linux as there can be several sound "servers" operating concurrently. Alsa is just one of those. Others include Pulse. I still don't really know too much about the ins and outs of Linux sound but I may be able to help a bit.

Open up a terminal window and type **alsamixer** (followed by Enter). Do you see a range of different volume controls (represented in terminal font) or just one? If it's just one, then check to see if you have Pulse installed as well.

Hope that helps! If there's anything you don't understand then please say so!

---

### Post by Stormspace on 2008-12-09
```
Card: SBLive! Value [CT4871]                                                 &#9474;
&#9474; Chip: Cirrus Logic CS4297A rev 4                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-40.50, -40.50]                                        &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;                        &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;  &#9474;                        &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;                        &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;                        &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9484;&#9472;&#9472;&#9488;     &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;MM&#9474;              &#9474;MM&#9474;      &#9474;MM&#9474;                       &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                       &#9474;
&#9474;   57<>57   13<>13              0<>0                       50<>50   50<>50    &#9474;
&#9474; < Master >Headphon  Headphon Headphon Headphon    Tone     Bass    Treble    
```

---

