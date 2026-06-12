---
title: "Help with project to send auto email when I leave my garage door open."
date: 2009-08-20
forum: Programming Talk
---

### Post by xl_cheese on 2009-08-20
I have a bad habit of leaving my garage door open when I leave my house.  

Sears makes a device that will alert you inside your home if your garage door is open.  I'm thinking there's someway to connect that to my pc and have it send an auto email to my phone account so I receive a txt message that it's open.

I have no idea where to start.  Perhaps someone here can help me?  My first thought is to wire up that sensor to a USB cable and run it to my PC?  

thanks.

---

### Post by smartbei on 2009-08-21
Generally, it is easier to wire things to your serial or parallel port than to the usb port. Use google.
Once you have done that, you could create a small program that watches for changes when the door opens) and if it doesn't close within, say, 5 minutes, send an email.

The sensor itself could be a button situated properly so as to touch the door when it is closed (microswitches ([like this one]("http://www.jameco.com/webapp/wcs/stores/servlet/ProductDisplay?langId=-1&storeId=10001&catalogId=10001&productId=2076279&")) work great for this).

As for the program, it could be a small python script that uses the serial/parallel module, checks once a second whether the door is open or closed, and if 5 minutes have passed with the door open, sends an email, plays a sound on the computer speakers, etc.

---

### Post by exutable on 2009-08-21
Sorry no help here.....

BUT THIS WOULD BE ****ing awesome.  That would actually be useful and kind of fun to make.

---

### Post by stinger30au on 2009-08-21
i have a better idea that is such much easier


how about before you dissapear from the house you check the garage door

its can be easily done by leaving a little remider note on the dash of your car near the speedo

that way as son as you look at the dash you will see the reminder note and you can get out of the car and check the door

this simple method has helped me for the past 17 years and cost me zero bucks!

---

### Post by djbushido on 2009-08-21
But that's not nearly as much fun.
I'm down for the python scripting, should be much easier to implement a timer than doing a compiled language.

---

### Post by xl_cheese on 2009-08-22
Here's the sensor:

[http://www.sears.com/shc/s/p_10153_12605_00953696000P?vName=Tools&cName=Garage+Door+Openers&sName=Garage+Door+Opener+Accessories](http://www.sears.com/shc/s/p_10153_12605_00953696000P?vName=Tools&cName=Garage+Door+Openers&sName=Garage+Door+Opener+Accessories)

It would be easy to take the signal from this.  I think it just lights up.

So all I need is a serial cable wired to this.  

Thanks for the help guys.

This is going to be a fun project for sure.  The python script should only be kicked off when the door is opened.  Seems like you wouldn't want this thing running constantly in the background.  Once it's kicked off it just sets a timer for a set amount of time.  Perhaps user defined.  Once the time is reached it would send an email to my phone number to send a txt.

---

### Post by Can+~ on 2009-08-22
Or you could make it close itself after a while, you know.

---

### Post by TheStatsMan on 2009-08-22
> **Can+~ said:**
> Or you could make it close itself after a while, you know.

That would be kind of annoying though if you were simply working with the garage open, or get held up by the wife and it decides to close while you are backing out.

---

### Post by Mirge on 2009-08-22
> **TheStatsMan said:**
> That would be kind of annoying though if you were simply working with the garage open, or get held up by the wife and **it decides to close while you are backing out.**

Neighbors may get a good laugh :)

---

