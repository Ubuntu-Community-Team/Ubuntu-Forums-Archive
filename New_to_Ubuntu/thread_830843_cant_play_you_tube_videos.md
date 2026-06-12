---
title: "cant play you tube videos"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by dexter.deepak on 2008-06-16
i had a dial-up modem, and was able to see as well as d/l the you tube videos through firefox, but now with a broadband connection, i cant even see the videos...the player applet just flashes and goes out.
is it something to do with my isp ?
i am using gnash for flash videos

in konquerer, it gives a crash message -"nspluginviewer crashed"

---

### Post by sharks on 2008-06-16
Just install flashplugin-nonfree plugin and then try. then if u have problem post here.

---

### Post by Tom--d on 2008-06-16
gnash cannot play the new youtube player.

If you install flashplugin-nonfree, you will experience broswer crashes when watching youtube video. this is due to lack of support from adobe on flash :(

---

### Post by sharks on 2008-06-16
I have also installed flashplugin-nonfree. i dont have a problem until now.

---

### Post by bumanie on 2008-06-16
Flash won't work on my 8.04 either. I have tried every 'fix' I've come across on this forum and none of them work.

---

### Post by aktiwers on 2008-06-16
If you are in Hardy you could also view Youtube through Movie Player.
Just go to enable the Youtube plugin and pick it instead of Playlist. I love this feature!

---

### Post by bumanie on 2008-06-16
> **aktiwers said:**
> If you are in Hardy you could also view Youtube through Movie Player.
Just go to enable the Youtube plugin and pick it instead of Playlist. I love this feature!

Thank you for that, although I am not an avid viewer of youtube, this is the first 'fix' that has actually worked. It's not quite a 'fix', but it is a decent work-around. Thanks again for the work-around.

---

### Post by wiebeest on 2008-06-16
> **aktiwers said:**
> If you are in Hardy you could also view Youtube through Movie Player.
Just go to enable the Youtube plugin and pick it instead of Playlist. I love this feature!
Dang! Didn't know this. Great tip, thanks, works awesome!

---

### Post by dexter.deepak on 2008-06-16
i installed flashplugin-nonfree but still it aint working...i am on ubuntu 7.10.
what to do ??

---

### Post by sharks on 2008-06-16
Which version of firefox r u using? just use the latest version.

---

### Post by aktiwers on 2008-06-16
Have you tried installing flash manually?
Download the tar.gz to your desktop from here:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash)

Extract it.

cd to it from terminal:
```
cd ~/Desktop/install_flash_player_9_linux/
```make it executable:
```
sudo chmod +x flashplayer-installer
```and run it:
```
sudo ./flashplayer-installer
```

---

### Post by dexter.deepak on 2008-06-16
thanks a lot !!
the manual installation worked.

---

### Post by dexter.deepak on 2008-06-16
one more help...
how to save the downloaded videos ??

---

