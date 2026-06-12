---
title: "Blue faces in youtube"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by CmdGabriel on 2012-09-01
Hi,

after changing to 12.04 the colors in youtube are all wrong. faces are blue...

but computergames and and pics are all right colored.

can you help?

thx
gabriel

---

### Post by anewguy on 2012-09-01
I'd do a search in these forums, and also a net search using:

ubuntu youtube blue faces

and see what it returned.  I know I've seen many, many entries on this already so you might be better off searching for one of those where everything is already explained and any solution is posted.

---

### Post by Autodave on 2012-09-01
> **CmdGabriel said:**
> Hi,

after changing to 12.04 the colors in youtube are all wrong. faces are blue...

but computergames and and pics are all right colored.

can you help?

thx
gabriel

Especially if you have an Nvidia card: right click on the video and uncheck the box for HARDWARE ACCELERATION.

If by chance it won't let you, maximize the screen and then do it.  Restart Firefox

---

### Post by CmdGabriel on 2012-09-02
> **anewguy said:**
> I'd do a search in these forums, and also a net search using:

ubuntu youtube blue faces

and see what it returned.  I know I've seen many, many entries on this already so you might be better off searching for one of those where everything is already explained and any solution is posted.

I did a search .. and now again. My thread is the only one on ubuntu blue faces.

---

### Post by anewguy on 2012-09-02
Just put:

youtube blue

in the search box on the upper part of the page.  There are many, many returns.  Just because the title doesn't say it you still need to read them.

[This]("http://ubuntuforums.org/showthread.php?t=2015589&highlight=youtube+blue") is just a sample.

Everything is there if you look.

---

### Post by kurt18947 on 2012-09-02
> **Autodave said:**
> Especially if you have an Nvidia card: right click on the video and uncheck the box for HARDWARE ACCELERATION.

If by chance it won't let you, maximize the screen and then do it.  Restart Firefox

This is the simplest fix if you won't miss hardware acceleration in other flash stuff.

---

### Post by Bodsda on 2012-09-02
> **CmdGabriel said:**
> Hi,

after changing to 12.04 the colors in youtube are all wrong. faces are blue...

but computergames and and pics are all right colored.

can you help?

thx
gabriel

I remember a similar problem cropping up a few releases ago. Jump into Movie Player (terminal: 'totem') Load something up, if you get the same colour issues go to 'Edit' > 'Preferences' > 'Display'   and adjust the 'Colour Balance' sliders.

HTH,
Bodsda

---

### Post by dodo3773 on 2012-09-02
Assuming you use nvidia since you never actually stated that yet. This is a libvdpau + flash issue. You can either patch libvdpau or remove it.

---

### Post by pqwoerituytrueiwoq on 2012-09-02
right click flash -> settings 
un-check enable hardware acceleration
hit ok and reload the page

---

### Post by anewguy on 2012-09-02
And all of that has been mentioned and is also in the thread I pointed to.

---

### Post by JRV on 2012-09-02
> **pqwoerituytrueiwoq said:**
> right click flash -> settings 
un-check enable hardware acceleration
hit ok and reload the page

Where is flash -> settings?

---

### Post by fooman on 2012-09-02
> **JRV said:**
> Where is flash -> settings?

*start a flash video* > right-click somewhere in the video > choose "settings"

uncheck enable hardware acceleration.  as was mentioned already....you will probably have to go fullscreen first in order to do it.  refresh the page or restart firefox and all should be fixed (for now)

---

### Post by mooz123 on 2012-09-13
I tried all of the above without solving the problem. Finally this solved it:

> add a file /etc/adobe/mms.cfg

with content

EnableLinuxHWVideoDecode = 1

