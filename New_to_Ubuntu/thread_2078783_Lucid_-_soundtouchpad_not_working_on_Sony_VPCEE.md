---
title: "Lucid - sound/touchpad not working on Sony VPCEE"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by statelessness on 2012-10-31
Hello.
This is a new config for me and my old Sony Vaio - 10.04 dual boot w/ win 7.
I checked out the bug reports on this problem (#549727) and  tried a few of the solutions offered...to no avail. #195181 does seem to  apply since the touchpad doesn't work at any time. 
Did a : $ sudo  lshw and the touchpad doesn't show up anywhere in the hardware so I am  thinking it is not getting recognized...which makes me think of a driver  issue first.
In addition, my sound (and probably microphone) are not working either, I have:                       
  ***-multimedia **
                 **description: Audio device **
                 **product: RS880 Audio Device [Radeon HD 4200] **
                 **vendor: ATI Technologies Inc **
                 **physical id: 5.1 **
                 **bus info: pci@0000:01:05.1 **
                 **version: 00 **
                 **width: 32 bits **
                 **clock: 33MHz **
                 **capabilities: pm msi bus_master cap_list **
                 **configuration: driver=HDA Intel latency=0 **
                 [B]resources: irq:19 memory:f4210000-f4213fff 
[/B]
...which has known problems



Seems both of these are fairly common, but I have not found where they are resolved.



I  am a real amateur at this so please keep instructions simple...as I  like to say...splain it to me like I was a child. I struggled thru the  dual boot load and got it done except for these problems


Thanks in advance for all replies.



statelessness

---

