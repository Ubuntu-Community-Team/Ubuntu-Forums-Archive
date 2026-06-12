---
title: "SAVE ME from going back to VISTA my sound does not work at all"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by ddoong91 on 2008-05-15
driver STDAUD-00963506
Sigmatel High Definition Audio
says driver name is sthda.sys

how can i fix it so i can run sound God I need sound, if not than i need to scrap ubuntu and crawl back to vista

i typed in alsamixer and i got
Card HDA ATI SB
Chip SigmaTel CXD9872RD/K
VIEW [PLAYBACK] CAPTURE ALL
ITEM MASTER [dB gain=0.00, 0.00]

and then in the bottom left it has a thing called <MASTER> in red
with 100<>100 and 00green in the box just below the bar

then theres another column PCM 100<>100

MY computer is a Vaio VGC VA11G and the sound will not work that is my info I do not know what more I can do if there is any other information I need to give please let me know

There was a reply to my previoius post 
 Re: sound help
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Quote:
For example: If cat /proc/asound/card0/codec#* | grep Codec or : aplay -l return "Realtek ALC260" , Look under "ALC260" in the list and add the following line in your /etc/modprobe.d/alsa-base or (if that one does not exist or is empty) /etc/modprobe.conf

but i dont think it worked or i did it right like i didnt get the whole list or whatever im not sure, can u guys if u know exactly wat im supposed to do just tell me what i have to put in terminal thanks that would be great

---

### Post by bsharp on 2008-05-15
First off, threatening to go back to Vista will not help your problem go away faster. Honestly, most people here don't care what operating system you use.

Now to fix your problem, post the results of
```
aplay -l
```

---

### Post by ddoong91 on 2008-05-15
sorry if you took it as a threat lol it was more of a plea if you can wait just like 10 minutes that would be great i have to reintstallthe ubuntu casue i meessed things up last time and i have no clue how to restore it to normal so im reinstalling

---

### Post by Xiong Chiamiov on 2008-05-15
When you get back, there is a comprehensive [sound problems guide here]("http://ubuntuforums.org/showthread.php?t=205449").

---

### Post by bsharp on 2008-05-15
> **ddoong91 said:**
> sorry if you took it as a threat lol

I (and many others) are frustrated with the "help me or I'm going back to Vista" type threads and people who plead with them to stay with ubuntu, etc. There is no obligation for anyone to help...we do it out of the goodness of our hearts (for beans/posts). 

As for the link posted above, it is a great guide and I have used it in the past to get my sound troubles ironed out. ;)

---

### Post by ddoong91 on 2008-05-15
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

is the result when i do aplay -1

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Sony Corporation Unknown device 81f4
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
when i type ~$ lspci -v

---

