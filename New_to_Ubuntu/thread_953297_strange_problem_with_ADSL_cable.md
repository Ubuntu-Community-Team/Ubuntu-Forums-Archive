---
title: "strange problem with ADSL cable"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by sazan on 2008-10-20
i hav a dual boot system with xp and ubuntu fiesty...

ther is a strange prob i am facing with my net connection.. 

i hav this ADSL connection for which i need to connect it to my LAN card for internet.. whenever i connect this cable in xp..Lan LEDS blink.. xp detects it easily and then i can connect to net and surf it happily..

now when i turn into ubuntu and then connect my cable the LED blinks for a short period of time and then goes away.. then i hav to resest my ADSL power cable.. and give it a try 4-5 times and then finally d LED blinks stable and i can use my net.. 

i hav been facing this problem from last 4-5 days and always i hav to do the same procedure again to use net in ubuntu.. 

can anyone tell me why am i facing this problem in ubuntu whereas i can use net happily in xp.(..the cable has no problem.. )

---

### Post by rolnics on 2008-10-20
I'm confused, why are you unplugging your adsl cable from the pc anyway? Is it the same pc / laptop you are running xp/linux on or is it different pc's

Please give us some more details?

---

### Post by ianhaycox on 2008-10-20
I would guess this is some sort of auto-negociation thing to determine your lan speed. It's possible that each end of the link is flipping between 10 and 100 mbs and a timing issue causes it to fail.

If possible turn off auto-negociation on one end of the link and see if that improves.

---

### Post by sazan on 2008-10-20
> **rolnics said:**
> I'm confused, why are you unplugging your adsl cable from the pc anyway? Is it the same pc / laptop you are running xp/linux on or is it different pc's

Please give us some more details?

yes.. it is the same pc where i hav oth linux and xp  ... i unplug it smtimes so tat i can use the net for other pc..

---

### Post by sazan on 2008-10-20
> **ianhaycox said:**
> I would guess this is some sort of auto-negociation thing to determine your lan speed. It's possible that each end of the link is flipping between 10 and 100 mbs and a timing issue causes it to fail.

If possible turn off auto-negociation on one end of the link and see if that improves.

can i tell me how to turn off auto-negociation ??

---

### Post by ianhaycox on 2008-10-20
It depends on your router/switch or LAN card.

You could try running ethtool from a terminal,

```
sudo ethtool eth0
```

to display options, then, 

e.g.

```
sudo ethtool -s eth0 autoneg off
```

see man ethtool for more options, like setting the speed, etc.

---

### Post by Flyingjester on 2008-10-20
> **sazan said:**
> i hav a dual boot system with xp and ubuntu fiesty...

ther is a strange prob i am facing with my net connection.. 

i hav this ADSL connection for which i need to connect it to my LAN card for internet.. whenever i connect this cable in xp..Lan LEDS blink.. xp detects it easily and then i can connect to net and surf it happily..

now when i turn into ubuntu and then connect my cable the LED blinks for a short period of time and then goes away.. then i hav to resest my ADSL power cable.. and give it a try 4-5 times and then finally d LED blinks stable and i can use my net.. 

i hav been facing this problem from last 4-5 days and always i hav to do the same procedure again to use net in ubuntu.. 

can anyone tell me why am i facing this problem in ubuntu whereas i can use net happily in xp.(..the cable has no problem.. )

buy a router, if it's wired you can pick up one for about 15 bucks nowadays and not have to worry about resyncing your modem to the computers every time.

---

### Post by sazan on 2008-10-20
> **ianhaycox said:**
> It depends on your router/switch or LAN card.

You could try running ethtool from a terminal,

```
sudo ethtool eth0
```

to display options, then, 

e.g.

```
sudo ethtool -s eth0 autoneg off
```

see man ethtool for more options, like setting the speed, etc.



currently i am using some other system outside. i will use those commands as soon as i get into my system.. but thanks a lot for the respone.. i will try those commands and reply back..

---

