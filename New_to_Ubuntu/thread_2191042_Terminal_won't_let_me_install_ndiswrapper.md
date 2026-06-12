---
title: "Terminal won't let me install ndiswrapper"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by ellordicus on 2013-11-30
Im a beginner and need help. I was trying to get a driver for the wireless card in my computer,but it wouldn't let me  install it I used the basic install code thing: "sudo apt- get Install ndiswrapper-1.59" and it came with this error message:
E: unable to locate package ndiswrapper-1.59
E: couldn't find any package by Regex ndiswrapper-1.59 

I got the instructions on installing it on this site "http://askubuntu.com/questions/285338/ubuntu-wont-detect-my-wireless-card "and followed pretty closely except the unzipping part (I couldn't unzip it through terminal because it was a .tar file so I just extracted it, I figured it was the same thing) 

P.s I'm sorry I didn't use those nice boxes to show the code thingy it would be nice to know how to use that feature....

---

### Post by ellordicus on 2013-11-30
Im a beginner and need help. I was trying to get a driver for the wireless card in my computer,but it wouldn't let me install it I used the basic install code thing: "sudo apt- get Install ndiswrapper-1.59" and it came with this error message:
E: unable to locate package ndiswrapper-1.59
E: couldn't find any package by Regex ndiswrapper-1.59 


I got the instructions on installing it on this site "http://askubuntu.com/questions/285338/ubuntu-wont-detect-my-wireless-card "and followed pretty closely except the unzipping part (I couldn't unzip it through terminal because it was a .tar file so I just extracted it, I figured it was the same thing) 


P.s I'm sorry I didn't use those nice boxes to show the code thingy it would be nice to know how to use that feature....

---

### Post by DuckHook on 2013-11-30
You would be infinitely better off installing the native Linux driver rather than trying to force-fit the square Windows driver into the round Linux hole&#8212;which is what ndiswrapper does. It's always been a kludge, always will be, and not a very attractive one at that.

Your linked web page already contains a link within it that takes you to the page with the Linux driver and instructions on how to install it.

---

### Post by bantuvez on 2013-11-30
Those instructions in the link are totally wrong.

If you want ndiswrapper do this:

```
sudo apt-get install ndisgtk
```

Then run ndisgtk from your dash, it is a graphical frontend for ndiswrapper. You will need the .inf file from the windows wifi-driver and give it to ndisgtk. If then ndisgtk complains that ndiswrapper module is not found, then do

```
sudo apt-get install ndiswrapper-dkms
sudo modprobe ndiswrapper
```

But you should only use ndiswrapper if your wifi card doesn't have proper linux drivers.

---

### Post by ellordicus on 2013-11-30
The instructions are very hard to understand, i am not sure what to do....

---

### Post by mörgæs on 2013-11-30
Please stop multiposting. 
Threads merged.

---

### Post by bantuvez on 2013-11-30
From your terminal run:

```

sudo apt-get install ndisgtk ndiswrapper-dkms
sudo modprobe ndiswrapper

```

Then from the dash launch the ndisgtk application, just like you launch any other graphical application (press windows button, write ndisgtk, click on the app icon). Write in your password when it asks for. In the application click on "Install new driver" and select the .inf file from your windows wifi-driver. (Get your windows wifi-driver from the CD which came with your laptop or download it from the webpage of your laptop manufacturer).

---

### Post by ellordicus on 2013-11-30
Oh.... I meant the Linux driver that Duckhook was talking about....I looked at the instructions he was talking about and they didn't make any sense....

---

### Post by bantuvez on 2013-12-01
Oh... In the end the readme says that Ubuntu comes with the driver prepackaged. And has some very simple instructions.

> Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

Sometimes the driver does not show up in the Hardware Drivers choices.  In
this case, try reintalling the driver from the GUI or shell like this:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

In either GUI or text case, after reinstalling, reboot your machine.

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.


---

### Post by ellordicus on 2013-12-01
Ok, thanks...


I really don't know what I did but I put in a wireless linksys USB card thing and looked up drivers for it...but before doing anything I unplugged the Ethernet( to put the computer back in my room) and was about to move it back whe I noticed that the signal strength was still there. To verify that was I went to the internet and it worked! I even put it back in my room and it still worked! I guessed my problem is solved... For now

---

