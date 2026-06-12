---
title: "Unable to set the right screen resolution"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by Adnihil on 2012-08-10
Hello,

The correct screen resolution for my monitor is 1024x1280, but in the Display menu, I can only choose between 800x600 and 1024x768. (Screenshot 1)
It also says Laptop for some reason, while I'm on a desktop computer.

I tried all four different drivers, but none of them work correctly. The first two don't even allow me to choose 1024x768. (Screenshot 2)
I also tried downloading the correct driver from nvidia.com, but when I try to run the file, it just opens up a blank window that crashes after a few minutes.

Any help?

---

### Post by johnathansmith on 2012-08-10
Hi
```
Due to buggy hardware or drivers, your monitor's correct resolutions may not always be detected. For example, the EDID data block queried from your monitor may be incorrect.

If the mode already exists, but just isn't associated for the particular output, you can add it like this:


  $ xrandr --addmode S-video 800x600
If the mode doesn't yet exist, you'll need to create it first by specifying a modeline:


  $ xrandr --newmode <Mode``Line>
You may create a modeline using the gtf or cvt utility. For example, if you want to add a mode with resolution 800x600 at 60 Hz, you can enter the following command: (The output is shown following.)


  $ cvt 800 600 60
  # 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
  Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
Then copy the information after the word "Modeline" into the xrandr command:


  $ xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
After the mode is entered, it needs to be added to the output using the --addmode command as explained above.


```
You can find more information [HERE]("https://wiki.ubuntu.com/X/Config/Resolution/") if you don't understand something, feel free to ask.

---

### Post by Adnihil on 2012-09-15
Thank you for your reply.
I'm still pretty clueless though.

> If the mode doesn't yet exist, you'll need to create it first by **specifying a modeline**:
Where or how can I do this?

> You may create a modeline using the **gtf or cvt utility**.
What are these?

I am very new to Ubuntu and have absolutely no idea where to begin.

---

### Post by Wim Sturkenboom on 2012-09-15
> 
Where or how can I do this?

In a terminal (assuming you use ubuntu 12.04: press <ctrl><alt>t)

> 
What are these?

Commands that you can use ;)

A copy from the first reply; in bold blue the command to issue in the terminal and in red the 'important part' of the output that the command will give.
> 
```

$ **[COLOR="Blue"]cvt 800 600 60[/COLOR]**
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
[COLOR="Red"]Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync[/COLOR]

```
Then copy the information after the word "Modeline" into the xrandr command:
```

$ **[COLOR="Blue"]xrandr --newmode _"800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync_[/COLOR]**

```

After the mode is entered, it needs to be added to the output using the --addmode command as explained above.

The underlined part in the second code block is what you copy from the result of the first command (the red line).

Note:
you need to adjust the parameters for the cvt command; check the specs
```

cvt pixhor pixvert refreshrate

```
pixhor and pixvert define the resolution (for you probably 1280 and 1024 respectively. Check the vertical refresh rate of your monitor at that resolution (e.g. 60Hz, 70Hz or maybe 50Hz) and fill that number in for the refreshrate.

---

### Post by Adnihil on 2013-06-19
Whoa, I forgot all about this thread. Thank you.

---

