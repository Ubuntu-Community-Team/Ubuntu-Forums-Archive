---
title: "Enlightened Gnome: The Ultimate in Ubuntu Eye Candy"
date: 2005-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-08-04
[B]BIG EDIT: People have been asking me about performance. I have found that this Eye Candy trick makes things FASTER!!!! (both versions) The trade off is that its harder to use.

I have the E16 version of Enlightened Gnome running on a 128mb, 300mhz computer and IT FLYS![/B]

Poofyhairguy here, with my latest way to increase your desktop&#8217;s Eye Candy. Last time I brought you the Luminocity Guide, but all that showed me was that Luminocity is a toy.

**Disclaimer**

Today I bring you an update that can make your desktop prettier. Please note that only more advanced users should do this, I don&#8217;t want you to cry to me if everything breaks. I will use some tough terminology, if you don&#8217;t understand this howto is not for you. Consider yourself warned. All Most of the things can be undone.

**Introduction**

First I have to introduce the big players involved:

Smoon: his repository makes it all work. Thank him in your own way, but be sure to do it

Rasterman: The creator of Enlightenment that has magic code pour from his fingers. He is the only reason this works at all. 

Gnome Developers: Even though they are really getting behind the KDE people when it comes to Eye Candy (just my opinion) they at least give us ways to make up for it.

Here is the summary: Gnome is a desktop environment. Inside Gnome there are many programs that work together, and one of them is Metacity a Window Manager. To normal users, Metacity is the thing that &#8220;draws all of that black shit all over my desktop when I minimize apps.&#8221; Enlightenment is a Window Manager like Metacity, but it is not connected to Gnome (it was at one point).

For a better explanation of the differences, look here:

