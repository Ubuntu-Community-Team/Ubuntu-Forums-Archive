---
title: "slow wifi RT3062 in ubuntu 12.04 x64 alternate install"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by nutpants on 2012-04-27
just installed 12.04 from the alternate x64 install image and while my ralink RT3062 wireless works,, is is running at less than 10% of the speed of my wired connection.
i have read and tried every slow wifi page i could find on google..
nothing has increased the speed at all.

it is running at 1.7 Mbps on wifi g  (yes my router is only g but should get up to 4 Mbps)

(there have been reports that the oem driver works better but im looking to fix the ubuntu driver)

---

### Post by ratcheer on 2012-04-27
My rt3062 requires the installation of a proprietary driver from Ralink. I have rarely gotten it to work with the standard kernel driver, and on those occasions, it was as you describe - extremely slow.

Please post the output of "sudo lspci -v". Just the section for your wireless card, please.

Tim

---

### Post by nutpants on 2012-04-27
decided just to install the oem drivers..
following the directions here
[http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux](http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux)

ill keep playing when i install my other computer with the same card,
then ill be back.

thank you for your interest..

---

