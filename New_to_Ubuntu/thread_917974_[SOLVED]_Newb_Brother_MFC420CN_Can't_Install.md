---
title: "[SOLVED] Newb: Brother MFC420CN Can't Install?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by jschodde on 2008-09-12
I've read other posts regarding this printer but need to know if I can install the downloaded .deb files just by using the GDebi Package Installer? 

I used this method on both of these files in this order:
mfc420cnlpr-1.0.2-1.i386.deb
cupswrapperMFC420CN-1.0.2-3.i386.deb

GDebi says everything was installed but when I go to add a new printer it can't find the drivers and I'm forced to select one. When I scroll through the Brother models, I don't even see the 420CN in the list!

I'm willing to do what's in this post (which I just found):
[http://ubuntuforums.org/showthread.php?t=590793&highlight=mfc420cn]("http://ubuntuforums.org/showthread.php?t=590793&highlight=mfc420cn")

but I'm not sure if I should reverse the GDebi installs first - or if that's even possible.

This is day #2 for me in Ubuntu-Land.

Thanks,
Jeff

---

### Post by jschodde on 2008-09-12
Problem solved! I ran through the instructions on the thread I mentioned. All I had to do was change the Device URI to socket://192.168.10.188:9100 because my printer is networked.

Oh, and I did not remove the .deb packages previously installed. I just plowed through the instructions on the "HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies!" thread.

Cheers!
Jeff

---

### Post by smokeysam on 2011-08-03
My first post: Thanks to everyone for all the help. 
I had this problem and could not install a Brother MFC420CN
that I had plugged into a router for the sole purpose of making it accessible. I do not have internet connected to the router. I just plugged the printer into one of the router ports and turned on the printer and router. The printer showed up as detected but then I had all the documented problems with getting a driver. I followed all the instructions downloaded from Brother both the printer driver and the cups driver, installed everything, all that and still no result. 

I am using Ubuntu 11.? Natty Narwal
What finally worked and was so easy was this. I removed all installed references to  MFC.
I used the software center on my computer, > "get software", searched for "mfc".   The first two entries were "LPR drivers for extra brother printers" and "CUPS Wrapper driver for extra brother printers". I installed both from there. 
Then did my normal printer add and like magic everything worked. 
So easy.

I am an absolute beginner and know nothing of Linux so I appreciate all the help. 

I hope this is helpful to someone else.

---

