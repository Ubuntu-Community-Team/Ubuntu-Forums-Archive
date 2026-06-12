---
title: "Need printer driver"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Damuson on 2012-04-01
Ok. So let me start by saying that I'm new to Ubuntu and Linux in general. I've been experiencing many issues trying to get my laptop to print. Originally, I started with a Kodak AiO and discovered that it was completely unsupported, so I invested in a Brother MFC-J435w only to find that the drivers on Brother's website seem to be made for i386 and not AMD64. I'm running Ubuntu 10.04 AMD64 on my laptop and can't figure out how to get it to print. Can anyone help me here? My fiance is losing patience with the switch. Thanks for any input.

---

### Post by Kevin McCready on 2012-04-01
I would shut your system down, plug in the printer and turn it on, reboot the system. See if the system finds the printer. If that doesn't work perhaps you could post any error messages for us to look at.

---

### Post by Baldrick_NZ on 2012-04-01
Have you tried the i386 drivers from the Brother website? 

Sometimes you can get away with using 32-bit drivers on a 64-bit machine, but not the other way around, which maybe why Brother hasn't released a 64-bit version yet.

---

### Post by Starcruiser322 on 2012-04-01
Sorry to state the seemingly obvious, but did you try System Settings>Printing>Add?
I have a networked printer, and after clicking add and waiting a few seconds it was automatically detected. I just selected it and installed automatically.

---

### Post by HermanAB on 2012-04-02
Howdy,

As far as I know, Ubuntu also uses the RedHat printer wizard.  So you could simply open a console and type:
$ sudo system-config-printer

---

### Post by wojox on 2012-04-02
Install the 32 bit libs on there and it will work:
```
sudo apt-get update; sudo apt-get install ia32-libs
```

---

### Post by Damuson on 2012-04-02
Ok, so I tried the command Herman mentioned, but received the error message "command not found". Additionally, I've attempted to install the 32-bit driver, but it comes back with the error message "error: wrong architecture '1386'". As a side note, I was successful in getting my fiance's netbook, running Ubuntu 10.04 i386, to print wirelessly with minimal troubleshooting. So this proves that the printer is set up properly and is fully compatible with Linux. The only issue seems to be that my laptop is running the 64-bit version, which seems at present unsupported by brother. As for hardwiring it to the printer and running a search, I feel it's unnecessary since the laptop does already recognize it as a network printer, but can't find a working driver for it.

---

### Post by Damuson on 2012-04-02
32 bit libs installed already. Still no joy.

---

### Post by wojox on 2012-04-02
How did you go about installing the drivers? I run a Bothers printer on Ubuntu 64.

---

### Post by Damuson on 2012-04-02
I went to the Brother page with the drivers for my printer ( [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J435W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J435W) ) and clicked on the deb link for both cups and driver, tried to run the package installer and received the error message "error: wrong architecture 'i386'".

---

### Post by kurt18947 on 2012-04-02
We have an MFC-J430W working on Ubuntu 11.10.  It's perfect, at least the printing is.  We haven't needed to set up the scanner so far.  The drivers are indeed 32 bit but the directions for installing found here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Look through the "before installation" link though most entries don't apply to recent Ubuntu distros.  64 bit installs must be done via the command line because they require '--force-all' to get around the 32 bit drivers on 64 bit O.S. issue. 
 
```
sudo dpkg  -i  --force-all  (lpr-drivername)

```first then the same command for the CUPS driver.
11.10 and earlier require ia-32libs to be installed.  Precise doesn't have ia-32libs in the repository so I installed  lib32stdc++.  Also take a look at the FAQs on the above web page.  There are additional steps required to get the scanner to work in 11.10 & 12.04.

Added thought:  I said above printing is perfect.  On 11.10 it is, 12.04 has an issue.  It prints fine but FireFox takes about 45 seconds after clicking "print" to start printing.  There is little or no delay printing simple text or pictures from Libre Office.  11.10 starts within a few seconds for all print jobs.  Brother will most likely come out with a fix once 12.04 is released.

---

### Post by wojox on 2012-04-02
> **kurt18947 said:**
> Precise doesn't have ia-32libs in the repository so I installed  lib32stdc++.

12.04 will be using [multiarch]("http://wiki.debian.org/Multiarch/Implementation")

@OP this should help [Set-up Brother MC-J435W]("http://jacobblock.com/2011/10/out-with-the-old-in-with-the-new/")

---

### Post by kurt18947 on 2012-04-02
> **wojox said:**
> 12.04 will be using [multiarch]("http://wiki.debian.org/Multiarch/Implementation")

@OP this should help [Set-up Brother MC-J435W]("http://jacobblock.com/2011/10/out-with-the-old-in-with-the-new/")

Right.  Except for the delay starting to print in 12.04 it seems like a good machine for the $.  Now to get some empty refillable ink cartridges and **good** quality ink.  One reason I favor Brother is that they don't have any electronics in their ink cartridges.  And their OEM cartridges are not badly priced, especially the 'large economy size' :p.  HP printers & scanners are usually no-brainers to install in Ubuntu but the ink can be a little $.

---

### Post by Damuson on 2012-04-03
> **wojox said:**
> @OP this should help [Set-up Brother MC-J435W]("http://jacobblock.com/2011/10/out-with-the-old-in-with-the-new/")

I actually stumbled on this page earlier in my attempts to find the solution to my dilemma. However, due to my lack of knowledge in linux, did not understand how to execute the bash script that came up when I clicked on the link provided. Perhaps this is my missing link. How do I set this to an executable and run it?

---

### Post by Damuson on 2012-04-03
Also, not sure if this helps, but when I got the printer to work for the netbook, it was by going into Firefox localhost:631 and providing the file manually via the address provided from the package installer. I tried to use the same technique for my laptop, but the opt folder came up empty for some reason.

---

