---
title: "Installing USB Linksys wireless-g with ndiwsrapper"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by gaza on 2006-06-04
The linksys wireless-G v4 I've got is not supported by default in Dapper (or Breezy, or any other). ;)

So here's a small how-to for those dealing with the same problem I've dealt with. Which is without internet connection, getting your usb wireless to work.

First of all, you're gonna need: Your Dapper CD, the Wireless-g drivers. (Put those drivers in your computer. You can't install them from the drivers cd.)

OK first, install Dapper. 

Once you're done installing, and are already logged in, insert the Dapper CD back into your cd rom. You'll be prompted to use the Package Manager to install packages. Say "yes".

Do a search for ndiswrapper, and when "ndiswrapper-utils" show up... install it.

OK. good. :)

Now you wanna do

```
sudo /usr/sbin/ndiswrapper -i /path/to/card/drivers/driverfile.inf
```

Make sure you direct your ndiswrapper to the file with the ".inf" extension. And make sure you work these commands with SUDO.

Now type

```
sudo depmod -a
```

Now to load the module type:

```
sudo modprobe ndiswrapper
```

OK, if you've gotten no errors or spooky stuff. You're probably done.

Connect your wireless-G card.

What I did next was simply to go to System > Administration > Networking through the graphical interface. Then I simply deactivated the Ethernet connection (because I'm not using it). And activated my WLAN connection.

Lauch firefox. Enjoy it.

I hope it works! :D

---

### Post by knichel on 2006-09-26
I was trying to follow, but I get the following error...

knichel@knichel:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

Any ideas?  Im somewhat of a noob.

--
TIA
Mike

---

### Post by flotsaminthecosmicsea on 2006-10-28
I've done everything you all said to and have gotten my interenet to work! Thanks, but now I have to go through the "sudo depmod -a" and "sudo modprobe ndiswrapper" steps everytime I start up my computer. How do I make this fix permanent?

---

