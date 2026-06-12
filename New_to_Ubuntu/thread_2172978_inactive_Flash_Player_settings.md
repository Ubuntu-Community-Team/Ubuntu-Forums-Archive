---
title: "inactive Flash Player settings"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-09-07
Hi all, 

I have got inactive Flash Player settings: 

[http://www.dumpt.com/img/viewer.php?file=0ry6zb8gkpirfkqwojo1.png](http://www.dumpt.com/img/viewer.php?file=0ry6zb8gkpirfkqwojo1.png)

"Allow" and "Remember" are inactive. 

What can be wrong? 

Ubuntu 12.04 LTS
Unity
Firefox 23.0

---

### Post by Drone4four on 2013-09-07
Have you tried [this]("http://askubuntu.com/questions/105261/not-able-to-change-flash-settings")? Here is a copy and paste from the link:> The easiest way to disable hardware acceleration in flash is to do it in the flash player window from the right click > settings & un-check the box for hardware acceleration.

In many cases though the box can't be clicked. If that's the case then you must not have scrollbars present so use F11 to fullscreen the window, then you'll be able to click in the box. After doing so press F11 again to return to normal window. (happens mainly when using compiz. On a 32 bit player going fullscreen works here, on a 64 bit player it currently doesn't

I don't see a "Adobe flash player settings panel" but if it's available with the option to disable hw accelerating then try to full screen it if the box isn't clickable

An alternate method would be to access the player settings in a non compiz session which is the surest way to do

---

### Post by Marchello_Lippi on 2013-09-08
[**[COLOR=#000000]Drone4four[/COLOR]**]("http://ubuntuforums.org/member.php?u=297831"),

Thanks! This chunk of text helped me after I followed your link: 


[I]You can [change flash privacy settings for specific websites online]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html").

  The settings are stored in your browser and then you can do things  like use Youtube and your own webcam to create and upload a video.[/I]

---

