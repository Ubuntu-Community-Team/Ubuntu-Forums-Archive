---
title: "Dual monitor issues"
date: 2015-08-02
forum: New to Ubuntu
---

### Post by Tigendo on 2015-08-02
Ubuntu is not allowing me to use my second monitor. Will this be corrected when I install the nVidia drivers i need to?

I have been so busy with 10-12 hour days at work, I cannot spend extended amounts of time fixing things.

Any advise would be greatly appreciated.

---

### Post by oldos2er on 2015-08-02
What version of Ubuntu? Which Nvidia card? I would guess the answer to your question is yes, but it would be better to have more info.

---

### Post by Tigendo on 2015-08-02
sorry i left this out. 

It is Ubuntu 14.04.2 LTS and the video card is nVidia GeForce 750 Ti

---

### Post by oldos2er on 2015-08-02
Ah, same card I use. The version 346 proprietary drivers in the repositories should allow you to use both monitors. See [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) for more info.

---

### Post by Tigendo on 2015-08-02
thank you, i had to manually DL the drivers from nvidia and will be  loading them when i get home. For some reason the proprietary did not  show in SOftware and updates.

---

### Post by oldos2er on 2015-08-02
Be aware if you choose to manually install Nvidia drivers from a downloaded *.run file, you will need to reinstall them after any kernel update. It is *far* easier to install from the repos or a PPA, so that if there is an kernel update all will be taken care of for you.

See [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) and note the first sentence.

---

### Post by Tigendo on 2015-08-02
I tried doing:

sudo apt-get update

but the proprietary drivers never showed in Software and Updates. I am not sure what I am doing wrong. Everything I have read says that it should be there.

---

### Post by oldos2er on 2015-08-02
Maybe 14.04 doesn't have the 346 drivers yet; check out the xorg-edgers PPA, [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty)

---

### Post by Tigendo on 2015-08-03
Thank you again for all of your help. Everything is working fine now. I am able to use both monitors, the resolution is proper. Life is Awesome. Now I am going to play around with themes and what not. Looking for something ultra futuristic

---

