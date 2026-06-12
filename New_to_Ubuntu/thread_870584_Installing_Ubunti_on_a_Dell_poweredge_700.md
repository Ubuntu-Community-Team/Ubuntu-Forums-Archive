---
title: "Installing Ubunti on a Dell poweredge 700"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by ggovak on 2008-07-26
Hi,

I'm tring to load ubuntu  8.04 lts destktop edition on to a Dell Poweredge 700.  When I "install ubuntu" I get a initramfs prompt.  Nothing else, I have a basic command set to work from but I can't get the software to install.  What do I have to do to start the install?

Greg.

---

### Post by talsemgeest on 2008-07-26
You should run the cd check just to make sure that the cd doesn't have any errors. Just a quick google has told me that other people with your computer have got it working, so I doubt it is the hardware.

Hope this helps :)

---

### Post by ggovak on 2008-07-26
The cd is good because I loaded on to a dell optiplex with no problems.  I did a Google also and seen that someone has it working.  I am hoping that can shed some light as to how to get it to load. 

Thanks.

Greg.

---

### Post by bushda on 2008-07-26
If the CD works on another system but doesn't work on that system, running the CD check might still help. It could be the CD drive on the system itself that's a problem. 

Run the test on that system, and then run the test on a different system. If it works in the second system but not the PowerEdge 700, the drive's your problem.

---

### Post by ggovak on 2008-07-27
The CD check does not work on the dell power edge, it freezes up.  I believe it does not like the video hardware.  I put it in graphics safe mode and then it just brings me to the console command line.  It’s not the cd drive because I swapped drive between the power edge and optplex and get the same results.

Greg.

---

### Post by Ryadt on 2008-07-27
Try the installing with the alternate cd. Download it from the ubuntu homepage.

---

### Post by talsemgeest on 2008-07-27
The only other thing I can suggest is play around with the bios settings, namely anything graphics related (but be careful). But first of all try Ryadt's suggestion.

---

### Post by bushda on 2008-07-27
I agree with Ryadt - try the alternate CD. 

When I've had trouble installing, the alternate CD has generally worked for me. If it didn't, the problem was typically hardware related.

---