(Found it here: [http://fabionotes.blogspot.se/2012/04/blue-faces-in-youtube-ubuntu.html](http://fabionotes.blogspot.se/2012/04/blue-faces-in-youtube-ubuntu.html))

I had to create an adobe folder, and restarted the machine. I hope this will help someone too.
Mark

PS I don't know if it's better than disabling hardware acceleration, and what else this setting does.

---

### Post by NikTh on 2012-09-13
> **mooz123 said:**
> I tried all of the above without solving the problem. Finally this solved it:



(Found it here: [http://fabionotes.blogspot.se/2012/04/blue-faces-in-youtube-ubuntu.html](http://fabionotes.blogspot.se/2012/04/blue-faces-in-youtube-ubuntu.html))

I had to create an adobe folder, and restarted the machine. I hope this will help someone too.
Mark

PS I don't know if it's better than disabling hardware acceleration, and what else this setting does.

Hi ,
this probably will work OR crash the Flash player. Is not for sure. 

[s]The problem is NOT related with Flash Player .[/s]
[s]The problem caused by NVIDIA's crappy code.[/s]
[s]When flash player calls the libvdpau library then the bug of "blue faces" appears.[/s] 
[s]Although this problem is old , Nvidia seems incapable to provide a fix.[/s] 

If this problem is related only with youtube , you can use html5 instead of flash player. 

[http://youtube/html5](http://youtube/html5) and click "Join the html5 trial" .

Thanks

---

### Post by pqwoerituytrueiwoq on 2012-09-13
it is a flash bug
right click flash clock setting uncheck hardware acceleration
there is another workaround
[Flash 11.2+Nvidia GPU+Youtube=Inverted red/blue - nV News Forums]("http://www.nvnews.net/vbulletin/showthread.php?p=2536788#post2536788")

enabling hardware acceleration in flash on nvidia is extremely unstable (and incompatable with flash drm)
```
~$ cat /etc/adobe/mms.cfg 
OverrideGPUValidation=false
EnableLinuxHWVideoDecode=0
```
that is to disable hardware acceleration, still have to do the checkbox

---

### Post by dodo3773 on 2012-09-13
> **NikTh said:**
> Hi ,
this probably will work OR crash the Flash player. Is not for sure. 

The problem is NOT related with Flash Player .
The problem caused by NVIDIA's crappy code.
When flash player calls the libvdpau library then the bug of "blue faces" appears. 
Although this problem is old , Nvidia seems incapable to provide a fix. 


That seems like an unfair assumption. They are both to blame it seems to me. Although, the biggest blame of all goes to us for being big enough suckers to still use proprietary software. But in the end you are right (libvdpau + flash issue). I for one am glad that flash is no longer supporting GNU/Linux. Hopefully the community will come together and we will wind up with  something better than that piece of junk player as an end result.

---

### Post by NikTh on 2012-09-14
Hi ,

I apologize. 

Probably I carried away too, from the rumors that Adobe spreads on Web. 

[SIZE=3]**Here is a good explanation and a possibly solution: **[/SIZE]http://askubuntu.com/questions/117127/flash-video-appears-blue


Thanks

---

### Post by mooz123 on 2012-09-28
I have to report back on the solution I tried, flash gets really buggy, keeps crashing. I will try one of the other suggested workarounds now.

---

### Post by LuckyDingo on 2012-10-08
> **Autodave said:**
> Especially if you have an Nvidia card: right click on the video and uncheck the box for HARDWARE ACCELERATION.

If by chance it won't let you, maximize the screen and then do it.  Restart Firefox


Hey,
Just wanted to say thanks - this worked perfectly for mine. I certainly didn't expect it to be that easy! Cheers!

---

### Post by legrandmawak on 2012-11-04
add a file /etc/adobe/mms.cfg

 with content

 EnableLinuxHWVideoDecode = 1

definetly made the trick : thanks a million 

:guitar:

---

### Post by monkeybrain2012 on 2012-11-04
> **legrandmawak said:**
> add a file /etc/adobe/mms.cfg

 with content

 EnableLinuxHWVideoDecode = 1

definetly made the trick : thanks a million 

:guitar:

That work around used to have the side effect that flash crashes on almost all other sites than Youtube. I haven't tested it with 12.04 but keep that in mind. A work around that used to work would be to disable hw acceleration BOTH in /etc/adobe/mms.cfg (setting EnableLinuxHWVideoDecode = 0) AND flash settings by right clicking any flash video as fooman says but there is a Unity bug that the flash settings menu is not clickable, so you would have to log into Unity 2d or gnome to do it (if you have gnome installed), not sure if that is fixed in 12.10.

There is a Nvidia patch that addresses this problem and it can be installed from ppa 
[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)
However I don't know if it works for all Nvidia driver versions and whether it has other side effects.

My suggestion is not to use flash for Youtube at all. Checkout the greasemonkey script Viewtube. It performs much better than flash anyway and you get hardware acceleration if you use mplayer as your backend. [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

---

### Post by Paari on 2012-11-05
> **CmdGabriel said:**
> 

after changing to 12.04 the colors in youtube are all wrong. faces are blue...

but computergames and and pics are all right colored.



Where you watching AVATAR !!!!!
sorry in case the timing was inappropriate... :lolflag:

---

