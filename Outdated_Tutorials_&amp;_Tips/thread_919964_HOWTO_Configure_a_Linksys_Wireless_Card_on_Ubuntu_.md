---
title: "HOWTO: Configure a Linksys Wireless Card on Ubuntu 8.04.1"
date: 2008-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by xenolalia on 2008-09-14
I had a few difficulties getting my Linksys wireless card up and running.  The following rather simple procedure was what ultimately worked for me:

1.) Using a computer (other than the target computer, as I'm assuming the target computer doesn't have access to the internet yet) go to the following link, and click on the image of your wireless card (you may have to compare model numbers/specs):

[http://www.linksysbycisco.com/US/en/products/Adapters]("http://www.linksys.com/servlet/Satellite?c=L_Product_C1&childpagename=US%2FLayout&cid=1115416939789&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3978991233B01")

2.) Click on the link entitled "Driver" or "Vista Driver" (under the "More Information" header).

3.) Follow the instructions to download the correct driver/version for your wireless card.  Note: You may download either the regular "Driver" or the "Vista Driver," but do not download the "Quick Install" file (if present).  Note: You may have to try both the Driver and Vista Driver options if one or the other does not work.

4.) Extract the contents of the archive to any folder.

5.) If you're using 32-bit Ubuntu, download and unzip the first zip archive I attached to this post. Else if you're using 64-bit Ubuntu, download and unzip the second zip archive. If in doubt, download the first one.

6.) Copy the driver folder and all of the .deb files from the zip archive you downloaded to a flash drive, or email them to yourself, or whatever (somehow, get everything to the target computer's desktop). Note: you must remove the individual .deb packages from the folder I zipped them in and place them "right" on the Desktop (as in not in any sub-folder of the desktop).

7.) ndisgtk is a simple GUI for ndiswrapper (a utility which allows Windows wireless card drivers to run in Linux). At the target computer, open up a Terminal and do the following (enter your password at the prompt):

```
cd Desktop
sudo dpkg -i ndis*.deb
```Once everything is installed, exit out of the Terminal (you can delete all of the .deb files you downloaded), and go to System -> Administration -> Windows Wireless Drivers, and click on "Install New Driver."

8.) Click on the "location" bar, navigate to the folder containing the Wireless driver (steps 4 & 6), and double-click on the .inf file (***not*** autorun.inf).  It might be something like lsbcmnds.inf or netr61.inf. Note: the .inf files might be located inside a sub-folder of the folder you downloaded called "Drivers" or "VISTA86."

9.) Now click install. Once finished, close the Windows Wireless Drivers dialog. Now, when you click on the "double-monitor" icon in the top right-hand corner of your desktop, you should see a list of all available wireless networks. Just click on the one you want and . . . you should be good to go!

I hope that the above will prove . . . remotely . . . helpful.  Let me know if you have any questions or if I messed up at some juncture :).  Thanks!

Good luck & happy internet-ing!

---

### Post by luka983 on 2009-09-05
Thank you so much for this post! The thorough description realy helped!
Luka

---

### Post by xenolalia on 2009-09-06
Thanks!  I'm glad I could help.

---

### Post by RichardSM on 2010-03-23
:p Well it look like it was a good idea but it did not work for me to bad ! I tryed it with a WMP54GS Linksys wireless brd. The .inf driver were named these in thr Driver folder WMP54GSa.inf, WMP54GS.inf. I guess i'll keep trying to find something that will work. Thanks just the same..:KS

---

### Post by xenolalia on 2010-03-24
Try it again with the Vista driver:

[http://downloads.linksysbycisco.com/downloads/WMP54GS-v1.1_v4.102.15.53_Vista_dr.exe](http://downloads.linksysbycisco.com/downloads/WMP54GS-v1.1_v4.102.15.53_Vista_dr.exe)

Use file bcmwl6.inf.

Best,
Xenolalia

---

### Post by RichardSM on 2010-03-24
:p OK I'll give it a try. You know the wireless card I'm using has speedbooster on it. 

Thanks you

---

### Post by xenolalia on 2010-03-24
Awesome.  Let me know how it works out.
 
Xenolalia

---

