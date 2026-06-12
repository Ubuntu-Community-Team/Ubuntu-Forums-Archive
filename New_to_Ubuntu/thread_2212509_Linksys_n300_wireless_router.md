---
title: "Linksys n300 wireless router"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by devlin3 on 2014-03-21
I have Ubuntu 13.10 on a wireless cpable lenovo laptop. I just bought a Linksys N300 (E1200) wireless router. While trying to set up the wireless router, the set up disc said that my laptop did not have networking capabilities. Ubuntu automatically launched Wine for the set-up disc. I realize this may be more on-topic in the networking and wireless board, but as it is such a basic question, I thought it better to ask here.

---

### Post by pqwoerituytrueiwoq on 2014-03-21
Just use the web ui on the router, i never use CDs for router setup.
Your web UI is probably on one of these 3 links
[http://192.168.1.1/](http://192.168.1.1/)
[http://192.168.100.1/](http://192.168.100.1/)
[http://192.168.0.1/](http://192.168.0.1/)
to get the numbers run [FONT=courier new]ifconfig|grep 'inet addr'[/FONT]
```
$ ifconfig |grep 'inet addr'
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet addr:10.0.0.134  Bcast:10.0.0.255  Mask:255.255.255.0
```
if you notice my laptop's address is [FONT=courier new]10.0.0.134[/FONT], your routers address will be the 1st 3 numbers then a 1, or a 0 in rare cases
in my case it is [FONT=courier new]10.0.0.1[/FONT]

ignore the [FONT=courier new]127.0.0.1[/FONT] address, that is the loop back address a computer uses to talk to itself (yes computers do that also)

---

### Post by devlin3 on 2014-03-21
you'll have to forgive me, I'm not sure what to do with the information you've given me (though it's probably correct).

for the record, this is what shows up on my terminal when i run that command
```
devlin@devlap:~$ ifconfig|grep 'inet addr'
          inet addr: <snip>  Bcast: <snip>  Mask:255.255.240.0
          inet addr:127.0.0.1  Mask:255.0.0.0
```

would you mind giving me a step-by-step?

---

### Post by gifford on 2014-03-21
You need to set up the router while connected to it with ethernet(hard wired).
Then check your inet addr.
The information (web UI addresses) you were given is put in your browsers address line after you are connected via ethernet and it will bring up the configuration window for your router.

---

### Post by pqwoerituytrueiwoq on 2014-03-21
assuming you are using a cable modem you will either need to have the router clone your MAC address or reboot your modem after it is connected to your router.
I assumed you knew you had to connect to your router to access it...

EDIT: You really need to use a firewall if you are going to connect to the Internet directly (without a router), i see you are running a windows share, a nvc server, and 3 other things. You wouldn't want someone to get unwanted access to that stuff would you?

---

### Post by Mark Phelps on 2014-03-21
If memory serves me right, the Linksys setup disk wants to install and run Cisco Connect -- which is a really GOOD app for controlling the Router -- IF -- you are running MS Windows, which you are not.

You're current not using the router because your IP address is the one assigned to you by your ISP.  The router sits between your machine and the Internet, and when you are connected through it, presuming your local router address is something like 192.168.0.1,  your IP address will be something like 192.168.0.100 --presuming that you set up the DHCP server to start assigning addresses starting with xxx.xxx.xxx.100.

Without something like Cisco Connect, setting up a router is not a one-click operation.

My suggestion is that you search the Networking section for threads about setting up this router. They will have the step-by-step activities you will need to perform.

---

### Post by devlin3 on 2014-03-21
copying the MAC and restarting the modem seemed to do the trick
thanks for all your help

---

### Post by pqwoerituytrueiwoq on 2014-03-21
> **devlin3 said:**
> copying the MAC and restarting the modem seemed to do the trick
thanks for all your help
that was overkill, should only require one of thoes
cable modems 'lock on' to a single max address and will only server that single one, a reboot removes the saved max allowing it to 'lock on' to a new one

---

