---
title: "Unity Broke after latest round of updates (10/10)"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by penguinmaster on 2011-10-10
Unity was working fine before updates, but after a quick reboot I'm greeted with a blue screen and very basic looking desktop.  A lot of the icons are missing on the launcher as well.  I went to the terminal and tried to do a unity --reset and was given this result.

tom@Tom-D:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Window manager warning: Failed to load theme "Adwaita": Failed to find a valid file for theme Adwaita

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session
tom@Tom-D:~$ Window manager warning: Failed to load theme "Adwaita": Failed to find a valid file for theme Adwaita

Any thoughts?

Thanks!

Tom

---

### Post by lucazade on 2011-10-10
> **penguinmaster said:**
> Unity was working fine before updates, but after a quick reboot I'm greeted with a blue screen and very basic looking desktop.  A lot of the icons are missing on the launcher as well.  I went to the terminal and tried to do a unity --reset and was given this result.

tom@Tom-D:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Window manager warning: Failed to load theme "Adwaita": Failed to find a valid file for theme Adwaita

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
[B]Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected[/B]
Compiz (bailer) - Info: Ensuring a shell for your session
tom@Tom-D:~$ Window manager warning: Failed to load theme "Adwaita": Failed to find a valid file for theme Adwaita

Any thoughts?

Thanks!

Tom

reinstall video drivers

---

### Post by collisionystm on 2011-10-10
Are you running 11.10?

> Failed to load theme "Adwaita": Failed to find a valid file for theme Adwaita

---

### Post by effenberg0x0 on 2011-10-10
Hey,

I don't have a punctual workaround for your problem. But the bulk solution, that generally works, is described here:

[http://ubuntuforums.org/showpost.php?p=11319420&postcount=4](http://ubuntuforums.org/showpost.php?p=11319420&postcount=4)
(considering you have proper video drivers installed - as Lucazade mentioned)
Regards,
Effenberg

---

### Post by penguinmaster on 2011-10-10
> **lucazade said:**
> reinstall video drivers

I'll give that a shot and yes I am running 11.10. 

Thanks!

---

### Post by penguinmaster on 2011-10-10
Updating and reinstalling the driver got me one step further but the issues are still there.  Honestly at this point I'll just wait for the final release to come out and hopefully that solves my issue.  The system is "usable" enough for me to get my VM up and running which I can work out of for the next two days so that's fine.  

Reality is I should have never updated to the beta as soon as I did, granted this is the most trouble I've had in a long time with an Ubuntu beta!  Oh well, live and learn.

---

### Post by dino99 on 2011-10-10
if you check "system settings" you can choose radiane or ambience instead of adwaita (and it loks better)
Adwaita is from a ppa

---

### Post by sgage on 2011-10-10
> **dino99 said:**
> if you check "system settings" you can choose radiane or ambience instead of adwaita (and it loks better)
Adwaita is from a ppa

Adwaita also comes with Gnome Shell from the stock repos.

---

### Post by penguinmaster on 2011-10-10
> **dino99 said:**
> if you check "system settings" you can choose radiane or ambience instead of adwaita (and it loks better)
Adwaita is from a ppa


HA!, I love it, that's exactly what worked.  Sometimes it's the easiest solution that fixes things.  

I do find it a bit weird though that it was set to Adwaita, as I've never selected a theme.  Either way, I'm happy that it's back up and running.

-Tom

---

