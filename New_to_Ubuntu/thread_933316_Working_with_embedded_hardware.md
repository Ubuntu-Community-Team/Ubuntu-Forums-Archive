---
title: "Working with embedded hardware"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Nervouswreck on 2008-09-29
I'm completely new to Ubuntu despite a brief period using it a couple years ago.

I just installed Kubuntu 8.04 using KDE 3 on my pretty-much-base-configured Inspiron 1525 laptop. Now I have the followowing issues I hope someone can help me with.

Amorak audio player reads my CDs, pauses and mutes when i press the right keys, but will not play anything audibly. I know the likely issue is a missing repository, but which one?

That brings us to the next issue. My (embedded) WiFi card is ignored by the system, and when I set up the dialup connection query the modem, I am told that the Modem is always "busy" even though I didn't dial yet.

Hope I gave enough information

---

### Post by Het Irv on 2008-09-29
Do you have a way of hooking up to the internet though an ethernet port?  It only has to be temporary, If you can, install the ubuntu restricted extras package... when you do that it will ask you to enable the Restricted Repo, which should pick up drivers for your WiFi card if you need them.  It might also pick up drivers for the modem, but I am not sure.

---

### Post by Nervouswreck on 2008-09-29
Sounds like a good idea if I can get to an ethrenet port. The only problem is that my WiFi is integrated and that might mean drivers won't be available. Also, do you have any advice for the modem issue since I will be using dialup regularly <groan>

---

### Post by OffAxis on 2008-09-29
Does your system play any sound audibly? Is it just amarok that is silent?

---

### Post by Nervouswreck on 2008-09-29
No audible sound at all, even with headphones. For some reason I don't have alphamixer or pulseaudio either.

---

### Post by Het Irv on 2008-09-29
> **Nervouswreck said:**
> Sounds like a good idea if I can get to an ethrenet port. The only problem is that my WiFi is integrated and that might mean drivers won't be available. Also, do you have any advice for the modem issue since I will be using dialup regularly <groan>

No advice on the modem whatsoever, I havn't even touched a modem in years.  Can you go into the terminal and type```
lspci
``` 
Paste the output here, I want to see what WiFi card you have.

---

### Post by Nervouswreck on 2008-09-29
I have the Intel Wireless WiFi link 4965AGN I'm running windows Vista at the moment to my great disgust :)

---

### Post by wladicus on 2008-09-29
> **Nervouswreck said:**
> I just installed Kubuntu 8.04 using KDE 3 on my pretty-much-base-configured Inspiron 1525 laptop. Now I have the followowing issues I hope someone can help me with.

Amorak audio player reads my CDs, pauses and mutes when i press the right keys, but will not play anything audibly. I know the likely issue is a missing repository, but which one?

I'm not sure if my info will help because I'm new also and installed Kubuntu 8.04 LTS (Hardy Heron) with KDE3 on my MDG VisionBook Laptop.  After I loaded Kubuntu and before I actually even became aware of sound I downloaded several suggested programmes, among them Kmix for the sound control.  Then I noticed that I wasn't getting any sound when I went to YouTube.  It finally came to me to check Kmix, and sure enough all the sound level controls were off, so I pumped them up to full and everything works great now.
Maybe downloading Kmix will be of help, I dont know for sure.:)

---

### Post by Het Irv on 2008-09-29
> **TeeJR said:**
> 
I am glad you posted that link since I need the drivers. I am currently just using ndiswrapper with the windows drivers for the 4965AGN. They seem to work pretty decent as long as all I do is browse the web. I only have trouble when I try to play video or download stuff. Doing either of those two things seems to kill the wireless driver and then I just have to use modprobe to remove/reload the ndiswrapper. That will bring it back. I hate doing that.

It looks like for basic functions NDISWrapper will work.  And I think there will be improvements in Intrepid to wireless, so it may work out of the box with the new version.  I know that my 3xxxabg Intel wireless does.

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