[http://slashdot.org/comments.pl?sid=157571&cid=13207087](http://slashdot.org/comments.pl?sid=157571&cid=13207087)

My howto guts Metacity from Gnome, and replaces it with Enlightenment. The advantage to this over just using Enlightenment is that GTK apps look WAY better, you can use (most) of the Gnome GUI tools to help you administer you system, and you can get access to all of your applications easier. Also (amazingly) I have found that after trading out Metacity for Enlightenment, everything feels FASTER. Prettier and faster, quite the combo.

**Decision Time**

Now you must make a decision: Am I going to use e17 or e16?

E17 is the unstable beta version that must be installed this way:

[http://www.ubuntuforums.org/showthread.php?t=46105&highlight=e17](http://www.ubuntuforums.org/showthread.php?t=46105&highlight=e17)

[COLOR=DarkRed]When E17 works inside of Gnome it has some incompatibilities (the nautilus desktop draws over the E17 tools, and E17 lacks virtual desktops or task switching that is compatible with Gnome). [/COLOR]

[COLOR=Navy]E16 is the stable version. It can easily be installed from the Universe in Synaptic. It works way better with Gnome, and the newest version has some neat tricks such as fake transparencies.[/COLOR]

To install E16: make sure the Universe repo is in your sources.list, then enter this command into normal terminal:

> sudo apt-get install enlightenment

Metacity--------------------E16--------------------E17
Ease of Use ---------------------------------------Looks

There is a chart. The reasons to pick E17: the title bar of Windows look like they are hit by lightening, fake drop shawdows are neat. The reasons to use E16: Still better than Metacity, GUI tools stay on top of Nautilus desktop, many Gnome tools work, has neat minimize trick.

**I suggest E16 the most, just because it works best with Gnome and because its not beta. **But for me...

I personally used E17 because the &#8220;lightening strikes the in focus task&#8221; is the eye candy I seeked. But on a friend&#8217;s machine I used E16 (Smoon&#8217;s E17 didn&#8217;t work for me that day) and he liked it. Overall it worked better with Gnome. But do what you want, this howto applies to both for the essential parts.

First thing to do in to install Enlightenment. Then log out of Gnome and log into whatever Enlightenment you choose to see if it works. If it doesn&#8217;t work, then you are using E17 and its broken today, try E16 or stop now. 

If you don't see the option, do this (thanks bored2k and bob mitch)

> sudo gedit /usr/share/xsessions/Enlightenment.desktop

Then put this in the new file:

> [Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application

Save the file as Enlightenment.desktop

MAKE SURE YOU CAN LOG INTO ENLIGHTENMENT!!!!!

Then after you affirm that you can, log out and go back to Gnome. Time to make the two work together.

**The Actual Trick**

You can thank mendicant for posting this info on the forum in the first place. Makes it all possible.

Put this in regular terminal:

> sudo cp /usr/share/gnome/default.session ~/.gnome2/session

Then this:

> sudo gedit ~/.gnome2/session

Look for this line:

> 1,RestartCommand=gnome-wm --sm-client-id default1

Change the like to look like this:

> 1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1

Save the file. Restart the X server (hit ctrl, alt, and backspace at the same time).

Then log back into Gnome. Enlightenment will start after a little while. Be very patient. The first time it took me a few minutes to log in., and my machine is pretty fast.

If it worked, you will be on your new desktop, using Enlightened Gnome.

**Suggestions**

If you used E16 start playing with the tools, get used to them. Also get to work on changing the default theme&#8230;.its pretty ugly to me. Luckily there are hundreds of E16 themes on the internet. 

If you used E17 you are faced with a problem. The Gnome desktop covers up the e17 tools. You have two choices for now:

1.	Use one of the other desktops. Move your mouse to the far right to find them. Go back to the first one for Pen Drives and CDs.

2.	Do what I did: install some gdesklet love. Gdesklets can be installed in Synaptic if you have added the backport repository. To install a gesklet, download the tar file from the site, start the gesklet program (under accessories) and drag and drop the tar file onto the gdesklet manager program.

3. Applications > System Tools > ConfiguratioN Editor > apps > nautilus > preferences > UNCHECK show desktop.  (thanks bored2k)

Here is the gdesklet I used:

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)

A few other notes about E17:

Since nothing on the default bottom Gnome Panel works anymore (except for trash)I just deleted the panel.

In the long run E16&#8217;s Engage:

[http://www.enlightenment.org/Applications/Engage/index.html](http://www.enlightenment.org/Applications/Engage/index.html)

Would be better than gdesklets. Anyone know how to add programs launchers to that thing? It can be installed from the Universe.

[B]To task switch in E17+Gnome, use hit the tab key and the alt key at the same time(MS Windows style). I have not found a better method yet. 
[/B]

Normal task switching works fine with E16.

Also, its nice to turn off the feature that kicks you to another desktop when you go to the far right. To do that, enter this command into the regular terminal:

> enlightenment_remote -edge-flip-set 0

After you do that, get to your other desktops by going through the upper right hand corner of your desktop with your mouse.

Here is the page with the other remote commands:

[http://get-e.org/User_Guide/English/_pages/3.1.html](http://get-e.org/User_Guide/English/_pages/3.1.html)

Also I really dislike the default E17 theme. I had this working in the past and gave up because I thought the default theme was blah. Then Stormy Eyes gave me the last piece to the puzzle:

[http://www.ubuntuforums.org/showpost.php?p=264459&postcount=32](http://www.ubuntuforums.org/showpost.php?p=264459&postcount=32)

I like the Slate theme best&#8230;.its very Gnomish. 

[http://get-e.org/Themes/E17/index.html](http://get-e.org/Themes/E17/index.html)

Well&#8230;That&#8217;s it for now. Enjoy Enlightened Gnome. Please leave suggestion in the thread and I&#8217;ll add them at my discretion.

Here is a screenshot:

[http://www.ubuntuforums.org/showpost.php?p=281853&postcount=1](http://www.ubuntuforums.org/showpost.php?p=281853&postcount=1)

But don't go by that. The coolness can't be shown in screenshots.

---

### Post by Stormy Eyes on 2005-08-04
[QUOTE=poofyhairguy]Also I really dislike the default E17 theme. I had this working in the past and gave up because I thought the default theme was blah. Then Stormy Eyes gave me the last piece to the puzzle:[/QUOTE]

Thanks for the mention. If you want to make program icons for Engage, you have to refer to [Section 3.3 of the E17 manual](http://get-e.org/User_Guide/English/_pages/3.3.html) for information on making EAP icon files, and then use the **entangle** utility (aka the Menu Editor in the E17 menu) to tell Engage which icons to show by default.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Stormy Eyes]Thanks for the mention. If you want to make program icons for Engage, you have to refer to [Section 3.3 of the E17 manual](http://get-e.org/User_Guide/English/_pages/3.3.html) for information on making EAP icon files, and then use the **entangle** utility (aka the Menu Editor in the E17 menu) to tell Engage which icons to show by default.[/QUOTE]

Thanks again Stormy. I'll play with that.

---

### Post by poofyhairguy on 2005-08-04
Lots of big edits......For most users I would recommend E16...

Man its fast! Look at these benchmarks:

[http://www.rasterman.com/index.php?page=News](http://www.rasterman.com/index.php?page=News)

Beats the crap out of Metacity.

---

### Post by Rob2687 on 2005-08-05
I did  'sudo apt-get install enlightenment' but there's no e16 in the login thing

---

### Post by bored2k on 2005-08-05
[QUOTE=Rob2687]I did  'sudo apt-get install enlightenment' but there's no e16 in the login thing[/QUOTE]
 [QUOTE=bobmitch]Create a file called e17.desktop in /usr/share/xsessions/
Add the following lines to this file:
```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application
```[/quote]Log out, tht should do it.

---

### Post by Rob2687 on 2005-08-05
[QUOTE=bored2k]Log out, tht should do it.[/QUOTE]

DIdn't work initially but so i checked the file I create and tried to take ownership of it,,,didn't work either so I was playing around with chmod and chown.
Then the file I created magically disappeared and a new file called Enlightenment.desktop magically appeared.

Weird  :-?

and that's my story :P

---

### Post by poofyhairguy on 2005-08-05
Here is another thread with info on this neat new trick.

[http://www.ubuntuforums.org/showthread.php?t=54478](http://www.ubuntuforums.org/showthread.php?t=54478)

---

### Post by darkmatter on 2005-08-05
[QUOTE=poofyhairguy]My howto guts Metacity from Gnome, and replaces it with Enlightenment. The advantage to this over just using Enlightenment is that GTK apps look WAY better, [/QUOTE]

Oh...Really...
[http://ubuntuforums.org/gallery/showimage.php?i=643&c=4](http://ubuntuforums.org/gallery/showimage.php?i=643&c=4)

[http://ubuntuforums.org/gallery/showimage.php?i=644&c=4](http://ubuntuforums.org/gallery/showimage.php?i=644&c=4)

It's amazing what preloading the gnome-settings-daemon can do... ;-)

---

### Post by kittcankitt on 2005-08-05
If I made a copy of my current ~/.gnome2/session file and put it somewhere else and decided to go back to it, would it be fair enough to say all I have to do is replace the new one with my backup and log back into gnome?  I only ask because I am currently using openbox inside gnome and find it quite responsive compared to metacity.  I would like to try e16 and see if I can get even more of a kick out my box.

Thanks and nice how-to

KCK

I renamed the the first session and created the new one...played with e16 for a bit and decided to see if I could return to the original and all went well.  For now I'll stick with openbox til I can convince the missus to get used to e16.  At least now all I have to do is re-rename my e16session.

---

### Post by super on 2005-08-05
[QUOTE=darkmatter]
It's amazing what preloading the gnome-settings-daemon can do... ;-)[/QUOTE]

yup! gotta run the settings daemon. :razz: 

also, engage has a taskbar and systray, you just have to pass the option when you start it.

and if you are using e16 many of the e17 apps will work (engage, eclair, entrance, etc..) :)

---

### Post by poofyhairguy on 2005-08-05
[QUOTE=kittcankitt]If I made a copy of my current ~/.gnome2/session file and put it somewhere else and decided to go back to it, would it be fair enough to say all I have to do is replace the new one with my backup and log back into gnome?  [/QUOTE]

Yes

---

### Post by poofyhairguy on 2005-08-05
[QUOTE=darkmatter]Oh...Really...
[http://ubuntuforums.org/gallery/showimage.php?i=643&c=4](http://ubuntuforums.org/gallery/showimage.php?i=643&c=4)

[http://ubuntuforums.org/gallery/showimage.php?i=644&c=4](http://ubuntuforums.org/gallery/showimage.php?i=644&c=4)

It's amazing what preloading the gnome-settings-daemon can do... ;-)[/QUOTE]

You could do it that way. Log into enlightenment and start gnome-settings-daemon, gnome-volume-manager, etc.

But I find it easier to just shove Enlightenment into Gnome.

---

### Post by twigsby on 2005-08-05
Nice guide, but doing this has crippled my games. Single digit frame rates and 4 fps in glxgears.   :-#

---

### Post by poofyhairguy on 2005-08-05
[QUOTE=twigsby]Nice guide, but doing this has crippled my games. Single digit frame rates and 4 fps in glxgears.   :-#[/QUOTE]

4. LOL. Did you try to use E16 or E17?

---

### Post by twigsby on 2005-08-05
E17 . I guess I'll go try 16.  \\:D/

---

### Post by plasmatonic on 2005-08-05
[QUOTE=darkmatter]Oh...Really...
[http://ubuntuforums.org/gallery/showimage.php?i=643&c=4](http://ubuntuforums.org/gallery/showimage.php?i=643&c=4)

[http://ubuntuforums.org/gallery/showimage.php?i=644&c=4](http://ubuntuforums.org/gallery/showimage.php?i=644&c=4)

It's amazing what preloading the gnome-settings-daemon can do... ;-)[/QUOTE]

How can I do so automatically?

---

### Post by darkmatter on 2005-08-05
> **super]also, engage has a taskbar and systray, you just have to pass the option when you start it.[/quote]

Yes, I know. :) I just don't use them, far to much clutter...
Besides, I don't need no stinking systray :razz: (it's a little...uhh...ugly atm. disrupts the flow of my desktop  said:**
> How can I do so automatically?

Just create .eap files fore the services you want (gnome-settings-daemon, gnome-volume-manager, etc.) and place them in ~/.e/e/applications/startup 

Then create a .order file in the same directory listing the .eap's in the order you want them to run, (eg: gnome-settings-daemon.eap)

You can also create .eap's for easy access to configuration options such as gnome-theme-manager, etc. for your menu, (or ibar, or whatever) as this allows greater control over the appearance of Gtk+ apps (i have settings for my fonts, theme manager (gtk + icons), and several other useful features in a 'GNOME' submenu)

One of the few things I haven't figured out yet is how to get terminal free sudo access to apps like synaptic and the update manager from within e.

---

### Post by darkmatter on 2005-08-05
On a side note, you can also create more than one set of .eap files for the programs installed on your system with different icon sets, place a complete set in a folder bearing the name you want, then after they are created, turn ~/.e/e/applicationa/all into a symlink to the set you want to use. Then you can change the icons for ibar, engage, ibox, the menu by just editing the symlink and restarting enlightenment.

For example, to change from your standard set (lets say gant) to an alternative (graphite), just edit the symlink for to point to the directory with the graphite eaps, and restart)

A nice little example of the power of symlinking. :)

---

### Post by plasmatonic on 2005-08-05
Thanks for the help. <3 the graphical EAP tool  :)

---

### Post by darkmatter on 2005-08-05
[QUOTE=plasmatonic]Thanks for the help. <3 the graphical EAP tool  :)[/QUOTE]

Yes and no. Use the method  described here [http://www.ubuntuforums.org/showpost.php?p=263550&postcount=135](http://www.ubuntuforums.org/showpost.php?p=263550&postcount=135)
for generating the startup services .eap's

The graphical tool works fine for most apps (the windowed type), but the the method linked above is a much faster way to get startup services enabled.

---

### Post by Neo40 on 2005-08-05
Hi,

After playing a bit with Gnome and E-17, I wanted my normal Gnome back. So I changed  in~/.gnome2/session the line with: 
 1,RestartCommand=gnome-wm --sm-client-id default1

And I changed Applications > System Tools > ConfiguratioN Editor > apps > nautilus > preferences > CHECK show desktop

The thing is Nautilus does not work anymore! If I open-up a terminal and I type "nautilus" nothing is happenning. :(
I tried to reinstall nautilus but did not help.

Any suggestion?
Thanks

---

### Post by seanroth on 2005-08-06
Wow, this is really cool. It definitely sped up performance.  :grin:

---

### Post by Hanj on 2005-08-06
Nice howto! I ran in to some problems though:

I can't find engage in synaptic. Is there some repo I must add? 

Also, how can I change the font size (for menus, window titles etc) in E16? Or is the font size part of the theme? All themes I have tried have fonts that are virtually impossible to read at a high resolution.

EDIT: Oh, and it's supposed to be "sudo gedit /usr/share/xsessions/enlightenment.desktop", right? Doing "sudo gedit /usr/share/xsessions/" produces an error since you are trying to edit a folder.

---

### Post by jnoreiko on 2005-08-06
I'm probably too much of n00b to try this, because I'm already stuck on this bit:

 log out of Gnome and log into Enlightenment

How do you log into Enlightenment?

When you say Enlightenment? takes a while to load, is that the first time you run it, or on every boot?

---

### Post by plasmatonic on 2005-08-06
[QUOTE=jnoreiko]I'm probably too much of n00b to try this, because I'm already stuck on this bit:

 log out of Gnome and log into Enlightenment

How do you log into Enlightenment?

When you say Enlightenment? takes a while to load, is that the first time you run it, or on every boot?[/QUOTE]

Simply click the Sessions button and choose Enlightenment before you login. If its not listed  than you will need to:

```
 sudo gedit /usr/share/xsessions/enlightenment.desktop
``` 

and paste
```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application 
``` 

into it as per the directions of the original post.

---

### Post by Nightblade on 2005-08-06
What's the diff between e16 and e17? Because I have some serious issues with tools in e17.

---

### Post by Omnios on 2005-08-06
How about a seperate E-16 thread with a bit of a how to specificly for E-16 Im not going to try E-17 not comfortable anouph yet to try that yet but am very interested in the recomended E-16 wich I think a lot of people will want to try. Basicly want to set it up so I still have access to regular gnome wich should be ok by adding a new manager entry I hope. Also I wan't to know how compatable it is with gnome there are certain features I realy don't want to do without.

---

### Post by Omnios on 2005-08-06
I think you may have stumbled onto something, knowledge of what is fast and "good" may play a long way to making a desktop that runs well on borderline spec and ram systems. Replacing resource hogs with streamlined components like E-16 may make for an interesting How to and possibly eventualy a version. Im definatly going to try E-16 as soon as I finish reading up on it, thanks for the how to's.

 Casts a Ubber Vote!
cheers!

---

### Post by jnoreiko on 2005-08-06
[QUOTE=plasmatonic]```
 sudo gedit /usr/share/xsessions/enlightenment.desktop
``` 
[/QUOTE]

Thanks :)
But there's a mistake in the original post: it says

sudo gedit /usr/share/xsessions/

---

### Post by NMUrugbysteve on 2005-08-06
Ok, I've gotten e16 install and running quite well within gnome. But now when i try to load synaptic, x freezes and I have to ctrl+alt+F1 and killall5 to get back into anything, anyone have any hints on this? I"m running on an thinkpad R51.

---

### Post by varunus on 2005-08-06
Excellent howto!  I love Enlightened GNOME!  Its a lot more responsive, and the eye-candy is great.

I did something the guide doesn't mention; I installed enlightenment DR16 from [http://packages.debian.org](http://packages.debian.org) instead of from Ubuntu's repositories.  They have E16.7 instead of E16.6 like Ubuntu does, which gives you the very sexy Winter theme.

I looked at the dependencies for E16.7 and E16.6, they're identical.  So I just had to get the enlightenment and enlightenment-data packages from Debian.  Its probably in fact a better idea to do this, since E16.7 fixes some bugs...

Has anyone else tried this out?  It hasn't broken for me at all...

Hehe, I also made a quick clearlooks theme to match Winter more or less by using some color changing...If anyone wants it, I can post it.  Though, I don't know how popular winter is among you guys.

---

### Post by darkmatter on 2005-08-06
You can also grab the Winter gtk2 theme for E16/E17 from [http://www.rephorm.com/rephorm/design/winter/](http://www.rephorm.com/rephorm/design/winter/) ;-)

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=NMUrugbysteve]Ok, I've gotten e16 install and running quite well within gnome. But now when i try to load synaptic, x freezes and I have to ctrl+alt+F1 and killall5 to get back into anything, anyone have any hints on this? I"m running on an thinkpad R51.[/QUOTE]

Try this command in a regular terminal

> 
gksudo synaptic


tell me if it works.

---

### Post by poofyhairguy on 2005-08-06
> **varunus]Excellent howto!  I love Enlightened GNOME!  Its a lot more responsive, and the eye-candy is great.

I did something the guide doesn't mention said:**
> http://packages.debian.org[/url] instead of from Ubuntu's repositories.  They have E16.7 instead of E16.6 like Ubuntu does, which gives you the very sexy Winter theme.

I looked at the dependencies for E16.7 and E16.6, they're identical.  So I just had to get the enlightenment and enlightenment-data packages from Debian.  Its probably in fact a better idea to do this, since E16.7 fixes some bugs...

Has anyone else tried this out?  It hasn't broken for me at all...

Hehe, I also made a quick clearlooks theme to match Winter more or less by using some color changing...If anyone wants it, I can post it.  Though, I don't know how popular winter is among you guys.

I'm glad you like it. I don't think I'll advise people to install these things from Sid....mixing Debian packages and Ubuntu are never the best idea to me. If yall want, we can ask jdong for a backport of these two packages.

Any takers?

---

### Post by NMUrugbysteve on 2005-08-06
[QUOTE=poofyhairguy]Try this command in a regular terminal



tell me if it works.[/QUOTE]
 Nope, still freezes up. So far i've figured out a workaround where I open another program that requires root and I type my password then just load synaptic. Has anyone else had this prob?

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=Nightblade]What's the diff between e16 and e17? Because I have some serious issues with tools in e17.[/QUOTE]

Wikipedia has the answers:

[http://en.wikipedia.org/wiki/Enlightenment_%28X_window_manager%29](http://en.wikipedia.org/wiki/Enlightenment_%28X_window_manager%29)

---

### Post by varunus on 2005-08-06
[QUOTE=poofyhairguy]I'm glad you like it. I don't think I'll advise people to install these things from Sid....mixing Debian packages and Ubuntu are never the best idea to me. If yall want, we can ask jdong for a backport of these two packages.

Any takers?[/QUOTE]

I checked the dependencies just to make sure; E16.7 didn't require anything above what E16.6 did.  Seemed it was just an internal enlightenment bugfix and theme-add thing.  It seems to work just fine, so maybe jdong maybe could just add it to ubuntu.  (The directory structure was the same too, I checked and did my homework so that I knew I wasn't breaking anything.)

Just using the winter theme would be fine for me too, so no need to advise anyone to use Sid, since winter is available separately (thanks a bunch for that site, darkmatter!).

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=NMUrugbysteve]Nope, still freezes up. So far i've figured out a workaround where I open another program that requires root and I type my password then just load synaptic. Has anyone else had this prob?[/QUOTE]

Thats a weird bug. Anyone else have it?

---

### Post by Sparkster on 2005-08-07
[QUOTE=poofyhairguy]Thats a weird bug. Anyone else have it?[/QUOTE]
 Hey guys... this whole 'enlightened gnome' tricked me into trying it :P
But...i ran into some problems :( , right after installing it...

... i ran the whole 'sudo apt-get install enlightment' thingie. Looked like it worked out just fine.

Then, I gedited my /usr/share/xsessions/ to properly show Enlightment at the gdm start. All good so far.

Then, I logged into it using my login info...screen went blank...then I got a 'please wait' cursor for a few seconds...
...then I got bounced off right into gdm login again! :(

Logged back into GNOME and everything was just as before.

Since you guys really pointed out that if you can't log into enlightment, STOP...I freaked out and desisted :P

What could be what's preventing me to log into enlightment? :( Im really puzzled, cant find any cases like mine around :P

---

### Post by Kyral on 2005-08-07
I love this, but a couple questions

Is it possible to import my keybindings from MetaCity into E16? How?

How do I install themes?

I run the starterbar desklet and sometimes when I move stuff over it, the little area where the Desklet has "reserved" for movement space covers the window I moved over it. Is there anyway to like run GDesklets so that doesn't happen?

---

### Post by PMO6022 on 2005-08-07
First off, thanks for the great How To!  I had been using e16 by its self, but this enlightenment/gnome combo is the best of both worlds.  

In addition, I would like to second the request to have e16.7 backported.  That version is actually in debian *stable* so I see no reason why it shouldn't be in ubuntu.  Maybe now with this how-to there will be some additional interest in a backport.

---

### Post by Omnios on 2005-08-07
Um dumb question but how can I set this up so there is a seperate entry to log into gnome and E-gnome. I still want to be able to log into regular gnome. That will allow me to play around with E-16 for a while and still have gnome if I need to lol. Figure I have to make a entry with enlightenment set up with gnome. Man 10 pages already maybe you can edit the fist post with all the goodies?

---

### Post by kelean on 2005-08-07
[QUOTE=Omnios]Um dumb question but how can I set this up so there is a seperate entry to log into gnome and E-gnome. I still want to be able to log into regular gnome. That will allow me to play around with E-16 for a while and still have gnome if I need to lol. Figure I have to make a entry with enlightenment set up with gnome. Man 10 pages already maybe you can edit the fist post with all the goodies?[/QUOTE]
 Thank you for all the work that went into this enlightend gnome thread.  I have E-16 setup on a P-3 450 and it flys.  This is the fastest setup on this computer.  Now I just need to get use to and do some playing.  Awesome job guys!!!!!!!

thank you Kelean

---

### Post by Omnios on 2005-08-07
Sweet looking real good so far and thanks for the great info we definatly need more stuff like this thanks for taking the time to do it. You might want to look into Phluid found it in synaptic but havent tryed it yet as it did not set up a session in login. Ill get around to that later after I finish playing with E-16, Its supposedly a light weight wm based on Enlightenment but havent looked it over yet said it had E type transparecies. 

 Anyways 
 
 Im trying to figure out how to do the following and still be able to log into regular Gnome.
 
 The Actual Trick

You can thank mendicant for posting this info on the forum in the first place. Makes it all possible.

Put this in regular terminal:

Quote:
sudo cp /usr/share/gnome/default.session ~/.gnome2/session


Then this:

Quote:
sudo gedit ~/.gnome2/session


Look for this line:

Quote:
1,RestartCommand=gnome-wm --sm-client-id default1


Change the like to look like this:

Quote:
1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1


Save the file. Restart the X server (hit ctrl, alt, and backspace at the same time).

Then log back into Gnome. Enlightenment will start after a little while. Be very patient. The first time it took me a few minutes to log in., and my machine is pretty fast.

If it worked, you will be on your new desktop, using Enlightened Gnome.

 Not shure if it changes gnome as there is a default and a gnome log in is it possible to make a seperate Gnome log in with the regular stuff?

---

### Post by krusbjorn on 2005-08-07
I guess I'm the only one getting this problem?
> 
lyle@mays:~$ sudo apt-get install enlightenment
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate

lyle@mays:~$ sudo apt-get install enlightenment-data
Reading package lists... Done
Building dependency tree... Done
Package enlightenment-data is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment-data has no installation candidate
lyle@mays:~$


Been googling for a while but havent found anything. Here's my sources.lst

> #deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/

Edit: Btw, i got the .deb package from the enlightenment site, but it would still be fun to know what i am doing wrong here ;)

---

### Post by Omnios on 2005-08-07
K got it to work and it does work. Now I have to fiddle around with it and find out what I can do with it.

---

### Post by cullan on 2005-08-07
Thanks for the guide. One question: does anyone else have a question mark show up in engage all the time? I know this happens when you run something that doesn't have an icon file setup but is there a way to find out what program it is and make an icon for it or maybe get it to not show up. It doesn't show up when I run plain enlightenment so I am guessing that some program is running with gnome. TIA

---

### Post by Lux Perpetua on 2005-08-07
[QUOTE=poofyhairguy]Thats a weird bug. Anyone else have it?[/QUOTE]
Yes, I had the same problem.

---

### Post by da_unruled on 2005-08-08
[QUOTE=kittcankitt]If I made a copy of my current ~/.gnome2/session file and put it somewhere else and decided to go back to it, would it be fair enough to say all I have to do is replace the new one with my backup and log back into gnome?  I only ask because I am currently using openbox inside gnome and find it quite responsive compared to metacity.  I would like to try e16 and see if I can get even more of a kick out my box.

Thanks and nice how-to

KCK

I renamed the the first session and created the new one...played with e16 for a bit and decided to see if I could return to the original and all went well.  For now I'll stick with openbox til I can convince the missus to get used to e16.  At least now all I have to do is re-rename my e16session.[/QUOTE]
 do you have a guide in case someone (eg me) wants to revert back to metacity? (default gnome)?

man Im having problems with installing different window managers...
I did apt-get install xfce, it installed, it doesnt appear in the login/sessions button thing. Same goes for enlightenment. What gives?  ](*,)  ](*,)

---

### Post by zarathustra on 2005-08-08
> Look for this line:

Quote:
1,RestartCommand=gnome-wm --sm-client-id default1

The closest I have is:

> 1,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-WYG2EA/ --sm-client-id

Is there something wrong with my installation? That line isn't in the file any where.

---

### Post by Pinguvin on 2005-08-08
i followed this guided and installed E16 and put it into Gnome but it was slow as F... any idea why?  :|

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=Pinguvin]i followed this guided and installed E16 and put it into Gnome but it was slow as F... any idea why?  :|[/QUOTE]


Hmm....is normal Enlightenment slow? 

(as in when you log out of Gnome and log into enlightenment)

What are your specs.

---

### Post by Pinguvin on 2005-08-08
Normal Enlightenment is also slow yes. I had the same problem with Fluxbox wich is weird since everything worked perfectly in Gentoo (actually Vidalinux)...so my specs should not be the problem..

---

### Post by zarathustra on 2005-08-08
Should I just replace that line with the new one anyway? I don't want to break my machine.

---

### Post by spacemonkey on 2005-08-08
I'm experiencing some strange results.  First, gdesklets and eterm's transparency is no longer transparent, it is just black.  Also, when I change virtual desktops, or when I first log in, I get wierd distortions on the screen.  Here is a screenshot:

[http://compy.gotdns.com/bfiser/e16.png](http://compy.gotdns.com/bfiser/e16.png) 

oh, and I'm running E16

---

### Post by mbirkis on 2005-08-08
hey! thanks for a nice guide... didn't like enlightment in gnome... but i now use e16 without gnome and it is great! and real fast on my 3000+ 64bit

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=zarathustra]Should I just replace that line with the new one anyway? I don't want to break my machine.[/QUOTE]

Everything in my guide can be undone.

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=spacemonkey] Also, when I change virtual desktops, or when I first log in, I get wierd distortions on the screen. [/QUOTE]

I think E16 has its own compositor, so it steals that away from the gdesklets. You have to run xcompmgr I think. Or use E17, works for me in E17.

How long do the distortions last?

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=Pinguvin]Normal Enlightenment is also slow yes. I had the same problem with Fluxbox wich is weird since everything worked perfectly in Gentoo (actually Vidalinux)...so my specs should not be the problem..[/QUOTE]


Hmmmm...well if E won't work, my guide can't work. Sorry.

---

### Post by ephman on 2005-08-08
awesome installed like a charm... now all i have to do is figure out how to add apps to the desktop and things like that :)

thanks,
ephman

---

### Post by spacemonkey on 2005-08-08
the distortions last until they are covered up by a window, then they go away.  I'll give E17 a shot tonight or tomorrow.

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=spacemonkey]the distortions last until they are covered up by a window, then they go away.  I'll give E17 a shot tonight or tomorrow.[/QUOTE]

That happens when I run xcompmgr. That is an essential problem with Xorg.

---

### Post by Stratus on 2005-08-08
[QUOTE=zarathustra]The closest I have is:

Is there something wrong with my installation? That line isn't in the file any where.[/QUOTE]

I had the same thing, just add the line under the last line that starts with 1, and log out then back in again. Worked for me  :wink:

---

### Post by srt4play on 2005-08-09
[QUOTE=krusbjorn]I guess I'm the only one getting this problem?
Quote:
lyle@mays:~$ sudo apt-get install enlightenment
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
enlightenment-data
E: Package enlightenment has no installation candidate

lyle@mays:~$ sudo apt-get install enlightenment-data
Reading package lists... Done
Building dependency tree... Done
Package enlightenment-data is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment-data has no installation candidate
lyle@mays:~$

[/QUOTE]

Nope, I'm having the same problem! Did you figure it out yet??

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=srt4play]Nope, I'm having the same problem! Did you figure it out yet??[/QUOTE]

Do you have the universe enabled?

[https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29](https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29)

Did you do

sudo apt-get update

first?

---

### Post by srt4play on 2005-08-09
[QUOTE=poofyhairguy]Do you have the universe enabled?

