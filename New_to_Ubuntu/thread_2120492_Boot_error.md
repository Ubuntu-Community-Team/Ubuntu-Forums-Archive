---
title: "Boot error"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by cheatos on 2013-02-26
Hi all,

I get a error at boot. I have installed lubuntu 11.04 since when it was released and upgraded to something (really don't have a clue which version it was) but I suppose it should be 12.04 or something now...
However last week and today again I get the
```
BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
```
error message.

Last week I could resolve it by inserting a win7 bootable installation disc. (however not a ubuntu live-cd, always received a 'no live-fs found' or something error)
I didn't need to install win7 i just had to boot from it once and then it worked well again, but just for about a week...

I am really concerned about this because today even the win7 installation disc couldn't help me anymore. I have tried the ubuntu disk in my laptop and it worked very well, as well as the win7 disc, both boot without a problem. I also have configured the desktop bios to boot from cd-rom.

Could it be that my hdd is broken? I have run the lubuntu disk check and it said that my disc has a few bad sectors, however the resume was that my hdd is in good condition...

Tomorrow I will be getting all my data from the old hdd and then I'll have to see what I'm gonna do :/

Thanks for any help on how this error could be caused!

---

### Post by oldfred on 2013-02-26
That looks more like a BIOS error than anything else.

Does BIOS still see hard drive?

From liveCD can you then see drive with Disk Tools and click on drive to see Smart Data?

A few BIOS primarily Intel motherboards need to see a boot flag on a primary partition. Windows has to have a boot flag, but grub does not use one. So those BIOS must think Windows. If you do not have a boot flag add one, it just needs to be a primary partition, grub will never use it.

---

### Post by cheatos on 2013-02-26
First of all, thanks for your reply.

> That looks more like a BIOS error than anything else.
The interesting thing about this error is, that it just occurs as of  now, and my lubuntu worked fine for more than a year already...

> Does BIOS still see hard drive?
Havent checked explicitly but I suppose.
How can i see wether my hdd is detected? Because in the boot options i can only configure to boot from hdd0, not which device name this is. Or will I have to go to the boot device priority dialog? (if there is one in my bios, dont know)

> From liveCD can you then see drive with Disk Tools and click on drive to see Smart Data?
Nope, first of all I can't boot my live cd, only thing thats booting is my win7 cd
second I tried check disk for errors and also the memtest thingy, both result in the (initramfs) commandline with the error 'can't find live fielsystem' or something like that

> A few BIOS primarily Intel motherboards need to see a boot flag on a  primary partition. Windows has to have a boot flag, but grub does not  use one. So those BIOS must think Windows. If you do not have a boot  flag add one, it just needs to be a primary partition, grub will never  use it. 	
I probably have a intel mb but not sure, furthermore it worked like a year and why should it suddenly stop working?

btw, when I had a grub boot-selection menu i also tried booting up older kernels, these didnt work either, same error.

---

### Post by cheatos on 2013-03-03
bump

---

### Post by oldfred on 2013-03-03
When you go into BIOS it should show the hard drive. It usually is the model number. 

This is example from my BIOS.

---

### Post by cheatos on 2013-03-05
ok, ill have a look for my hdd there. thanks!

---

