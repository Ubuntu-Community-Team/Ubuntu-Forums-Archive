---
title: "[SOLVED] RAM discrepancy"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Sisyphus48 on 2008-10-29
I'm using Ubuntu 7.04, Feisty Fawn and when I start the computer it shows the  4 GB of RAM that I have.  However, when I use Applications-System Tools-Sysinfo it only shows that I have 3 GB.  Same thing when I use System-Administration-System Monitor-Resources.  Can anyone tell me why this happens?

Thanks for all the replies.  I had read that a 32 bit system could address up to 4 GB of Ram but I didn't know that the Ubuntu kernel couldn't go up that high.  The reason I'm using Feisty is that when I went up to Hardy I had a number of problems that I couldn't solve (couldn't get Nexius to play for one) so I went back to Feisty.

Desktop:AMD Athlon 64 X2 Dual Core Processor 6000+, Nvidia 7300GT, 4 GB DDR2 RAM, 80 GB Western Digital HD

---

### Post by sudo_chop on 2008-10-29
This is just one noob to another, but are you using the i386 version of Ubuntu?
 
I dont think the 32bit version can address more then 3ish GB of RAM

---

### Post by fooman on 2008-10-29
i believe its a limitation of a 32bit os.  to get ubuntu to see 4 gigs,  i think you need to be running the 64 bit flavor.

there may be other ways...not sure.

---

### Post by igknighted on 2008-10-29
The way the Ubuntu kernel is compiled, that is all it can address.  I believe there is a PAE kernel in the repo's that can address more, but there is a performance penalty for those high-mem kernels for those without more ram (which is most people), so that is why that support isn't built in to the standard kernel.  Until recently many distro's didn't recognize more than 1gb ram in the default kernel for this reason.

EDIT: Any reason you are using 7.04?  That is now so old it is beyond support (with the release of 8.10 later today, anyways).  As of 8.04 (Hardy) the kernel should be able to address 4gb (or at least have one available that does), but I'm not sure Ubuntu included that so far back.

---

