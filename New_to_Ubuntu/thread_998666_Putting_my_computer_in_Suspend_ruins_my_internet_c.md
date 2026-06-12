---
title: "Putting my computer in Suspend ruins my internet connection!"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by josh995 on 2008-12-01
Hi.. I've had Ubuntu for a while but I still know nothing about it!

When I put my computer in "suspend" mode (Is that the same as Windows "Sleep" mode?) and then I push my power button to bring it back, it comes back, however I go to a website in Firefox and it says I'm not connected...

So I have to restart. So, basically, there's no point in suspending, I might as well just turn it off and turn it back on when I need it...

Is there a way I can put Ubuntu in suspend mode and have my connection still work without having to restart?

Thanks.

Oh, and like I said, I know nothing about Ubuntu, really. So please, detailed and step by step instructions are GREATLY appreciated.

---

### Post by twiz86 on 2008-12-01
Yea, same for me. I leave my computer for a while, it goes to sleep then when i come back my wireless trys to connect but never finds a connection. a few minute after tryin to connect it asks for the WEP key again and even after putting that in it still doesnt find it so i have to reboot.

Id disable the suspend option but with a laptop and fridge the only thing running in the house the difference is seen on my electric bill. :)

---

### Post by lswest on 2008-12-01
> **twiz86 said:**
> Yea, same for me. I leave my computer for a while, it goes to sleep then when i come back my wireless trys to connect but never finds a connection. a few minute after tryin to connect it asks for the WEP key again and even after putting that in it still doesnt find it so i have to reboot.

Id disable the suspend option but with a laptop and fridge the only thing running in the house the difference is seen on my electric bill. :)

The only way I've gotten it to work again was right-clicking nm-applet and unchecking "enable wireless" and "enable networking" then re-enabling them both.

Doesn't work all the time, but it does do it more often than not.

---

### Post by 3rdalbum on 2008-12-01
Sometimes when you suspend, not all your hardware comes back. This most commonly occurs when the drivers have been reverse-engineered as the programmers don't know what parts of the hardware still need to be running in order for the whole computer to come back up.

You can try finding the module name of your wireless driver, and then using "modprobe" to reload the driver. Usually the name of the driver will be somewhere inside the kernel logs (run the "dmesg | less" command from the terminal to read the current kernel log).

Let's say I was doing this on my computer. My wireless card's driver is called "ath5k". To reload the driver, I would use these commands:

```
sudo modprobe -r ath5k
sudo modprobe ath5k
```

(This removes the driver then reinserts it).

After 10-15 seconds, Network Manager should start to reconnect.

You can put the commands into a script. Create a file on your desktop called "fix_wireless". Open it in Gedit and put in the following:

```
#!/bin/sh
sudo modprobe -r ath5k
sudo modprobe ath5k

```

Save your changes and close. Right-click the file and go to Properties, then the Permissions tab. Click "Allow this file to be executed". Now when you double-click the file it will ask you how you want to run or display the file; click "Run in terminal". Put in your password when prompted, and this will reload your wireless driver.

Don't forget, you need to replace "ath5k" with the actual name of your wireless module. And submit a bug report to Ubuntu, so hopefully they can work out the problem and fix it in time for the next version of Ubuntu.

---

