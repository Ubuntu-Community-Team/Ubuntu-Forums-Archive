---
title: "Some minor problems after upgrading to 12.04"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by Ashish Mishra on 2012-05-30
There are some minor problems which i am facing on my Dell mini inspiron after upgrading to 12.04 from 10.04. These are:

1. Booting takes a very long time compared to earlier 10.04.

2. I have set the brightness to zero. But whenever i start the netbook, the brightness is at 25% or 100% and i have to decrease it each time to zero percent.

3. The launcher does not get hidden or faded when i open internet. I tried to use "MY Unity", but that has only two options for launcher- hidden or fixed. If i choose hidden, i cannot see the launcher even when all the applications are closed.  So choosing hidden as an option is a bigger problem.

4. The netbook is getting more heated. The temperature is around 70 C as shown by psensor.  Is there any way to decrease the heating? I saw some video on Youtube where it was suggested to make some changes in the grub. Is it useful? However, when i do try to make those change using gksudo, it asks for my password and after giving password, nothing happens.

---

### Post by roton on 2012-05-30
1. I'm not sure about this one. Boot times for me are similar to 11.10.

2. I had a similar issue and found this helped - [http://blog.shishio.net/saving-brightness-setting-ubuntu-11-10/](http://blog.shishio.net/saving-brightness-setting-ubuntu-11-10/)

3. Go to 'Appearance' and the 'Behaviour' tab. There is no option to make it visible when all windows are closed but if you do autohide with a high sensitivity you should find it ok.

---

### Post by samitharansara on 2012-05-30
Yah.. Agree.. I also moved from 10.04 and booting time is high in 12.04.  But still much lesser than my win7 installation.

---

### Post by daslinkard on 2012-05-30
1. I would check **System > Administration > Log File Viewer > Messages**.  It may show something lagging or stalling before it backgrounds the  process while booting. The log has time date stamp with seconds. Look  for excessive gaps in the seconds,, etc. and repeated items. If your box  has been booted over successive days you may be able to compare  previous logs.

Or you could start by disabling some services at startup like Bluetooth and Remote Desktop and Gnome Login Sound.  Go to **System > Administration > Startup Applications** to de-select the items for running at startup and see if you notice any change in boot up time.

2. Due to hardware compatibility problem, some Ubuntu laptops’ screen  brightness reset to the lowest or highest on every boot. It’s  inconvenient to configure the screen birghtness on every login. Here’s a way to save the screen brightness settings in Ubuntu laptop. 
 
**Just do this at your own risk!**
 

Open a terminal window, and execute this command to edit /etc/rc.local:
 ```
sudo gedit /etc/rc.local
``` Add this before the last line “exit 0&#8243;:


 ```
echo 4 > /sys/class/backlight/acpi_video0/brightness
``` here number 4 is the value of your screen brightness. Use this command to check the maximum:
 ```
cat /sys/class/backlight/acpi_video0/max_brightness
```

3.  You can go to this [site]("http://www.liberiangeek.net/2012/04/automatically-hide-unity-launcher-in-ubuntu-12-04-precise-pangolin/") to answer your question about autohiding the launcher. 

4.  It seems that the overheating issue has been felt by many, have you considered going down to 11.04 or 11.10 since you were coming from 10.04?

---

### Post by Ashish Mishra on 2012-05-31
Ok, thanks for replies. I have been able to autohide launcher.

---

