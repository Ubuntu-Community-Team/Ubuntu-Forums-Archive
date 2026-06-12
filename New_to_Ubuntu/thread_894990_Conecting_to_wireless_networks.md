---
title: "Conecting to wireless networks"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Breeman on 2008-08-19
Hi, Im haveing problems conecting to wireless networks under 8.04(I believe). Im using Ndiswrapper for my Linksys WMP300N. I've gotten a good conction once after I set of Ndiswrapper and no other time. Does anyone have any segistions?

---

### Post by brandoncolorado on 2008-08-19
This may be of some help

[https://answers.launchpad.net/ubuntu/+question/3973](https://answers.launchpad.net/ubuntu/+question/3973)

---

### Post by Breeman on 2008-08-19
I used that in my orginal set up of the wireless and it worked fine till I turned off the computer.

---

### Post by anewguy on 2008-08-19
If it worked until you rebooted, then you probably need to have ndiswrapper get started by the system.  Try this:

(1) sudo ndiswrapper -m

(2) sudo gedit /etc/modules

at the end of that file press <enter> and add the following, if it is not already there:

ndiswrapper

Now save the file and exit, then reboot and see if it is working.

---

### Post by nicedude on 2008-08-19
Your pci wifi adapter has a Atheros AR5416 wifi chipset inside and as such I would recommend you learn about and then install a proper Madwifi driver and ditch Ndiswrapper. Madwifi drivers are supperior to using Ndis in many ways but can be tough to install. Fortunately their are many guides etc to installing them on these forums and others. I have an AR5007 so the driver I use is different than the one you need but you just need to use the chipset I list above and find some instructions on how to do it.

Here is a post where a guy says he has his working in Kubuntu ( same thing for our purposes as Ubuntu ) with Madwifi r3123
[http://ubuntuforums.org/showthread.php?t=668272](http://ubuntuforums.org/showthread.php?t=668272)

Hope this helps you out.

---

### Post by iaskedalice09 on 2008-08-20
Hi!

I'm a newb myself so I hope I can help. Click the Internet icon on the top bar (looks like two computers when disconnected, when connected, looks like the Cingular bars thing), pick Connect To Another Wireless Network or Create New Wireless Network. Enter the info and click connect. It should show a little chaser thing as a circle...that means it's searching. It worked for me out of the box that way.

I hope you get your Internet working! Good Luck!

---

