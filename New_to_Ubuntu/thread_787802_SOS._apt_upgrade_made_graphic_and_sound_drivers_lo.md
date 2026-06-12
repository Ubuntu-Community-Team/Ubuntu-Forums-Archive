---
title: "SOS. apt upgrade made graphic and sound drivers lost"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by caoanroad4800 on 2008-05-09
Hey guys, i'm a VIRGIN to posting on this website, lol :)

I use IBM Thinkpad T43, with ubuntu 8.04 installed. I have a ATI graphics card and also embeded audio card. and i also got compiz-fusion on my system, everthing was just fine.

about 3 hours ago i got a notification of apt showing that there are available upgrades. and i sudo apt-get upgrade it. Then it required reboot. Then nightmire happened:

apt automatically upgraded my kernel from 2.6.24-16 to 2.6.24-17-386. Then i found

1) i lost my audio card driver, now there's no audio output at all.
2) my ati driver doesn't work at all, whenever i open compiz-fusion, everthing is blank on my screen, i can not see anything but white world. There's nothing i can do even i change my boot kernel as 2.6.24-16. I chose to dpkg-reconfigure xserver-xorg and then it's ok with metacity or compiz-fusion, but the speed is intolerable.

Seems it's becaues my automatic-upgrade to kernel 2.6.24-17. HOW can i fix the problems? I'm a totaly newbie and dont know what to do ...


Besides, after upgrade is done, i could no longer turn back to text mode by alt+ctrl+f1 or f2 or f3 ... What's wrong ?

---

### Post by Biggy on 2008-05-09
In terminal type :
> sudo aptitude update
and
> sudo aptitude safe-upgrade

---

