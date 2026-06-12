---
title: "Live 14.04 DVD/USB only works with nomodeset on AMD APU system"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by newbie4 on 2014-04-28
Live 14.04 DVD/USB only works with nomodeset on AMD APU system, otherwise it will go into blank screen.

     I've also had trouble with installation because of the same problem, but the workaround is the nomodeset.
     The problem with nomodeset is the resolutions available are all distorted on my monitor, and have no option for my monitor's native resolution.  

Am I stuck with the nomodeset workaround, or is there a fix from developers?

---

### Post by su:bhatta on 2014-04-29
I am also using AMD APU A4 and for previous versions i.e. from 12.04 to 13.10 had to use nomodeset to get my installation working.

Easiest thing to do is install the proprietary drivers from the 'Software & Updates'.
You have not specified what Graphics card you are using, but if it is Radeon 6xxx and upwards, then the 'Software & Updates' should list available drivers in the 'Additional Drivers' tab.
Select one and the resolution will be set to native properties. You will have to reboot after new driver installation.

Also, read this for Dynamic Power Management : [http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html](http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html)
Once you have set the DPM, go for a reboot and you will see battery life improve.

---

### Post by newbie4 on 2014-04-29
Thank you bhatta for your reply and tip.  
I didn't get to mention that it works fine when installed.  I just like using Live DVD/USB on my 3 other machines (all Radeon HD) that aren't installed with Ubuntu.  
Sounds like I have to temporarily install/update the drivers on the Live DVD/USB everytime I use the Live DVD/USB?

---

### Post by su:bhatta on 2014-04-29
I don't know of any other way to get the resolution going !
So, yes, if you are using Live then you will have to temporarily get the Fglrx every time.

But, why not create a small 15-20Gb partition and install Ubuntu, if you are using it regularly?

---

### Post by newbie4 on 2014-04-29
Alright, I will just have to do it everytime (I've downloaded the drivers into the ubuntu live usb)  I have 2 other machines with Ubuntu that I use regularly.  
Unfortunately the other 3 all have about 5Gb's left, which is why I use the live dvd/usb about one a week-2 weeks when I'm transferring files to and from or for scanning them for viruses.  Thanks for the suggestion though.

I like your quote "May the Source be with you !" :)

---

### Post by su:bhatta on 2014-04-29
Thanks newbie4 ! Glad you like it!

Sad to hear about your HDD situation. Hopefully you will get something working.
One last thought, you can use minimal ISO of Ubuntu and install a OS in that 5 Gb left :)

---

### Post by fkkroundabout on 2014-05-01
or perhaps persistent USB with graphics drivers ?
you might have to tweak it to redetect new hardware on startup

---

