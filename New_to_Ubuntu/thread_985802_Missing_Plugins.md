---
title: "Missing Plugins"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by acreech on 2008-11-18
My 7 year old son likes playing junkbot at the following website [http://www.lego.com/eng/create/activities/junkbot/]("http://www.lego.com/eng/create/activities/junkbot/")

Ever since changing over to Linux he has not been able to play the game. When I go to the site firefox tells me that i am missing a plugin and Firefox can not find a suitable plugin for the game. 

How do I get my computer to play this game? I have Ubuntu 8.10 with a 32 bit system.

---

### Post by shredder12 on 2008-11-18
There should be a plugin available for firefox to play this game. Newaz.. did he use firefox to play that game earlier when you were not using linux..... if you used IE at that time then you could try to use run IE on linux using wine... 
May be that will help..

---

### Post by acreech on 2008-11-18
he used IE on a Windows XP system. I have read threads in the past about wine. I will see if I can find some useful instructions for that. I am not that familiar with wine.

---

### Post by frankleeee on 2008-11-18
> **acreech said:**
> My 7 year old son likes playing junkbot at the following website [http://www.lego.com/eng/create/activities/junkbot/]("http://www.lego.com/eng/create/activities/junkbot/")

Ever since changing over to Linux he has not been able to play the game. When I go to the site firefox tells me that i am missing a plugin and Firefox can not find a suitable plugin for the game. 

How do I get my computer to play this game? I have Ubuntu 8.10 with a 32 bit system.

what is the pluggin,

---

### Post by Crafty Kisses on 2008-11-18
Try pasting this command in the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by frankleeee on 2008-11-18
> **Codename said:**
> Try pasting this command in the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

That wont do it I am on the website now and I have everything needed installed for every other site and can't get it to identify the plugin or work,

---

### Post by acreech on 2008-11-18
Ya I saw another post that suggested adding the restricted extras so I did that before. firefox tells tells you that you are missing a plugin , but then it does not tell you which one. it has been one of the least of my worries, but seems how I have everything else working, I thought that I would try to get this working too.

---

### Post by ubuntu27 on 2008-11-18
Hello acreech.

It seems to me that the Lego.com website uses ShockWave (similar to Flash).
Adobe never released Shockwave for GNU/Linux.

The only way to be able to interact with pages with ShockWave is install Wine, install Windows' Firefox, and install Shockwave through Wine.

Here is a guide to Install Shockwave for Linux:

[https://help.ubuntu.com/community/Shockwave]("https://help.ubuntu.com/community/Shockwave")



Hope that helps.

EDIT: yes, I just confirmed. That website uses Shockwave, confirmedd by looking through its source code.

> <div class="mc-generic" style="background-image : url([http://cache.lego.com/images/create/mainpagepane753x10BG.gif);background-repeat:](http://cache.lego.com/images/create/mainpagepane753x10BG.gif);background-repeat:) repeat-y;">
			<img src="http://cache.lego.com/images/create/mainpagepane753x12header.gif" width="753" height="12" alt="" border="0" /><br />
				<div align="center">
									<object classid="clsid:166B1BCA-3F9C-11CF-8075-444553540000" codebase="http://download.macromedia.com/pub/**shockwave**/cabs/director/sw.cab#version=8,0,0,0" ID="junkbot2_13g_asp" width="650" height="420" VIEWASTEXT>
										<param name="src" value="junkbot2_13g_asp.dcr">
										<param name="swRemote" value="swContextMenu='false'">

										<param name="swStretchStyle" value="none">
										<PARAM NAME="bgColor" VALUE="#FFFFFF">
										<embed src="junkbot2_13g_asp.dcr" bgColor="#FFFFFF" width="650" height="420" swRemote="swContextMenu='false'" swStretchStyle="none" type="application/x-director" pluginspage="http://www.macromedia.com/**shockwav****e/**download/"></embed>
									</object>

---

### Post by acreech on 2008-11-18
thanks for the help. I will give it a shot.

---

### Post by frankleeee on 2008-11-18
> **ubuntu27 said:**
> Hello acreech.

It seems to me that the Lego.com website uses ShockWave (similar to Flash).
Adobe never released Shockwave for GNU/Linux.

The only way to be able to interact with pages with ShockWave is install Wine, install Windows' Firefox, and install Shockwave through Wine.

Here is a guide to Install Shockwave for Linux:

[https://help.ubuntu.com/community/Shockwave]("https://help.ubuntu.com/community/Shockwave")


Hope that helps.

I have shockwave and cannot get the web site to work. Actually I switched computers and shockwave does run the site good job figuring that out.

---

### Post by acreech on 2008-11-18
I was doing good with installing the windows firefox and the macromedia shockwave, until I reached this step..... 

> 
Finally, you need to make Firefox reload the plugin database. Close all Firefox windows and run this command in a terminal:

rm ~/.mozilla/firefox/pluginreg.dat

In later versions this file may have been moved:

rm ~/.mozilla/firefox/ln4t0cle.default/pluginreg.dat


the first problem is that the file is in a different location. I found that file though then gave the correct location in the command. The output of the command was that I could not delete the file. 

I don't have something right because the site now says Adobe Shockwave Player is now installing, however nothing seems to be occuring.

---

### Post by frankleeee on 2008-11-18
> **acreech said:**
> I was doing good with installing the windows firefox and the macromedia shockwave, until I reached this step..... 



the first problem is that the file is in a different location. I found that file though then gave the correct location in the command. The output of the command was that I could not delete the file. 

I don't have something right because the site now says Adobe Shockwave Player is now installing, however nothing seems to be occuring.

I have shockwave without wine I think it is in the gstreamer ffmpeg in add remove, but here is a link to a Linux version.
[http://www.brothersoft.com/downloads/shockwave-player-linux.html](http://www.brothersoft.com/downloads/shockwave-player-linux.html)

---

### Post by frankleeee on 2008-11-18
This is the Shockwave deb from Adobe choose from the dropdown.
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by ubuntu27 on 2008-11-18
> **acreech said:**
> I was doing good with installing the windows firefox and the macromedia shockwave, until I reached this step..... 



the first problem is that the file is in a different location. I found that file though then gave the correct location in the command. The output of the command was that[B] I could not delete the file. 
[/B]
I don't have something right because the site now says Adobe Shockwave Player is now installing, however nothing seems to be occuring.

use sudo before the command

like this:

```
sudo rm ~/.mozilla/firefox/pluginreg.dat
```


Also try to leave it alone, don't move the plugin.dat or pluginreg.dat 
Let's see if it works that way.
It is important to experiment until you are successful.

I don't think that page (Install Shockwave in Linux) has been updated, so there might be things that is no longer true for the current Ubuntu.

When you install shockwave successfully, tell us here how you did it, so someone can update that site. Or you can also update it yourself.

> **frankleeee said:**
> This is the Shockwave deb from Adobe choose from the dropdown.
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Sorry Frank, Shockwave is NOT the same as Flash.

Shockwave has NEVER been released for Linux.

---

### Post by frankleeee on 2008-11-18
> **ubuntu27 said:**
> use sudo before the command

like this:

```
sudo rm ~/.mozilla/firefox/pluginreg.dat
```


Also try to leave it alone, don't move the plugin.dat or pluginreg.dat 
Let's see if it works that way.
It is important to experiment until you are successful.

I don't think that page (Install Shockwave in Linux) has been updated, so there might be things that is no longer true for the current Ubuntu.

When you install shockwave successfully, tell us here how you did it, so someone can update that site. Or you can also update it yourself.



Sorry Frank, Shockwave is NOT the same as Flash.

Shockwave has NEVER been released for Linux.

Then how do I have it installed without wine or crossover.

---

### Post by ubuntu27 on 2008-11-18
> **frankleeee said:**
> Then how do I have it installed without wine or crossover.

I do not know. But, if you could post how did you install Shockwave, everyone will benefit.

What I do know is that Flash Player is not the same as Shockwave Player, and that you provided the link for Flash Player

Flash Player: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Shockwaave Player: [http://get.adobe.com/shockwave/](http://get.adobe.com/shockwave/)

---

### Post by frankleeee on 2008-11-18
> **ubuntu27 said:**
> I do not know. But, if you could post how did you install Shockwave, everyone will benefit.

What I do know is that Flash Player is not the same as Shockwave Player, and that you provided the link for Flash Player

Flash Player: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Shockwaave Player: [http://get.adobe.com/shockwave/](http://get.adobe.com/shockwave/)

I don't remember how I installed shockwave, since I am just a average user when I install or upgrade I just go to add remove and add all the gstreamer stuff, the restricted extras, vlc. When I search in add remove with shockwave it brings up the gstreamer ffmpeg set. I think that somewhere in this mess of codecs is the shockwave player. I am trying to figure it out, I do like to help others.

---

### Post by frankleeee on 2008-11-18
So I think what I have installed is actually swfdec from synaptic, here is a screen shots of my plugins. Also I believe you have to go into FF preference application and double click on the Shockwave and have it read use Shockwave flash in FF.

[ATTACH]93233[/ATTACH]

I don't know but this link may help.
[http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/playing-online-radio-and-other-media-content-includes-youtube-shockwave.-667873/](http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/playing-online-radio-and-other-media-content-includes-youtube-shockwave.-667873/)

---

### Post by frankleeee on 2008-11-18
> **frankleeee said:**
> So I think what I have installed is actually swfdec from synaptic, here is a screen shots of my plugins. Also I believe you have to go into FF preference application and double click on the Shockwave and have it read use Shockwave flash in FF.

[ATTACH]93233[/ATTACH]

I don't know but this link may help.
[http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/playing-online-radio-and-other-media-content-includes-youtube-shockwave.-667873/](http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/playing-online-radio-and-other-media-content-includes-youtube-shockwave.-667873/)

So here is a snapshot of synaptic.
[ATTACH]93234[/ATTACH]

I hope this is helpful. ;)

---

### Post by Zantaskan on 2008-11-18
I _almost_got the shockwave player to work under wine. I installed Firefox for Windows version under wine, then through Win Firefox i installed the shockwave plugin. It seemed to install fine, but when I go back to teh page with shockwave, the shockwave logo comes up and says" Shockwave is installing" Although the page is loaded already it seems, and the message does not go away.  Any ideas how to fix this last step?

---

### Post by cosmoshell on 2008-11-18
> **ubuntu27 said:**
> I do not know. But, if you could post how did you install Shockwave, everyone will benefit.

What I do know is that Flash Player is not the same as Shockwave Player, and that you provided the link for Flash Player

Flash Player: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Shockwaave Player: [http://get.adobe.com/shockwave/](http://get.adobe.com/shockwave/)

ive got shockwave too

dont know how thought

---

### Post by cosmoshell on 2008-11-18
> **frankleeee said:**
> So here is a snapshot of synaptic.
[ATTACH]93234[/ATTACH]

I hope this is helpful. ;)

ive got it but none of those are installed

---

### Post by ubuntu27 on 2008-11-19
> **cosmoshell said:**
> ive got it but none of those are installed

Maybe you got [Gnash]("http://www.gnu.org/software/gnash/") installed?

> **frankleeee said:**
> So here is a snapshot of synaptic.
[ATTACH]93234[/ATTACH]

I hope this is helpful. ;)


Anything is helpful :)


So maybe [Gnash]("http://www.gnu.org/software/gnash/") and [SWFdec]("http://swfdec.freedesktop.org/wiki/") provides showckwave and flash support unlike Adobe's flash player.

I am using Adobe's Flash Player so I don't know.

I will try them out.

**EDIT**:  Ok, I just tried both Gnash (version 0.8.4) and Swfdec (version 0.8.0) Both doesn't provide shockwae support. I visited online games that are made with shockwave, and they don't work.

As a side note, gnash and swfdec works well on many flash sites. 
Unfortunately, in some video sites, gnash doesn't display the control (the bar where you can move the video's running time, the pause and stop button). But it still works.

swfdec display videos on popular sites. In some sites, it doesn't display any video at all.

Ok, that's all for my little review.

*****************

All this means that we still have to search on how to install shockwave without wine.
And [this guide]("https://help.ubuntu.com/community/Shockwave") needs to be updated for the current version of Ubuntu.

[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

---

### Post by frankleeee on 2008-11-19
> **ubuntu27 said:**
> Maybe you got [Gnash]("http://www.gnu.org/software/gnash/") installed?




Anything is helpful :)


So maybe [Gnash]("http://www.gnu.org/software/gnash/") and [SWFdec]("http://swfdec.freedesktop.org/wiki/") provides showckwave and flash support unlike Adobe's flash player.

I am using Adobe's Flash Player so I don't know.

I will try them out.

**EDIT**:  Ok, I just tried both Gnash (version 0.8.4) and Swfdec (version 0.8.0) Both doesn't provide shockwae support. I visited online games that are made with shockwave, and they don't work.

As a side note, gnash and swfdec works well on many flash sites. 
Unfortunately, in some video sites, gnash doesn't display the control (the bar where you can move the video's running time, the pause and stop button). But it still works.

swfdec display videos on popular sites. In some sites, it doesn't display any video at all.

Ok, that's all for my little review.

*****************

All this means that we still have to search on how to install shockwave without wine.
And [this guide]("https://help.ubuntu.com/community/Shockwave") needs to be updated for the current version of Ubuntu.

[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

Even though I have the swfdec installed FF is set to read with the Shockwave plugins, I went to the lego site and joined and was able to play a game. I think Shockwave is in the 3rd party downloads in add remove this only makes sense to me in that I only use gdebi to install and auto installs with targz downloads I am not much of a terminal user.

---

### Post by acreech on 2008-11-19
I have to be close on it. I can now play a few games on that site. the Junkbot game still does not load. This is an  improvement. I installed gnash, swfdec and ffmpeg. 

I still have not got the game to play on the windows firefox through wine. I will have time to work on this project again this weekend. 

Thanks for the help.

---

### Post by gandaran on 2008-11-19
> **acreech said:**
> I have to be close on it. I can now play a few games on that site. the Junkbot game still does not load. This is an  improvement. I installed gnash, swfdec and ffmpeg. 

I still have not got the game to play on the windows firefox through wine. I will have time to work on this project again this weekend. 

Thanks for the help.
the reason the Junkbot game doesn't load is probably due to an activex issue, don't forget in windows theres a shockwave activex plugin only for internet explorer
activex is a microsoft windows thing, will never work in linux
it has nothing to do with shockwave, shockwave flash and flash videos work fine in linux with any flash package installed be it adobe flash, gnash or swfdec

---

### Post by starcannon on 2008-11-19
If its an activeX issue, the easiest fix is to run windows in a VirtualBox if its a mission critical situation (when your 7 it probably is lol), or find him some other games that don't require activeX (I know not much of a compromise, but its the problem with websites that assume that all s is p). 

GL and hope it works out well for you and your son.

---

### Post by frankleeee on 2008-11-19
> **acreech said:**
> I have to be close on it. I can now play a few games on that site. the Junkbot game still does not load. This is an  improvement. I installed gnash, swfdec and ffmpeg. 

I still have not got the game to play on the windows firefox through wine. I will have time to work on this project again this weekend. 

Thanks for the help.

I am unable to get junkbot to run either, so the virtual set up may be the answer, although I personally have never been able to figure out what that actually is, I have never used MS so I don't need it. 

What does your plugin list look like in the FF add-ons area is shockwave in there now? I tried to remove some codecs like the ffmpeg top see if it would disappear in mine but the computer wouldn't remove without removing other stuff like gnome. I have  2 desktops installed, ubuntu stock and Xubuntu, and every gstreamer installed that is in add remove, probably overkill but I never run into any media that doesn't run except for the junkbot.

---

### Post by acreech on 2008-11-20
> **starcannon said:**
> If its an activeX issue, the easiest fix is to run windows in a VirtualBox if its a mission critical situation (when your 7 it probably is lol), or find him some other games that don't require activeX (I know not much of a compromise, but its the problem with websites that assume that all s is p). 

GL and hope it works out well for you and your son.

thanks for the info. it has no bearing on whether I like or dislike Linux. to my son it may matter, but he will get over it. :) I have been helping him learn the begining steps of the language C, so hopefully his interests will change. 

Thanks for all the help.

---

### Post by frankleeee on 2008-11-20
This thread explains the shockwave inclusion in the link I posted from Adobe.
[http://ubuntuforums.org/showthread.php?t=987616](http://ubuntuforums.org/showthread.php?t=987616)
It says flash but it is more.

---

### Post by acreech on 2009-11-03
I was able to get this to work by installing virtualbox and then installing Windows XP into the Virtualbox program. Once I downloaded the service pack 2 and installed the plugins, it worked. This is the best solution that I have come up with for the problem.

---

