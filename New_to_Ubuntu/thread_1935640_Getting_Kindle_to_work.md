---
title: "Getting Kindle to work"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by s1wood on 2012-03-04
I've installed Kindle via Wine and have a nice icon on my desktop, I have made it executable but nothing happens when I try to open it. This is the same on both my 10.10 and my 11.04 computers.
Any suggestions?

Susan

---

### Post by winh8r on 2012-03-04
I never needed to install anything to use my Kindle (I am running 10.04).

Whenever I plug it in it is recognised and I can just drag and drop books into it from the Calibre library or from downloads if they are from Amazon.

Was yours not showing up on the desktop?

---

### Post by anewguy on 2012-03-04
This will never work in Wine - you need to use Callibre native in Linux.  The reason is that you can't use USB devices in Wine, so of course the app will never find the Kindle.

Go native using Callibre - works like a champ!

Dave ;)

---

### Post by cortman on 2012-03-04
> **winh8r said:**
> I never needed to install anything to use my Kindle

Same here. I use 11.10, and just copy/pasting from the file browser is plenty adequate for me. If I want to read an ebook on my computer I use Calibre.

---

### Post by anewguy on 2012-03-04
Again, everyone please read my post.  They were asking about why this wasn't working in Wine.  The explanation was given and is simple:  wine doesn't support USB device.  The solution was also given - use Callibre native in Linux.

---

### Post by s1wood on 2012-03-05
I have Calibre installed and working but what I want to be able to do is download books from Amazon onto my computer (and then transfer them to my e-reader). 
Amazon require me to register my computer via the Kindle download which is why I want to be able to open Kindle.
No USB device involved at his point.
If there is a way to use Calibre to access Amazon books could someone explain it from the beginning please.

Susan

---

### Post by forrestcupp on 2012-03-05
Right guys. She doesn't want to hook up her Kindle device. She wants to be able to read her Kindle books with the PC Kindle app.

Honestly, I think you'd be much better off using [the Kindle Cloud Reader](https://read.amazon.com/about). It runs perfectly from within Firefox or Chrome, and it's just as good as the Kindle app.

---

### Post by s1wood on 2012-03-05
Right, the cloud reader sounds good. I'll try it out. 
Thanks very much

Susan

---

### Post by cortman on 2012-03-05
> **anewguy said:**
> Again, everyone please read my post.  They were asking about why this wasn't working in Wine.  The explanation was given and is simple:  wine doesn't support USB device.  The solution was also given - use Callibre native in Linux.

Sorry, all- just read the second post or so and got distracted. Hope the cloud reader fills your need!

---

### Post by s1wood on 2012-03-05
The Cloud reader takes me to Amazon.com but when I want to buy something I get referred back to Amazon.uk which wants me to install the Kindle app! 
I realise this isn't a Ubuntu question any more - unless someone can tell me how to activate that Kindle app, but what am I doing wrong apart from living in the United Kingdom?

Susan

---

### Post by winh8r on 2012-03-05
I seem have to completely misunderstood the post, I had assumed there was a kindle device involved. I wasn't aware of the cloud reading service.

POST EDITED DUE TO MISUNDERSTANDING ON MY PART>

---

### Post by forrestcupp on 2012-03-05
Again, she doesn't have a Kindle device that she wants to hook up. She wants to install the Kindle reader app using Wine so she can buy books and read them in Linux. Evidently, in the UK, the web site won't let you buy books for the cloud reader. That really stinks.

Anyway, about running the Kindle app with Wine. According to the WineHQ app database, the latest Kindle for PC app gets a platinum rating, which means it works without any problems. Based on your signature, I suspect you are using an old version of Ubuntu, and therefore also using an old version of Wine. You need to use a PPA to update to the latest Wine, and that should get it to work for you. 

