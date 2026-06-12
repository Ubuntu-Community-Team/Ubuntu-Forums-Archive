---
title: "Laptop Power Management?"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by d4m1r on 2013-04-16
Hey guys, I've largely restricted using Ubuntu to my desktop as it is my main PC, but now I have installed it on my laptop as well for use when I am not at home. I plan to use my laptop exclusvely in the future so wanna get it all setup. Basically, it will be docked 50% running on full AC power and at full performance, but the other 50% of the time I will be traveling with it so battery life is important to me. I did a stock install of Ubuntu 12.04 LTS (x64) and basically, what tips/tricks/applications do you guys recommend to optimize battery life? Juniper is appearently dead(?) so I shouldn't use it and Ubuntu does have some built in power management options but I don't know effective they are at extending battery life...

Laptop specs = Intel Core i5, 8GB DDR3, 128GB SSD, Intel 4000 HD graphics, etc.

---

### Post by pqwoerituytrueiwoq on 2013-04-16
you can change the cpu governor in /etc/init.d/ondemand

i am running 13.04 so my file is different than yours, if you don't know what you need to edit post the content and i can mark where you can edit it
you want to change "ondemand" to "conservative"
i change the line that says 'sleep 60' to 'sleep 30' so it does its thing faster

i hope you made the appropriate config options for your ssd 
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

you can also set your brightness below the min setting, i can do this on my laptop
```
echo 160 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
i use my /etc/lightdm/lightdm.conf file to restore the brightness setting on boot using xbacklight
```
greeter-setup-script = xbacklight -set 0
```
i have mine setup a bit more fancy so it saves the brightness at logout and then restores it at boot
that does not restore the below 0 value btw

be sure your screensaver is set to blackscreen and turns the screen off

---

### Post by fyfe54 on 2013-04-16
I have Powertop on my Dell.  It's in the repositories.

Also, I have Jupiter.  There is a ppa for it at [https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)

---