### Post by aktiwers on 2008-06-16
Check out this link:
[http://www.arrakis.es/~rggi3/youtube-dl/](http://www.arrakis.es/~rggi3/youtube-dl/)

Though there are lots of website on the net that lets you copy/paste the URL of a video and then download. Search google for "youtube online downloader" or something..

There are also firefox extensions who does this:
[https://addons.mozilla.org/en-US/firefox/addon/3590](https://addons.mozilla.org/en-US/firefox/addon/3590)

---

### Post by stchman on 2008-06-16
> **Tom--d said:**
> gnash cannot play the new youtube player.

If you install flashplugin-nonfree, you will experience broswer crashes when watching youtube video. this is due to lack of support from adobe on flash :(

I have the flashplugin-nonfree installed on Hardy and FF3 runs YouTube with no crashes.

---

### Post by tstduke on 2008-07-23
I am using hardy Heron 8.04. I had similar problems with Mozilla 3 not playing You Tube videos. I installed the restricted packages and the non free packages and it still didnt work, I had to un-install Gnash through the synaptic package manager and then everything worked fine.

---

### Post by grtwhiterhyno on 2008-08-05
when installing the flash tar.gz, i get all the way to where it asks for the instalation path but i cant seem to get it right.  i keep getting error messages

lease enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox

WARNING: Please enter a valid installation path.

i have tried numerous path names, hopefully im just retarded and not typing it right and its not a critical failure.  please, in the name of everything that is holy, will someone help me??

---

### Post by gjoellee on 2008-08-05
.

---

### Post by grtwhiterhyno on 2008-08-05
Im a total noob, so could you tell me how to uninstall it?  and i went to adobe and i get offered 9.0.31.0 or whatever, where do i get 10?

---

### Post by SunnyRabbiera on 2008-08-05
> **grtwhiterhyno said:**
> Im a total noob, so could you tell me how to uninstall it?  and i went to adobe and i get offered 9.0.31.0 or whatever, where do i get 10?

well did you try the flash installer in the repositories?

---

### Post by aktiwers on 2008-08-05
[http://labs.adobe.com/technologies/flashplayer10/releasenotes.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes.html)

---

### Post by gjoellee on 2008-08-05
the post you see is written by me on page 2 is bugged or something....here is is again

download the tar.gz file from this page: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
extract the file and put it to your home folder

now go to your home folder and press CTRL+H and go to ".mozilla" and then into "plugins", if "libflashplayer.so" is there delete it...

now go to terminal and type
```
cd install*
```and then
```
./flashplayer-installer
``` and follow the instructions you get...

if the problem is still there reinstall firefox

---

### Post by richie42 on 2008-08-05
> **aktiwers said:**
> Have you tried installing flash manually?
Download the tar.gz to your desktop from here:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash)

Extract it.

cd to it from terminal:
```
cd ~/Desktop/install_flash_player_9_linux/
```

make it executable:
```
sudo chmod +x flashplayer-installer
```

and run it:
```
sudo ./flashplayer-installer
```

(I think this is the right way)

Okay: I am a n00b with Ubuntu.

What does CD and extract mean?

---

### Post by grtwhiterhyno on 2008-08-05
what about unistalling gnash? i dont see it in add/remove apps, but i know its on here somewhere, at least im pretty sure,

---

### Post by gjoellee on 2008-08-05
the CD command means something like select if I can say so
extract: I am not sure how to explain that...

---

### Post by gjoellee on 2008-08-05
> **grtwhiterhyno said:**
> what about unistalling gnash? i dont see it in add/remove apps, but i know its on here somewhere, at least im pretty sure,
you will find gnash if Add/Remove shows "All Available Applications"

---

### Post by aktiwers on 2008-08-05
> **richie42 said:**
> Okay: I am a n00b with Ubuntu.

What does CD and extract mean?

Extract => Right-click the file and pick "extract here"

CD is what I do in that command below my statement. It is the way you navigate to a folder through the terminal. (actually its the same on Windows)

---

### Post by grtwhiterhyno on 2008-08-05
arrrg! it will not let me put the folder in the home folder. i am the admin, a sorry one but still, infact im the only user on this computer

---

### Post by aktiwers on 2008-08-05
What error are you getting? and putting what in your home folder?

---

### Post by gjoellee on 2008-08-05
right click and click on cut" and then go to home folder and right click and click on paste
you can also drag the file and you can copy and paste it as well

---

### Post by richie42 on 2008-08-05
I went on youtube, went on flash, and it gae 3 options for Flash for linux, should I use .tar.gz, .rpm, or YUM?

I use version 8.04

---

### Post by grtwhiterhyno on 2008-08-05
nope, cant do any of those, tried several times

---

### Post by aktiwers on 2008-08-05
For manual install it is the tar.gz file you need..

---

### Post by grtwhiterhyno on 2008-08-05
error while moving, 
click on details and indicates i dont have permission! thats a buch of rubbish

---

### Post by richie42 on 2008-08-05
i got this whe I tried installing it It was good, but now what do I do?

```

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 

```

---

### Post by grtwhiterhyno on 2008-08-05
thats where i get stuck

---

### Post by Bucky Ball on 2008-08-05
Posted twice cos got error message first time and didn't think it went up. Refer next post ... :)

---

### Post by Bucky Ball on 2008-08-05
Are you meaning you can't get full screen or just can't watch video? If it is the former, then refer to this post of mine. I had the same problem and worked on it for a couple of months;

[http://ubuntuforums.org/showthread.php?t=878479](http://ubuntuforums.org/showthread.php?t=878479)

Good luck.

---

### Post by gandaran on 2008-08-05
> **richie42 said:**
> i got this whe I tried installing it It was good, but now what do I do?

```

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 

```

you can either choose home/user/.mozilla or /usr/lib/mozilla, if you want to install  to /usr/lib/mozilla you must run the installer as root, use sudo for that.

or you can just extract the tar package and drag the libflashplayer.so file to home/user/.mozilla/plugins or /usr/lib/mozilla/plugins, it's just that simple.

---

### Post by vivow on 2008-08-06
I hope I'm in the right thread with this here.

I also have a small issue with flash. I have no problems watching and using flash pages except for youtube. I see the player, the video loads and everything but it only will play 2secs max, without sound. the video then just stops. I can forward it and it starts playing again, but still only for about 2secs.

I'm using the adobe flash player on FF3. Tried reinstalling it, didnt fix it. I cant use other flash player since some pages wont work with them. Also deinstalled the libflashthingy.

I am aware of the movie player work around, but i wanna watch it with FF, not an external program.

thx in advance.

---

### Post by Paul86fxr on 2009-07-11
Un-installing gnash worked for me as well, I can play anything now

---

### Post by Dnyce2k6 on 2009-08-12
> **aktiwers said:**
> Have you tried installing flash manually?
Download the tar.gz to your desktop from here:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash)

Extract it.

cd to it from terminal:
```
cd ~/Desktop/install_flash_player_9_linux/
```make it executable:
```
sudo chmod +x flashplayer-installer
```and run it:
```
sudo ./flashplayer-installer
```

The link takes me to version 10 (instead of 9), so I figured all I had to do was download the tar of version 10 and then just do cd ~/Desktop/install_flash_player_10_linux/. However this doesn't work, it just says "No such file or directory". I also tried
 cd ~/Desktop/install_flash_player_9_linux.tar.gz, out of desperation. Also didn't work. Any suggestions? Please keep in mind Im very new to Ubuntu. Im also trying to get my Youtube/Gamespot/Ign/etc. videos to have sound.

---

### Post by Dnyce2k6 on 2009-08-12
I tried uninstalling every flash plug in and then reinstalling firefox. Upon installation I had no flash player, according to plan. Then I reinstalled flash player non free and the non free extras in synaptic. I still dont have sound in youtube or other flash video using sites.

---

### Post by krnk on 2009-08-13
can any one help me i have the same vid problems iam new to ubuntu i just installed it how do i install flashplugin-nonfree  plz help mee anyone:P

---

### Post by Bucky Ball on 2009-08-13
Open:

System->Administration->Synaptic Package Manager

Do a search for:

ubuntu-restricted-extras

Just copy/paste that into the search box as is. Mark it for installation and hit the 'Apply' icon.

Make sure Firefox is closed before you start. That should be it.

* Also, if you are using 9.04, when you go to a site and you don't have the right plug-ins you will normally be offered the option of downloading and installing them in a yellow bar below the toolbar.

---

### Post by andru183 on 2009-08-13
if your using 56k youtube is goina make you bald as you look at it, may wana get sumit a lill faster

---

### Post by Dnyce2k6 on 2009-08-13
I got mine working finally. :)

If you don't restart, apparently there will be no effect. What I did was go into Synaptic, search for flash, un-install every flash player plug in. Also, mark Mozilla for a reinstall. Once Mozilla is restarted, check youtube, it should say you have no flash player plugin. That means you uninstalled all the plugins (everything is going according to plan). Then install flashplugin-nonfree, and restart your computer. Once you restart flash videos should work. Thats what I did. I hope it works out for anyone having trouble, I understand how annoying this  **** can be, especially to a new Ubuntu user like myself.

---

### Post by Garyhans on 2009-08-13
If you install flash..  remove all instances of gnash..  only one flash prog.. can be installed..

---