[https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29](https://wiki.ubuntu.com/UniversePackages?highlight=%28universe%29)

Did you do

sudo apt-get update

first?[/QUOTE]

Yes.

---

### Post by krusbjorn on 2005-08-09
[QUOTE=srt4play]Nope, I'm having the same problem! Did you figure it out yet??[/QUOTE]

Nope, i have no idea how to solve it :P

---

### Post by srt4play on 2005-08-09
krusbjorn -

I see you have the E17 repository (by swoon I think it is) in your sources.list file as do I.  If you followed the howto on getting E17, then you need to delete the /etc/apt/preferences file that defines a higher priority for E17.  I did this and I pulled down E16 with no problem.

---

### Post by varunus on 2005-08-09
EDIT:  Now that I see the above post, that's probably the problem...so undoing the pin step should make E work without the below files...Ah well, already uploaded them.  :) 

Enlightenment isn't showing up in the repositories for you guys?  That's really weird..

I'm putting enlightenment, enlightenment-data, and all their dependencies that don't come with Ubuntu (I think) up at the following URL, feel free to grab them from there (these are the hoary versions poofyhairguy, so don't worry that i'm telling other ppl to use sid packages :) ).  Just download all of the .deb packages, open a terminal, CD to the directory that they're in, and type:
```
sudo dpkg -i *.deb
``` 

Then follow poofyhairguy's howto, but without any apt-get steps.

Here you go:
[http://web.ics.purdue.edu/~ajgore/](http://web.ics.purdue.edu/~ajgore/)

---

### Post by NMUrugbysteve on 2005-08-09
Ok, I've established that my problem is based on window ordering somehow.
When I open synaptic with a window open, X freezes. When all windows are minimized, it starts right up.

---

### Post by krusbjorn on 2005-08-09
[QUOTE=srt4play]krusbjorn -

I see you have the E17 repository (by swoon I think it is) in your sources.list file as do I.  If you followed the howto on getting E17, then you need to delete the /etc/apt/preferences file that defines a higher priority for E17.  I did this and I pulled down E16 with no problem.[/QUOTE]

Oh, I think i followed that guide a long time ago without completeing it successfully. I will try this in a couple of days, when i get home from my gf. Thanks a lot for the tip!

---

### Post by ephman on 2005-08-09
hi,

i know it's not this "how to's" issue but as a sidenote has anybody had a right click issue not showing apps occur?

thanks,
ephman

---

### Post by bored2k on 2005-08-09
[QUOTE=ephman]hi,

i know it's not this "how to's" issue but as a sidenote has anybody had a right click issue not showing apps occur?

thanks,
ephman[/QUOTE]
 I have. Have not found a cure of it though, but since the gnome-panel is there, it doesn't bother me.

---

### Post by ephman on 2005-08-09
i'm sorry i made a mistake, it's supposed to be the left mouse button that produces the menu for apps.  when i click it nothing appears.  also i don't think i get the gnome panel?

thanks,
ephman

---

### Post by bored2k on 2005-08-09
[QUOTE=ephman]i'm sorry i made a mistake, it's supposed to be the left mouse button that produces the menu for apps.  when i click it nothing appears.

thanks,
ephman[/QUOTE]
 Me too.. lol. I meant the left mouse click :roll: (it's confusing) !

---

### Post by ephman on 2005-08-09
i don't see the gnome panel either or else i wouldn't be bothered by it as well.  i installed 16  

thanks,
ephman

---

### Post by bored2k on 2005-08-09
[QUOTE=ephman]i don't see the gnome panel either or else i wouldn't be bothered by it as well.  i installed 16  

thanks,
ephman[/QUOTE]
 Did you follow the guide ? The guide incorporated Enlightenment into GNOME. That's the whole point. If you followed it and you can't see it, run gnome-panel.

---

### Post by zarathustra on 2005-08-09
[QUOTE=Stratus]I had the same thing, just add the line under the last line that starts with 1, and log out then back in again. Worked for me  :wink:[/QUOTE]
 OK I tried this, but all it's done is boot up into a blank desktop. I waited for a bit and it did load the terminal and a blank document in gedit :s

Edit: it also appears to have deleted the line I put in.

---

### Post by ephman on 2005-08-09
[QUOTE=bored2k]Did you follow the guide ? The guide incorporated Enlightenment into GNOME. That's the whole point. If you followed it and you can't see it, run gnome-panel.[/QUOTE]

silly me i should have read the rest.  go figure, my bad.

thank you,
ephman

---

### Post by juanej on 2005-08-09
Im getting some problems with E16 + Winter theme:
-My desktop buttond doesnt work anymore
-I cant minimize azureus to systray

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=juanej]Im getting some problems with E16 + Winter theme:
-My desktop buttond doesnt work anymore
-I cant minimize azureus to systray[/QUOTE]

The "show desktop" applet does not work in E16.

---

### Post by spacemonkey on 2005-08-09
What about enlightenment with Nvidia TwinView enabled and dual monitors?  It creates 8 virtual desktops, 4 for each monitor, and if a window is in one monitor, and my mouse is in the other, I am unalbe to alt tab to that window.  This is really annoying.  In gnome with metacity it treated the two monitors as one screen.  Any suggestions on how to fix this?

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=spacemonkey]What about enlightenment with Nvidia TwinView enabled and dual monitors?  It creates 8 virtual desktops, 4 for each monitor, and if a window is in one monitor, and my mouse is in the other, I am unalbe to alt tab to that window.  This is really annoying.  In gnome with metacity it treated the two monitors as one screen.  Any suggestions on how to fix this?[/QUOTE]


Turn of the some of the virtual desktops? When I get home I will face the same issue, so I WILL have an answer soon enough.

---

### Post by ephman on 2005-08-09
if i decide to revert back to metacity, how would i do that?

thanks,
ephman

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=ephman]if i decide to revert back to metacity, how would i do that?

thanks,
ephman[/QUOTE]

reopen the text file, delete the:

> --default-wm enlightenment


part.
log in and log out.

---

### Post by ephman on 2005-08-09
[QUOTE=poofyhairguy]reopen the text file, delete the:




part.
log in and log out.[/QUOTE]

just tried it... didn't work.  here's the file. 

# This is the default session that is launched if the user doesn't
# already have a session.
# The RestartCommand specifies the command to run from the $PATH.
# The Priority determines the order in which the commands are started
# (with Priority = 0 first) and defaults to 50.
# The id provides a name that is unique within this file and passed to the
# app as the client id which it must use to register with gnome-session.
# The clients must be numbered from 0 to the value of num_clients - 1.

[Default]
num_clients=9
0,id=default0
0,Priority=0
0,RestartCommand=gnome-smproxy --sm-client-id default0
1,id=default1
1,Priority=10
1,RestartCommand=gnome-wm --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=gnome-panel --sm-client-id default2
3,id=default3
3,Priority=40
3,RestartCommand=nautilus --no-default-window --sm-client-id default3
4,id=default4
4,Priority=60
4,RestartCommand=gnome-cups-icon --sm-client-id default4
5,id=default5
5,Priority=40
5,RestartCommand=gnome-volume-manager --sm-client-id default5
6,id=default6
6,Priority=40
6,RestartCommand=magicdev --sm-client-id default6
7,id=default7
7,Priority=50
7,RestartCommand=vino-session --sm-client-id default7
8,id=default8
8,Priority=50
8,RestartCommand=update-notifier --sm-client-id default8


thanks,
ephman

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=ephman]just tried it... didn't work.  here's the file. 

# This is the default session that is launched if the user doesn't
# already have a session.
# The RestartCommand specifies the command to run from the $PATH.
# The Priority determines the order in which the commands are started
# (with Priority = 0 first) and defaults to 50.
# The id provides a name that is unique within this file and passed to the
# app as the client id which it must use to register with gnome-session.
# The clients must be numbered from 0 to the value of num_clients - 1.

[Default]
num_clients=9
0,id=default0
0,Priority=0
0,RestartCommand=gnome-smproxy --sm-client-id default0
1,id=default1
1,Priority=10
1,RestartCommand=gnome-wm --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=gnome-panel --sm-client-id default2
3,id=default3
3,Priority=40
3,RestartCommand=nautilus --no-default-window --sm-client-id default3
4,id=default4
4,Priority=60
4,RestartCommand=gnome-cups-icon --sm-client-id default4
5,id=default5
5,Priority=40
5,RestartCommand=gnome-volume-manager --sm-client-id default5
6,id=default6
6,Priority=40
6,RestartCommand=magicdev --sm-client-id default6
7,id=default7
7,Priority=50
7,RestartCommand=vino-session --sm-client-id default7
8,id=default8
8,Priority=50
8,RestartCommand=update-notifier --sm-client-id default8


thanks,
ephman[/QUOTE]

Then lets delete the file:

>  sudo rm ~/.gnome2/session

(don't worry, you made it in the howto, you can delete it).

---

### Post by spacemonkey on 2005-08-09
I've discovered more problems:

using compositing, I still can't get anything to be transparent.  gdesklets, when I don't have it set to use xcompmgr for transparency, it just shows the gnome background, when I do have it set to use xcompmgr, it is solid black.  Also, engage just shows the gnome background.  Any suggestions on how to get transpareny working?  I really like enlightenment, I just can't justify using it without transparency.

---

### Post by ephman on 2005-08-09
[QUOTE=poofyhairguy]Then lets delete the file:



(don't worry, you made it in the howto, you can delete it).[/QUOTE]

nope still logging into enlightenment.  any other ideas i'm at a lost.  the file has been deleted.

thanks,
ephman

---

### Post by clarke.rainey on 2005-08-09
Ok I know this is going to be a dumb question... but I like enlightenment by itself... but I would love to have something like nautilus... is there a natilus like part in enlightenment 17?..

---

### Post by bored2k on 2005-08-09
[QUOTE=clarke.rainey]Ok I know this is going to be a dumb question... but I like enlightenment by itself... but I would love to have something like nautilus... is there a natilus like part in enlightenment 17?..[/QUOTE]
 It's called Evidence. You can also try rox-filer. It's on smoon's E repositories.

P.S. - Nice Naruto avatar ;)

---

### Post by zarathustra on 2005-08-09
OK managed to get it working.

---

### Post by spacemonkey on 2005-08-09
I've been fiddling since I got home from work.  I'm still not able to get transparency working, but I might not need it.  Emodules is nice, and is, so far, a good replacement for gdesklets.  But there are still a few desklets I'd like to replace with emodules.  I installed emodules from synaptic, but are there any other places to download other ones?

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=ephman]nope still logging into enlightenment.  any other ideas i'm at a lost.  the file has been deleted.

thanks,
ephman[/QUOTE]


Ok, try this. Remake teh file according to the how to (the sudo cp line). then open the file again and change the line to look like this:

>  1,RestartCommand=gnome-wm --default-wm metacity --sm-client-id default1

restart afterwards.

---

### Post by ephman on 2005-08-09
[QUOTE=poofyhairguy]Ok, try this. Remake teh file according to the how to (the sudo cp line). then open the file again and change the line to look like this:



restart afterwards.[/QUOTE]


your idea was actually the first thing i tried.  infact even after the restart 

1,RestartCommand=gnome-wm --default-wm metacity --sm-client-id default1

is still in the session file.  this is pretty strange eh?  your help is really appreciated big time.

thanks,
ephman

---

### Post by varunus on 2005-08-09
[QUOTE=poofyhairguy]The "show desktop" applet does not work in E16.[/QUOTE]

poofyhairguy,

When I installed E16.6 from Ubuntu, the show desktop applet did not work, and gave that nasty little message.  However, in E16.7, it works!  I accidentally clicked show desktop today, and it worked, and I was very confused for a minute...
(I'm one of those evil people who used the Sid/Sarge/Woody packages, Debian has E16.7 as stabe across the board.)  I posted this over in the thread to backport E16.7 also.

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=ephman]your idea was actually the first thing i tried.  infact even after the restart 

1,RestartCommand=gnome-wm --default-wm metacity --sm-client-id default1

is still in the session file.  this is pretty strange eh?  your help is really appreciated big time.

thanks,
ephman[/QUOTE]

I feel bad I'm running out of ideas. Next try the Configuration Editor tool. 

In it go: Desktop, then Gnome, then Applications, then window_manager.

Change it there, save and reboot.

If that doesn't work uninstall enlightenment with apt-get then reboot. If that doesn't work I'm out of ideas.

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=varunus]poofyhairguy,

When I installed E16.6 from Ubuntu, the show desktop applet did not work, and gave that nasty little message.  However, in E16.7, it works!  I accidentally clicked show desktop today, and it worked, and I was very confused for a minute...
(I'm one of those evil people who used the Sid/Sarge/Woody packages, Debian has E16.7 as stabe across the board.)  I posted this over in the thread to backport E16.7 also.[/QUOTE]

Thanks for the info. If I don't get the backport in a week, I'm going to try messing with thier backporting script.

---

### Post by ephman on 2005-08-09
[QUOTE=poofyhairguy]I feel bad I'm running out of ideas. Next try the Configuration Editor tool. 

In it go: Desktop, then Gnome, then Applications, then window_manager.

Change it there, save and reboot.

If that doesn't work uninstall enlightenment with apt-get then reboot. If that doesn't work I'm out of ideas.[/QUOTE]

really no reason to feel badly.  i was running out of ideas as well.  anyhow the only thing that seemed to work was to uninstall it completely.  and then everything seemed to work fine after a reboot.  at least now we know, and i'll reinstall it and i can fool around and know that getting back to metacity is just as an uninstall away.  you'd figure that i'd be able to keep in installed though?  anyhow.  thank you for your help.

ciao!
ephman

---

### Post by pranith on 2005-08-10
i have a serious problem.....

when i run "enlightenment_remote ...."

i am gettin this error 

""WARNING: not a utf8 locale!
ERROR: Enlightenment_remote cannot set up the IPC socket.
Maybe try the '-display :0.0' option?""

i donno wat to do.....cud neone help me with that???

---

### Post by darkmatter on 2005-08-10
pranith, what exactly is the command you are trying to issue with enlightenment_remote?

If you could give more detail as to what you are trying to accomplish, I may be able to help...

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=pranith]i have a serious problem.....

when i run "enlightenment_remote ...."

i am gettin this error 

""WARNING: not a utf8 locale!
ERROR: Enlightenment_remote cannot set up the IPC socket.
Maybe try the '-display :0.0' option?""

i donno wat to do.....cud neone help me with that???[/QUOTE]

In which version? E16 or 17?

---

### Post by wo.anderer on 2005-08-10
[QUOTE=zarathustra]The closest I have is:

1,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-WYG2EA/ --sm-client-id

Is there something wrong with my installation? That line isn't in the file any where.[/QUOTE]

I had the same problem. An nice alternative to editing this file is to use the gnome sessions utility in system-preferences. Follow the instructions from trilliji in this thread:[http://ubuntuforums.org/showthread.php?t=21160](http://ubuntuforums.org/showthread.php?t=21160) 

The e16 enlightened gnome is nice and fast  :)   Thanks for all the help. 
Though i'm still searching for a way to limit the desktop 'slide' to just the top right hand corner and not the whole right hand side of the screen. pretty annoying as default i would say.

---

### Post by JimmyJazz on 2005-08-10
I gotta tell ya I tried this with both E17 and E16 and they both looked really bad and went really slow, I may have been doing something wrong though anyways I kinda like metacity so I guess I'll stick with it.

---

### Post by PMO6022 on 2005-08-10
[QUOTE=wo.anderer]Though i'm still searching for a way to limit the desktop 'slide' to just the top right hand corner and not the whole right hand side of the screen. pretty annoying as default i would say.[/QUOTE]
If you right click on the desktop and select "virtual desktop settings" you can increase the resistance at the edge of the screen - so the flip doesn't happen so readily. I think the default is way too low, but I never flip accidentaly after increasing the resistance.

---

### Post by kittcankitt on 2005-08-10
[QUOTE=Omnios]Um dumb question but how can I set this up so there is a seperate entry to log into gnome and E-gnome. I still want to be able to log into regular gnome. That will allow me to play around with E-16 for a while and still have gnome if I need to lol. Figure I have to make a entry with enlightenment set up with gnome. Man 10 pages already maybe you can edit the fist post with all the goodies?[/QUOTE]

I also would like to figure this one out.  I tried a few things with NO positive outcomes.  I have everything up and running again but if anyone has any suggestions on this it would be appreciated if you could throw out a few pointers.  Thanks!  Kck

---

### Post by NMUrugbysteve on 2005-08-10
Anyone want to tell me how to change the background in E16?

---

### Post by varunus on 2005-08-10
[QUOTE=NMUrugbysteve]Anyone want to tell me how to change the background in E16?[/QUOTE]

Open up a terminal or nautilus, and change to the directory ~/.enlightenment (use CTRL-L in nautilus, just cd in a terminal).  Put any wallpapers you want in that folder and restart enlightenment (middle-click, user menus, restart enlightenment); they'll show up in the desktop background settings now.  I actually did something else; I already had a folder called Wallpaper in my home folder that I put all my wallpaper into, so I did the following:
```

cd ~/.enlightenment/
rmdir backgrounds
ln -s ~/Wallpaper backgrounds
```

Also, in E16.7, there's a nice new feature; instead of having to use the desktop background settings thing in E, the menu itself will show you thumbnails of all your wallpaper, and you can pick from there.

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=JimmyJazz]I gotta tell ya I tried this with both E17 and E16 and they both looked really bad and went really slow, I may have been doing something wrong though anyways I kinda like metacity so I guess I'll stick with it.[/QUOTE]

