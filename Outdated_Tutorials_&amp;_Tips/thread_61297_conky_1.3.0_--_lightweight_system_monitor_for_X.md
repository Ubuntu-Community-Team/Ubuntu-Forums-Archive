---
title: "conky 1.3.0 -- lightweight system monitor for X"
date: 2005-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by jtan325 on 2005-08-31
Hi everyone. not sure if this is the right place to post this, and I am not going to spam or anything, but here goes.

I would like to recommend you check out a little program called conky, which is a lightweight, highly configurable system monitor for X. a descendent of the now-defunct torsmo. its main purpose is to be uninvading and consume *very little* resources, much much less than gdesklets and gkrellm.

of course, you want screenshots  \\:D/ , so find them under "screenshots" at **[http://conky.sf.net](http://conky.sf.net)** pretty documentation there too, as opposed to the rather long man page. 

Conky 1.3.0, released just yesterday is out and about. download at **[http://www.sf.net/projects/conky](http://www.sf.net/projects/conky) ** there's a debian package too now, made by yours truly :-) , and hopefully it'll appear in the ubuntu repos for breezy in a month or two. 

coincidentally, i'm a conky developer. ;-)  **if you need help, post here,** or join **#conky** on irc, or [http://forums.gentoo.org/viewtopic-t-351806-highlight-conky.html](http://forums.gentoo.org/viewtopic-t-351806-highlight-conky.html) (freakish 20+ pages though). 

post bugs/feature requests at [http://sourceforge.net/tracker/?group_id=143975](http://sourceforge.net/tracker/?group_id=143975)

---

### Post by joede on 2005-09-01
[QUOTE=jtan325]I would like to recommend you check out a little program called conky, which is a lightweight, highly configurable system monitor for X. a descendent of the now-defunct torsmo.[/QUOTE]

Thanx for the post. I've give it a try right after I found the posting at freshmeat.

It looks very nice and I think I'll use it. Nevertheless, there are some drawbacks (the same torsmo have...).

The old "flicker" problems still exists (with nautilus) if I set own_window to no. Any solutions on the roadmap?

If I turn on own_window, it is possible to click on the window to put it on top of all other windows. Is there a way to fix it as lowest window?


[QUOTE=jtan325]there's a debian package too now, made by yours truly :-) , and hopefully it'll appear in the ubuntu repos for breezy in a month or two.[/QUOTE]

There is no ./debian directory inside the source tarball. Why that?

---

### Post by Jason-X on 2005-09-01
This looks really cool. I'm going to try it out later :)

---

### Post by jtan325 on 2005-09-01
[QUOTE=joede]Thanx for the post. I've give it a try right after I found the posting at freshmeat.
It looks very nice and I think I'll use it. Nevertheless, there are some drawbacks (the same torsmo have...).
The old "flicker" problems still exists (with nautilus) if I set own_window to no. Any solutions on the roadmap?
If I turn on own_window, it is possible to click on the window to put it on top of all other windows. Is there a way to fix it as lowest window?
There is no ./debian directory inside the source tarball. Why that?[/QUOTE]

joede, try turning on the double_buffer option to eliminate the flickering. in your ~/.conkyrc file, there is a "double_buffer" line, change it from 'no' to 'yes'. 

as for the window priority, that's something your window manager should support using Extended Window Manager Hints... i use fvwm, i could tell you how to do it for fvwm if you use it...

as for the debian, i don't think you usually distribute debian/* with the source tarball, otherwise you're containing distribution-specific stuff. 

what i meant by debian package was that I've built a .deb package that makes the conky installation process much easier for debian/ubuntu users, found at [http://sourceforge.net/project/showfiles.php?group_id=143975](http://sourceforge.net/project/showfiles.php?group_id=143975) . 

download the one for your platform (intel = i386, amd64 = amd64, ppc = mac). this is similiar to using synaptic or apt-get, it's just that conky is not in the official internet ubuntu repositories (but soon will be, i'm working on that). 

once you've download the .deb, follow the instructions under the "debian/ubuntu" section of install notes on [http://conky.sf.net](http://conky.sf.net) . hopefully it works. 

let me know if you need more help, i'm also in #conky (or other devs are around to help).

---

### Post by A-star on 2005-09-01
Well I use as allignment "Top_left" but then the uppermost line of the window is under the upper gnome bar, which make the line on top unreadable.

Is there a way to avoid this?

If you need a screenshot, I'll post one this evening.

---

### Post by jtan325 on 2005-09-01
[QUOTE=A-star]Well I use as allignment "Top_left" but then the uppermost line of the window is under the upper gnome bar, which make the line on top unreadable.

Is there a way to avoid this?

If you need a screenshot, I'll post one this evening.[/QUOTE]

A-star, there are some different ways around this.

1) launch conky in its own window, either by passing -o to conky at command line, or changing the own_window setting in your .conkyrc to yes, and then you can move conky around to wherever you want. 

2) use the gap_y setting your .conkyrc , see [http://conky.sf.net/config_settings.html](http://conky.sf.net/config_settings.html) to put some space between your border and the text to be displayed... that may look kind of crude

3) don't use gnome panel :-) i assume you're using the default gnome window manager, metacity? there's plenty more wm's out there, and one is the right one for you.... hehe

let me know if this helps or if you still have problems.

---

### Post by jerome bettis on 2005-09-01
i just found out about this tonight.  i was using torsmo but this is better.

