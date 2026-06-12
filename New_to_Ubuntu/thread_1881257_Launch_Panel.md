---
title: "Launch Panel"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by leilton on 2011-11-15
No Not complaining about either the panel or unity.   Just wish I could find out how you get the panel to do all the wonderful things it should do. i.e. fade or dodge window.   Mine just sits and defies me to get it out of the way of my working.

Yes have been to Unity Plug in, and ticked all the options one by one.

Please, before it drives me mad, how do you get it to do as its meant.

---

### Post by BillyBoa on 2011-11-15
Try to reset Unity to see if the problem insists. In a terminal write the command:


```
unity --reset
```

---

### Post by leilton on 2011-11-15
> **BillyBoa said:**
> Try to reset Unity to see if the problem insists. In a terminal write the command:


```
unity --reset
```
Thank you BillyBoa, have tried to do that, if I only knew how, would post the page length response I got.

Think gist of response, is that there is a problem with my Unity set up.

Will havel have to site down and think way through either trying to repair, or at worst delete and re-install Unity.   Did not want to do either really, as taken me nearly two weeks to understand how to get this far.

Many thanks for help

---

### Post by leilton on 2011-11-23
Yes I know this is not a new Thread.

Just spent nearly an hour going back and fro trying to find my oringinal question, and the response that I had, but system says I have not posted anything.   So here go's again.

I had successfully, I hoped, installed Ubuntu 11.4,  after a lot of trial and error and  got the panel on the left,where is should be, only trouble is that it will now not move, whatever commands I give via Unity Plug in.   Helpful member suggested that I reinstall Unity, but that did not work.

There is not much more that I think I can safely do, always bearing in mind a complete novice, and don't want to lose what I have.   

Apart from removing panel altogether, is there anyway I can get it to function?

---

### Post by Frogs Hair on 2011-11-23
Hello leilton ,

What exactly are you having trouble with ? I'm not sure what you mean by  "where it should be"

When you me say it doesn't move do you mean the auto hide in the unity plug-in is not working ? Unity can be reset via the terminal with the following command .```
unity --reset
```
To reset icons only .```
unity --reset-icons
``` 

To find you your previous poats select your user name and on your profile page select statistics . This will display your started threads and posts .

---

### Post by 3rdalbum on 2011-11-23
Indulge me: Make sure you've got the Dodge Windows item selected in the "Hide Launcher" popup menu in the Unity Plugin. Move your mouse away from the left side of the screen, and hold down the Super key (it's usually marked with a Windows logo). Release the Super key. Does the Launcher hide now?

---

### Post by leilton on 2011-11-23
For Frogs Hair and3rdAlbum.

Thanks for quick response.

Have not explained myself well have I.

By where its meant to be, I mean on the left side of the screen.   Was advised by Billy Boa to do as you suggested, i.e. Unity-reset, nothing changed.

Have tried all four options in Unity Plugin, Dodge, Dodge Active, Auto Hide and Never,to no avail..

Left setting as Dodge, and have just tried what you suggested, all that appeared to happen was that I got numbers displayed on the icons in the panel, which still does not fade, move, or whatever it is meant to do, very disconcerting, as means cannot reach minimize, close etc buttons on window panel.

Hope this has made my problems clearer to you.

---

### Post by Frogs Hair on 2011-11-23
If you have the CCSM installed I'm assuming you have installed a proprietary driver from additional drivers for your Graphics card /chip . 

To find out for sure if you can run unity 3d run the following command .```
/usr/lib/nux/unity_support_test -p
``` 

To completely reset Compiz / Unity use the following .```
gconftool-2 --recursive-unset /apps/compiz-1

unity --reset

```

If the desktop is blank ```
ccsm
```

---

### Post by leilton on 2011-11-24
Hi Frogs Hair.

The following are the results of doing as you suggested.   Sorry for taking time to get back to you, but as a novice, have gone grey working out how to do even this simple task.

Does it give any indication, all double dutch to me, as to what  my problem is?

Before I forget, thanks for taking the time to assist.

```
edward@edward-AMILO-PRO-V2030:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: no
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    no
GL version is 1.4+:       no

Unity supported:          no 


edward@edward-AMILO-PRO-V2030:~$ gconftool-2 --recursive-unset /apps/compiz-1 
edward@edward-AMILO-PRO-V2030:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Support for non power of two textures missing
Compiz (bailer) - Info: Ensuring a shell for your session
edward@edward-AMILO-PRO-V2030:~$ Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (438605).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
edward@edward-AMILO-PRO-V2030:~$ Unable to open desktop file /usr/share/applications/chromium-browser.desktop for panel launcher: No such file or directory
edward@edward-AMILO-PRO-V2030:~$ Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (757880).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (888761).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...

(metacity:2539): LIBDBUSMENU-GLIB-WARNING **: About to Show called on an item wihtout submenus.  We're ignoring it.
Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (1053805).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
edward@edward-AMILO-PRO-V2030:~$ Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (1220204).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (1522533).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
edward@edward-AMILO-PRO-V2030:~$ Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (1555666).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...

```
Did not do three suggestion as assumed only to do if my screen went blank, which ii didn't

---

### Post by nothingspecial on 2011-11-24
Hi there,

When posting output from your terminal, please use code tags.

The easiest way to do that is to highlight the text and click the # in the formatting options at the top of the posting box.

It makes the output much easier to read and will help people to assist you :)

---

### Post by Frogs Hair on 2011-11-24
> **leilton said:**
> Hi Frogs Hair.

The following are the results of doing as you suggested.   Sorry for taking time to get back to you, but as a novice, have gone grey working out how to do even this simple task.

Does it give any indication, all double dutch to me, as to what  my problem is?

Before I forget, thanks for taking the time to assist.

```
edward@edward-AMILO-PRO-V2030:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: no
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    no
GL version is 1.4+:       no

Unity supported:          no 


edward@edward-AMILO-PRO-V2030:~$ gconftool-2 --recursive-unset /apps/compiz-1 
edward@edward-AMILO-PRO-V2030:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Support for non power of two textures missing
Compiz (bailer) - Info: Ensuring a shell for your session
edward@edward-AMILO-PRO-V2030:~$ Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (438605).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
edward@edward-AMILO-PRO-V2030:~$ Unable to open desktop file /usr/share/applications/chromium-browser.desktop for panel launcher: No such file or directory
edward@edward-AMILO-PRO-V2030:~$ Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (757880).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (888761).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...

(metacity:2539): LIBDBUSMENU-GLIB-WARNING **: About to Show called on an item wihtout submenus.  We're ignoring it.
Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (1053805).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
edward@edward-AMILO-PRO-V2030:~$ Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (1220204).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (1522533).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...
edward@edward-AMILO-PRO-V2030:~$ Window manager warning: last_user_time (1322133780) is greater than comparison timestamp (1555666).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x40005dc (edward@edw) appears to be one of the offending windows with a timestamp of 1322133780.  Working around...

```
Did not do three suggestion as assumed only to do if my screen went blank, which ii didn't

The support test indicates your system can't run Unity 3D and that is why it is not fully functional . You can happily run Ubuntu 2D or install the Gnome shell from the software center  and see how it works for you .

---

### Post by leilton on 2011-11-24
For: Nothingspecial.

```
As I have mentioned in any threads I have started, or responded to, I am very new to Linux, (except for a spell with Open Suse), and still feeling my way around it.

I had assumed that as I was responding to a reply to my question regarding malfunction of the Launch Panel, that Frogs Hair would understand  the message.

I am afraid I did not know about the  ' code tags', and if I have done something wrong I apologies, , and will  try and ensure I do it in the future.
```

---

