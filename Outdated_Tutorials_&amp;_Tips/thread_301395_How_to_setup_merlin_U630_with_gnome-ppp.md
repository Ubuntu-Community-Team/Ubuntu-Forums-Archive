---
title: "How to setup merlin U630 with gnome-ppp"
date: 2006-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by YaseenKriel on 2006-11-17
i have a merlin U630 Data card for MTN and it was working under windows until i upgraded to IE7. IE7 now stops the software i need to work the card. So i had to get it working on linux.

First u need to install gnome-ppp

sudo apt-get install gnome-ppp

it should then appear under applications->internet

enter the following:

Username:mtnmms
password:anything
phone no: *99#

insert card, no drivers required for edgy eft, click on setup and then detect modem. It should be /dev/ttyS0 and set your speed. no other configuration required.

Now when u dail-up it will take few seconds to connect and when u open firefox,it should report that its having trouble finding the page. Manually type in an address and u should be surfing.

Hope this helps someone cause it took me three days to get it workin!

---

### Post by jmvidalvia on 2006-11-29
Why this looks that simple while others (including me) have been trying to use complicate ways to run merlin card.
My question: ¿where can I write the pin for the card in gnome-ppp?
Thanks a lot!

---

### Post by YaseenKriel on 2006-12-27
not sure where to add PIN since i do not have one for my SIM. I use a separate SIM for my cell phone and data card. i to have tried all the other ways of getting it work and i think things go wrong when u try get 3G speeds. this way does not use 3G but standard GPRS speeds and thats fine for me since i have broadband at home and i only need access to my emails when i am out of the office.

---

### Post by jmvidalvia on 2006-12-27
I solved it: I put the card in my cellular and just set the PIN no to be asked every time.
Thanks a lot!

---

