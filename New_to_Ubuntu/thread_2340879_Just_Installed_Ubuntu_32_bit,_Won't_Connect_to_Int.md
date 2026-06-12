---
title: "Just Installed Ubuntu 32 bit, Won't Connect to Internet, Won't Shut Down Properly"
date: 2016-10-22
forum: New to Ubuntu
---

### Post by bashkim2 on 2016-10-22
Hello there,

So I just installed Ubuntu 32 bit on my computer and I am having some trouble configuring it.


First, it won't recognize any wireless networks, and then when I try to shut it down, it will stay stuck at the ubuntu screen.

Any solutions or suggestions?



Thanks

Bashkim

---

### Post by oldos2er on 2016-10-22
Please give us your hardware specs, particularly which wireless device your system has.

---

### Post by yetimon_64 on 2016-10-22
Some advice, and further down the post some handy commands, that may help you get such hardware information for posting in the forum is in [[COLOR=#0000ff]--this thread post--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=1422475") (linked in the blue text). See the "Hardware Information" title a bit down the post for what you want. 

Supplying such information helps the volunteers here to help you. Regards, yeti.

**Edit:** when posting the output from such commands here it also helps us if you use [noparse]```

```[/noparse] tags when composing your reply. Use the advanced editor (Adv Reply) and place the output between such tags by highlighting the output and pressing the "#" symbol on your editors toolbar. Cheers.
 
P.S. Welcome to the forum :-)

---

### Post by RobGoss on 2016-10-22
Hello and welcome, With out providing your hardware information it's going to be kind of hard to pin point your problem 

How did you install Ubuntu USB or DVD?

What software did you use to create the Live media?

Which version of Ubuntu did you install?

---

### Post by bashkim2 on 2016-10-23
Hello there,

Well thanks for the responses.

Anyhow, to answer all of you, I checked the device manager in my computer and under "network adapters" there's three options: 1394 Net Adapter, Broadcom 440x 10/100 Integrated Controller and Dell Wireless 1390 WLAN Mini-Card.

I'm pretty sure that Dell card is what is being used for wireless.

Anyhow, aside from that I installed the Ubuntu 16.10 i386 for 32 bit. I installed via USB, and I am dual booting right now with Windows XP (Which I am using right now).

---

### Post by RobGoss on 2016-10-23
Hello is this your first time installing Ubuntu? if it is I would recommend** 16.04.1** it is a LTS release meaning it's a long term support and might be a better choice 

Addressing your wireless problem, have you install any proprietary drivers? if not open up **software and update**, choose **additional drivers,** choose from the list that's provided. You will need to use a **ethernet cable** in order to install additional drivers

---

### Post by bashkim2 on 2016-10-23
I haven't installed anything.

I pretty much just followed the installation process as it went.

So wait, what exactly do I have to do to get my internet working?

---

### Post by RobGoss on 2016-10-23
Please see post** #6** I left instructions for you to try to get your internet working make sure you have a **Ethernet connection, **in order to get connected to install additional drivers that may be needed

---

### Post by bashkim2 on 2016-10-23
Alright, I'll give that a shot and get back to you.

---

### Post by oldos2er on 2016-10-23
You will need a wired connection to install the package firmware-b43-installer, which I believe might solve the wireless connectivity problem. ```
sudo apt update && sudo apt install firmware-b43-installer
```

It would be nice to know the rest of your hardware specs too.

---

### Post by bashkim2 on 2016-10-23
What other hardware specs?

---

### Post by oldos2er on 2016-10-23
Make and model, RAM, CPU, video card, number and size of hard discs, and anything else you feel might be relevant. The more information you give people to work with, the more likely you are to get useful answers to your questions.

---

### Post by bashkim2 on 2016-10-23
Which hardware specs in particular?

I have a Dell Inspiron E1505 with 2GB of RAM, with a Mobile Intel 945GM Express Video Card (came with laptop), I have a 120gb SSD and Processor: Intel T2300 @ 1.66Ghz.

> **RobGoss said:**
> Please see post** #6** I left instructions for you to try to get your internet working make sure you have a **Ethernet connection, **in order to get connected to install additional drivers that may be needed

Is there a way to download that drive through the internet wirelessly? I'm at a coffee shop working off Wi-FI. I have my USB drive with me, can I use that?

---

### Post by RobGoss on 2016-10-23
As long as you have a connection you should be able to update your drivers as mentioned

---

### Post by jeremy31 on 2016-10-23
Since it seems that the Dell 1390 wireless card is ```
Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
``` from a search I would recommend doing
```
sudo apt-get install firmware-b43-installer
```
If you have an ethernet connection

---

