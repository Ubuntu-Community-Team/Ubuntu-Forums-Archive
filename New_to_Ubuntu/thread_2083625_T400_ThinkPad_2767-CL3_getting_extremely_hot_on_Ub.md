---
title: "T400 ThinkPad 2767-CL3 getting extremely hot on Ubuntu 12.10"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by brodedra on 2012-11-13
I have recently migrated from Windows XP SP2 Professional 32 Bit to Ubuntu 12.10 32 Bit on my T400 ThinkPad 2767-CL3. It seems after installing Ubuntu, the system is getting over heated for no stupid reason! Is this usual in Ubuntu with ThinkPads? if so, I can cook eggs for free every morning I guess :confused:

---

### Post by NikTh on 2012-11-13
> **brodedra said:**
> I have recently migrated from Windows XP SP2 Professional 32 Bit to Ubuntu 12.10 32 Bit on my T400 ThinkPad 2767-CL3. It seems after installing Ubuntu, the system is getting over heated for no stupid reason! 
Hi,
I guess you not faced the same problem when you had Windows XP installed. I mean , this is not a problem with dust - clean or something similar. (correct?) 
> **brodedra said:**
> Is this usual in Ubuntu with ThinkPads? 
No is not. Sometimes the graphics card is responsible for that.
> **brodedra said:**
> if so, I can cook eggs for free every morning I guess 
What else you want? Ubuntu cares about your breakfast :P 

Open a terminal (CTLR+ALT+T) and copy-paste from here bellow command
```
lspci -nnk | grep -iA2 vga
```post the results back here. **Click on "New Reply" and put the results inside ```
 tags to be easier to read. **[See here how]("http://i.stack.imgur.com/zADbK.png")

Also install psensor and lm-sensors to see the actual temperatures. 

[code]sudo apt-get install psensor lm-sesnors
sudo sensors-detect #Just press [Enter] to answer all questions
```**Tip:** During Psensor's install it  will ask you for hddtemp to start as a daemon. Navigate with [TAB] key and press [Enter] to confirm. Answer Yes. 
Then reboot and after login psensor will open (after 20secs). See the temperatures there.

---

### Post by brodedra on 2012-11-13
I've figured out Ubuntu somehow doesn't like my 256MB ATI Radeon HD3470 and the WiFi daughter card both are not supported by Ubuntu 12.10 - Strange!

NikTh, Thanks for your help though.

Heading back to Windows!

---