A: Its not for everyone.

B: the default themes do suck.

---

### Post by spacemonkey on 2005-08-10
Thanks for the great how to!  Here's a screenshot if anyone is interested:

[http://compy.gotdns.com/bfiser/e17.png](http://compy.gotdns.com/bfiser/e17.png) 

E17 with gnome, Ice Theme from the website mentioned in the howto, clearlooks-quicksilver gnome theme (they match perfectly).  Xcompmgr isn't running because of the screen distortion thing I mentioned in one of my earlier posts.  I'm using several modules from emodules.

Also, if anyone knows where I can find an enlightenment module that is an RSS reader, that would be excellent.

Thanks again for the great howto.

---

### Post by duminas on 2005-08-10
Nice Howto, though Enlightenment looks pretty god-awful to me.
To each their own, though, and back to Blackbox I go~

Quick question, since I don't want to make stuff blow up when I step backward:

Just do this, correct?
```
sudo rm ~/.gnome2/session
sudo rm /usr/share/xsession/Enlightenment.desktop
```

---

### Post by NMUrugbysteve on 2005-08-10
[QUOTE=varunus]Open up a terminal or nautilus, and change to the directory ~/.enlightenment (use CTRL-L in nautilus, just cd in a terminal).  Put any wallpapers you want in that folder and restart enlightenment (middle-click, user menus, restart enlightenment); they'll show up in the desktop background settings now.  I actually did something else; I already had a folder called Wallpaper in my home folder that I put all my wallpaper into, so I did the following:
```

cd ~/.enlightenment/
rmdir backgrounds
ln -s ~/Wallpaper backgrounds
```

Also, in E16.7, there's a nice new feature; instead of having to use the desktop background settings thing in E, the menu itself will show you thumbnails of all your wallpaper, and you can pick from there.[/QUOTE]
 Cool, thanks so much!

---

### Post by kvidell on 2005-08-10
[QUOTE=spacemonkey]Thanks for the great how to!  Here's a screenshot if anyone is interested:

[http://compy.gotdns.com/bfiser/e17.png](http://compy.gotdns.com/bfiser/e17.png) 

E17 with gnome, Ice Theme from the website mentioned in the howto, clearlooks-quicksilver gnome theme (they match perfectly).  Xcompmgr isn't running because of the screen distortion thing I mentioned in one of my earlier posts.  I'm using several modules from emodules.

Also, if anyone knows where I can find an enlightenment module that is an RSS reader, that would be excellent.

Thanks again for the great howto.[/QUOTE]
 That looks really nice, good work :)

Dual head or workspaces?

---

### Post by Wesley on 2005-08-11
got this error  :-( , pls look at the screenshot

[IMG][[IMG]http://img360.imageshack.us/img360/8261/screenshot6ag.th.png[/IMG]](http://img360.imageshack.us/my.php?image=screenshot6ag.png)[/IMG]

---

### Post by darkmatter on 2005-08-11
[QUOTE=Wesley]got this error  :-( , pls look at the screenshot

[IMG][[IMG]http://img360.imageshack.us/img360/8261/screenshot6ag.th.png[/IMG]](http://img360.imageshack.us/my.php?image=screenshot6ag.png)[/IMG][/QUOTE]

The command should be:
```
sudo gedit /usr/share/xsessions/Enlightenment.desktop
```

---

### Post by jterhune on 2005-08-11
Hi, thanks for writing such a great guide.

I'm having a slight problem using enlightened gnome, however. When I start gnome using enlightenment as the wm, enlightenment says it is starting and then proceeds to cover my screen with white and two gray lines running horizontally across. The gnome panel does not load, nor anything of that nature. If I go to a term and kill enlightenment I drop to my desktop, but without the panel or any wm.

Enlightenment 1:0.16.7.2-1

Any suggestions?
Thanks

---

### Post by poofyhairguy on 2005-08-11
[QUOTE=jterhune]Hi, thanks for writing such a great guide.

I'm having a slight problem using enlightened gnome, however. When I start gnome using enlightenment as the wm, enlightenment says it is starting and then proceeds to cover my screen with white and two gray lines running horizontally across. The gnome panel does not load, nor anything of that nature. If I go to a term and kill enlightenment I drop to my desktop, but without the panel or any wm.

Enlightenment 1:0.16.7.2-1

Any suggestions?
Thanks[/QUOTE]


Can you log into Enlightenment? Like log out of Gnome and log into Enlightenment?

---

### Post by jterhune on 2005-08-11
Yes, I can log into enlightenment. It seems to mostly be scrolling virtual desktops and context menus... but I assume that is what enlightenment is supposed to be like.

---

### Post by jterhune on 2005-08-11
Now that I try it again, perhaps enlightenment alone is not running properly. When I left click in enlightenment it does not bring up the applications menu, as it says it should, so I cannot figure out how to launch anything.

Perhaps I'm just missing something.

---

### Post by Stallone on 2005-08-11
Hello... I tried to remove enlightenment today, so i replaced the "1,RestartCommand" to what it was, and it still loaded Enlightenment. So I uninstalled it, and now when I try to log into my default session it comes up with an error talking about the fact that my session lasted less than 10 seconds so it told me to view the error file to see what went wrong. I went to see it and this is what i got:

**.xsession-errors**:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "tim"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/11025
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030
Starting gdesklets-daemon...

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
(gnome-panel:11129): GLib-GObject-CRITICAL **: g_object_unref: assertion `object->ref_count > 0' failed

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

                                        
Connected to daemon in 2142 milliseconds.

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

** (gnome-cups-icon:11133): WARNING **: failed request with status 1030

```

And my session file in .gnome2 is:

```

[Failsafe]
0,id=117f000001000112378698300000096680002
0,RestartStyleHint=2
0,Priority=40
0,Program=gnome-panel
0,CurrentDirectory=/home/tim
0,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-ijN1LQ/ 
0,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-ijN1LQ/ --sm-client-id 117f000001000112378698300000096680002 --screen 0 
1,id=117f000001000112378698400000096680004
1,RestartStyleHint=1
1,Priority=40
1,Program=gnome-volume-manager
1,CurrentDirectory=/home/tim
1,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-wG08oF/ 
1,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-wG08oF/ --sm-client-id 117f000001000112378698400000096680004 --screen 0 
2,id=117f000001000112378698400000096680005
2,RestartStyleHint=1
2,Priority=50
2,Program=update-notifier
2,CurrentDirectory=/home/tim
2,CloneCommand=update-notifier --sm-config-prefix /update-notifier-s3G1qF/ 
2,RestartCommand=update-notifier --sm-config-prefix /update-notifier-s3G1qF/ --sm-client-id 117f000001000112378698400000096680005 --screen 0 
3,id=117f000001000112378698500000096680006
3,RestartStyleHint=2
3,Priority=50
3,Program=gnome-cups-icon
3,CurrentDirectory=/home/tim
3,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-R3IlxF/ 
3,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-R3IlxF/ --sm-client-id 117f000001000112378698500000096680006 --screen 0 
4,id=117f000001000112378698300000096680000
4,RestartStyleHint=2
4,Priority=0
4,Program=gnome-smproxy
4,DiscardCommand=rm /home/tim/.gnome2//.gnome-smproxy-FhUipf 
4,CloneCommand=gnome-smproxy --sm-config-prefix /.gnome-smproxy-FhUipf/ 
4,RestartCommand=gnome-smproxy --sm-config-prefix /.gnome-smproxy-FhUipf/ --sm-client-id 117f000001000112378698300000096680000 
5,id=117f000001000112378698300000096680001
5,RestartStyleHint=2
5,Priority=20
5,Program=metacity
5,CurrentDirectory=/home/tim
5,DiscardCommand=rm -f /home/tim/.metacity/sessions/1123787239-9717-3221241425.ms 
5,CloneCommand=metacity 
5,RestartCommand=metacity --sm-save-file 1123787239-9717-3221241425.ms 
num_clients=6

[Default]
0,id=default0
0,RestartStyleHint=2
0,Priority=0
0,Program=gnome-smproxy
0,DiscardCommand=rm /home/tim/.gnome2//.gnome-smproxy-SJcNdu 
0,CloneCommand=gnome-smproxy --sm-config-prefix /.gnome-smproxy-SJcNdu/ 
0,RestartCommand=gnome-smproxy --sm-config-prefix /.gnome-smproxy-SJcNdu/ --sm-client-id default0 
1,id=117f000001000112378726300000098830000
1,RestartStyleHint=2
1,Priority=20
1,Program=metacity
1,CurrentDirectory=/home/tim
1,DiscardCommand=rm -f /home/tim/.metacity/sessions/1123791366-10778-1204764223.ms 
1,CloneCommand=metacity 
1,RestartCommand=metacity --sm-save-file 1123791366-10778-1204764223.ms 
2,id=default5
2,RestartStyleHint=1
2,Priority=40
2,Program=gnome-volume-manager
2,CurrentDirectory=/home/tim
2,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-WufSql/ 
2,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-WufSql/ --sm-client-id default5 --screen 0 
3,id=default2
3,RestartStyleHint=2
3,Priority=40
3,Program=gnome-panel
3,CurrentDirectory=/home/tim
3,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-D0TEA4/ 
3,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-D0TEA4/ --sm-client-id default2 --screen 0 
4,id=default8
4,RestartStyleHint=1
4,Priority=50
4,Program=update-notifier
4,CurrentDirectory=/home/tim
4,CloneCommand=update-notifier --sm-config-prefix /update-notifier-cXZ62t/ 
4,RestartCommand=update-notifier --sm-config-prefix /update-notifier-cXZ62t/ --sm-client-id default8 --screen 0 
5,id=default4
5,RestartStyleHint=2
5,Priority=50
5,Program=gnome-cups-icon
5,CurrentDirectory=/home/tim
5,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-z7mpWt/ 
5,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-z7mpWt/ --sm-client-id default4 --screen 0 
6,id=117f000001000112379141200000110250000
6,Program=gdesklets-daemon
6,CloneCommand=gdesklets-daemon 
6,RestartCommand=gdesklets-daemon 
7,id=117f000001000112379145400000110250001
7,RestartStyleHint=0
7,Priority=40
7,Program=nautilus
7,CurrentDirectory=/home/tim
7,CloneCommand=nautilus 
7,RestartCommand=nautilus --sm-client-id 117f000001000112379145400000110250001 --screen 0 
8,id=117f000001000112379146300000110250002
8,Program=gedit
8,CurrentDirectory=/home/tim
8,CloneCommand=gedit 
8,RestartCommand=gedit --sm-client-id 117f000001000112379146300000110250002 --screen 0 
9,id=117f000001000112379151400000110250003
9,Program=firefox-bin
9,CloneCommand=firefox-bin 
9,RestartCommand=firefox-bin 
num_clients=10 
```

Please help!

---

### Post by spacemonkey on 2005-08-11
> Quote:
Originally Posted by spacemonkey
Thanks for the great how to! Here's a screenshot if anyone is interested:

[http://compy.gotdns.com/bfiser/e17.png](http://compy.gotdns.com/bfiser/e17.png)

E17 with gnome, Ice Theme from the website mentioned in the howto, clearlooks-quicksilver gnome theme (they match perfectly). Xcompmgr isn't running because of the screen distortion thing I mentioned in one of my earlier posts. I'm using several modules from emodules.

Also, if anyone knows where I can find an enlightenment module that is an RSS reader, that would be excellent.

Thanks again for the great howto.

That looks really nice, good work

Dual head or workspaces? 

It's dual heads.  Two 17" LCDs.

---

### Post by kvidell on 2005-08-11
I asked this in the other enlightenment thread but this one's fresher so I'll ask again here:

How does one get **Entrance** working?
I have it installed but GDM is still the login manager.

Thanks,
- Kev

---

### Post by oceanelement on 2005-08-13
Many thanks to all the people who put the effort into enlightenment. It is a great system and it works seamlessly with gnome (using E16). Poofyhairguy, without the forum I would have not tried it out, so hats off to you too.

One thing that I noticed and would like to comment on some statements made earlier. Poofyhairguy and some others say that it "feels" faster using enlightenment. Actually based on using glxgears my fps went from 1400 fps with metacity to 1640 fps with enlightenment. So in 3D performance with an ATI card it is FASTER. Does anyone else experience the same? 

More eyecandy and speed... what a deal.

Oceanelement

---

### Post by Tab on 2005-08-14
Okay, A. E17's default theme is awesome (but if you must use another, Detour is next best). B. It's easier to create the settings-daemon eap and then add it to "startup" with entangle (a.k.a. "menu editor" in the E17 menu). C. Nautilus works fantastically with E17, so long as you're using the --no-desktop option.

---

### Post by darkmatter on 2005-08-14
[QUOTE=Tab]Nautilus works fantastically with E17[/QUOTE]

So does gksudo. Also, I would recommend using fbpanel to handle the notifications (systray), as the tray included with engage looks really out of place when enabled.

It's a shame that apps like gaim insist on having tray notifications, otherwise I'd never need it.

---

### Post by spacemonkey on 2005-08-15
To you Enlightenment experts:

Is there anyway to make the windows raise on a mouse click anywhere in the window, instead of just when clicking on the title bar?  Focus follows my mouse, which is how I had it set in metacity, and I like it that way.  By in metacity, i could click anywhere inside the window, and it would move to the top, but in e17, I have to click the title bar to raise the window.  Anyway to change this?

---

### Post by darkmatter on 2005-08-16
To switch the focus model to accept clicks anywhere in the window, do the following in a terminal:

```
enlightenment_remote -focus-policy-set CLICK
```

---

### Post by spacemonkey on 2005-08-16
I tried that, but that isn't what I want.  I like having the window focus on mouse over, but I want it to raise to the top when it is clicked anywhere on the window, instead of just the title bar.  When I set the focus policy to click, it only focuses on click.

---

### Post by true nemesis on 2005-08-16
Okay, I followed the howto exactly. Made all the files, restarted gnome, and then logged back. Nothing happens. E doesnt activate. When does it exactly start to load?

---

### Post by PMO6022 on 2005-08-16
[QUOTE=spacemonkey]Is there anyway to make the windows raise on a mouse click anywhere in the window, instead of just when clicking on the title bar? Focus follows my mouse, which is how I had it set in metacity, and I like it that way. By in metacity, i could click anywhere inside the window, and it would move to the top, but in e17, I have to click the title bar to raise the window. Anyway to change this?[/QUOTE]

Right click on your desktop, and select "focus settings"
Select "Focus follows pointer [sloppily]", and "clicking in a window always raises it"

That should do it.

[edit] awww, this is only for e16, I gotta read more closely...sorry.

---

### Post by darkmatter on 2005-08-16
[QUOTE=spacemonkey]I tried that, but that isn't what I want.  I like having the window focus on mouse over, but I want it to raise to the top when it is clicked anywhere on the window, instead of just the title bar.  When I set the focus policy to click, it only focuses on click.[/QUOTE]

Not sure, I've tried various setting, but it looks like it's a comprimise. I haven't yet found a way to enable click AND mouse focus in E17 (I'd like to, as it is my preference as well)

---

### Post by juantxorena on 2005-08-17
Greetings.

First of all, sorry for my horrible english.

Second: I'm VEEERY confused about gnome-E17 integration. For example:
> 2. Do what I did: install some gdesklet love. Gdesklets can be installed in Synaptic if you have added the backport repository. To install a gesklet, download the tar file from the site, start the gesklet program (under accessories) and drag and drop the tar file onto the gdesklet manager program.

In this case, some cool E17 things like Engage toolbar, are useless? Or you can use both gDesklets and Engage? In this case, E17 "only" cares about window config. I'm right?
> 3. Applications > System Tools > ConfiguratioN Editor > apps > nautilus > preferences > UNCHECK show desktop.
In this case, what Gnome does? Is it necessary?

More confusing things:
I suppose that pager and other gnome-menu things have a enlightenment-equivalent applet(?). But, can I use gnome-menus (applications-locations-system)? Or you can't access easily applications like synapatic?
Can I use gDesklets and the enlightenment equivalent (I don't know its name)?
If I open a folder, will be open with nautilus? Or with Evidende?

I think that's all, for now. To sum up, I'd like to know Gnome-E17 integration things.

Thanks for thy time.

---

### Post by vinbuntu on 2005-08-17
[QUOTE=darkmatter]Not sure, I've tried various setting, but it looks like it's a comprimise. I haven't yet found a way to enable click AND mouse focus in E17 (I'd like to, as it is my preference as well)[/QUOTE]
 This doesn't really help your problem but I've been trying to figure out this too.  I know if you hold Alt and left click anywhere on the window it will focus it and bring it to the top (so the capability to do this is built in).  But how to make this default for a left click?

---

### Post by true nemesis on 2005-08-17
[QUOTE=vinbuntu]This doesn't really help your problem but I've been trying to figure out this too.  I know if you hold Alt and left click anywhere on the window it will focus it and bring it to the top (so the capability to do this is built in).  But how to make this default for a left click?[/QUOTE]
 I followed the instructions as posted. I logged back into Gnome after applying that enlightened gnome trick. The first thing that happens is nautilus crashing 4 times in a row. And then nothing happens. My desktop looks the same as well. 

btw, enlightenment is on my sessions options and i installed E 1:0.16.6. Can you anyone help me please? Is there a specific loading time?

---

### Post by jegler on 2005-08-17
I have got this working and it is amazing. I had tried out E17 before but due to its maturity I hadn't found a way to use it productively. Thanks!

However, (you all knew there was a catch), eclair seems to be having trouble setting up the database table it needs. I get the following error after starting eclair in the consol:

```
$ eclair
Database: Unable to create "media_files" table: table media_files already exists
 
```

It has the effect of not letting me add any playlists or files and so I cannot use it. I figured that this thread would be my best chance of an answer, hope someone can help.

EDIT: turns out this appears to be a known breakage at the moment so there is nothing that can be done until the code is fixed

---

### Post by super on 2005-08-17
hmm...  :-k 
is e17 finally pretty-ing up those hideous (and so far un-themable) dialog boxes?

just saw this over on the ::get-e.org:: news page. [take a look.](http://shots.hisham.cc/shots/eblocks_gtk_ewl_2.png?orig) 

shh!
can you hear that?
i believe that's the sound of progress being made!  :-P

---

### Post by darkmatter on 2005-08-17
[QUOTE=super]hmm...  :-k 
is e17 finally pretty-ing up those hideous (and so far un-themable) dialog boxes?

just saw this over on the ::get-e.org:: news page. [take a look.](http://shots.hisham.cc/shots/eblocks_gtk_ewl_2.png?orig) 

shh!
can you hear that?
i believe that's the sound of progress being made!  :-P[/QUOTE]

Yes, our beloved E just keeps getting better by the moment. :smile: 

Maybe now I won't have to use gtk to build matching themes for E, one the ewl gets up to speed (looks like it's getting close)

---

### Post by andradelipe on 2005-08-18
Hi,

I didin't find the line to modify in session, here's what i have:

[COLOR=Blue]
1,id=11c0a80032000111347975800000069560001
1,RestartStyleHint=2
1,Priority=20
1,Program=metacity
1,CurrentDirectory=/home/felipe
1,DiscardCommand=rm -f /home/felipe/.metacity/sessions/1124375297-7917-862714956.ms 
1,CloneCommand=metacity 
1,RestartCommand=metacity --sm-save-file 1124375297-7917-862714956.ms 
2,id=11c0a80032000111347975800000069560002
2,RestartStyleHint=2
2,Priority=40
2,Program=gnome-panel
2,CurrentDirectory=/home/felipe
2,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-WNfnJG/ 
2,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-WNfnJG/ --sm-client-id 11c0a80032000111347975800000069560002 --screen 0 [/COLOR]

So, i don't have the line:  1,RestartCommand=gnome-wm --sm-client-id default1


what should I have to do?

thanks!

---

### Post by darkmatter on 2005-08-18
[QUOTE=andradelipe]what should I have to do?

thanks![/QUOTE]

Do it the easy way, System->Preferences->Session, find metacity and set the style to normal and apply the changes. Then, open a terminal and type the following:

```
killall metacity && sleep 1 && enlightenment
```
leave the terminal open for the moment.

Then go to System->Preferences->Session again. Find enlightenment and set order to 20, style to restart. Apply the settings then close the terminal. Enlightenment should quit and restart.

Next, log out with the 'save current setup' marked.

Log in, it will take a bit to load the first time (be patient) but you will now happily be using E instead of metacity. :smile:

EDIT: Just a side note, if you want E to handle the drawing of the desktop, use the configuration editor to set nautilus to not draw the desktop.

The results look like this
[http://img221.imageshack.us/my.php?image=screenshot1vd.jpg](http://img221.imageshack.us/my.php?image=screenshot1vd.jpg)
[http://img221.imageshack.us/my.php?image=screenshot24te.jpg](http://img221.imageshack.us/my.php?image=screenshot24te.jpg)
[http://img260.imageshack.us/my.php?image=screenshot30nm.jpg](http://img260.imageshack.us/my.php?image=screenshot30nm.jpg)

---

### Post by kingzasz on 2005-08-18
Few things that are really bugging me with e17.

1.  Where is the configuration?  Where can I enable click to raise?  Where do I set what the windows does when it is resized.  It was all there in e16, but now it disappeared!

2.  What happened to the pager.  I would like the pager to be like it was in e16, where it showed a preview of the windows in each desktop, instead of just showing the icon for the program that is running.  Again, why is e17 a step down?

3.  Is there anyway to get a taskbar for e17.  I know that it isn't needed and you can just right click, but after 10 years with a taskbar I'm kinda missing it  :grin: 

Thanks for the great guide, and I hope I can fix these so I don't have to go back to KDE.

---

### Post by darkmatter on 2005-08-18
[QUOTE=kingzasz]Few things that are really bugging me with e17.

1.  Where is the configuration?  Where can I enable click to raise?  Where do I set what the windows does when it is resized.  It was all there in e16, but now it disappeared!

2.  What happened to the pager.  I would like the pager to be like it was in e16, where it showed a preview of the windows in each desktop, instead of just showing the icon for the program that is running.  Again, why is e17 a step down?

3.  Is there anyway to get a taskbar for e17.  I know that it isn't needed and you can just right click, but after 10 years with a taskbar I'm kinda missing it  :grin: 

Thanks for the great guide, and I hope I can fix these so I don't have to go back to KDE.[/QUOTE]

1-> enlightenment_remote. As dr 17 is still pre-alpha, a lot of GUI is still missing, but this command-line tool can handle most of the configuration of the WM. You can find documentation on it's use at [http://www.get-e.org/User_Guide/English/_pages/3.1.html](http://www.get-e.org/User_Guide/English/_pages/3.1.html)

2-> E 17 isn't a step down, it's a complete rewrite of the code using new core libraries (the EFL), and still has a lot of work to be done. It's unfair to Raster and the other dev's to approach it as a 'step down', as the previous version (dr 16) has been around for several years, and is the continued evolution of the ORIGINAL Enlightenment. Once again, E 17 is fresh and brand-spanking new.

3-> ```
enlightenment_remote -module-load ibox
``` or use engage, as it lists running apps as icons. You can also run [fbpanel](http://fbpanel.sourceforge.net/) within E if you need a notification area/support for gnome applets. Engage has a systray, but it is currently butt ugly. :roll:

I haven't tried it (I loath taskbars) but as fbpanel is [NETWM](http://www.freedesktop.org/Standards/wm-spec) compliant, it should be capable of handling task management within E.

---

### Post by kingzasz on 2005-08-18
[QUOTE=darkmatter]It's unfair to Raster and the other dev's to approach it as a 'step down', as the previous version (dr 16) has been around for several years, and is the continued evolution of the ORIGINAL Enlightenment. [/QUOTE]

Sorry about the 'step down' wording.  I didn't realize that it was a rewrite, I was thinking that it was just a new version.

Also, so there isn't a current module that displays a preview for the pager?

---

### Post by darkmatter on 2005-08-18
[QUOTE=kingzasz]Also, so there isn't a current module that displays a preview for the pager?[/QUOTE]

None that I've seen. Hopefully they'll end up adding thumbnailing to the pager module, as that is the one feature from dr 16 that I miss.

And no need to apologize for the 'step down' comment. I just thought I'd 'Enlighten' you.  ;-) 
Eventually, E 17 will be a complete 'shell' (think explorer under windows - only 10,000 times better)

---

### Post by kingzasz on 2005-08-18
I figured out how to raise a window when you click anywhere on the window, instead of just the top. 

In the console type:

```
enlightenment_remote -focus-policy-set CLICK
```

---

### Post by darkmatter on 2005-08-19
[QUOTE=kingzasz]I figured out how to raise a window when you click anywhere on the window, instead of just the top. 

In the console type:

```
enlightenment_remote -focus-policy-set CLICK
```[/QUOTE]

Yes, that's the ticket. It's a rewarding learning experience when you figure things out on your own, isn't it? :)

---

### Post by oceanelement on 2005-08-19
to all the enlightened users of ubuntu

question: shouldn't there be a section on the ubutnuforum.com site for "e-buntu"? a section specifically for ubuntu and elightenment. many people say that ubuntu has almost everything a linux user could ask for, but the desktop could use some more work. i know that enlightenment is still in its beta phase but i think it is already an amazing system. implementing enlightenment could push ubuntu lightyears ahead of the other distros. this is what i thought of when i saw someone else type e-buntu. 

in addition, thanks to smoon, poofyhairguy, rasterman, and all the others who have made this possible. i have heard many complications of people installing enlightenment, but with apt-get and smoon it has been a relatively smooth ride for us all. 

oceanelement

p.s. anyone with comments, criticisms, ideas... give them in  :grin:

---

### Post by darkmatter on 2005-08-19
[QUOTE=oceanelement]to all the enlightened users of ubuntu

question: shouldn't there be a section on the ubutnuforum.com site for "e-buntu"? <snipped>

p.s. anyone with comments, criticisms, ideas... give them in  :grin:[/QUOTE]

Yes, yes and..yes. ;-) 

Considering the e-develop forums are currently down (they seem to do that a lot), a forum section dedicated to Enlightenment users would be a great idea, as long as the Admin's feel there are enough of us to warrant it.

That way, we could all share our knowledge, ideas, hacks, and even artwork (themes, etc.) for E in a unified arena.

---

### Post by rpgcyco on 2005-08-19
> Considering the e-develop forums are currently down (they seem to do that a lot), a forum section dedicated to Enlightenment users would be a great idea, as long as the Admin's feel there are enough of us to warrant it.

Yeah, as long as there is enough of us, it'd be good. :) I've been using E17 standalone for a few weeks, and apart from a few weird issues with the window manager side of things, it's been rock solid. :)

- Rpg Cyco

---

### Post by SwissArmyKnife on 2005-08-19
This all works great, thanks for the great guide.
I'm running into a block here which the answer isnt obvious to me -> not matter what theme I choose in enlightenment (e16), its interfering with the gnome one.

I always get a panel on the top of the screen thats just wasted real estate and have to move about the normal panels to retain usablity.  

Is there any way to turn off all enlightenment panels when logged into gnome ?

---

### Post by darkmatter on 2005-08-19
[QUOTE=SwissArmyKnife]I always get a panel on the top of the screen thats just wasted real estate and have to move about the normal panels to retain usablity.  

Is there any way to turn off all enlightenment panels when logged into gnome ?[/QUOTE]

That panel would be the drag bar. You can disable it by using the 'Special FX Settings' dialog and and unchecking the 'Display desktop dragbar' option.

---

### Post by SwissArmyKnife on 2005-08-20
[QUOTE=darkmatter]That panel would be the drag bar. You can disable it by using the 'Special FX Settings' dialog and and unchecking the 'Display desktop dragbar' option.[/QUOTE]
 Great ! , thanks darkmatter,  that was just the trick.

---

### Post by lyricmuse on 2005-08-20
Hello everyone,
 
First of all, nice howto. But since I'm a newbie I'm having a problem that I can't figure out.
 
1. I'm running a 3Dfx Voodoo 4 agp card (which does some interesting things)](*,)
2. Here is the strange error I get when trying to login to enlightened
 
```
FATAL ERROR:
 
This Xserver does not support the Shape extension
This is required for Enlightenment to run.
 
Your Xserver probably is too old or mis-configured.
 
Exiting.
``` 
 
Thanks for any help in this
 
I figured out the problem.  I did an update on my 3DFX drivers and everything worked fine.  I guess no one else has had this problem since I didn't get a reaction.  If you own a 3DFX card, I would suggest trying something else.  I've had nothing but problems with mine.  It's a Voodoo 4 4500.

---

### Post by zenrox on 2005-08-22
e17 and gnome woohoo
[http://www.deviantart.com/view/22047212/](http://www.deviantart.com/view/22047212/) <--screenshot thare \\:D/

---

### Post by Amol_Karmarkar on 2005-08-23
Works for me with E16.

---

### Post by Weav on 2005-08-24
Hi i am unable to get to the step where i can log onto enlightenment, it gives me no option besides gnome and the other choices.

I tried to  sudo gedit /usr/share/xsessions/
but it said the file was a regular file and it wouldn't let me type anything into it
i tried to chmod +rw it and still no success

Anyone know whats going on?

Thanks

---

### Post by SwissArmyKnife on 2005-08-25
[QUOTE=Weav]Hi i am unable to get to the step where i can log onto enlightenment, it gives me no option besides gnome and the other choices.

I tried to  sudo gedit /usr/share/xsessions/
but it said the file was a regular file and it wouldn't let me type anything into it
i tried to chmod +rw it and still no success

Anyone know whats going on?

Thanks[/QUOTE]

The OP hasn't updated this, its later on in this thread though.

Do this instead..
```
sudo gedit /usr/share/xsessions/Enlightenment.desktop
```
Paste in.. ```
 [Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application 
```

Hit save, and you should now have the "Enlightenment" option on login.

Its a fantastic peice of eye candy and everything does run that little bit faster, well worth persisting with !!

---

### Post by oceanelement on 2005-08-25
Does anyone have the problem when the splash screen comes up that the windows manager takes about 2 minutes to lead? 

The loading happens as follows:

splash starts
then enlightenment starts up
back to splash screen - windows manager is still loading
2 minutes later - all other programs load at normal rate and system is ready run

Is there a way to fix it? 

Oceanelement

---

### Post by poofyhairguy on 2005-08-25
[QUOTE=oceanelement]Does anyone have the problem when the splash screen comes up that the windows manager takes about 2 minutes to lead? 

The loading happens as follows:

splash starts
then enlightenment starts up
back to splash screen - windows manager is still loading
2 minutes later - all other programs load at normal rate and system is ready run

Is there a way to fix it? 

Oceanelement[/QUOTE]

I fixed it by logging out and selecting "save session." The Next time I logged in it was much better.

---

### Post by sapo on 2005-08-27
thanx for the good tutorial.. my "Enlightened Gnome" now is far faster and its really pretty  :grin: 

here a screenshot 
[[IMG]http://img380.imageshack.us/img380/840/enlightenedgnome016ob.th.jpg[/IMG]](http://img380.imageshack.us/my.php?image=enlightenedgnome016ob.jpg)

 :grin:

---

### Post by wondering_jew on 2005-08-27
courtesy of  [http://www.get-e.org/User_Guide/English/_pages/3.4.html](http://www.get-e.org/User_Guide/English/_pages/3.4.html) , I finally found how to create an edj desktop background from one of my normal png's or other more common image formats. In a terminal type

 e17setroot -s ~/location of desired background image 

this will convert your background image to edj and set it as the background image. I set mine to be the same as my gnome background image so things that are transparent (gdesklets, terminal on my desktop etc) look right. Lots of info in the user guide but I thought this might be one other people who have not looked at the guide might be struggling with... Any one have other simple tricks that a newbie might benefit from?

---

### Post by flip on 2005-08-27
Hey all,

I'm trying to install enlightenement and I think it might have a broken dependency: libttf2. I found this package in the debian repositories but apt-get can't seem to find them in the ubuntu ones. Before I start mixing repositories I thought I'd ask here if there's some other way around this.

Thanks in advance,

EDIT: found needed deb packages in ubuntu repositories under "pool" directory. I guess apt doesn't look for packages here? I'm sure there's a reason for this, just not one I know of. Manual download and 'dpkg -i' works.

- flip

---

### Post by argux on 2005-08-28
OK, for all those guys having trouble finding the left-click menu, you need to actually create it first. But worry not, it will be a million times easier to do it than it for me to explain it.
Mind you, this is for e16. I now nothing of e17, but the procedure might be similar.

Middle-click on the desktop and you'll get the Enlightenment menu. If you don't have a middle button but you have the third button emulation enabled, click with both buttons at the same time. If you don't have this emulation enabled, then do Ctrl+Left-Click, it's all the same.

In the Enlightenment menu, follow Maintenence->Regenerate Menus. It will take a few seconds (on my piii-450) after which the left-click menu will be accesible.

If you want to edit this menu, just do this:

```
sudo apt-get install e16menuedit
``` 

and execute this program, which is the menu editor for e16.

You might like to install also e16keyedit for your keybinding pleasure.

---

### Post by argux on 2005-08-28
One thing I miss from other wm's is the ability to run commands by hitting Alt+F2. This works both in kde and gnome with metacity. I haven't found a way to do this in e16.

The best I can do is to make a keybinding to Eterm. But I'm sure there must be a better way. Anyone knows how to invoke this?

A way around is that, as I have the gnome panel anyway, I just add a mini-commander to it. Still, I'd like to have this Alt+F2 thing working if only just to have some peace of mind.

---

### Post by Weav on 2005-08-28
Wow ok thanks for the guide i got e16 up and running within Gnome.

Just one question: Those links that you gave are only for e17. Where do i find themes for e16 and how do i get that engage icon taskbar to work?

Thanks a lot.

---

### Post by justaguynpc on 2005-08-28
I followed poofyhairguy's installation for E16 Enlightenment, and had a couple of issues:

1.) never could access any sort of "applications menu" running the "stand-alone" version
2.) my desktop resolution seemed to have been changed somehow, all the window sizes and font sizes became so small, it was basically unusable
3.) install of E16 within Gnome seemed to go well, however, I really didn't care for it.  I would rather run E16 on it's own if I could remedy the issues in 1.) and 2.) above.
4.) I am not savy enough for the E17 install, concurrent with the idea of "unstable" and "alpha-status" I think I better stay with the "tried and true" version.

Reason for this post

1.) Would like to "try-again" with the "stand-alone" E16 install, BUT synaptic informs me:

      [B] enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/B]

Naturally, I DO have universe enabled in my repository.  I am unsure what course of action to take next.........................

Cheers

---

### Post by poofyhairguy on 2005-08-29
[QUOTE=Weav]Wow ok thanks for the guide i got e16 up and running within Gnome.

Just one question: Those links that you gave are only for e17. Where do i find themes for e16 and how do i get that engage icon taskbar to work?

Thanks a lot.[/QUOTE]


Look here:

[http://themes.freshmeat.net/browse/60/](http://themes.freshmeat.net/browse/60/)

My fav is #21.

---

### Post by poofyhairguy on 2005-08-29
[QUOTE=justaguynpc]I followed poofyhairguy's installation for E16 Enlightenment, and had a couple of issues:

1.) never could access any sort of "applications menu" running the "stand-alone" version
2.) my desktop resolution seemed to have been changed somehow, all the window sizes and font sizes became so small, it was basically unusable
3.) install of E16 within Gnome seemed to go well, however, I really didn't care for it.  I would rather run E16 on it's own if I could remedy the issues in 1.) and 2.) above.
4.) I am not savy enough for the E17 install, concurrent with the idea of "unstable" and "alpha-status" I think I better stay with the "tried and true" version.

