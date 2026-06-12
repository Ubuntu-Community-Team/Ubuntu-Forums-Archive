---
title: "wireless problems"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by Devo88 on 2012-08-06
hi ive just installed ubuntu 12.04 on my laptop. it has built in wireless but i cant find my wireless network.
it works fine with the ethernet cable plugged in.
im totally new to ubuntu and have no idea what to do. 
can anyone help?

---

### Post by 2blue on 2012-08-06
If you haven`t done it already I would start update manager, let it download and install all updates (there is probably a large list of updates), then reboot and take it from there. There is an application for activating some hardware that can be found in menue-preferances-additional hardware, it might detect something too. Make a new post and you will get further help if needed. 

There is a FAQ for all kinds of issues that are common fixes for all that needs attention.

---

### Post by Devo88 on 2012-08-06
ive already done the updates and tried additional drivers but that didnt do anything

---

### Post by gifford on 2012-08-06
Did you activate the wireless connection? When you installed Ubuntu and did the updating, was this using the wired connection? If so, you might not have the wireless connection established or recognized.

You can activate the wireless connection by going to the upper right corner of the panel and click on the network connection symbol. It will give you choices on your wireless connections.

---

### Post by Devo88 on 2012-08-06
yes i installed with the wired connection. ive gone into the network settings and no networks are shown. ive tried manually entering my network details and still nothing. 
ive also installed wifi radar from USC and still nothing.   

its beyond frustrating :(

---

### Post by f1ndingwalden on 2012-08-06
I had a similar problem, go to system settings>additional drivers and activate any recommended items. Also be sure that there is not an actual switch on the outside of your laptop.

---

### Post by Devo88 on 2012-08-06
okay so i tried additional drivers and it showed there wasnt any proprietery drivers in use. i have the network switch on my laptop and it is turned on. 
i really dont understand why it wont work

---

### Post by f1ndingwalden on 2012-08-06
Ok, so whenever you unplug from the ether-net cable, is it showing that wireless is enabled, and if so is it showing any  wireless networks at all? I know this may sound dumb, but if it is showing networks other than yours, you might want to make sure your router is working properly.

---

### Post by Devo88 on 2012-08-06
no its not showing anything. my laptop wireless light is on and it worked fine on windows XP. so i know its not my laptop. it doesnt even show an option for wireless connections

---

### Post by gifford on 2012-08-06
What kind of laptop is it? If you could provide more details it may be easier to track down.

---

### Post by westie457 on 2012-08-06
Hi, could you post the output of all these commands please.
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod
```

Highlight the text in the terminal, right-click and copy. Then in a New Reply here click the # at the top of the pane and paste between the [CODE] [/ CODE] tags.

---

