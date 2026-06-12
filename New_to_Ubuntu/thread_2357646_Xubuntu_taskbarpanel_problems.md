---
title: "Xubuntu taskbar/panel problems"
date: 2017-04-04
forum: New to Ubuntu
---

### Post by kesetyan on 2017-04-04
Hi,
I am new to the Ubuntu family of operating systems other than previous use of live cds and dvds.  I have just installed Xubuntu 15.04 to a 16gb USB memory stick to use on my Windows 7 SP1 desktop computer. 

Everything went fine once I overcame a few problems of my own making (which thankfully only wasted time rather than cause any real problems).  However, once I was up and running I began to explore and perhaps fiddled too early - I prefer the taskbar/panel at the bottom of the screen so set up a new one which I located at the screen bottom.  I tried to set up a notification area, found I could not so deleted the one on the top panel.  That created odd results because, when I tried to add a notification area to the new panel, what appeared was a note creating application.  Attempting to resurrect the notification area on the top panel produced a similar result.  More experimentation revealed that if the notification area was the first thing I added to a new panel, it would work but I now have a couple of problems I cannot resolve.

I deleted the upper, original panel but have found that the new panel does not show icons for programs I load, not critical for me until I minimize a program but a minor irritation.  The other problem is that I have not yet worked out how to push the notification area and the the clock to the right hand end of the panel.

Other than these issues, I am quite a happy 75 year old - using the usb memory stick installation seems a good way of exploring Xubuntu without the risk of doing any damage to the desktop computer.  My longer term intention is to get a larger capacity hard drive and set up a dual boot arrangement in the desktop computer *(I've done that with Puppy Linux on my old XP desktop and disconnected XP from the internet after Microsoft support finished)*.

Any help or advice relating to my problems would be greatly appreciated - Thanks.

---

### Post by yetimon_64 on 2017-04-04
> **kesetyan said:**
> ... Xubuntu 15.04 ...

If that is _*not*_ a typo and you are really running 15.04 be aware that it is no longer supported. 15.04 has already reached end of life status. You should consider using either 14.04 or 16.04 (long term support versions) which get a 5 year support base whereas intermediate versions like 15.04 are only supported for 18 months.

---

### Post by deadflowr on 2017-04-04
> Intermediate versions like 15.04 are only supported for 18 months.

less
it's now nine months for non-lts releases.

---

### Post by Bucky Ball on 2017-04-04
As above. Wrong way, go back with 15.04. 16.04 LTS will get you through to 2021. Try there and see if you have a better ride. Good luck. :)

---

### Post by Impavidus on 2017-04-04
Wisely spoken by the three above, although not entirely correct: Xubuntu LTS releases only get 3 years of support. So pick Xubuntu 16.04 and you'll get all updates until april 2019.

You can put the icons for your programs on the bar by adding the window button element. If you're not using the english version, it may be translated (and, in fact, I'm translating here). You can select any task bar element in the task bar editor and click the small up and down arrow to move things up and down to change the order of the elements on the bar. To get empty space inbetween two elements to move some to the right (or bottom, if vertical) end of the bar, insert a division line, edit its properties and make it expandable/stretchable.

---

### Post by ajgreeny on 2017-04-04
In fact all the LTS Xubuntu versions are supported for 3 years now, not 5 years, so Xubuntu 14.04 is about to lose full support.  Only Ubuntu and Kubuntu get the full 5 years, I believe.

I have never totally thought about the risks of keeping Xubuntu 14.04 going for longer, as most of the underlying bits and pieces of the OS are still Ubuntu 14.04 and they, I assume, will continue to be supported till 2019; very confusing I agree.

I also do not know how well supported an installation of Ubuntu 14.04 to which you have added the xfce4 desktop would be but I assume that will get full support also till 2019, and that it is the specifically Xubuntu packages only that lose support very soon, not the rest of the OS.

By the way, you need not have deleted the original panel and created a new one as you could have used the **right click ->Panel ->Panel Preferences**, unlocked the top one and dragged it to the bottom by grabbing at the very end with your cursor; dead simple and it would have kept all applets/icons for you, just as it was before.

To make space in the panel you need to add a **separator** from the **right click ->Panel ->Add new items**, go to the properties of the new separator and tick the **expand** box, then move it where you want it.

---

### Post by Bucky Ball on 2017-04-04
> **Impavidus said:**
> Xubuntu LTS releases only get 3 years of support.

You speak the truth and an oversight on my part. ;)

Ludicrous considering I've been using it for years! :)

---

### Post by yetimon_64 on 2017-04-04
> **deadflowr said:**
> less
it's now nine months for non-lts releases.
Ah, that's right, I was still thinking of the older system of releases when posting there, thanks for the correction.

> **ajgreeny said:**
> In fact all the LTS Xubuntu versions are supported for 3 years now,...

What happens to a 14.04 install with both xubuntu-desktop and ubuntu-desktop packages installed ? Will it only partially be kept up to date ?
I'll have to call this install a Schrodinger install ... I'm not sure if it is alive or dead now :-)

---

### Post by ajgreeny on 2017-04-05
> **yetimon_64 said:**
> Ah, that's right, I was still thinking of the older system of releases when posting there, thanks for the correction.



What happens to a 14.04 install with both xubuntu-desktop and ubuntu-desktop packages installed ? Will it only partially be kept up to date ?
I'll have to call this install a Schrodinger install ... I'm not sure if it is alive or dead now :-)
Yes indeed!
I did say it is confusing, and I am certainly confused about that type of chimera installation's support.

---

### Post by kesetyan on 2017-04-05
Hi All,

Thanks for your advice - I'm on a steep but exciting learning curve here.

Hi All again - an update:

It was not exactly a typo but more an eyesight issue when I labelled my live disc after creating it from the downloaded iso file - it is indeed the 16.04 version.  I'll reinstall on a usb stick - the experience will be useful and hopefully I'll get it all right this time.

---

### Post by kesetyan on 2017-04-05
Hi All,

Another update: the new installation to usb memory stick went well and following ajgreeny's advice, I successfully moved the panel from top to bottom.  I reset the clock/date format to suit my needs and added the shutdown and restart buttons.  My only problem so far has been the updater which appeared to freeze at about 85% done.  I closed it and got an error message saying there was a problem.  I restarted Xubuntu, got the error message again, closed the message window, ran the updater once more and found that everything was up to date so the updater had done its work.  Since then I have had no additional problems; I've set up my mail accounts in Thunderbird, set up Firefox for my security/privacy requirements and added just a few addons, managed to add a new program and removed a few unwanted items.

I'm very pleased with what I've got - I like the basic simple, unfussy look of Xubuntu particularly the default desktop wallpaper which is attractive yet without the clutter found on the default desktop wallpapers of some Linux operating systems.  So thanks to you forum members who came to my aid - it is very reassuring that there are people like you so willing to help an old codger like me.  Cheers and regards.

---

### Post by Bucky Ball on 2017-04-05
Glad you're loving it. Been using Xubuntu, or a something close, for a long time and I too love the simplicity, among other things (I prefer to make it even simpler!).

Please mark as solved to help others (see Thread Tools at top right or last link in my signature at bottom of this post). 

Well done getting the USB install together and everything working, BTW. 

Enjoy the ride. ;)

---

