---
title: "completely new user needs help tether blackberry 8310 at&amp;t"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by steve joe bob on 2008-07-15
i need to know how to tether my blackberry 8310. my carrier is at&t. it is my only source of internet connection and i'm trying to leave windows behind. i have yet to install ubuntu but i have tried it on a live cd and like what i've seen so far. i've looked around some forums and have seen people that appear to be doing it successfully but how they are doing it i'm not sure. any help would be much appreciated.

---

### Post by phantomjoker on 2008-07-15
Ok so just to clarify the matter what is your question? - and Im no expert on blackberries - what is the 
> carrier?

thanks

---

### Post by steve joe bob on 2008-07-15
Iwould like to be able to tether (use my phone as a wireless modem) with ubuntu linux 8.04. My phone is a blackberry 8310 and my cell service is through AT and T. It is my only form of net connection so being able to do it is very important and the one thing keeping me from using linux

---

### Post by steve joe bob on 2008-07-15
Maybe to get started someone could advise what software I would need to get ahold of to get started. Or maybe ubuntu comes with something I could use?

---

### Post by MrKlean on 2008-07-15
From what I remember, the BB is a pda which means it needs the tethering plan which is 60 bucks a month. I have an N75 Nokia and use the 20 unlimited paln. I use Gnome PPP, I can give you the dialing number I use, which is *99***1# , password is pass, username is user...they can be whatever you want because ATT no longer uses special username and passwords.  Hope this helps !

---

### Post by steve joe bob on 2008-07-16
Ok cool i'll give it a shot. i do have the tethering plan and everything cuz i currently use it on windows. i'll post back to let you know how it worked out or if i have any problems/questions.

---

### Post by steve joe bob on 2008-07-16
ok so i'm going to probably ask my first crazy newb questions (but like i said i'm a completely new user) i downloaded Gnome PPP (using windows of course. i can't get on the net using ubuntu till i get this figured out) and got the file transfered to where i could use it when i booted ubuntu (i have multiple drives in my comp and i can access that drive with booth os' fairly easy it seems). any ways i unzipped the download but i have no idea how to install the program?? i was reading a file that was unzipped with everything called installation and it said something about cding to the directory and then configuring..... anyways i have no idea what they are talkin about. hopefully someone has the patients to explain this to me. thnx in advance

---

### Post by ad_267 on 2008-07-16
Download it from here [http://packages.ubuntu.com/hardy/gnome-ppp](http://packages.ubuntu.com/hardy/gnome-ppp)

It is a .deb file so you can install it by double clicking. Check the list of dependencies to make sure you have all of that too, otherwise you won't be able to install it.

---

### Post by foots2015 on 2008-07-16
Open up the Terminal in Ubuntu an type

```
sudo apt-get install ppp

```

type in password should install.

---

### Post by ftabor on 2008-07-16
> **steve joe bob said:**
> i need to know how to tether my blackberry 8310. my carrier is at&t. it is my only source of internet connection and i'm trying to leave windows behind. i have yet to install ubuntu but i have tried it on a live cd and like what i've seen so far. i've looked around some forums and have seen people that appear to be doing it successfully but how they are doing it i'm not sure. any help would be much appreciated.

I would suggest you start here: [http://www.blackberryforums.com/linux-users-corner/92085-how-tether-use-modem-your-bb-linux.html](http://www.blackberryforums.com/linux-users-corner/92085-how-tether-use-modem-your-bb-linux.html).  It's not an easy process.

---

### Post by steve joe bob on 2008-07-16
ok so i got gnome ppp installed finally! thnx for everybodys help (especially the link that made it way easy). my problem now is that it doesn't detect my modem (i used the phone # that was provided and the user name and pass). so i changed a setting and would detect again but regardless to what i changed it would detect the modem (i'm pretty sure i tried every option/combination). ubuntu doesn't detect my blackberry 8310 when i plug it in but it does detect the flash memory on it. so that's where i'm at with it currently. i'm gonna try the link ftabor provided and do some research. any help again is greatly appreciated. and if i happen to figure it out i'll do my best to post back and share the steps i took to making it work.

---

### Post by Borg3533 on 2008-08-19
i have an nokia N75 also and i put the user for the user name and pass for the pass word and the number you dial and nothing happens it says unable to connect to modem. does my phone have to be pc suite mode, or do i need some special drivers

---

### Post by fyrmedic on 2008-10-03
I have recently acquired a Blackberry Pearl and my provider is Verizon. I have been searching all over and tried a lot of different tutorials without much success. 

Yesterday, I tried one that I had seen several times but had not attempted yet and it worked. The url is: [http://forum.eeeuser.com/viewtopic.php?id=18053](http://forum.eeeuser.com/viewtopic.php?id=18053)

These are set for Verizon but should get you going. I am using a bluetooth dongle from Trendnet (TBW-105ub). I think it was like $12 usd at Newegg.com.

Good Luck

---

