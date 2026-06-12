---
title: "Intel Pro/Wireless 3945ABG wireless card"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-06-21
after running BT3 and having all these unneeded programs cluttering up the computer, i decided that the best thing to do was scrap installing BT3 and simply install Kismet and the Aircrack-NG suite in ubuntu. I figure it would be easier when the shortcuts are all reflex for me (you should have seen me, apparently what "copy" is in ubuntu is "close every terminal window without warning" in BT3)

i have an IPW3945 chip in my laptop, what driver should i install for the best compatibility with Aircrack-NG and Kismet?

[QUOTE=My Original Post]i have a IPW3945 wireless card in my laptop, i just did a clean install of XP, Hardy, and i'm about to install backtrack 3 on a spare partition.

wireless was really slow on the previous installation of hardy, but i managed over a meg/sec with the XP drivers from intel in XP. i tried to install the XP drivers with ndisgtk/ndiswrapper but it wasn't working right.

before i fiddle with ndiswrapper any more, is this the best option for me? as i understand it, the drivers for windows usually has the most effort put into them (owing to their market share) and the drivers from the manufacturer are usually the most advanced ones (thats why i use the RaLink XP RT2500 driver for my Linksys WMP54G, instead of the Linksys XP driver). am I correct in assuming that the best driver to use is the Intel XP driver?

also, if any of you happen to know, what driver would be best for backtrack if i wanted to PenTest "my" wireless access point?[/QUOTE]

---

### Post by hyper_ch on 2008-06-21
I would disagree that the best driver on LINUX is the WINDOWS XP driver.

---

### Post by Sonic Reducer on 2008-06-22
> **hyper_ch said:**
> I would disagree that the best driver on LINUX is the WINDOWS XP driver.

speedwise it's pretty damn good, but i'm looking for compatibility for the programs i will use to pentest my networks

---

### Post by sdennie on 2008-06-22
I can't imagine a scenario where using the ndiswrapper for intel wireless cards would be beneficial (is that even possible?).  If you are using ipw3945, that is more or less out of date and you should switch to iwl3945.  You can either google for how to switch, search these forums or post back and I will explain it.

---

### Post by Sonic Reducer on 2008-06-22
> **vor said:**
> I can't imagine a scenario where using the ndiswrapper for intel wireless cards would be beneficial (is that even possible?).  If you are using ipw3945, that is more or less out of date and you should switch to iwl3945.  You can either google for how to switch, search these forums or post back and I will explain it.

so i should read up on using/installing IWL3945? thats the best driver to use?

i'll search for it and try to figure it out myself, if i get stuck i'll ask you.

thanks =]

---

### Post by sdennie on 2008-06-22
Regardless of whether or not you are running a Dell, this is a good guide: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues).

There is one more step and that is to edit /etc/udev/rules.d/70-persistent-net.rules and, if there is a rule about ipw3945, comment it out.  Of course, you should check to see if this returns anything:

```

lsmod | grep iwl3945

```

If it does, you are already using the iwl driver.  Which is probably the best linux wifi driver for any card.

---

### Post by Sonic Reducer on 2008-06-22
i just downloaded iwl3945 v2.14.1.5 from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) i'm going to take a stab at it in a few minutes.

just a quick question: when i am running wicd from the stock driver it says it's source is "wext", do i leave it the same when i install IWL?

---

### Post by Paqman on 2008-06-22
I've used Aircrack with no problems at all with the 3945 on my girlfriend's laptop. Speed is also good. The whole reason I put that card in (instead of the default Broadcom rubbish) was so that I could *avoid* using ndiswrapper.

---

### Post by Sonic Reducer on 2008-06-22
apparently IWL3945 is included by default in Hardy, how can i update it to version 2.12.1.5?

i looked around, and the instructions i've found online mention a file with .ko as a suffix, or they talk about bugs while installing it on hardy while hardy is in development.

do you have a link for some directions?

.:EDIT:. i took kismet for a spin with the outdated drivers, and it's been running for 15 minutes and have only found the AP at my house when Wicd can see four or five, and backtrack3 found six in a few seconds. i altered **/etc/kismet/kismet.conf** with this line:

```
channelvelocity=5
```
and
```
source=iwl3945,wlan0,Intel
```

did i edit kismet.conf right? i would think kismet running from a hard disk would work better than BT3, but it isn't

---

