---
title: "I installed ubuntu 12.04 on my inspiron 1018 and the wireless is not working."
date: 2012-07-18
forum: New to Ubuntu
---

### Post by Aw35omeAnth0ny on 2012-07-18
Im an absolute beginner (as the post signifies) and the only reason I downloaded ubuntu is because my school gave us netbooks pre-loaded with ubuntu 10.04 netbook edition. Wanting an upgrade, I downloaded 12.04. When I click the network icon on the top of the screen wireless is greyed out and I know for a fact the wireless "switch" is on because I tired pressing it and it didn't work.

I've read on other forums to try rfkill list all and rfkill unblock all and they didnt work

rfkill list all just gave me these results:

0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

And to my understanding hard-blocked is not a good thing. Im a teenage boy, without access to the Internet. PLEASE. HELP.

---

### Post by Nerdishman on 2012-07-18
you can try "sudo etc /init.d/networking restart" but that will reset ALL network settings to default (DHCP)

---

### Post by techvish81 on 2012-07-18
have you tried to install additional driver  (type "driver" in the dash) ? if not try to connect to internet with dsl or phone and install if any available.

---

### Post by Finnicella on 2012-07-18
Did you try?:
```
sudo rfkill unblock all
```

---

### Post by anewguy on 2012-07-18
You may want to look through the posts from [this]("http://www.google.com/search?q=ubuntu+12.04+dell+inspirion+1018+wireless&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs").  Don't worry if some aren't for your device.  Read through and get ideas.

---

