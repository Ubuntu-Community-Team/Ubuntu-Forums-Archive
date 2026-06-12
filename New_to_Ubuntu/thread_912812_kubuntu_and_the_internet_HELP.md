---
title: "kubuntu and the internet HELP"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by asgharjon on 2008-09-07
HI, 

I am an absolute new to linux user.
I installed kubuntu yesterday, along with XP on my comp.
Everything is fine, but the thing is I cant get the WIFI to work, 
I cant get it to see any networks , or connect to my own. The computer uses a lynksis wireless.G usb connected device for wifi, is it because linux does not support it?

please help, 
thank you

---

### Post by forger on 2008-09-07
We will need more than that, can you open up the konsole application and execute this:
```
lsusb
sudo lshw -C network
```

Post a reply with the full output of that command

---

### Post by Crafty Kisses on 2008-09-07
Kubuntu is very good about including proprietary drivers and supports wireless cards very well. It's probably already working, you just need to configure it to use with your wireless network.

Try this command:
```
iwconfig
```


It should report back which interface supports wireless extensions. That's the network interface assigned to your wireless card. For my laptop, for example, it's eth1.

You can simply use the graphical network setup tool to configure your wireless card, or you can do it through the command line. If you like, I can post some screenshots of how to do that.

---

