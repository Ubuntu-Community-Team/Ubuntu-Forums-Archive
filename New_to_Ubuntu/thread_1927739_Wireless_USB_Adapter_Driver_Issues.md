---
title: "Wireless USB Adapter Driver Issues?"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by SmrtMouth on 2012-02-18
Hi all. I'm new to Ubuntu 11.10. I just got it up and running after a long battle with nVidia drivers. My video and audio is working perfectly as of now. I'm having trouble installing the drivers for my wireless USB Adapter. It's a Belkin N600 DB Wireless USB. I'm trying to use ndiswrapper to install the drivers straight from the disc. I click install driver and have tried the INF files from Windows XP, Windows 7, and Windows Vista with no luck. It said "Hardware Present: Yes" in the program for each driver. The program is fully updated aswell. I've tried each driver one at a time. I restarted the computer after each driver install. I am not given the option to select a wireless network. Please, somebody help! This is really frustrating me.

---

### Post by MasterNetra on 2012-02-18
Did you try "addtional drivers" first to see what it had and if anything attempt to install via that? Also you should clear the other stuff out first.

---

### Post by SmrtMouth on 2012-02-18
> **MasterNetra said:**
> Did you try "addtional drivers" first to see what it had and if anything attempt to install via that? Also you should clear the other stuff out first.

Tried that.

---

### Post by Old_Grey_Wolf on 2012-02-18
If this is not what you are already doing, try installing the "Windows Wireless Drivers" from the Ubuntu Software Center or Synaptic. Then start the program "Windows Wireless Drivers". Click on "Install New Driver" button. Navigate to the .INF file on the CD and install it.

---

### Post by SmrtMouth on 2012-02-18
> **Old_Gray_Wolf said:**
> If this is not what you are already doing, try installing the "Windows Wireless Drivers" from the Ubuntu Software Center or Synaptic. Then start the program "Windows Wireless Drivers". Click on "Install New Driver" button. Navigate to the .INF file on the CD and install it.
Exactly what I am trying to do but it doesn't seem to be working.:(

---

### Post by SmrtMouth on 2012-02-18
I forgot to post the error message I got when trying to install the drivers. It showed a red circle with a white minus sign and said:

"Module could not be loaded. Error was:"

And it does not display an error. That's all it says!

---

### Post by sailor2001 on 2012-02-18
I have 2 usb adapters. One is labeled  as blue tooth. Both actually have the same chip. One will work on one machine and the other won't. It must have something to do with mother boards on different machines. My usb adapters only cost about $22 each. edit: ubuntu finds the driver at start-up. no disk involved.

---

### Post by SmrtMouth on 2012-02-18
> **sailor2001 said:**
> I have 2 usb adapters. One is labeled  as blue tooth. Both actually have the same chip. One will work on one machine and the other won't. It must have something to do with mother boards on different machines. My usb adapters only cost about $22 each. edit: ubuntu finds the driver at start-up. no disk involved.

Ubuntu doesn't recognize this driver. I don't think they support Belkin. Any suggestions?

---

### Post by Old_Grey_Wolf on 2012-02-18
> **SmrtMouth said:**
> Ubuntu doesn't recognize this driver. I don't think they support Belkin. Any suggestions?

I have spent almost a hour looking for a solution to the Belkin N600 driver problem, and I haven't found anything that worked. It is not a problem unique to Ubuntu. I found posts in other Linux distro forums with no solution.

I hate to say this; but, my suggestion would be to buy an adapter that works with Linux :(

Edit:  It is Belkin that has to write drivers that work with Linux. It is not the responsibility of Linux distros to make Belkin's hardware work with Linux.

---

### Post by matbluvenger on 2012-02-18
> **Old_Gray_Wolf said:**
> I have spent almost a hour looking for a solution to the Belkin N600 driver problem, and I haven't found anything that worked. It is not a problem unique to Ubuntu. I found posts in other Linux distro forums with no solution.

I hate to say this; but, my suggestion would be to buy an adapter that works with Linux.

This!

I know it's frustrating but it's minor tweaking to ensure you don't have to use Windows :D

I just got the Netgear WNA1000M G54/N150 USB wireless adapter... it's teeny-tiny. At first it didn't work great (pretty unstable connection) but I got the proper fix on these forums. It's only $25 and you can find it at Wally World, Radio Shack, or Best Buy. 

If you opt for that one I will give you links to the instructions to make it work properly.

---

### Post by SmrtMouth on 2012-02-18
> **matbluvenger said:**
> This!

I know it's frustrating but it's minor tweaking to ensure you don't have to use Windows :D

I just got the Netgear WNA1000M G54/N150 USB wireless adapter... it's teeny-tiny. At first it didn't work great (pretty unstable connection) but I got the proper fix on these forums. It's only $25 and you can find it at Wally World, Radio Shack, or Best Buy. 

If you opt for that one I will give you links to the instructions to make it work properly.

I will pick it up eventually or maybe I will get another Ubuntu compatible adapter. Thanks for the info :)

---

### Post by kurt18947 on 2012-02-18
If you choose to get another WiFi adapter, I got one of these  (Dlink DWA-131) a couple weeks ago.  it's plug'n'play 11.04 and after.  Rtl-8192SU chip set,  TrendNet TEW-649UB is a twin.  Ebay $16.00 & free shipping.  You'd have 3 days to return it, you'd need about 10 minutes to decide. Plug it in, if the blue light doesn't flash send it back.  Ebay item #200673473287.

---

