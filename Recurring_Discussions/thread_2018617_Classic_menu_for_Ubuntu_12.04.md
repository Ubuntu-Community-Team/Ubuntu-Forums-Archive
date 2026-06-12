---
title: "Classic menu for Ubuntu 12.04"
date: 2012-07-06
forum: Recurring Discussions
---

### Post by aimwin on 2012-07-06
**You can install Classic Menu**

With 2 options

Option 1 go back to the old Gnome Classic.
            (which also you can run Unity 2D shell and get Hybrid Desktop)

Option 2 stay with unity and install Classic Menu and Place Indicator
            (you will also get Hybrid Desktop in this option too)

Option 1 go back to the old Gnome Classic.

1. click on Ubuntu Software Center.
2. Key in the search box "Gnome Shell"
3. Click Install.

4. LOG OUT.

5. on the log in window,
   click on right hand top corner setting-round icon.

6. choose classic menu or Classic Menu (no effect) for older machine.

7 Key in the password and click log in.

8 You will get Classic Menu with only Applications and Places Tab.

Please experiment to choose "Gnome" Option for Gnome 3 which is similar to Unity defaut desktop in many ways.

You can log out and pick your choice of those desktop and login anytime.
I have switch back and forth so many times, it is very stable and will not crash.

Option 2 stay with unity and install Classic Menu and Place Indicator

1. open Terminal (Click on Dash Home, type T in a pop up search box, Terminal icon will appear, click on it)

2. copy the following lines and paste into Terminal and press Enter.
only one line, at a time.

sudo apt-add-repository ppa:diesch/testing
sudo apt-get update && sudo apt-get install classicmenu-indicator

