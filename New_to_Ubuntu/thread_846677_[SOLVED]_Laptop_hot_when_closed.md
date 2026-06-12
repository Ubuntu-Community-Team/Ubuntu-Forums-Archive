---
title: "[SOLVED] Laptop hot when closed"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Sydius on 2008-07-01
My ThinkPad X60s gets very hot when I leave it closed and put it into my bag.  With Windows, when I close it, it more or less goes to sleep and doesn't generate any heat, but it seems that in Ubuntu, it just keeps generating heat.

Any way to fix this so that when it hibernates/suspends (whatever happens when you close it) it generates less heat?

---

### Post by speeddemon8803 on 2008-07-01
Is there any reason you NEED it to be hibernating/suspended?  if your using Ubuntu Hardy you may go to your system menu, go to the preferences submenu, and click on the sessions button..then after that window pops up you can go to the Session Options tab and click the "Automatically remember currently running applications" tick box...and click the close button. I believe this also does the duty your requesting...it saves your session to your hard drive and therefore you will not have to hibernate/suspend.

---

### Post by |{urse on 2008-07-01
There are settings for cpu fan control in your bios (intel calls it Qfan) check in your bios and look for an "always on" setting. This will keep your laptop nice and cool (and possibly noisy)

---

### Post by Sydius on 2008-07-01
> **speeddemon8803 said:**
> Is there any reason you NEED it to be hibernating/suspended?  if your using Ubuntu Hardy you may go to your system menu, go to the preferences submenu, and click on the sessions button..then after that window pops up you can go to the Session Options tab and click the "Automatically remember currently running applications" tick box...and click the close button. I believe this also does the duty your requesting...it saves your session to your hard drive and therefore you will not have to hibernate/suspend.

I'm not so much concerned with currently running applications as I am with being able to skip the long boot time.

---

### Post by Sydius on 2008-07-01
> **|{urse said:**
> There are settings for cpu fan control in your bios (intel calls it Qfan) check in your bios and look for an "always on" setting. This will keep your laptop nice and cool (and possibly noisy)

I'm sure that would help, but I often need to keep the computer in a closed bag, so the fan would be blocked and far less effective.

---

### Post by |{urse on 2008-07-01
then create compartmentalized ductwork and an air conditioner in the bag :lolflag:. Or turn it off. Maybe a mesh laptop bag would sell pretty well, huh. Good Idea ^^

---

### Post by sdennie on 2008-07-01
I think by default, Ubuntu just turns off your screen when you close the lid so, you aren't actually suspending or hibernating.  Go to System->Preferences->Power Management and on both the On AC Power and On Battery Power, set the the lid shut behavior to suspend.

---

### Post by Sydius on 2008-07-01
> **vor said:**
> I think by default, Ubuntu just turns off your screen when you close the lid so, you aren't actually suspending or hibernating.  Go to System->Preferences->Power Management and on both the On AC Power and On Battery Power, set the the lid shut behavior to suspend.

Oh, I didn't know that.  Thanks.

---

### Post by eival on 2010-01-19
i have this issue with my HP Pavilion Enternainment laptop, but i dont see where theres any solution to the issue, even tho its been tagged as such.

i currently use my laptop as a desktop replacement, i also use it as my media server to stream movies thru my WD LIVE player, and i also use it as an audio receiver for my tv because its max volume is relatively low and Ubuntu's "Mic In" allows me to boost it quite higher, anyways, needless to say i have to leave my laptop on 24/7 except for manditory system updates that require restarts, and the black screensaver is too bright to use it as an option at night while im sleeping so i just close my lid, and i have the power management settings set to turn off the screen and i see it go black when its about 75% closed, and obviously putting it in hibernation mode wouldn't allow me to use the laptop for the above mentioned purposes so that option is out..


as for my heat issue, for some reason the CPU section of my laptop (right under the touchpad) gets very hot to the touch, hotter than when its running idle(no apps/processes) BUT if i check the nvidia control panel the internal temp is normal(around 60-70) where as i know for the CPU to feel as hot as it does i would have to be running processes and the temp gets to around 90+ so i dont know what is causing it.

---