Reason for this post

1.) Would like to "try-again" with the "stand-alone" E16 install, BUT synaptic informs me:

      [B] enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/B]

Naturally, I DO have universe enabled in my repository.  I am unsure what course of action to take next.........................

Cheers[/QUOTE]


A: run command "gnome-panel" in e16 to get an applications panel.

B: sudo apt-get update to hopefully fix install problems. Did you install e17? You have to delete that preferences file you made if you did.

---

### Post by juantxorena on 2005-08-29
[QUOTE=justaguynpc]Would like to "try-again" with the "stand-alone" E16 install, BUT synaptic informs me:

      [B] enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/B]

Naturally, I DO have universe enabled in my repository.  I am unsure what course of action to take next.........................

Cheers[/QUOTE]

I had this problem also, and a sudo apt-get update didnt's fix it. I had to download de deb packages from debian repository manually and install them with ```
sudo dpkg -i name_of_package

```
[These](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=enlightenment&searchon=names&subword=1&version=stable&release=all) are the packages you must download and install this way. They are version 16.7, but these packages are from stable debian, so they must be "stable".

P.D. Sorry for my english :oops:

---

### Post by justaguynpc on 2005-08-29
**You have to delete that preferences file you made if you did.**

I reread the whole thread, and fail to see a "preference file" mentioned.  Could you please be more specific about the file to which you refer?

Cheers

---

### Post by poofyhairguy on 2005-08-29
[QUOTE=justaguynpc]**You have to delete that preferences file you made if you did.**

I reread the whole thread, and fail to see a "preference file" mentioned.  Could you please be more specific about the file to which you refer?

Cheers[/QUOTE]

The one in the second step here:

[http://www.ubuntuforums.org/showpost.php?p=239028&postcount=1](http://www.ubuntuforums.org/showpost.php?p=239028&postcount=1)

---

### Post by justaguynpc on 2005-08-29
Thanks poofyhairguy!

Always prompt and supportive

Cheers

---

### Post by j.hill on 2005-08-29
OK, so I got E16 to replace Metacity.  New question:

How do I get all the cool E backgrounds to work in GNOME?  Right now I've only got access to the awful backgrounds that came with Ubuntu, plus one slightly less hideous one that I downloaded.  The E settings menu, which I would use in standard E, doesn't help -- it sets the background on my virtual desktops (I can see it working in the pager) but not on my primary desktop.  

So E is drawing the window borders and doing the minimize/maximize animation, but GNOME is handling backgrounds and menus.  It's an uneasy alliance, to say the least.  How can I further enlighten GNOME?

Thanks --

EDIT:  When I go into regular E (no GNOME) and start Nautilus, I revert partially to the GNOME desktop -- ghastly brown wallpaper, icons of downloaded files that don't appear in E, &c.  What gives?

---

### Post by darkmatter on 2005-08-29
[QUOTE=j.hill]OK, so I got E16 to replace Metacity.  New question:

How do I get all the cool E backgrounds to work in GNOME?  Right now I've only got access to the awful backgrounds that came with Ubuntu, plus one slightly less hideous one that I downloaded.  The E settings menu, which I would use in standard E, doesn't help -- it sets the background on my virtual desktops (I can see it working in the pager) but not on my primary desktop.  

So E is drawing the window borders and doing the minimize/maximize animation, but GNOME is handling backgrounds and menus.  It's an uneasy alliance, to say the least.  How can I further enlighten GNOME?

Thanks --

EDIT:  When I go into regular E (no GNOME) and start Nautilus, I revert partially to the GNOME desktop -- ghastly brown wallpaper, icons of downloaded files that don't appear in E, &c.  What gives?[/QUOTE]

For the first part, if you want E to handle the desktop, go into the configuration editor: apps->nautilus->preferences, uncheck the 'show_desktop' option. Next time you start your session, control of the desktop should be handed over to Enlightenment.

For the second, start nautilus with:
```
nautilus --no-desktop
```
for spatial, or
```
nautilus --no-desktop --browser
```
for a traditional file browser window.

You need to use one of these flags when running nautilus in another environment.

Remember, nautilus is mor than just a filer, it is also the desktop in gnome. The above flags tell nautilus to not start it's desktop component.

---

### Post by jeffbacon on 2005-08-29
ok, so reading through this all, how do I go back to Metacity?

---

### Post by jeffbacon on 2005-08-30
[QUOTE=jeffbacon]ok, so reading through this all, how do I go back to Metacity?[/QUOTE]

(the only solution on this forum seems to be uninstall Enlightenment)

---

### Post by darkmatter on 2005-08-30
[QUOTE=jeffbacon]ok, so reading through this all, how do I go back to Metacity?[/QUOTE]

Exactly which command did you use to switch the WM to Enlightenment?

As there is more than one way, a little more info would be helpful.

---

### Post by jeffbacon on 2005-08-30
[QUOTE=darkmatter]Exactly which command did you use to switch the WM to Enlightenment?

As there is more than one way, a little more info would be helpful.[/QUOTE]

I just followed the instructions in the first post to switch to E16

(after uninstalling, I now have no window manager =)

---

### Post by Weav on 2005-08-30
Hi i have tried e16 before and did not exactly like it because of its lagging when switching desktops (i have a slow computer), is there anyway to uninstall e16 so i can do a fresh install of e17 and try to get engage and what not to work.

Thanks  :wink:

---

### Post by jeffbacon on 2005-08-30
[QUOTE=jeffbacon]I just followed the instructions in the first post to switch to E16

(after uninstalling, I now have no window manager =)[/QUOTE]

so, I added "--default-wm metacity" to that orginal line in ~/.gnome2/sessions but that didn't seem to work, so I started metacity from within GNOME and now it starts each time I log back in so I gues it's 'fixed' but not sure how reliably.

---

### Post by poofyhairguy on 2005-08-30
[QUOTE=jeffbacon]so, I added "--default-wm metacity" to that orginal line in ~/.gnome2/sessions but that didn't seem to work, so I started metacity from within GNOME and now it starts each time I log back in so I gues it's 'fixed' but not sure how reliably.[/QUOTE]

Tell me if it doesn't work. I will post this answer if your change is permenant.

---

### Post by oceanelement on 2005-08-30
[QUOTE=poofyhairguy]I fixed it by logging out and selecting "save session." The Next time I logged in it was much better.[/QUOTE]

poofyhairguy, thanks for the tip. It worked great and now the ubuntu is working 100%.

Oceanelement

---

### Post by j.hill on 2005-08-30
[QUOTE=darkmatter]Remember, nautilus is mor than just a filer, it is also the desktop in gnome. The above flags tell nautilus to not start it's desktop component.[/QUOTE]

Ah...didn't realize that.  Light dawns -- in fact I am Enlightened.  Thanks.

---

### Post by darkmatter on 2005-08-30
[QUOTE=j.hill]Ah...didn't realize that.  Light dawns -- in fact I am Enlightened.  Thanks.[/QUOTE]

You're most welcome. :smile:

---

### Post by j.hill on 2005-08-30
> For the first part, if you want E to handle the desktop, go into the configuration editor: apps->nautilus->preferences, uncheck the 'show_desktop' option. Next time you start your session, control of the desktop should be handed over to Enlightenment.

Hmm.  This is odd:  I don't have that option.  The closest I can come is apps->system tools->file browser->edit->preferences; but there's no "show desktop" option.  Is there another menu I might look for?  Or maybe a terminal command that would do the job?

---

### Post by darkmatter on 2005-08-30
[QUOTE=j.hill]Hmm.  This is odd:  I don't have that option.  The closest I can come is apps->system tools->file browser->edit->preferences; but there's no "show desktop" option.  Is there another menu I might look for?  Or maybe a terminal command that would do the job?[/QUOTE]

The configuration editor is under Applications -> System Tools (icon is a little red car with an open hood, can't miss it).

Just launch that app, you will see a tree-view on the left side panel. use it to navigate the following path: apps -> nautilus-> preferences. In the right are of the window you will see a list of settings. Find the one named 'show_desktop' uncheck the box to the right of it. close the configuration editor, and log out.

---

### Post by jeffbacon on 2005-08-30
[QUOTE=poofyhairguy]Tell me if it doesn't work. I will post this answer if your change is permenant.[/QUOTE]

I rebooted and it still launched metacity so it seems fixed.

My ~/.gnome2/session file now has this in it:

```

