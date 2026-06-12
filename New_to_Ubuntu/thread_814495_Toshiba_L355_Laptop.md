---
title: "Toshiba L355 Laptop"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by pawnrocket on 2008-05-31
Howdy everyone. 

Let me start by saying I have actually Googled this stuff and have had no luck. 

I have a Toshiba L355 Laptop that cam pre-installed with Vista. The first thing I did was remove it during the Hardy installation. After which Hardy wouldn't boot. I was curious so I installed Gutsy, erasing Hardy and that booted and everything worked (Webcam/Wireless) except the headphone jack. But that I will worry about later. 

After getting Gutsy installed I updated and ran the Dist. Upgrade to Hardy and Again I couldn't boot into the 2.6.24 Kernel. I could however boot into the old 2.6.22 Kernel that came with Gutsy.

So now I have the Gutsy Kernel with everything thing else from Hardy (I guess)   

Two Questions : 

Obviously :1.) Why will the 2.6.22 Kernel work and not the 2.6.24? 
           2.) What kind of problems can I expect to have running the old Kernel? 


Thanks for being around. 
Pawnrocket

---

### Post by MDSmith2 on 2008-05-31
Does it give you a error message like "Grub Error **" or something like that or any onther error or does it just boot blank?

---

### Post by pawnrocket on 2008-05-31
I guess you could say it boots blank.. I get no errors .. I will remove the bootsplash real fast, and change my menu.lst (I took it out so it wouldn't default into 2.6.24) so I can see where it freezes... If it gives any info..

---

### Post by pawnrocket on 2008-05-31
opps I no longer have 2.6.24 I must have gone brain dead and deleted it. 

Sorry 

I will apt the new kernel and get back to you...

oh I never gave a grub error - it started loading, and then froze

---

### Post by pawnrocket on 2008-05-31
I reinstalled 2.6.24-17-generic and the bootsplash started. It loaded about two bars on the progress bar and stops. I waited about 5 mins and nothing. 

Is there a way to turn off the bootsplash while it is loaded so that I can get only the text screen on boot up?

---

### Post by pawnrocket on 2008-05-31
bump

---

### Post by spiderbatdad on 2008-05-31
from the grub menu, at start up, select the kernel you wish to boot...2.6.24-17, then press e, move to the line beginning with the word kernel; press e again. Go to the end of the line and delete --quiet splash. Hit enter and press b to boot. That should give you the verbose boot.

The factory install may have specified some boot parameters in place of --quiet splash, like acpi=off in order to boot. You may have to add some parameter like that.

---

### Post by pawnrocket on 2008-05-31
After hitting e on the option with Kernel, I scrolled to the end and found

ro quite splash 

I removed "quite splash" pressed enter, then b - and it still loaded the bootsplash
I then removed "ro quite splash" pressed enter, then b - and it still loaded the bootsplash


UPDATE - I removed "ro quite splash" and tried --verbose --acpi=off and it loaded in verbose mode. 

Then it froze while Attaching scsi

---

### Post by spiderbatdad on 2008-05-31
maybe try with:

lapic pci=routeirq

no need fro the dashes, and leave ro. so:

ro lapic pci=routeirq

---

