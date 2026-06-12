---
title: "'Sound ' in control centre will not open"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by ricky4 on 2013-09-07
Sorry cant find anything related to this specific problem..

No Sound cards are shown:  aplay: device_list:252: no soundcards found...
and of course sound is not functioning
Clicking sound in control centre opens and instantly closes - no chance to read text



Mother board: VIA MiniITX
ubuntu lxle 12.04

Thanks

---

### Post by newb85 on 2013-09-07
More details about your card would be helpful.  Please run

```
sudo lshw -C sound
```

and post the output.

---

### Post by ricky4 on 2013-09-08
Hi
PCI (sysfs)

Is reported when 
sudo lshw -C sound is run.

 VIA EPIA EN Mini-ITX is the motherboard (using on-board sound device)
 I will check bios - just in case it is not enabled.

[http://www.viaembedded.com/en/products/boards/399/1/EPIA_EN_%28EOL%29.html](http://www.viaembedded.com/en/products/boards/399/1/EPIA_EN_%28EOL%29.html)

Thanks for your help so far!
 		 			 				

 		
 	
Just checked bios it was disabled :oops: Seems ok now I have sound!!
Thank you so much for your help!

---

