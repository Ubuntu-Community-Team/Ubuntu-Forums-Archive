---
title: "DWL-650+ used to run ok with ndiswrapper, now doesn't. And I haven't done anything."
date: 2013-01-25
forum: New to Ubuntu
---

### Post by johnjonh on 2013-01-25
I have a IBM T23 running Xubuntu 12.10 ... just to get used to Linux.

I have a DWL-650+ PCMCIA wlan card that was running ok after I installed ndiswrapper and used the Windows Network Driver thingy. 

Now I have booted a couple of times but there is no connection. The setup was - honest to god - working perfectly and I have not done any alterations.  

How does one debug a situation like this - i.e. see whats running and whats not ?

Edit: this message is posted from the same dual booting T23 using the wlan card in question = its not failed hardware.

---

### Post by squakie on 2013-01-25
Well, I don't advocate ndiswrapper now, however if you had it working then rebooted and it no longer works, I would try the following:

- open a terminal window and type:

sudo depmod -a <press enter>

sudo echo ndiswrapper >> /etc/modules <press enter>  **SEE NOTE BELOW**

NOTE:  ON THE ECHO COMMAND YOU *MUST* USE 2 GREATER THAN CHARACTERS (>>).  FAILURE TO DO SO MAY CAUSE SOMETHING ON YOUR SYSTEM TO NOT WORK.  IT CAN BE CORRECTED, BUT USE 2 - >> - AND YOU SHOULDN'T HAVE A PROBLEM.

What this is doing is appending ndiswrapper to the /etc/modules file.  This file tells Ubuntu what additional modules to load at boot.  I suspect you just never updated the file.

After finishing the above, reboot and see if your wireless is now working.

---

### Post by johnjonh on 2013-01-25
Thanks for the advice, however no success.

If I run "ndiswrapper -l" i get:

"airplus: driver installed device (104C:8400) present"

If I run "modprobe ndiswrapper" I get

"FATAL: module ndiswrapper not found"

If I add "ndiswrapper" to the end of the etc/modules file, it doesn't change the outcome (yes I rebooted)

So... do I have to copy something somewhere ? I did make install on the ndiswrapper source that created some files but where to put them ?

EDIT: there is no native support for Airplus DWL-650+. And the funny thing is that it was already working. I think Ubuntu updates might have screwed it up.

---

### Post by squakie on 2013-01-25
Also - if you manually followed the steps to install a driver with ndiswrapper, I would suggest the following (assuming of course you need to use ndiswrapper):

sudo ndiswrapper -l

sudo ndiswrapper -r <the name of the device returned on the list>

repeat this until this list is empty.

lsmod ndiswrapper

If ndiswrapper is in the list:

sudo rmmod ndiswrapper

Next, install ndisgtk - a graphical front-end to ndiswrapper.

Run ndisgtk, pointing it to the .inf file for your device.

Remember:  architectures must match (32-bit driver for 32-bit Ubuntu, 64-bit driver for 64-bit Ubuntu), and that rarely does ndiswrapper really work unless you are using the Windows XP .inf and .sys files.

---

### Post by squakie on 2013-01-30
Also, was there a reason you didn't use ndiswrapper either from the repositories or from the installation CD (it and ndisgtk are in subfolders under /pool/main/n on the installation CD)?

---