[screenshot](http://www.pitt.edu/~jwn7/screenshot.jpg)

i like it.  are there any new features in the new version i should check out?  i'd like to see a bunch of stuff for weather at some point.  i wrote a python script to get that, but it's really a hack.  let me know if you want it and i can post it.  i also wrote the wifi script.

and i've seen some people with xmms stuff on there.  can you control the player or does it just show what's playing?  if i could skip tracks with it i'd be all over it.

---

### Post by jtan325 on 2005-09-01
[QUOTE=jerome bettis]i just found out about this tonight.  i was using torsmo but this is better.

[screenshot](http://www.pitt.edu/~jwn7/screenshot.jpg)

i like it.  are there any new features in the new version i should check out?  i'd like to see a bunch of stuff for weather at some point.  i wrote a python script to get that, but it's really a hack.  let me know if you want it and i can post it.  i also wrote the wifi script.

and i've seen some people with xmms stuff on there.  can you control the player or does it just show what's playing?  if i could skip tracks with it i'd be all over it.[/QUOTE]

besides lots of bug fixes, here are some new features: [http://conky.sourceforge.net/changelog.html](http://conky.sourceforge.net/changelog.html)

weather stuff was removed because the library used for that stuff was waaaay too unstable and causing too many problems. we are open to suggestions/help for conky 2.x. 

the xmms stuff is actually mpd (music player daemon), which conky can interface with to some extent. unfortunately, it can't do actual control of the playing of tracks right now... definitely another thing to add for 2.x.

hehe is that really a screenshot of conky, or torsmo? it's the same link as the one you posted in that other thread about system monitors... or you're using conky with your torsmo config? that works too. 

sure, send those scripts over. we're hoping to start a user-driven library of scripts for conky. word has it that conky 2.x may have a plug-in system... but you didn' hear it here. shhhhhhhhhhhhh or else i'm gonna have to do the code for that :-)

email me screenshot link, .conkyrc, scripts to < jtan325 at gmail dot com > or post them here. have fun!

---

### Post by A-star on 2005-09-01
[QUOTE=jtan325]
2) use the gap_y setting your .conkyrc , see [http://conky.sf.net/config_settings.html](http://conky.sf.net/config_settings.html) to put some space between your border and the text to be displayed... that may look kind of crude
[/QUOTE]
This worked fine, thanks for the help

---

### Post by joede on 2005-09-01
[QUOTE=jtan325]joede, try turning on the double_buffer option to eliminate the flickering. in your ~/.conkyrc file, there is a "double_buffer" line, change it from 'no' to 'yes'. [/QUOTE]
Thanx, but I'm running into the "nautilus" problem. I now use "own_window=off" and must live with the window priority.

[QUOTE=jtan325]as for the window priority, that's something your window manager should support using Extended Window Manager Hints... i use fvwm, i could tell you how to do it for fvwm if you use it...[/QUOTE]
Ok, after a system crash I'm currently running ubuntu warty together with gnome and metacity. On my old PC, I've used Woody with WindowMaker, which is a much better WM (it can handle this hints). I know, I can use WindowMaker together with Gnome, but I plan to give GNUstep a try, after updating to Ubuntu Hoary (or Debian Testing).

[QUOTE=jtan325]as for the debian, i don't think you usually distribute debian/* with the source tarball, otherwise you're containing distribution-specific stuff.[/QUOTE]
That's right, but for which flavour of Debian do you build the package? For the most packages, I build my own "backport" to warty. ;-)

By the way, wouldn't it be a good idea to add the configuration files to the sample screenshots? I'm interrested in this one: [http://conky.sourceforge.net/conky-jc-thumb-2.png](http://conky.sourceforge.net/conky-jc-thumb-2.png)

---

### Post by jtan325 on 2005-09-01
> **joede]
That's right, but for which flavour of Debian do you build the package? For the most packages, I build my own "backport" to warty.  said:**
> http://conky.sourceforge.net/conky-jc-thumb-2.png[/url]

ah, sorry. this was my first debian package, and i still haven't understood or know about all the details. i think the answer to your question  the packages was built on ubuntu hoary systems... is that what you're looking for? 

 as for config files with screenshots, we already have them. just click on the "screenshots" link under "screenshots" on [http://conky.sf.net](http://conky.sf.net) and there are links next to each screenshot to their accompanying .conkyrc. enjoy!

---

### Post by joede on 2005-09-06
> i think the answer to your question the packages was built on ubuntu hoary systems...

Thats the reason why I have to compile my own package, I'm using the older warty. 


> as for config files with screenshots, we already have them. just click on the "screenshots" link

Thanx, I haven't visited this page before.

---

### Post by joede on 2005-09-06
I just looked into the samples. There are sereval ways to add some preformatted text like weather informations etc. The way used in most samples is, that a script is called and the output of the script is used. conky calls that script with a definable delay.

This means, that it tries to update the entries even if there is nothing new to display (like the call to cat!). Wouldn't it be a good solution to check the modification time of a textfile instead? I've installed a cron job to fetch my weather informations and push it into a "global" textfile (a temp file first, and thean i moved into the final location). Corky could recognize the changes by polling the mtime and update it's display.

I have had a look into the source, but I's to hard to find the right position to add this feature. You could use a new variable **mtime *filename*** to include the file if the mtime changes.

What do you think about this?

---

### Post by jtan325 on 2005-09-06
[QUOTE=joede]I just looked into the samples. There are sereval ways to add some preformatted text like weather informations etc. The way used in most samples is, that a script is called and the output of the script is used. conky calls that script with a definable delay.

This means, that it tries to update the entries even if there is nothing new to display (like the call to cat!). Wouldn't it be a good solution to check the modification time of a textfile instead? I've installed a cron job to fetch my weather informations and push it into a "global" textfile (a temp file first, and thean i moved into the final location). Corky could recognize the changes by polling the mtime and update it's display.

I have had a look into the source, but I's to hard to find the right position to add this feature. You could use a new variable **mtime *filename*** to include the file if the mtime changes.

What do you think about this?[/QUOTE]

excellent idea, and yes, the code is very very messy and hard to modify. that is precisely why we are doing a conky overhaul as we speak, completely rewriting in C++... conky 2.0 hopefully by Christmas, and I'll keep you all posted.

---

### Post by joede on 2005-09-07
Do you think this feature could be implemented in a 1.4 release?

> that is precisely why we are doing a conky overhaul as we speak, completely rewriting in C++
Please don't use C++. :wink: At least don't use the "bells and whistles" stuff offered by libraries / frameworks like STL or Boost or something else. **conky** is such a lean monitor. I think (no, I worry) that with C++, it could become a resource monster like gdesklet. :wink:

Have you started with coding?

---

### Post by Stormy Eyes on 2005-09-07
[QUOTE=jtan325]I would like to recommend you check out a little program called conky, which is a lightweight, highly configurable system monitor for X. a descendent of the now-defunct torsmo. its main purpose is to be uninvading and consume *very little* resources, much much less than gdesklets and gkrellm.[/QUOTE]

I installed the deb last night and fired it up. Good work so far; I just need to tinker with it to make it rock like ninja. Would it be possible to add top_center, bottom_center, left_center, and right_center to the alignment options?

---

### Post by Stormy Eyes on 2005-09-07
[QUOTE=joede]Do you think this feature could be implemented in a 1.4 release?


Please don't use C++. :wink: At least don't use the "bells and whistles" stuff offered by libraries / frameworks like STL or Boost or something else. **conky** is such a lean monitor. I think (no, I worry) that with C++, it could become a resource monster like gdesklet. :wink:[/QUOTE]

One of the reasons gdesklets is a monster is that it was implemented in Python. If you use the STL properly, there's no reason why a C++ app can't be tighter than a Republican's butt at a gay bar.

---

### Post by thecrimsonking on 2005-09-07
I am probably missing something, but I can't hide the conky tab from my taskbar in KDE.  Anybody know how?

thanks
theck

edit:
D'oh!!
I forgot about specific window settings in the KDE control panel.  
Sometimes the easiest solutions are right in front of you.

---

### Post by joede on 2005-09-08
[QUOTE=Stormy Eyes]One of the reasons gdesklets is a monster is that it was implemented in Python.[/QUOTE]

Have a look at adesklet. It's also implemented with python, but it doesn't make use of the gnome* stuff. IMO that's the reason why gdesklets is "heavier" than adesklets.

[QUOTE=Stormy Eyes]If you use the STL properly, there's no reason why a C++ app can't be tighter than a Republican's butt at a gay bar.[/QUOTE]

Are you really shure? I have **not** written explicit test applications, but that's my (subjective) experience. Do you know some "hard facts"? :wink:

---

### Post by Stormy Eyes on 2005-09-08
[QUOTE=joede]Are you really shure? I have **not** written explicit test applications, but that's my (subjective) experience. Do you know some "hard facts"? :wink:[/QUOTE]

Off the top of my head? No. It has been a while since I did anything with C++, but if I remember correctly, both the Blackbox and Openbox 3 window managers are implemented with C++, and neither of them are monsters.

---

### Post by joede on 2005-09-09
> It has been a while since I did anything with C++, but if I remember correctly, both the Blackbox and Openbox 3 window managers are implemented with C++, and neither of them are monsters.

ok. I do most of my GUI programming with the excellent [FLTK](http://www.fltk.org) . This is a C++ Framework wrapping X, Windoze and Mac. It is a very lean framework. But it doesn't use all the bells and whistles of C++. So all strings are char* instead of string classes. There are no pattern used. pure virtual methods are avoided. The same for persistent objects. This makes fltk less beautifull and OO like, but extremly lean.

This doesn't mean that C++ is a bad choose. FLTK does it's job.

I'm afraid that the usage of collection classes and some of the OO tricks blow up the memory consumption. This happens to C programms if we use Gnome / GDK libraries too. :wink:

---

### Post by jtan325 on 2005-09-10
[QUOTE=Stormy Eyes]I installed the deb last night and fired it up. Good work so far; I just need to tinker with it to make it rock like ninja. Would it be possible to add top_center, bottom_center, left_center, and right_center to the alignment options?[/QUOTE]

I think I understand the top_center and the bottom_center, and will bring it up to the other developers, but could you explain the left_center and right_center a little bit more? 

Also, it'd be nice if you could file a feature request, see "tracker" on [http://www.sf.net/projects/conky](http://www.sf.net/projects/conky) so I don't forget :-) 

Once you have your conky "rock like ninja", please, send me a screenshot and your ~/.conkyrc , and we'll post it onto our screenshots portion of our site! jtan325 at gmail dot com . Thanks for the feedback, and for trying conky!

---

### Post by jtan325 on 2005-09-10
[QUOTE=joede]Do you think this feature could be implemented in a 1.4 release?

Please don't use C++. :wink: At least don't use the "bells and whistles" stuff offered by libraries / frameworks like STL or Boost or something else. **conky** is such a lean monitor. I think (no, I worry) that with C++, it could become a resource monster like gdesklet. :wink:

Have you started with coding?[/QUOTE]

I hate to say this, but the Conky development team has decided that any more work on  the 1.x branch will primarily be bug fixes. Feature requests will be considered (and hopefully implemented) in Conky 2.0. Our C++ overhaul will take alot of time to get right, and we are going full throttle with that effort... we hope to get something out by christmas. 

Besides the C++ rewrite, which provides the oo-programming that naturally fits Conky's variables, Conky 2.0 will hopefully have a single dependency -- Cairo --, which provides suppport for multiple backends, svg, and makes rendering ten times easier/cooler than before... More to come later.

---

### Post by joede on 2005-09-11
[QUOTE=jtan325]I hate to say this, but the Conky development team has decided that any more work on  the 1.x branch will primarily be bug fixes.[/QUOTE]

Ok. So we have to wait 'til christmas. :wink:

[QUOTE=jtan325]Conky 2.0 will hopefully have a single dependency -- Cairo --, which provides suppport for multiple backends, svg, and makes rendering ten times easier/cooler than before...[/QUOTE]

Have you ever checked the memory consumption of a simple program using cairo to draw to the it's own (or the root) window? Can you post a comparison of conky 1 and the cairo program?

PS: do you know if it is possible to compile / backport CAIRO to older systems (Gnome 2.8,...)?

---

### Post by Stormy Eyes on 2005-09-11
[QUOTE=jtan325]I think I understand the top_center and the bottom_center, and will bring it up to the other developers, but could you explain the left_center and right_center a little bit more? 

Also, it'd be nice if you could file a feature request, see "tracker" on [http://www.sf.net/projects/conky](http://www.sf.net/projects/conky) so I don't forget :-) [/quote]

I filed a feature request with a more detailed explanation of what I had in mind at [SourceForge](http://sourceforge.net/tracker/?func=detail&atid=757311&aid=1287810&group_id=143975), as you requested.

[QUOTE=jtan325]Once you have your conky "rock like ninja", please, send me a screenshot and your ~/.conkyrc , and we'll post it onto our screenshots portion of our site! jtan325 at gmail dot com . Thanks for the feedback, and for trying conky![/QUOTE]

You sure you want it? All I have my conky doing is displaying CPU/RAM/SWAP usage with a bar and percentage, the uptime, and my MPD status. [Here's a screenshot](http://ubuntuforums.org/gallery/showimage.php?i=849&original=1&c=7). I just emailed you a cropped screenshot and my .conkyrc if you still want 'em.

---

### Post by skatedawe on 2005-09-12
Im having a lot of problems with this program :=

 First, i wanna set up the lm_sensors.

 I have ASUS-A8N-E motherboard, S939, Nforce 4, it seems that its not supported with lm_sensors. How can that be fixed ? I typed; sensors-detect. I did went threw it but i got a lot of problems;

 ```
Do you want to scan the ISA bus? (YES/no): y
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8705F / IT8712F / SiS 950'
  Trying address 0x0290... Success!
    (confidence 8, driver `it87')
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!
``` 

 And so on...

 So the temp is dead.

 Then i got theese text in the program at the bottom; 

 MPD: MPD not responding Uknown - Unknown from unknown at 0
 Warning: font redering for ".bdf.gz" already registred at priority 0
 Warning: font redering for ".pmf" already registred at priority 0
 Could not init font path element unix/:7100, removing from list!

 Thats the problems, hope anyone could plz help me. I don't know where / or how to start the config. If i can get in toutch with that i could maybe solve some problems with removing some code.

 I really wanna try this out. gkrellm is not good at all :/, or tell me some other nice monitor programs.

---

### Post by jtan325 on 2005-09-12
[QUOTE=skatedawe]Im having a lot of problems with this program :=

 First, i wanna set up the lm_sensors.

 I have ASUS-A8N-E motherboard, S939, Nforce 4, it seems that its not supported with lm_sensors. How can that be fixed ? I typed; sensors-detect. I did went threw it but i got a lot of problems;

 And so on...

 So the temp is dead.

 Then i got theese text in the program at the bottom; 

 MPD: MPD not responding Uknown - Unknown from unknown at 0
 Warning: font redering for ".bdf.gz" already registred at priority 0
 Warning: font redering for ".pmf" already registred at priority 0
 Could not init font path element unix/:7100, removing from list!

 Thats the problems, hope anyone could plz help me. I don't know where / or how to start the config. If i can get in toutch with that i could maybe solve some problems with removing some code.

 I really wanna try this out. gkrellm is not good at all :/, or tell me some other nice monitor programs.[/QUOTE]

I can't help with the lm-sensors stuff, as I have a laptop, and lm-sensors doesn't work on laptops :-( maybe someone else can help with that?

but to remove the MPD and warnings you see in conky, just delete the very last line in your ~/.conkyrc file (something with "tail" and Xorg), and remove any lines after TEXT that contain "MPD". 

if you don't already have a .conkyrc file in your home directory, follow steps 2-4 under the debian/ubuntu installation notes on [http://conky.sf.net](http://conky.sf.net) . there are other example .conkyrc's that you can learn from on [http://conky.sf.net/screenshots.html](http://conky.sf.net/screenshots.html) . 

hope this helps, let me know if you have other problems!

---

### Post by skatedawe on 2005-09-18
[QUOTE=jtan325]I can't help with the lm-sensors stuff, as I have a laptop, and lm-sensors doesn't work on laptops :-( maybe someone else can help with that?

but to remove the MPD and warnings you see in conky, just delete the very last line in your ~/.conkyrc file (something with "tail" and Xorg), and remove any lines after TEXT that contain "MPD". 

if you don't already have a .conkyrc file in your home directory, follow steps 2-4 under the debian/ubuntu installation notes on [http://conky.sf.net](http://conky.sf.net) . there are other example .conkyrc's that you can learn from on [http://conky.sf.net/screenshots.html](http://conky.sf.net/screenshots.html) . 

hope this helps, let me know if you have other problems![/QUOTE]

 I got it all work now, except from MPD. I was required to install the packade: sensords + alla the lm_sesords. Anyway, it work now.

 I will try to edit my config and try google for other nice configs. Maybe we could do a request for config, you do not have peaple working on .configs? That would be nice for next realeases, maybe a .rar pack full of conigs and screenshots :D.

 The only problem, or Im not sure if its a problem. But if i drag the mouse over the program the text dissapear for 2sec and then blink back. Is there anything i could do to solve this little problem ?

---

### Post by wrtpeeps on 2005-09-18
conky really is nifty. And the devs rock too! :D

---

### Post by skatedawe on 2005-09-18
You need a package called:

 mpd
 
 to get the music deamon thing work.

 1 more thing fixxed.

---

### Post by skatedawe on 2005-09-19
the gdm package didn't solve it :/

---

### Post by jtan325 on 2005-09-20
[QUOTE=skatedawe]the gdm package didn't solve it :/[/QUOTE]

what are you talking about? 

and if you want to look at some other sample configs, they're here: [http://conky.sf.net/screenshots.html](http://conky.sf.net/screenshots.html) . more will be coming soon

---

### Post by skatedawe on 2005-09-20
[QUOTE=jtan325]what are you talking about? 

and if you want to look at some other sample configs, they're here: [http://conky.sf.net/screenshots.html](http://conky.sf.net/screenshots.html) . more will be coming soon[/QUOTE]

 I installed a package called gdm, i thought that would solve my gdm error.

 My gdm can't load, what can i do?
 
 Im waiting for the configs, I "borrowed" 1 and edited it, now i got a pretty clean config.

---

### Post by Stormy Eyes on 2005-09-20
GDM's got nothing to do with Conky, skatedawe. You should ask in the desktop support section if you're having problems with the GNOME Display Mangler.

---

### Post by Stormy Eyes on 2005-09-20
Also, don't use the conky that's in the Breezy repositories. It's been built without XFT support.

---

### Post by Ainvar on 2005-09-24
First off cool app!!

Now I have installed the latest deb file from sourceforge these darn updates want to keep overwriting the file in breezy. I am not sure how to tell synaptics and apt-get to ignore what is in the repo since the lock and force options in synaptics dont do it.

Next thing is with the deb file from sourceforge xft works but I still get this error.

Conky: drawing to subwindow of root window (1228d62)
Conky: failed to set up double buffer
Conky: drawing to single buffer

Now I am running gnome with metacity (dont really know what other WM to run and I dont feel like trying to switch out a dozen to find one I *might* like atm.

My last question for now is how can I get conky to read both nic interfaces without having 2 diffrent config files since I am on a laptop (Dell i6000D).

Also awesome program again it lets me have some stats like I do on my win boxes that use coolmon 1.x (simple and to the point)

---

### Post by Az7 on 2005-10-18
was there an easy fix for the blinking / flashing problem?

i get this output after i used synaptic to get conky 1.3.1-1

```

Conky: Xft not enabled
Conky: drawing to subwindow of root window (100006b)
Conky: failed to set up double buffer
Conky: drawing to single buffer

```

thanks

---

### Post by majikstreet on 2005-10-18
I <3 conky!!!!

Conky gets a :KS :KS :KS :KS :KS

---

### Post by thecrimsonking on 2005-10-18
Has anybody got transparncy to work with breezy.  I grew dependent on this app in hoary, but i can't live without the transparency!

---

### Post by Gandalf on 2005-10-21
Hello there,
Do anyone know where xmmsctrl & xmmsbar commands are?, i tried apt-cache and apt-file plus google i found only (kde) karamba xmmsctrl/bar but the command line i didn't find them :(

---

### Post by renzokuken on 2005-10-24
i cant seem to find the conkyrc file

i installed conky from synaptic and it works fine i just need to move it and tweak a tad but cant find the config file anywhere

thanks

---

### Post by jtan325 on 2005-10-25
[QUOTE=renzokuken]i cant seem to find the conkyrc file

i installed conky from synaptic and it works fine i just need to move it and tweak a tad but cant find the config file anywhere

thanks[/QUOTE]

see ubuntu/debian instructions on [http://conky.sf.net](http://conky.sf.net) , the sample config file is at /usr/share/doc/conky/examples/conkyrc.sample.gz (gotta gunzip it first).

---

### Post by renzokuken on 2005-10-25
thanks......i just created my own in $HOME and it works fine

---

### Post by jtan325 on 2005-10-25
[QUOTE=thecrimsonking]Has anybody got transparncy to work with breezy.  I grew dependent on this app in hoary, but i can't live without the transparency![/QUOTE]

exactly what problems are you getting with transparency? conky has been known to have issues with the default gnome window manager (metacity), but i'm not sure if that's what you're talking about...

---

### Post by bl4ckm0r3 on 2005-10-30
[QUOTE=Ainvar]First off cool app!!
Next thing is with the deb file from sourceforge xft works but I still get this error.

Conky: drawing to subwindow of root window (1228d62)
Conky: failed to set up double buffer
Conky: drawing to single buffer

[/QUOTE]

you have to enable the double buffer module for xorg...

add 

Load "dbe"

to your xorg.conf

---

### Post by thecrimsonking on 2005-10-31
[QUOTE=jtan325]exactly what problems are you getting with transparency? conky has been known to have issues with the default gnome window manager (metacity), but i'm not sure if that's what you're talking about...[/QUOTE]

Well, first I use KDE.
Conky will only stay transparent if I do NOT use the -o option. (create own window)
I have worked around this by just telling conky where to appear on the screen.
But it would be nice if I could use -o so i could drag it around on my screen.

---

### Post by skatedawe on 2005-11-10
I got a problem after upgrade to breezy.

 I got this failing;

 main@ubuntu-main:~$ conky
 Conky: /home/main/.conkyrc: 1: no such configuration: '.'
 Conky: Xft not enabled
 Segmentfail

 Any ideas ? How to i enable xtf ?

---

### Post by benplaut on 2005-11-11
didn't want to revive an old thread, but since it's here, i'll say it... conky totally rocks :D 

[IMG]http://img492.imageshack.us/img492/5725/screenshot4gp.png[/IMG]
^^my config... yes, it's possible to overlap items :)

---

### Post by jtan325 on 2005-11-11
[QUOTE=benplaut]didn't want to revive an old thread, but since it's here, i'll say it... conky totally rocks :D [/QUOTE]

HAHA i remember asking you to try conky on #ubuntu :p

---

### Post by ranf on 2005-11-16
Just played a bit with my .conkyrc:
[[IMG]http://img491.imageshack.us/img491/8169/bildschirmfotoconky17hu.th.png[/IMG]](http://img491.imageshack.us/my.php?image=bildschirmfotoconky17hu.png)

---

### Post by majikstreet on 2005-11-16
my conky's in my latest screenshot: [http://majikstreet.org/screenshots/111205.png](http://majikstreet.org/screenshots/111205.png)

---

### Post by rockz on 2005-11-16
conky is very very cool but i have some problems... when i start it my icons on desktop is hide... ok i use conky -o ... but conky is go to the taskbar... how i hide conky to the taskbar? and if i hide it when i click in "show desktop" button the conky is minimize too?

sorry for my english.

---

### Post by mustang on 2005-11-16
[QUOTE=rockz]conky is very very cool but i have some problems... when i start it my icons on desktop is hide... ok i use conky -o ... but conky is go to the taskbar... how i hide conky to the taskbar? and if i hide it when i click in "show desktop" button the conky is minimize too?

sorry for my english.[/QUOTE]

I'm having the same exact problem. If you run conky without having draw in its own window, all the icons disappear everytime you drag your mouse into the conky section. 

If you have it draw in its own window, there's a little window in the window list (since it is its own window) and if you're like me, and you like to use to the show desktop button, all your windows including conky get minimized.

Has anyone found a workaround for this?

Besides those issues, this is fantastic program.

---

### Post by rockz on 2005-11-17
> my conky's in my latest screenshot: [http://majikstreet.org/screenshots/111205.png](http://majikstreet.org/screenshots/111205.png)


in he desktop he have icons and no conky in taskbar? how do you do that?

---

### Post by Bukran on 2005-11-17
[QUOTE=skatedawe]
I got a problem after upgrade to breezy.

 I got this failing;

 main@ubuntu-main:~$ conky
 Conky: /home/main/.conkyrc: 1: no such configuration: '.'
 Conky: Xft not enabled
 Segmentfail

 Any ideas ? How to i enable xtf ?[/QUOTE]

I've solved the problem with double-buffer thanks to this thread but I still get the same error as skatedawe 'Xft not enabled'. I also got the message: 'xft-config... no', when I typed './configure' before the installation of Conky 1.3.3.

I know that Xft has something to do with fonts but, as I am quite new with Linux, could anyone help with this? What is Xft? How do I install it?

Thanks!

---

### Post by majikstreet on 2005-11-17
[QUOTE=rockz]in he desktop he have icons and no conky in taskbar? how do you do that?[/QUOTE]
I use fluxbox... not gnome or anything.... and i don't use -o

---

### Post by limit223 on 2005-11-20
First: Thank you for this nice program! I found it a great project!
I played a lot with variables, integrated programs and I can say I love it!
Here is my conky


I installed the last version of it and found in man description a new variable implemented tcp_portmon. I tested inserting a line in my file as
${color lightgrey}${tcp_portmon 1 1024 rhost 0}

and the shown output on my desk was  just written line as
${tcp_portmon}

Is this variable integrated already in conky 1.3.4, or there are just some testing work ahead?

---

### Post by gbm31 on 2005-11-21
here's my conky... (hide it with devilspie)

[img]http://www.gbm31.de/files/conky.jpg[/img]


question: conky doesn't start (1.30 & above) if the variable apcitemp is used.

at least on my x24. previous versions do.

am i alone?

(btw: i'm monitoring the cpu-temp by showing /proc/acpi/temp...)

---

### Post by limit223 on 2005-11-21
Reinstalled conky 1.3.4 with ./configure --enable-portmon and disable ipv6 was another advice...Everything is fine, I've got all desired connection shown on my screen now!

---

### Post by wishyjr on 2005-11-24
hiya, ive been reading through this thread but cant seem to find anything that relates to my own problem..

conky runs fine however it seems to cut off parts of the 'window'. It appears in a corner of the screen (as it should) but for example if i start it say top_left the top of conky will be cut off only showing the bottom half and visa-versa if i run in from the bottom -it cuts the bottom half of the display. Is there something ive missed? ive been playing with the command parameters but to no avail.

thanks

---

### Post by iced-tux on 2005-11-24
Hi everyone,
though I read this thread, googled my a** off and searched the *extensive* thread at forums.gentoo.org, I couldn't figure out why my conky doesn't stop to flicker :(

I ```
aptitude install conky
``` 
this is my ~/.conkyrc:
```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft no

# Set conky on the bottom of all other applications
on_bottom yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=10

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 0.5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no


# Use pseudo transparency with own_window?
own_window_transparent no

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline yes

# Draw borders around text
draw_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename - $sysname $kernel on $machine
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color red}${cpugraph 0000ff 00ff00}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #0000ff}${downspeedgraph eth0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth0 32,150 0000ff ff0000}
${color lightgrey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

```

I have the the line
```
Load "dbe"
```
in my xorg.conf.

So now what is my F**** problem :(

thanx 
iced-tux

---

### Post by benplaut on 2005-11-24
[QUOTE=jtan325]HAHA i remember asking you to try conky on #ubuntu :p[/QUOTE]

...and then later on in #conky trying to figure out how the hell to use the thing :rolleyes:

---

### Post by iced-tux on 2005-11-27
For anyone who runs conky in a window:
Install devislpie *aptitude install devilspie*
put in your .devilspie.xml:
```

<devilspie>
<flurb name="Conky pinned and no taskbar">
    <matchers>
       <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="conky"/>
       </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
      <action name="DevilsPieActionLayer">
	<property name="above" value="FALSE"/>
      </action>
     </actions>
</flurb>
</devilspie>

```

This is the same as when you would like to install a transparent terminal to your desktop

---

### Post by mustang on 2005-11-28
[QUOTE=iced-tux]For anyone who runs conky in a window:
Install devislpie *aptitude install devilspie*
put in your .devilspie.xml:
```

<devilspie>
<flurb name="Conky pinned and no taskbar">
    <matchers>
       <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="conky"/>
       </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
      <action name="DevilsPieActionLayer">
	<property name="above" value="FALSE"/>
      </action>
     </actions>
</flurb>
</devilspie>

```

This is the same as when you would like to install a transparent terminal to your desktop[/QUOTE]

Hello iced-tux,

I run conky in window mode (because it flickers otherwise even with the load dbe in my xorg.conf). However, i use the show desktop button a lot and it hides conky as well. Is there anyway to fix this? I tried using devilspie but it still hides conky.

---

### Post by skatedawe on 2005-12-01
How do i get hdd_temp to work ? Can anyone type the right code. I've installed hddtemp package, and got it to work in the gnome bar. But i want it in conky of course. 

 Im not sure about the variable.

 How can this be solved ?

---

### Post by limit223 on 2005-12-03
[QUOTE=iced-tux]For anyone who runs conky in a window:
Install devislpie *aptitude install devilspie*
put in your .devilspie.xml:
```

<devilspie>
<flurb name="Conky pinned and no taskbar">
    <matchers>
       <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="conky"/>
       </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
      <action name="DevilsPieActionLayer">
	<property name="above" value="FALSE"/>
      </action>
     </actions>
</flurb>
</devilspie>

```

This is the same as when you would like to install a transparent terminal to your desktop[/QUOTE]

From version 0.13 devilspie has completly different customed configuration.
I compiled form source of 0.16 version and I made a file which I inserted in my ~/.devilspie directory named conky.ds like this:

```
(if (is (window_class) "conky") (begin undecorate skip_tasklist skip_pager))
```
and conky was gone from my taskbar.
More details to customize devil's pie you may find [here]("http://www.burtonini.com/blog/computers/devilspie")

---

### Post by benplaut on 2005-12-03
[QUOTE=limit223]From version 0.13 devilspie has completly different customed configuration.
I compiled form source of 0.16 version and I made a file which I inserted in my ~/.devilspie directory named conky.ds like this:

```
(if (is (window_class) "conky") (begin undecorate skip_tasklist skip_pager))
```
and conky was gone from my taskbar.
More details to customize devil's pie you may find [here]("http://www.burtonini.com/blog/computers/devilspie")[/QUOTE]

...and show desktop button doesn't hide it?

---

### Post by mustang on 2005-12-03
[QUOTE=benplaut]...and show desktop button doesn't hide it?[/QUOTE]

Benplaut,

I PMed that question to him and this is his response:

> If I use that desktop clearance my conky disapear completly from destop even after the next click of recover. If you are talking about taskbar ...after desktop recoverance...I get my conky in the bar but after first click it disappear from it.

So I'm taking that as a yes? The language is a little unclear.

---

### Post by majikstreet on 2005-12-03
new conky = hot.

---

### Post by limit223 on 2005-12-03
The main goal of devilspie is to hide a program from taskbar...
I'm not really sure what you are asking about that desktop button..you mean to  make conky visible in window or in taskbar?..
I do not use taskbar applet from kicker right now and I can't help you much...
Compile the new devil's pie and do what suggest above...and see the result.




[SIZE="1"]btw: i'm a she..[/SIZE]

---

### Post by mustang on 2005-12-03
[QUOTE=limit223]The main goal of devilspie is to hide a program from taskbar...
I'm not really sure what you are asking about that desktop button..you mean to  make conky visible in window or in taskbar?..
I do not use taskbar applet from kicker right now and I can't help you much...
Compile the new devil's pie and do what suggest above...and see the result.




[SIZE="1"]btw: i'm a she..[/SIZE][/QUOTE]

We're referring to the show desktop button. This button will minimize every window and show you your desktop. 

The problem is that when you do that, conky gets minimized too. Even if you run it with devilspie. We were wondering if the new version fixes that.

I just installed the 0.16 .deb of devilspie and followed limit223's instructions about the conky.ds but to no avail. It still hides the conky window. Would compiling from the source make a difference?

P.S. Sorry about the gender confusion ;)

---

### Post by limit223 on 2005-12-03
We were talking about 2 completly things.
I actually made an answer to ice-tux...how to hide conky from taskbar which doesn't have nothing to do with your question regarding run conky in different window :)...sorry about that..someone else might have a hint for you...

---

### Post by Baphijmm on 2005-12-06
Slight problem, and I'm not entirely sure from whence it is arising (very much newb here); I downloaded the file, extracted it, and got to the ./configure command, but it gives me this error:

> configure: error: something went wrong when checking for Xdbe (double buffer extension)

Any input on what I might do to help this along?

EDIT: Actually, I think I found my own way.  Thanks anyway.

---

### Post by marguz on 2005-12-06
Hello,
I complie 1.3.4 and I also tried the version 1.3.3-1 deb from the projects homepage. When I try to start either versin, as root or user I get this error:

Conky: can't open '/sys/bus/i2c/devices/0-0050/temp1_input': No such file or directory

The error message is correct in that that file indeed is not there. Has anyone seen this?

I'm using a Intel P4.

?

---

### Post by jtan325 on 2005-12-07
[QUOTE=marguz]Hello,
I complie 1.3.4 and I also tried the version 1.3.3-1 deb from the projects homepage. When I try to start either versin, as root or user I get this error:

Conky: can't open '/sys/bus/i2c/devices/0-0050/temp1_input': No such file or directory

The error message is correct in that that file indeed is not there. Has anyone seen this?

I'm using a Intel P4.

?[/QUOTE]

just delete any lines that contain "i2c" in your ~/.conkyrc configuration file. if you don't have one, see the instructions on the conky page (conky.sf.net) on how to copy it over from the install directory to ~

---

### Post by reet on 2005-12-11
Hi, I am using Conky 1.3.4 and am just loving it. There is only one problem I am having and it is that I cannot get it to start automatically when I log on. I have hit the "save session" button when I log off, but when I log back on I have to start Conky manually. What dod I have to do to get this to start automatically? I use XFCE.

---

### Post by benplaut on 2005-12-11
ok... we need to figure something out - what's the command-line  set of instructions for working with windows? if we could just create a shortcut to that command to "minimize all" instead of "show nautilus-desktop," and even have a custom icon, to boot ;)

---

### Post by jtan325 on 2005-12-11
[QUOTE=reet]Hi, I am using Conky 1.3.4 and am just loving it. There is only one problem I am having and it is that I cannot get it to start automatically when I log on. I have hit the "save session" button when I log off, but when I log back on I have to start Conky manually. What dod I have to do to get this to start automatically? I use XFCE.[/QUOTE]

not sure if this'll work (I use FVWM instead of XFCE), but I found this: 
[http://www.os-cillation.de/cgi-bin/yabb/YaBB.cgi?board=deb-help;action=display;num=1110846760]("http://www.os-cillation.de/cgi-bin/yabb/YaBB.cgi?board=deb-help;action=display;num=1110846760")

---

### Post by Nano on 2005-12-12
I've been using conky for a while and this is the config that matches what I need.
If anyone is interested I can provide the conf.

Cheers

---

### Post by reet on 2005-12-12
[QUOTE=reet]Hi, I am using Conky 1.3.4 and am just loving it. There is only one problem I am having and it is that I cannot get it to start automatically when I log on. I have hit the "save session" button when I log off, but when I log back on I have to start Conky manually. What dod I have to do to get this to start automatically? I use XFCE.[/QUOTE]
I have found out that conky is being started when I log on, it just isn't being displayed. How odd.

---

### Post by reet on 2005-12-12
> **jtan325]not sure if this'll work (I use FVWM instead of XFCE), but I found this: 
[URL="http://www.os-cillation.de/cgi-bin/yabb/YaBB.cgi?board=deb-help said:**
> http://www.os-cillation.de/cgi-bin/yabb/YaBB.cgi?board=deb-help;action=display;num=1110846760[/URL]
Thanks, that worked great!

---

### Post by astoltz on 2005-12-12
[QUOTE=gbm31]
question: conky doesn't start (1.30 & above) if the variable apcitemp is used.
at least on my x24. previous versions do.
am i alone?
(btw: i'm monitoring the cpu-temp by showing /proc/acpi/temp...)[/QUOTE]

Nope, me too.  I'm using the conky from the breezy repo's and it took me a while to figure out that it was acpitemp causing the problem.  My temperature shows up in /proc/acpi/thermal_zone/THRM/temperature - maybe that has something to do with it?

Quick question.  What should I put in the config to make it show the contents of a file?

---

### Post by dartakaum on 2005-12-14
Hy.
i'm running conky 1.3.4 and i'm having some problems.

first how to set a bar ou % of volume?
and i saw one user showing % of signal from WLAN, how to do that?

cheers.

---

### Post by dartakaum on 2005-12-14
and by the way, i can't get it to stay near the edge of my screen. :\

---

### Post by limit223 on 2005-12-14
I found people interested in my configuration file from Gallery section where I post my last screenshot..therefore I'm going to share it here. It took some time  to make use all conky variables correctly in the desire way. Meanwhile I change some ports so I reconfigure conky for them as well. 
 Conky's thread from Gentoo forum helped me a lot, actually.


I'll skip comment lines, you may find them easyly in any conkyrc sample from the source program.(hope I won't omit the real line by mistake)

```
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

use_xft yes

xftfont Bitstream Vera Sans Mono:size=9

own_window_transparent yes

xftalpha 0.8
on_bottom yes

mail_spool $MAIL

update_interval 1

own_window yes

double_buffer yes

draw_shades no

draw_outline no

draw_borders no

stippled_borders 0

border_margin 4

border_width 1

default_color white
default_shade_color white
default_outline_color white


alignment top_right
gap_x 10
gap_y 25


use_spacer no

no_buffers no

uppercase no

TEXT
$sysname $kernel    ${time %A,%d %B}
$stippled_hr
${color lightgrey}Time:$color ${time %k:%M:%S}
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}
${color #4F6B93}${cpugraph 25 8098ff ffc7ea}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% $membar
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
${offset 10}Down:${color #a9c7ea} ${downspeed eth1} k/s${color lightgrey} ${alignr}Up:${color #a9c7ea} ${upspeed eth1} k/s
${offset 10}${color #4F6B93}${downspeedgraph eth1 25,100 8098ff ffc7ea} ${alignr}${color #4F6B93}${upspeedgraph eth1 25,100 8098ff ffc7ea}
${offset 10}${color lightgrey}Total: ${color #a9c7ea}${totaldown eth1} ${alignr}${color lightgrey}Total: ${color #a9c7ea}${totalup eth1}
${color lightgrey}File systems:$alignr
/      $color${fs_used_perc /}%   ${fs_used /}/${fs_size /} ${fs_bar /}
/hdb11 $color${fs_used_perc /media/hdb11}%  ${fs_used /media/hdb11}/${fs_size /media/hdb11} ${fs_bar /media/hdb11}
/hdb9  $color${fs_used_perc /media/hdb9}%   ${fs_used /media/hdb9}/${fs_size /media/hdb9} ${fs_bar /media/hdb9}
/hdb8  $color${fs_used_perc /media/hdb8}%   ${fs_used /media/hdb8}/${fs_size /media/hdb8} ${fs_bar /media/hdb8}
/sda6  $color${fs_used_perc /media/sda6}%  ${fs_used /media/sda6}/${fs_size /media/sda6} ${fs_bar /media/sda6}

  ${color}Name            PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
  ${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${font Verdana:style=Bold:pixelsize=12}${color #9AB7FF} ${alignc}$mpd_artist - $mpd_title
${font Verdana:style=Bold:pixelsize=12}${color #9AB7FF} ${alignc}vol: $mpd_vol bitrate: $mpd_bitrate kbp length: $mpd_length $mpd_percent%  
${color #9AB7FF}$mpd_bar
${color #9AB7FF}${alignc}$mpd_status
${color lightgrey}${execi 1 ~/Documents/conky/get_calendar.sh first_part}${color #ddaa00}${execi 1 ~/Documents/conky/get_calendar.sh today }${color }${execi 1 ~/Documents/conky/get_calendar.sh second_part}

${color lightgrey}Port(s)${offset 48}Connections:
${color lightgrey} ALL: ${alignc}${tcp_portmon 1 65535 count}
${color lightgrey} mpd:${alignc}${tcp_portmon 6600 6600 count}
${color lightgrey} 1 - 1024:${alignc}${tcp_portmon 1 1024 count}
${color lightgrey} 1025 - 65535:${alignc}${tcp_portmon 1024 65535 count}
${color lightgrey}Remote Address:${alignr} Local Service/Port:
${color}${tcp_portmon 1 1024 rport 0} 
${color}${tcp_portmon 1 65535 rhost 0}${alignr}${tcp_portmon  1 65535 lservice 0}
${color}${tcp_portmon 1 65535 rhost 1}${alignr}${tcp_portmon  1 65535 lservice 1}
${color}${tcp_portmon 1 65535 rhost 2}${alignr}${tcp_portmon  1 65535 lservice 2}
${color}${tcp_portmon 1 65535 rhost 3}${alignr}${tcp_portmon  1 65535 lservice 3}
${color}${tcp_portmon 1 65535 rhost 4}${alignr}${tcp_portmon  1 65535 lservice 4}
${color}${tcp_portmon 1 65535 rhost 5}${alignr}${tcp_portmon  1 65535 lservice 5}


```

You may remove /hdb* lines, containing mounted partion devices of my system and change them with yours given by fstab file (or whatever mount point device want to be shown by conky).

The calendar script noticed in my path "~/Documente/conky/get_calendar.sh"    wasn't my creation I just copied from Gentoo thread mentioned above you may find there or I'll posted here:

```
#! /bin/sh
#str=`echo '\033[01;32m29'`

DATE=`date | awk -F" " '{print $3}'`

case "$1" in
first_part)
cal | grep '[a-zA-Z]';
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}
($1 != $0 && i==0){i=i+1;print $1}';
;;
today)
echo $DATE;
;;
second_part)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}
($1 != $0 && i==1){i=i-1;print $2}
';
;;
esac

```

All you should do just name it in the way you want and change the path where  you place it, in .conkyrc file.

Note that I've got a smp HT CPU which runs the second CPU:CPU1, CPU2, this setting in conky is available for dual core type as well.
For a normal CPU if don't mistaken the setting is CPU0.. you should check with conky sample.

Sometimes I run another setting file called .conky-next were I place the calender for the next month...it took a little time to figure out exactly the geometry of it to be in the same line with previous conky loaded.


```
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

use_xft yes

xftfont Bitstream Vera Sans Mono:size=9

own_window_transparent yes
xftalpha 0.8

on_bottom yes
update_interval 1
own_window yes
double_buffer no
draw_shades no
draw_outline no

draw_borders no

stippled_borders 0

border_margin 4

border_width 1

default_color white
default_shade_color white
default_outline_color white

alignment top_right
gap_x 10
gap_y 582

objects.
use_spacer no

no_buffers no

uppercase no

TEXT
${color lightgrey}${exec  cal $(date +'%b %Y' --date '1 month')}


```

Another trick that again I found it on mentioned forum was to run my wallpaper background on a virtual root window to achive conky' s transparency in KDE, otherwise my background would be black no matter of conky settings. So I dropped a line in ~/.kde/Autostart/whatevernamed file as: 

#! /bin/bash
display -size 1280x1024 -window root /your/path/to/your/wallpaper.jpg

above you may choose your resolution as well. This trick is unnecessary in Gnome desktop.

This is something that you should see on your desktop...
[http://ubuntuforums.org/gallery/showimage.php?i=1436](http://ubuntuforums.org/gallery/showimage.php?i=1436)

I think that's all I can share now...enjoy! :)

---

### Post by nb- on 2005-12-15
Is it possible to get conky to graph another conky variable such as memory usage, without making a script to return it.  i.e something along the lines of;

 ${execgraph $memperc ...}

Without having to make a bash scrip to return it something like top -n 1 and then messing about to get the memory use out of it and then converting it to a percentage;

---

### Post by limit223 on 2005-12-15
.well..I tried once exec conky in conky ...but the cpu consume went up like crazy....and I didn't have really the right output...

---

### Post by towsonu2003 on 2005-12-16
using conky 1.3.1 since installed breez, and LOVIN it! I don't know what I would do without it!!! Here is my conky screenshot with my .conkyrc for anyone who might be interested:
[img]http://ubuntuforums.org/attachment.php?attachmentid=4562&stc=1&d=1134717392[/img]

```

# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
on_bottom yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour hereown_window_colour grey

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline yes

# Draw borders around text
draw_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 6
gap_y 30

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase yes

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$alignc =CONKY=
$alignc $nodename - $sysname $kernel on $machine
$alignc Uptime:${color lightgrey} $uptime $color -  Load:${color lightgrey} 1m-$color${loadavg 1}${color lightgrey} 5m-$color${loadavg 2}${color lightgrey} 15m-$color${loadavg 3}$color
$stippled_hr
${color lightgrey}HDD I/O:$color $diskio
${color red}${diskiograph 0000ff 00ff00}
${color lightgrey}CPU Usage:$color $cpu% ${color #cc2222} ${cpubar}
${color red}${cpugraph 0000ff 00ff00}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:$color PPP0 ${color lightgrey} on $color ${addr ppp0}
${color lightgrey} Down:${color #8844ee} ${downspeedf ppp0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeedf ppp0} k/s
${color #0000ff}${downspeedgraph ppp0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph ppp0 32,150 0000ff ff0000}
$color$stippled_hr
${color lightgrey}Networking:$color WLAN0 ${color lightgrey} on $color ${addr wlan0}
${color lightgrey}Link Status:$color ${linkstatus wlan0}
 ${color lightgrey}Down:${color #8844ee} ${downspeed wlan0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed wlan0} k/s
${color #0000ff}${downspeedgraph wlan0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph wlan0 32,150 0000ff ff0000}
$color$stippled_hr
${color lightgrey}Networking:$color ETH0 ${color lightgrey} on $color ${addr eth0}
 ${color lightgrey}Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #0000ff}${downspeedgraph eth0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth0 32,150 0000ff ff0000}
$color$stippled_hr
${color lightgrey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
 /home $color${fs_used /home}/${fs_size /home} ${fs_bar /home}
 /fat32 $color${fs_used /fat32}/${fs_size /fat32} ${fs_bar /fat32}
$color$stippled_hr
CPU ${tail /proc/acpi/thermal_zone/THRM/temperature 1 30}
$color$stippled_hr
${color lightgrey}Name              CPU%   MEM%   PID
${color #ff4500} ${top name 1} ${top cpu 1} ${top mem 1} ${top pid 1}
${color #eeee00} ${top name 2} ${top cpu 2} ${top mem 2} ${top pid 2}
${color #00ee00} ${top name 3} ${top cpu 3} ${top mem 3} ${top pid 3}
${color} ${top name 4} ${top cpu 4} ${top mem 4} ${top pid 4}
${color} ${top name 5} ${top cpu 5} ${top mem 5} ${top pid 5}
${color} ${top name 6} ${top cpu 6} ${top mem 6} ${top pid 6}
${color} ${top name 7} ${top cpu 7} ${top mem 7} ${top pid 7}
${color} ${top name 8} ${top cpu 8} ${top mem 8} ${top pid 8}
${color} ${top name 9} ${top cpu 9} ${top mem 9} ${top pid 9}

```

---

### Post by Chris Tucker on 2005-12-16
is there any way to get conky to not blink every time it updates? it gets really annoying...

---

### Post by limit223 on 2005-12-16
[QUOTE=Chris Tucker]is there any way to get conky to not blink every time it updates? it gets really annoying...[/QUOTE]
In .conkyrc
```
double_buffer yes
```

and in /etc/X11/xorg.conf

```
Section "Module"
Load     "dbe"
```

---

### Post by Chris Tucker on 2005-12-16
that works, but with own_window yes, it appears in the taskbar, but with own_window no, it hides all my desktop items when running, when i move a window over and then off of where my icons were, they reappear untill conky updates again... how do i keep my icons but get conky out of my taskbar?

---

### Post by Chris Tucker on 2005-12-16
[http://conky.sourceforge.net/gnome.html](http://conky.sourceforge.net/gnome.html)
 
nevermind :D that should work

---

### Post by limit223 on 2005-12-16
Install devilspie version >=0.13 and follow my post #66 from this thread.

---

### Post by benplaut on 2005-12-16
i enabled Double Buffer to stop the flickering, and the nautilus icons hide themselves as soon as Conky refreshes. I set the refresh to 5 seconds, put reallly big SVG icons, and now i have an iconless desktop... it's a bug, but it looks pretty damn nice ;)

---

### Post by Chris Tucker on 2005-12-16
well, with devilspie you dont need to worry about icons..

---

### Post by benplaut on 2005-12-17
[QUOTE=Chris Tucker]well, with devilspie you dont need to worry about icons..[/QUOTE]

...then the Show Desktop kills you...

---

### Post by Chris Tucker on 2005-12-19
i never use that :P i have that button taken off my taskbar...

---

### Post by r0nin on 2005-12-19
[QUOTE=benplaut]i enabled Double Buffer to stop the flickering, and the nautilus icons hide themselves as soon as Conky refreshes. I set the refresh to 5 seconds, put reallly big SVG icons, and now i have an iconless desktop... it's a bug, but it looks pretty damn nice ;)[/QUOTE]

I've got the same problem. I just leave it to flicker now. Most of the time I've got Opera covering my Desktop anyway. Not the best solution, but suits me at the moment.

Thanks limit223 for your config-file, I've modified it to my likeing. Could need a little help with adding temperatures and fan speeds (lm-sensors work properly) to my script though :)

---

### Post by astronerd on 2005-12-19
Hey all, I just got conky from synaptic.  When I run conky from the terminal, it places it in the lower left hand corner, half way cut off.  I dont know where my conky config file is to edit it, nor do I really know what to edit so that I can move conky's location etc..  I am just trying it out to replace gkrellm, so I would like tranparency and basic monitoring tools.  TIA.
Charles

oh, running breezy, gnome.

---

### Post by PMO6022 on 2005-12-19
[quote=astronerd]I dont know where my conky config file is to edit it...[/quote] 
The example conkyrc should be at /usr/share/doc/conky/examples/conkyrc.sample.gz

You'll need to copy it to ~/.conkyrc and edit it to suit your needs.

---

### Post by astronerd on 2005-12-19
So, I did 

cp /usr/share/doc/conky/examples/conkyrc.sample.gz ~/.conkyrc

Then did gedit ~/.conkyrc and it said that it couldnt edit that file type.  Is there something I didnt get when I downloaded it from synaptic?

---

### Post by limit223 on 2005-12-19
[QUOTE=r0nin]
Thanks limit223 for your config-file, I've modified it to my likeing. Could need a little help with adding temperatures and fan speeds (lm-sensors work properly) to my script though :)[/QUOTE]

You are welcome..I share as many people in this community do.
 Unluckly, as the part of temperature in conky it was not really my attention 'cause I have a controller (ic2 from ICH6 series - w83637thf) unsupported by the sensors driver..yet..



astronerd,
could you read more how to change permission of a file?? would help you ...

---

### Post by PMO6022 on 2005-12-19
Ok.  The file is gzipped so you'll need to cd to /usr/share/doc/conky/examples and do the following:```
sudo gunzip conkyrc.sample.gz
```This will give you the file conkyrc.sample in the current directory, which can then be copied to ~/.conkyrc, which should then be editable in gedit.

---

### Post by astronerd on 2005-12-19
Thanks, got it working.. but it keeps flickering and giving me another error.  I used the config file from here.
[http://www.ubuntuforums.org/showpost.php?p=574297&postcount=85](http://www.ubuntuforums.org/showpost.php?p=574297&postcount=85)

But when I run it gives me this in the terminal, 
sh: /home/malespin/Documents/conky/get_calendar.sh: No such file or directory

I am assuming I just need to add the get_calendar.sh file, but I dont know what/where that is.  And how do I stop the flickering?
Thanks

---

### Post by PMO6022 on 2005-12-19
[quote=astronerd]But when I run it gives me this in the terminal, 
sh: /home/malespin/Documents/conky/get_calendar.sh: No such file or directory

I am assuming I just need to add the get_calendar.sh file, but I dont know what/where that is.  And how do I stop the flickering?
Thanks[/quote] 
If I recall correctly, the flickering is a gnome problem, and since I'm running enlightenment, I can't help you there, sorry.  As for get_calendar.sh  it appears to be in the post you linked to above.  Just copy and paste it wherever you want, and then edit the path in the conkyrc file to point to it.

Alternatively, I simply use ${pre_exec cal} in my conkyrc to generate a calendar.  To see what it will look like, type cal into your terminal.

I've attached the two conkyrc's I use.  To see the output from them, see the screenshots at: 
[http://ubuntuforums.org/gallery/files/1/0/1/9/8/e16.8-pre1_original.jpg](http://ubuntuforums.org/gallery/files/1/0/1/9/8/e16.8-pre1_original.jpg)

The weather and mail check scripts are something I'm currently working on, and will hopefully release in the next couple of weeks.

---

### Post by limit223 on 2005-12-19
Some sample scripts for everybody's guidance are here:
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by r0nin on 2005-12-20
```

background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

use_xft yes

xftfont Bitstream Vera Sans Mono:size=9

own_window_transparent yes

xftalpha 0.8
on_bottom yes

update_interval 1

own_window no

double_buffer yes

draw_shades no

draw_outline no

draw_borders no

stippled_borders 0

border_margin 4

border_width 1

default_color white
default_shade_color white
default_outline_color white


alignment top_right
gap_x 10
gap_y 25


use_spacer no

no_buffers no

uppercase no

TEXT
$sysname $kernel    ${time %A,%d %B}
$stippled_hr
${color lightgrey}Time:$color ${time %k:%M:%S}
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}
${color #4F6B93}${cpugraph 25 8098ff ffc7ea}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% $membar
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color lightgrey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Top Processes:
${color lightgrey}Name              PID     CPU%   MEM%
${offset 10}${color lightgrey}$color${top name 1} ${color #a9c7ea}${top pid 1} ${top cpu 1} ${top mem 1}
${offset 10}${color lightgrey}$color${top name 2} ${color #a9c7ea}${top pid 2} ${top cpu 2} ${top mem 2}
${offset 10}${color lightgrey}$color${top name 3} ${color #a9c7ea}${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey}Mem usage
${offset 10}${color lightgrey}$color${top_mem name 1} ${color #a9c7ea}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${offset 10}${color lightgrey}$color${top_mem name 2} ${color #a9c7ea}${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${offset 10}${color lightgrey}$color${top_mem name 3} ${color #a9c7ea}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$color$stippled_hr
${color lightgrey}Temperatures:
${offset 10}CPU:${color #a9c7ea} ${i2c 1-0290 temp 2} C
${offset 10}${color lightgrey}MB: ${color #a9c7ea} ${i2c 1-0290 temp 1} C
$color$stippled_hr
${color lightgrey}Networking:
${offset 10}Down:${color #a9c7ea} ${downspeed eth0} k/s${color lightgrey} ${alignr}Up:${color #a9c7ea} ${upspeed eth0} k/s
${offset 10}${color #4F6B93}${downspeedgraph eth0 25,100 8098ff ffc7ea} ${alignr}${color #4F6B93}${upspeedgraph eth0 25,100 8098ff ffc7ea}
${offset 10}${color lightgrey}Total: ${color #a9c7ea}${totaldown eth0} ${alignr}${color lightgrey}Total: ${color #a9c7ea}${totalup eth0}
$color$stippled_hr
${color lightgrey}File systems:$alignr
/root  $color${fs_used_perc /}%   ${fs_used /}/ ${fs_size /} ${fs_bar /}
/home $color${fs_used_perc /home/pierre}%  ${fs_used /home/pierre}/ ${fs_size /home/pierre} ${fs_bar /home/pierre}
/music  $color${fs_used_perc /mnt/music}%   ${fs_used /mnt/music}/ ${fs_size /mnt/music} ${fs_bar /mnt/music}
/temp  $color${fs_used_perc /mnt/temp}%   ${fs_used /mnt/temp}/ ${fs_size /mnt/temp} ${fs_bar /mnt/temp}
$color$stippled_hr

```

Well, here's my script. Managed to get the temperatures working. I won't bother with the fans as they aren't being monitored correctly (I'm using silent low RPM fans and I'm guessing that's the problem).
I'll probably continue playing around with it though ;)

---

### Post by nb- on 2005-12-20
Well here is my conky, with hard disk and graphics card temps.

Hard disk temps are done with hddtemp ( [http://www.guzu.net/linux/hddtemp.php](http://www.guzu.net/linux/hddtemp.php) )
             
${execi 10 hddtemp /dev/sdb |cut -c 24-28}°C
hddtemp /dev/device |cut -c characters that list temperature

${execi 10 nvidia-settings -q gpucoretemp |grep Attribute |cut -c 41-42}°C
GPU temp is done with the nvidia settings tool.  Output is searched for Attribute to get only the first line with the temp in it (it didnt seem to like moving lines 2&3 to /dev/null) and cut at the right characters to give the temp.

```
# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use pseudo transparency with own_window?
own_window_transparent no

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 280 5
#maximum_width 150

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 10

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 13
gap_y 13
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
#${font Luxi Mono:size=10}justo como este texto que o google traduz fÃªz o portuguÃªs
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}

TEXT
Lemur@$nodename - $sysname $kernel on $machine
$hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #5000a0} ${cpu}% ${color lightgrey}| RAM Usage:$color $mem/$memmax - ${color #5000a0}$memperc%
${color black}${cpugraph ff0000 0000ff}
${color lightgrey}Buffer Memory:$color $buffers ${color lightgrey}Cache Memory:$color $cached
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$hr
${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed eth1} k/s${color lightgrey} ${offset 70}Up:${color #22ccff} ${upspeed eth1} k/s
${color black}${downspeedgraph eth1 32,150 ff0000 0000ff} $alignr${color black}${upspeedgraph eth1 32,150 0000ff ff0000}
DiskIO: $diskio
${color black}${diskiograph 32,300 ff0000 0000ff}
${color lightgrey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
 /home $color${fs_used /home}/${fs_size /home} ${fs_bar /home}
$color$hr
${color lightgrey}Temperatures:
 CPU:$color ${i2c 2-0290 temp 1}°C${color grey} - MB:$color ${i2c 2-0290 temp 2}°C - GPU:$color ${execi 10 nvidia-settings -q gpucoretemp |grep Attribute |cut -c 41-42}°C
 HDC:$color ${execi 10 hddtemp /dev/hdc |cut -c 27-31} ${color grey} - SDA:$color ${execi 10 hddtemp /dev/sda |cut -c 24-28} ${color grey}  - SDB:$color ${execi 10 hddtemp /dev/sdb |cut -c 24-28}
${font Dungeon:style=Bold:pixelsize=12}${color #88aadd}MPD: ${alignc}$mpd_artist - $mpd_title
${color #88aadd}$mpd_bar
${color #88aadd}${alignc}$mpd_status
${color}Name              PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

```

---

### Post by reet on 2005-12-21
Everyone seems to be posting their .conkyrc files here so I thought I would join the party... You'll have to rename the conkyrc.txt file and edit it to suit your system if you want to use it. I'm not too sure about my color choices yet for the graphs.

---

### Post by daschl on 2005-12-21
i really like to see your postings here (because i saw them a month or two in the gentoo forums)!

conky is a real nice program and i like it more then gdesklets or stuff like this.

congratulations to your great work, and keep on developing :)

---

### Post by r0nin on 2005-12-21
My final version: new colours, hddtemp (thanks nb-). New wallpaper. Now I just need to get rid of Ubuntus brown colour scheme.
Thanks to all the guys posting their configs and tweaks :)

```

background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

use_xft yes

xftfont Bitstream Vera Sans Mono:size=9

own_window_transparent yes

xftalpha 1
on_bottom yes

update_interval 1

own_window no

double_buffer yes

draw_shades no

draw_outline no

draw_borders no

stippled_borders 0

border_margin 4

border_width 1

default_color white
default_shade_color white
default_outline_color white


alignment top_right
gap_x 10
gap_y 25


use_spacer no

no_buffers yes

uppercase no

TEXT
$sysname $kernel    ${time %A,%d %B}
$stippled_hr
${color lightgrey}Time:$color ${time %k:%M:%S}             ${color lightgrey}Uptime:$color $uptime ${color lightgrey}
Load:$color $loadavg
${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}
${color lightgrey}${cpugraph 25 F0822C 88050B}
${color lightgrey}RAM Usage:$color  $mem/$memmax ${color lightgrey}-$color $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax ${color lightgrey}-$color  $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color lightgrey}Running:$color $running_processes
${color lightgrey}DiskIO: ${color white}$diskio
${color lightgrey}${diskiograph 325 F0822C 88050B}
$color$stippled_hr
${color lightgrey}Top Processes:
${color lightgrey}Name               PID     CPU%   MEM%
${offset 10}${color white}$color${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${offset 10}${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${offset 10}${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey}Mem usage
${offset 10}${color white}$color${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${offset 10}${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${offset 10}${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$color$stippled_hr
${color lightgrey}Temperatures:
${offset 10}CPU:${color white} ${i2c 1-0290 temp 2}°C ${color lightgrey} - MB: ${color white} ${i2c 1-0290 temp 1}°C
${offset 10}${color lightgrey}SDA:  ${color white}${execi 10 hddtemp /dev/sda |cut -c 27-31}C ${color lightgrey} - SDB:  ${color white}${execi 10 hddtemp /dev/sdb |cut -c 27-31}C
$color$stippled_hr
${color lightgrey}Networking:
${offset 10}Down:${color white} ${downspeed eth0} k/s${color lightgrey} ${alignr}Up:${color white} ${upspeed eth0} k/s
${offset 10}${color lightgrey}${downspeedgraph eth0 25,100 F0822C 88050B} ${alignr}${color lightgrey}${upspeedgraph eth0 25,100 F0822C 88050B}
${offset 10}${color lightgrey}Total: ${color white}${totaldown eth0} ${alignr}${color lightgrey}Total: ${color white}${totalup eth0}
$color$stippled_hr
${color lightgrey}File systems:$alignr
${offset 10}${color}/root  ${fs_used_perc /}%   ${fs_used /}/   ${fs_size /} ${fs_bar /}
${offset 10}/home  $color${fs_used_perc /home/pierre}%   ${fs_used /home/pierre}/   ${fs_size /home/pierre} ${fs_bar /home/pierre}
${offset 10}/music $color${fs_used_perc /mnt/music}% ${fs_used /mnt/music}/ ${fs_size /mnt/music} ${fs_bar /mnt/music}
${offset 10}/temp  $color${fs_used_perc /mnt/temp}% ${fs_used /mnt/temp}/ ${fs_size /mnt/temp} ${fs_bar /mnt/temp}
$color$stippled_hr

```

---

### Post by venice on 2006-01-08
Well I have a problem that my conky is blinking all the time... it shows and disappears all the time. Is there anything that can be done to solve this anoying problem?

thanks,
venice

---

### Post by reet on 2006-01-08
Have you read this thread? Or at least the first 4 posts?

---

### Post by denkedran on 2006-01-08
Hi forum,
i just installed conky, but can't get it to start. I installed it via apt-get and did the following
```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~.conkyrc
```
when i start conky it quits with the following message
```
Conky: can't open '/sys/bus/i2c/devices/0-0050/temp2_input': No such file or directory
please fix i2c or remove it from Conky
```
I configured my kernel with appropriate drivers for my sensor chip including support for eeprom
```
$ sensors
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.47 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
VCore 2:   +1.52 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
+3.3V:     +3.36 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +5.08 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.16 V  (min = +10.82 V, max = +13.19 V)
-12V:      +1.70 V  (min = -13.18 V, max = -10.80 V)       ALARM
-5V:       +2.54 V  (min =  -5.25 V, max =  -4.75 V)       ALARM
V5SB:      +5.64 V  (min =  +4.76 V, max =  +5.24 V)       ALARM
VBat:      +2.05 V  (min =  +2.40 V, max =  +3.60 V)       ALARM
fan1:     1205 RPM  (min =    0 RPM, div = 8)
fan2:     1506 RPM  (min =    0 RPM, div = 8)
fan3:        0 RPM  (min = 3068 RPM, div = 2)              ALARM
temp1:       +25°C  (high =   +89°C, hyst =    -2°C)   sensor = thermistor 
temp2:     +29.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor 
temp3:     +26.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor 
vid:      +0.000 V  (VRM Version 2.4)
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm enabled

eeprom-i2c-0-51
Adapter: SMBus ALi 1563 Adapter @ 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus ALi 1563 Adapter @ 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

```

It seems that conky tries to read the temperature from my DDR-RAM-modules. :confused: 
I removed these lines from .conkyrc
```
#${color lightgrey}Temperatures:
# CPU:$color ${i2c temp 2}C${color grey} - MB:$color ${i2c temp 1}C
```
But the same error appears. how can i avoid that conky scans that sensors ?

Thanx for any help

---

### Post by NZ-Wanderer on 2006-01-09
I seem to have a slight problem with Conky...

I been experimenting with a couple of users conky files (thanks guys) and have got something working combining the best... :)

My problem is, when I boot Ubuntu (breezy) Conky appears as it loads, but then disappears when my desktop wallpaper appears...

Any ideas??

---

### Post by cutOff on 2006-01-09
denkedran try to *remove* the lines, don't comment them.

---

### Post by venice on 2006-01-09
reet - sorry for bodering. I omitted the first posts... Problem solved. Thank you.

venice

---

### Post by Caboto on 2006-01-09
I've used torsmo for a long time. Got a nice rc file off the net and changed it a little bit for my needs.
When I've discovered conky some time ago, I just used my .torsmorc and modified some commands. Still using Conky 1.3.1, because the new Version 1.3.3 had some ugly font, when I've first tried it.
Screenshot is attached and if someone needs some help with his .conkyrc, here's mine. The Comments are still from my old .torsmorc file. So don't bet on them...

```
# set to yes if you want tormo to be forked in the background
background yes

# X font used, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
# font *mintsmild.se*
# font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
# font terminus-14
# font modd-12
#font microsoft-tahoma

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8
#xftfont Terminus:size=6
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont monospace-6

own_window_transparent yes
own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders naround text
draw_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 20

# border width
border_width 0

# Default colors and also border colors
#default_color darkslategrey
default_color black
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 12
gap_y 32

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

#${execi 2 ps --sort -pcpu x -eo comm,pid,pcpu,user|head -7}

TEXT
login: ${color grey}${pre_exec whoami}${color}
host: ${color grey}$nodename - $sysname $kernel on $machine
${color}time: ${color grey}${time %d.%m.%Y %H:%M}${color} (uptime: ${color grey}$uptime_short${color})
${color}$hr
${color}cpu usage:${color grey} $cpu%${color}  -   processes:${color grey} $processes  ${color}(${color grey}$running_processes${color})
${cpubar}
${color}ram:${color grey} $mem/$memmax - $memperc%${color}
$membar
swap:${color grey} $swap/$swapmax - $swapperc%${color}
$swapbar
${color}$hr
${color}networking:${color} down:${color grey} ${downspeed eth0} k/s - ${color}up:${color grey} ${upspeed eth0} k/s${color}
${color}$hr
${color}file systems:
${color}/          ${color grey}${fs_used /}/${fs_size /}${color}   (${color grey}${fs_free_perc /}%${color} free)
${fs_bar /}
${color}/home      ${color grey}${fs_used /home}/${fs_size /home}${color}   (${color grey}${fs_free_perc /home}%${color} free)
${fs_bar /home}
${color}/windows/c ${color grey}${fs_used /windows/c}/${fs_size /windows/c}${color}   (${color grey}${fs_free_perc /windows/c}%${color} free)
${fs_bar /windows/c}
${color}/windows/d ${color grey}${fs_used /windows/d}/${fs_size /windows/d}${color} (${color grey}${fs_free_perc /windows/d}%${color} free)
${fs_bar /windows/d}
${color}/windows/e ${color grey}${fs_used /windows/e}/${fs_size /windows/e}${color} (${color grey}${fs_free_perc /windows/e}%${color} free)
${fs_bar /windows/e}
${color}/windows/f ${color grey}${fs_used /windows/f}/${fs_size /windows/f}${color} (${color grey}${fs_free_perc /windows/f}%${color} free)
${fs_bar /windows/f}
${color}/windows/g ${color grey}${fs_used /windows/g}/${fs_size /windows/g}${color} (${color grey}${fs_free_perc /windows/g}%${color} free)
${fs_bar /windows/g}
${color}/windows/h ${color grey}${fs_used /windows/h}/${fs_size /windows/h}${color}   (${color grey}${fs_free_perc /windows/h}%${color} free)
${fs_bar /windows/h}
${color}/windows/i ${color grey}${fs_used /windows/i}/${fs_size /windows/i}${color} (${color grey}${fs_free_perc /windows/i}%${color} free)
${fs_bar /windows/i}
${color}$hr
${color}cpu usage	   pid     cpu%    mem%
${color darkred} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color grey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color grey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color grey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color grey} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}
${color}mem usage
${color darkred} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color grey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color grey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color grey} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
${color grey} ${top_mem name 5} ${top_mem pid 5} ${top_mem cpu 5} ${top_mem mem 5}
```

Got to do something against the grey font on the bright background. :\

---

### Post by fog on 2006-01-09
[QUOTE=denkedran]
when i start conky it quits with the following message
```
Conky: can't open '/sys/bus/i2c/devices/0-0050/temp2_input': No such file or directory
please fix i2c or remove it from Conky
```
[/QUOTE]
[COLOR="DarkOrchid"]**I solve this problem like this:**[/COLOR]
```
${color lightgrey}Temperatures:
CPU:$color ${i2c 9191-0290 temp 2}C${color grey} - MB:$color ${i2c 9191-0290 temp 1}C
```
because my temperatures are in:
**/sys/bus/i2c/devices/9191-0290/**

[IMG]http://img230.imageshack.us/img230/4301/screenshot3xj.jpg[/IMG]

Find where are your "temp 2" and "temp 1" and change this value: [COLOR="DarkOrchid"]9191-0290[/COLOR] with yours.

With this code you can see CPU and MB temperatures. :) 

[[IMG]http://img230.imageshack.us/img230/4159/screenshot10uj.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=screenshot10uj.jpg)

---

### Post by firehead on 2006-01-09
thx anyway

---

### Post by mustang on 2006-01-09
Was anybody able to fix the problem with the show desktop button?

---

### Post by denkedran on 2006-01-10
@cutOff
your soulution worked. cjust commenting the lines didn't work. After remove them conky started.

@fog
thanx a lot i couldn't handle the syntax with i2c, after your advise
```
${color lightgrey}Temperatures:
CPU:$color ${i2c 9191-0290 temp 2}C${color grey} - MB:$color ${i2c 9191-0290 temp 1}C
```
it works really great

thanx a lot to both of you

---

### Post by souteneur3190 on 2006-01-13
umm....yah i just have no idea how to use this program.  i am on ubunut using the gnome window manger.  after installing i type conky and in the left hand bottom corner i see it. but it disappears.  i kno you guys already know about this problem but can someone please give me a method that actually works?

1.3.1-1   <-------That is the version of conky i have

Also when i try to join conky in irc it says i must be identified or somthing.  Pleas help

Thanks in advace

---

### Post by bluevoodoo1 on 2006-02-04
[QUOTE=limit223]In .conkyrc
```
double_buffer yes
```

and in /etc/X11/xorg.conf

```
Section "Module"
Load     "dbe"
```[/QUOTE]

Thanks limit223! I tried that but it didn't work... then I restarted... and it did!

I'm a fan of the weather in conky and I've come up with something like [http://conky.sourceforge.net/metar.py](http://conky.sourceforge.net/metar.py) but a bit simpler...

From what I've read METAR support was stopped after version 1.3 right?... but here's somewhat of a workaround (not the greatest, hopefully something better will work)

get python-pymetar...

```

sudo apt-get install python-pymetar

```

Then add the following line to your .conkyrc file (replacing KROC with your 4-digit code, a list is here [http://adds.aviationweather.noaa.gov/metars/stations.txt)](http://adds.aviationweather.noaa.gov/metars/stations.txt)). The number 60 refers to the time in seconds before updating. You can change it to anything you wish.

```
${texeci 60 pymetar KROC}
``` 

Thoughts about this method?


I still can't get the mpd to work. I enabled it during ./configure and I have the mpd package... and no luck. Any ideas?


By the way, I'm obsessed with conky!!!

---

### Post by limit223 on 2006-02-05
bluevoodoo1,
Thank you for the python-pymetar hint! Actually I tried once for a short but "tangle" script which uses cron to run it for each sec, and I couldn't make it work, though. I didn't know that I could use this CL so easy in execi conky's variable.


Media player daemon MPD is just a daemon application that provide a mp3 or ogg audio format that easily can be accessed remotely. For that you need a client of it as mpc or a GUI client as gmpc.
More info here : [http://mpd.wikicities.com/wiki/Main_Page](http://mpd.wikicities.com/wiki/Main_Page)
And you don't have to build them from source you have them in Breezy universe repo(gmpc 0.11.2 ver)

sudo apt-get install mpd gmpc

Start the daemon: 

mpd

Then run gmpc, Settings-Connection tab: Connect, Server settings: Update database and play around with the rest of the settings and Playlist button.

If you follow my .conkyrc you'll have there most of the options for the $mpd variable.

:KS

---

### Post by fog on 2006-02-05
[QUOTE=bluevoodoo1]
```
${texeci 60 pymetar KROC}
``` 
[/QUOTE]
I'm using this line in .conkyrc like this:
> ${texeci 60 pymetar LGAV}
but no results. What I'm doing wrong?
Thanx

I found it, is:
> ${execi 60 pymetar LGAV}
without the "t"

---

### Post by ChaKy on 2006-02-05
Is there a script that will run inside of the conky, to show number of updated packages for Ubuntu and what packages are ready for upgrade?

---

### Post by cutOff on 2006-02-05
[QUOTE=ChaKy]Is there a script that will run inside of the conky, to show number of updated packages for Ubuntu and what packages are ready for upgrade?[/QUOTE]
Personally I don't know any but would be interested too.

---

### Post by bluevoodoo1 on 2006-02-05
[QUOTE=limit223]

Media player daemon MPD is just a daemon application that provide a mp3 or ogg audio format that easily can be accessed remotely. For that you need a client of it as mpc or a GUI client as gmpc.
More info here : [http://mpd.wikicities.com/wiki/Main_Page](http://mpd.wikicities.com/wiki/Main_Page)
And you don't have to build them from source you have them in Breezy universe repo(gmpc 0.11.2 ver)

sudo apt-get install mpd gmpc

Start the daemon: 

mpd

Then run gmpc, Settings-Connection tab: Connect, Server settings: Update database and play around with the rest of the settings and Playlist button.

If you follow my .conkyrc you'll have there most of the options for the $mpd variable.

:KS[/QUOTE]


Great! Thanks! I'll be sure to check that out as soon as I can!

[QUOTE=fog]I'm using this line in .conkyrc like this:

but no results. What I'm doing wrong?
Thanx

I found it, is:

without the "t"[/QUOTE]

Hmmm, the texeci works for me, but if execi works too... then great!

---

### Post by gasparov on 2006-02-08
Hi,
  I've been following this thread and a few things are quite strange.
[On this page ]("http://conky.sourceforge.net/gnome.html") there are two solutions to avoid icons disappearing when conky refreshes
[LIST]
[*]use devilspy with own_window yes
[*]disable nautilus desktop (that is no icons on desktop)
[/LIST]

on this thread a couple of people post their screenshot and their conkyrc,it seems that they where able to run conky with "own_window no" and still have icons on the desktop.Did you actually solve this nautilus related problem in another way than the two ones specified above or you just are good in taking the screenshots at the right time?

---

### Post by mcduck on 2006-02-08
[QUOTE=gasparov]Hi,
  I've been following this thread and a few things are quite strange.
[On this page ]("http://conky.sourceforge.net/gnome.html") there are two solutions to avoid icons disappearing when conky refreshes
[LIST]
[*]use devilspy with own_window yes
[*]disable nautilus desktop (that is no icons on desktop)
[/LIST]

on this thread a couple of people post their screenshot and their conkyrc,it seems that they where able to run conky with "own_window no" and still have icons on the desktop.Did you actually solve this nautilus related problem in another way than the two ones specified above or you just are good in taking the screenshots at the right time?[/QUOTE]
I have 'own_window yes', 'background yes' 'on_bottom yes', 'own_window yes' and 'own_window_transparent yes' in my .conkyrc, and 'pinned', 'skip_taskilist' and 'skip_pager' in devilspie.

---

### Post by zi99y on 2006-02-08
Did anyone get to the bottom of the problem where the desktop wallpaper loads over the top of conky on startup? If I could just fix this I'ld be happy.

Works fine ifI launch conky once the desktop has fully loaded.

---

### Post by andlinux21 on 2006-02-08
Do they have more sample conky files that I can look at so that i can do my own?  I am trying to see what does what so that I can adjust only what's needed for my laptop

---

### Post by bluevoodoo1 on 2006-02-08
[QUOTE=andlinux21]Do they have more sample conky files that I can look at so that i can do my own?  I am trying to see what does what so that I can adjust only what's needed for my laptop[/QUOTE]


[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)  <--- click on conkyrc to see each file
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by mcduck on 2006-02-09
[QUOTE=zi99y]Did anyone get to the bottom of the problem where the desktop wallpaper loads over the top of conky on startup? If I could just fix this I'ld be happy.

Works fine if I launch conky once the desktop has fully loaded.[/QUOTE]
If you have set conky to load on startup with Gnome Session manager, try giving it a bit higher number.

---

### Post by limit223 on 2006-02-14
For those who have an ASUS motherboard of P5GDx series, and haven't got so far sensors working I'll pass a very good news :)..
 I just tested the last script of sensor-detect from [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/prog/detect/sensors-detect](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/prog/detect/sensors-detect) and finally it recognized the driver for w83627ehf chipset which was for long in development.
I'm really happy to see my temperature, fans sensors for my mb and cpu in conky!!


Yuuuppi!!!!:)

---

### Post by TherapyQuestionMark on 2006-02-15
Is there any way I can specify conky to start at a specific set of co-ordinates on my screen?
thanks!

---

### Post by limit223 on 2006-02-15
A new conky release 1.4 is up!
It has xmms, bmp, audacious, infopipe and bmpx support.
If anyone trust in my homemade .deb files and of course doesn't have much time/know how to compile I made one with all these features support included. In order to install bmpx you might add to apt-get repo :

deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/) breezy/

Cheers!


TherapyQuestionMark,
AFIK, the only values in variable **alignment** that you may use are: top_left, top_right, bottom_left, bottom_right or none. I haven't seen any guide from conky that may instruct a customed position on the screen...

PS. Added a demo picture with my conky using audacious variables.

---

### Post by kabus on 2006-02-18
Is there a way to limit the length of a variable in conky ?
For example, I'd like to limit $mpd_title to 30 characters, anything beyond that should get truncated. 
I've looked through the documentation and there doesn't seem to be way to set this explicitly, but maybe there's a workaround ? :confused:

---

### Post by simplyw00x on 2006-02-19
I just installed this and devilspie today, and, as the saying goes, it rocks like ninja. The 'show desktop' bug is a little annoying, but the good outweighs the bad. Screenshot attached. 

The real cunning, which took a while to concuct, was the xmms functionality. Yes so the new conky does this anyway blah blah download deb blah recompile blah dependecies I can't meet etc.

Anyway, the magic is in the xmms-info plugin (package of that name in Breezy repos) and the following 3 scripts:

```
#!/bin/bash
foo=`cat /tmp/xmms-info | grep -m1 Title: | cut -d : -f2 | cut -d - -f1`
echo $foo;
```
~/bin/xmms-1.sh

```
#!/bin/bash
foo=`cat /tmp/xmms-info | grep -m1 Title: | cut -d : -f2 | cut -d - -f2`
echo $foo;
```
~/bin/xmms-2.sh

```
#!/bin/bash
#User Settings here
file=/tmp/xmms-info

#Grab needed information
pos=`cat $file | grep -m1 uSecPosition: | cut -d : -f2`
len=`cat $file | grep -m1 uSecTime: | cut -d : -f2`
hun=100

foo=$(($hun*$pos/$len))

echo $foo
```
~/bin/xmms-3.sh

Now all you need to do is bung in the following in your .conkyrc:
```
${if_existing /tmp/xmms-info}
${color slate grey}XMMS:
${exec /home/carl/bin/xmms-1.sh}
${exec /home/carl/bin/xmms-2.sh}
${execbar /home/carl/bin/xmms-3.sh}
${endif}
```
This also checks if xmms is actually running, so if it isn't then it won't display those things or call the scripts, saving space and processing power. Bonus!

Thanks to the conky developers for a great app!

---

### Post by markmark on 2006-02-19
[QUOTE=TherapyQuestionMark]Is there any way I can specify conky to start at a specific set of co-ordinates on my screen?
thanks![/QUOTE]You can use the gap_x and gap_y variables to give an offset out from your specified corner. For example I have:
```
alignment top_right
gap_x 25
gap_y 35
```To get mine a little out from the right edge, and low enough to clear the top gnome panel.

---

### Post by simplyw00x on 2006-02-20
Hey, sorry to keep coming back to this but I managed to find a (really quite ugly and hacked) solution to the good old 'Show Desktop' bug. It doesn't really fix it, but what it does do is rescues the conky window from the netherworl of devilspie and miimisation.

What you need is the wmctrl package.
```
sudo apt-get install wmctrl
```

Then, whenever you lose your conky window:
```
wmctrl -a conky
```

I'll be playing around with wmctrl to try and find some more useful things to do, but for now that's it.

---

### Post by YourSurrogateGod on 2006-02-25
After I installed it from synap and tried starting it, this is what I got.
```
$ conky&
[1] 13724
$ Conky: /home/andrew/.conkyrc: 95: no such configuration: 'min_port_monitors'
Conky: /home/andrew/.conkyrc: 98: no such configuration: 'min_port_monitor_connections'
Conky: can't open '/sys/bus/i2c/devices/1-002d/temp2_input': No such file or directory
please fix i2c or remove it from Conky
```
I used [this](http://conky.sourceforge.net/conkyrc-drphibes) script that I got off the official conky site.

What am I doing wrong?

---

### Post by limit223 on 2006-02-25
Synaptic has an older ver of conky 1.3.3 which doesn't have protmon variable implemented that you use it in your script. Compile a new version with --enable-portmon in configuration and you'll get rid of that error message.
Plus that i2c message is that your sensor it is not set up correctly. 
A few posts above you may find the latest version of conky with all variables enabled, as an attachment of my post and i2c settings very well explained by **fog**.

---

### Post by YourSurrogateGod on 2006-02-26
[QUOTE=limit223]Synaptic has an older ver of conky 1.3.3 which doesn't have protmon variable implemented that you use it in your script. Compile a new version with --enable-portmon in configuration and you'll get rid of that error message.
Plus that i2c message is that your sensor it is not set up correctly. 
A few posts above you may find the latest version of conky with all variables enabled, as an attachment of my post and i2c settings very well explained by **fog**.[/QUOTE]
Didn't work.
```
$ sudo dpkg -i conky-1.4.0_1.4.0-1_i386.deb
Selecting previously deselected package conky-1.4.0.
(Reading database ... 126554 files and directories currently installed.)
Unpacking conky-1.4.0 (from conky-1.4.0_1.4.0-1_i386.deb) ...
dpkg: error processing conky-1.4.0_1.4.0-1_i386.deb (--install):
 trying to overwrite `/usr/bin/conky', which is also in package conky
Errors were encountered while processing:
 conky-1.4.0_1.4.0-1_i386.deb
```

---

### Post by limit223 on 2006-02-26
Did you try to uninstall first,  last version and after reinstall the new version?

---

### Post by YourSurrogateGod on 2006-03-06
[QUOTE=limit223]Did you try to uninstall first,  last version and after reinstall the new version?[/QUOTE]
Nope, I just did that now.

I also tried to install conky 1.4 through synap (the easy way) and [this](http://www.engr.uconn.edu/~ats01001/Screenshot.png) is what I got.

---

### Post by YourSurrogateGod on 2006-03-06
Ok, after installing it and such and putting in the features that I want into the .conkyrc file, I got the below.
```
$ conky&
[1] 9515
$ Conky: can't open '/sys/bus/i2c/devices/1-002d/temp2_input': No such file or directory
please fix i2c or remove it from Conky
```

---

### Post by theProf on 2006-03-06
simplyw00x,

Thank you so much for finding the wmctrl program.  It makes conky liveable, anyway.  Be nice to have it just stay on the desktop, but this'll do.

---

### Post by preyer on 2006-04-01
Hi,

Anyone of you know how to autostart conky when my kde desktop loads, I've tried the autostart option in the control panel and it works for everything else other than conky.

Thanks.

---

### Post by zi99y on 2006-04-01
Yes! You need to put a symbolic link in the HOME/.kde/Autostart directory

You can just enter the following command like so:
```
 ln -s /usr/bin/conky ~/.kde/Autostart/conky
```

(Hang on, I thought I was a noob!) :-k

---

### Post by daedalusman on 2006-04-03
How can I get the cpu MHz to display, I have tried a couple of things but nothing has worked so far. Here is my conkyrc file

```
# THIS CONFIG RELIES ON 2 SCRIPTS, CPUSPEED AND CPUTEMP
# YOUR SYSTEM MAY NOT REQUIRE THEM, REPLACE AS DESIRED

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want tormo to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono-7
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# Create own window instead of using desktop (required in nautilus)
own_window yes

own_window_transparent yes
own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 24
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #ffcb48}$nodename$color      ${color #828282}$sysname $kernel on 
$machine$color

${color #ffcb48}PROCESSING$color
   ${color #98c2c7}CPU:$color     ${execi 5 acpispeed}MHz       $cpu% 
   ${i2c 1-0290 temp 2}°C $color ${i2c 1-0290 temp 1}°C
   ${color #78af78}$cpubar
   ${color #78af78}${cpugraph 78af78 a3a3a3}

   ${color #98c2c7}NAME             PID       CPU%      MEM%
   ${color #e5e5e5}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
   ${color #c4c4c4}${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
   ${color #a3a3a3}${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
   ${color #828282}${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color #ffcb48}DATA$color
   ${color #98c2c7}RAM:$color     $memperc%         ${color 
#78af78}${membar 6}${color}

   ${color #98c2c7}NAME             PID       CPU%      MEM%
   ${color #e5e5e5}${top_mem name 1} ${top_mem pid 1}   ${top_mem cpu 1} 
    ${top_mem mem 1}
   ${color #c4c4c4}${top_mem name 2} ${top_mem pid 2}   ${top_mem cpu 2} 
    ${top_mem mem 2}
   ${color #a3a3a3}${top_mem name 3} ${top_mem pid 3}   ${top_mem cpu 3} 
    ${top_mem mem 3}
   ${color #828282}${top_mem name 4} ${top_mem pid 4}   ${top_mem cpu 4} 
    ${top_mem mem 4}

   ${color #98c2c7}Swap:$color    $swapperc%         ${color 
#78af78}${swapbar 6}$color
   ${color #98c2c7}/:$color       ${fs_free_perc /}%  $fs_free  ${color 
#78af78}${fs_bar 6 /}$color

   ${color #98c2c7}Upload:$color  ${upspeed eth0}kb/s${color #98c2c7} 
   Download:$color  ${downspeed eth0}kb/s

${color #ffcb48}Local Weather:
${color #98c2c7}${execi 1800 /home/daedalus/scripts/weather/weather.sh}

```

---

### Post by daedalusman on 2006-04-04
Ok, nevermind, I figured it out, I need freq_dyn_g in there instead of the cpuspeed which is a script I think. I'm having trouble getting the weather script working though. When I start conky from terminal it displays this...

```
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
unable to parse -
Conky: drawing to double buffer
Conky: forked to background, pid is 17447
```

and here is my updated and much better conky config file...

```
background yes
font 7x13
use_xft no
on_bottom yes

mpd_host 192.168.150.2
mpd_port 6600

update_interval 1.0

total_run_times 0

own_window yes

own_window_transparent yes

double_buffer yes

minimum_size 280 5

draw_shades yes
draw_outline no
draw_borders yes
stippled_borders 2
border_margin 4
border_width 1

default_color white
default_shade_color black
default_outline_color black

alignment bottom_right

maximum_width 308

gap_x 12
gap_y 12

no_buffers yes

uppercase no

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale no

use_spacer no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #5b6dad}$nodename   linux-$kernel${alignr}${time %T}

${color #5b6dad}System:
${color #5b6dad} Uptime:${color #7f8ed3} $uptime ${color #5b6dad}- Load:${color #7f8ed3} $loadavg
${color #5b6dad} CPU Frequency:${color #7f8ed3} $freq_dyn_g ${color #5b6dad} Maximum:${color #7f8ed3} $freq_g
${color #5b6dad} CPU Usage:${color #7f8ed3} $cpu% ${cpubar}
${color #000000}${cpugraph cpu0 32,309 000000 7f8ed3}
${color #5b6dad} RAM Usage:${color #7f8ed3} $mem/$memmax - $memperc% ${membar}
${color #5b6dad} Swap Usage:${color #7f8ed3} $swap/$swapmax - $swapperc% ${swapbar}
${color #5b6dad} Processes:${color #7f8ed3} $processes  ${color #5b6dad}Running:${color #7f8ed3} $running_processes
${color #5b6dad}Monitors          CPU      MB
${color #7f8ed3}                  ${i2c 1-0290 temp 2}C    ${i2c 1-0290 temp 1}C

${color #5b6dad}Networking:
 ${color #5b6dad}Down:${color #7f8ed3} ${downspeed eth0} k/s${color #5b6dad}${offset 80}Up:${color #7f8ed3} ${upspeed eth0} k/s
${color #000000}${downspeedgraph eth0 32,150 000000 7f8ed3} ${color #000000}${upspeedgraph eth0 32,150 000000 7f8ed3}

${color #5b6dad}File Systems:
 ${color #5b6dad}/ ${color #7f8ed3}${fs_used /}/${fs_size /} ${color #7f8ed3}${fs_bar /}
 ${color #5b6dad}/boot ${color #7f8ed3}${fs_used /boot/}/${fs_size /boot/} ${color #7f8ed3}${fs_bar /boot/}
 ${color #5b6dad}/home ${color #7f8ed3}${fs_used /home/}/${fs_size /home/} ${color #7f8ed3}${fs_bar /home/}
 ${color #5b6dad}Games ${color #7f8ed3}${fs_used /media/Games/}/${fs_size /media/Games/} ${color #7f8ed3}${fs_bar /media/Games/}
 ${color #5b6dad}Misc ${color #7f8ed3}${fs_used /media/Misc/}/${fs_size /media/Misc/} ${color #7f8ed3}${fs_bar /media/Misc/}
 ${color #5b6dad}Music ${color #7f8ed3}${fs_used /media/Music/}/${fs_size /media/Music/} ${color #7f8ed3}${fs_bar /media/Music/}
 ${color #5b6dad}Video ${color #7f8ed3}${fs_used /media/Video/}/${fs_size /media/Video/} ${color #7f8ed3}${fs_bar /media/Video/}
 ${color #5b6dad}WinShare ${color #7f8ed3}${fs_used /media/WinShare/}/${fs_size /media/WinShare/} ${color #7f8ed3}${fs_bar /media/WinShare/}

${color #5b6dad}Name              PID     CPU%   MEM%
${color #7f8ed3} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #7f8ed3} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #7f8ed3} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #5b6dad}Mem usage
${color #7f8ed3} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #7f8ed3} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #7f8ed3} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #5b6dad}Local Weather:
${color #7f8ed3}${execi 1800 /home/daedalus/scripts/weather/weather.sh}

```

I got the weather script from the conky website, I have no idea what that error message means. Can someone please help me out here, thanks.

---

### Post by sYs^ on 2006-04-04
I had the same problem with the weather script :\

and I have one more problem: I can't set conky "on all workplaces", my devilspie conf:

```
(if (is (application_name) "ubuntu - conky") (begin pin skip_tasklist skip_pager pin below))
```

How could I set that?

btw it's a great app. :>

---

### Post by daedalusman on 2006-04-04
[QUOTE=sYs^]and I have one more problem: I can't set conky "on all workplaces", my devilspie conf:

```
(if (is (application_name) "ubuntu - conky") (begin pin skip_tasklist skip_pager pin below))
```

How could I set that?

btw it's a great app. :>[/QUOTE]


I think what you need is rather than "ubuntu-conky" you just need "conky" in there, at least thats what I've got and it works great.

---

### Post by sYs^ on 2006-04-04
I think DevilsPie detects the window correctly and it removes conky from the tasklits and sticks it to the background but it simply doesn't set it on all workplaces.

If I modify my settings as u said even those options aren't working :\

---

### Post by daedalusman on 2006-04-04
This is what I have in my conky.ds file...

```
(if (matches (window_name) ".*conky") (begin pin (skip_pager) (skip_tasklist)))
```

Thats what works for me, I really don't know what else if this doesn't work. But give it a try and see what happens.

---

### Post by sYs^ on 2006-04-05
Thanks but it isn't working (for me) :\

---

### Post by arnieboy on 2006-04-11
[QUOTE=daedalusman]Ok, nevermind, I figured it out, I need freq_dyn_g in there instead of the cpuspeed which is a script I think. I'm having trouble getting the weather script working though. When I start conky from terminal it displays this...

```
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
unable to parse -
Conky: drawing to double buffer
Conky: forked to background, pid is 17447
```
[/quote]

to get the weather update working, u need to have curl and xsltproc installed.
do from terminal:
```
sudo apt-get install curl xsltproc
```

The weather script will now work fine.

---

### Post by daedalusman on 2006-04-13
[QUOTE=arnieboy]to get the weather update working, u need to have curl and xsltproc installed.
do from terminal:
```
sudo apt-get install curl xsltproc
```

The weather script will now work fine.[/QUOTE]


Thanks man, worked great once I set my location code. One thing though, do you know how I could get the script to display the temps in fahrenheit in paranthesis next to the celsius temp, kinda like thins 18C (75F)?

---

### Post by zasf on 2006-04-16
[QUOTE=daedalusman]This is what I have in my conky.ds file...

```
(if (matches (window_name) ".*conky") (begin pin (skip_pager) (skip_tasklist)))
```

Thats what works for me, I really don't know what else if this doesn't work. But give it a try and see what happens.[/QUOTE]

Download latest conky and you won't need devilspie anymore.

---

### Post by Mikebgr on 2006-05-01
[QUOTE=Baphijmm]Slight problem, and I'm not entirely sure from whence it is arising (very much newb here); I downloaded the file, extracted it, and got to the ./configure command, but it gives me this error:



Any input on what I might do to help this along?

EDIT: Actually, I think I found my own way.  Thanks anyway.[/QUOTE]

Having the same problem here. apt-getting it works fine, but its not the latest version, so I got the tarball and the ./configure breaks and gives me the exact same message at the end.

How did you solve this?

Btw note that dbe module is already loaded

---

### Post by paul.maddox on 2006-05-13
Just discovered conky, what a great app!

Thanks for the tips about loading the "dbe" module in my xorg.conf and also about devilspie, they work great!

Anyway... Here is my conky, I actually have 2 copies of conky running. One on my PC (the top one) and one on my downloads server (also running ubuntu) which is run using ssh forwarding. This one displays stats on files i'm downloading via a small shell script I wrote.

[IMG]http://www.accountsclub.com/Screenshot.jpeg[/IMG]

The eth monitor on the 2nd one doesn't seem to be working at the moment although i'm sure i'll crack it soon.

---

### Post by arnieboy on 2006-05-13
[QUOTE=daedalusman]Thanks man, worked great once I set my location code. One thing though, do you know how I could get the script to display the temps in fahrenheit in paranthesis next to the celsius temp, kinda like thins 18C (75F)?[/QUOTE]
if u are using the same weather script that I am, you can use british units instead of metric by looking for the following line in "weather.sh"
> UNITS=m
change that to:
> UNITS=s
and restart conky

---

### Post by apresvoop on 2006-05-13
I'm trying to install the latest Conky 1.4.1 but when I run configure, I get the following:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized
configure: error: /bin/sh ./config.sub i686-pc-linux- failed


Any reason why this is failing and how I can go about getting around it?  I don't know much about this, and a half hour of googling yielded only similar questions, and no answers.

---

### Post by Spug on 2006-05-15
[QUOTE=paul.maddox]This one displays stats on files i'm downloading via a small shell script I wrote.

[http://www.accountsclub.com/Screenshot.jpeg](http://www.accountsclub.com/Screenshot.jpeg)[/QUOTE]
"Current Connections" and the file download script were very interesting. How do they work? Is the former a script, a built-in function or a command output? And does the latter show wget or bittorrent downloads, or something else?

---

### Post by paul.maddox on 2006-05-15
Well the 'current connections' section is built into conky by default.

The download script is something i've written to manage my downloads.

Basically I have a script on my laptop which is triggered by right clicking on a download link in firefox and via an extension called launchy the link is sent to the download script.

This script then works out if i'm on the same network as my home downloads server or not and sends the link to my downloads server at home through SSH (no login needed, via public/private key) either locally or remotly depending on where I am. The downloads server will then start downloading it via wget providing any download credentials needed (user/pass), outputting a log file of the progress using wget's -o option. 

I have another script on my laptop that monitors the progress of any active downloads and calculates stuff like average speed and number of files downloaded etc by parsing the wget log files. conky then runs this script every few seconds and displays the output. 

When a download has been completed it moves it to the correct folder and sends me an email telling me the download has completed and also attaches a log of the download to the email.

All of this is quite useful as my usenet provider (easynews) automatically applies PAR files and unrar's any movies/tv etc I want in their web interface so I just right click the file in firefox and then wait for the email to tell me that it's finished downloading.


Hope this made sense, i'm pretty damn tired today! If you want to see the scripts just let me know and i'll post them online sometime.

---

### Post by CameronCalver on 2006-05-20
how come myn doens not look liek anyone elses look at the screen shot

---

### Post by YourSurrogateGod on 2006-06-07
[QUOTE=fog][COLOR="DarkOrchid"]**I solve this problem like this:**[/COLOR]
```
${color lightgrey}Temperatures:
CPU:$color ${i2c 9191-0290 temp 2}C${color grey} - MB:$color ${i2c 9191-0290 temp 1}C
```
because my temperatures are in:
**/sys/bus/i2c/devices/9191-0290/**

[IMG]http://img230.imageshack.us/img230/4301/screenshot3xj.jpg[/IMG]

Find where are your "temp 2" and "temp 1" and change this value: [COLOR="DarkOrchid"]9191-0290[/COLOR] with yours.

With this code you can see CPU and MB temperatures. :) 

[[IMG]http://img230.imageshack.us/img230/4159/screenshot10uj.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=screenshot10uj.jpg)[/QUOTE]
Umm... I have a problem with that. I don't have any files or directories in my /sys/bus/i2c/devices folder. Where do I go from now?

Also, how I can I make it so that conky starts up whenever I boot my pc?

---

### Post by u-blunt-2 on 2006-06-11
After reading most of this thread, it still isin't clear to me how to get conky working properly. I installed the latest version (1.4.2) correctly and get conky runnning ok, except that my desktop icons disappear whenever conky refreshes. 

I have tried everything except devilspie, is there any way to fix this bug without devilspie ? If not, how do I use devilspie to fix the problem (what commands should I use?). 

To get conky to run on startup, add "conky" in the startup tab in System -> Prefs -> Sessions

---

### Post by simplyw00x on 2006-06-11
> After reading most of this thread, it still isin't clear to me how to get conky working properly. I installed the latest version (1.4.2) correctly and get conky runnning ok, except that my desktop icons disappear whenever conky refreshes.

conky -o

---

### Post by u-blunt-2 on 2006-06-15
Doesn't running conky in it's own window sort of ruin all the fun ? I mean, might as well just run gnome-system-monitor... 
I installed conky to replace all the gdesklets on my desktop, but now I am thinking of switching to blackbox or even kde to pimp my desktop (and free-up some ressources). :-({|=

---

### Post by mustang on 2006-06-24
Would anyone mind posting the .deb for the latest conky?

Thanks!

---

### Post by simplyw00x on 2006-06-25
It's not decorated; the only problem is that it can be stealth-minimised by 'show desktop' or similar.

---

### Post by u-blunt-2 on 2006-06-26
I got the desktop icons to stop disappearing by adding this to .conskyrc
```
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints below sticky undecorated
```
This works well, however Compiz recognizes the "sticky" window as a normal one when I scale all open windows (quite unattractive). 

Another problem I have with conky-1.4.2, after a clean Dapper reinstallation, is recognizing Xft fonts. 
I get :
> Conky: Xft not enabled
when I run conky ( use_Xft is set to yes in my .conkyrc ). I did not get this before and the default font is bogus! 

EDIT: 
Fixed the problem. I did not compile with proper arguments and forgot to "make clean" before recompiling ;)
For those who get this problem, just go to the conky instalation directory and run 
```

make clean
./configure --prefix=/usr --enable-xft --enable-mpd --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime
make
sudo make install
checkinstall

```
You will need to have package "checkinstall" installed to run the last line of code.

---

### Post by Skoezie on 2006-10-16
How would I create a black transparent background just behind conky? Or just a black background and make it transparent with Beryl? So it is more viewable & usable with every background

---

### Post by bloodfilledwater on 2007-01-24
I have the newest version of conky, don't remember the exact version right off hand. The problem I am having, I use XGL and Beryl, during the startup, when conky starts it makes it's own window than it on top of all windows and the top tool bar. I've configured the .conkyrc file and set it so it doesn't set it's own window, but than after loading beryl at startup, it disappears. Any ideas? Also, I've configured the .conkyrc file to make the window below other windows and it has no effect.

---

### Post by DaMan on 2007-01-24
@bloodfilledwater - You need to load conky after beryl loads up... add the last instructions in the first post: [http://www.ubuntuforums.org/showthread.php?t=205865](http://www.ubuntuforums.org/showthread.php?t=205865)

Actually, there are some good instructions in that thread for getting conky working...
If someone needs it, I'll attach the newest version for conky.

---

### Post by wimac on 2007-01-24
I use conky with openbox it is great, highly recomend it.

---

### Post by bloodfilledwater on 2007-01-26
If I start conky after beryl has started, that fixes the issue with conky being on top of other Windows, but now I don't have graphs and it doesn't use my .conkyrc config file. Is there another file to configure?

---

### Post by loclarkey on 2007-02-08
Problem:  you are using KDE, and your desktop icons keep disappearing whenever you are using a double buffer to keep conky from flickering.  

Link: [Solution that I just used.]("http://briancarper.net/2006/08/25/transparent-conky-in-kde-part-2/")

Disclaimer - this is not my blog.  I still don't know why this solution works, but it does work, and I thought there should be a record of it on these forums.  You might have to install feh first:  sudo apt-get install feh

---

### Post by loclarkey on 2007-02-08
And I just realized that I posted this in a very old thread.  Hopefully it's still useful for later versions.:)

---

### Post by deltaandroid on 2008-06-07
I dont know if anyone mentioned it yet, and I can only speak for hardy, but

sudo apt-get install conky

:)

---

### Post by anonymous_user on 2008-11-26
Is it possible to list computer specs in conky?

For example I want to list the processor(s), motherboard, ram, disk(s), and video card(s).

---

