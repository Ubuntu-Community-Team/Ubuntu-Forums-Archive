---
title: "SOLUTION for Brightness-Problem"
date: 2015-09-15
forum: New to Ubuntu
---

### Post by hamza5 on 2015-09-15
hey guys,
i am very new to ubuntu. as i installed ubuntu 14.04, i came across this well know brightness problem. meaning; the key combination [fn] [f5]/[f6] was creating now change in the brightness of my monitor. finally i came across the following post:
--------------------------------------------------------------------------------------------------
                                                                                                                                                             January 26th, 2013                                                                                                                                                                                                     [#2]("http://ubuntuforums.org/showthread.php?t=2109104&p=12475771#post12475771")                                                                                                                                                                                              
                                                             [                                                      [IMG]http://ubuntuforums.org/images/avatars/UF_Logo_original_90.png[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=1276411")                                                                                     [**[COLOR=#000000]frank604[/COLOR]**]("http://ubuntuforums.org/member.php?u=1276411")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]                                                                    A Carafe of Ubuntu                                                                   [IMG]http://ubuntuforums.org/images/rank_15.png[/IMG]                                                                                                                                                                                            
                                      
             
                                                   Join DateApr 2011LocationVictoria/Vancouver, BCBeans96DistroUbuntu 12.04 Precise Pangolin                                                           
                      
     
                                          **Re: Brightness function does not work. Always stays at the max**

                                                                                                       What model is that Gateway laptop?  The steps shown in this article  had a Gateway Laptop NV57H resolve this issue.  Wouldn't hurt to do the  following steps in the guide.  [URL="http://www.refreshit.info/2012/08/solved-brightness-increase-and-decrease.html"]http://www.refreshit.info/2012/08/so...-decrease.html
[/URL]

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

very simple and straight forward solution which was unfortunately not marked as [SOLVED]. therefore this post.
hopefully this will help other users as well!

---

### Post by kerry_s on 2015-09-15
on my toshiba t135 i have to create a /usr/share/X11/xorg.conf.d/20-intel.conf with this in it:
```


Section "Device"
    Identifier  "Intel Graphics"
    Driver      "intel"
    Option      "Backlight"  "intel_backlight"
EndSection


```

then just reboot. 
on my toshiba the key's are fn+ f6/f7 .
only announce is on start up it's always set to max, doesn't remember what it was last set at.

---

