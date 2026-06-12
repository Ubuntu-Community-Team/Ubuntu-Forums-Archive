---
title: "Asus eee pc X101ch"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by Donkey666 on 2013-03-24
Hi people , 

Am vry new to Ubuntu and recently bought a asus x101ch realised how slow the windows on there was and thought there must be a better way. 
Enter UBUNTU :D 
All installed fine on 12.04 lts loving it except one thing 

The display brightness setting is very low and i cant get it to be brighter i have looked for a fix and search but struggling to get the fix on to the netbook :( 

can anyone please help me my eyes are starting to sting.;)

---

### Post by matt_symes on 2013-03-24
Hi

Looks like this may be a bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132261](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132261)

From the terminal, please post the output of 

```
ls /sys/class/backlight
```

and 

```
cat /sys/class/backlight/*/max_brightness /sys/class/backlight/*/brightness
```

Copy and paste the output from the terminal by selecting the text, right click -> Copy and paste into the post.

EDIT:

And welcome to the forums :D

Kind regards

---

### Post by Donkey666 on 2013-03-24
Hi the output brougt back for the first Terminal

acpi_video0  psb-bl

and the secound one was 

10
100
10
0

Hope this is all ok am still pretty new to this so thanks for helping 

and thanks for the welcome and fast reply

---

### Post by gabriolastyle on 2013-03-24
I have the same issue on my acer aspire one for now after i boot up i paste the following in the terminal:  sudo setpci -s 00:02.0 f4.b=ff

Fastest way to the terminal is: Crtl Alt T

---

### Post by Donkey666 on 2013-03-24
Wow just tried that and WOW it wokred man is there a perminant fix to this or can we get this to stick ?


ok just want to post this now after a reboot to check the above fix WORKS 100% will still test though

---

### Post by matt_symes on 2013-03-24
Hi

> **Donkey666 said:**
> Wow just tried that and WOW it wokred man is there a perminant fix to this or can we get this to stick ?


ok just want to post this now after a reboot to check the above fix WORKS 100% will still test though

Wow ! You're lucky that worked :D

I have no device at that location:

```
matthew-S206:/home/matthew/test % lspci -s 00:02.0
matthew-S206:/home/matthew/test % 

```

```
matthew-S206:/home/matthew/test % sudo setpci -s 00:02.0 f4.b=55
setpci: Warning: No devices selected for "f4.b=55".
matthew-S206:/home/matthew/test % 

```

For a more general solution you want to be piping a value into the brightness file in sysfs.

Something along the lines of...

```
echo 100 | sudo tee /sys/class/backlight/psb-bl/brightness
```

The value above is either 100 or 10.

Is it sticking after a reboot ?

Kind regards

---

### Post by gabriolastyle on 2013-03-24
If you want the fix I posted above to stick after a reboot you need to make the scrip run on start up which is listed below.
This does not fix the problem though, you still cant adjust the brightness atleast you can see your screen :/ 


Open a terminal window and type
cd /etc
sudo nano rc.local
above where it says Exit 0 paste:       sudo setpci -s 00:02.0 f4.b=ff
crtl x, and select y to save it.

---

### Post by Donkey666 on 2013-03-24
i have been working on getting ait all up and tunning but have rebooted 4 times so far and it seems to have stuck :P


Maybe this is the fix for this \netbook am not sure or maybe am just lucky but thanks for all the help:)

will keep looking through the forums as will need to find good things to install on the Netbook to give me good proformance and for when i start programing or least learning :) 

Thanks again

---

### Post by Donkey666 on 2013-03-24
well least i can see the screen it has stuck been able to adjust brightness will have to keep investigating

---

