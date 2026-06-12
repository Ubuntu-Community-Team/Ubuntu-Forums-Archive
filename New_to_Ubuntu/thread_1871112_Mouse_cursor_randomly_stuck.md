---
title: "Mouse cursor randomly stuck"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by Alfango on 2011-10-28
Hi

I have a Compaq Presario F700. I've just made a fresh install and my PC has both Windows 7 and Ubuntu 11.10.

Everything works fine, except for my mouse cursor randomly gets stuck. System keeps working, it's just the cursor.

My PC has a little button that locks touchpad. That makes me thing this is a driver issue.

Let me know what additional information you need.

Thanks for your help.

---

### Post by 2F4U on 2011-10-28
Did you verify that the system is not busy with other tasks when the mouse cursor gets stuck?

---

### Post by Alfango on 2011-10-28
Yes. All what system does is running Chrome.

---

### Post by jhuhmann on 2011-11-10
I have a Dell Vostro a860 and I upgraded from 11.04.  I'm getting the same problem.  I also only have had it happen when I am running chrome.

---

### Post by jhuhmann on 2011-11-14
This no longer occurs for me after a recent batch of system updates.

---

### Post by bghansel on 2011-12-31
I am having this problem now with a random freezing of the cursor. I thought it might relate to pop-up windows at first, but I don't think so now. I also use Chrome, but sometimes I believe the problem comes about in Thunderbird email, though I might have Chrome running in the background, and it is my default browser. I have no attached mouse and only the touch pad on the Dell Vostro N series. I can't figure if this is a dell problem, a Ubuntu problem, or a problem with either Chrome or Thunderbird. 

Would love to know what updates jhuhmann installed. Thanks for any info.

---

### Post by pretty_whistle on 2011-12-31
Could just be that the touch pad has dirt on it.

---

