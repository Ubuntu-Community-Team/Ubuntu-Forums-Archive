---
title: "Sound problems with virtualbox"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-04
I'm having problems with sound in hardy heron when i run virtuabox i can here videos and youtube from inside the xp guest but when i try and play something in ubuntu there is no sound until i restart the pc or logoff and on again:confused:

---

### Post by kamitsukai on 2008-05-05
<bump>

---

### Post by shad0w_walker on 2008-05-05
Why are you playing youtube videos in a virtual machine? Just play them straight from firefox. As for the actual issue, it sounds like your system isn't working properly with ALS or ESD. There should be a setting in Virtual box to choose what type of Audio output you use. Make sure it's not set to OSS. 

If that doesn't work, try looking in the sound properties on Ubuntu. System > Preferences > Sound. In the window that pops up, goto the 'sounds' tab and make sure that 'Enable software sound mixing (ESD)' is ticked.

---

### Post by kamitsukai on 2008-05-05
No i think you miss interpreted what i was trying to say, what i meant was i can here sounds within virtualbox but when virtualbox is running i am unable to here sounds coming from ubuntu

---

### Post by kamitsukai on 2008-05-05
Also i did what you reccomended about checking if virtualbox sound was set to oss and it was so i have changed it to pulse audio (is that correct?) and hopefully this will solve my problems :)

---

### Post by shad0w_walker on 2008-05-06
That sounds like the right setting (I'm not using the latest Ubuntu release but it should be the right option) and hopefully it will work. The reason I said to switch virtualboxes sound method is that OSS ties up the sound card and stops other things from using it unless you're careful.

Good luck, hope it works out.

---

### Post by Oldsoldier2003 on 2008-05-06
> **kamitsukai said:**
> Also i did what you reccomended about checking if virtualbox sound was set to oss and it was so i have changed it to pulse audio (is that correct?) and hopefully this will solve my problems :)

changing to pulse in Vbox is what worked for me. I can hear sound from within and outside the VM.

---

