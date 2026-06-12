---
title: "Poor internet connection via cable"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by Esot-Eric on 2011-09-19
Hey chaps, I just installed Ubuntu on my laptop (a dv6 pavillion) as the sole OS and when I went to the update manager it was all going swimmingly until about halfway when I got a message saying the connection had dropped, I got the update manager backup and it seemed to do the rest of the update but at a rather slow pace. Now when I go on the Internet with it via a ethernet cable it's very slow (20 seconds or so for a google search) but if I connect to our wireless all is well, what might have happened here? The iso and the burn were fine.

---

### Post by Esot-Eric on 2011-09-19
Right oh chaps, I decided to just install Ubuntu once more and this time it went a bit better (though I had to force a shut down after the update manager froze after pressing 'restart now'). So that's all good, I did notice one thing, the burn was fine and yet when I checked it before I installed this second time I got an error regarding 'casper initrd.lz' (the md5sum that is). So I burnt a new one onto my USB and that passed the check, I've now checked it after the install and it now fails, is this normal? One last, very minor, thing, on the bit of the install screen where you choose whether to download updates and mp3, flash etc. now I notice that on my laptop neither box was checked and yet when I installed onto my PC the one regarding mp3/flash etc. was already checked. Most peculiar! Has there been any updates in the last few days by the way? I've not had any through the update manager.

---

### Post by Esot-Eric on 2011-09-19
It does seem a rather specific query, I'll just be bumping this now, I'm somewhat on edge as soon I'll be in a position where it's not as simple to access the Internet should there be a problem with my laptop. Would like to know that everything is running smoothly.

---

### Post by westie457 on 2011-09-19
Have you tried using a different cable or just unplugging completely at each end and refitting? The slow internet connection could be caused by dirty connectors or a broken cable.

---

### Post by Esot-Eric on 2011-09-19
Yes I did try that at the time, the cable itself worked as per usual when I plugged it into my PC so it wasn't that, I noted down what the update manager froze on if that is relevant, it was 'system-config-printer-udev' though I can't see a relation.

---

### Post by westie457 on 2011-09-19
Personally I leave any updates until the install has finished and the system has been restarted, even then the installer seems to lag at various stages. Sometimes I have thought about aborting and just as I am ready to press the power button everything gets back to normal.
Now about where it is hanging for you. If the printer is connected at the time unplug it. Printer configuration takes seconds once the system is installed and the printer reconnected. If your printer is one of those that has poor support in Linux that is probably why it hangs there.

---

### Post by Esot-Eric on 2011-09-19
I really ought to provide more information, very sorry there. I did leave it until Ubuntu had installed and restarted, there is no printer connected either and regarding compatibility fortunately it's a HP printer and I believe HP provide drivers for linux somewhere, very nice of them.

---

### Post by westie457 on 2011-09-19
It is very generous of HP. Most if not all of their printers use the CUPS (Common Unix Printing System) generic drivers as default.
As to what is causing your drop in internet speed I have no real idea. 
Could you open a terminal and post the output of ```
lshw -C network
``` this will hopefully tell us what the name of your chips are.

Thank you.

---

### Post by Esot-Eric on 2011-09-19
Right oh, I assume only the ethernet bit is important, I'll soon try to reinstall once more and see if I encounter any hindrances if we are unable to resolve the matter, the product is "RT8111/8168B PCI Express Gigabit Ethernet Controller". Sorry to keep bombarding with questions, I also notice that my battery life is rather less than what it was when I was on Windows 7 (and it's currently set to be dim when not plugged in), this isn't too much of a concern though. Ta for your patience. Edit: I just tried the cable again and it's all working! This is most unusual, we shall just have to see whether it fails once more.

---

### Post by westie457 on 2011-09-19
Yes the ethernet bit is the important bit however a lot of the other details are quite important as well because while you or I are fast asleep there will be others who know far more than me may be looking at your problem. The more info we can put out the better.
So this time run the command I gave earlier, highlight all the text and in a new reply here paste between ```
 tags by clicking on the # in the menu bar. Also run [CODE]lspci -vnn
```

Thank you.

---

### Post by westie457 on 2011-09-19
Glad its working. That came through while I was typing so missed it.

Hopefully it will stay working.

Any issues in the future always ask with a new thread.

Happy Ubuntuing.

---

