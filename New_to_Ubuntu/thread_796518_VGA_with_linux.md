---
title: "VGA with linux"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by natman on 2008-05-16
Hi, 
I am running Kubuntu kde4 and want to give a presentation at work using kubuntu. My laptop has an nvidia vga and s video out ports. Im guessing its not as simple as hitting ctrl+F4 to switch  displays.
How do i go about using the vga? is it even possible?

Thanks:
Patrick

---

### Post by aimpau on 2008-05-16
Are you able to connect it to the LCD screen using the serial connection (the one with many holes in it)?

I have an HP Pavillion and yep, if you connect the LCD projector to your laptop, it is pretty simple to switch to view it.

[edit]

Use the "FN" key and look for an icon of what looks like a screen in the function keys.

---

### Post by EXCiD3 on 2008-05-16
I have been able to use VGA out, svideo out, and even my hdmi out all by using the nvidia-settings tool (installed along with your nvidia driver). Just open terminal and do ```
sudo nvidia-settings
``` to configure it and everything should work fine except for audio through svideo and hdmi...still havent figured that one out yet.

You may be able to automatically have it configured by using the FN keys as mentioned earlier. Its worth a shot since the nvidia-settings method takes a little while to setup. You can save your settings and merge them into your xorg.conf to have it automatically load that configuration if it detects the external screen if you save it to your xorg.conf.

---

### Post by natman on 2008-05-16
I havent tried yet to hook up the laptop under 804 to the projector. I wil try again over the weekend and see if it works.

---

### Post by natman on 2008-05-16
OK i just hooked up the laptop to a spare LCD screen via the vga cabel, cable plugged in from boot. Nothing, hit ctrl and the f key nothiing tried all alt+F super+F all nothing.
any ideas?

---

### Post by EXCiD3 on 2008-05-16
Did you try the nvidia-settings tool like I mentioned?

---

### Post by natman on 2008-05-16
Yea, i have no nvidia settings, all i have is nvidia -xconfig, i ran it
Then loged in and out repeated again and no change

---

### Post by EXCiD3 on 2008-05-16
try searching synaptic for nvidia-settings. if it asks to remove your nvidia driver dont do it because then you wont have a graphics driver anymore. nvidia-xconfig wont do the trick because it only configures the default monitor.

---

### Post by natman on 2008-05-16
Perfect thank you so much, its working but i cant get the exact display on the other screen always either and etnded version of my current or a way out resoultion, guess i will have to play with the settings, thank you so much

---

### Post by EXCiD3 on 2008-05-16
You're welcome. There are a lot of different things you can configure with that. Ive had it hooked up to my HDTV and there are lots of different configurations. It took me a while but i realized you can click and drag the monitor boxes to change their positions. ;) Whats the problem you were having? Maybe i can help get you started with configuring them too, im just not quite sure what you mean.

---

### Post by natman on 2008-05-16
Its just that when i switch displays, the external screen was only ever showing a portion of the actual screen, like the far right
Im guess i have to set some values to get it just right, if i find a sweet spot do i save to xorg?

---

### Post by EXCiD3 on 2008-05-16
Yes if you figure out your configuration you like, you can choose Save to X Configuration File, make sure you check the Merge button, then save it and next time you start the xserver with that plugged it in will automatically use that configuration.

Is your external screen using a smaller resolution by any chance? You might try using separate xservers instead of using twinview.

---

