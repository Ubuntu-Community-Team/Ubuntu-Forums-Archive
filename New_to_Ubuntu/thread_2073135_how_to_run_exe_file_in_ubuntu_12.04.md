---
title: "how to run exe file in ubuntu 12.04"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by sunil5 on 2012-10-19
hi,
Iam having airtel 3g dongle but iam not able to install it in ubuntu 12.04, because it contain exe file. so please help me...

---

### Post by 2F4U on 2012-10-19
Linux doesn't run .exe files natively, but you can use Wine.

---

### Post by NikTh on 2012-10-19
Hi,

> **sunil5 said:**
> 
Iam having airtel 3g dongle but iam not able to install it in ubuntu 12.04
What did you try until now and was failed ? 
 > **sunil5 said:**
> because it contain exe file. so please help me...
As @2F4U said , you cannot run .exe files in Ubuntu. 

I don't know if you use [Wine](https://help.ubuntu.com/community/Wine) if resolve your problem with the dongle but you can try. 

Another try (natively try) would be [Sakis3g](http://ubuntuforums.org/showthread.php?t=1580427) program. 

Thanks

---

### Post by Metalpen1984 on 2012-10-19
Hi, sunil5
I am guessing that you're trying to install the USB modem by its .exe setup file. If so, of course that will fail.
I have found a post by Google: [http://computer-kamal.blogspot.de/2011/12/how-to-install-sh-file-in-linux.html](http://computer-kamal.blogspot.de/2011/12/how-to-install-sh-file-in-linux.html)
If yes, maybe you can find an .sh file in the use. Otherwise, you could check the website of the producer (Airtel). 

In my experience of laptop-using-usb-modem, both in 10.04 and 12.04, I don't have to install any of the module to activate the USB modem (hTC Legend). This is quite convenient for me.

---

### Post by danelwillis on 2012-10-19
There should be two ways to do it, you can try an use wine to run the exe file, but that might not work althought you should be able to set it up in network connections.  If you enter in to network manager via the top right of the screen or enter through system settings you should be able to add the dondle throught the diffrent tabs of network manager.
hope this helps :)

---

### Post by buckyaustin on 2012-10-19
Ok since this is clearly a hardware thing your talking about here. Wine is not the way to go. Try using the network settings like danelwillis has recommended. Wine is to only run Software not drivers. So can not be the solution in this case.

Use wine for games,browsers and any other day to day software.
To get a wireless driver from windows to work on Linux use Ndiswrapper.

That's as far as using Windows software on Linux that you can go.

---

### Post by Mark Phelps on 2012-10-19
For future reference, Wine can NOT be used to install Windows drivers.  With the sole exception of NDISWrapper for network drivers, ALL the other drivers must be Liniux drivers, not Windows drivers.

---

### Post by C.S.Cameron on 2012-10-19
When I installed my 3G dongle I found the manufacturer in Network, and it worked fine with the Ubuntu drivers.
You probably don't need to run the .exe file to install the dongle.

---

### Post by audiomick on 2012-10-19
You wont need to install any drivers for a 3G dongle. Forget about the .exe, it wont run in Linux, but you don't need it anyway.

Your dongle is quite likely to be a Huawei model. Quite a lot of them are. You an check on tha by plugging it in and doing
```
lsusb
```

If you are not sure you are seeing it, unplug it, do the lsusb again, plug it in again, doe the command again. See what appears and disappears.

Anyway, the way to get the thing working is to plug it in, and let the computer think a bit. It is likely that a usb storage will appear, but not certain. Right click on your network icon and choose "edit connections" or whatever it is in english that is similar to that. In the network setup thing, go to the "moblie broadband" tab and choose "add". Follow it through. Should work.

---

### Post by buckyaustin on 2012-10-23
Ubuntu has the drivers for these devices already. You just need configure the device in network settings. It's like a 4 step configuration just to get those devices to work. But they do work on Ubuntu. You just have to enter who is the ISP and your type of contract with them. Then (going purely by memory here), you tell Ubuntu what the pin to the dongle is. Save. Restart, connect and your done.

Ok that's more like 6 steps, but still very easy, all done through a GUI as well.

---

### Post by 3rdalbum on 2012-10-23
1. Plug in your device.
2. Go to the bar on the top of your screen.
3. Go through the menus at the right side of the bar until you find the one that deals with internet and networking.
4. In that menu, you will find "Edit Connections...". Go to that.
5. Click on "Mobile Broadband" and then click "Add". Follow the instructions on the screen to set up the device.

You do **NOT** need the .exe file.

---

