---
title: "which graphic card is much better for linux, NVIDIA or ATI."
date: 2011-11-08
forum: New to Ubuntu
---

### Post by gautam_jat on 2011-11-08
My nvidia graphics card malfunctioned when i used open suse, but nothing happened when i used ubuntu earlier.But i really like to try different types of linux distros, i searched for forums on net and found out that ATI has driver issues and most of users hesitate to try NVIDIA properiotary drivers.
I m still not sure wether a technical fault or nvidia properiotary drivers were responsible for the malfunctioning of my Nvidia graphic card.
Now i am planning to purchase a new pc, totally dedicated to ubuntu, can any one tell that which graphic card is much better for ubuntu??? kindly i just require a basic graphic card, as for gaming i have another pc dedicated to it.

---

### Post by Frogs Hair on 2011-11-08
Both companies make some nice cards , but I'm not sure why you think users hesitate to try Nvidia proprietary drivers .

I have used a Nvidia card and driver on 5 different versions of Ubuntu so far . Ubuntu will be switching to Wayland in the future and Nvidia has stated they will not have driver support for it and the open source drivers are simply not an option for me . 

If I can't use my preferred hardware driver included , I will have to move on to another distribution . (wait and see)   

[http://en.wikipedia.org/wiki/Wayland_(display_server_protocol](http://en.wikipedia.org/wiki/Wayland_(display_server_protocol))

---

### Post by collisionystm on 2011-11-08
not ATI

---

### Post by gamblor01 on 2011-11-08
Definitely nvidia though ATI seems to have been catching up recently.  But if you want stuff to work go with nvidia and use the proprietary drivers.  Ubuntu should recognize your nvidia card and allow you to install the proprietary drivers with ease.  I have never had problems with them and I highly recommend it.

Just be sure that your card is supported.  Go here and then select the latest driver for either 32 or 64 bit (depending on your CPU architecture):

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)


Then click on the "Supported Products" tab and ensure that your card is listed there.  Just about any new card they put out should be there (except for the really cheap ones -- for example the GT520 does not have Linux support).

---

### Post by Phrostie on 2011-11-08
I'm an ATI fan, but they can be a nightmare on linux.

I still have a 5870 in my desktop, but i picked a laptop with a Nvidia for a reason.  I was spending too much time fighting it.

---

### Post by BaftDrush on 2011-11-08
I've got an ATI in my machine and it's running fine - full output upto 1080 through HDMI into 42" LG.

---

### Post by mannequin on 2011-11-08
I would still go Nvidia.  In my last laptop, it was a pain to install and maintain the latest version of ATI drivers until that was taken from me when they stopped supporting my card.  I now have a very good Nvidia card in my new laptop that I couldn't be happier with.  The proprietary drivers seem to give more options and control than I experienced with ATI.  (This is something coming from me as I used to be an ATI fanboy. :) )

-M.

---

### Post by audiomick on 2011-11-08
My vote for nVidia. Been using only nVidia with Ubuntu since about 2007 with no issues.

---

### Post by larrypg on 2011-11-08
for what its worth am using an amd radeon 6770 with no problems at all

---

### Post by NoNameWill on 2011-11-08
I have only used nvidia cards. So I can say anything about ATI. I tried openSUSE also and had problems with the nouveau driver. The open source driver for nvidia cards. The vid card in my laptop is not supported well with that driver. I was going to read up on the documentation but never got motivated.

---

### Post by 1clue on 2011-11-08
I'm currently using nvidia, but over the years I've used both with approximately equal success.

At one point, ATI will be in front, and at another nvidia will win.  Proprietary driver support gets good and then falls off, for both brands, but not in sync with the free drivers.

IMO the people who hesitate to use the proprietary driver are the people who insist that everything on their box is Open Source.  There is no other reason to worry AFAICT, unless the driver is new and buggy.

More important than brand IMO is how bleeding edge new the card is.  If you stick with mainstream hardware that has been out for a bit, you're probably just fine no matter which brand you get.  If you get a $500 card then you can count on problems, or at least features that are not implemented in either driver.  Same thing with sound cards.

---

### Post by boonybouncer on 2011-11-09
^Agree^
I tried a GTX 550 Ti and had issues with Ubuntu 11.10, switched to a GT 440, and it worked great.

---

### Post by elgordodude on 2011-11-09
I'll add another vote for Nvidia, still running an 8800GT with the proprietary drivers. Haven't had any problems and it's much quieter than my friend's Radeons. However, they'll both work or at least should with some tweaking, if you're building a high end machine I'd do it on the factors of the machine more than the OS.

---

### Post by asadmalik on 2011-11-09
ATI ftw..i had some issues with ati on 11.10(gnome3) regarding the proprietary drivers but there's a wiki round the corner on how to purge the ati fglrx drivers and install the open source ones. fropm then on, i have had no issues with the ati.

---

### Post by Perfect Storm on 2011-11-09
Nvidia got my vote.

And if you want to game in Linux (either Native games or through wine etc.), you'll get the best result with a Nvidia card (restricted drivers).

---

### Post by beew on 2011-11-09
Nvidia is great, just watch out for Optimus if you are buying a laptop.

---

### Post by HellesAngel on 2011-11-09
Yes, another vote for NVidia, but a huge hope that their commitment to support for Linux stays the same or improves in the future.  I use an X53SV Asus laptop with Optimus onboard/NVidia GT540M switching capability and this was a nightmare under Ubuntu 11.04 with Bumblebee - the regular security updates almost always broke something but since upgrading to 11.10 in desperation it has all worked like a charm with dual displays, 1080p and full effects turned on.

---

### Post by mastablasta on 2011-11-09
It really depends on the model as it was noted. Some Nvidia models don't work at all (see Optimus issue for example), some work crappy, while a lot work as they should.
 
Same with ATI. some of the models simply won't work well, while others do work as they should. 
 
In either case older model cards (since you won't be gaming) should be ok from both brands, but do a google check on the model first to see if anyone had some major issues with it.

---

### Post by Mark Phelps on 2011-11-09
I would previously have said Nvidia -- since it was impossible to get decent graphics performance without installing the restricted ATI drivers, and my card got "dropped" when AMD discontinued support for it.

But ... with 11.10, the open source ATI drivers are really great!  With 11.04, I couldn't get full res, nor could I get independent desktops on my dual monitor display.  But, with 11.10, all of the worked "out of the box".

So, I would have to say now, that it is a tossup -- and go with others that say it depends on the model of the card you're planning to use.

---

### Post by 1clue on 2011-11-09
+1 on toss-up.

I haven't looked real close on this thread, but you have an approximately equal split of ATI and NVidia I think, and not many trash talking the free drivers vs commercial.  In my opinion that means all 4 drivers are reliable and mostly functional.  So your choice.

Before you buy a specific card, search the forums for that model or family specifically.

I don't know if you're in the USA or not, but this thread reminds me of the thousands of Ford vs Chevy discussions you can have in any diner in America.

---

### Post by AVH on 2011-11-18
Now is a tough time to pick a video card. Historically, Nvidia cards have been less trouble than ATI/AMD. Unfortunately, Unity 3D is broken on some Nvidia cards ( my Geforce 8400GS for one). Meanwhile AMD cards seem to rule the low end of the market. pay your money and name your poison.

---

### Post by Jacobonbuntu on 2011-11-18
....I would say definitely Nvidia! I never had a (fully) good working ATI card on Ubuntu, never had problems with Nvidia. better support too!

---

