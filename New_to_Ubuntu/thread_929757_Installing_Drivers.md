---
title: "Installing Drivers???"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by kingtut35 on 2008-09-25
Ubuntu doesn't recognize my ethernet card.  I have a p5ql pro asus motherboard and i have the drivers but i'm new to linux and i dont really know how to install drivers.  I finally got this installed to dual boot with xp after a long night of changing ide to ahci without reinstalling xp. Now i need a little more help please

---

### Post by aeiah on 2008-09-25
are you sure it doesnt? go in the terminal and type ```
ifconfig
```

it should tell you what's available. ethernet will be eth0 or eth1

---

### Post by Bölvaður on 2008-09-25
ndiswrapper is the program you need to use. It makes windows drivers for wireless cards work on linux.

You can find everything you need by searching these forums, try search words like "wlan0 windows driver" wlan0 is often the logical name of your wireless hardware, other can be simply just "wireless".

But all you probably need to do is install ndiswrapper from synaptic package manager found under System &#8594; Administra... &#8594; Synaptic Packa...
(note that I was lazy and wrote ... instaed of letters ^^ )

Then open ndiswrapper either by typing ndiswrapper in terminal or find it under applications in the menu. When you are asked where the windows driver is then you have to browse to it and press ok.
ndiswrapper will then tell you if the driver is ok or not.


other threads will give you more detailed information so please search this forum if you run into problems

---

### Post by PierreDeKat on 2008-09-25
Yeah, ditto what Bölvaður said.

---

### Post by Bölvaður on 2008-09-25
commands that might help you realize what the computer detects.

iwconfig
ifconfig

and you might want to add parameters behind each. found out by typing --help after the name of the program

like:  ifconfig --help


I know this is confuseing but perhaps it will be useful later on (like 1 month from now)

---

### Post by kingtut35 on 2008-09-25
thanks guys.  its not wireless its my wired port also.

---

### Post by kingtut35 on 2008-09-25
i looked to install ndiswrapper and it wasn't found.  I typed it into the terminal as well.  I also have the linux drivers that came with my motherboard not just the windows.  I'm just struggling to get on the internet.

---

### Post by StunnerAlpha on 2008-09-25
What if I wanted to intall drivers specific to my computer? I have a Thinkpad T60 and want my ultranav buttons to work properly. How would i go about installing those?

---

### Post by Tatty on 2008-09-25
> **kingtut35 said:**
> thanks guys.  its not wireless its my wired port also.

Wow, I have never heard of a wired ethernet port not working of-of-the-box in ubuntu.  Are you absolutely sure it is not working?  Can you give a description of how far you have got with this and where it goes wrong?
Which version of ubuntu are you using?

Also, presuming you are currently physically plugged in to your network, if you could open a terminal and post the output of ```
ifconfig
```


> **kingtut35 said:**
> i looked to install ndiswrapper and it wasn't found.  I typed it into the terminal as well.  I also have the linux drivers that came with my motherboard not just the windows.  I'm just struggling to get on the internet.

There are several methods of installing software and drivers in linux, the one you need to use depends on what your motherboard manufacturer has given you.
Do you have any instructions included on installing?  If not then what do you appear to have file-wise - is it a .tar.gz?

---

### Post by Tatty on 2008-09-25
> **StunnerAlpha said:**
> What if I wanted to intall drivers specific to my computer? I have a Thinkpad T60 and want my ultranav buttons to work properly. How would i go about installing those?

Hi Stunner,  It would be best for you to open a new thread for this question.  Its best to stick to one question per thread on this forum to prevent things getting confusing :)

---

### Post by StunnerAlpha on 2008-09-25
> **Tatty said:**
> Hi Stunner,  It would be best for you to open a new thread for this question.  Its best to stick to one question per thread on this forum to prevent things getting confusing :)

Alright cool, thought they were similar enough to be shared since we are both looking to install drivers. Thanks though.

---

### Post by cariboo on 2008-09-25
TO the origional poster run in a Applications-->Accessories-->Terminal:

```
sudo lshw -C network
```

this will list the specifics about your network card. Then we will be able to give some assistance in getting the nic to work.

Jim

---

