---
title: "Newly Installed Ubuntu 12.04 64bit on MacBook Pro Brightness will not Change"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by rossjohn07 on 2013-05-19
The brightness on my mac seems to be frozen. I just recently switched to Ubuntu 12.04 on my MacBook Pro Intel Core 2 Duo. Whenever I try to increase or decrease the brightness, nothing changes no matter what level of brightness its on the screen looks the same. 

However if I change it to its brightest setting, then close it, it will open up with that brightness level. Then with the same very bright level if I change it to the lowest then put my mac to sleep, it will suddenly change to that brightness level when my mac is no longer asleep.

It seems like there is always something wrong with after I try to fix something else wrong with my laptop. I guess that is the task of all beginners.

---

### Post by Kevin McCready on 2013-05-19
sudo apt-get install xbacklight
xbacklight =<percentage of max>

---

### Post by Kopkins on 2013-05-19
I was going to suggest xbacklight. You could rebind the keys to do ```
xbacklight +5%
xbacklight -5%
``` 

If the light level resets, to retain brightness you could probably write a script that gets the current backlight setting and writes it to a file, then reads the file after wakeup to resume the same level of brightness.

---

### Post by rossjohn07 on 2013-05-21
After entering in the command

[COLOR=#000000]```
sudo apt-get install xbacklight
```
 
Nothing has seemed to change

[/COLOR]

---

### Post by rossjohn07 on 2013-05-21
It seems like if the laptop is not running off the ac outlet and I shut my laptop to go to sleep, the laptop will then open up in a dimmer mode. But if I plug it in to the outlet, then put my laptop to sleep, it will wake up with the brightness that I set it to.

I still can't change the brightness of my laptop with the keys. Whenever I close my laptop, and its about to go to sleep, the apple symbol on the back will pulse twice then remain off. Weird, but I just noticed that ever since I installed Ubuntu on this system. I'll keep doing research, thank you.

---

### Post by rossjohn07 on 2013-05-23
With a little research I actually managed to find a solution to my brightness issue. Through this page [HTML]https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Sound[/HTML] Using a series of commands: ```
[COLOR=#333333][FONT=UbuntuMono]sudo gedit /etc/modules[/FONT][/COLOR]
```, then adding ```
[COLOR=#333333][FONT=UbuntuMono]mbp-nvidia-bl[/FONT][/COLOR]
``` to the end of the page. Then following the remaining commands and rebooting my computer, and it worked :)

And of course, once I fixed one problem, then another popped up, and my sound didn't work. So I looked at the same page to update my sound, and sure enough my sound works now too!

Hooray for the internet and Linux! Hopefully I will get to more advanced topics soon.

---

