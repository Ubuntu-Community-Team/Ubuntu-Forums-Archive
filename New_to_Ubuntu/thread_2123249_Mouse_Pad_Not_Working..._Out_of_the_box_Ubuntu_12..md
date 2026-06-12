---
title: "Mouse Pad Not Working... Out of the box Ubuntu 12.10 Aspire 57367"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by Ibrahim717 on 2013-03-07
So I finally got Ubuntu installed on my laptop after months of trying then giving up..... I am an absolute beginner and half of the post that I read require an hour of research to understand.  This is my first install and use of Ubuntu and I am eager to get it running correctly..I did a full install so there is no going back at this point.... It seems to be working fine. When installing the the mouse pointer worked fine and the internet connection worked. After I boot up and log in the mouse pad doesn't work. I successfully turned on the mouse keys and I am able to slowly navigate through the OS... Due to not being able to get the internet online I am not able to download or cut and past code so I have to enter it in manually.... 
I attempted to write the code into the xorg.config folder but I do not have one. 

12.10 Ubuntu 64bit
Acer Aspire 5736Z 64 amd

I'm looking for step by step instructions on how to correct this issue..... please do not assume that I know how to do anything e.g. boot into recovery mode......and create the conf folder.....

---

### Post by slickymaster on 2013-03-07
Try the following command in a terminal window:
```
synclient TouchpadOff=0
```
That should turn the touchpad on in case it's been disabled.

---

### Post by Ibrahim717 on 2013-03-07
Tried this and it states: " Couldn't find synaptics properties. No synaptic driver loaded?"

---

### Post by Ibrahim717 on 2013-03-07
Thank you for replying so quickly...... Also while I have you on the line I do not have wireless networking abilities on my device there for cannot get internet without a Ethernet cable ..... 



New and determined .....

---

### Post by Ibrahim717 on 2013-03-07
[COLOR=#333333]When I run this command:[/COLOR][COLOR=#333333]cat /proc/bus/input/devices:\[/COLOR][COLOR=#333333]this isN: Name= ""Power Button"[/COLOR]

---

### Post by slickymaster on 2013-03-07
> **Ibrahim717 said:**
> Tried this and it states: " Couldn't find synaptics properties. No synaptic driver loaded?"

Can you please post the output of:
[CODEcat /var/log/Xorg.0.log | grep synap -i[/CODE]

---

### Post by slickymaster on 2013-03-07
> **Ibrahim717 said:**
> Thank you for replying so quickly...... Also while I have you on the line I do not have wireless networking abilities on my device there for cannot get internet without a Ethernet cable ......

Please post the output of the following:
```
lspci | grep -i wireless
```

---

### Post by Ibrahim717 on 2013-03-07
[COLOR=#000000]When I type this into the termanal ...... letter for letter .... 
[CODEcat /var/log/Xorg.0.log | grep synap -i[/CODE]

it states No such file or directory 



[/COLOR]

---

### Post by Ibrahim717 on 2013-03-07
[FONT=Ubuntu Mono, monospace][COLOR=#000000]lspci | grep -i wireless[/COLOR][/FONT][FONT=Ubuntu Mono, monospace][COLOR=#000000][/COLOR][/FONT][FONT=Ubuntu Mono, monospace][COLOR=#000000][/COLOR][/FONT][FONT=Ubuntu Mono, monospace][COLOR=#000000]When I type this into the terminal .... nothing happens...... the $ line re appears [/COLOR][/FONT]

---

### Post by Ibrahim717 on 2013-03-07
I'm sure there is no driver for my touch pad installed and there for it not recognized by the OS......  is there a download or source code I can install to make it work........ I don't mind going up to 13 or down to an earlier version also.... as my main objective is to learn to code thorough modifying the OS....    Open to any solution

---

### Post by slickymaster on 2013-03-08
> **Ibrahim717 said:**
> [COLOR=#000000]When I type this into the termanal ...... letter for letter .... 
[CODEcat /var/log/Xorg.0.log | grep synap -i[/CODE][/COLOR]

Sorry, the command in my post was poorly formatted.
Please post the output of (I advise you to copy/paste it to your terminal window):
[COLOR=#000000]```
cat /var/log/Xorg.0.log | grep synap -i
```[/COLOR]

---

### Post by slickymaster on 2013-03-08
> **Ibrahim717 said:**
> [FONT=Ubuntu Mono][COLOR=#000000]lspci | grep -i wireless[/COLOR][/FONT][FONT=Ubuntu Mono][COLOR=#000000]When I type this into the terminal .... nothing happens...... the $ line re appears [/COLOR][/FONT]

Try to search for the Wireless module:
```
lsmod | grep "wlan_module_name"
```
And kernel boot messages:
```
dmesg | grep "wlan_module_name"
```

---

### Post by Ibrahim717 on 2013-03-08
So I was having so many problems that made it way to difficult for "this beginner" to transition to Ubuntu that I uninstalled 12.10 and installed 13.04 ..... and the mouse pad works...... Thanks for your help.....

---

### Post by Ibrahim717 on 2013-03-09
Also the wireless works by turning on the default driver "broadcom" in 13.04. these issues were deal breakers for me so I had to make the switch...... I believe in 12.10 this was a Kernal issue.... and I still learning how to file bug reports... 

Thanks for the help though...

---

### Post by slickymaster on 2013-03-11
Glad you got it working. Now you can mark this thread as solved.

If you have any doubts on how to do it, just follow this link: [How to mark your thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by PeterL172 on 2013-04-09
Thanks for the advice, just like to say this helped me as well :)

---

