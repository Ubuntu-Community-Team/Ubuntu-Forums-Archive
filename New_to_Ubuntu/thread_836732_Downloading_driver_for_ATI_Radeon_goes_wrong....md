---
title: "Downloading driver for ATI Radeon goes wrong..."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by retskrad on 2008-06-21
Hi.

After I installed Ubuntu, a small window pops up and displays: "**Found ATI Accelerator**" and I click on it, and I choose to enable the driver.

After a few seconds it tells me to restart the computer. I restart the computer. After restart, the screen becomes black and nothing happens. 

I tried restarting again, but this time I get an error: "**Unknown format chart** "**o**" and I must log into Windows and uninstall Ubuntu. 

I have tried serveral times to reinstall. Still the same error... Any ideas?

By the way, I have got an: **ATI Radeon x1650 512MB AGP**. Recently bought.

EDIT: I'm using Ubuntu v8.04

---

### Post by Dbugger on 2008-06-21
Same problem here. It worked fine with Ubuntu 7.10. After upgrade to 8.04, the restricted drivers of my ATI (in my case, ATI RADEON Xpress 200M) didnt work. I always get the black screen.

To get back to the system, I had to enter in recovery mode and chose the "xfix" option to deactivate the restricted drivers. Now I can use ubuntu, but my graphic card is getting bored, and im sad cos I cant play :(

@retskrad: If you want to use badly the graphic hardware, swtich back to Ubuntu 7.10. it works fine (even though I had other kind of problems there :S)

---

### Post by retskrad on 2008-06-21
> **Dbugger said:**
> Same problem here. It worked fine with Ubuntu 7.10. After upgrade to 8.04, the restricted drivers of my ATI (in my case, ATI RADEON Xpress 200M) didnt work. I always get the black screen.

To get back to the system, I had to enter in recovery mode and chose the "xfix" option to deactivate the restricted drivers. Now I can use ubuntu, but my graphic card is getting bored, and im sad cos I cant play :(

@retskrad: If you want to use badly the graphic hardware, swtich back to Ubuntu 7.10. it works fine (even though I had other kind of problems there :S)

IS there a big difference between 7.10 and 8.04?

---

### Post by Dbugger on 2008-06-21
not really.

Bigget issue in my opinion is, it comes with firefox 2, but you can install firefox 3 manually....

other stuff worked fine. I had a bug with 7.10 though: when I jacked in my headset, audio came out by both spearks and headset :D

I'd remain with gutsy, if I wasnt such a last-version wh0re :D

---

### Post by retskrad on 2008-06-21
> **Dbugger said:**
> not really.

Bigget issue in my opinion is, it comes with firefox 2, but you can install firefox 3 manually....

other stuff worked fine. I had a bug with 7.10 though: when I jacked in my headset, audio came out by both spearks and headset :D

I'd remain with gutsy, if I wasnt such a last-version wh0re :D

Lol. I'll try again to install Ubuntu 8.04 and try installing drivers from the ATI website instead.

---

### Post by Dbugger on 2008-06-21
> **retskrad said:**
> Lol. I'll try again to install Ubuntu 8.04 and try installing drivers from the ATI website instead.

If it's same issue I had... it wont work. But still good luck with it.

I tried to solve it for 2 weeks everywhere:web pages, irc... absolutely nothing. and noone who had the same problem fixed it.

Still if you fix it, tell me how you did it ;)

---

### Post by retskrad on 2008-06-21
> **Dbugger said:**
> If it's same issue I had... it wont work. But still good luck with it.

I tried to solve it for 2 weeks everywhere:web pages, irc... absolutely nothing. and noone who had the same problem fixed it.

Still if you fix it, tell me how you did it ;)

Lmao. Now, when installing, suddenly the screen became black and I coudn't even see the desktop.. :/

---

### Post by whitedays81 on 2008-06-21
i have the exact Video Card as you do, but i have yet to solve the problem, this is my 3rd day of trying to figure out what's wrong with it.

the only way i can get any Desktop Effects was when i use this in the terminal. (but first disable the driver in "Hardware Driver" because that would result in a blank screen at startup, witch could be fix by logging in session Failsafe GNOME)

> sudo apt-get install xserver-xgl

when i did it, my computer goes ungodly slow. but the effects where there. i've heard it works for some people. but if you experience slowdown, or if its not working 

And to uninstall it, i just go to the terminal and type.

> sudo apt-get remove xserver-xgl

i wish i can give you a better solution, but i cant find any, if you find a solution and actually manage to get it to work, please notify me. :)

---

### Post by retskrad on 2008-06-22
> **whitedays81 said:**
> i have the exact Video Card as you do, but i have yet to solve the problem, this is my 3rd day of trying to figure out what's wrong with it.

the only way i can get any Desktop Effects was when i use this in the terminal. (but first disable the driver in "Hardware Driver" because that would result in a blank screen at startup, witch could be fix by logging in session Failsafe GNOME)



when i did it, my computer goes ungodly slow. but the effects where there. i've heard it works for some people. but if you experience slowdown, or if its not working 

And to uninstall it, i just go to the terminal and type.



i wish i can give you a better solution, but i cant find any, if you find a solution and actually manage to get it to work, please notify me. :)

Already removed Ubuntu. My new video card that I have got now , seems like it doesn't like Ubuntu. Lol. When I had x1050, it worked. Oh well. Thanks for replying.

---

### Post by hopelessone on 2008-06-22
you can always install a program called "ENVY" to take the hassles out of graphic cards...

Hope helps..

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by retskrad on 2008-06-22
> **hopelessone said:**
> you can always install a program called "ENVY" to take the hassles out of graphic cards...

Hope helps..

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I'm too lazy to do install again. Maybe I'll try some day. Thanks for reply.

---

### Post by megadave on 2008-06-23
Has anyone who's had the black screen problem successfully used envy to properly install the restricted driver?

---

### Post by lavinog on 2008-06-23
envy works to my knowledge, but the driver you can get with envy is not much different than the restricted driver in the repositories.
in fact the latest restricted driver (8-6) caused alot of corruption (likely to be a problem with the 64bit driver)
the repositories have 8-3 or 8-4 both were very good drivers.
The new drivers from amd have been working well with their automated installer though...so really i don't see the point in envy.

It may be beneficial to post your Xorg.log to see what errors are occurring.

When you get a blank screen does your monitor go into standby?...if so the problem may be that the video card doesn't know the limits of your monitor and is trying to use a resolution that your monitor doesn't support...this was a problem I had to face by updating my /etc/X11/xorg.conf file

what type of monitor are you using? lcd, crt, widescreen...etc

Also make sure that the desktop effects are disabled.

---

### Post by retskrad on 2008-06-23
I cant usse any effects, I can't even have on "Normal" , when I change to normal or high, the screen becomes totally white, you can only see the mouse. You have to press ESC to close the effects windows to go back to normal again. I'm using a LCD screen.

---

