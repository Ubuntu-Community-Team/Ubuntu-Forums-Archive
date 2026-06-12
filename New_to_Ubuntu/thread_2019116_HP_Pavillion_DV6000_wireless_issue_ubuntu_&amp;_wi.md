---
title: "HP Pavillion DV6000 wireless issue ubuntu &amp; windows"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by xoScarlettRose on 2012-07-07
Ive had this issue on both Ubuntu and Windows, it's driving me crazy! The wireless switch on my laptop glows orange in both the on and off position. I don't know why... It worked when I'd restore windows to its factory settings but only temporarily and usually only until it was powered down, then I'd have to restore it all over again just to access the internet. FRUSTRATING! I don't know where to begin in Ubuntu. Install the drivers perhaps? Hoping someone could possibly help and maybe explain what the commands are suppose to do. Thanks in advance! xoScarlett

---

### Post by jonnyboysmithy on 2012-07-07
I would say something is wrong with the hardware. If you're lucky perhaps you can somehow make it so that it loads up the card like it was before you powered off.. I'm stumped..:confused:

---

### Post by hypnot0ad on 2012-07-07
I am still just getting the hang of things with ubuntu, making the switch from Win7. After the switch I am always losing my wireless signal and find myself rebooting the router/modem a whole lot more often than I did with 7.

Not quite sure what this means, maybe some bugs still.

---

### Post by jonnyboysmithy on 2012-07-07
[I found this troubleshooting guide]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html"). 
Do you want to go through it by yourself or together step by step?

Either way you would start by:
(Quoting from the site)
> **Check for device recognition**

                                                                                             
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: sudo lshw -C network
[/LIST]
Could you post the output of the command?

---

### Post by xoScarlettRose on 2012-07-08
The only output is > PCI (sysfs) but that only appears briefly. It dissapears and then> scarlett@scarlett-HP-Pavilion-dv6000-RV009UA-ABA:~$ I'm so stumped!

---

### Post by jonnyboysmithy on 2012-07-08
Same thing with me it also puts out ```
PCI (sysfs)
``` and then I wait a few seconds at it spits out the rest. Tried waiting a say half a minute?

---

### Post by xoScarlettRose on 2012-07-08
I tried again just to be sure, it waits a bit and just starts a new line waiting for input on my end theres absolutely no output. Does this mean the driver software isnt installed?

---

### Post by jonnyboysmithy on 2012-07-08
I don't know. I'm not very knowledge. Anyone else want to jump in here?

---

### Post by xoScarlettRose on 2012-07-08
Thanks for your time anyways! I hope I can get this worked out soon :( what a nightmare

---

### Post by Rexilion on 2012-07-08
Could you perhaps post the output of the following at pastebin.com and give us the link?

> uname -a
nm-tool
lspci -v
dmesg

---

### Post by xoScarlettRose on 2012-07-08
[http://pastebin.com/g0mgt0AB](http://pastebin.com/g0mgt0AB)
 
I had to copy my text output onto my external drive and bring it to a different computer to post the output, hopefully it didn't alter it in any way. Thank you!

---

### Post by xoScarlettRose on 2012-07-12
[http://pastebin.com/Gtes1Pcs](http://pastebin.com/Gtes1Pcs)
 
I reinstalled Ubuntu on my computer and this was the new output. Maybe this is progress??

---

### Post by Rexilion on 2012-08-25
Stumps his head.

You now, my Compaq Presario had these same issue's. It turned out to be a malfunction caused by misdesign. I returned my laptop to HP and got a free mobo which now also identifies itself as a HP Pavilion, which is odd since it was a Compaq Presario V6000 :???: .

My best guess would be that your WIFI is dying. It's not a bad driver issue's since it doesn't even show up in your lspci -v output!

P.S. Altough HP had a good (little slow) repair service, I never would buy their laptops again.

---

