---
title: "which is the best script in which I can put the code to set the resolution of screen"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by richardjl on 2013-03-02
Greetings.

My monitor support 1680*1050 resolution. However, when my ubuntu startup, it only provide two options 1024*768 or 800*600 and it is in 1024*768 by default. 

I found some code which can enable the high resoltion. After excuting the following command, my screen shows the resoltion of 1680*1050 now.
cvt 1680 1050
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA1 "1680x1050_60.00"
xrandr --output VGA1 --mode  "1680x1050_60.00" 

However, I hope the above script can be excuted automatically. I am expecting the script can be excuted after I login. I tried rc.local and it doesn't work. In which script should I put above code ? 

Thanks!

---

### Post by prodigy_ on 2013-03-02
Try to run your script via /etc/lightdm/lightdm.conf:
[http://askubuntu.com/questions/73804/wrong-login-screen-resolution](http://askubuntu.com/questions/73804/wrong-login-screen-resolution)

---

### Post by richardjl on 2013-03-02
Greetings.

My monitor support 1680*1050 resolution. However, when my ubuntu startup, it only provide two options 1024*768 or 800*600 and it is in 1024*768 by default. 

I found some code which can enable the high resoltion. After excuting the following command, my screen shows the resoltion of 1680*1050 now.
cvt 1680 1050
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA1 "1680x1050_60.00"
xrandr --output VGA1 --mode  "1680x1050_60.00" 

However, I hope the above script can be excuted automatically. I am expecting the script can be excuted after I login. I tried rc.local and it doesn't work. In which script should I put above code ? 

Thanks!

---

### Post by cortman on 2013-03-02
> **richardjl said:**
> Greetings.

My monitor support 1680*1050 resolution. However, when my ubuntu startup, it only provide two options 1024*768 or 800*600 and it is in 1024*768 by default. 

I found some code which can enable the high resoltion. After excuting the following command, my screen shows the resoltion of 1680*1050 now.
cvt 1680 1050
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA1 "1680x1050_60.00"
xrandr --output VGA1 --mode  "1680x1050_60.00" 

However, I hope the above script can be excuted automatically. I am expecting the script can be excuted after I login. I tried rc.local and it doesn't work. In which script should I put above code ? 

Thanks!

If the xrandr commands indeed work, that's great! I've never had much success adding new modes to xrandr.
To turn these commands into a script, first copy the code into a text file, and save it in ~/bin. If the folder doesn't exist, create it. Mark it executable by running

```
chmod +x ~/bin/your_script
```

It's easy to set the script to run at startup, but it depends what DE you're using.  I wrote an article on adding startup scripts [here]("http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/").

---

### Post by matt_symes on 2013-03-02
Hi

> I found some code which can enable the high resoltion. After excuting  the following command, my screen shows the resoltion of 1680*1050 now.
cvt 1680 1050
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA1 "1680x1050_60.00"
xrandr --output VGA1 --mode  "1680x1050_60.00"

Kernel mode setting is not working correctly ?

> However, I hope the above script can be excuted automatically. I am  expecting the script can be excuted after I login. I tried rc.local and  it doesn't work. In which script should I put above code ?

At this point the xserver is not running so xrandr will not work.

I would put your script in ~/.xsession in your home directory.

Open a terminal and type

```
nano ~/.xsession
```

Copy and paste the above lines into it.

Remember to make the script executable.

```
chmod 755 .xsession
```

Hopefully that should get you going. 

Post back on efficacy as i am not surrently using Unity.

Kind regards

---

### Post by mörgæs on 2013-03-02
Please don't double-post.
Merged.

---

### Post by richardjl on 2013-03-03
Thank all for your providing help!
 According to the suggestions in the replies, I tried two ways:  

1. create a script to set the monitor mode and then put a line in the /etc/lightdm/lightdm.conf. This way works perfect! 

2. create ~/.xsession in my home directory, in which the script for setting the monitor mode is included. Unfortunately, this does not work in my computer. I dont know the reason.  I found there is a file .xsession-errors and have the following error message. I guess this might be related to the reason when .xsession does not work in my PC.  

[I]** (zeitgeist-datahub:2299): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus! failed to create drawable 
compiz (core) - Warn: glXCreatePixmap failed 
compiz (core) - Warn: Couldn't bind background pixmap 0x1c00001 to texture 
(gnome-settings-daemon:1980): color-plugin-WARNING **: unable to get EDID for xrandr-VGA-0: unable to get EDID for output 
(gnome-settings-daemon:1980): color-plugin-WARNING **: unable to get EDID for xrandr-VGA-0: unable to get EDID for output 
(gnome-settings-daemon:1980): color-plugin-WARNING **: unable to get EDID for xrandr-VGA-0: unable to get EDID for output 
(gnome-settings-daemon:1980): color-plugin-WARNING **: unable to get EDID for xrandr-VGA-0: unable to get EDID for output 
(gnome-settings-daemon:1980): color-plugin-WARNING **: unable to get EDID for xrandr-VGA-0: unable to get EDID for output 
failed to create drawable 
compiz (core) - Warn: glXCreatePixmap failed 
compiz (core) - Warn: Couldn't bind background pixmap 0x4000001 to texture 
** (nautilus:2004): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist 
** (nautilus:2004): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed 
(gnome-settings-daemon:1980): print-notifications-plugin-CRITICAL **: gsd_print_notifications_plugin_finalize: assertion `plugin->priv != NULL' failed 
(gnome-settings-daemon:1980): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
(gnome-settings-daemon:1980): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
(gnome-fallback-mount-helper:2007): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0. 
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0. 
(vino-server:2005): Gdk-WARNING **: vino-server: Fatal IO error 11 (Resource temporarily unavailable) on X server :0. 
(bluetooth-applet:2009): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/I]

---

### Post by matt_symes on 2013-03-04
Hi

Thanks for posting back especially about ~/.xsession. That was the traditional way of setting settings for your xsession.

That obviously does not work in Ubuntu although i will run some tests myself.

> *(gnome-settings-daemon:1980): color-plugin-WARNING **: unable to get EDID for xrandr-VGA-0: unable to get EDID for output *

This is the reason why your resolution is stuck at startup.

Your monitor EDID contains the modes (screen resolutions) your monitor can run at.

As Ubuntu has not been able to get this it defualts to the resolution to have been getting at startup.

You can confirm this by checking 

```
/var/log/xorg.0.log
```

Kind regards

---

