---
title: "Wireless Issues T60p Hardy Heron"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by abgemacht on 2008-07-01
Hello,

I recently installed Ubuntu 8.04 on my T60p.  So far, it's been working very well and I'm really enjoying it.

When I was at school, I was able to connect to the wireless internet by left clicking on the network icon in the top right and selecting the network that was in range.  No problems.

I'm now back at home and it detects my wireless router, but when I try to connect, it tries for about 5 minutes and then says it is unable to.  I have been able to connect to the wireless router with other computers, so I don't think that's the issue.

Please let me know what additional information would be useful.

Thanks in advance!

---

### Post by jingo811 on 2008-07-01
Maybe your router has its WiFi security set so that only certain MAC-addresses can connect to your router?  That is only chosen Wireless Network Cards are listed in your router.
I think you should dive into your router and check that things are OK in there.

---

### Post by abgemacht on 2008-07-01
I have people over a lot and they've never had trouble connecting to the router.  I'll take a look and see if anything's changed, though.

Thanks

---

### Post by jingo811 on 2008-07-01
Hmm does these CLI commands report anything meaningful to you?
```
ifconfig
```
```
iwconfig
```

Maybe you need to refresh your DHCP ip every now and then.
```
sudo dhclient
```

---

### Post by Sydius on 2008-07-01
[http://ubuntuforums.org/showthread.php?t=841529](http://ubuntuforums.org/showthread.php?t=841529)

I just fixed my similar problem. :-D

Specifically:
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

I'm using a ThinkPad X60s.

---

### Post by abgemacht on 2008-07-01
Awesome!

That download did the trick.  Thanks to both of you for your time!

---