0,DiscardCommand=rm -f /home/jeffbacon/.metacity/sessions/1125376780-13775-1003375462.ms
0,CloneCommand=metacity
0,RestartCommand=metacity --sm-save-file 1125376780-13775-1003375462.ms

```

---

### Post by dahli.llama on 2005-08-30
How do you get Engage to work?

I am running E16.7 and I would like some kind of taskbar and engage looked pretty neat.  I've tried to get it with apt-get install engage but it can't be found.  Am I looking for the wrong thing?  Or is there a repository I need to add?

Please help.  I like Enlightenment so far, I just need to do some tweaking.

---

### Post by poofyhairguy on 2005-08-30
[QUOTE=dahli.llama]How do you get Engage to work?

I am running E16.7 and I would like some kind of taskbar and engage looked pretty neat.  I've tried to get it with apt-get install engage but it can't be found.  Am I looking for the wrong thing?  Or is there a repository I need to add?

Please help.  I like Enlightenment so far, I just need to do some tweaking.[/QUOTE]


Its in smoon repo:

[http://www.ubuntuforums.org/showthread.php?t=46105](http://www.ubuntuforums.org/showthread.php?t=46105)

don't do the part of the guide about aming the file though. Just add the repo to your sources.list and install engage. Now using it is another matter. I wish you could tell me that!

---

### Post by dahli.llama on 2005-08-30
From the looks of things Smoon isn't hosting any repositories anymore :(  Oh well.

I am using fbpanel and that seems to work alright.  Nothing spectacular, but better than nothing.

I do have a question though, I was using eterm with no borders and transparent, basically to completely match my decktop, but now when I start it up it shows up in the task bask.  Is there a way to prevent that?

So far everything is looking pretty good.

---

### Post by UrbanSlayer on 2005-09-04
Ive now finally gotten round to sorting out Enlightened Gnome, and while I kinda wanted to use E17, since it is still Alpha, and a PITA to install, I went with E16.  I like it, its very very nice, i've told E16 to draw the desktop as well now, so its less like Gnome.  So, thankyou very much for the excellent howto.

The only issue I have, is when I ran Generate Menu's, it only generated 2 Gnome menus - Multimedia and Internet, and only put xine in Multimedia and nothing in Internet.  While I have got the e16menuedit app and so could create all my own bits, I'd kinda like the rest of the Gnome menus to be there to begin with for me to just edit.  Anyway of doing so?

---

### Post by John.Michael.Kane on 2005-09-09
Has anyone tried installing this using just the server based instal?l and then building up from there.just wondered if that could even be done,  if it could i guess it would lighten up and speed up the machine as well..

---

### Post by Zhukov on 2005-09-10
typing nautilus at the console will fire up the desktop too, but if you alter the command to nautilus --no-desktop you can bypass this easily

---

### Post by Owdy on 2005-09-11
If i install this, how easy it would get old one back if i dont like it?

---

### Post by Zhukov on 2005-09-11
Just do this:

 sudo cp /usr/share/gnome/default.session ~/.gnome2/session

---

### Post by sethmahoney on 2005-09-15
Hey all, just a note to say I tried this with E16 and Breezy, and it works perfectly!  But anybody have any more info on getting Engage for E16 working?

---

### Post by linkunderscore on 2005-09-15
[QUOTE=darkmatter]Do it the easy way, System->Preferences->Session, find metacity and set the style to normal and apply the changes. Then, open a terminal and type the following:

```
killall metacity && sleep 1 && enlightenment
```
leave the terminal open for the moment.

Then go to System->Preferences->Session again. Find enlightenment and set order to 20, style to restart. Apply the settings then close the terminal. Enlightenment should quit and restart.

Next, log out with the 'save current setup' marked.

Log in, it will take a bit to load the first time (be patient) but you will now happily be using E instead of metacity. :smile:

EDIT: Just a side note, if you want E to handle the drawing of the desktop, use the configuration editor to set nautilus to not draw the desktop.

The results look like this
[http://img221.imageshack.us/my.php?image=screenshot1vd.jpg](http://img221.imageshack.us/my.php?image=screenshot1vd.jpg)
[http://img221.imageshack.us/my.php?image=screenshot24te.jpg](http://img221.imageshack.us/my.php?image=screenshot24te.jpg)
[http://img260.imageshack.us/my.php?image=screenshot30nm.jpg](http://img260.imageshack.us/my.php?image=screenshot30nm.jpg)[/QUOTE]


I really like your set up. What theme are you using and where did you get that background?

---

### Post by linkunderscore on 2005-09-15
I really like the theme that comes on the e-live cd. Does anyone knwo where I can download this theme?

---

### Post by linkunderscore on 2005-09-16
Allright...so I basically decided that I want to try e17. I want to install e17 seperately so that I can log into it by itself...not in gnome. 

How can I install e17 without removing e16(that i really like with gnome)? Do I install it like the instructions say? Or do I have to do something different so it doesn't overwrite e16.


I want to keep enlightened gnome(e16) 
BUT
I want to try out e17 as well (without implementing it in gnome) 

How do I do this?

---

### Post by juantxorena on 2005-09-16
There's any good file manager for E16? I'm tired of that slowly nautilus...

---

### Post by poofyhairguy on 2005-09-16
[QUOTE=linkunderscore]Allright...so I basically decided that I want to try e17. I want to install e17 seperately so that I can log into it by itself...not in gnome. 

How can I install e17 without removing e16(that i really like with gnome)? Do I install it like the instructions say? Or do I have to do something different so it doesn't overwrite e16.


I want to keep enlightened gnome(e16) 
BUT
I want to try out e17 as well (without implementing it in gnome) 

How do I do this?[/QUOTE]

I really don't know. I guess you have to compile e17 from scratch.

---

### Post by poofyhairguy on 2005-09-16
[QUOTE=juantxorena]There's any good file manager for E16? I'm tired of that slowly nautilus...[/QUOTE]


Ever tried rox?

---

### Post by juantxorena on 2005-09-16
[QUOTE=poofyhairguy]Ever tried rox?[/QUOTE]
 Never mind. I tried E16, but I didn't like it. The I tried E17 with Gnome, I didn't like it neither. Now I'm using only E17, without Gnome. Cool.

---

### Post by linkunderscore on 2005-09-18
[QUOTE=poofyhairguy]I really don't know. I guess you have to compile e17 from scratch.[/QUOTE]


Well, fyi...you can't install e17 without overwriting e16. It b0rkd my system and I had to fix it.  I can't wait until e17 is stable, because I really think i would switch to it competely.

---

### Post by TakisX on 2005-09-19
I installed e16 but i cant log in it.
I made the file you say in this thread but when i boot no option just gnome
Any ideas ?

---

### Post by Duncan_Idaho on 2005-09-30
[QUOTE=poofyhairguy]
Put this in regular terminal: sudo cp /usr/share/gnome/default.session ~/.gnome2/session
Then this:sudo gedit ~/.gnome2/session
Look for this line: 1,RestartCommand=gnome-wm --sm-client-id default1
Change the like to look like this: 1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1
[/QUOTE]
I can't find that line in my file, the ones starting with 1 are the followings
```
1,id=117f000001000112456197100000264310001
1,RestartStyleHint=2
1,Priority=20
1,Program=metacity
1,CurrentDirectory=/home/rokusho
1,DiscardCommand=rm -f /home/rokusho/.metacity/sessions/1128105839-9422-4168377607.ms 
1,CloneCommand=metacity 
1,RestartCommand=metacity --sm-save-file 1128105839-9422-4168377607.ms 
```

wich one is to be replaced?
it's ok if i just add that line to the end of the "1" section??

---

### Post by SilverTab on 2005-10-01
[QUOTE=NMUrugbysteve]Ok, I've gotten e16 install and running quite well within gnome. But now when i try to load synaptic, x freezes and I have to ctrl+alt+F1 and killall5 to get back into anything, anyone have any hints on this? I"m running on an thinkpad R51.[/QUOTE]


exact same problem here :(

I love the look/feel/speed of enlighted gnome, but can't get synaptic to run in it...

seems to be the only bug

---

### Post by darkmatter on 2005-10-01
[QUOTE=SilverTab]I love the look/feel/speed of enlighted gnome, but can't get synaptic to run in it...
seems to be the only bug[/QUOTE]

What command are you trying to launch synaptic with?

It should be:

```
gksudo /usr/sbin/synaptic
```

---

### Post by jesseman on 2005-10-01
All I have to say is e16 in Gnome is awesome. Lightning fast with all the eye candy I enjoy. I cannot wait for e17 to go stable and do this all over again when I upgrade to Breezy!

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=Duncan_Idaho]I can't find that line in my file, the ones starting with 1 are the followings
```
1,id=117f000001000112456197100000264310001
1,RestartStyleHint=2
1,Priority=20
1,Program=metacity
1,CurrentDirectory=/home/rokusho
1,DiscardCommand=rm -f /home/rokusho/.metacity/sessions/1128105839-9422-4168377607.ms 
1,CloneCommand=metacity 
1,RestartCommand=metacity --sm-save-file 1128105839-9422-4168377607.ms 
```

wich one is to be replaced?
it's ok if i just add that line to the end of the "1" section??[/QUOTE]


just add the whole line

---

### Post by darkmatter on 2005-10-02
[QUOTE=linkunderscore]Well, fyi...you can't install e17 without overwriting e16. It b0rkd my system and I had to fix it.[/QUOTE]

At least not with the version packaged for Ubuntu, unless you install E 17 with a different prefix.

The repositories really need to update dr16 to version 16.8, so both E 16 and E 17 can coexist in harmony.

---

### Post by gangalee on 2005-10-12
[QUOTE=poofyhairguy]
In the long run E16’s Engage:

[http://www.enlightenment.org/Applications/Engage/index.html](http://www.enlightenment.org/Applications/Engage/index.html)

Would be better than gdesklets. Anyone know how to add programs launchers to that thing? It can be installed from the Universe.[/QUOTE]

I'm using E16, how/whereis Engage? :confused:

---

### Post by ubuntuuser on 2005-10-19
Hi. Does anybody know how to change the icon size in the mouse menues? I want them to be roughly 20 px high. I haven't found an option to specify a certain icon size.

Is it possible to have icons on my desktop and still use enlightenment?

---

### Post by poofyhairguy on 2005-10-19
[QUOTE=ubuntuuser]Hi. Does anybody know how to change the icon size in the mouse menues? I want them to be roughly 20 px high. I haven't found an option to specify a certain icon size.

Is it possible to have icons on my desktop and still use enlightenment?[/QUOTE]


Use nautilus

---

### Post by Pedricko on 2005-10-20
Heres my story

I tried enlightened gnome and decided I didnt like it

so i apt-get removed enlightenment from the terminal and now when i log onto a standard gnome session, i have no window manager, just the desktop my home window and the frozen splash screen stuck on nautilus...

Help me restory metacity!

---

### Post by Wolveen on 2005-10-21
I dont get it...i followed the guide exactly, but now when I log into Gnome it tells me that a Window Manager is already running and to F1(edit) F2("blank") or F3(cancel).
F1 and F3 do sqaut.
F2 just spins a watch around forever.

What am I missing?

---

### Post by racter on 2005-10-22
this worked great for me, with one exception.

where poofyhairguy says to replace:
> 
1,RestartCommand=gnome-wm --sm-client-id default1


with

> 
1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1


i actually had to replace the line

> 
0,RestartCommand=gnome-wm --sm-client-id default1


just the '0' instead of '1' -- i actually replaced both of them.

i'm loving e17+gnome now, but i can't seem to figure out mapping a key to the act of moving a window from one virtual desktop to another.  in gnome/metacity this is "ctrl-alt-shift-[left/right]" for example.

i tried:
> 
enlightenment_remote -binding-key-add ANY Left "SHIFT|CTRL|ALT" 0 "window_desk_move_by" "0 -1"


and many (blind) variations thereof, but neither "window_desk_move_by" nor "window_desk_move_to" seem to do anything.  this is my first time using enlightenment, so i'm not too familiar with the key-binding system.  has anyone had any luck with this?

also where are the themez?  i only see 5 on get-e.org -- will e16 etc themes work?

thanks
jake

---

### Post by ubuntuuser on 2005-10-30
I have a question regarding character encoding. I have already started another thread [here]("http://ubuntuforums.org/showthread.php?p=454482#post454482") about that. I would be very thankful if somebody here could help me with that one. Thanks.

---

### Post by endersshadow on 2005-11-01
Just wanted to give a quick update.

I did this on Breezy final, and it worked fantastically.

Also, I spent forever trying to figure out how to install themes on Enlightenment, and I've seen that some people have asked but it got lost in the fray.  Make sure that you have Nautilus desktop drawing off (apps>nautilus>preferences-->show_desktop unchecked in configuration editor)

First, get a theme.  I found the following site, and I liked it's huge array of themes: [http://themes.freshmeat.net/browse/60/](http://themes.freshmeat.net/browse/60/)

Second, download it and save it to ~/.enlightenment/themes

Third, untar it.  It should create a new folder, but if it doesn't, you'll manually have to make it a folder (such as "CoolTheme" or something) and put all of the contents into there.

Fourth, the manual and the GUI way to change the theme.  First, the manual:

```
sudo gedit ~/.enlightenment/user_theme.cfg
```

Simply make the name of the folder (CoolTheme) the only contents of the cfg file on the first line.  Restart Enlightenment by CTRL+Left Click on the desktop, and selecting "Restart Enlightenment" (they make it tough).

The GUI way: CTRL+Left Click on the desktop, and Restart Enlightenment.  Then, CTRL+Left Click again, select Themes>CoolTheme (where CoolTheme is the desired theme).  Note that this requires you to have unpacked the theme into the ~/.enlightenment folder already.

Hope this helped!

This is the way that I've found it best to do it, though I wasn't overly impressed with E16.  It just didn't seem as clean to me, even after I figured out the themes and such.  While Metacity has its problems, I'm  running it on a 900Mhz P2 wannabe with 256MB SDRAM and it's doing just fine.  To each his or her own, I suppose.

---

### Post by Turtle.net on 2005-11-21
Just a little message to thank you. I spend a lot of time to try to find a compromise between Gnome and Enlightenment.
I really love enlightenment, but I really like the usefullness of gnome (and my gitlfriend prefer gnome anyway)...
For me Enlightened Gnome is the perfect compromise (and its really fast ;-))
So in one word THANKS !!!

---

### Post by WetWilly on 2005-11-27
[QUOTE=racter]this worked great for me, with one exception.

where poofyhairguy says to replace:

with

i actually had to replace the line


just the '0' instead of '1' -- i actually replaced both of them.
[/QUOTE]

could u extend that part?

I use Breezy and in my sudo gedit ~/.gnome2/session I have

0,RestartCommand=gnome-wm --sm-client-id default1

and

1,RestartCommand=gnome-panel --sm-client-id default1

Which one am I supposed to replace? And with what?

---

### Post by daedalusman on 2005-12-12
> Look for this line:

Quote:
1,RestartCommand=gnome-wm --sm-client-id default1



That line was not present inside my file. Should I just add it? I have E17 installed and I can login to it from GDM so I know it works but I can't add it to start up as I don't have that line in my sessions file. Thanks for the help.

Edit
In fact nothing with gnome-wm was in that file, I looked through the whole file and there is one line that says RestartCommand=gnome-wm --sm-client-id default1. Theres a line for metacity, which is 0,RestartCommand=metacity --sm-save-file 1134421859-13054-2623429848.ms, dont know if that will help at all but there it is, other lines are for volume-manger, nautilus, gnome-panel, cups, rhythmbox, gaim, update-notifier, gnome-terminal, and gedit, not in that order. 

Another thing, since I have tried doing this my applications dropdown menu no longer displays properly. What it does, it will flash for half a sec and then there will just be a very small square just underneath the gnomefoot. Can some one help me to get this back to normal. Thanks

---

### Post by abyssspecter on 2005-12-13
okay, maybe im just a n00b, but im having a problem. 

I installed E16, followed the thing to the T. but, i tried logging in to enlightenment, and it looks nothing like any of the screenshots if found. I mean, i dont even have any ICONS. 

i really like what ive seen, but I'd like to keep GAIM, or get another similar messanger, and id also like to keep my music, and Continue playing Steam, which im running on Wine.

If someone could help me out, id be very greatful.

---

### Post by madjinx on 2005-12-13
[QUOTE=daedalusman]That line was not present inside my file. Should I just add it? I have E17 installed and I can login to it from GDM so I know it works but I can't add it to start up as I don't have that line in my sessions file. Thanks for the help.

Edit
In fact nothing with gnome-wm was in that file, I looked through the whole file and there is one line that says RestartCommand=gnome-wm --sm-client-id default1. Theres a line for metacity, which is 0,RestartCommand=metacity --sm-save-file 1134421859-13054-2623429848.ms, dont know if that will help at all but there it is, other lines are for volume-manger, nautilus, gnome-panel, cups, rhythmbox, gaim, update-notifier, gnome-terminal, and gedit, not in that order. 

Another thing, since I have tried doing this my applications dropdown menu no longer displays properly. What it does, it will flash for half a sec and then there will just be a very small square just underneath the gnomefoot. Can some one help me to get this back to normal. Thanks[/QUOTE]

same here, cant find that line anywhere.

---

### Post by jerrygofixit on 2005-12-15
I also got that problem saying I was using 2 window managers, so I had to revert back to regular gnome. Anyone know how to get around this, I'd love to speed up gnome. I'm a bit of a reborn-noob (I just fixed my ubuntu after being down for a few months) so if you could help me, the more detailed, the better, thanks all.

---

### Post by ddumanis on 2006-01-03
I installed E16 and the speed increase is definitely noticeable. 

One warning to other newbies: my line in gnome2/session said
 1,RestartCommand=gnome-wm --sm-client-id default0

So, accordingly, I had to change it to
 1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default0

to get Enlightenment to work.  (When I just changed it to the "default1" line, I ended up with NO window manager.)

Somebody a little more experienced probably would have picked up on this right away.

Anyway, thanks for a great tip, poofyhairguy. I'm much happier with my old 500 mhz Dell Latitude now.

---

### Post by BoneyOne on 2006-01-04
First of all, I know this is an older how-to, but thanks!! I tried Enlightenment a while back by itself and never could get it to function correctly. But Elightened Gnome rocks. I'm currently running E16 on Breezy.

Only one thing...when I attempt to install
```
sudo apt-get install emodules engage entrance eclair elicit entice examine eclips
```

I recieve the depenancy errors and it will not install. Any way to get around this? I've read through the entire thread and noticed others with the same issue, but wasn't able to find a solution in the thread (doesn't mean it wasn't there...just I didn't see it).

Thanks

---

### Post by tonydm on 2006-01-05
HI All,

I'm new to Ubuntu, and I do like it alot, but confused :confused: .  I've been going through this Enlightenment thread an found it very interesting.  I've wanted to give Enlightement a try for some time.  When I search for it in Synaptic I doing find it.  It also is not found with the command sudo apt-get install enlightenment.  Nor is it found with apt-cache search "^enlightenmtent".  Could someone give me a little help?  I'm not familar with repository settings, etc.  Thanks!
 
Tony

---

### Post by Turtle.net on 2006-01-05
You have to install extra repository to install enlightenment (I think it's in universe).
just take a look at [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by tommie-lie on 2006-01-09
I use E17 from shadoi's repository (debs from 08-14-2005) and want to replace metacity with E. That works well for a running session (kill metacity, then start E) or for a new session if I use the method provided in this howto (the .gnome2/session thing), but whenever I log out and start Gnome again, it has forgotton that it should also load Enlightenment. I have to start Enlightenment manually to make it work. After I start it manually, all works perfectly until I log out again.
What seems strange to me is that Enlightenment is not listed in the current session (System -> Settings (or Properties in English?) -> Session. Maybe that is the core of the problem, but I have no idea how I can make it apear in the session. Any ideas?

My Gnome is 2.12.1, the latest from the Breezy repositories.

---

### Post by john16384 on 2006-01-10
In the "Actual Trick" section, you mention copying the /usr/share/gnome/default.session to ~/.gnome2/session and several other actions.  You can however simply replace them with this:

> echo export WINDOW_MANAGER=/usr/bin/enlightenment >> ~/.gnomerc

Just check to make sure you didn't already have a WINDOW_MANAGER defined in .gnomerc

---

### Post by tommie-lie on 2006-01-10
[QUOTE=john16384]```
 echo export WINDOW_MANAGER=/usr/bin/enlightenment >> ~/.gnomerc