Unless you have other Wine apps installed that are important, I would completely uninstall Wine and delete the .wine directory before proceeding. Just remember that you'll lose any apps you installed with Wine by doing that, so if you have apps you need, don't do it. But it will make things cleaner if you can do that. Then go over to [WineHQ](http://www.winehq.org/download/ubuntu) to learn how to add the Ubuntu PPA for Wine. Then you'll need to go to a terminal and type
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine
```After that, you'll have the latest version of Wine that supposedly runs the Kindle for PC app perfectly. Make sure you have downloaded the latest version of Kindle, and try installing it again with Wine. I'll bet it will work for you.

Edit: I guess it's not the latest version that gets a Platinum rating. But doing this might work for you anyway. It looks like most people have gotten it to work. [Here's the web page](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10597) on the WineHQ app database for the Kindle reader for PC. If it doesn't work perfectly, maybe you can get some hints for workarounds there.

---

### Post by s1wood on 2012-03-05
On the netbook (11.04) I only installed Wine a few days ago from the software centre - won't that be the most up-to-date version?

I've been on that Wine HQ page and it just directs me to the same Kindle download site.

I've had a reply from Amazon: guess what.....
*>Unfortunately, Kindle Cloud Reader is available only from Amazon.com  and it is not currently available for UK customers. Even if you  download it from Amazon.com and register it to Amazon.co.uk, you will  not be able to use it.<*

You'd think they might say that somewhere on the site wouldn't you?

regards,

Susan

---

### Post by forrestcupp on 2012-03-05
I'm not sure if they have the latest beta version on 11.04. But it doesn't matter anyway. I tried myself to install it, and I've been beating my brains out over this. I've tried with the stable Wine 1.2, and the very latest beta version from the PPA. I've tried installing the latest version of the Kindle app, and I've even tried installing the older version that supposedly got a Platinum rating.

Even after a lot of dll tweaks from the terminal output and changing it to Windows 98 compatibility, like was suggested, no matter what I do, I can't get it to work. I'm sorry I can't be of more help.

---

### Post by Dr Watts On on 2012-03-05
Hi, all, I might be blowin in the wind here, but just wondering if there is any possibility of registering through a non-UK friend's proxy setup? If the people of the Internet do not soon stand up and create some new internet that can't be blocked, WE ARE DONE! But I suppose, if I want to sell something I should have the right to select who gets to purchase or use it. But anyway, any application? Just trying to jog what seems to be unsolvable by thinking (or, questioning) outside the box. Would registering the app through a proxy server help? 
(And what re: legalities. I don't really care at my age about becoming "a criminal" as long as I know that's what I'm doing).

---

### Post by JayKay3OOO on 2012-03-05
> **forrestcupp said:**
> Right guys. She doesn't want to hook up her Kindle device. She wants to be able to read her Kindle books with the PC Kindle app.

Honestly, I think you'd be much better off using [the Kindle Cloud Reader](https://read.amazon.com/about). It runs perfectly from within Firefox or Chrome, and it's just as good as the Kindle app.

Thanks.

I did not know this existed. Shame the kindle for PC app is dead in Linux though I saw from googling that for a time it worked in the past.

Cloud reader works great under Chromium.



> **Dr Watts On said:**
> Hi, all, I might be blowin in the wind here, but just wondering if there is any possibility of registering through a non-UK friend's proxy setup? If the people of the Internet do not soon stand up and create some new internet that can't be blocked, WE ARE DONE! But I suppose, if I want to sell something I should have the right to select who gets to purchase or use it. But anyway, any application? Just trying to jog what seems to be unsolvable by thinking (or, questioning) outside the box. Would registering the app through a proxy server help? 
(And what re: legalities. I don't really care at my age about becoming "a criminal" as long as I know that's what I'm doing).

This is a different topic. Perhaps you should make your own post rather than hijacking this one.

---

### Post by s1wood on 2012-03-05
On further examination, USC had installed Wine 1.0 so I tried 1.2. with no further success. I have now upgraded to wine 1.3 nd re-installed Kindle.
It still won't open - there is now a brief appearance of the rotating circle which suggests something is happening but to no effect.
According to the Kindle download page, when set-up finishes  a screen  should open to allow me to register my device. This does not happen
Am I missing something very basic here (I often am)? Should I be doing something with that other icon on the desktop marked kindle.lnk? I have tried making that executable and opening with Wine but nothing happens. 

Regards,

Susan

---

### Post by s1wood on 2012-03-06
Ah,
I see Forestcupp actually answered that one in a post that hadn't been opened. Glad to know it's not just me. 
Shall have to try my son's windows computer.

Thanks anyway.

Susan

---

### Post by anewguy on 2012-03-06
And......I don't think the Kindle APP will start in Wine because it wants a Kindle DEVICE - hence my comments on not using it in Wine and going with native Callibre.  I *thought*, back when I had my Kindle Fire (which I got rid of in a month - hated it - got a different tablet/reader) that I got books directly from Amazon without the Kindle app.  I also had a reader app for them - wish I could remember exactly what I did.  That's why I said what I did.  So, I wasn't blindly posting, and would appreciate not being interpretted incorrectly.

---

### Post by anewguy on 2012-03-06
As far as Kindle in Wine, I've already answered that, and I wish people would quit assuming I'm talking about the PHYSICAL Kindle.  The Kindle APPLICATION *WON'T* run in Wine.  Period.  The application LOOKS for the Kindle device (what do you think it's doing when it is going to register your device?), the Kindle device is USB, USB isn't supported in Wine.  Again, this is for the Kindle APPLICATION.

I'm sorry to be so rude, but some people completely missed what I was saying and assumed I meant the hardware.  Think about what the app is doing - you'll fine they are inseparable - the App wants the Kindle, the Kindle needs USB, Wine doesn't support USB (at least it never has except for things like keyboards, mice, printers, as they are devices Wine has to have to run).  At least, the Kindle app I tried to install, just for reading, still wanted the device.  Maybe that has changed.

Basing this on my experience with the old Kindle which I had for a couple of years with Ubuntu, and the Kindle Fire with Ubuntu.

If they have a separate reader-only app that really doesn't look for the device - well, I'd still bet it does.

If I'm wrong, so be it.  Just don't make this assumption about talking about a DEVICE when someone is talking about an APPLICATION.

> **s1wood said:**
> On further examination, USC had installed Wine 1.0 so I tried 1.2. with no further success. I have now upgraded to wine 1.3 nd re-installed Kindle.
It still won't open - there is now a brief appearance of the rotating circle which suggests something is happening but to no effect.
According to the Kindle download page, when set-up finishes  a screen  should open to allow me to register my device. This does not happen
Am I missing something very basic here (I often am)? Should I be doing something with that other icon on the desktop marked kindle.lnk? I have tried making that executable and opening with Wine but nothing happens. 

Regards,

Susan

---