### Post by surisitcs on 2012-03-16
I am using DELL N4110... I am also facing same problem.. Some times as soon as the system start ups the mouse cursor will be stuck.. I have to restart the system to over come this problem.. Please suggest something.. :(

---

### Post by Mackinon on 2012-05-08
I have a sony vaio cs24gh 
i have installed ubuntu earlier but recently i got a copy of 10.10 and everything was working fine...
i upgraded it to 11.4 and still no problem..
few days back i got a 11.10 update and since then i got the same Mouse cursor problem.. 
it doesn't get stuck all the time but most of the time i am able to move the cursor but not able to do a left or right click.
problem i think is the touch sensor on the laptop which when i touch sometimes moves the cursor or even causes a click option..
is there any way i can find a driver for this or disable this touch sensor all together?
please help.... ubuntu is a grate OS and only this problem is making me stop using it.

---

### Post by Salvagluque on 2012-05-17
Well for me it happens when i&#7743; ussing the mouse in my lapto. the touch pad works perfectly fine, but what's the point to have a mouse if it gets stuck in every move you make? I&#7743; using ubuntu 12.04 right now in that one. It reacts when I push a button and works again, but I have to do it every time.

Thanks

---

### Post by Salvagluque on 2012-05-18
I kinda sorta solved it for myself. In my case, the problem was that when I controlled the cursor via the mouse and not the touchpad, the cursor got stuck every time I released it. What I did was this. Went to mouse and touchpad (ratón y touchpad) in system configurations and deactivated the deactivate the touchpad when typing and activate mouse pulses with the touchpad. And I always keep the touchpad active.

And now it gets stuck a lot less. I mean, it gets stuck when I leave it for a reasonable amount of time, but not every time I let the mouse still.

By the way, when i push the touchpad deactivation button that my laptop comes with the touchpad does deactivate, but when i push it again, the touchpad panel doesn't work. Any idea why this happens?

thanks

---

### Post by kAzblakh on 2012-06-30
This problem is very likely to be caused by a setting in one of the *laptop-mode-tools* config files. To solve it, you need to disable the USB auto-suspend feature in **/etc/laptop_mode/conf.d/usb-autosuspend.conf**. It's ridiculously easy.

Navigate to the **/etc/laptop_mode/conf.d** folder and open **usb-autosuspend.conf** as administrator for editing. Find this row:
```
CONTROL_USB_AUTOSUSPEND="auto"
```Change **"auto"** to **0** to disable the feature:
```
CONTROL_USB_AUTOSUSPEND=**0**
```Save the document and unplug/replug your laptop to trigger the new setting. Your mouse should behave normally now.

[COLOR=Gray]Alternatively, if you're positive that you need the USB auto-suspend feature to be enabled under certain circumstances, you can leave the setting as **"auto"** or change it to **1** (*always on*), and then add your mouse by USB ID to the blacklist in the same config file or edit the auto-suspension conditional circumstances and timeout at the bottom of the file. Use the **lsusb** command to find out the appropriate USB ID.
[/COLOR]

---

### Post by Salvagluque on 2012-07-01
tried it, but I couldn't find the laptop_mode folder anywhere.

I installed ubuntu trhough the wubi installer for windows.

---

### Post by kAzblakh on 2012-07-01
> **Salvagluque said:**
> tried it, but I couldn't find the laptop_mode folder anywhere.

You probably don't have *laptop-mode-tools* installed. I'll provide a tested solution for this case as well. It seems lengthy but really is easy to accomplish.

**For those who have laptop-mode-tools installed:**

Follow the steps in post [#12]("http://ubuntuforums.org/showpost.php?p=12065536&postcount=12"). This should be your only option as *laptop-mode-tools* is designed to override the system defaults.

**For those who don't:**

You either have some other power management tool installed to handle your USB auto-suspension settings or your system is using its defaults for the USB devices. With any other tool, you should first try and find a setting to disable or customize the USB auto-suspend feature. If you don't have any power management tools installed, you can tackle the problem at its source: **the USB device defaults**.

You find your USB devices in the **/sys/bus/usb/devices** folder. Now, the naming convention for the device subfolders you find here is a bit tricky. It's nicely documented [here]("http://www.linux-usb.org/FAQ.html#i6"). To identify your USB mouse use the terminal:
```
lsusb
```It should give you the bus and device numbers for your USB mouse which you can then use to identify the appropriate subfolder under the aforementioned **/sys/bus/usb/devices**. Another trick is to unplug/replug your mouse while refreshing the contents of this folder. The subfolder for your mouse should disappear/reappear so now you know which one it is. Once you find the subfolder for the mouse, open it, navigate to the **power** folder and look for the file **autosuspend_delay_ms**. So the full path is:

**/sys/bus/usb/devices/*(your USB mouse subfolder)*/power/autosuspend_delay_ms**

This file contains the timeout in milliseconds after which your mouse goes to sleep. Open it as administrator and change its content (the default is probably *2000*) to **-1**. This will tell the device not to suspend, ever.

Save it and you're good to go.

[COLOR=Gray]Note that there's a file in the same folder called **autosuspend**. This file [is deprecated]("http://www.mjmwired.net/kernel/Documentation/usb/power-management.txt#104") since **2.6.38** but for some reason it's still present. Probably just to confuse the fsck out of everyone.[/COLOR]

---

### Post by Salvagluque on 2012-07-01
ok, I could find the file but the text editor denies me to save or replace the original file, eventhough I went to the folder with sudo nautilus.

Thanks

for the help

---

### Post by kAzblakh on 2012-07-02
You should always use **gksudo** instead of **sudo** for graphical applications:
```
**gk**sudo gedit /sys/bus/usb/devices/*(your USB mouse subfolder)*/power/autosuspend_delay_ms
``` Nonetheless, it will probably still deny to save the file. I'm using Pluma (the MATE equivalent of gedit) and indeed it tells me that the file cannot be saved. Funnily, it saves it properly anyway. If it still doesn't work for you, you should probably fiddle around with permissions.

---

