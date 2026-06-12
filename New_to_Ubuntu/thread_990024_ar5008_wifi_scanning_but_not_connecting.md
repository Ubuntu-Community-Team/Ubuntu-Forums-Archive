---
title: "ar5008 wifi scanning but not connecting"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by mortuk on 2008-11-22
Hi

I own an asus eee 1000, and I have swapped out the stock wifi pcie card, for a gigabyte gn-wi06n atheros 5008 card.

I am running 8.10 with the custon eee kernel linux-headers-2.6.27-7-eeepc and cannot get the wifi working. i can scan and see AP's but I cannot connect to anything

Any ideas?

---

### Post by mortuk on 2008-11-22
anyone??

have got the madwifi trunk using subversion

did make, make install, then modprobe ath_pci but still no joy, any ideas?

---

### Post by NoobBiscUiT on 2009-01-12
at least you have something, 

i have the same card in my dell mini and i get no wireless after numerous madwifi installs.

im having the same problem though.

---

### Post by diectus on 2009-01-28
Im using the same card and nothing will connect if I use anything but 2.6.27-11. Im also using the ath9k driver and I replaced NetworkManager with WICD and now I can at least connect to my netgear b/g router. but I cant connect to my dlink n router which is what I wanted the card for anyway so its kind of a wash but at least I got the card working.

---

### Post by Zeosz on 2009-06-21
I have had the same card and a dell mini 9 as well.  It scans fine, and will even get into monitor mode and shows all the netowrks in my area.  The only way I've gotten it to connect to a wireless network has been using BackTrack 3.

I'd be curious to try WICD though, that sounds like a decent solution since I'm not really shooting for N speeds, just functionality.

EDIT: Thanks a ton diectus, the WICD network manager did the trick for me too.  I haven't tried to connect to an N router but it certainly works for my Linksys G router.

---

