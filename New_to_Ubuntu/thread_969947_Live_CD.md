---
title: "Live CD"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by aagavin on 2008-11-03
I have a compaq Presario CQ50-113ca

and when i put in the live CD it doesn't loads, then I click on try ubuntu without any changes, it the loads the kernel but after that it just shows a blank screen???


compaq Presario CQ50-113ca
Vista Home prem
AMD 1.9 GHz

2814mb ram

---

### Post by Bölvaður on 2008-11-03
Black screen?
Could be because of graphical card. Is that a laptop, and what card do you have?

In boot menu, press F4 and pick "Safe Graphic Mode" and then click Try Ubuntu...

---

### Post by aagavin on 2008-11-03
I have a Nvisia graphics card and yes it is a laptop

thanks

---

### Post by aagavin on 2008-11-03
sorry nvidia not Nvisia

---

### Post by aagavin on 2008-11-03
> **Bölvaður said:**
> Black screen?
Could be because of graphical card. Is that a laptop, and what card do you have?

In boot menu, press F4 and pick "Safe Graphic Mode" and then click Try Ubuntu...

did that but it didn't work, it just gave me some command line thing that said buzybox ect..????

---

### Post by mkvnmtr on 2008-11-03
I am afraid I can't be much help because I have only done this on a powerpc Mack but I will give My experience.  When you start up, before it starts to load the the kernal if you press the tab a page will come up. This page will list many options to proceed. Many times it is something with "no splash". Since I don't know you will need to try them one at a time. Type in the exactly what you see. On mine "live linux ofonly=nosplash" worked but yours is probaly some thing else. When you have typed this in you should see it at the bottom of the page. Then press enter. Give it plenty of time to see if it works. If not restart and try another. If your lucky someone that knows mor than me will give you a lead to the right option or another way to bring up the desktop.

---

### Post by bennachie on 2008-11-03
Might be worth hitting F6 when the boot screen comes up, then adding the following commands at the end of the line of parameters that will be presented at the bottom of the screen:

all_generic_ide floppy=off irqpoll

Worked for me

---

### Post by the.phantom on 2008-11-04
gotta ask
it was burned as a ISO?

so when you are looking it in windows it has a  " xxxxx.iso" file type?

and you burned it at a slow speed?

and you put it in the cd tray and THEN booted the computer?
and did you verify the mdm5 checksum?

---

### Post by aagavin on 2008-11-04
It was a CD that was mailed to me by Canonical Ltd

so I don't see why there would be any problems with it 

thanks

---

### Post by Bölvaður on 2008-11-04
it might be worth it for you to look on the forums for how to install nvidia drivers from the repositories from commandline. it should be 1 line of code... unless if you are unlucky

---

### Post by aagavin on 2008-11-04
> Might be worth hitting F6 when the boot screen comes up, then adding the following commands at the end of the line of parameters that will be presented at the bottom of the screen:

all_generic_ide floppy=off irqpoll

Worked for me 

and it worked for me too thanks 

now I have another problem see [here]("http://ubuntuforums.org/showthread.php?t=969804&page=2")

---

