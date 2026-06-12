---
title: "How to resume paused download?"
date: 2012-01-21
forum: Philippine Team
---

### Post by Whongsky on 2012-01-21
Mga Sir, patulong naman po regarding dito.

[ATTACH]211219[/ATTACH]

Paano ko po mare-resume itong dina-download kong Ubuntu 11.10 ISO file? Nsa 200mb+ na po kasi sya and then pinose*(pause)* ko po yung download. Nung ire-resume ko na po sya, yan na po yung nangyari? May posible way pa po ba para mai-resume ko yung download ko? Medyo may kabagalan po kasi ang internet connection namin kaya hanggat maaari ayaw ko na po sanang magsimula sa umpisa. (wag naman sana). And Google Chrome po ang ginagamit kong browser.

Maraming salamat po in advance! Sana po matulungan nyo ako.

---

### Post by Script Warlock on 2012-01-21
bitorrent sana ginamit mo para magdownload ng iso or any important files. try mo [link]("http://www.google.com/support/forum/p/Chrome/thread?tid=73cd99d09433b3b3&hl=en")

---

### Post by kiminaiseah on 2012-01-21
> **Whongsky said:**
> Mga Sir, patulong naman po regarding dito.

[ATTACH]211219[/ATTACH]

Paano ko po mare-resume itong dina-download kong Ubuntu 11.10 ISO file? Nsa 200mb+ na po kasi sya and then pinose*(pause)* ko po yung download. Nung ire-resume ko na po sya, yan na po yung nangyari? May posible way pa po ba para mai-resume ko yung download ko? Medyo may kabagalan po kasi ang internet connection namin kaya hanggat maaari ayaw ko na po sanang magsimula sa umpisa. (wag naman sana). And Google Chrome po ang ginagamit kong browser.

Maraming salamat po in advance! Sana po matulungan nyo ako.

in terminal

wget --tries=0 -c <URL>

then i re-type mo lang ulit pag na disconnect net mo

okay rin ang bit torrent pero pag proxified ang ISP mo like using 3G/HSPA Modems, torrent are impossible, but sometime nakaka tagos

---

### Post by Whongsky on 2012-01-22
> **Script Warlock said:**
> bitorrent sana ginamit mo para magdownload ng iso or any important files. try mo [link]("http://www.google.com/support/forum/p/Chrome/thread?tid=73cd99d09433b3b3&hl=en")

Hindi ko po naisip yung option na yun sir. Nasa isip ko lang kasi e maka-download ng iso para mai-install ko sya ulit. Hindi ko naman po kasi akalain na ganun pala ang mangyayari. Anyway, maraming salamat sa tulong sir!

> **kiminaiseah said:**
> in terminal

wget --tries=0 -c <URL>

then i re-type mo lang ulit pag na disconnect net mo

okay rin ang bit torrent pero pag proxified ang ISP mo like using 3G/HSPA Modems, torrent are impossible, but sometime nakaka tagos

Dinaan ko na lang sa tyaga sir! And I'm already using it right now! :D Thanks for help!

---

### Post by kiminaiseah on 2012-01-25
your welcome, 

enjoy using ubuntu =)

---

### Post by pinoyskull on 2012-01-26
best is to download Ubuntu ISOs thru bittorrent :)

---

### Post by kiminaiseah on 2012-01-26
alternative to wget

---

multi part or multi session download

axel

apt-get install axel

axel -n <# of download part> <url>

---

