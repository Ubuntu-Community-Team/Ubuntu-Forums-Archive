---
title: "VCD and DvD problem"
date: 2009-02-07
forum: Philippine Team
---

### Post by guitar_man on 2009-02-07
gandang gabi...
mga ubunturero...I'm trying to play vcd and dvd on my laptop but it wont play.
Files like .DAT wont play on Totem and Mplayer.I've installed all the codec and plugins for both of the players.
And when I play DVD(pirated);) there would be a audio problem.
I dont know if its a hardware problem,cause I'm running Hardy on my Desktop and it can play VCD and DVD,even though they're from Quiapo:lolflag:


Any suggestions...


Salamat..:D

---

### Post by adredz on 2009-02-07
VLC. try it...

---

### Post by Tomatz on 2009-02-07
> **guitar_man said:**
> gandang gabi...
mga ubunturero...I'm trying to play vcd and dvd on my laptop but it wont play.
Files like .DAT wont play on Totem and Mplayer.I've installed all the codec and plugins for both of the players.
And when I play DVD(pirated);) there would be a audio problem.
I dont know if its a hardware problem,cause I'm running Hardy on my Desktop and it can play VCD and DVD,even though they're from Quiapo:lolflag:


Any suggestions...


Salamat..:D

Open a terminal and copy and paste thge following text and press enter/return (one at a time):

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
```

```
sudo dpkg -i libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
```

**Logout and login**

Now you will have dvd playback ;)

---

### Post by guitar_man on 2009-02-07
@Tomatz


ginoong Tomatz....ito ung mga file para sa medibuntu diba?

---

### Post by Tomatz on 2009-02-07
> **guitar_man said:**
> @Tomatz


ginoong Tomatz....ito ung mga file para sa medibuntu diba?

Im English, sorry i cant understand you :(

---

### Post by guitar_man on 2009-02-07
oh I'm so sorry...

just let me translate it in english



Mr Tomatz.....are this the files for the medibuntu?:D

---

### Post by Tomatz on 2009-02-07
> **guitar_man said:**
> oh I'm so sorry...

just let me translate it in english



Mr Tomatz.....are this the files for the medibuntu?:D

No Problem. I should have realised the post was in the Philippine Team forum. :/

Yes **libdvdcss2** is part of the mediabuntu repository. ;)

---

### Post by guitar_man on 2009-02-07
@Tomatz



its ok....Thank you so much for the help...Appreciate the help...
I'm watching 'Saving Private Ryan' right now.:lolflag:
Nice to know that there were some people viewing the Philippine Team Threads.
GB

---

### Post by guitar_man on 2009-02-07
@adresz
sir salamat din;)

---

### Post by Tomatz on 2009-02-07
> **guitar_man said:**
> @Tomatz



its ok....Thank you so much for the help...Appreciate the help...
I'm watching 'Saving Private Ryan' right now.:lolflag:
Nice to know that there were some people viewing the Philippine Team Threads.
GB

No problem, glad its fixed ;)

---

