---
title: "OS override?"
date: 2011-10-10
forum: Philippine Team
---

### Post by ihazpower on 2011-10-10
guys patulong
d ko malaman kung ano mali ko..
meron kc ako new pc sa office,una kong ininstall ung ubuntun 10.04
meron ako 500gb na hd at napartition ng sumusunod
100mb /boot
4gb - swap
150gb /
100gb /home

meron p qng ntitiring 250gb reserved q sa windows ksi tnetesting q p ung ad nmin windows2003server(para mapaglaruan q)

fully setup n ung ubuntu, nalikewise q na at na dl na lahat ng packages n kelangan q..after nun ininstall q nman ung windows sa isang partition, nung ok na lahat sa windows...
khit anong try kong restart d q mkta ung option ng os..rekta sa windows :(

p.s. d q ksi mgets ung sa mga ngoogle ko..hehe

---

### Post by @Craw on 2011-10-10
Ang dapat diyan is Windows muna ang ininstall mo then Ubuntu.

---

### Post by ihazpower on 2011-10-10
> **@Craw said:**
> Ang dapat diyan is Windows muna ang ininstall mo then Ubuntu.

yan ang karamihan nkkta q..hehe pero baka meron p ibang paraan

---

### Post by zeroseven0183 on 2011-10-10
Most likely nagalaw na ng Windows yung MBR nyan kaya hindi na makita ang Ubuntu. Tingnan mo dito kung meron kang na-skip na step [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) So far updated naman ang documentation na yan as of August this year hehehe

---

### Post by tech-hero on 2011-10-10
> **zeroseven0183 said:**
> Most likely nagalaw na ng Windows yung MBR nyan kaya hindi na makita ang Ubuntu. Tingnan mo dito kung meron kang na-skip na step [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) So far updated naman ang documentation na yan as of August this year hehehe
may ways pa jan. pero kailangan mo gumamit yata ng Live CD. aayusin mo ang Master Boot Record mo. mas madali yun kesa mag reinstall ka ulit na uunahin ang windows etc.

---

### Post by ihazpower on 2011-10-10
> **tech-hero said:**
> may ways pa jan. pero kailangan mo gumamit yata ng Live CD. aayusin mo ang Master Boot Record mo. mas madali yun kesa mag reinstall ka ulit na uunahin ang windows etc.

windows live cd b or ubuntu sir? :) teach me how to dougie, do it pala hehe

---

### Post by zeroseven0183 on 2011-10-12
Ubuntu Live CD pwede. Dito yung instructions [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I think naka grub2 yan so eto dapat [http://www.bitsbythepound.com/reinstall-grub2-after-installing-windows-334.html](http://www.bitsbythepound.com/reinstall-grub2-after-installing-windows-334.html)

---

### Post by ihazpower on 2011-10-12
> **zeroseven0183 said:**
> Ubuntu Live CD pwede. Dito yung instructions [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I think naka grub2 yan so eto dapat [http://www.bitsbythepound.com/reinstall-grub2-after-installing-windows-334.html](http://www.bitsbythepound.com/reinstall-grub2-after-installing-windows-334.html)

haha :)) sarap magkaproblema noh..dami natutuhan
thanks

---

### Post by tech-hero on 2011-10-13
goodluck! nagkaganyan din ako dati.

---