3 Install "Place" indicator.
[https://github.com/shamil/indicator-places](https://github.com/shamil/indicator-places)

1. Download the latest version from above link
2. Extract the files to the desk top,
3. Right Click the file "indicator-places.py", open property, 
   click permission tab, and check "Allow Executing File as Program" 
4. Run indicator-places.py by double click and choose RUN option.

Many indicators for desktop customisation is at
[http://askubuntu.com/questions/30334/what-application-indicators-are-available](http://askubuntu.com/questions/30334/what-application-indicators-are-available)

---

### Post by tstduke on 2012-07-09
Thank you, this is exactly what I have been looking for!
It makes 12.04 look and behave a little bit more like good old 10.04!

Ubuntu developers should really offer a "classic" version option at the install screen. No one wants to type to find an application (providing they even know what it is called) when they can just use the mouse!

---

### Post by aimwin on 2012-07-14
> **tstduke said:**
> Thank you,........ more like good old 10.04!

Ubuntu developers should really offer a "classic" version option at the install screen. No one wants to type to find an application (providing they even know what it is called) when they can just use the mouse!

They did offer in DVD Edubuntu 11.10
[http://ubuntuforums.org/showthread.php?t=1900756](http://ubuntuforums.org/showthread.php?t=1900756)
............
my comments ====>
After installing Edubuntu 11.10 DVD, today,
I found that Edubuntu provide the "Option" during Installation,
to choose Gnome Classic (fallback module).
That is what we just need during our main UBUNTU installation.
alongside the choice for 3rd party software and codec.
...........................

Why they still did not offer in new Desktop 12.04?

My quess, they are afraid that people will not use UNITY DESKTOP 
as much as they would like us to do so.

So they forced all loyal clients to use UNITY Desktop.

Well they have agenda to push for financial survival for Canonical.
The more people use UNITY, the more chance they can sell OEM.

And MORE CHANCE OF UBUNTU GET ON TO TABLET, MOBILE AND TV. 

More people help testing. more stable.

So I understand them. AND SUPPORT THEM ON UNITY.

BUT .... I disagree that they did not provide "OUT STANDING CLASSIC MENU OPTION"

And they end up loosing so many supporters to other distributions.

I think still they should provide the option when we install Ubuntu.
They explain that, not enough disk in CD,
so they have to force only one desktop installation.

But I propose it here again, to our UBUNTU community, to voice our opinion, 
the more we demand, may be they will listen.

I don't know if they have option in DVD version of 12.04 as with EDUBUNTU 11.10.
I have no time to look at that yet, I will later do so.

But for the CD Live version.
They should have an option, 
Classic Menu 

WITH CONDITIONS you have to have internet connection,
and Ubuntu Installer will down load the additional files,
as we did when we install GNOME SHELL.

AND THAT WILL MAKE LIVE OF OUR COMMUNITY EASIER AND 
AT THE END CANONICAL WILL NOT LOOSE AS MUCH SUPPORTERS TO MINT.. AND OTHERS..

Quote from "drdos2006"
[http://ubuntuforums.org/showpost.php?p=11570728&postcount=4](http://ubuntuforums.org/showpost.php?p=11570728&postcount=4)
Personally I think that giving consumers an option to have the Classic Menu,
would be beneficial for loyal Ubuntu users and allow new users to transition away from Windows. ............

---

### Post by chocklet on 2012-07-14
aimwin, many of your sentiments are dear to me.  In my own perfect world I'd be 100% behind you.  Unfortunately, the world seems to go its own way, heading for a future that completely ignores my preferences!

To get to the future world, Ubuntu has to make decisions about policy and about resources.  To be successful in a competitive field, an organization must be concerned with a clear vision, with internally consistent and focused policies that support the vision, and with realistic resource management.

A multiplicity of options makes everything more difficult.  It sends conflicting messages to users/clients and to staff.  The vision is blurred, policy gets confused, resources get scarce, and resource management becomes a hassle.

So, I'm not going urge Ubuntu/Canonical to widen their focus to include old conventions, even conventions to which I am addicted.

I'm willing to put up with changes to my daily desktop environment to begin to adapt to a computing world that will be different 3 years from now.  In 2015 desktops will be only a fraction of a computing scene dominated by small screens (tablets and smartphones).  Tablet sales alone will exceed desktop sales.  Small screen computers will be common in the work environment.

Those in my family must be prepared for that world.

In the meantime we, in my home, have installed ClassicMenuIndicator as you have suggested.  We also use modified launchers (.desktop files edited to add several programs to a laucher).  These modifications ease the pain that we are feeling as we are forced to change.  We are slowly warming to the new environment and eventually will be able to adapt to a pure Unity desktop.

---

### Post by fjgaude on 2012-07-14
@chocklet. Very good... the way the world is going, even for the desktop computers, and of course the tablets, is touch screens. When Windows 8 comes out it will be clear how the world reacts to it all.

---

### Post by QDR06VV9 on 2012-07-15
> **chocklet said:**
> aimwin, many of your sentiments are dear to me.  In my own perfect world I'd be 100% behind you.  Unfortunately, the world seems to go its own way, heading for a future that completely ignores my preferences!

To get to the future world, Ubuntu has to make decisions about policy and about resources.  To be successful in a competitive field, an organization must be concerned with a clear vision, with internally consistent and focused policies that support the vision, and with realistic resource management.

:confused: _IMHMO They made the wrong Choice!!!!!!!!!!!!_
Sorry Very PASSIONATE About this. Always had a Great deal of respect for the Devs, and have used Buntu for many many Years! Happily.
But Unity will [COLOR="Red"]Never[/COLOR] Be on my Machines!!
No Flames. Just Choice..

---

### Post by kansasnoob on 2012-07-15
I'd just remind everyone that opinions belong at the community cafe:

[http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

---

### Post by aimwin on 2012-07-15
To pay respect to the comments of kansasnoob and cariboo907
I have remove my opinions from this post, but later re post my opinion, since it is now move to the CAFE.
Thank you for reminding the essense of this thread,
and I know it should also be in the wiki Document.., which I have not got time to learn how to use it yet.

> **chocklet said:**
> aimwin, many of your sentiments are dear to me.  ......
.......To be successful....... with realistic resource management.
......... resources get scarce, and resource management becomes a hassle.

So, I'm not going urge Ubuntu/Canonical to widen their focus to include old conventions, even conventions to which I am addicted.


And I am not going to urge them to slow down too, they are too slow already.
And I am fully support their move.
[http://ubuntuforums.org/showpost.php?p=12104759&postcount=10](http://ubuntuforums.org/showpost.php?p=12104759&postcount=10)

But....
> **chocklet said:**
> ..........
....
In the meantime we, in my home, have installed ClassicMenuIndicator as you have suggested.  We also use modified launchers (.desktop files edited to add several programs to a laucher).  These modifications ease the pain that we are feeling as we are forced to change.  We are slowly warming to the new environment and eventually will be able to adapt to a pure Unity desktop.........

many more will still use their Desktops and Notebooks for 10+ years yet.
And many will not waste time to change and learn new things that aren't benefit them immediatly. 

So those that don't want to change at this stage need an easy options.
and UBUNTU/CANONICAL can waste just a few hours to prepare that option,
when the installation menu progress.

Gnome Shell or that Classic Menu Indicator show that "Canonical does not provide updates for GNOME Shell (nor the Classic Menu Indicator). Some updates may be provided by the Ubuntu community.".....

So the rest of the conventional works are done by community anyway.
And Canonical don't have to bother with that.

But for the sake of Canonical's own popularity and Ubuntu Loyal users,
it will cost Canonical Nothing but just a few hours of the team,
just to give a message and a link during installation menu.
[B]
Am I asking for too much from Canonical Staff to pay tribute to their hundreds thousands of their followers?[/B]

[COLOR="Red"]Just a message and a link and a script,[/COLOR]

 not even a 1MB space on the Live CD for that classic menu installation option.

WITH CONDITIONS you have to have internet connection,
and Ubuntu Installer will download Gnome Shell additional files,
and the "script" to config the desk top to Gnome Classic after Reboot.
(as we did when we install GNOME SHELL).
[B]
The rest of the works ARE the built in functions that UBUNTU has.[/B]

Canonical must take care thier "NON-PAID" customers too,

since they help advertising UBUNTU to today success and for the future success too.

and will at the end help UBUNTU to be the most popular as it has been.

I am expressing my comments hope to help maintaining old customers and "communities", 
while UBUNTU/CANONICAL leap forward to the future,

[B][SIZE="3"]
and the base of UBUNTU/CANONICAL will be expanding both dimensions.[/SIZE][/B]

---

### Post by cariboo on 2012-07-15
This thread seems have turned from a helpful one to an opinion piece, moved to the Cafe.

---

### Post by aimwin on 2012-07-15
I found one very important info from

[http://ubuntuforums.org/showpost.php?p=12104156&postcount=10](http://ubuntuforums.org/showpost.php?p=12104156&postcount=10)

glennric wrote.

There seems to be a lot of confusion here as to what gnome, gnome-shell, gnome classic, and unity are. Gnome is the desktop manager that ubuntu uses by default. Gnome-shell, gnome classic, and unity are all different gnome sessions. They just use different components of gnome and alternate window managers to give different user interfaces.

Gnome-shell is the true gnome 3. It provides the windows manager (mutter) and the whole desktop gui.

Gnome classic and unity both run in the gnome 2 fallback mode of gnome 3. Gnome classic uses the gnome-panel and is most like the old gnome 2. Unity is Ubuntu's home brewed variant. With both gnome classic and unity you have a choice of using compiz (and all the snazzy eye candy effects) or metacity for the window manager.

The most light weight version of all of those is to run the gnome classic session without effects (i.e. without compiz). If you run gnome-shell, gnome classic with effects, or unity-3d then you have the added load of a compositing window manager.

That being said, low end computers will benefit from a desktop that has an even smaller resource footprint. XFCE is better for this. I don't know much about LXDE, but it is supposed to be made for low end computers. So these are probably your best bet. That is unless you want to forgo the GUI completely and go command line only.
=========================================================
[B]
I myself now drop Unity in day to day use,
and use only Gnome Classic (without effects)
So my aging notebooks boots and reboots faster,
and run applicaton faster too.
I have only 1.2 GB RAM.[/B]

So Classic menu is not just only the choice of taste and old skill.
But in fact it is necessary for many users, and will be millions too,
(who are using old computers)

ONCE UBUNTU TAKE ON THE REAL POPULARITY.
[COLOR="Red"][SIZE="3"]
And GNOME CLASSIC option during installation will be a MUST.[/SIZE][/COLOR]

**_AND when that time arrive, I hope Conical will make an effort to cater the mass._**

So the normal and newbies will not be in pain,
as many of us are, including me.

And that made me wrote this simple tutorial topic after a hard time of experiments and searching.

I was thinking of me, being a newbies to ubuntu a few years back.
How easy to start learning UBUNTU.
And start promoting UBUNTU.

Now I have a hard time learning how to use UNITY, and GNOME 3.
And I am now consider intemediate UBUNTU desktop user.

But for many of those who are used to Windows,
and we are working to convert them to use UBUNTU or LINUX.

[COLOR="Red"]**Gnome Classic will be the easiest way to help and convince them to move along.**[/COLOR]

And I hope that UBUNTU will still be the leader not MINTs nor others.

---

### Post by philinux on 2012-07-15
Moved to recurring .

---

### Post by kansasnoob on 2012-07-15
> **aimwin said:**
> I found one very important info from

[http://ubuntuforums.org/showpost.php?p=12104156&postcount=10](http://ubuntuforums.org/showpost.php?p=12104156&postcount=10)

glennric wrote.

There seems to be a lot of confusion here as to what gnome, gnome-shell, gnome classic, and unity are. Gnome is the desktop manager that ubuntu uses by default. Gnome-shell, gnome classic, and unity are all different gnome sessions. They just use different components of gnome and alternate window managers to give different user interfaces.

Gnome-shell is the true gnome 3. It provides the windows manager (mutter) and the whole desktop gui.

Gnome classic and unity both run in the gnome 2 fallback mode of gnome 3. Gnome classic uses the gnome-panel and is most like the old gnome 2. Unity is Ubuntu's home brewed variant. With both gnome classic and unity you have a choice of using compiz (and all the snazzy eye candy effects) or metacity for the window manager.

The most light weight version of all of those is to run the gnome classic session without effects (i.e. without compiz). If you run gnome-shell, gnome classic with effects, or unity-3d then you have the added load of a compositing window manager.

That being said, low end computers will benefit from a desktop that has an even smaller resource footprint. XFCE is better for this. I don't know much about LXDE, but it is supposed to be made for low end computers. So these are probably your best bet. That is unless you want to forgo the GUI completely and go command line only.
=========================================================
[B]
I myself now drop Unity in day to day use,
and use only Gnome Classic (without effects)
So my aging notebooks boots and reboots faster,
and run applicaton faster too.
I have only 1.2 GB RAM.[/B]

So Classic menu is not just only the choice of taste and old skill.
But in fact it is necessary for many users, and will be millions too,
(who are using old computers)

ONCE UBUNTU TAKE ON THE REAL POPULARITY.
[COLOR="Red"][SIZE="3"]
And GNOME CLASSIC option during installation will be a MUST.[/SIZE][/COLOR]

**_AND when that time arrive, I hope Conical will make an effort to cater the mass._**

So the normal and newbies will not be in pain,
as many of us are, including me.

And that made me wrote this simple tutorial topic after a hard time of experiments and searching.

I was thinking of me, being a newbies to ubuntu a few years back.
How easy to start learning UBUNTU.
And start promoting UBUNTU.

Now I have a hard time learning how to use UNITY, and GNOME 3.
And I am now consider intemediate UBUNTU desktop user.

But for many of those who are used to Windows,
and we are working to convert them to use UBUNTU or LINUX.

[COLOR="Red"]**Gnome Classic will be the easiest way to help and convince them to move along.**[/COLOR]

And I hope that UBUNTU will still be the leader not MINTs nor others.

Part of what you're saying is not 100% correct. Is this helpful:

[http://ubuntuforums.org/showpost.php?p=12104700&postcount=108](http://ubuntuforums.org/showpost.php?p=12104700&postcount=108)

Neither Gnome nor Ubuntu are at all likely to change paths when it comes to development but there are other small projects that may keep a classic Gnome interface alive, like SolusOS and Mate :)

Once the code exists someone will hack it, create a PPA, etc.

---

### Post by craig10x on 2012-07-15
yes...you might want to check out Solus Os....the Os1 version is gnome 2 (already finalized and stable) and the newer Os2 version (which is in alpha and just about to go into it's first beta and already pretty darn stable) is their version of gnome 3...but the main developer of the project (Ikey) is bringing in total gnome 2 like functionality into it...

so it would be a way you could have gnome 3 (the latest gnome) with the latest applications but with the functionality and customizing ability you are use to from gnome 2 :)

---

