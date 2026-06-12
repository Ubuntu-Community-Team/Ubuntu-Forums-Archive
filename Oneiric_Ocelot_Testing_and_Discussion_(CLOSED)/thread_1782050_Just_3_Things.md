---
title: "Just 3 Things"
date: 2011-06-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2011-06-14
I like swapping between UNITY and GNOME SHELL .... just a few questions though .....

1 .... Gnome-Shell in the repositories .... can we have a fresh build of GNOME-SHELL - updated please as the last one is quite old.

[B][COLOR=Red]Does the old GNOME-SHELL have any problems - not sure if anyone has noticed though as nobody on here seems to mention it ....... or is that because they just cannot get it to run.
[/COLOR][/B]
2 .... Jhbuild for Gnome Shell .... is this ERROR being fixed or is it going to remain for some time to come .... as its the only thing stopping me doing a full new build of it.

[COLOR=Red][B]configure: error: libgdata-0.9 is not yet supported.  Use 0.8 instead   :(
[/B][/COLOR]
3 .... Is Gnome-Shell to be included in the Ubuntu repositories working properly for the 11.10 release ? 

[B][COLOR=Red]Does anybody know if this is going to be included ?


[http://ubuntuforums.org/showthread.php?p=10937537#post10937537](http://ubuntuforums.org/showthread.php?p=10937537#post10937537)
[/COLOR][/B]> 
Finally got a running version of [Gnome Shell in OO .... 11.10]("http://img18.imageshack.us/img18/4801/screenshot10wa.jpg") ....... kernel generic 3.0.0
as of today .... and .... [**compiz replace works**]("http://img232.imageshack.us/img232/3197/screenshot15k.jpg") ....

no blues flashes ....

The ***[video problems no longer exist]("http://www.youtube.com/watch?v=d4W1nr2vEi8")*** .... this is quickly done basic video using Gtk-Recordmydesktop
[B][COLOR=Red] 
[/COLOR][/B]

---

### Post by lucazade on 2011-06-14
Oneiric will ship GNOME 3.2 for final release in October, now we're using 3.0.1
This means we'll have an updated DE stack with new shell and panel.

---

### Post by cpatrick08 on 2011-06-14
> **23dornot23d said:**
> I like swapping between UNITY and GNOME SHELL .... just a few questions though .....

1 .... Gnome-Shell in the repositories .... can we have a fresh build of GNOME-SHELL - updated please as the last one is quite old.

[B][COLOR=Red]Does the old GNOME-SHELL have any problems - not sure if anyone has noticed though as nobody on here seems to mention it ....... or is that because they just cannot get it to run.
[/COLOR][/B]
2 .... Jhbuild for Gnome Shell .... is this ERROR being fixed or is it going to remain for some time to come .... as its the only thing stopping me doing a full new build of it.

[COLOR=Red][B]configure: error: libgdata-0.9 is not yet supported.  Use 0.8 instead   :(
[/B][/COLOR]
3 .... Is Gnome-Shell to be included in the Ubuntu repositories working properly for the 11.10 release ? 

[B][COLOR=Red]Does anybody know if this is going to be included ?
[/COLOR][/B]

you can add **ppa:ricotz/testing** to get a more update ppa he also has more ppa like a staging one to get a more update gnome-themes-standard  **ppa:ricotz/staging here is a link to his launchpad accound where you can find all of his ppas **[https://launchpad.net/~ricotz]("https://launchpad.net/%7Ericotz")

---

### Post by 23dornot23d on 2011-06-14
> 
Oneiric will ship GNOME 3.2 for final release in October, now we're using 3.0.1
This means we'll have an updated DE stack with new shell and panel.
Cheers for the Information.

> 
you can add **ppa:ricotz/testing** to get a more update ppa he also has more ppa like a staging one to get a more update gnome-themes-standard  **ppa:ricotz/staging here is a link to his launchpad accound where you can find all of his ppas **[https://launchpad.net/~ricotz]("https://launchpad.net/%7Ericotz")
I have the Ricotz PPA that is how I managed to get it to run .... but in the

**.local/share/gnome-shell/extensions**

The extension - I now have in there is just USERTHEMES just so it will run ok.



Thank you for this though as many USER's will not know the Ricotz PPA is there for their use .....
also the PPA for the Nvidia graphics will be needed too xorg-edgers
I would like to see that USER's can run this without adding PPA's though, if at all possible.

---

### Post by mc4man on 2011-06-14
> Does the old GNOME-SHELL have any problems - not sure if anyone has noticed though as nobody on here seems to mention it ....... or is that because they just cannot get it to run.
The current O supplied GS works fine here and is subject to many of the bugs affecting O when using unity
Using 3rd party extensions seems quite hit or miss.

> Is Gnome-Shell to be included in the Ubuntu repositories working properly for the 11.10 release ? 
I'm sure it will be working well at release, whether it will get any SRU'ed updates after that as easily as unity may don't know though doubt it will

---

### Post by 23dornot23d on 2011-06-14
> 
The current O supplied GS works fine here and is subject to many of the bugs affecting O when using unity
Using 3rd party extensions seems quite hit or miss.
Good to hear ..... what graphics card is that on and have you ever tried a jhbuild of it lately ?
( I would be interested in the results .... )


Would like to know if anybody else gets this .... one - not sure why I get it - 64 bit I use.

[COLOR=Red]**configure: error: libgdata-0.9 is not yet supported.  Use 0.8 instead   :sad:**[/COLOR]

**EXTENSIONS**
You may have seen this thread was moved out of desktop environments ..... 

[http://ubuntuforums.org/showthread.php?t=1754198&page=91](http://ubuntuforums.org/showthread.php?t=1754198&page=91)

It has most of the needed information to get the extensions working 

A lot of simple fixes are just version number checks against the metadata.json file for each one ...... change to 3.0 often sorts this out ........ as some still have 3.0.1 

..... more information is being added each day too to the thread but things I am seeing here to do with extensions
may have already been covered  .... which seems a shame .

---

### Post by jbicha on 2011-06-14
> **23dornot23d said:**
> 
Thank you for this though as many USER's will not know the Ricotz PPA is there for their use .....
also the PPA for the Nvidia graphics will be needed too xorg-edgers
I would like to see that USER's can run this without adding PPA's though, if at all possible.

Ricotz' staging PPA is not meant for users; that's why it's just a staging PPA for a development release. Oneiric is currently in early alpha status and is not meant for users; when it is released, you won't need to use a PPA to get the Nvidia proprietary driver working.

The Gnome Shell in the repositories is not old; it was released [3 weeks]("http://mail.gnome.org/archives/ftp-release-list/2011-May/msg00150.html") ago. And honestly, it's so early in the Gnome 3.2 cycle that Gnome 3.1 isn't that different than Gnome 3.0.

---

### Post by 23dornot23d on 2011-06-14
> 
Ricotz' staging PPA is not meant for users; that's why it's just a  staging PPA for a development release. Oneiric is currently in early  alpha status and is not meant for users; when it is released, you won't  need to use a PPA to get the Nvidia proprietary driver working.
I do understand this - the Ricotz PPa does say testing on it and I sort of guessed that might be the case ..... that was not one of the questions I asked but thank you for pointing this out ..... 

I would not advise users to use a 3 week old version of UNITY  .......

 saying its not out of date -  on day to day testing !!!

Not sure I follow what you are telling me here ..... is 3 weeks good for UNITY too is that how old that one is ?

______________________________________________________________

Its just that possibilities seem a little reduced at this moment in time ...... 

The jhbuild fails ..... on the error I mentioned ....

The version in the repos is 3 weeks old .... and does not work for me .......

So the only option was the Ricotz PPA and the Nvidia PPA ......  
for me at least as other users may have Gnome-Shell working ok ..... but if so on what systems ?



All I really asked for is - for a way forward to a problem .

---

### Post by jbicha on 2011-06-14
> **23dornot23d said:**
> saying its not out of date -  on day to day testing !!!

Not sure I follow what you are telling me here ..... is 3 weeks good for UNITY too is that how old that one is ?
...
The version in the repos is 3 weeks old .... and does not work for me .......

So the only option was the Ricotz PPA and the Nvidia PPA ......  
for me at least as other users may have Gnome-Shell working ok ..... but if so on what systems ?


I believe Gnome Shell in Oneiric works fine for everyone. I'd be happy to be pointed to bugs where it doesn't work.

jhbuild is for developers, not users. The error message tells you what your problem is: you need to install gdata 0.8 not 0.9. If you do find something not working in jhbuild, the Ubuntu forums aren't really the place to get that fixed; you should probably talk to the Gnome developers directly.

The version of Gnome Shell in the repositories is NOT out of date; it is the most recent released version. [See]("http://ftp.gnome.org/pub/GNOME/sources/gnome-shell/") for yourself.

---

### Post by 23dornot23d on 2011-06-14
Thanks for the link .....   ;)

Good to know we are up to date .... possibly my system then that is not compatible ......
with the new version  .... can't be though .... because if I run LXDE and plonk it on top of that
then it works ok .......


**FOR THE COMPILATION of Gnome Shell**
Have you tried installing the earlier version .....  0.8 .....

I have ..... and its still saying 0.9 is there - even though I have un installed the later one.

and used a deb package to put the older one into place ......

[COLOR=Red][B]Does it work ok for you .... if so could you please tell us all how did you do it ..... 
this is as good as any place for a solution ..... 
as it is Ubuntu that I would like to see it running on ......
[/B] [/COLOR]

> 
I believe Gnome Shell in Oneiric works fine for everyone. I'd be happy to be pointed to bugs where it doesn't work.
Interesting you should say this .... as the information gets hidden behind the Blue Smile of Death (BSOD)

and even in Looking Glass ..... it gives no real clues as to what has died .......

So it would surprise me to see a Bug other than we got this screen with the BLUE SMILE OF DEATH ON IT.

__________________________________________________________________

I would be very surprised if nobody has seen this ...... so what error do we report ?

and where is it stored please ..... then we can be of more help .... this message is of little use
and now it blocks the whole screen - does not show you that all the processes are running quite happily
in the background .......

[IMG]http://img8.imageshack.us/img8/9250/errorjh.jpg[/IMG]


Is the Adwaita theme on everyones computer now in 11.10 ? [%3A+Got+HUP+on+stdin+-+exiting&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=Ezt&channel=fs&source=hp&q=Adweita+theme+missing+launchpad+2011&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=5014d35bb6efb157&biw=1189&bih=544"]link to reports]("http://www.google.com/search?client=ubuntu&channel=fs&q=gnome-shell-calendar-server[2432)

Just out of interest as the last install I did said that this was not there .........

---

### Post by mc4man on 2011-06-14
> what graphics card is that on
As far as an install I have it on an older P4 w/nvidia (7800 AGP
Will put on a more recent laptop (nvidia) shortly, don't anticipate any issues

As far as the P4 it's fully updated with the exception of  - 
cairo - will not use a gl enabled cairo until nvidia mem issue is resolved
kernel - using 2.6.38-9 (patched), this particular hardware has issue w/ the 2.6.39 and 3.0, 100% chance of kernel panic
sudo - personal preference to use 1.7.2

As far as unity, at this point O is  using what's basically the natty version, (3.8.14), should be a significant upgrade in near future (A2?

---

### Post by 23dornot23d on 2011-06-14
Ok just been looking through [that thread on cairo]("http://ubuntuforums.org/showthread.php?t=1695326&page=3") and memory usage ..... seems it will 
get fixed here in 11.10 at some point ....

My Graphics card is a Nvidia 9300M GS 512 ...... 

I run cairo-dock and Gnome shell most of the time
and noticed if I swap to UNITY then the memory shoots up by around 200 Meg .....
also the Temp of the graphics card is 5 to 6 degrees higher than running everything
the same in Gnome Shell.

Obviously no Compiz though .... but does that account for around 200 meg of extra memory 
being used and a 5 degree Temp increase of the Graphics card ...... who knows.

My computer usually runs at around 58 to 60 degrees ..... 
with firefox and UNITY its been upto 77 degrees

Never gone above 70 in Gnome Shell ....... even with Firefox or any of my 3D renders ......

Running Gnome shell now on  3.0.0 Kernel  .... latest Graphics Driver 275.09.04 and its sitting steady at 60 degrees

---

### Post by mc4man on 2011-06-14
As far as extensions was trying out the set from 
git://git.gnome.org/gnome-shell-extensions
They all work with the exception of the apps menu on panel one
 The places dropdown ext.  seems useful - is currently subject to small bug in  desktop-files-utils that should hopefully be fixed soon, atm can be fixed user side if need be

---

### Post by 23dornot23d on 2011-06-15
Would be interesting to see the file contents of these directories to show what you have
running - it may help others too ...

home/.local/share/gnome-shell/extensions

usr/share/gnome-shell/extensions

> 
The places dropdown ext.  seems useful - is currently subject to small  bug in  desktop-files-utils that should hopefully be fixed soon, atm can  be fixed user side if need be


Is it a simple fix or something else .... do you have a link to the solution ?

---

### Post by mc4man on 2011-06-15
> **23dornot23d said:**
> Would be interesting to see the file contents of these directories to show what you have
running - it may help others too ...

Is it a simple fix or something else .... do you have a link to the solution ?
The ext. I got are from gnome.org, probably similar to what's in the ppa everyone uses
The one highlighted in screen doesn't work, have tried it from elsewhere, same thing
looking-glass just reports some generic error, not helpful

The one I do find useful is the places one - screen 2

As far as bug, it only occurs once you've opened a folder with anything else but nautilus from the right click > 'open with other appl..' > 'show other applications' menu - for example open a folder with a music player, or to just see open any folder with firefox.

after that there are 4 things so far affected - 
the places GS ext.
opening trash from unity launcher
opening any external drive from unity launcher
using firefox's  'open containing folder' from the download dialog box
They will use the app chosen from above instead of nautilus

The local fix is to open ~/.local/share/applications/mimeapps.list and edit this line in the _Default_ section

[Default Applications]
inode/directory=nautilus-folder-handler.desktop
to either
inode/directory=nautilus.desktop
or
inode/directory=nautilus-home.desktop

A system wide fix would be to edit /etc/gnome/defaults.list
and again edit the inode/directory= line  as above

The 3rd possible fix would be to recreate a proper nautilus-folder-handler.desktop in an applications dir.

Edit: the trash icon in unity launcher only seems to accept nautilus-folder-handler.desktop in the Default section, the other instances are fine with either of the 2 existing .desktops

---

### Post by 23dornot23d on 2011-06-16
Brilliant information .... explains a lot and have now put a link on the other thread so the
guys working on the extensions in the other version can see this too.

Loving it now .... and have a way forward ....  think that either looking glass or the error
reporting in Gnome-Shell needs a bit more documentation or better error reports.

Am now in a position to start to enjoy this again thanks for the information and screen shots too. ;)

---

