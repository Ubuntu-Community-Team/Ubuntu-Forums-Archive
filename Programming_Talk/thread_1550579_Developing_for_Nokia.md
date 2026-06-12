---
title: "Developing for Nokia"
date: 2010-08-11
forum: Programming Talk
---

### Post by flldom001 on 2010-08-11
Hi all.

I need to develop a mobile application for second year computer science project, on the Nokia N96.

However I am a little lost on what I need in order to begin development.

I have downloaded through the Ubuntu Software Center, Qt4.

I need to program the application in C++, and compile it for Symbian OS, and use an emulator for testing before deployment.

I would be exceedingly grateful if anyone could point me in the right direction with respect to mobile development on Ubuntu.

Regards
dominic

---

### Post by WitchCraft on 2010-08-11
Developer Platform S60 3rd Edition, 
Feature Pack 2 
Operating System Symbian OS v9.3 
Screen Resolution 240 x 320

[http://developer.symbian.org/wiki/index.php/Manufacturer_SDKs#S60_3rd_Edition.2C_FP2](http://developer.symbian.org/wiki/index.php/Manufacturer_SDKs#S60_3rd_Edition.2C_FP2)
[http://www.forum.nokia.com/info/sw.nokia.com/id/ec866fab-4b76-49f6-b5a5-af0631419e9c/S60_All_in_One_SDKs.html](http://www.forum.nokia.com/info/sw.nokia.com/id/ec866fab-4b76-49f6-b5a5-af0631419e9c/S60_All_in_One_SDKs.html)


You need the header-files from the Nokia Symbian SDK.

I'm afraid it's a bit complicated:
[http://labs.trolltech.com/blogs/2010/04/21/symbian-development-using-linux/](http://labs.trolltech.com/blogs/2010/04/21/symbian-development-using-linux/)

[http://www.newlc.com/en/Getting-started-with-Symbian,134.html](http://www.newlc.com/en/Getting-started-with-Symbian,134.html)



Are you sure you don't want to develop for Android? Nokia is switching...

---

### Post by flldom001 on 2010-08-12
You are a life-saver, thank you so much :)

---

### Post by WitchCraft on 2010-08-12
> **flldom001 said:**
> You are a life-saver, thank you so much :)

You're welcome. I hope it helped.

---

### Post by CptPicard on 2010-08-12
> **WitchCraft said:**
> 
Are you sure you don't want to develop for android? Nokia is switching...

No it's not switching... they're going for a two-pronged strategy with Meego and Symbian, running Qt GUIs that run on both. IMO it's at least technically an excellent idea, but may be too late in the business sense.

---

### Post by WitchCraft on 2010-08-16
> **CptPicard said:**
> No it's not switching... they're going for a two-pronged strategy with Meego and Symbian, running Qt GUIs that run on both. IMO it's at least technically an excellent idea, but may be too late in the business sense.

It's never a good idea to develop an operating system when you could have somebody else doing most work for you excellently and FOR FREE.

But it makes perfect sense if you want to have a more closed platform. 

But as such, AAPL has already proved that this doesn't work on the long run.
I'd had expected Nokia to be smarter than that. 
Well, we'll probably see Nokia going down all too soon. Petty.

---

