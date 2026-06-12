---
title: "I lost volume control"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-05-18
I changed my desktop from taskbars to the AWN dock. Before I did that though I lowered the sound. I dont have taskbars anymore because I got rid of them and I use AWN now. Problem is, I have no volume control. In AWN there is an applet for volume control but it doesnt work. The trash applet doesnt work either. The AWN dock is terrible, its full of bugs, I just want things to work. Id like to go back to using the taskbar but I dont know how to bring them back.

---

### Post by SunnyRabbiera on 2008-05-18
Well AWN is still experimental so issues are to be expected.
But first do you have at least one panel around?
If you do I can give you suggestions on what to put in it.

---

### Post by Bigtime_Scrub on 2008-05-18
No I have no sound panels. I have no deskbars or panels period.

---

### Post by ryanhaigh on 2008-05-18
Did you use the most up to date version of AWN from the ppa, I used it for a long time on gutsy but have since reverted for other reasons. 

To use the latest version follow [these instructions]("http://ubuntuforums.org/showthread.php?t=762363").

For the volume issue you may need to change the device that the applet is set to adjust. I have to use Front on my desktop but the laptop needs Master or PCM.

---

### Post by Bigtime_Scrub on 2008-05-18
I also dont get update notifications any more. i just run them through terminal every 2 days because I dont know when they are ready.

If I had known AWN was experimental I never would have installed it.

I just want to add a taskbar on the top but I ended the session and I dont know how to get it back.

---

### Post by Bigtime_Scrub on 2008-05-18
I figured it out.

I needed to reinstall gnome-panel for some weird reason.

sudo apt-get install gnome-panel

The AWN trash, volume control, auto-update, and alt-f2 did not work. Before you delete the panels, and use AWN be sure to remove from them all the applets! It is extremely important to remove all the applets and let the panels "naked" for the AWN dock to perform properly!

Unfortunatly, my volume control STILL does not work. When I right click panel and click Add to panel -> Volume control I get this error message:

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

---

### Post by ryanhaigh on 2008-05-18
What do you mean you ended the session? If you just disabled gnome panel  from system>preferences>session then you should simply be able to re-enable it from there as well. After making the change you will need to logout and back in. 

As for not getting update notifications you can also change that from system>preferences>sessions, I believe its called update notifier. If this is still enabled then you just need to add the system tray applet (sorry if thats not the exact name) to awn.

In my experience using awn from the PPA repository as discussed in that thread stable enough for daily use.

By the way to get to those menu items I have discussed even if you have no panels you may need to start gnome-panel, alt-f2 then enter gnome-panel, then use alt-f1 to bring up the menu even without a bar.

---

### Post by Bigtime_Scrub on 2008-05-18
> **ryanhaigh said:**
> What do you mean you ended the session? If you just disabled gnome panel  from system>preferences>session then you should simply be able to re-enable it from there as well. After making the change you will need to logout and back in. 

As for not getting update notifications you can also change that from system>preferences>sessions, I believe its called update notifier. If this is still enabled then you just need to add the system tray applet (sorry if thats not the exact name) to awn.

In my experience using awn from the PPA repository as discussed in that thread stable enough for daily use.

By the way to get to those menu items I have discussed even if you have no panels you may need to start gnome-panel, alt-f2 then enter gnome-panel, then use alt-f1 to bring up the menu even without a bar.

See the alt-f2 did not work either that was part of the problem. I got it to work now. I think I deleted gnome-panel by mistake when I was trying to get rid of them. 

I just need to find a way to get the volume applet on gnome panel working now.

---

### Post by ryanhaigh on 2008-05-18
Sorry my mistake, alt-f2 actually calls the gnome-panel run dialog, so without gnome-panel running it obviously will not work. 

Apparently to address the volume applet issue you just need to reinstall [apt://gnome-applets]("apt://gnome-applets"). 

[http://ubuntuforums.org/archive/index.php/t-25259.html](http://ubuntuforums.org/archive/index.php/t-25259.html) for more info

---

