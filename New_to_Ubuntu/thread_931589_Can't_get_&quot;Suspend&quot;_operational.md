---
title: "Can't get &quot;Suspend&quot; operational"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by faron45 on 2008-09-27
Okay,folks-I posted this yesterday & received absolutely no replies.I figured I'd try one more time over the weekend since there may be more traffic.Sorry for the repost...
 
 
I've tried everything possible [I think] [google,etc,etc] but,to no avail.I've been working on this problem for hours now & finally decided to give you guys a try.....

I've finally gotten my screensaver and power management to work through hours of exhaustive research.But,now,I'd like to be able to have both of the options ["suspend" & "hibernate"] available to me since I seem to have buttons for both.Only "hibernate" works though.And,under "Power Management Preferences",I seem to only have the option to "hibernate" or "do nothing" when the suspend button is pressed.....
.
Why does "suspend" not work on my pc when I have the button for it,and, why is there not an option to "suspend",rather than just "hibernate" or "do nothing" under "Power Management Preferences" ?

All help GREATLY appreciated

And,for some reason now,smilies seem to not be fuctioning.Wonder if java script needs to be on for that.Hmmmm.

Yer pal...J.Garcia
aka...faron45

---

### Post by chrisod on 2008-09-27
Have you tried suspending from the CL? 

 ```
sudo /etc/acpi/sleep.sh sleep
```

My laptop won't suspend with the power button or the suspend option in the shut down menu, but it works just fine from the command line.

---

### Post by faron45 on 2008-09-27
chrisod-No,my friend.I haven't tried this.But,see,my purpose is to be able to have those buttons available to me.Particularly,so power management can handle them automatically after a certain time period of inactivity.
         Thanks,faron.

---

