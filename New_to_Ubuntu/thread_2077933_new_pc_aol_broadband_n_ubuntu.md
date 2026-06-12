---
title: "new pc aol broadband n ubuntu"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by merciaol on 2012-10-29
hi, ive just got a new pc with no os ,ive installed ubuntu from a usb onto it. however im having problems with my isp aol broadband (uk)the modem bt yoyager 105 has one green light on (the power). i usually have to use an aol cd with drivers for it to work on windows. what can i do ?

---

### Post by grahammechanical on 2012-10-29
The issue is not so much the BT voyager but the network card/adapter in the machine. Does Ubuntu recognise the network card?

Look at the top panel to the right. Do you see the network icon. It should look like an upside down cone.

Click on it. A menu should drop down. If you see a list of wireless networks that are in range, then your wireless adapter is being recognised by Ubuntu. You need to select your network and enter the information required to connect to the router.

We assume that your router is already programmed to connect to your ISP when you switch it on.

On the bottom of my router I have this information:

Router address:
Router user:
Router password:
Wireless name:
Wireless key:

Do you have similar information? When you try to connect to your netwrok (router) you will be asked to authenticate the connection. That is when you put in the wireless key. Be careful to use capital letters if there are capital letters in the wireless key.

That should do it. At least it did for me when I just established a wireless connection on a new install that I am testing.

If your problem is getting the router to connect to the ISP, then you should tell us. And we will help you there.

Regards.

---

### Post by merciaol on 2012-10-29
its not a wireless connection i use an usb* cable, the cone is there and it said i had a wired connnction( i think now it says last used 1 day ago) but when i tried to open firefox it said i didnt have an internet connection i googled and found some other ideas for example one was to typed in some numbers into the browser but that didnt work. its a new pc as of today i read on ubuntu that i dont need other drivers but on the dvd that came with the pc it has drivers software

---

### Post by Mark Phelps on 2012-10-30
> **merciaol said:**
> ... but on the dvd that came with the pc it has drivers software

Those are Windows drivers -- you can't use them in Linux.

---

### Post by merciaol on 2012-10-30
will installing my old windows xp in virtual box and then installing aol broadband software on that work?

---

### Post by merciaol on 2012-10-30
ok it seems to be the bt voyager 105 modem any idea what modems will suffice

---

### Post by pqwoerituytrueiwoq on 2012-10-30
only pci modem i know that will work is some tp link ones and that is on 10.04 32bit, and that takes some work, and some googling
if you can get a usb 56k modem that should work, to my knowledge [this one](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134008) works

---

### Post by squakie on 2012-10-30
When you say AOL Broadband N, I would assume you might mean a DSL connection?

---

### Post by pandacookie on 2012-10-30
Are there instructions for installing AOL Broadband in Linux? Because in my experience with AOL Broadband, it works only in Windows. At least the drivers they provide do. Maybe AOL has changed in the years since I've used it, but as far as I know, it works only in Windows.

---

### Post by Mark Phelps on 2012-10-30
> **merciaol said:**
> will installing my old windows xp in virtual box and then installing aol broadband software on that work?

Sorry, don't use VB much, but my guess is that while they MIGHT work and provide you Internet access while inside the XP in VB, once you exit that, you are likely to lose the connection. This doesn't sound like what you want to do.

---

### Post by merciaol on 2012-10-30
thanks ... anyway ive managed to do it , i just replaced the bt voyager 'modem' and hey presto it works

---

### Post by pandacookie on 2012-10-30
> **merciaol said:**
> thanks ... anyway ive managed to do it , i just replaced the bt voyager 'modem' and hey presto it works

Great! I love being proven wrong in cases like this.

If you don't mind, would you scroll up to thread tools and mark this as "solved"? Thanks! :)

---