```[/QUOTE]I already tried that. I had no .gnomerc before, with just this line in it, I still have no windowmanager in Gnome (it does not start metacity). If I add "#!/bin/bash" to the beginning of the file, nothing changes, still the same problem.

---

### Post by tommie-lie on 2006-01-13
I worked around that by putting E in the session's autostart programs (correct term in English locale?). This is not really satisfying, though, a *real* support for  E as window manager would be a nicer solution.

---

### Post by johnnymo87 on 2006-01-13
I'm not sure if anyone has caught this yet, but there's an error in the original post.

The file that he recommends to edit:

> Look for this line:
**1,RestartCommand=gnome-wm --sm-client-id default1**  
Change the like to look like this:
**1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1**  


should really be:
> **0,RestartCommand=gnome-wm --sm-client-id default0**
changed to:
> **0,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default0**

Just turn the 1s to 0s.

Edit: This could be just me though.

---

### Post by j-a-p on 2006-01-19
I've managed to get E16 to load but I have no left click (I can't access any apps).

Anyone know how to rectify?

---

### Post by eliabramo on 2006-01-19
> j-a-p
I've managed to get E16 to load but I have no left click (I can't access any apps).

Anyone know how to rectify?

I fix it by changing the permission of the menu.cfg files in usr/share/enlightenment/config and allow writing to the user, but it's on your own risk.
and don't forget do do "maintenance>regenerate menus" by middle click.

---

### Post by Jakanden on 2006-01-30
I just wanted to say this is a great guide. I found this upon searching for other things and decided to give it a try. Everything worked great =)

---

### Post by poofyhairguy on 2006-01-30
[QUOTE=Jakanden]I just wanted to say this is a great guide. I found this upon searching for other things and decided to give it a try. Everything worked great =)[/QUOTE]

I am flattered people are still using this old thing.

---

### Post by Jakanden on 2006-01-30
Heh - I am a linux newbie and was just looking for things to play around with. The last time I used linux was RedHat 7.0 and got fed up and stopped using it. Ubuntu has me playing with it again.

Next goal is to figure out how to setup different themes for E16. Maybe even update to E17 depending on the difficulty =)

---

### Post by mellamogsd on 2006-02-17
Yes I came across this guide today as well and tried it out. Excellent setup! Enlightenment 'feels' much faster than metacity, and especially load times are a snap. I don't have the greatest sys specs (1.4 AMD athlon, 256 RAM) but it cranks with under 50% VM used. Niceeeee.      

My problem is: I went back to metacity to do some actual comparisons of load times, mem usage, etc. (very scientifical-like). I merely deleted the "trick" line. Everything is just fine except I noticed I have no interface with the desktop now. Normally in Gnome there's right-click options such as create folder, etc (or am I just losing it?:-k ) but I don't have any access to them. I'm stumped.

Let me know any suggestions.:???: 

~graham

---

### Post by quadomatic on 2006-02-19
For some weird reason, when I put themes into the folder where your supposed to put them, the theme browser will never show them....what's going on?

BTW:I installed e17 with the cvs guide. I'm putting the themes in /opt/e17/share/enlightenment/data/themes

---

### Post by almahtar on 2006-03-02
quadomatic: try middle clicking your desktop, going to maintenance->regenerate menus.
Wait a moment, it'll give you a "menus generated" dialog.  Hit ok, then middle click your desktop again and check out the themes list.  If it doesn't include all your themes then, the themes are not installed correctly.

---

### Post by max-power on 2006-03-22
hey have the repositories moved? couldnt seem to get in

---

### Post by Turtle.net on 2006-03-22
Which one ?
Sometimes some repo can be outline (technical problem, maintenance...i don't know).

---

### Post by Maelgwyn on 2006-04-05
weird problem - How do I get menus back? A la the Gnome menu at the top of the screen... I've installed & run everything, so I'm running Enlightened Gnome, but if I middle-click and go to User Menus > User Application list, all I get is XTerm, Gnome Terminal, GIMP, XMag, X-Chat, XMan & XMMS (the last four aren't even installed on my computer!:confused: )

I'd like to get menus back... The only E-like menu I get from clicking on the background is the middle click... Right click gives me the Gnome Desktop menu, and left click selects etc just like before..

I feel like such a n00b! ](*,)

EDIT: I'm stoopid... :P Fixed.

Next question though - Whenever I login to Gnome using E16, I get an error message saying that there's another WM running, and do I want E to re-write something for me...
Tad confused...

---

### Post by Nonno Bassotto on 2006-05-11
I'd like to try this out, but I'm a little scared about the complaints of some people who are not able to restore their default window-manager.
In the first someone also asked if it is possible to get two different sessions (gnome and E-gnome) so that one can choose at the login. I tried to look through the whole post but I didn't find an answer. Can someone correct me or confirm that I have to choose between metacity and enlightenment?
Thank you

---

### Post by Nonno Bassotto on 2006-05-12
I reply to myself about the double configuration (see previous post; I just would like to have a choice between standard and enlightened gnome right at the start). In /etc/gdm there are some scipts put in folders named like
PostLogin
PostSession
etc. which appear to be launched by the gdm when appopriate. A friend of mine suggests it should be not too difficult to create two distinct .gnome2/session files and make a script to switch between them based on the choice you make at the gdm.
BUT I' can't find where the information about the possible session choices is stored. So I can't add a Enlightened Gnome session. Anybody willing to elaborate on this and try something?

---

### Post by bohboh on 2006-06-17
This thread started a while ago with talk that E17 was unstable, is that still the case?

I would like to install one and ideally like it to be E17, but only if it stable enough.

Thanks

---

### Post by adam.skinner on 2006-06-18
I did an apt-get install of enlightenment, and I noticed that I have two new entries in my wm list:

E-Gnome and E-KDE.

How does that relate to this thread?  Is the integration now packaged with the enlightenment install?

---

### Post by Raavea on 2006-06-18
> [Default]
num_clients=6
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
I don't seem to have the line needed. Do I modify;
*0,RestartCommand=gnome-wm*
Or do I modify;
*1,RestartCommand=gnome-panel*
PS: e16 :D

EDIT: I went ahead and altered it to;
> [Default]
num_clients=6
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
And it seems to have worked. I just wish I could find a site with some e16 themes...

---

### Post by Third Thoughts on 2006-07-22
> **bohboh said:**
> This thread started a while ago with talk that E17 was unstable, is that still the case?

I would like to install one and ideally like it to be E17, but only if it stable enough.

Thanks

I run E17 and I find that its fairly stable. It still crashes occasionally, but when it crashes it simply gives you the option to exit or restart. If you restart it doesn't mess with anything you're working on, just reboots the window manager. All your apps stay open and unmessed with. 
That being said, its still a little rough of around the edges. Sometimes you have to mess around with the command line to configure things. And there's definitely a time investment that goes into setting things up (ie, getting the applications menu generated). Also, I haven't found a good package or repository, so I'm compiling from CVS using a script found in this thread. 
[http://www.ubuntuforums.org/showthread.php?t=97199](http://www.ubuntuforums.org/showthread.php?t=97199)
So its fairly stable, but still not perfectly user friendly.

~Andrew S.

---

### Post by moore.bryan on 2006-07-23
had a ton of problems post-install... said it couldn't find my gdm and it wouldn't load startx, saying it was corrupted.  in case anyone else runs into that problem, i was able to get everything okay by just replacing the /.gnome2/session with the old /usr/share/gnome.desktop.
[code]sudo cp /usr/share/gnome.desktop /.gnome2/session[code]
just in case...

---

### Post by corefile on 2006-08-21
3. Applications > System Tools > ConfiguratioN Editor > apps > nautilus > preferences > UNCHECK show desktop. (thanks bored2k)

Trying to find how to turn this off, but I don't have that menu item.

EDIT:
I was able to do it using the gconf-editor, but would still like to know what I need to install to get the Configuration Editor

---

### Post by Warbo on 2006-08-23
I didn't want to read all 26 pages of comments, so forgive me if this has already been mentioned.
I use Enlightenment 0.16.8, since it offers Composite support (xcompmgr makes E really screw up if you use 0.16.7 from the repos), and this can be installed either by using the source for 0.16.8.2 from E's website, or by getting an RPM from there for 0.16.8.1 and using alien. The only thing you may have to do to get these working in GNOME is run "sudo apt-get --download-only install enlightenment-data" then get the enlightenment-data package from /var/cache/apt/archives, open it with file-roller and extract the data.tar.gz from it, then open THAT in file-roller and get the xsession file from it and put it in the right place (follow the structure of the data.tar.gz file).

Since Gdesklets goes really slow I use Adesklets to give me icons instead. Adesklets takes a little more setting up, but I have written a how-to on help.ubuntu.com/community if anyone wants to use it.

E16 has always had a place in my heart ever since I first used Linux with RedHat 9. I have tried LOADS of different desktops, but somehow always come back to E-GNOME, and I am glad that the occasional cool feature is still being added.

---

### Post by StickyC on 2007-01-06
Great writeup! I followed things pretty tightly, although in my **./gnome2/session**, I had to change **0,RestartCommand**... instead of **1,RestartCommand**...
Also, I didnt have any left-click functionality until I changed themes and turned off Show Desktop (even after rebuilding the menus).

Two questions:
I, too, dont have any System menu under applications - did anyone resolve how to get that menu? (AFAIK, I never had it in the first place)

When logging in, I get the following error: "**Xsession: unable to launch "starte16 GNOME" X session --- "starte16 GNOME" not found; falling back to default session.**". Clicking OK seems to log in normally and everything works, but the error message is annoying. Any idea what could be causing that and how I'd got about fixing it?

Thanks!

---

### Post by zazzsa on 2007-01-23
It worked right for me first time   WOO HOO !!!!!!!!   :guitar: 

Now that I have been Enlightened  Can someone please explain it to me what all that can be done with this wonderful program .

---

### Post by andy gee on 2007-01-28
I just installed E from Ubuntu repos. Enlightenment works well, but I get the same error as above:

"Xsession: unable to launch "starte16 GNOME" X session --- "starte16 GNOME" not found; falling back to default session.". 

Unfortunately, my default was XFCE and it goes back to that - I can't get E-Gnome. I even changed the default to E-Gnome, but it defaulted to the previous default (ie still XFCE). This is more than an annoyance - I can't partake in the hybrid beauty of E-Gnome! Help me please, Obi Wan!

---

### Post by klittzzer on 2007-02-28
I dunno if this will make anyones life easier when trying to get e17 and gnome working together. The how2 at the start of this post didn't work for me but I have found a much easier way to get all of the gnome stuff, nautilus etc etc to work in e17 with all of the settings I had in gnome.

All I did was install gtk-theme-switch with synaptic (I don't know if this is necessary) and when logged into e17, entered

:~$ gnome-theme-manager

in a terminal (works in eterm and the one that comes with gnome) while inside e17 and choose the GTK2 style I want in the control tab and likewise with the icons. Metacity is obviously disabled in e17 and the terminal will moan about not being able to open Metacity and thus there is no option to select a window border in the theme settings.

Once I have done that I have all the drop shadows etc that Enlightenment offers along with the gtk controls with all of my applications I have in gnome.

I prefer to search for files with nautilus so I created a launcher in the ibar in e17 which runs with 'nautilus --no-desktop'. Same goes for other gnome apps.

I can't seem to get the e17 apps,(entropy etc rtc) to install with synaptic from the SeerOfSouls repos because of dependency issues (eet, libeet, same thing aren't they) which all end up with libeet not being available. 'sudo aptitude install emodules0all' or 'sudo aptitude install entropy' doesn't work. I know how to compile these missing dependencies and know where to find them. The problem is, on the web page that lists the lib files there are about a dozen 'eet' files with diff numbers and I haven't a clue as to what one I need. If anyone can help with this I will be grateful.

I have attached a couple of screen shots [ATTACH]26331[/ATTACH]

[ATTACH]26332[/ATTACH]

[ATTACH]26333[/ATTACH]

to show what I am getting at.

PEACE

kl

---

### Post by crackers8199 on 2007-03-05
when i modify the line specified, i get a message telling me that running enlightenment directly is bad - what gives?  i can't seem to get this to work any other way...

---

### Post by Sweet Mercury on 2007-06-13
This is interesting.

Here is my session file

```
[Default]
0,id=117f000101000118119610300000120410000
0,RestartStyleHint=2
0,Priority=40
0,Program=gnome-panel
0,CurrentDirectory=/home/mason
0,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-eiHuRr/ 
0,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-eiHuRr/ --sm-client-id 117f000101000118119610300000120410000 --screen 0 
1,id=117f000101000118119610300000120410001
1,RestartStyleHint=1
1,Priority=40
1,Program=gnome-volume-manager
1,CurrentDirectory=/home/mason
1,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-mfwZis/ 
1,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-mfwZis/ --sm-client-id 117f000101000118119610300000120410001 --screen 0 
2,id=117f000101000118119610400000120410003
2,RestartStyleHint=2
2,Priority=20
2,Program=metacity
2,CurrentDirectory=/home/mason
2,DiscardCommand=rm -f /home/mason/.metacity/sessions/1181718212-10886-3690151515.ms 
2,CloneCommand=metacity 
2,RestartCommand=metacity --sm-save-file 1181718212-10886-3690151515.ms 
3,id=117f000101000118119610300000120410002
3,RestartStyleHint=2
3,Priority=40
3,Program=nautilus
3,CurrentDirectory=/home/mason
3,CloneCommand=nautilus --sm-config-prefix /nautilus-cMv9dV/ 
3,RestartCommand=nautilus --sm-config-prefix /nautilus-cMv9dV/ --sm-client-id 117f000101000118119610300000120410002 --screen 0 
4,id=117f000101000118119610500000120410006
4,RestartStyleHint=1
4,Program=update-notifier
4,CurrentDirectory=/home/mason
4,CloneCommand=update-notifier --sm-config-prefix /update-notifier-YkVU4o/ 
4,RestartCommand=update-notifier --sm-config-prefix /update-notifier-YkVU4o/ --sm-client-id 117f000101000118119610500000120410006 --screen 0 
5,id=117f000101000118119610400000120410004
5,Program=gnome-power-manager
5,CurrentDirectory=/home/mason
5,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-qr5ZNo/ 
5,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-qr5ZNo/ --sm-client-id 117f000101000118119610400000120410004 --screen 0 
6,id=117f000101000118119610500000120410005
6,RestartStyleHint=2
6,Priority=50
6,Program=gnome-cups-icon
6,CurrentDirectory=/home/mason
6,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-nCkxbs/ 
6,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-nCkxbs/ --sm-client-id 117f000101000118119610500000120410005 --screen 0 
7,id=117f000101000118161702600000052440000
7,RestartStyleHint=0
7,Program=evolution-alarm-notify
7,CurrentDirectory=/home/mason
7,CloneCommand=evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-mpyMOs/ 
7,RestartCommand=evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-mpyMOs/ --sm-client-id 117f000101000118161702600000052440000 --screen 0 
8,id=117f000101000118153395900000052030003
8,RestartStyleHint=0
8,Program=gaim
8,CurrentDirectory=/home/mason
8,DiscardCommand=/bin/true 
8,CloneCommand=gaim 
8,RestartCommand=gaim --session 117f000101000118153395900000052030003 
9,id=117f000101000118174860700000053570010
9,Program=gedit
9,CurrentDirectory=/home/mason
9,CloneCommand=gedit 
9,RestartCommand=gedit --sm-client-id 117f000101000118174860700000053570010 --screen 0 
10,RestartCommand=restricted-manager --check 
11,RestartCommand=nm-applet --sm-disable 
12,RestartCommand=/usr/bin/system-config-printer-applet 
13,RestartCommand=gdesklets 
num_clients=14
```

Like a few other posters, I didn't have the line from the OP that required replacing (1,RestartCommand=gnome-wm --sm-client-id default1), and, as per advice from this thread, I just added the line to my file.

It didn't replace Metacity with E16, it instead only loaded half of my startup session, and it still loaded Metacity!

Why doesn't my session file look like other people's?

---

### Post by DGentry on 2007-09-03
If I followed this and decide I don't like it, what do I need to do to get back to my default metacity thing.

I found that when I would left click on the desktop I would get my apps and stuff. but like when I'd mouse over to like GTK I would get a fly out box with a bunch of apps and then my user apps box would pop up to the very top and I'd lose everything and couldn't click on anything.

If I try opening a term window and doing the metacity --replace This is what I get.

doug@Doug-Linux:~$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager
doug@Doug-Linux:~$

---

### Post by cooldude on 2007-09-19
There's a whole lot easier way then that. Just log into Enlightnment & in a terminal type: gnome-panel & It does not give total enlightenment integration but gives you an idea. I think there was another command to  add icons to desktop but not sure.

---

### Post by revchris on 2007-09-22
I installed e17 over e16 which seems to have went fine.  Only problem is I can't get e17 to work with gnome.  I don't have an option for egnome like I did with e16.  I redid the file(~/.gnome2/session) again and it didn't work.  Should the file be in a different place?  or will that not work in e17?

---

### Post by jacob01 on 2007-11-09
yea i just got it installed but i had to open up a terminal and run e16, i also used the e16menuedit2 from the repository, the only difference i noticed was on one line stared with a 0 and ended with a zero bun in your post it said it started and ended with 1, so i replaced it and yea worked, looks pretty cool, but im fine with the default. nice work,




i am a bit of a noob but i still accomplished this, then reversed every thing and uninstalled it with out a flaw.

nice how-to

---

### Post by zach12 on 2007-12-14
Hello
I just installed E16 and would like be able to right click to open the Menu

How can i do that?

---

### Post by DTHCND on 2009-12-14
I am VERY new to Ubuntu, but am sort of getting the hang of it but I don't understand what to do... I have used a command similar to ```
sudo apt-get install enlightenment
``` but when I try this certain command it gives me this response 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment has no installation candidate
```
What did I do wrong?

