---
title: "Nvidia GTX660"
date: 2014-08-23
forum: New to Ubuntu
---

### Post by Urbanmasque on 2014-08-23
I was able to install and boot to GUI, started getting the issue in the image below - updated everything and still getting this issue. Its isolated to Firefox, because every folder and menu I open appears this way a few minutes after putting my password into the login.
Any help would be greatly appreciated!

Graphics card: [COLOR=#929091][FONT=Arial]Graphic Card | [/FONT][/COLOR][COLOR=#929091][FONT=Arial]NVIDIA SERIES | [/FONT][/COLOR][COLOR=#54A0C2][FONT=Arial]GTX660-DC2O-2GD5[/FONT][/COLOR]

[IMG]http://i.imgur.com/lTxHajfl.png[/IMG]

---

### Post by sotiris2 on 2014-08-24
Which driver are you using? Did you download from Nvidia's site? If not you can find which driver you are using from "Software and Updates", "Additional Drivers" tab.

---

### Post by bizhat on 2014-08-24
Driver issue. I had exactly same problem with my AMD card. Solved it by changing driver. It is better remove old drivers if you have more than one driver installed, my problem was conflict between the drivers, so switch between fglrx and opensource did not help, but uninstalled fglrx completely helped.

---

### Post by kc1di on 2014-08-24
Hi Urbanmasque  and Welcome to Ubuntu,

It's better to use the Propitiatory driver than the open source one for your card. 
You can see if the additional driver tool will offer you another driver first.
do the following:

go to software center > on edit >software sources > device drivers.
when it comes up wait, it may take awhile for it to search your system and offer driver choices 
for your card you want 304. driver. 

you can also install this driver from the terminal with this command:
```
sudo apt-get update && sudo apt-get install nvidia-304
```

Good luck :)

---

### Post by Rob Sayer on 2014-08-24
> **bizhat said:**
> Driver issue. I had exactly same problem with my AMD card. Solved it by changing driver. It is better remove old drivers if you have more than one driver installed, my problem was conflict between the drivers, so switch between fglrx and opensource did not help, but uninstalled fglrx completely helped.

AMD has its own set of issues in linux that are different from Nvidia.  Setting up nvidia cards seems more complex but their support is better than AMD's.

It is likely the driver though.  I don't have a lot of experience with nvidia but the 1st answer here looks good, though it's for 13.10 (I didn't see anywhere what ubuntu release is used):

[http://askubuntu.com/questions/399530/how-do-i-install-geforce-gtx-660-in-13-10](http://askubuntu.com/questions/399530/how-do-i-install-geforce-gtx-660-in-13-10)

I saw a couple of things in blogs on nvidia drivers but they recommended installing drivers from external ppa's, which are not tested by ubuntu.  I generally won't touch that sort of thing with a 10 foot pole.  Even if it does work at first it'll break at some point generally when you update.

I highly recommend finding out what your peripherals are ... the make and model isn't that useful ... and searching here and askubuntu, which has ranked answers.  Once you begin to figure out what to ask it's a very fast way to find out things.

---

### Post by oldfred on 2014-08-24
It looks like the 304.xx driver was the first to support it, but all the newer ones will also.
Best to install the newest the repository installs, unless you have a very new video card that is only supported by the very newest driver. Then you may have to use ppa which at least is pre-complied, where direct download from nVidia also requires separate updates with every kernel update.

[http://www.nvidia.com/object/linux-display-amd64-304.51-driver](http://www.nvidia.com/object/linux-display-amd64-304.51-driver)

If you search on your model it shows all the newer drivers as options.
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by Urbanmasque on 2014-08-24
Hey guys,

Thanks for the tips! 
Inside the drivers tab it is saying that I am using the recommended driver.  I've also noticed that when I use Chromium the issue doesn't pop up - it only happens when I browse the web in Firefox for an extended period of time.
[IMG]http://i.imgur.com/N7jKRxkl.png[/IMG]

Thanks for the tip kc1di, I'll install that driver if you think it'll help and report back.

---

### Post by impliedconsent2 on 2014-08-24
Maybe I'm missing something, but why are y'all pushing 3.04 (circa 2012) drivers?  Is it because it's 'certified'?  I'm not following here at all when the latest [proprietary is 340.32]("http://www.nvidia.com/object/unix.html"). It's not like the GTX660 is in the legacy realm just yet. (Don't beat me up, I just am asking because I do not understand)

---

### Post by kc1di on 2014-08-25
Your welcome Urbanmasque, 
and impliedconsent2 That's the major reason, also it just works with most cards. and machines. though I believe the latest in the official repository is 331.

---

### Post by Urbanmasque on 2014-09-04
Update:  Used the nvidia-304 driver and havent hade any issues with the graphics and web browsing since I posted about it.

Thanks guys.

---

