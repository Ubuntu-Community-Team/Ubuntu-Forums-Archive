---
title: "Ubuntu with dual screens"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Vegadark on 2008-07-15
Ok, I just installed Ubuntu 8.04.1 on one of my PC's in a dual boot setup with windows xp home. The PC has an ATI 9200 Pro video card and I have two LG 19 inch LCD screens. The setup works great in winxp, it is set up so the second screen is an extension of the desktop. I want to use the same type of setup in Ubuntu, but I am hitting a road block as how to do it. Right now both of my screens show the same thing (cloned.) I have read about an ATI Big desktop or something, but from what it sounds like, is only possible with a newer ATI card (9500 series or later.) 

Am I reading into this correctly, that I would need a newer series video card from ATI to get the dual screens to work (I want to also be able to run all the cool compiz and other cool stuff as well, if that makes any difference at all in this context. I don't want that stuff to suffer on account of having dual screens.) 

Or would I be better off getting an Nvidia card? Is that easier to setup than the ATI stuff? Does it work better with Ubuntu? Don't really know which direction to go here. Any thoughts?

---

### Post by Paddy Landau on 2008-07-15
Be prepared for a bit of work.

I can't comment on your specific hardware, but after I had spent a fruitless month or so on it, someone pointed me to the right place.

Follow the lead from this post:
[http://ubuntuforums.org/showthread.php?p=5296990#post5296990](http://ubuntuforums.org/showthread.php?p=5296990#post5296990)

It should do you fine.

---

### Post by bodhi.zazen on 2008-07-15
You can get your dual monitors to work with both ATI and Nvidia.

I am more familiar with nvidia, see if this helps :

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

[http://geekravings.blogspot.com/2008/03/howto-dual-monitors-in-linux-with-ati.html](http://geekravings.blogspot.com/2008/03/howto-dual-monitors-in-linux-with-ati.html)

---

### Post by Vegadark on 2008-07-15
Would it be wiser of me to just get an nvidia card, do they support this function better than an ati in ubuntu?

---

### Post by bodhi.zazen on 2008-07-15
> **Vegadark said:**
> Would it be wiser of me to just get an nvidia card, do they support this function better than an ati in ubuntu?

Up to you, of course.

They both will work, they both may be some hassle.

If you change cards, do your homework first. You may be looking at envy to install the nvidia drivers or you may have luck with installing nvidia-glx or nvidia-glx-new.

---

### Post by rossjman1 on 2008-07-15
I have ATI, and dual monitors work fine, for the most part. The only real problem is that I have to change from clone screen to big desktop every time I log in.
sudo apt-get install amdcccle to get ATI Catalyst Control Center. Also, I have compiz and emerald running, giving me a VERY nice desktop.

---

### Post by ster1357 on 2008-07-15
hello all!

i cannot get it working with ATI All in wonder 
best i can do is a cloning! 

it's driving me crazy! 

has anyone got it working with this video card! 
see, both monitors hang off of the same card! 

[IMG]http://kasacomputer.com/images/AGP/ATI%20All-in-Wonder%209600.jpg[/IMG]


[IMG]http://img.tomshardware.com/us/2006/04/06/confessions_of_aa_serial_htpc_builder_part_2/9600_dongle.jpg[/IMG]

---

### Post by Vegadark on 2008-07-15
> **rossjman1 said:**
> I have ATI, and dual monitors work fine, for the most part. The only real problem is that I have to change from clone screen to big desktop every time I log in.
sudo apt-get install amdcccle to get ATI Catalyst Control Center. Also, I have compiz and emerald running, giving me a VERY nice desktop.

Which ATI card do you have?

---

### Post by Vegadark on 2008-07-15
> **bodhi.zazen said:**
> Up to you, of course.

They both will work, they both may be some hassle.

If you change cards, do your homework first. You may be looking at envy to install the nvidia drivers or you may have luck with installing nvidia-glx or nvidia-glx-new.

I have had little luck searching around these forums for a specific model number or otherwise. Some people claim that the nvidia cards are better supported, while others claim the ATI ones are. The only specific thing I did find, is that the FGLRX or whatever it is driver for the ATI stuff only works on newer than 9500 series ATI cards. Being that I have a 9200, it appears I am out of luck in that respect. So I am willing to get one of the newer ones to fit that range, but am also open to an Nvidia card if that may be easier as well.

---

### Post by bodhi.zazen on 2008-07-15
> **Vegadark said:**
> I have had little luck searching around these forums for a specific model number or otherwise. Some people claim that the nvidia cards are better supported, while others claim the ATI ones are. The only specific thing I did find, is that the FGLRX or whatever it is driver for the ATI stuff only works on newer than 9500 series ATI cards. Being that I have a 9200, it appears I am out of luck in that respect. So I am willing to get one of the newer ones to fit that range, but am also open to an Nvidia card if that may be easier as well.

It is not nvidia or ati, it is dependent on the card/model you use.

Try these links:

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

### Post by markbuntu on 2008-07-16
The 9200 card should work great with the open source Radeon driver. It is fully supported. As the open source drivers become more complete for more cards, ATI sees no need to support the cards with their proprietary one. They have released all the info on the older cards to the driver writers.

I have a Radeon HD 3650 1GB card and it works great. I have  24 inch and 19 inch monitors on big desktop. Couldn't ask for more for $70.

---

### Post by markbuntu on 2008-07-16
Sorry. dP

---

