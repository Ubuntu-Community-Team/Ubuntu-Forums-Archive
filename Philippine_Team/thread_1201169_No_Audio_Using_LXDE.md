---
title: "No Audio Using LXDE"
date: 2009-06-30
forum: Philippine Team
---

### Post by sieg06 on 2009-06-30
isa pa ito sa problema ko sa LXDE. bakit po naka mute ang audio once na nakainstall ang LXDE. how can i unmute the audio? wala po kasi sa panel ang icon na audio. nag iinstall ko ang jaunty ok naman ang audio ng maginstall ako ng lxde nakaunmute ang audio. i try na alisin ang lxde at unmute ko ang audio sa jaunty gumagana. ng install ko ulit ang LXDE naka mute ulit ang audio ko. help po mga bosing

---

### Post by dannybuntu on 2009-07-01
Mukang busy mga expert natin. Try kitang tulungan pero hindi ako magaling...

Ok? 

1. Open Terminal
2. $ sudo apt-get install aumix
3. $ aumix
4. adjust mo volume, master, pci

Pag hindi ito nagwork, sa totoo lang hindi ko na alam. 

Try mo rin tignan kung naka plug in sa tamang lugar yung audio jack.

btw: nangyari na rin sa akin yang ganyang problema = lalo na pag 2 ang sound card - on board at pci. Frankenstein kasi tong pc ko. Puros luma mga piyesa. sira yung onboard sound card kaya nag install ako ng second hand na audio card... napansin ko na nag mu mute siya. So inaadjust ko na lang volume through aumix or gnome-alsamixer = kung alin man ang nakainstall.

---

### Post by vidgen13 on 2009-07-02
pre try mo install ung "alsautils" pag ayaw gumana. tapos mag "sudo alactl" ka para idetect soundcard mo, tapos mag "alsamixer" ka tapos taas mo lahat ng volume. un lng po

---