---

### Post by lemmy999 on 2009-12-14
The thread you are posting in is over 3 years  old and the last post was in 2007. My suggestion would be to start a new thread in Desktop Environments. I think you will probably get a quicker response there.

---

### Post by 1proton on 2010-05-17
> **DTHCND said:**
> I am VERY new to Ubuntu, but am sort of getting the hang of it but I don't understand what to do... I have used a command similar to ```
sudo apt-get install enlightenment
``` but when I try this certain command it gives me this response 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment has no installation candidate
```What did I do wrong?

try 'sudo apt-get install e16'
:)

---

### Post by Nick_Jinn on 2010-09-01
> **lemmy999 said:**
> The thread you are posting in is over 3 years  old and the last post was in 2007. My suggestion would be to start a new thread in Desktop Environments. I think you will probably get a quicker response there.


I am considering posting a new thread, but how often do you get such a detailed instruction manual on how to set up something like this? I almost think it would be better to modify and rewrite the OP updated for the advanced in E17 than to start over with a basic discussion which might only get a few replies. 

E17 is now almost stable and ready for its official release, isnt it? Thats what I heard over on OpenGEU.


I really prefer the Gnome controls and menus to Enlightenments....its just easier to use, and I dont care if Nautilus is slow...some of its features I consider essential.

If I could just have the animated backgrounds, mostly the fire and rain, all going on my Gnome desktop with Compiz, I would be a happy customer. 


This is a really valuable how-to, though it should probably be updated.

---

### Post by kokoshmusun on 2010-12-04
Yes, I just posted about this question, and then found this how-to (which didn't work with Maverick).  It would be great to try E17 with GNOME, so if anybody knows how things have changed since 2005 and can do an update, that would be swell.

---

