---
title: "Fan problem and Device Manager?"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Felixret on 2012-02-20
Hi, I have got an actual hardware problem-with my fan. It won't stop working after Ubuntu (11.10) has logged off... I had the same problem when I was running Windows XP on my computer, so the problem is not the software.
Here's a thing: a friend of mine who knows about computers told me to try and do the following: 

"Go into the windows control panel and the device manager to the tab for IEEE-1394 Bus Host Controllers and click the tab to expand it then right click for properties and under power managment click "Allow the computer to turn off this device...." and all is back the way it should be!"

...but the directions are clearly for a Windows interface!
The question is, does anyone know how I can enable/disable a device through something like a device manager? And what exactly is the "IEEE-1394 Bus Host Controllers"? All the programs I have found so far (Udev, Disk Utility, and others...) simply show INFO on the devices but do not allow any changes.
Alternatively, could someone give me a hint on what I can do in the first place through Ubuntu?
Thank you in advance...

---

### Post by 2F4U on 2012-02-20
What exactly do you mean by > Ubuntu (11.10) has logged off? Do you mean the fan remains running when you shutdown Ubuntu? If yes, then the problem is that Ubuntu does not shutdown, since on all computers I know, if you shutdown, all components are turned off.

---

### Post by Mark Phelps on 2012-02-20
You didn't say if you were using a laptop, but presuming you ARE (otherwise, my comments don't apoply), then given the known kernel bug that causes some laptops to run really HOT with Ubuntu, it's to be expected that AFTER you shut it down, the fan might still run for a short while to cool down the process.

This is especially true if the laptop is running very HOT.

If you have a desktop PC, though, it's not likely to be overheating, so I would suspect some other problem.

---

### Post by Felixret on 2012-02-20
@2F4U,
I mean when I shut down Ubuntu, yes, but the problem was EXACTLY the same when I used Windows, too. System off, Screen not displaying, fan working!

@Mark Phelps,
Nope! Not a laptop... It's a desktop...

---

