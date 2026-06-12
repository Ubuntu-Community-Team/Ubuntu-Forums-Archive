---
title: "9,04 upgrade--&gt; 9.10 and so on"
date: 2009-08-19
forum: Philippine Team
---

### Post by zilu54 on 2009-08-19
gustu ku lang malaman...pwede pu bang i-upgrade ang ubuntu jaunty from PC then pag labas ng karmic eh saka naman patungan naman ng panibagung version?

...since inaabangan ang karmic eh balak kong malagyan muna ulit ng ubuntu ang laptop *tinanggal na kasi dati*

---

### Post by frustphil on 2009-08-19
pwede..for now just install jaunty..you can decide later whether you go fresh install or not for karmic..

---

### Post by loell on 2009-08-19
pwedeh, but in reality, it's not as smooth as intended.
in fact from past to present, the mileage varies greatly.

---

### Post by killer_d76 on 2009-08-19
fresh install is always (in my own opinion) is the best way if you plan to upgrade your distro.. what i'm doing right now is testing the Beta 4 of Karmic Koala on a different HDD (WOW!!!.. :KS:KS:KS ), now if i messed up something, it would be easier for me to go back to the old Jaunty by putting the old HDD back! ;)

oh and don't forget to install **"aptoncd"** so that whatever apps you have downloaded on your Karmic HDD (testing) you can easily install it on your final Karmic!

---

### Post by jepong on 2009-08-19
fresh install din for me kaya its a best practice to keep your /home to another partition para di na kailangan backup. :guitar:

---

### Post by zilu54 on 2009-08-19
oh...ibigsabihin pag fresh install talaga ay as in wala talagang laman ang latest version bagong format ulit?

papaanu naman pu sa mga na install nang mga applications? inkscape, audacity, scribus etc.... may ibang solution pu ba diyan para mailagay ulit sa freshly installed karmic? nakakatamad na kasi mag download ulit.

---

### Post by dodimar on 2009-08-19
> **killer_d76 said:**
> oh and don't forget to install **"aptoncd"** so that whatever apps you have downloaded on your Karmic HDD (testing) you can easily install it on your final Karmic!

Try mo.. so you don't have to re-download the apps..

---

### Post by killer_d76 on 2009-08-19
> **zilu54 said:**
> oh...ibigsabihin pag fresh install talaga ay as in wala talagang laman ang latest version bagong format ulit?

papaanu naman pu sa mga na install nang mga applications? inkscape, audacity, scribus etc.... may ibang solution pu ba diyan para mailagay ulit sa freshly installed karmic? nakakatamad na kasi mag download ulit.

you could try **aptoncd** (sudo apt-get install aptoncd) read some info about this app at [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/") , but if you are referring to apps that you have installed on Jaunty and you plan to move it on Karmic?.. i believe that most apps usually have specific distro versions, you could experiment a bit.. try this.. install aptoncd on your Jaunty (then follow the procedure on how to create an apt on cd! ) and then install Karmic on a virtual machine like virtualbox, then use the .iso image created by aptoncd on your karmic and see if that should work.

---

### Post by frustphil on 2009-08-20
pano ung packages downloaded from PPA's? will it save it automatically and add it to the new sources.list?

---

### Post by guitar_man on 2009-08-20
> **jepong said:**
> fresh install din for me kaya its a best practice to keep your /home to another partition para di na kailangan backup. :guitar:

sir pano to???
tama ba pagkakaintindi ko?
yung /home nasa ibang disk or yung home mo nakaback-up sa ibang disk?:confused::confused:

---

