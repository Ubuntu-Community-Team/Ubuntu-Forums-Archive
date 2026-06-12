---
title: "wireless problems"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by brucegriffin on 2008-08-27
I want to connect to the internet through a wireless card. I do have a wireless airlink 101 usb  adapter model awll3028. Can anyone tell me if I can get it to work maybe through wine. Or someone can let me know if there is either a usb wireless adapter or a cardbus that I can buy that will work right out of the box for my laptop. It doesn't have a built in wireless card. Thanks.

---

### Post by sboy on 2008-08-28
Ah, wireless cards. The great demon of linux users everywhere. As far as I know there is no reliable support for any usb wireless adapters. Your best bet is probably to get a card. I picked mine up online for ten bucks or so. As for which one to get, pick one off [http://madwifi.or/wiki/Compatibility](http://madwifi.or/wiki/Compatibility) . The trick is to get an Atheros chipset.. they tend play nice with linux.

If you're really devoted to the usb, you might be able to do something with ndiswrapper, but it probably won't be as stable. Trying to run a driver through wine is probably a very bad idea, just seems like inviting frustration to me.

---

### Post by Crafty Kisses on 2008-08-28
Post results of this command:
```
lshw -C network
```

---

### Post by Kevbert on 2008-08-28
Please take a look at this [[COLOR="Red"]page[/COLOR]]("http://madwifi.org/").

---

