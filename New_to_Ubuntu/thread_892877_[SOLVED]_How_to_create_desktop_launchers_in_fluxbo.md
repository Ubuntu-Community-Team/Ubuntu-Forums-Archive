---
title: "[SOLVED] How to create desktop launchers in fluxbox using idesk?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by bhadotia on 2008-08-17
The title says it all.
I had recently come across fluxbox and am starting to like it. Configuring it was (still is) a hell of a work. But after (almost)everything done, my system flies like anything  and the window manager now is no less in functionality or eye candy than GNOME.
The thing (I think the only one) that I haven't been able to figure out is how to create the desktop icons in fluxbox. The documentation just says that you can draw the desktop icons using the package  'idesk' but does not detail on how to do it. I have downloaded a tar.gz file of icons from the documentation website , but have no idea what to do now as google search is also not helping much (same for the thread search on the forums).
I have extracted the tar file I downloaded to the ~/.fluxbox/pixmaps directory.

So can someone with fluxbox experience please help me.
Many thanks in advance.

---

### Post by snowpine on 2008-08-17
If you use Rox-Filer, you can add the following to your ~/.fluxbox/startup to get desktop icons:

```
rox --pinboard=MyPinboard &
```

Then, you can just drag applications or documents onto the desktop to create icons. That's how Fluxbuntu does it anyway. There may be other methods, I'm not sure.

---

### Post by bhadotia on 2008-08-17
Hi, thanks for the reply.
Well I don't use rox and also don't intend to use (tried it and did not like it). I tried drag-drop before also (again, this time) but it did not work. 

 Any other suggestions, please.

---

### Post by bhadotia on 2008-08-18
bump! 

I am having some more problems with fluxbox. When I start my computer and log into fluxbox I don't see the screenlets which I have added to the ~/.fluxbox/startup file (i.e., they don't start). But, if I exit fluxbox (log out) and start it again (log back in with the fluxbox session) all my screenlets startup automatically.

So far my progress in research on idesk is this:
I found a file /usr/share/idesk/dot.xsessions , whose content was :
```
#
# sample .xsession file
#

# start idesk (we need the sleep because fluxbox will overpaint the
# idesk with the rootCommand
(sleep 2; idesk &) &

# start fluxbox
exec fluxbox
exit $?
```

Till the time I had come acroos this file I was unable even to start my screenlets automatically at login. But this file gave me the idea that fluxbox could be "overpainting" (thats the word used in the above file- don't know what it means) the screenlets. So in the ~/.fluxbox/startup file which had commands for starting screenlets such as these:
```
python -u /usr/share/screenlets/Sysmonitor/SysmonitorScreenlet.py &
```
I changed them to ones that looked like this:
```
(sleep 4; python -u /usr/share/screenlets/Sysmonitor/SysmonitorScreenlet.py &) &
```

So that now I am at-least able to start screenlets automatically at the startup after (re)login.
In the same way, I changed the command to launch idesk at startup from 
```
idesk &
```
to
```
(sleep 3; idesk &)&
```.
Also, I found that my ~/.ideskrc file was not executable so I ,made it executable.
Plus, there were no icons which I had defined in the ~/.idesktoprc/ folder so I defined some test icons home.lnk & Documents.lnk in that folder:
```
table Icon
  Caption: Home
  CaptionTip: This is my home
  Command[1]: thunar /home/abhishek
  Icon: /home/abhishek/.idesktop/l33t_DES_gentoo-home.png
  Width: 48
  Height: 48
  X: 10
  Y: 30
end
```
```
table Icon
  Caption: Documents
  CaptionTip: This are my documents
  Command[1]: thunar /data/Documents
  Icon: /home/abhishek/.idesktop/l33t_CLR_penguin.png
  Width: 48
  Height: 48
  X: 600
  Y: 100
end
```
Also the icons file I downloaded (about which I spoke in a previous post in this thread) that I  had downloaded, I extrcated it to the ~/.idesktop/ folder. The above icon came with that file.

So can someone please point out where I am going wrong.

---

### Post by ellgor on 2008-08-19
Hi,

I have fluxbox and there is a known issue with versions earlier than 1.0.0 that any adjustments made during a session were lost on restart/reboot, upgrade if you are able.
As far as the idesk and icons, there is a tutorial which I think is at the idesk site if not the Fluxbox home site (maybe the Wiki) has one, I know, I read it, thought it would be quite easy but never did it, lets know how you get on.

Regards, Ellgor.

---

### Post by bhadotia on 2008-09-07
I have found many tutorials regarding fluxbox and I will go through them now.
I will mark the thread as solved now as no replies are coming.
I am giving below the list of resources:
[http://fluxbox.sourceforge.net/docs/en/newdoc.starting.php](http://fluxbox.sourceforge.net/docs/en/newdoc.starting.php)
[http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/](http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/)
These two guides further point to many other resources.

---

### Post by niceangelbaby on 2008-09-07
just been browsing and came across  [www.watchesshopping.net](http://www.watchesshopping.net) there prices seem to be way lower that standard. All of the watches seem to be priced around $200 to $300. Are they fakes? The site seems to look quite legit.

---

### Post by bhadotia on 2008-09-08
After reading all those tutorials I still have no luck with idesk.
Guess I'm destined not to be able to experience what these idesk icons look like:)

Well, so much much for fluxbox config.
Everything else is working just great in fluxbox. I, anyway don't use desktop icons- I lke my desktop clean; but I was just curious about how we can make desktop icons which we have configured from hand edited files- all I have ever done to create an icon somewhere is the usual drag and drop.

Well, thanks for the replies.

Abhishek

---

### Post by linuxlizard on 2008-09-08
couple of suggestions as a longtime fluxbox user

- for icons, I like to just use wbar. It looks really nice and is really simple to setup.

- Another nice little app is fbpanel. It gives you a taskbar, start menu, desktop switcher, clock, etc. It can even be configured to look like ubuntu's gnome panels.

Both of these are very low resource needs. I have both running on a 333 mhz computer running pcfluxboxos with 128 mb ram and it's still a snappy system- just can't play 3d games or watch youtube on it, but I use it for webdesign (bluefish, kompiz, gimp, open office all the time, and surfing the net (opera loads up and runs pretty fast on it).

---

### Post by bhadotia on 2008-09-08
Thanks for the suggestions.
I already have wbar, but now I will also try fbpanel.

---

