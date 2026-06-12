---
title: "ubuntu 14.04 alsa ca0106 Writing to ADC failed!"
date: 2015-11-22
forum: New to Ubuntu
---

### Post by Jan_Steuer on 2015-11-22
Hello,
I have ubuntu 14.04 and these soundcards:

 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xbf00 irq 21
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbffc000 irq 19
(The last one seems to be sth on my graphic card).

I have a problem with my Audigy SE. It worked till I tried to make my microphone working and messed up sth with alsa (I think it overwritten my config files when I reinstalled it).
Now I see this in my syslog : "Writing to ADC failed!"

I googled it and it seems that it is quite an old bug in sound blaster driver which should by fixed by now. People were solving the problem around 2010 and nobody complained since that time.
Does anybody know where could be the problem?

Thanks!

---

