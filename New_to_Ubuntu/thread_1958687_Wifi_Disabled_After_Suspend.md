---
title: "Wifi Disabled After Suspend"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by EternalDecree on 2012-04-14
I have my laptop set to 'suspend' (I assume this is like 'sleep' on Windows) when I shut the lid. Upon wake-up I no longer have wifi. The wifi light on the front of my computer is still on but it does not display any available networks and I cannot find a way to re-enable my connection. I have even rebooted the system with no luck. My wireless card is an Atheros AR242x, I am running Ubuntu 11.10.

Thank you so much for your help!

---

### Post by daslinkard on 2012-04-14
You can try this [link]("http://askubuntu.com/questions/67280/wireless-doesnt-connect-after-suspend-on-an-asus-k52f")

or possibly you could type this sudo command each time

```
sudo service network-manager restart
```

---

### Post by EternalDecree on 2012-04-14
I've been playing around with it some more. I tried your suggestion, daslinkard, and read the page you linked to but nothing is working. If I reboot the system it still does not work. Even if I reboot and load Windows my wifi does not work in Windows. 

The only way I have solved this problem is by doing a full shutdown. Only then does my wifi work in Windows and/or Ubuntu after starting the computer.

Any idea why it is different when I reboot vs. shutdown? Also, any idea why this effects Windows as well?

Thank you :)

---

