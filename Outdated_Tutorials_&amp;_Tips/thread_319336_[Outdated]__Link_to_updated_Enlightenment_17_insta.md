---
title: "[Outdated]  Link to updated Enlightenment 17 install thread in #1 Post"
date: 2006-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by tcrroadie on 2006-12-15
**[Updated Link for Enlightenment install Thread]("http://ubuntuforums.org/showthread.php?t=546746&highlight=e17&page=7")**.



[SIZE="2"][SIZE="2"]**[SIZE="3"]I thought I would create a new post on the installation of Enlightenment E17 (DR17) on Ubuntu.[/SIZE]**[/SIZE]
[B][/SIZE]
[SIZE="2"]
[COLOR="Red"]The installation of Enlightenment E17 sited in this thread uses the repositories created by the Elbuntu team.  Special thanks goes out to all of the Elbuntu developers for taking the time to package E17 for Ubuntu and making the repositories available to the community. 

More information on the Elbuntu project can be found here.[/COLOR][/SIZE]

[http://e17blog.tuxfamily.org/ebuntu_en.php/]("http://e17blog.tuxfamily.org/ebuntu_en.php/")

Now lets begin the installation process for E17.

Lets make sure our system is up to date. [/B]

**In a terminal run the following command.**

```
sudo aptitude update
```

```
sudo aptitude upgrade
```

[B]Next we will add the needed repository for E17 to our apt sources list.

In a terminal copy and past the following command.[/B]

```
sudo gedit /etc/apt/sources.list
```

[B]There are three repositories available, with available packages for Dapper Drake, Edgy Eft, and Feisty Fawn, "edevelop.org" and "e17.dunnewind.net".  Add one of the following repositories to the end of your apt sources list.
[/B]

**Dapper Drake repositories**

```
## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu dapper e17
deb-src http://edevelop.org/pkg-e/ubuntu dapper e17
```

```

## E17 Repository "e17.dunnewind.net"
deb http://e17.dunnewind.net/ubuntu dapper e17
deb-src http://e17.dunnewind.net/ubuntu dapper e17
```

**Edgy Eft repositories**

```
## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu edgy e17
deb-src http://edevelop.org/pkg-e/ubuntu edgy e17
```

```

## E17 Repository "e17.dunnewind.net"
deb http://e17.dunnewind.net/ubuntu edgy e17
deb-src http://e17.dunnewind.net/ubuntu edgy e17
```

**Feisty Fawn repositories**

```
## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu feisty e17
deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
```

```

## E17 Repository "e17.dunnewind.net"
deb http://e17.dunnewind.net/ubuntu feisty e17
deb-src http://e17.dunnewind.net/ubuntu feisty e17
```

**Save and close gedit.**

**Add the key.**

```
wget http://lut1n.ifrance.com/repo_key.asc
```

```
sudo apt-key add repo_key.asc
```

**Install Enlightenment E17**

```
sudo aptitude update
```

```
sudo aptitude install e17
```
[B]
Log out of Gnome.  Select session in your log in manager.  Enlightenment should be listed.  Select Enlightenment as your session and log in.  
[/B]
[COLOR="Red"]
**[SIZE="3"]Please Read Before Posting With Installation Problems[/SIZE]**[/COLOR]

[SIZE="2"]If you encounter dependency errors when installing E17, please check for the presence of an /etc/apt/preferences file.  If you are using an apt preferences file, please check for pinning of any enlightenment packages.  Please remove any reference to Enlightenment from your /etc/apt/preferences file if listed.  Then run [/SIZE]

```
sudo aptitude update
```

```
sudo aptitude install e17
```

[SIZE="2"]
If problems with installing E17 still occur, then please post the output you recieve from apt in your post.  

You can also contact Lutin or Sp4rKy on the Elbuntu IRC channel at irc.freenode.net with any problems you encounter with installation.[/SIZE]
[SIZE="2"]
Thank you.[/SIZE]

---

### Post by jlc on 2006-12-19
Anyone else getting the repository to hang updating your cache?

> 
Err [http://edevelop.org](http://edevelop.org) edgy Release.gpg
  Could not connect to edevelop.org:80 (67.138.240.42), connection timed out
Fetched 8B in 2m0s (0B/s)
Reading package lists... Done


---

### Post by bugzor on 2006-12-19
> **jlc said:**
> Anyone else getting the repository to hang updating your cache?

edevelop.org is down.

looks like iTray and engage applet has been removed from cvs, aka. no 'native' tray for e17 and i dont like trayer T_T

---

### Post by Lut!n on 2006-12-19
Works fine here, edevelop.org no longer seems to be down. just a bit slow ;)

---

### Post by Frak on 2006-12-21
Thanks, e17 is the most beautiful, useful, and enventive (pun intended) desktop I've seen.

---

### Post by Cody Body on 2006-12-23
E17 replace gnome or not ?

---

### Post by dakini on 2006-12-23
Very nice :D  Thanks for the tutorial!

---

### Post by Sandman32 on 2006-12-24
Nice howto, worked like a charm.  However, in the editing your sources section you are missing an s at the end of sources.

Other than that perfect!

---

### Post by komaroveli on 2006-12-29
isn't enlightenment in edgy repos? and in most uptodate version? or am i missing something

---

### Post by AgenT on 2006-12-29
> **komaroveli said:**
> isn't enlightenment in edgy repos? and in most uptodate version? or am i missing something
Yes. The version in the official Ubuntu repo is 16.7.2. This is the stable version, but E17 has been in the works for a very long time now (at least two years).

But even E16 is outdated as the newest version is 16.8.5.
The E17 repo information can be [found here]("http://www0.get-e.org/Main/News/_articles/365.html").

[http://enlightenment.sourceforge.net/](http://enlightenment.sourceforge.net/)
[http://fr.enlightenment.org/](http://fr.enlightenment.org/)
[http://www.get-e.org/](http://www.get-e.org/)
[http://www.elivecd.org/](http://www.elivecd.org/)

---

### Post by komaroveli on 2006-12-30
thnx for info AgenT.
it is indeed best desktop i have ever worked on. they should make Eubuntu (you know like thay have Kubuntu, Xubuntu...). i would do it if only i knew how (or at least if someone would tell me where to start educating myself)

---

### Post by autocrosser on 2006-12-30
Yes--I am liking Enlightenment (running in it right now:))--one small problem--E seems to not like my Firefox install--keeps telling me that Firefox is already running & close Firefox or restart to use it--this is only happing in my E user (I created a seperate user just for E) & will happen with any E user I setup--My "normal" user in Gnome has no problems--In E, Mozilla works fine, as will SeaMonkey or Opera:-k

Any ideas?

---

### Post by AgenT on 2006-12-30
> **komaroveli said:**
> thnx for info AgenT.
it is indeed best desktop i have ever worked on. they should make Eubuntu (you know like thay have Kubuntu, Xubuntu...). i would do it if only i knew how (or at least if someone would tell me where to start educating myself)
You probably searched for Eubuntu and not Ebuntu, the latter giving you the information you need.
[https://wiki.ubuntu.com/Ebuntu](https://wiki.ubuntu.com/Ebuntu)

As for myself, it is Beryl over Enlightenment for the following reasons:
1) scale plugin, this plugin with 3 scale modes and 3 style modes puts OSX's expose to shame and is amazing
2) very rapid development with a very responsive and open developers

UPDATE: According to [this bug report]("https://launchpad.net/products/ebuntu/+bug/70689"), the Ebuntu project has changed its name to [Elbuntu]("http://e17blog.tuxfamily.org/ebuntu_en.php/").

---

### Post by Frédéric Perrin on 2006-12-30
Work on an Ubuntu derivative with E17 as its default window manager has started : [https://launchpad.net/products/ebuntu](https://launchpad.net/products/ebuntu)

Due to name conflicts with Edubuntu, its name is going to be Elbuntu (see [discussion](https://bugs.launchpad.net/products/ebuntu/+bug/70689) on Launchpad).

AgenT > For Beryl + E17, is it what you are using, or what you wish to see ?
In the latter case, I would be very interested in how you did it.

---

### Post by AgenT on 2006-12-30
> **Frédéric Perrin said:**
> AgenT > For Beryl + E17, is it what you are using, or what you wish to see ?
In the latter case, I would be very interested in how you did it.Neither. I use Beryl without E17 and do not wish to use Beryl with E17. Although I would imagine that using Beryl with E17 would not be too difficult.

What I meant by the above post was that I use Beryl over E17 because E17 is missing point #1, or something that has similar benefits and #2. I actually have most of the graphical features turned off in Beryl because I use it for the usability and productivity aspects. However, E17 is a very good window manager or desktop, depending on how you use it.

---

### Post by FyreBrand on 2007-01-03
> **AgenT said:**
> Neither. I use Beryl without E17 and do not wish to use Beryl with E17. Although I would imagine that using Beryl with E17 would not be too difficult.

What I meant by the above post was that I use Beryl over E17 because E17 is missing point #1, or something that has similar benefits and #2. I actually have most of the graphical features turned off in Beryl because I use it for the usability and productivity aspects. However, E17 is a very good window manager or desktop, depending on how you use it.I tested out Beryl about a month ago just to see what it is like.  It seems like there are some things about it that could really improve productivity.  I'm not really interested in burning windows and that, but to help me out programming.  I often have a lot of windows open over 2 or 3 desktops.  Would it be useful for that?  I've looked at E17, but it doesn't seem like it will improve on what I can do in KDE (which I like a lot).  If you have links to other threads or articles on using Beryl or Compiz for productivity I would appreciate it.  Also I'm curious why the plug-in you use is so important to that.  The major thing I didn't like about Beryl (using Emerald configurator) is that most all the themes and effects are tied to Gnome libraries which I would rather not install.

Apologies at the off topic request.  I did look into E17 though because I find the concept very interesting.  In many ways I think the E17 developers are heading in a great direction.

---

### Post by AgenT on 2007-01-03
> **FyreBrand said:**
> I tested out Beryl about a month ago just to see what it is like.  It seems like there are some things about it that could really improve productivity.Are you sure that you tried out Beryl and not Compiz. They do differ. Beryl is a fork of Compiz. 

> **FyreBrand said:**
> I'm not really interested in burning windows and that, but to help me out programming.I also am not interested in fancy graphical shows which is why I turn most plugins off.

> **FyreBrand said:**
> I often have a lot of windows open over 2 or 3 desktops.  Would it be useful for that?... Also I'm curious why the plug-in you use is so important to that...Yes, very much useful for that if you use it correctly. This is one of the major productivity boosts that I gained. I no longer bother with using minimized windows or a panel. Instead, I use  many plugins, all of which are important. But the major one concerning changing windows is Scale. Scale is like expose in OSX except much better. It also has three modes, with three styles each. I use scale two of the three: scale all windows and scale all windows in viewport. I also have scale scale minimized windows "just in case" which is off by default. I have scale bound to top-right screen touch and bottom-left. Bottom-right is to show desktop which works *much* better than normal show desktop in metacity. Also, there are a few tricks to scale, such as having drag-and-drop using it (very useful) and closing windows by clicking mouse button 2. You can close not needed windows very fast this way. Scale is really nice, especially for smaller screens (I use a 12" screen).

Another very important aspect of Beryl is the key binding ability. Play around with it a little and you will soon find huge improvements in productivity. For example, my Thinkpad has a trackpoint and with custom key bindings, I not only never have to take my hands off the keyboard, but everything from switching windows to show desktop to switching viewports can be done very quickly. I have all panels hidden and rarely use them. I am also looking into getting rid of all panels and menus now that I have found out how much better it is to not have to use them so much.

This is just a short summery and in truth productivity is different for everyone and everyone will have their "weaknesses" that they can improve upon. Even some of the effects that people think are only for show (like the ones in animation plugin) are pretty useful if used properly. Also, describing a WM is pretty difficult. It's about as useful as a picture (not very).

> **FyreBrand said:**
> I've looked at E17, but it doesn't seem like it will improve on what I can do in KDE (which I like a lot).Are you sure you looked into it and gave it enough time? Try it out for a longer time and look into everything that it has to offer. You never know, you may just find that one or two features that really work for you. Not everything is enabled by default or made for your habits.

> **FyreBrand said:**
> If you have links to other threads or articles on using Beryl or Compiz for productivity I would appreciate it.I do not. But I do have a video that you may be interested in. I tried looking for it on the Internet but I cannot find it. I can, however, upload it somewhere or send it to you. Private message me your information and I will upload/send it. Do note that it is 20mb.

> **FyreBrand said:**
> Also I'm curious why the plug-in you use is so important to that.  The major thing I didn't like about Beryl (using Emerald configurator) is that most all the themes and effects are tied to Gnome libraries which I would rather not install.Again, are you sure you tried Beryl and emerald? The really big difference between Beryl and Compiz is that Compiz requires DE libraries and Beryl is 100% standalone. Emerald is also DE agnostic, but there are also theme engines for GNOME and KDE themes (100% compatible) that use GNOME and KDE libs. You can install the same Beryl (with Emerald) on GNOME, KDE, any other DE or none at all.

> **FyreBrand said:**
> I did look into E17 though because I find the concept very interesting.  In many ways I think the E17 developers are heading in a great direction.The one thing that is *very* nice about E is how bloat-free it is and how low of a system it will run on. KDE and GNOME are all as bloated as you pretty much can get in Linux and E is just amazing. Especially considering that E is not only a WM but also a DE.

---

### Post by FyreBrand on 2007-01-03
I did use Beryl with Emerald.  I installed it using these instructions: [Installing Beryl on Edgy with XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL").  I wasn't really clear in that Beryl didn't ask for Gnome dependencies, but many of the themes wanted Gnome components.

I did like it though, but I should have given it more time.  The same thing goes for E17.  I just tried it out for a very short bit and then switched back and actually I think it was E16 when I think back and not E17 so I'm going to try out the newer version on the easy install thread.

I'm going to try out E17 first and then Beryl.  I'm not exactly sure if I can install Beryl on KDE  and also E17 without breaking everything.  Not really a big deal since I keep a separate document partition, but I'll go slow to start.

Thanks for the feedback.

---

### Post by fuscia on 2007-01-05
this was *so* easy, it didn't really feel like e17. thanks.

---

### Post by _simon_ on 2007-01-05
If I install E17, is removal just a case of going into synaptic and removing?

---

### Post by CowzRule on 2007-01-05
> **_simon_ said:**
> If I install E17, is removal just a case of going into synaptic and removing?
yep

---

### Post by The Noble on 2007-01-05
I don't think you can use synaptic to remove e17 and all of its dependencies, as synamptic uses apt-get. To remove e17, type "sudo aptitude remove e17" in the console and everything will be removed. Also, thanks for making this guide, as enlightenment is actually usable now! Looks amazing as well.

---

### Post by limaunion on 2007-01-05
While trying to browse [http://edevelop.org/pkg-e/ubuntu/](http://edevelop.org/pkg-e/ubuntu/) I'm getting: 

"Forbidden
You don't have permission to access /pkg-e/ubuntu/ on this server.

Apache/1.3.34 Server at edevelop.org Port 80"

Is there any other mirror available ?
Thanks.

---

### Post by AgenT on 2007-01-05
The mirror works, you just cannot browse it with your web browser.

And in terms of removing via aptitude: it will do you no good if you only remove via aptitude, you must also install it via aptitude:
```
sudo aptitude install e17
sudo aptitiude remove e17
```Or a more clean and program error proof way would be to use synaptic and after selecting to install e17, saving the marked packages or just use apt-get and save the list of installed packages. Then iterating over the list of installed packages (hint: use awk to only select package names) and removing every single one. This is for advanced users only.

---

### Post by tcrroadie on 2007-01-06
_simon_

I believe a little clarification on the differences between apt-get and aptitude needs to be made.  I am not an expert but from what I understand the main difference between apt-get and aptitude is that aptitude is a little more agressive on package selection.  Meaning that when installing packages with aptitude such as E17, aptitude will install all recommended packages as well as all required packages were as apt-get will only install required packages by default.  This also applies to removing packages.  

So when removing *any* package, you will want to carefully read what packages aptitude is going to remove, the same also applies to apt-get.

I tend use aptitude over apt-get when it comes to installing packages (applications) because I believe aptitude does a better job of handleing needed packages at install time.  As far as removing packages is concerned you can use either.  You can also simulate an install or removal of a package by using the -s option to give you an idea of how things will work out. 

I hope this info helps and wasn't to long.  

Kris.

---

### Post by AgenT on 2007-01-06
A little bit misinformation in the above post. More information:
[ aptitude versus apt-get]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by finferflu on 2007-01-08
Thanks a lot! E17 is *amazing*. Very eyecandy, very quick and very customizable. I just wonder why it's not as popular as KDE and Gnome. I think E17 will definately be my #1 Window Manager.
Thank you!

---

### Post by Reb on 2007-01-09
The repo isn't resolving for me... is it down?
I guess that's not really a question more a statement...

---

### Post by Lut!n on 2007-01-09
works fine here (tm) :)

---

### Post by AgenT on 2007-01-09
> **finferflu said:**
> Thanks a lot! E17 is *amazing*. Very eyecandy, very quick and very customizable. I just wonder why it's not as popular as KDE and Gnome. I think E17 will definately be my #1 Window Manager.
Thank you!
Probably because E17 does not install 100 other applications to make the desktop environment "complete". Also, probably because it is a little more advanced than GNOME/KDE and bundle that with the fact that a large portion of Ubuntu users is not Linux savvy....

---

### Post by finferflu on 2007-01-09
> **AgenT said:**
> Probably because E17 does not install 100 other applications to make the desktop environment "complete". Also, probably because it is a little more advanced than GNOME/KDE and bundle that with the fact that a large portion of Ubuntu users is not Linux savvy....

Actually I think you are right, especially because E17 is a window manager and not a desktop environment like GNOME and KDE. It's still an optimal solution if used on top of either of them. I just love it. I would never expect I could have such beautiful eyecandy and FX combined with velocity that can be compared to IceWM or fluxbox.

---

### Post by Reb on 2007-01-09
IMO, E17 is kinda in between WM and DE... the mirror's working fine now, by the way.

---

### Post by Sconeface on 2007-01-09
So, I'm sure this is a total n00b question, but since I'm n00 (heh heh) to this, I'll ask.

I went through everything and got to the last step, but when I go to install, I get this

Segmentation Faulttate Information.........1%

](*,) ](*,) ](*,) ](*,) ](*,) 

Any help would be amazingly appretiated!

---

### Post by floke on 2007-01-09
The one gripe I have with E17 is that you can't autohide the panel - am i wrong? Does anyone know how to do this?

---

### Post by tcrroadie on 2007-01-09
> **Steve.K said:**
> The one gripe I have with E17 is that you can't autohide the panel - am i wrong? Does anyone know how to do this?

Hi Steve.  About the closest thing that E17 has to autohiding the panel or shelf is to configure the shelf to allow all windows to overlap the shelf.  This can be done by right clicking the shelf and selecting Shelf Configuration from the menu.  Click the Advanced tab.  In the upper left hand area of the window were Stacking is listed, make shure above everything is unchecked and Allow Windows To Overlap The Shelf is checked.  Click apply and you should be good to go.  

This will allow windows to overlap the shelf when moving windows and when maximizing windows. 

Here is a screen shot from my pc that may be helpfull.

---

### Post by tcrroadie on 2007-01-09
> **Sconeface said:**
> So, I'm sure this is a total n00b question, but since I'm n00 (heh heh) to this, I'll ask.

I went through everything and got to the last step, but when I go to install, I get this

Segmentation Faulttate Information.........1%

](*,) ](*,) ](*,) ](*,) ](*,) 

Any help would be amazingly appretiated!

The segmentation fault you are receiving may be due to a bug in the version of aptitude you are using.  I would recommend trying apt-get in place of aptitude and see if apt-get will work for you.  

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get install e17
```

Good luck.  Please report back with your results.

---

### Post by Sconeface on 2007-01-10
No go, man. Heres what came up:

rob@Sconebox:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
       Depends: emodules0-all (>= 0.16.999) but it is not going to be installed
       Depends: eutils but it is not going to be installed
E: Broken packages


I really appretiate the effort though! Thanks!

---

### Post by finferflu on 2007-01-10
> **Sconeface said:**
> No go, man. Heres what came up:

rob@Sconebox:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
       Depends: emodules0-all (>= 0.16.999) but it is not going to be installed
       Depends: eutils but it is not going to be installed
E: Broken packages


I really appretiate the effort though! Thanks!

Have you, by any chance, tried to use aptitude instead of apt-get? Don't know if that makes any difference, but I know that aptitude manages dependencies better...

---

### Post by floke on 2007-01-10
If you allow a window to overlap the shelf (I think I remember trying this a while back actually) - how do you get to the shelf when it's covered? Do you have to resize windows that are above it? It seems like a bit of a hassle. Toi be honest, it's the only thing I don't like about E17, especially since it's pretty much a default feature with the others (KDE, Gnome, XFCE etc.) - you might've thought they would have put it in!

Thanks for the tip though - will try next time I boot into it.

---

### Post by john_spiral on 2007-01-12
Yeeeehaaaaaaaaaaa!!!!

Got it working no probs, thanks for the howto!

Nice quick and beautiful.

---

### Post by Lut!n on 2007-01-13
Hay guys, I've some interesting news for those of you who use feisty:
I uploaded yesterday the e17 builds for feisty, both i386 and and64
you can check them out at
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17

Have fun :)

---

### Post by john_spiral on 2007-01-13
Hi,

I've just installed Enlightenment using the method from this howto. 

The 'About Enlightenment' screen shows that I'm using version **0.16.999.037** is this the same as **E17**?

John

---

### Post by john_spiral on 2007-01-13
> **john_spiral said:**
> Hi,

I've just installed Enlightenment using the method from this howto. 

The 'About Enlightenment' screen shows that I'm using version **0.16.999.037** is this the same as **E17**?

John

I found an answer to my question on the [http://www.enlightenment.org/Main/FAQs/#4](http://www.enlightenment.org/Main/FAQs/#4) site:

"**What is the meaning of the release versions: E 17 and DR17 or 0.17?**

The full name of the current stable release is "Enlightenment Development Release 0.16.7.2", but people like to shorten it. "E" stands for Enlightenment, while "DR" stands for Development Release. The current stable window manager can be called any of the following, E 0.16.7.2, E 16.7, E16, DR16.7, or DR16 it's all the same thing.

Which you use is a matter of personal preference.

Likewise the full name of the unstable, unreleased version is "Enlightenment Development Release 0.17.0", and people like to shorten that as well, and in the same manner. But, just to confuse the issue, until E17 gets released, it has a version number of 0.16.999.018 or higher."

---

### Post by icefaerie on 2007-01-14
Thanks so much for this HOWTO!  I used to run enlightenment on another distro, and I'm so happy to have it again!  Everything worked great.  Now I just have to get used to the differences between e16 and e17...

---

### Post by Neo40 on 2007-01-14
Hi,

I have installed Ubuntu-server 6.10  into my another HDD and I want only E17. So, if I follow this Howto, I think it won't be a problem to install E17. However, if I want Entrance as login manager, how can I install it correctly?

Thanks

---

### Post by kuripot on 2007-01-14
Thanks for the howto. I'm currently using Beryl and just installed e17, and so far I'm liking the responsiveness and the interface, in addition to the eye candy. Beryl was taking up so many resources just opening a terminal was sluggish. I think it was using around 90mb compared to 17.6mb for e17!! (I just used right clicked to bring up the "run command" selection to run the system monitor and it brings up a menu of possible entries, way cool! what program is this? seems like fish but not in a terminal and prettier). 

I'm with the above poster about autohiding the shelf, hopefully they add this option in a future release.

---

### Post by Sp4rKy on 2007-01-15
Hi, 
@Neo40, please, if you use our repo for install E17 ([http://edevelop.org/pkg-e](http://edevelop.org/pkg-e) or [http://e17.dunnewind.net)](http://e17.dunnewind.net)), please wait about a week.
I've just finish to package entrance 3days ago. Actually it is in review state,ie : we have to be sure it works correctly and it hasn't big bugs.

Anyway, it already works on 2 computers perfectly, so i think it will be validated & included during the next week.

You can get more information at [http://e17blog.tuxfamily.org](http://e17blog.tuxfamily.org) , and in our mailing list :)

---

### Post by tcrroadie on 2007-01-15
> **Sp4rKy said:**
> Hi, 
@Neo40, please, if you use our repo for install E17 ([http://edevelop.org/pkg-e](http://edevelop.org/pkg-e) or [http://e17.dunnewind.net)](http://e17.dunnewind.net)), please wait about a week.
I've just finish to package entrance 3days ago. Actually it is in review state,ie : we have to be sure it works correctly and it hasn't big bugs.

Anyway, it already works on 2 computers perfectly, so i think it will be validated & included during the next week.

You can get more information at [http://e17blog.tuxfamily.org](http://e17blog.tuxfamily.org) , and in our mailing list :)

Thanks for the update on Entrance Sp4rky.  I was thinking about compiling and installing Entrance from source to see if I could get it working myself but eventually figured if Entrance is not included in the repo's yet, it must not be quite ready.  

I personally think that the Enlightenment team is doing a great job on E17 and thoroughly enjoy using it.  Also big thanks for all the hard work packaging E17 for Ubuntu.  The team is doing a great job. :)

---

### Post by Sp4rKy on 2007-01-15
Thanks tcrroadie :)

Now just wait for Elbuntu release :D

---

### Post by Frak on 2007-01-15
> **Sp4rKy said:**
> Thanks tcrroadie :)

Now just wait for Elbuntu release :D
I know alot of people who are waiting for it (i.e. **ME**)

---

### Post by nekr0z on 2007-01-15
Thanks for the guide, it's really cool and working. The only thing I cannot understand (in E, not the guide) is how do you guys manage wireless network connections in E? I got used to gnome's network-manager applet, so I really miss it in E...

---

### Post by Sp4rKy on 2007-01-15
indeed, there is no network applications intergated in E
Maybe you can use wifi-radar, which is a bit more independant of Gnome :)
And, for me, the best conf util is xterm ^^

---

### Post by nekr0z on 2007-01-15
WiFi radar is actually not more dependable on GNOME than Network-Manager. As the matter of fact, there's native KDE applet for controlling network-manager, too... And I beleive nm-applet would work good in E as well, if only E had some kind of System Tray (or Notification Area or whatever you call it). There are several reasons for me to miss such thing in E, but the wireless issue is the one that hurts most...

Xterm, by the way, really rocks as a conf util, but I'm not that mastered in Linux yet.

---

### Post by finferflu on 2007-01-16
Do you know how to install the Enlightenment applications by any chance?
On the website there's no link, and in the repositories they are not present...

Any idea?

Thanks

---

### Post by tcrroadie on 2007-01-16
> **finferflu said:**
> Do you know how to install the Enlightenment applications by any chance?
On the website there's no link, and in the repositories they are not present...

Any idea?

Thanks

I believe the main reasoning why many of E17 applications are currently missing from the repositories is because they are not yet finished and are to buggy. Please keep in mind that many of E17's native applications are in *heavy development *and may *not work at all *due to changes in E17's own libraries and complete rewrites. 

From what Sp4rky noted in an earlier post, E17's login manager Entrance may soon be included in an upcomming repository update. Be patient, in time more applications will come.

If you feel brave enough, you can try installing additional applications from source. Please keep in mind that they may not work. Additional information can be found at the links listed below. 

[http://www4.get-e.org/EFL_User_Guide/English/_pages/2.1.html]("http://www4.get-e.org/EFL_User_Guide/English/_pages/2.1.html")  

[http://enlightenment.freedesktop.org]("http://enlightenment.freedesktop.org")

---

### Post by Sp4rKy on 2007-01-16
You're wrong, many of the EFL apps are integrated in our repo ^^
I think an apt-cache search enlightenment should print you the app.
The eclair app isn't yet in the repo, but it will be integrated in a few days ago (it is in review state, like Entrance).

Like tcrroadie said, much of the EFL app aren't really usuable. So we only integrate those we can use.
Anyway, if you show some EFL based software we hasn't intergated yet, let us know on this topic, or in IRC :)

---

### Post by finferflu on 2007-01-16
> **Sp4rKy said:**
> You're wrong, many of the EFL apps are integrated in our repo ^^
I think an apt-cache search enlightenment should print you the app.
The eclair app isn't yet in the repo, but it will be integrated in a few days ago (it is in review state, like Entrance).

Like tcrroadie said, much of the EFL app aren't really usuable. So we only integrate those we can use.
Anyway, if you show some EFL based software we hasn't intergated yet, let us know on this topic, or in IRC :)

Ah! Thanks for that! You know I had tried to search for enlightenment using aptitude, but nothing more than Enlightenment and some themes had turned up. With apt-cache search I got a lot more stuff. Good to know..

By the way, I've seen on Elive that there is an awesome feature, the blur transparency, is there any way I can make it work on my install? I've tried to google it a lot, but I couldn't find anything else...

Thanks a lot!

---

### Post by Sp4rKy on 2007-01-16
what do you call blur transparency ? any screenshot ?

---

### Post by kcallis on 2007-01-17
I guess the biggest thing for me, is not how to install E, but more importantly some pointers on how to make E more functional. For instance, the download and installation of E was not a problem. But once I get inside the E wm, my issue becomes how do I make it function with some of the previous functionality that I had in Metacity?

That is just my $0.02 worth of comment!

K.

---

### Post by finferflu on 2007-01-17
> **Sp4rKy said:**
> what do you call blur transparency ? any screenshot ?

Here you go: [http://elivecd.org/gb/Main/Screenshots/E17/_previews/blur-01.jpg.html](http://elivecd.org/gb/Main/Screenshots/E17/_previews/blur-01.jpg.html)

---

### Post by tcrroadie on 2007-01-17
> **kcallis said:**
> I guess the biggest thing for me, is not how to install E, but more importantly some pointers on how to make E more functional. For instance, the download and installation of E was not a problem. But once I get inside the E wm, my issue becomes how do I make it function with some of the previous functionality that I had in Metacity?

That is just my $0.02 worth of comment!

K.

Hi Kcallis.  Could you please elaborate on the functionality you speak of between Metacity and E17?  My personal needs are very simple.  In E17 you can shade windows, alt+tab to select windows and easily move between other desktops.  Even E's own menu helps you manage open windows.  

I'm just a little curious as to what people really have to say about the usability of E17.  Lately I have been coming across some post with statements that E17 is awkward to use.  I suppose it is all just personal preference.

---

### Post by Sp4rKy on 2007-01-17
> **kcallis said:**
> I guess the biggest thing for me, is not how to install E, but more importantly some pointers on how to make E more functional. For instance, the download and installation of E was not a problem. But once I get inside the E wm, my issue becomes how do I make it function with some of the previous functionality that I had in Metacity?

That is just my $0.02 worth of comment!

K.

Remember E isn't Gnome nor KDE . You don't have and you will never have all the gadget's included in those DM.
For configuration/management of E, i think the best way is a left click on the desktop=> configuration 

Good luck ^^:twisted:

---

### Post by Hendrixski on 2007-01-17
> **kcallis said:**
> I guess the biggest thing for me, is not how to install E, but more importantly some pointers on how to make E more functional. For instance, the download and installation of E was not a problem. But once I get inside the E wm, my issue becomes how do I make it function with some of the previous functionality that I had in Metacity?

That is just my $0.02 worth of comment!

K.

Everything is configurable (even though not everything works perfectly yet).  If you play around with the hundreds of settings, and dozen or so settings tools, you can get it to do pretty much anything you want.

Mind you, this is still a developers release, so while I have it installed on my laptop, I wouldn't use it at work.

---

### Post by Sp4rKy on 2007-01-17
> **finferflu said:**
> Here you go: [http://elivecd.org/gb/Main/Screenshots/E17/_previews/blur-01.jpg.html](http://elivecd.org/gb/Main/Screenshots/E17/_previews/blur-01.jpg.html)

hmm, after some request on #e channel, this kind of transparency seems depend of the term, and not E :)

---

### Post by finferflu on 2007-01-17
> **Sp4rKy said:**
> hmm, after some request on #e channel, this kind of transparency seems depend of the term, and not E :)

Ah! Is that Eterm, xterm? I find it very hard to get terminal transparency on E17, actually I have given it up for an animated wallpaper... 

Thanks!

---

### Post by Sp4rKy on 2007-01-17
animated wallpaper is pretty easy :)
maybe xterm, with pseudo-transparency. Not xterm ...

So good nught guys :)

---

### Post by Chouca on 2007-01-18
Excellent Guide!!!

I have now made the journey Ubuntu -->  Xubuntu --> ICEwm --> E17  and it is getting better and better  :) 

The Installation of E17,  by the How To, was very smooth and the first impression of E17 is Wow - why fuzz around with other lightweight alternatives when E17 is both fast and beautiful!!! 



Martin

---

### Post by finferflu on 2007-01-18
> **Chouca said:**
> The Installation of E17,  by the How To, was very smooth and the first impression of E17 is Wow - why fuzz around with other lightweight alternatives when E17 is both fast and beautiful!!! 


That's also my point! :D

---

### Post by kopinux on 2007-01-18
i've been looking for a dr17 distro, and i never thought i could install it very easily with ubuntu, the guide works perfect with ubuntu dapper, ubuntu edgy and kubuntu edgy.

but i think i like the dr17 kubuntu base since it does not have any bulky windows. it matched the dr17 themes. though i would really like the ps3-linux-ydl look, its the main reason why im looking for dr17. this is great and easy im gonna use this for a long time. both kde and gnome feels like windows, dr17 is kinda unique and kick the windows habit and more easier to use.

---

### Post by nsleiman on 2007-01-19
the HowTo worked like a charm. E17 is really great and i like it. i am only missing the volume manager, think i will work more on it.

Great work :)

---

### Post by finferflu on 2007-01-19
> **nsleiman said:**
> the HowTo worked like a charm. E17 is really great and i like it. i am only missing the volume manager, think i will work more on it.

Great work :)

There is a module for the volume manager, it's called mixer, you have to enable it in the modules configuration, and then you'll be able to add it to your shelf. You can also associate an application to it, so that when you middle-click on it, the app will start. For instance, I've used kmix. It's perfect.

Enjoy!

---

### Post by nsleiman on 2007-01-19
thank you very much! module is loaded and gadget running,still can not configure it to launch  Kmix. any idea what the 'configure' button not working ?

---

### Post by Lut!n on 2007-01-19
the 'configure' button in the modules panel is disabled because this module handles a per-shelf config (that means, you can a mixer launching kmix, another launching xmms or whatever if you want). you have to right-click on the module in the shelf and click 'configure', then you'll be able to configure it.

Have fun :)

---

### Post by AgenT on 2007-01-20
It should be noted that Eterm does pseudo transparency and is able to have a custom background, at least it did around 4 years ago. However, Eterm does not seem to be maintained anymore and even E17 no longer uses it. Try a different terminal emulator. There are a lot, but not all support transparency due to it not being very useful and just adding "bloat". Look into rxvt-unicode, mrxvt and aterm. There are more, so search freshmeat and sourceforge.

---

### Post by abrand15 on 2007-01-20
I'm using Edgy and got the following error when trying this HOWTO:
> dpkg: dependency problems prevent configuration of e17:
 e17 depends on emodules0-all (>= 0.16.999); however:
  Package emodules0-all is not configured yet.
dpkg: error processing e17 (--configure):
 dependency problems - leaving unconfigured
...
Errors were encountered while processing:
 emodule0-language
 emodules0-all
 e17
Can someone help me?

Cheers,
Allan

---

### Post by Lut!n on 2007-01-21
what is the message when you try to install emodules0-all ?

---

### Post by abrand15 on 2007-01-22
Solved it with the following:
```
 sudo dpkg -i --force-all "/var/cache/apt/archives/libexml1_0.1.1+cvs20070110-1_i386.deb"
```

E17 now installs just fine.

Cheers,
Allan

---

### Post by john_spiral on 2007-01-23
Have any e17 crack heads out there built the latest version of Enlightenment?

[http://enlightenment.org/Enlightenment/Get_Enlightenment/Build_Notes/](http://enlightenment.org/Enlightenment/Get_Enlightenment/Build_Notes/)

On another note does anyone know any good e17 theme sites?

---

### Post by Lut!n on 2007-01-23
> **john_spiral said:**
> Have any e17 crack heads out there built the latest version of Enlightenment?

[http://enlightenment.org/Enlightenment/Get_Enlightenment/Build_Notes/](http://enlightenment.org/Enlightenment/Get_Enlightenment/Build_Notes/)

What do you mean ? The version in the repos is recent, there haven't been any major changes in 2 weeks :)

> **john_spiral said:**
> On another note does anyone know any good e17 theme sites?
get-e.org :)

---

### Post by finferflu on 2007-01-23
Unfortunately there are not many themes... but hey! this is pre-alpha release (have I read correctly?). To be in such an early state and being so wonderful I seriously wonder what the final product will be... I think I'll start buying t-shirts and gadgets at that time :P

---

### Post by Kratos on 2007-01-23
I'm having time-out issues with the repository. Anyone else?

```
Err http://edevelop.org edgy Release.gpg
  Could not connect to edevelop.org:80 (67.138.240.42), connection timed out
```

---

### Post by john_spiral on 2007-01-24
> **Lut!n said:**
> What do you mean ? The version in the repos is recent, there haven't been any major changes in 2 weeks :)


get-e.org :)

Alright I'll hang off until there is something more delicious to install. 

Every now and again E17 crashes when I choose a particular GUI option. Is there a site where I can submit such bugs? 

[http://www.bugzilla.org/](http://www.bugzilla.org/) doesn't seem to have anything?

Any other sites besides get-e.org for themes?

Edit:

I've just discovered:

[http://www.enlightenment.org/Main/Debugging/](http://www.enlightenment.org/Main/Debugging/)

But there doesn't seem to be any noob friendly bug submitting tools/sites.

---

### Post by J.Pulumbarit on 2007-01-24
> **Kratos said:**
> I'm having time-out issues with the repository. Anyone else?

```
Err http://edevelop.org edgy Release.gpg
  Could not connect to edevelop.org:80 (67.138.240.42), connection timed out
```


same problem here... any ideas on when it will be back up/ any other options?

---

### Post by st1ck3m_tux on 2007-01-25
I have been trying for a couple of days with no luck. It just times out.  :confused:

---

### Post by J.Pulumbarit on 2007-01-25
i guess ill just wait it out then...

---

### Post by st1ck3m_tux on 2007-01-25
Hi all!  Just found a different Repo to install from.  This one is really fast.  I have E 17 up and running with no problems.  Here is the link for instructions...

[http://e17blog.tuxfamily.org/e17blog-edgy_en.php/post/2006/12/05/Enlightenment-Repositories-for-Ubuntu-Edgy-Eft](http://e17blog.tuxfamily.org/e17blog-edgy_en.php/post/2006/12/05/Enlightenment-Repositories-for-Ubuntu-Edgy-Eft)

I used the second repo which is...

## E17 Repository "e17.dunnewind.net"
deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17
deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17


Hope that this helps.  :D

---

### Post by tcrroadie on 2007-01-25
> **st1ck3m_tux said:**
> 

I used the second repo which is...

## E17 Repository "e17.dunnewind.net"
deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17
deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17


Hope that this helps.  :D

Thanks for posting the information on the second available Elbuntu repository.  I have been meaning to add the dunnewind.net repositories to the install guide, but ran into issues with the dunnwind.net server running slow during testing.  I may be wrong but I believe that the Elbuntu developers may be moving to using only the dunnewind.net server in the future.  I'll check the dunnewind repository when I get a chance and edit the install guide as necessary. 

I also believe that the dunnwind.net repositories are a mirror of the repositories located at edevelop.org, so they both should be in sync. 

Also as a reminder, if there are any issues encountered when installing E17 in regardes to dependency errors or servers down, please try to contact Lutin or Sp4rKy on IRC.  #elbuntu on irc.freenode.net

Thanks  :)

---

### Post by J.Pulumbarit on 2007-01-25
sweet im at school right now but as soon as i get home im going to try them out. thanks for the info.

---

### Post by J.Pulumbarit on 2007-01-25
> 

Install Enlightenment :

    sudo apt-get install enlightenment e17 e17-devel-extras emodule-alarm emodule-cpu emodule-deskshow emodule-flame emodule-language emodule-mail emodule-mem emodule-mixer emodule-moon emodule-net emodule-photo emodule-rain emodule-screenshot emodule-slideshow emodule-snow emodule-taskbar emodule-tclock emodule-uptime emodule-weather emodule-winselector emodule-wlan

after doing that i got this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate

=/ i tried enlightenment-data and got the same error except without telling me which packages replace it.

---

### Post by finferflu on 2007-01-25
> **J.Pulumbarit said:**
> after doing that i got this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate

=/ i tried enlightenment-data and got the same error except without telling me which packages replace it.

Where did you get that quote from? To install e17 you should only do

```
sudo aptitude install e17
```

---

### Post by J.Pulumbarit on 2007-01-25
i got the quote from here: [http://e17blog.tuxfamily.org/e17blog...buntu-Edgy-Eft](http://e17blog.tuxfamily.org/e17blog...buntu-Edgy-Eft)
i used that howto cause the repositories for this howto arent working right now

---

### Post by finferflu on 2007-01-25
> **J.Pulumbarit said:**
> i got the quote from here: [http://e17blog.tuxfamily.org/e17blog...buntu-Edgy-Eft](http://e17blog.tuxfamily.org/e17blog...buntu-Edgy-Eft)
i used that howto cause the repositories for this howto arent working right now

> Not Found

The requested URL /e17blog...buntu-Edgy-Eft was not found on this server.
I think that's due to copy-paste, anyways...

However, if you try to install the package *enlightenment* alongside the package *e17*, is like you're installing Enlightenment DR16 and DR17 at the same time, no wonder you get that error. Try not to use the package *enlightenment* and see how it goes.

---

### Post by J.Pulumbarit on 2007-01-25
> **finferflu said:**
> Where did you get that quote from? To install e17 you should only do

```
sudo aptitude install e17
```

i didnt notice it was aptitude instead of apt-get, that helped alot.
after it tells me how much space is going to be used and i agree it says this:
Segmentation fault (core dumped)on... 1%
what does that mean?

---

### Post by Beej on 2007-01-26
Does anybody know of any working repos for edgy? Ive tried the edevelop and the dunnewind repos and can't get either to work, timeout errors for both.

---

### Post by Lut!n on 2007-01-26
You should try again, dunnewind.net seems to work fine here (c)

---

### Post by Beej on 2007-01-26
Cool, I'll give it another go when i get home

---

### Post by tcrroadie on 2007-01-26
> **J.Pulumbarit said:**
> i didnt notice it was aptitude instead of apt-get, that helped alot.
after it tells me how much space is going to be used and i agree it says this:
Segmentation fault (core dumped)on... 1%
what does that mean?

Are you using Dapper Drake?  Try using apt-get in place of aptitude and post your results.

```
sudo apt-get install e17
```

The error you are receiving may be due to a bug in aptitude.

---

### Post by J.Pulumbarit on 2007-01-26
> **tcrroadie said:**
> Are you using Dapper Drake?  Try using apt-get in place of aptitude and post your results.

```
sudo apt-get install e17
```

The error you are receiving may be due to a bug in aptitude.

im on edgy, i tried to use apt-get and i got some other error about not being installable, im at school right now but i can give more information when i get home.

---

### Post by L_V on 2007-01-30
Small clarification request:

"*Enlightenment's current design aim is to become a desktop shell. That means it will manage your application windows, being able to launch applications, and also manage your files.* "

Today, can E17 be installed on a base installation without any gnome or KDE ?

---

### Post by finferflu on 2007-01-30
> **L_V said:**
> Small clarification request:

"*Enlightenment's current design aim is to become a desktop shell. That means it will manage your application windows, being able to launch applications, and also manage your files.* "

Today, can E17 be installed on a base installation without any gnome or KDE ?

> It is currently in a pre-alpha stage and is under heavy development.

In any ways, I don't think that's particularly recommended...

---

### Post by L_V on 2007-01-30
Ok E17 is an alpha, but this does not clarify the question.

What is a window manager without a desktop manager ?
Is it possible to use, today, E17 without any desktop manager ?
If not, what minimum part of desktop manager is necessary for E17 ?

Never got clear answer on that one.

---

### Post by finferflu on 2007-01-30
> **L_V said:**
> Ok E17 is an alpha, but this does not clarify the question.

What is a window manager without a desktop manager ?
Is it possible to use, today, E17 without any desktop manager ?
If not, what minimum part of desktop manager is necessary for E17 ?

Never got clear answer on that one.

I know, I hadn't answered because I didn't know the answer.. I've done some research though, and found out that you can use a Windows Manager without the need of a Desktop Environment. I guess the main advantage of a DE is that all applications share the same libraries, so everything should be quicker to start up, and use less disk space. Not sure about any other advantage. As for a WM, you can use it to manage everything you decide to install, since there aren't many applications that come with a WM. With E17 you've got a basic file manager and the xterm. I guess that's it. 

You could also give a look to [http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)

Enjoy!

---

### Post by L_V on 2007-01-30
Ok but the progress on enlightment is so slow (already more than 6 years  ?) and basic information so difficult to find (how to configure a minimum etc...) that I think I will wait.
Not yet clear to me the added value of this new one (compared to XFCe etc...)

My main concern for the moment is the quality of fonts in linux (not clean at all compared to windows, even with gnome or KDE), more than looking for funny icons !

---

### Post by tcrroadie on 2007-01-30
> **L_V said:**
> Ok E17 is an alpha, but this does not clarify the question.

What is a window manager without a desktop manager ?
Is it possible to use, today, E17 without any desktop manager ?
If not, what minimum part of desktop manager is necessary for E17 ?

Never got clear answer on that one.

The classic sence of a Window Manager is just that, it manages application windows.  Think Fluxbox, Icewm, Window Maker.  

Enlightenment E17 is aiming to be more than just a basic Window Manager, hence the term Desktop Shell.  E17 will eventually have its own fully functional file manager, media player and image viewer/editor.  Most of E17's applications such as the file manager Entropy and the log in manager Entrance are partly finished and working but not always recommended for everyday use.    

> Is it possible to use, today, E17 without any desktop manager ?

You bet.  Enlightenment E17 is its own working environment.  E17 includeds a configuration panel for easily changing themes, fonts, wallpapers, screen resolution, loaded modules, window management options, number of available desktops, and more.  Once you install E17 onto your system you just select Enlightenment from your session manager located in GDM (Gnome's log-in manager).

If you desire you can use Gnome (GTK) and KDE (QT) applications in E17.  Firefox and Thunar are GTK applications and work wonderfully in E17.  

> Not yet clear to me the added value of this new one (compared to XFCe etc...)

To me Enlightenment E17's added value over other window managers and desktop environments such as XFCE, is it's speed, simplicity, and of course its looks.  Just to give you an example of just how light E17 is, I did a command line install of Ubuntu with just E17, Firefox, Thunar and XMMS installed.  After booting up into the E17 desktop my system was only using an incredible 68mb's of ram.  After launching Firefox my use was just over 100mb.   

I would highly recommend just installing E17 and giving a try for at least 1 week.  The installation process is very easy.  If E17 is not for you, you can easily remove it.   

Also, you can easily change GTK themes by using an application called gtk-theme-switch.  You can install it using synaptic or in a terminal with

```
sudo aptitude install gtk-theme-switch 
```

Then in a terminal you can launch gtk-theme-switch with the command 

```
switch2
```

More information on Enlightenment E17 and its related applications can be found at get-e.org.

[http://www3.get-e.org/](http://www3.get-e.org/)

As far as fonts on Linux, I think the default fonts used on Ubuntu look fantastic compared to Windows XP.  

I am also posting a couple of screen captures of E17 taken from my system over the past month.  Maybe they will help encourage you.

---

### Post by L_V on 2007-01-30
Impressive result !
Thank you for your long and very detailed feedback.

BTW, could you help me to identify the right Enlightment sources.list for Debian Etch (the one I use to try).
Thanks.

EDIT: I found the debs ! 
[http://seerofsouls.com/dists/edgy/e17/binary-i386/](http://seerofsouls.com/dists/edgy/e17/binary-i386/)

---

### Post by tcrroadie on 2007-01-30
> **L_V said:**
> Impressive result !
Thank you for your long and very detailed feedback.

BTW, could you help me to identify the right Enlightment sources.list for Debian Etch (the one I use to try).
Thanks.

EDIT: I found the debs ! 
[http://seerofsouls.com/dists/edgy/e17/binary-i386/](http://seerofsouls.com/dists/edgy/e17/binary-i386/)

Are you currently using Debian Etch?  The repository link you listed states that it is for Ubuntu Edgy.  You can give it a try but it may not fully work on your system.  

Also the repsitory listed uses packages that are much older than the repositories supplied by the Elbuntu team.  The Elbuntu team tries to keep current with the CVS snapshots of E17 so they are very recent.  It looks like the Elbuntu repsitories were last updated Jan 26 2007.  The repository you listed is very old, Oct 10 2006.  

If you are also using Ubuntu, are you having any trouble installing E17?  

:confused:

---

### Post by Xummoner on 2007-01-30
I'm getting errors using both apt-get and aptitude, Here's what I get using both (hope someone can help me) I've been trying to install all kinds of eyecandy since I got Ubuntu a couple of months ago with no success at all.

```
david@David-Desktop:~$ sudo aptitude install e17
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan
  emodules0-all
The following NEW packages will be automatically installed:
  enlightenment-theme enlightenment-theme-cthulhain
  enlightenment-theme-darkness enlightenment-theme-kor
  enlightenment-theme-milky enlightenment-theme-simply-white eutils
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-desktop
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job
  libecore1-txt libecore1-x libevas1 libevas1-loader-eet
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png
  libevas1-loader-tiff libevas1-loader-xpm libevas1-loaders-all libexml1
The following NEW packages will be installed:
  enlightenment-theme enlightenment-theme-cthulhain
  enlightenment-theme-darkness enlightenment-theme-kor
  enlightenment-theme-milky enlightenment-theme-simply-white eutils
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-desktop
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job
  libecore1-txt libecore1-x libevas1 libevas1-loader-eet
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png
  libevas1-loader-tiff libevas1-loader-xpm libevas1-loaders-all libexml1
0 packages upgraded, 51 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.0MB of archives. After unpacking 22.6MB will be used.
The following packages have unmet dependencies:
  emodule0-screenshot: Depends: enlightenment but it is not installable
  emodule0-wlan: Depends: enlightenment but it is not installable
  emodule0-language: Depends: enlightenment but it is not installable
  emodules0-all: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mail: Depends: enlightenment but it is not installable
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-photo: Depends: enlightenment but it is not installable
  emodule0-deskshow: Depends: enlightenment but it is not installable
  emodule0-taskbar: Depends: enlightenment but it is not installable
  emodule0-flame: Depends: enlightenment but it is not installable
  emodule0-moon: Depends: enlightenment but it is not installable
  emodule0-mixer: Depends: enlightenment but it is not installable
  emodule0-rain: Depends: enlightenment but it is not installable
  emodule0-cpu: Depends: enlightenment but it is not installable
  emodule0-uptime: Depends: enlightenment but it is not installable
  emodule0-mem: Depends: enlightenment but it is not installable
  emodule0-net: Depends: enlightenment but it is not installable
  emodule0-tclock: Depends: enlightenment but it is not installable
  emodule0-snow: Depends: enlightenment but it is not installable
  emodule0-winselector: Depends: enlightenment but it is not installable
  emodule0-slideshow: Depends: enlightenment but it is not installable
  emodule0-alarm: Depends: enlightenment but it is not installable
  emodule0-weather: Depends: enlightenment but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
enlightenment [1:0.16.7.2-3ubuntu1 (dapper)]
enlightenment-data [1:0.16.7.2-3ubuntu1 (dapper)]
menu [2.1.27 (dapper)]

Score is -197

Accept this solution? [Y/n/q/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  emodule0-screenshot libecore1-desktop emodule0-wlan
  enlightenment-theme-simply-white libevas1-loader-eet libecore1-x
  libevas1-loader-gif libecore1-file emodule0-language libecore1-con
  libecore1-evas libevas1-loader-png libecore1-ipc libexml1 libecore1-job
  libecore1 libevas1-loader-jpeg libecore1-config
  enlightenment-theme-darkness enlightenment-theme-kor emodules0-all
  emodule0-mail libevas1-loader-xpm libevas1-loaders-all e17 emodule0-photo
  libecore1-txt emodule0-deskshow emodule0-taskbar emodule0-flame
  emodule0-moon emodule0-mixer emodule0-rain emodule0-cpu emodule0-uptime
  libecore1-fb emodule0-mem emodule0-net libevas1-loader-tiff
  emodule0-tclock emodule0-snow emodule0-winselector emodule0-slideshow
  enlightenment-theme-cthulhain libecore1-dbus enlightenment-theme-milky
  enlightenment-theme emodule0-alarm eutils libevas1 emodule0-weather

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
The following NEW packages will be automatically installed:
  emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan
  emodules0-all enlightenment enlightenment-data enlightenment-theme
  enlightenment-theme-cthulhain enlightenment-theme-darkness
  enlightenment-theme-kor enlightenment-theme-milky
  enlightenment-theme-simply-white eutils libecore1 libecore1-con
  libecore1-config libecore1-dbus libecore1-desktop libecore1-evas
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt
  libecore1-x libevas1 libevas1-loader-eet libevas1-loader-gif
  libevas1-loader-jpeg libevas1-loader-png libevas1-loader-tiff
  libevas1-loader-xpm libevas1-loaders-all libexml1 menu
The following NEW packages will be installed:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan
  emodules0-all enlightenment enlightenment-data enlightenment-theme
  enlightenment-theme-cthulhain enlightenment-theme-darkness
  enlightenment-theme-kor enlightenment-theme-milky
  enlightenment-theme-simply-white eutils libecore1 libecore1-con
  libecore1-config libecore1-dbus libecore1-desktop libecore1-evas
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt
  libecore1-x libevas1 libevas1-loader-eet libevas1-loader-gif
  libevas1-loader-jpeg libevas1-loader-png libevas1-loader-tiff
  libevas1-loader-xpm libevas1-loaders-all libexml1 menu
0 packages upgraded, 54 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.4MB of archives. After unpacking 30.3MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  emodule0-screenshot libecore1-desktop emodule0-wlan
  enlightenment-theme-simply-white libevas1-loader-eet libecore1-x
  libevas1-loader-gif libecore1-file emodule0-language libecore1-con
  libecore1-evas libevas1-loader-png libecore1-ipc libexml1 libecore1-job
  libecore1 libevas1-loader-jpeg libecore1-config
  enlightenment-theme-darkness enlightenment-theme-kor emodules0-all
  emodule0-mail libevas1-loader-xpm libevas1-loaders-all e17 emodule0-photo
  libecore1-txt emodule0-deskshow emodule0-taskbar emodule0-flame
  emodule0-moon emodule0-mixer emodule0-rain emodule0-cpu emodule0-uptime
  libecore1-fb emodule0-mem emodule0-net libevas1-loader-tiff
  emodule0-tclock emodule0-snow emodule0-winselector emodule0-slideshow
  enlightenment-theme-cthulhain libecore1-dbus enlightenment-theme-milky
  enlightenment-theme emodule0-alarm eutils libevas1 emodule0-weather

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Segmentation faulttate information... 1%
```

```
david@David-Desktop:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
       Depends: emodules0-all (>= 0.16.999) but it is not going to be installed
E: Broken packages

```

---

### Post by nekr0z on 2007-01-30
> As far as fonts on Linux, I think the default fonts used on Ubuntu look fantastic compared to Windows XP.

I would love to hang the bastard that invented these fonts in the boiling oil... How come, that the **default** fonts lack unicode cyrillic letters and just display empty squares instead?

I have installed E17 on an Edgy machine with Russian default locale (which never caused any problems), and found E totally unusable because of the default fonts. Even more, I couldn't change the fonts, because to do it I would have to go through some menus &#8212; and all the menus had all the items looking as one, so I could only guess where I should click...

---

### Post by tcrroadie on 2007-01-30
Xummoner,

Do you have a previous installation of Enlightenment E16 installed?

It looks to me as if apt is try to install E16 along with E17.  

If you have previously installed E16 try this. 

```
sudo apt-get --purge remove enlightenment
```

Then 

```
sudo apt-get clean
```
```

sudo apt-get update
```
```

sudo apt-get install e17

```

If you still run into the same error, try commenting out the regular Ubuntu repositories so that apt only sees the Elbuntu repository available. Then try installing E17 again.

Run the above three commands again. 

Please post back with your results.  I have noticed that there are some other Dapper users that are running into the same error that you are.  

If I have time tonight, I will do a test install of E17 on a Dapper system and get back.  Currently I have only installed E17 using Elbuntu's repositories on Edgy.

---

### Post by Xummoner on 2007-01-30
I'm still getting the same errors after editing the sources list. Synaptic won't install it either, it gives a warning about the packages "enlightenment (>= 0.16.999)" and "emodules0-all", says that they can't be installed and then nothing happens.

---

### Post by tcrroadie on 2007-01-30
> **Xummoner said:**
> I'm still getting the same errors after editing the sources list. Synaptic won't install it either, it gives a warning about the packages "enlightenment (>= 0.16.999)" and "emodules0-all", says that they can't be installed and then nothing happens.

There are two things that you can do at this point.  

1.  Contact the Elbuntu developers on the Elbuntu IRC chat channel at irc.freenode.net
     Contact Lutin or Sp4rKy on #elbuntu and let them know about your installation problem on your 
     Dapper system.   There may be a packaging issue for Dapper.  

2.  You could upgrade your system to Edgy.  Their binary packages install flawlessly on Edgy. 

Sorry I couldn't help more at this point.

---

### Post by Lut!n on 2007-01-30
> **Xummoner said:**
> I'm still getting the same errors after editing the sources list. Synaptic won't install it either, it gives a warning about the packages "enlightenment (>= 0.16.999)" and "emodules0-all", says that they can't be installed and then nothing happens.

The point is, it seems your system is not able to install the enlightenment package.
This could be a wrong pin in /etc/apt/preferences, or some other trouble which I'm not aware of yet

Please post here the log when you try install the enlightenment package, and I'd be more likely able to help you

Cheers
Lut!n

ps: thanks tcrroadie for what you're doing on that topic :)

PPS, as a general notice for users having problems: Post a log that just says 'unable to do it' is quite useless. If you can, look into the log and see what package is causing the error. Then, paste here the log when trying to install this particular package. That'd help really us to fix issues much more quickly. thanks :)

---

### Post by tcrroadie on 2007-01-30
> **Lut!n said:**
> 
PPS, as a general notice for users having problems: Post a log that just says 'unable to do it' is quite useless. If you can, look into the log and see what package is causing the error. Then, paste here the log when trying to install this particular package. That'd help really us to fix issues much more quickly. thanks :)

Thanks for the heads up Lut!n.:)   I myself am still new at trying to problem solve issues with installing binaray packages with apt.  

Other than the output of apt, what log should users post when they encounter installation issues?  In /var/log ?

Thanks.

---

### Post by J.Pulumbarit on 2007-01-30
So i still get this error 

Segmentation fault (core dumped)on... 1%

attached is a file with the full text of what happens leading to the error

---

### Post by Lut!n on 2007-01-31
> **J.Pulumbarit said:**
> So i still get this error 

Segmentation fault (core dumped)on... 1%

attached is a file with the full text of what happens leading to the error

Hehe, forgot that. for tracking issues, aptitude is evil (tm). Please provide apt-get logs instead. Besides, it's what I meant in my previous post: in your log, we can see
```
emodules0-all: Depends: enlightenment (>= 0.16.999) but it is not installable
``` which makes me think of some problem with the 'enlightenment' package installation. Then, please provide the log when trying to install only this particular package.
Thanks :)
Lut!n

---

### Post by adil_uk on 2007-01-31
> **Xummoner said:**
> I'm getting errors using both apt-get and aptitude, Here's what I get using both (hope someone can help me) I've been trying to install all kinds of eyecandy since I got Ubuntu a couple of months ago with no success at all.

```
david@David-Desktop:~$ sudo aptitude install e17
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan
  emodules0-all
The following NEW packages will be automatically installed:
  enlightenment-theme enlightenment-theme-cthulhain
  enlightenment-theme-darkness enlightenment-theme-kor
  enlightenment-theme-milky enlightenment-theme-simply-white eutils
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-desktop
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job
  libecore1-txt libecore1-x libevas1 libevas1-loader-eet
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png
  libevas1-loader-tiff libevas1-loader-xpm libevas1-loaders-all libexml1
The following NEW packages will be installed:
  enlightenment-theme enlightenment-theme-cthulhain
  enlightenment-theme-darkness enlightenment-theme-kor
  enlightenment-theme-milky enlightenment-theme-simply-white eutils
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-desktop
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job
  libecore1-txt libecore1-x libevas1 libevas1-loader-eet
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png
  libevas1-loader-tiff libevas1-loader-xpm libevas1-loaders-all libexml1
0 packages upgraded, 51 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.0MB of archives. After unpacking 22.6MB will be used.
The following packages have unmet dependencies:
  emodule0-screenshot: Depends: enlightenment but it is not installable
  emodule0-wlan: Depends: enlightenment but it is not installable
  emodule0-language: Depends: enlightenment but it is not installable
  emodules0-all: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mail: Depends: enlightenment but it is not installable
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-photo: Depends: enlightenment but it is not installable
  emodule0-deskshow: Depends: enlightenment but it is not installable
  emodule0-taskbar: Depends: enlightenment but it is not installable
  emodule0-flame: Depends: enlightenment but it is not installable
  emodule0-moon: Depends: enlightenment but it is not installable
  emodule0-mixer: Depends: enlightenment but it is not installable
  emodule0-rain: Depends: enlightenment but it is not installable
  emodule0-cpu: Depends: enlightenment but it is not installable
  emodule0-uptime: Depends: enlightenment but it is not installable
  emodule0-mem: Depends: enlightenment but it is not installable
  emodule0-net: Depends: enlightenment but it is not installable
  emodule0-tclock: Depends: enlightenment but it is not installable
  emodule0-snow: Depends: enlightenment but it is not installable
  emodule0-winselector: Depends: enlightenment but it is not installable
  emodule0-slideshow: Depends: enlightenment but it is not installable
  emodule0-alarm: Depends: enlightenment but it is not installable
  emodule0-weather: Depends: enlightenment but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
enlightenment [1:0.16.7.2-3ubuntu1 (dapper)]
enlightenment-data [1:0.16.7.2-3ubuntu1 (dapper)]
menu [2.1.27 (dapper)]

Score is -197

Accept this solution? [Y/n/q/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  emodule0-screenshot libecore1-desktop emodule0-wlan
  enlightenment-theme-simply-white libevas1-loader-eet libecore1-x
  libevas1-loader-gif libecore1-file emodule0-language libecore1-con
  libecore1-evas libevas1-loader-png libecore1-ipc libexml1 libecore1-job
  libecore1 libevas1-loader-jpeg libecore1-config
  enlightenment-theme-darkness enlightenment-theme-kor emodules0-all
  emodule0-mail libevas1-loader-xpm libevas1-loaders-all e17 emodule0-photo
  libecore1-txt emodule0-deskshow emodule0-taskbar emodule0-flame
  emodule0-moon emodule0-mixer emodule0-rain emodule0-cpu emodule0-uptime
  libecore1-fb emodule0-mem emodule0-net libevas1-loader-tiff
  emodule0-tclock emodule0-snow emodule0-winselector emodule0-slideshow
  enlightenment-theme-cthulhain libecore1-dbus enlightenment-theme-milky
  enlightenment-theme emodule0-alarm eutils libevas1 emodule0-weather

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
The following NEW packages will be automatically installed:
  emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan
  emodules0-all enlightenment enlightenment-data enlightenment-theme
  enlightenment-theme-cthulhain enlightenment-theme-darkness
  enlightenment-theme-kor enlightenment-theme-milky
  enlightenment-theme-simply-white eutils libecore1 libecore1-con
  libecore1-config libecore1-dbus libecore1-desktop libecore1-evas
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt
  libecore1-x libevas1 libevas1-loader-eet libevas1-loader-gif
  libevas1-loader-jpeg libevas1-loader-png libevas1-loader-tiff
  libevas1-loader-xpm libevas1-loaders-all libexml1 menu
The following NEW packages will be installed:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan
  emodules0-all enlightenment enlightenment-data enlightenment-theme
  enlightenment-theme-cthulhain enlightenment-theme-darkness
  enlightenment-theme-kor enlightenment-theme-milky
  enlightenment-theme-simply-white eutils libecore1 libecore1-con
  libecore1-config libecore1-dbus libecore1-desktop libecore1-evas
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt
  libecore1-x libevas1 libevas1-loader-eet libevas1-loader-gif
  libevas1-loader-jpeg libevas1-loader-png libevas1-loader-tiff
  libevas1-loader-xpm libevas1-loaders-all libexml1 menu
0 packages upgraded, 54 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.4MB of archives. After unpacking 30.3MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  emodule0-screenshot libecore1-desktop emodule0-wlan
  enlightenment-theme-simply-white libevas1-loader-eet libecore1-x
  libevas1-loader-gif libecore1-file emodule0-language libecore1-con
  libecore1-evas libevas1-loader-png libecore1-ipc libexml1 libecore1-job
  libecore1 libevas1-loader-jpeg libecore1-config
  enlightenment-theme-darkness enlightenment-theme-kor emodules0-all
  emodule0-mail libevas1-loader-xpm libevas1-loaders-all e17 emodule0-photo
  libecore1-txt emodule0-deskshow emodule0-taskbar emodule0-flame
  emodule0-moon emodule0-mixer emodule0-rain emodule0-cpu emodule0-uptime
  libecore1-fb emodule0-mem emodule0-net libevas1-loader-tiff
  emodule0-tclock emodule0-snow emodule0-winselector emodule0-slideshow
  enlightenment-theme-cthulhain libecore1-dbus enlightenment-theme-milky
  enlightenment-theme emodule0-alarm eutils libevas1 emodule0-weather

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Segmentation faulttate information... 1%
```

```
david@David-Desktop:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
       Depends: emodules0-all (>= 0.16.999) but it is not going to be installed
E: Broken packages

```

 
I had the same problem, in my case I had to remove the file /etc/apt/preferences 
. if you have anything of value in it then just delete anything to do with "e17" in the file.

please make backup of the file "preferences" in case it this workaround does not solve the problem.

---

### Post by Lut!n on 2007-01-31
I will never say that enough: pinning enlightenment in /etc/apt/preferences is _evil_
People do that and then forget, leading to this kind of errors. sad :/. 
tcrroadie, would you mind adding a reminder in your first post that'd ask people to check it before any further operations ?.
Thanks ;)

---

### Post by tcrroadie on 2007-01-31
> **Lut!n said:**
> I will never say that enough: pinning enlightenment in /etc/apt/preferences is _evil_
People do that and then forget, leading to this kind of errors. sad :/. 
tcrroadie, would you mind adding a reminder in your first post that'd ask people to check it before any further operations ?.
Thanks ;)

Hi Lut!n.  I was just thinking the same thing you were about adding a cautionary or warning statement to my guide about the use of an /etc/apt/preferences file.  

After adil_uk posted and mentioned the apt preferences file causing installation problems of E17 on his system it hit me, I remembered seeing mention of pinning Enlightenment E17 in previous E17 install threads on the forums here.  Looks like you were right. :) 

I would also like to mention that I just finished an installation of E17 on a fresh install of Dapper and your packages installed flawlessly.  No problems on my end. 

When I get the chance I'll edit my install guide with the mention of editing the users /etc/apt/preferences file if one exist, and stating the removal of any previous pinning of Enlightenment packages.  At the moment, it is time for me to spend some time with the wife.

Thanks.    :D

---

### Post by J.Pulumbarit on 2007-01-31
Lut!n, attached is the other log you wished to see. I am aware that there is something i may have to change in the /etc/apt/prefences or something liek that. I also wanted you to know that I am trying to install e17 on a fresh edgy install...

---

### Post by Lut!n on 2007-02-01
Indeed, seems to be an /ets/apt/preferences issues.
You should try to edit the fle and look for a pin in 'enlightenment'. If there is one , remove it, apt-get update and try again. Everythin should work fine ;)

---

### Post by J.Pulumbarit on 2007-02-01
yes taking out the pin worked, now im on enlightenment. id like to thank anyone and everyone that has helped me, i appreciate it very much and sorry for causing any trouble.

---

### Post by finferflu on 2007-02-09
Is there anyone who can tell me how to set the entrance theme back to default?

With the default theme everything worked, but when I tried to change it, I think it crashes, since I have to login from the command line. I also tried to remove it and delete the configuration with aptitude remove --purge, but I still have no success. I tried changing a couple of themes, but it doesn't work. I tried with the command:

```
entranced -T -t <path to theme>
```

and the test works... but it won't start at the startup... annoying...

another thing: since terminal transparency is enabled with Esetroot, is there any way I can run this command at startup time? I tried to add:

```
exec "Esetroot -scaled <path to file>"
```

in ~/.xinitrc, but it doesn't do anything...

Any help will be greatly appreciated.

Thanks for your time!

---

### Post by tcrroadie on 2007-02-09
> another thing: since terminal transparency is enabled with Esetroot, is there any way I can run this command at startup time? 

I can't personally help you on your issue with Entrance since I haven't used it yet on my system, but I may be able to help out on autostarting Esetroot.  

I'm at work at the moment on a Windows box so I will try to remember how to add applications to E17 startup the best I can.  

You can creat a .desktop launcher (previously named eap file) for Esetroot and place it in the startup directory for E17.  I created a .desktop file for the gnome-settings-daemon so that all of my gtk apps would have the same look as they did under Gnome. 

I believe I just did it by right clicking on the icon in the upper left hand corner of an application window, in my case it was Firefox at the time.  In the window that opens, select "Edit Icon".  In the Application Editor, enter the name for your new application launcher and set your executable options.  In your case, your new application name would be Esetroot and your executable field would be  

[HTML]Esetroot -scaled <path to image file> [/HTML]

If memory serves me right, your newly created .desktop file for Esetroot will be created in /home/user/.e/e/applications/all

To have E17 autostart Esetroot for you, just copy your new Esetroot.desktop file from /home/user/.e/e/applications/all to /home/user/.e/e/applications/startup

```
cp ~/.e/e/applications/all/Esetroot.desktop ~/.e/e/applications/startup
``` 
 
If any of my information is incorrect, please feel free to correct me.

---

### Post by mathmanp on 2007-02-09
To get back to default configuration on entrance you can try:
sudo ./usr/share/entrance/build_config.sh -c /etc/entrance_config.cg
That should generate the default entrance configuration.


Bytheway did anybody else encounter this problem:
When starting a session different from the system default session entrance just executes
the start of the Window Manager/Desktop enviroment but doesn't execute /etc/X11/Xsession
so no session dbus is running ?

---

### Post by finferflu on 2007-02-09
@ tcrroadie

Thanks a lot, I haven't got much time tonight, but I'll try that tomorrow and I'll tell you how it goes. Thanks!

> **mathmanp said:**
> To get back to default configuration on entrance you can try:
sudo ./usr/share/entrance/build_config.sh -c /etc/entrance_config.cg
That should generate the default entrance configuration.


I get this:
```
$ sudo ./usr/share/entrance/build_config.sh -c /etc/entrance_config.cg
sudo: ./usr/share/entrance/build_config.sh: command not found
```

It seems I've got something missing...

---

### Post by mathmanp on 2007-02-09
Sorry this file doesn't seem to be in the package, still was in my directory from an old CVS built. I attach it here, but cannot give a garanty that it works properly with the packages.

---

### Post by finferflu on 2007-02-09
Thanks! The script worked, I think, I had some output. Entrance is not starting anyway... I hate when those things happen...

---

### Post by mathmanp on 2007-02-09
I did some tests. Obviously the configuration file of entrance doesn't accept paths for the themes. Copying the themes in the directory where the default themes are stored 
```
/usr/share/entrance/themes/
```
and doing e.g.
```
sudo entrance_edit --theme supertheme.edj
```
(if supertheme.edj is the name of the theme you want to use.
activates the theme.  For activating entrance at startup make sure you made it your default display manager.
Depending on what is your default is now try
```
sudo dpkg--reconfigure gdm
```
or ```
sudo dpkg--reconfigure entrance
```
or ```
sudo dpkg--reconfigure kdm
```

If everything else fails delete the configuration file
```
/etc/entrance_config.cfg
```
and reinstall. 

So entrance should run, but as I said at least in my case I have problems with the sessions started by entrance.

---

### Post by finferflu on 2007-02-10
> **mathmanp said:**
> I did some tests. Obviously the configuration file of entrance doesn't accept paths for the themes. Copying the themes in the directory where the default themes are stored 
```
/usr/share/entrance/themes/
```
and doing e.g.
```
sudo entrance_edit --theme supertheme.edj
```
(if supertheme.edj is the name of the theme you want to use.
activates the theme.  For activating entrance at startup make sure you made it your default display manager.
Depending on what is your default is now try
```
sudo dpkg--reconfigure gdm
```
or ```
sudo dpkg--reconfigure entrance
```
or ```
sudo dpkg--reconfigure kdm
```

If everything else fails delete the configuration file
```
/etc/entrance_config.cfg
```
and reinstall. 

So entrance should run, but as I said at least in my case I have problems with the sessions started by entrance.

Yeah! You're my hero! :smile: 
Thanks for spending so much time! Actually on get-e they say you can put the theme anywhere, and then just specify the path. They should be aware of this problem. 

As for the problem you encounter, I'm not so experienced, so I might get the same thing, but I haven't noticed anything so far (as I said entrance worked with the default theme). I don't know what you mean by "session dbus", so I might have not noticed its loss...

Thank you!

---

### Post by finferflu on 2007-02-10
> **tcrroadie said:**
> I can't personally help you on your issue with Entrance since I haven't used it yet on my system, but I may be able to help out on autostarting Esetroot.  

I'm at work at the moment on a Windows box so I will try to remember how to add applications to E17 startup the best I can.  

You can creat a .desktop launcher (previously named eap file) for Esetroot and place it in the startup directory for E17.  I created a .desktop file for the gnome-settings-daemon so that all of my gtk apps would have the same look as they did under Gnome. 

I believe I just did it by right clicking on the icon in the upper left hand corner of an application window, in my case it was Firefox at the time.  In the window that opens, select "Edit Icon".  In the Application Editor, enter the name for your new application launcher and set your executable options.  In your case, your new application name would be Esetroot and your executable field would be  

[HTML]Esetroot -scaled <path to image file> [/HTML]

If memory serves me right, your newly created .desktop file for Esetroot will be created in /home/user/.e/e/applications/all

To have E17 autostart Esetroot for you, just copy your new Esetroot.desktop file from /home/user/.e/e/applications/all to /home/user/.e/e/applications/startup

```
cp ~/.e/e/applications/all/Esetroot.desktop ~/.e/e/applications/startup
``` 
 
If any of my information is incorrect, please feel free to correct me.


No, it didn't work. When I edited the firefox icon, it simply changed the icon properties, so that firefox had become Esetroot. Moreover there was no Esetroot.desktop in ~/.e/e/applications/all/. I have tried to open firefox.desktop with a text editor, and I can see this:  

```
[Desktop Entry]
Encoding=UTF-8
X-Enlightenment-IconClass=web_browser.png,firefox.edj,firefox
Type=Application
Exec=firefox
StartupNotify=true
StartupWMClass=Firefox-bin
GenericName=Web Browser
X-Enlightenment-IconPath=/usr/share/enlightenment/data/icons/web_browser.png
Name=Firefox
Comment=Browse the Internet
Icon=web_browser.png
```

Maybe it's easier to create another one in this way, but I don't know how to fill in all the parameters...

Thanks a lot!

---

### Post by Onyros on 2007-02-10
tcrroadie, mate, what are you using as a system tray, if you're using any, right now?

BTW, here's my e17 setup, I stole a few ideas from Elive Revolution, and adapted according to my own taste.

[[img]http://img442.imageshack.us/img442/115/e17bo2.th.png[/img]](http://img442.imageshack.us/my.php?image=e17bo2.png)

Ubuntu Edgy Eft (6.10)
Enlightenment 17, under the Milky theme :P
System Monitor: Conky
Icon set: a mix of a whole lot of icons, the basics coming from NuoveXT
XMMS Skin: Almond
File Manager: PCManFM
Dock: iBar
"System Tray": iBox
Terminal: xterm -fg white -bg black (foreground white, background black)

---

### Post by mehaga on 2007-02-11
I get this when I try to load most of the modules:

'[I]There was an error loading module named: xxxx
No module namex xxx/linux-gnu-i486/module.so could be found in th module search directories...[/I]'

module.so are located in /lib/enlightenment/xxxx/linux-gnu-i686, not .../i486.

How do I fix this, please?

---

### Post by tcrroadie on 2007-02-11
^finferflu^
> 
No, it didn't work. When I edited the firefox icon, it simply changed the icon properties, so that firefox had become Esetroot. Moreover there was no Esetroot.desktop in ~/.e/e/applications/all/. I have tried to open firefox.desktop with a text editor, and I can see this:

Sorry, I could have sworn I created a launcher that way over a week ago for my system.  Since I am sitting right in front of my E17 system at the moment, lets try another way. 

Bring up E17's main menu and select Configuration -> Configuration Panel

Under the Categories column select Applications then Startup Applications from the right column.

Then in the window that pops up select Create a new Application.

A new window named Application Editor will open.  Simply fill in the fields then click the Apply button.  A new application launcher will then be available in the column named Available Applications in the Startup Applications Window.  

Checkmark the All Applications box and scroll down to the bottom of the list.  Your new launcher for Esetroot should be available.  To add your new Esetroot laucher to the Startup column, simply drag and drop the Esetroot launcher from the Available Applications column to the Startup column.  That should do it for you.  The next time you start E17, Esetroot should start in the background.  

Please see my screenshots for more info.  

Hope this helps out more.

---

### Post by finferflu on 2007-02-11
That was lovely, thank you very much!

The only thing I really miss in Enlightenment, by the way, is a proper status/tray bar. For example when I use apps like gaim I want to feel the difference between the main window and the chat windows, I don't want the minimized windows to be iconified, and I don't want the iconified windows to appear as minimized windows when I use the task bar. It gets very messy. Also, some apps that work best as tray icons don't work properly in Enlightenment: Kbittorrent, for example, even when it's started doesn't show up, and I don't know how to get hold of it, I can only see its messages like: "Download complete". I know it's pre-alpha stage, but I hope those features will be improved, that is, I hope the ibox is gonna have tray bar functionalities, and that there will be a difference between iconified windows and minimized ones...

---

### Post by tcrroadie on 2007-02-11
> **Onyros said:**
> tcrroadie, mate, what are you using as a system tray, if you're using any, right now?

BTW, here's my e17 setup, I stole a few ideas from Elive Revolution, and adapted according to my own taste.

[[img]http://img442.imageshack.us/img442/115/e17bo2.th.png[/img]](http://img442.imageshack.us/my.php?image=e17bo2.png)

Ubuntu Edgy Eft (6.10)
Enlightenment 17, under the Milky theme :P
System Monitor: Conky
Icon set: a mix of a whole lot of icons, the basics coming from NuoveXT
XMMS Skin: Almond
File Manager: PCManFM
Dock: iBar
"System Tray": iBox
Terminal: xterm -fg white -bg black (foreground white, background black)

Hi Onyrus.  I am just using E17's standard modules.  I am currently just using one shelf placed at the bottom of my screen.  I am using the ibar, taskbar, pager, start, and clock modules.  

You can have multiple shelfs on your desktop.  For example, using your screenshot you posted as an example, you can place an additional shelf at the top of your screen with a second ibar module loaded on it.  You can also place the shelf contents anywhere on the screen.  

Nice screencapture.  I read in another post that PCman is a good file manager to use.  I'll have to give it a try some time.

---

### Post by finferflu on 2007-02-11
> **tcrroadie said:**
> 
You can have multiple shelfs on your desktop.  For example, using your screenshot you posted as an example, you can place an additional shelf at the top of your screen with a second ibar module loaded on it.  You can also place the shelf contents anywhere on the screen.  


Multiple shelves will cost you some speed though. I've been using 3, and when I went back to only 1 shelf I could notice the difference.

How can you place shelf contents on the screen? Thanks!

---

### Post by mathmanp on 2007-02-11
> **finferflu said:**
> That was lovely, thank you very much!

The only thing I really miss in Enlightenment, by the way, is a proper status/tray bar. For example when I use apps like gaim I want to feel the difference between the main window and the chat windows, I don't want the minimized windows to be iconified, and I don't want the iconified windows to appear as minimized windows when I use the task bar. It gets very messy. Also, some apps that work best as tray icons don't work properly in Enlightenment: Kbittorrent, for example, even when it's started doesn't show up, and I don't know how to get hold of it, I can only see its messages like: "Download complete". I know it's pre-alpha stage, but I hope those features will be improved, that is, I hope the ibox is gonna have tray bar functionalities, and that there will be a difference between iconified windows and minimized ones...

[LEFT][/LEFT]

If you need a traybar you could try out "trayer", it's not E-based but might be a drop in.
just 
```
apt-get install trayer
```
installs it, to lauch as a traybar type:
```
trayer --SetDockType true
```

There are also options to manipulate width, heith and alignment, and it also has a --tranparency option which might work if you used Esetroot (I didn' try though.)
Best you read the manpage for all available options.

If you don't like it, most applications have an option in their configuration dialog to disable
the "show tray icon" option (at least the KDE apps I had problems with had), which at least keeps them from vanishing or not popping up a window.

---

### Post by Daveth on 2007-02-18
Well, the install went just fine using the guide, and it is very fast on my machine.

But how do you reverse the mouse buttons ? All I can see is mouse button key bindings rather than a switch left and right mouse buttons for left handers. I assume it is a /etc/X11/xorg.conf edit, but what is it I change?

Thanks

---

### Post by bestial on 2007-02-18
Onyros: what's that nice lookin' uptime-app called? Would love to have it on my own desktop!

Also, anyone got any great site with modules etc.? Cause e-get is a little bit empty.

---

### Post by MkfIbK7a on 2007-02-25
e17 is 30000x better than e16 ever was...

---

### Post by klittzzer on 2007-02-28
Dunno if this is of any interest to anyone. I saw another topic about using e17 and gnome together but found an easier (I think) way to do it.

All I did was install gtk-theme-switch with synaptic (I don't know if this is necessary) and when logged into e17, entered

:~$ gnome-theme-manager

in a terminal (works in eterm and the one that comes with gnome) while inside e17 and choose the GTK2 style I want in the control tab and likewise with the icons. Metacity is obviously disabled in e17 and the terminal will moan about not being able to open Metacity and thus there is no option to select a window border in the theme settings.

Once I have done that I have all the drop shadows etc that Enlightenment offers along with the gtk controls with all of my applications I have in gnome.

I prefer to browse for files with nautilus instead of the default enlightenment one (is this configurable so that I can have folders in a window instead of the menu list style?) so I created a launcher in the ibar in e17 which runs with 'nautilus --no-desktop'. Same goes for other gnome apps.

I can't seem to get the e17 apps,(entropy etc rtc) to install with synaptic from the SeerOfSouls repos because of dependency issues (eet, libeet, same thing aren't they) which all end up with libeet not being available. 'sudo aptitude install emodules0all' or 'sudo aptitude install entropy' doesn't work. I know how to compile these missing dependencies and know where to find them. The problem is, on the web page that lists the lib files there are about a dozen 'eet' files with diff numbers and I haven't a clue as to what one I need. If anyone can help with this I will be grateful. I would rather try the applications that have been built for e17 instead of using nautilus etc.

I have done a couple of screenshots. I have only been using Linux for a few months now and think it is great. A bit frustrating at times but I have learnt a lot more about computers and software in these last 3 months than I did in years of using windows.

[ATTACH]26334[/ATTACH]

[ATTACH]26335[/ATTACH]

[ATTACH]26336[/ATTACH]

PEACE

---

### Post by steve101101 on 2007-03-01
worked great. thanks for the great guide.

---

### Post by tcrroadie on 2007-03-01
^^klittzzer^^

Thanks for adding the tip.  

As an added note on how to get GTK applications to use the widget and icon themes that where set in gnome-theme-manager, gnome-settings-daemon can be added to E17 Startup Applications.  

Simply follow my instructions in the link below, and when creating a new application launcher, simply replace the reference to Esetroot to gnome-settings-daemon.

[http://www.ubuntuforums.org/showpost.php?p=2139824&postcount=133](http://www.ubuntuforums.org/showpost.php?p=2139824&postcount=133)

---

### Post by Lut!n on 2007-03-01
> **klittzzer said:**
> 

I can't seem to get the e17 apps,(entropy etc rtc) to install with synaptic from the SeerOfSouls repos because of dependency issues (eet, libeet, same thing aren't they) which all end up with libeet not being available. 'sudo aptitude install emodules0all' or 'sudo aptitude install entropy' doesn't work.

Those repos are no longer maintained, imho you'd better remove all your packages and follow the howto on the first post of this thread :)

As a side note concerning the gtk look'n'feel thing, here is a tip that can make you have the desired behaviour without even having to launch gnome-settings-daemon (hay, that eats ram)
just add and adapt the following lines in ~/.gtkrc-2.0:
```
gtk-font-name = "Bitstream Vera Sans 7"
gtk-theme-name = "Human"
gtk-icon-theme-name = "Human"
```
And then, enjoy the gtk looknfeel with 10Mo ram freed ;) (works fine on edgy)

Cheers
Lut!n

---

### Post by klittzzer on 2007-03-01
Cheers for letting me know how to get the gtk stuff working properly. It makes more sense configuring it the way tcrroadie said and even more sense to edit the .gtkrc2.0 file.

Doing it the way I mentioned above just proves I am an amateur. :confused: 

I think I installed this e17 version from those repos you mentioned but will try again after I have disabled the SOS ones. They seem to be the cause of the dependency issues. 

Cheers again for the advice.

kl

:)

ps whenever I do  'sudo apt-get update' I always get loads of 'failed to fetch' messages at the end of the output. Is this standard behaviour or am I doing something daft? Sometimes I get very few of the errors but most of the time I get loads. Some are found but if I do update again to rectify the errors they get fixed but others which were ok previously can't be found. As I said, I am an amateur really. Any ideas?

---

### Post by tcrroadie on 2007-03-01
> **klittzzer said:**
> 

ps whenever I do  'sudo apt-get update' I always get loads of 'failed to fetch' messages at the end of the output. Is this standard behaviour or am I doing something daft? Sometimes I get very few of the errors but most of the time I get loads. Some are found but if I do update again to rectify the errors they get fixed but others which were ok previously can't be found. As I said, I am an amateur really. Any ideas?

Please post the output you receive from apt when you run 
```

sudo apt-get update
```

Please also post your apt sources.list
```

cat /etc/apt/sources.list

```

You are probably just hitting a third party repository that is experiencing heavy load or is being poorly maintained.

---

### Post by klittzzer on 2007-03-02
Hello again tcrroadie. Thanx for taking interest in my 'apt update' dilemma.:) 
I took notice of your 'third party' comment and as a result have reconfigured my /etc/apt/sources.list. I did have a greedy list really and didn't need half of the stuff that was on there. I have subsequently made it easier to read, cut a load of the 3rd party repos out, and am getting an error free update most of the time.

I still have a dilemma though and wonder what your opinion of this is...

Ok, I had enlightenment DR17 installed and running ok. The repositories I used to install that working one were-

############## E17 Repository "e17.dunnewind.net"

deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17
deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17

############### edevelop - e17 (Enlightenment DR 17)

deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb [http://edevelop.org/~lut1n/ubuntu](http://edevelop.org/~lut1n/ubuntu) edgy e17

Ok, as I said the enlightenment desktop was running well, blah, blah, blah.

And then I found this one...

##################  e17 repository from Elive

deb [http://www.vobcopy.org/mirror/elive/](http://www.vobcopy.org/mirror/elive/) elive main efl elive 

So I commented out the first lot, cut and paste the Elive one above into my sources.list, updated apt, and had a look in synaptic to see if there were any differences between the two. 
There are. It looks like there are a lot more themes and applications on the Elive repo in comparison to the dunnewind/edevelop repos.

I am getting well confused now with all this. If I try to download a new theme from the Elive repo apt wants to delete all of the e17 stuff that I got from edevelop & dunnewind.](*,)  That will leave me with a few extra themes but no e17 desktop to use them in won't it?:(  Is it a matter of uninstalling all of the edevelop stuff, swapping the comments on the sources.list, apt update, and then reinstalling it with the Elive repo?

As I said, I am getting well confused with it.:confused:  It seems that different repos have different dependencies and all that. I also reckon that some of the probs I have been having with apt are down to me having conflicting e17 repos-I think?? I dunno really. I am just a humble Linux amateur who misspent his youth getting into strife on the streets and pubs of London and got left behind by the rest of the techno kids in my generation.:confused: 

Clue me in to this confusing scenario tcr if you can m8. I will be grateful.
Also, how do you get a cool picture beside your name in the forum? 

Here is my /etc/apt/sources.list (I know it is long but I put all of the ##### and spaces so that I could find the erroneus repos and comment or delete them). (I know,I have got A LOT to learn)#-o 

[ATTACH]26483[/ATTACH]

Take it easy tcrroadie
and anyone else who passes through this neck of the woods

PEACE

kl

---

### Post by tcrroadie on 2007-03-02
^^^klittzzer^^^

Thanks for posting back.  First I would like to ask what your reasoning in using Elive's repository is?  Have you used Elive before?  

There are Major differences in the packages at Elive's repository compared to that of Elbuntu's repositories.  Elive uses a much older version of E17 compared to the version that the Elbuntu team is using.  The Elbuntu team packages E17 for Ubuntu from the latest current 
CVS snapshots.  If you download and boot an Elive live cd you will see the differences.  E17 on Elive is missing much of the configuration utilities that the current version of E17 has.  

The Elive developers configure all of their packages to work specifically with the latest testing version of Debian, Etch I think.  

If you want to use E17 on Ubuntu, do not mix repositories, and I would not try to use Elive's repos on you Ubuntu system.  I may break it, and trust me, the version of E17 that Elive is using is no where near as nice as the current release of E17 that the Elbuntu developers offer.

If you would like to try out Elive, I would recommend just downloading the ISO and running it from the cd.  I'm an Elive user myself and use it from time to time at work on my lunch break.  It's fun to play with.  

Now on to your source list.  You are doing a great job at listing comments in your source list.  The only thing that I would mention at this time is to remove the Elive repository and only use one of the available Elbuntu E17 mirrors.  You can just comment one of the repos like this

############## E17 Repository "e17.dunnewind.net"

#deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17
#deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17

############### edevelop - e17 (Enlightenment DR 17)

deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
[COLOR="Red"]Remove this line[/COLOR]
#deb [http://edevelop.org/~lut1n/ubuntu](http://edevelop.org/~lut1n/ubuntu) edgy e17 

Thanks for posting back.  :)

---

### Post by tcrroadie on 2007-03-02
```
Also, how do you get a cool picture beside your name in the forum? 
```

You can set an Avatar in your Profile.  Click the 'Quick Links' tab, then Edit Profile->Edit Avatar (in left column under Control Panel).

---

### Post by hanzomon4 on 2007-03-02
How do you place modules on the screen? Like I want to move the clock to the upper-left corner but when I drag it from the shelf it just disappears.

---

### Post by tcrroadie on 2007-03-02
> **hanzomon4 said:**
> How do you place modules on the screen? Like I want to move the clock to the upper-left corner but when I drag it from the shelf it just disappears.

Simply create an additional shelf placed at the top of your screen.  

From E17's main menu, select Configuration->Shelves.  Click the 'Add' button to add an additional shelf to your desktop.  Then click on your new shelve and click the Configure button.  The rest is pretty self explanatory.

---

### Post by klittzzer on 2007-03-03
tcrroadie,

thanx m8.

You're dead right about that elive lot. Why are they putting progs on their server that don't work? I have even heard that the elive cd image doesn't work. I took your word for it and commented the elive repo out. I will probably delete it as it is not much cop. I tried the 'alien' gtk2 engine and that crashes x every time. Those elive people are struggling ain't they?

What do you think of the kwin in gnome thing? I tried kde when I first got on the linux tip but much prefer gnome. Apprently the kwin will only replace meta-city. i don't think meta-city is that bad or boring.

Take it easy tcrroadie

PEACE

kl

---

### Post by Atreus12 on 2007-03-05
Hey all!

I am running 6.06 dapper

I recently tried the live cd for elive, and am hooked on enlightenment as a window manager. I attemped to install following the instructions in this thread, and here is what I got:

NM: Repos were down

---

### Post by hornett on 2007-03-05
> **Atreus12 said:**
> Hey all!

I am running 6.06 dapper

<SNIP>

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

I didn't attept to install, because it didn't look like it was going to go. Any advice?

Same here, except I'm running Edgy. :-k I'm not used to aptitude, is it safe to let it go ahead with that?

---

### Post by Lut!n on 2007-03-05
Please paste here your sources.list, and check if you don't have any pin /etc/apt/preferences for enlightenment dr17. I just tried and it worked fine, so I can't tell much :/

---

### Post by Atreus12 on 2007-03-05
etc/apt/preferences  does not exist on my machine

NM: repos were down

---

### Post by polydectes on 2007-03-05
It appears that the e17 repositories are currently down.  I've been trying all day to rebuild my e17 and received errors about mismatched dependencies and now the 404 error.

---

### Post by nlogax on 2007-03-06
Yes, the E17 repos are down...  I want to cry :-(

I need to install it on this laptop to replace Fluxbox.  I've posted on the edevelop forums so hopefully they're working on the problem.

---

### Post by Lut!n on 2007-03-06
Ok, should be fixed now. tahnks for your reports :)

---

### Post by Atreus12 on 2007-03-06
Awesome! It worked!

---

### Post by hornett on 2007-03-06
Yep, fixed thank-you!:guitar:

---

### Post by voltron87 on 2007-03-10
I've looked and tried but how do you change your favorite applications. I go into the favorites folder but i am unable to add anything into it or remove anything. Thanks

---

### Post by nlogax on 2007-03-10
First you want to copy all of the .desktop files for all installed applications on your machine to E17's local application store:

```
cp /usr/share/applications/*.desktop ~/.e/e/applications/all
```

The menu hierarchy begins at ~/.e/e/applications/menu/favorite/, and in this directory there is a file called .order which lists the programs at the top level.  Simply type the full name of the .desktop file into this file, e.g.

```
gaim.desktop
firefox.desktop
```

Make directories for any submenus you wish to have, and likewise simply create a file named .order in each one listing each .desktop file.

There may be a way to do this through the GUI itself, but I'm not aware of it (and haven't looked). Let me know if you need any part of this clarified.

---

### Post by tcrroadie on 2007-03-10
> **nlogax said:**
> 

There may be a way to do this through the GUI itself, but I'm not aware of it (and haven't looked). Let me know if you need any part of this clarified.

E17 main menu -> Configuration -> Application Menus

---

### Post by jjalocha on 2007-03-10
I am trying to install Enlightenment E17 on a clean (server) installation of Ubuntu Edgy, but i am unable to start enlightenment. What i have done so far:

* Clean install of Ubuntu with the [FONT="Fixedsys"]server[/FONT] option
* Add the edevelop.org repository to [FONT="Fixedsys"]/etc/apt/sources.list[/FONT]
* [FONT="Fixedsys"]wget [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)[/FONT]
* [FONT="Fixedsys"]sudo apt-key add repo_key.asc[/FONT]
* [FONT="Fixedsys"]sudo apt-get update[/FONT]
* [FONT="Fixedsys"]sudo apt-get upgrade[/FONT]
* [FONT="Fixedsys"]sudo apt-get install e17[/FONT]
* [FONT="Fixedsys"]sudo apt-get install xorg[/FONT]

When i try to start enlightenment with [FONT="Fixedsys"]startx[/FONT], i get the following error:

> 
Enlightenment Error.
You are executing enlightenment directly. This is bad. Please do not execute the "enlightnment" binary. Use the "enlightenment_start" launcher. It will handle setting up environment variables, paths, and launching any other required services etc. before enlightenment itself begins running.



Installing [FONT="Fixedsys"]entrance[/FONT] from the same repository has not solved the problem.

The [FONT="Fixedsys"]/usr/share/xsessions/enlightenment.desktop[/FONT] file looks OK to me:

```


[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Log in using Enlightenment (Version 0.16.999.037)
Type=XSession
Icon=/usr/share/enlightenment/data/images/enlightenment.png
Exec=/usr/bin/enlightenment_start
TryExec=/usr/bin/enlightenment_start


```

Does anybody know what else could be missing?

---

### Post by john_spiral on 2007-03-11
> **jjalocha said:**
> I am trying to install Enlightenment E17 on a clean (server) installation of Ubuntu Edgy, but i am unable to start enlightenment. What i have done so far:

* Clean install of Ubuntu with the [FONT="Fixedsys"]server[/FONT] option
* Add the edevelop.org repository to [FONT="Fixedsys"]/etc/apt/sources.list[/FONT]
* [FONT="Fixedsys"]wget [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)[/FONT]
* [FONT="Fixedsys"]sudo apt-key add repo_key.asc[/FONT]
* [FONT="Fixedsys"]sudo apt-get update[/FONT]
* [FONT="Fixedsys"]sudo apt-get upgrade[/FONT]
* [FONT="Fixedsys"]sudo apt-get install e17[/FONT]
* [FONT="Fixedsys"]sudo apt-get install xorg[/FONT]

When i try to start enlightenment with [FONT="Fixedsys"]startx[/FONT], i get the following error:



Installing [FONT="Fixedsys"]entrance[/FONT] from the same repository has not solved the problem.

The [FONT="Fixedsys"]/usr/share/xsessions/enlightenment.desktop[/FONT] file looks OK to me:

```


[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Log in using Enlightenment (Version 0.16.999.037)
Type=XSession
Icon=/usr/share/enlightenment/data/images/enlightenment.png
Exec=/usr/bin/enlightenment_start
TryExec=/usr/bin/enlightenment_start


```

Does anybody know what else could be missing?

I'm sure your need to have **xorg** installed before E17?

---

### Post by yabbadabbadont on 2007-03-11
> **jjalocha said:**
> I am trying to install Enlightenment E17 on a clean (server) installation of Ubuntu Edgy, but i am unable to start enlightenment. What i have done so far:

* Clean install of Ubuntu with the [FONT="Fixedsys"]server[/FONT] option
* Add the edevelop.org repository to [FONT="Fixedsys"]/etc/apt/sources.list[/FONT]
* [FONT="Fixedsys"]wget [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)[/FONT]
* [FONT="Fixedsys"]sudo apt-key add repo_key.asc[/FONT]
* [FONT="Fixedsys"]sudo apt-get update[/FONT]
* [FONT="Fixedsys"]sudo apt-get upgrade[/FONT]
* [FONT="Fixedsys"]sudo apt-get install e17[/FONT]
* [FONT="Fixedsys"]sudo apt-get install xorg[/FONT]

When i try to start enlightenment with [FONT="Fixedsys"]startx[/FONT], i get the following error:



Installing [FONT="Fixedsys"]entrance[/FONT] from the same repository has not solved the problem.

The [FONT="Fixedsys"]/usr/share/xsessions/enlightenment.desktop[/FONT] file looks OK to me:

```


[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Log in using Enlightenment (Version 0.16.999.037)
Type=XSession
Icon=/usr/share/enlightenment/data/images/enlightenment.png
Exec=/usr/bin/enlightenment_start
TryExec=/usr/bin/enlightenment_start


```

Does anybody know what else could be missing?

That desktop file is only used when you login using GDM or KDM or some other graphical login manager.  When you run startx, you need to have /usr/bin/enlightenment_start in your ~/.xinitrc file.

---

### Post by jjalocha on 2007-03-11
I don't think it makes much difference, and I don't remember very well, but I think I installed e17 and xorg in that order.

Anyway, creating .xinitrc solved the issue. I'm writing this from my new enlightenment installation --at least!

BTW. Does anybody know, if it is possible to set this up in a more general way, or is it absolutely necessary to create the .xinitrc for every new user?

Thank you very much for your help!

---

### Post by Faytz on 2007-03-11
Nice. I always thought id have to get elbuntu to get enlightenment guess not. Thanks!
(Reason why i said this is because elbuntu is still 0.1  X_X)

---

### Post by kopilo on 2007-03-12
Worked like a charm, thanks for posting this howto and repository links. =)

---

### Post by nrKist on 2007-03-16
I've been meaning to say thanks tcrroadie. So far E17 is the only window manager that has all of the fn buttons working on my Toshiba Satellite L25.

Side note. I like your alias. My LBS has a bright yellow NOS '04 TCR Alloy that I'd love to get my hands on.

---

### Post by Stone123 on 2007-03-18
Off topic question:

Whats with the slowness of elbuntu team and inactivity

---

### Post by Sp4rKy on 2007-03-19
> **Stone123 said:**
> Off topic question:

Whats with the slowness of elbuntu team and inactivity

Hi,
The elbuntu team is very small in fact :
Lut!n who to the biggest part of work in repo & packaging
Me who build the Elbuntu distro
ZaZo0o who works on artwork
(+ people for docs).

And in the last few days, i got a lot of issue with my server. So the development  of Elbuntu is a bit slow actually. Anyway, my first test work and i think i'll upload the first iso in a few days.

Anyway, feel free to join us if you want speed up the Elbuntu dev :)

---

### Post by Stone123 on 2007-03-19
> **Sp4rKy said:**
> Hi,
The elbuntu team is very small in fact :
Lut!n who to the biggest part of work in repo & packaging
Me who build the Elbuntu distro
ZaZo0o who works on artwork
(+ people for docs).

And in the last few days, i got a lot of issue with my server. So the development  of Elbuntu is a bit slow actually. Anyway, my first test work and i think i'll upload the first iso in a few days.

Anyway, feel free to join us if you want speed up the Elbuntu dev :)

Ok i was jumping in #elbuntu channel on freenode to see what needs to be done. I'll check out launcpad to see if i can join.

---

### Post by drf_av on 2007-03-21
I just wanted to say thanks!
Enlightenment worked out of the box with my brand-new Feisty install and it took me 5 minutes to forget how gnome looked like ;)
And, Flame thing is sick :|

---

### Post by kopilo on 2007-03-21
mmmhmmm, also try getting an animated backgrounds off of [get-e]("http://www4.get-e.org/") (such as the one of the world).

---

### Post by dbbolton on 2007-03-22
```
daniel@lennox:~$ sudo aptitude install e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-forecasts emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan emodules0-all 
The following NEW packages will be automatically installed:
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1 
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 libungif4g 
The following NEW packages will be installed:
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1 
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 libungif4g 
0 packages upgraded, 54 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.2MB of archives. After unpacking 24.2MB will be used.
The following packages have unmet dependencies:
  emodule0-screenshot: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-wlan: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-language: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodules0-all: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mail: Depends: enlightenment (>= 0.16.999) but it is not installable
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-photo: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-deskshow: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-taskbar: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-flame: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-moon: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mixer: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-rain: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-cpu: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-uptime: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mem: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-net: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-tclock: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-snow: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-winselector: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-slideshow: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-alarm: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-forecasts: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-weather: Depends: enlightenment (>= 0.16.999) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
enlightenment [1:0.16.7.2-3ubuntu1 (edgy)]
enlightenment-data [1:0.16.7.2-3ubuntu1 (edgy)]
libimlib2 [1.3.0.0debian1-4~edgy1 (edgy, edgy)]

Score is -197

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be automatically installed:
  emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-forecasts emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan emodules0-all enlightenment enlightenment-data 
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1 
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 libimlib2 libungif4g 
The following NEW packages will be installed:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-forecasts emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan emodules0-all enlightenment enlightenment-data 
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1 
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 libimlib2 libungif4g 
0 packages upgraded, 57 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.4MB of archives. After unpacking 30.9MB will be used.
Do you want to continue? [Y/n/?] Y
Segmentation fault (core dumped)on... 1%

```

---

### Post by Lut!n on 2007-03-23
> **dbbolton said:**
> ```
daniel@lennox:~$ sudo aptitude install e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-forecasts emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan emodules0-all 
The following NEW packages will be automatically installed:
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1 
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 libungif4g 
The following NEW packages will be installed:
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1 
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 libungif4g 
0 packages upgraded, 54 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.2MB of archives. After unpacking 24.2MB will be used.
The following packages have unmet dependencies:
  emodule0-screenshot: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-wlan: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-language: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodules0-all: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mail: Depends: enlightenment (>= 0.16.999) but it is not installable
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-photo: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-deskshow: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-taskbar: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-flame: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-moon: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mixer: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-rain: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-cpu: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-uptime: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mem: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-net: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-tclock: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-snow: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-winselector: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-slideshow: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-alarm: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-forecasts: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-weather: Depends: enlightenment (>= 0.16.999) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
enlightenment [1:0.16.7.2-3ubuntu1 (edgy)]
enlightenment-data [1:0.16.7.2-3ubuntu1 (edgy)]
libimlib2 [1.3.0.0debian1-4~edgy1 (edgy, edgy)]

Score is -197

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be automatically installed:
  emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-forecasts emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan emodules0-all enlightenment enlightenment-data 
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1 
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 libimlib2 libungif4g 
The following NEW packages will be installed:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-forecasts emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan emodules0-all enlightenment enlightenment-data 
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1 
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 libimlib2 libungif4g 
0 packages upgraded, 57 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.4MB of archives. After unpacking 30.9MB will be used.
Do you want to continue? [Y/n/?] Y
Segmentation fault (core dumped)on... 1%

```

I'd say you probably have a pin on enlightenment in /etc/apt/preferences. Please check it and remove it if there's one
Cheers

---

### Post by bettlebrox on 2007-03-24
Anyone know if there are packages for feisty or will the edgy packages work in feisty? A little googling turns up this page:

[http://ubuntuos.wordpress.com/2007/03/12/howto-ubuntu-feisty-install-e17-enlightenment-desktop/](http://ubuntuos.wordpress.com/2007/03/12/howto-ubuntu-feisty-install-e17-enlightenment-desktop/)

So I''m hoping that the edgy packages do work w/ feisty.

---

### Post by tgrisier on 2007-03-25
Well I installed e17 according to the tutorial but when I log out and move the mouse to "options" my screen goes crazy.  I can see well enough to log back in but the screen stays messed up.  The only way to get it back right is to shut down and restart.  I've run update manager and it says my system (6.10) is up to date.  

I must have missed something or not have something set right.  Any help would be appreciated.

---

### Post by martinw89 on 2007-03-25
> **bettlebrox said:**
> Anyone know if there are packages for feisty or will the edgy packages work in feisty? A little googling turns up this page:

[http://ubuntuos.wordpress.com/2007/03/12/howto-ubuntu-feisty-install-e17-enlightenment-desktop/](http://ubuntuos.wordpress.com/2007/03/12/howto-ubuntu-feisty-install-e17-enlightenment-desktop/)

So I''m hoping that the edgy packages do work w/ feisty.
Yup, there are packages available for Feisty.  Just use the following in your sources.list:
```
## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu feisty e17
deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
```

---

### Post by bettlebrox on 2007-03-26
Great, thanks.

---

### Post by feldsinc on 2007-03-31
First off, thanks for this great tutorial.  I followed it from step one to the last got it working great in Fiery.  

However, I've run into one small problem... I can't seem to find the infamous 'Bling' module.  If I understand this correctly, it is this module that causes transparency in e17.  I can't seem to figure out why I am not getting any transparency effects on my desktop and I think the missing Bling module may be the cause.  Where might I find this module or if it is not needed, how do I get to the transparency settings?

I am running on:
Dell Inspiron 6000
X300 ATI Dedicated graphics

Thanks in advance.

---

### Post by Lut!n on 2007-04-22
As bling is not stable, I've decided not to put it in the repos. You can compile it though, it's not very hard. All you need is grapd the source from cvs (cvs -qz3 -d:pserver:@anoncvs.enlightenment.org:/var/cvs/e co e_modules/bling) and install enlightenment-dev and any other -dev package required by the configure, run ./autogen.sh, make, make install and you're done

Cheers

ps:be aware that it is _software_ compositing, thus it might heavily slow down your computer

---

### Post by lognok on 2007-04-24
Very nice and fast how-to.
Got it running in Feisty and it looks sooooo goooood. Nice and fast.
Now all I need to do is get accustomed to the enviroment and see if I can live without a system tray (where Gaim, Skype and Network Manager usually resides).

---

### Post by nlogax on 2007-04-28
You can always use 'trayer' for a very basic system tray.

Or run E17's Engage which is a combined launcher, tasklist & system tray (kinda like Apple's Dock) -- however the module version apparently isn't stable yet and I've never quite got the standalone version working well.

---

### Post by worldwithoutgurus on 2007-04-28
Engage is *no longer* maintained.

Use Itask instead. Please refer to this threadt:
[http://ubuntuforums.org/showthread.php?t=415283&highlight=e17](http://ubuntuforums.org/showthread.php?t=415283&highlight=e17)

---

### Post by Dax0r on 2007-04-28
I Can select Miky as gtk theme?

this is my .gtkrc2

gtk-theme-name = "MorningGlory"
gtk-icon-theme-name = "Edge"
#-gtk-font-name = "Bitstream Vera Sans 7"
#-gtk-icon-sizes = "gtk-menu=32,32:gtk-button=32,32"
#gtk-cursor-theme-name = "e"
#-gtk-cursor-theme-size = 48


[/QUOTE]
Any idea??

---

### Post by Lut!n on 2007-04-28
No, you can't, as e17 themes are usable only with e17, as metacity themes are only useable with metacity, etc...
You can browse gnome-look.org though, there's a bunch of gtk2 miky-ish themes there.
Cheers

---

### Post by Xummoner on 2007-05-01
I've been trying to install Elightenment for ages (look for previous posts) with no luck. Right now I'm running Feisty Fawn and I get this errors:

```
david@David-Desktop:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Get: 4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates Release.gpg [191B]          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Get: 5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports Release.gpg [191B]        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/restricted Translation-en_US 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/universe Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/universe Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/main Packages                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/restricted Packages          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/multiverse Packages          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/universe Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/main Sources                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/restricted Sources           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/multiverse Sources           
Get: 8 [http://edevelop.org](http://edevelop.org) feisty Release.gpg [189B]                           
Ign [http://edevelop.org](http://edevelop.org) feisty/e17 Translation-en_US                           
Hit [http://edevelop.org](http://edevelop.org) feisty Release                                         
Get: 9 [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty Release.gpg [189B]
Hit [http://edevelop.org](http://edevelop.org) feisty/e17 Packages    
Ign [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 Translation-en_US
Hit [http://edevelop.org](http://edevelop.org) feisty/e17 Sources
Get: 10 [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty Release [6196B]
Get: 11 [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 Packages [24.8kB]                  
Get: 12 [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 Sources [4049B]                    
Fetched 35.2kB in 13s (2692B/s)                                                
Reading package lists... Done
david@David-Desktop:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
e17 is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  emodule0-language: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
  enlightenment: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-con (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-config (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-dbus (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-evas (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-fb (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-file (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-ipc (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-job (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-txt (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-x (>= 0.9.9.037) but it is not going to be installed
                 Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libecore1-bin: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-config (>= 0.9.9.037) but it is not going to be installed
  libedje0: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-evas (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-fb (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-job (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-txt (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-x (>= 0.9.9.037) but it is not going to be installed
            Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libedje0-bin: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
                Depends: libecore1-evas (>= 0.9.9.037) but it is not going to be installed
                Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libefreet1: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
              Depends: libecore1-file (>= 0.9.9.037) but it is not going to be installed
  libevas1-engine-buffer: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-engine-software-generic: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-engine-software-x11: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-eet: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-gif: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-jpeg: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-png: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-svg: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-tiff: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-xpm: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-saver-eet: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-saver-jpeg: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-saver-png: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libexml1: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
david@David-Desktop:~$ sudo gedit /etc/apt/preferences
david@David-Desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
david@David-Desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-evas
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt
  libecore1-x libevas1
Suggested packages:
  libevas1-all
The following NEW packages will be installed
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-evas
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt
  libecore1-x libevas1
0 upgraded, 12 newly installed, 0 to remove and 4 not upgraded.
52 not fully installed or removed.
Need to get 0B/460kB of archives.
After unpacking 1749kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163882 files and directories currently installed.)
Unpacking libecore1 (from .../libecore1_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore.so.1.0.0', which is also in package libecore0
Unpacking libecore1-con (from .../libecore1-con_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-con_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_con.so.1.0.0', which is also in package libecore0
Unpacking libecore1-ipc (from .../libecore1-ipc_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-ipc_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_ipc.so.1.0.0', which is also in package libecore0
Unpacking libevas1 (from .../libevas1_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libevas1_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libevas.so.1.0.0', which is also in package libevas0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libecore1-config (from .../libecore1-config_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-config_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_config.so.1.0.0', which is also in package libecore0
Unpacking libecore1-dbus (from .../libecore1-dbus_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-dbus_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_dbus.so.1.0.0', which is also in package libecore0
Unpacking libecore1-fb (from .../libecore1-fb_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-fb_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_fb.so.1.0.0', which is also in package libecore0
Unpacking libecore1-txt (from .../libecore1-txt_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-txt_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_txt.so.1.0.0', which is also in package libecore0
Unpacking libecore1-x (from .../libecore1-x_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-x_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_x.so.1.0.0', which is also in package libecore0
Unpacking libecore1-evas (from .../libecore1-evas_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-evas_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_evas.so.1.0.0', which is also in package libecore0
Unpacking libecore1-file (from .../libecore1-file_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-file_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_file.so.1.0.0', which is also in package libecore0
Unpacking libecore1-job (from .../libecore1-job_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-job_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_job.so.1.0.0', which is also in package libecore0
Errors were encountered while processing:
 /var/cache/apt/archives/libecore1_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-con_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-ipc_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libevas1_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-config_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-dbus_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-fb_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-txt_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-x_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-evas_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-file_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-job_0.9.9.037+cvs20070428-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Now the update manager, says my package index is broken.

---

### Post by jharbert on 2007-05-01
Thanks for the howto, it worked great.  I'm having an issue with the fonts.  The basic system font sizes are fine, but the font size in most of my applications is really big.  See the picture to see what I'm talking about.  Any ideas on how to make them smaller.

---

### Post by Lut!n on 2007-05-02
> **Xummoner said:**
> I've been trying to install Elightenment for ages (look for previous posts) with no luck. Right now I'm running Feisty Fawn and I get this errors:

```
david@David-Desktop:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Get: 4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates Release.gpg [191B]          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Get: 5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports Release.gpg [191B]        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/restricted Translation-en_US 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/universe Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/universe Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/main Packages                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/restricted Packages          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/multiverse Packages          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/universe Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/main Sources                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/restricted Sources           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports/multiverse Sources           
Get: 8 [http://edevelop.org](http://edevelop.org) feisty Release.gpg [189B]                           
Ign [http://edevelop.org](http://edevelop.org) feisty/e17 Translation-en_US                           
Hit [http://edevelop.org](http://edevelop.org) feisty Release                                         
Get: 9 [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty Release.gpg [189B]
Hit [http://edevelop.org](http://edevelop.org) feisty/e17 Packages    
Ign [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 Translation-en_US
Hit [http://edevelop.org](http://edevelop.org) feisty/e17 Sources
Get: 10 [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty Release [6196B]
Get: 11 [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 Packages [24.8kB]                  
Get: 12 [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 Sources [4049B]                    
Fetched 35.2kB in 13s (2692B/s)                                                
Reading package lists... Done
david@David-Desktop:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
e17 is already the newest version.
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  emodule0-language: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
  enlightenment: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-con (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-config (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-dbus (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-evas (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-fb (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-file (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-ipc (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-job (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-txt (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-x (>= 0.9.9.037) but it is not going to be installed
                 Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libecore1-bin: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
                 Depends: libecore1-config (>= 0.9.9.037) but it is not going to be installed
  libedje0: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-evas (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-fb (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-job (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-txt (>= 0.9.9.037) but it is not going to be installed
            Depends: libecore1-x (>= 0.9.9.037) but it is not going to be installed
            Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libedje0-bin: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
                Depends: libecore1-evas (>= 0.9.9.037) but it is not going to be installed
                Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libefreet1: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
              Depends: libecore1-file (>= 0.9.9.037) but it is not going to be installed
  libevas1-engine-buffer: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-engine-software-generic: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-engine-software-x11: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-eet: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-gif: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-jpeg: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-png: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-svg: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-tiff: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-loader-xpm: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-saver-eet: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-saver-jpeg: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libevas1-saver-png: Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  libexml1: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).
david@David-Desktop:~$ sudo gedit /etc/apt/preferences
david@David-Desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
david@David-Desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-evas
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt
  libecore1-x libevas1
Suggested packages:
  libevas1-all
The following NEW packages will be installed
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-evas
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt
  libecore1-x libevas1
0 upgraded, 12 newly installed, 0 to remove and 4 not upgraded.
52 not fully installed or removed.
Need to get 0B/460kB of archives.
After unpacking 1749kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163882 files and directories currently installed.)
Unpacking libecore1 (from .../libecore1_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore.so.1.0.0', which is also in package libecore0
Unpacking libecore1-con (from .../libecore1-con_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-con_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_con.so.1.0.0', which is also in package libecore0
Unpacking libecore1-ipc (from .../libecore1-ipc_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-ipc_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_ipc.so.1.0.0', which is also in package libecore0
Unpacking libevas1 (from .../libevas1_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libevas1_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libevas.so.1.0.0', which is also in package libevas0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libecore1-config (from .../libecore1-config_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-config_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_config.so.1.0.0', which is also in package libecore0
Unpacking libecore1-dbus (from .../libecore1-dbus_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-dbus_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_dbus.so.1.0.0', which is also in package libecore0
Unpacking libecore1-fb (from .../libecore1-fb_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-fb_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_fb.so.1.0.0', which is also in package libecore0
Unpacking libecore1-txt (from .../libecore1-txt_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-txt_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_txt.so.1.0.0', which is also in package libecore0
Unpacking libecore1-x (from .../libecore1-x_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-x_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_x.so.1.0.0', which is also in package libecore0
Unpacking libecore1-evas (from .../libecore1-evas_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-evas_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_evas.so.1.0.0', which is also in package libecore0
Unpacking libecore1-file (from .../libecore1-file_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-file_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_file.so.1.0.0', which is also in package libecore0
Unpacking libecore1-job (from .../libecore1-job_0.9.9.037+cvs20070428-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore1-job_0.9.9.037+cvs20070428-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore_job.so.1.0.0', which is also in package libecore0
Errors were encountered while processing:
 /var/cache/apt/archives/libecore1_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-con_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-ipc_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libevas1_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-config_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-dbus_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-fb_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-txt_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-x_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-evas_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-file_0.9.9.037+cvs20070428-1_i386.deb
 /var/cache/apt/archives/libecore1-job_0.9.9.037+cvs20070428-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Now the update manager, says my package index is broken.

Hey,
I don't know what repo you are upgrading from but for sure, given the package names, it's odlly outdated or at least 100% incompatible with this repo. You won't be able to install this way. I suggest you to remove your enlightenment packages (ie, those ones who are conflicting) and to reinstall
Cheers


@jharbert : if you're talking about the GTK font size / theme, this post could be interesting ; [http://ubuntuforums.org/showpost.php?p=2231464&postcount=144]("http://ubuntuforums.org/showpost.php?p=2231464&postcount=144")

---

### Post by Xummoner on 2007-05-02
Thanks for the reply Lut!n, I was able to install it using a compiling guide I found in here and with a lot of help on IRC, there are still a couple of things I have to figure out (using themes available as .tar and such), but I'll leave that for later.

---

### Post by jharbert on 2007-05-02
Thanks Lut!n.  Worked great.

---

### Post by trmiv on 2007-05-02
So I installed E17 on 7.04 last night, and it went OK.  I was able to use E17 and everything was good.  Then I tried to use a different theme, and it got messed up.  I selected the Milky theme, and now suddenly I can't click on any of the buttons on the launcher bar, nothing works.  I was able to get back into the theme menu by clicking on the desktop, but when the list of themes comes up I can't actually click on any of them.  Any idea what's going on?  And how can I get it set back to the default theme so I can use it?

---

### Post by clyde9999 on 2007-05-03
Like someone said earlier. There is not System Tray. You cannot see programs like Messenger running in the background, Amarok, and any program that runs in the background. with most programs, like amarok, this is not a problem, you can just click to start it and it will open the existing program, but with programs like skype, you cannot do this. it will open a new skype and the old one will be still running in the background. A System Tray is needed, and TRAYER is not good enough, it is just ugly and a large step backwards.......

Clyde

---

### Post by Lut!n on 2007-05-03
> **trmiv said:**
> So I installed E17 on 7.04 last night, and it went OK.  I was able to use E17 and everything was good.  Then I tried to use a different theme, and it got messed up.  I selected the Milky theme, and now suddenly I can't click on any of the buttons on the launcher bar, nothing works.  I was able to get back into the theme menu by clicking on the desktop, but when the list of themes comes up I can't actually click on any of them.  Any idea what's going on?  And how can I get it set back to the default theme so I can use it?

You can see on get-e.org that milky is ou of date. it's only provided not to completely break E for the users using it at the moment of the upgrade.
One thing you can do to go back to the default theme so you can select an other is to press 'alt + esc', then open xterm (just type 'xterm' in the prompt), and use the following command : 'enlightenment_remote -theme-set theme default.edj . Then restart E (click -> enlightenment -> restart) and you're done.
Cheers

PS: the other easy way is rm -R ~/.e/e/config , though you'll have to reconfigure E from scratch. You should try this onmy is you're experiencing issues with E

---

### Post by ju^ju on 2007-05-04
Hi all!

Are the e17 repos currently down? I followed the how-to and have the packages listet in synaptic, but when I try to install e17 I get lots of 404 errors...

---

### Post by Sp4rKy on 2007-05-04
hmm ,

strange, it should work.

can you paste the error log please ?

Thx

---

### Post by kvonb on 2007-05-04
Tried it using the supplied Feisty repos on the first page, and this is the result:

```
Need to get 25.5MB of archives. After unpacking 37.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err http://edevelop.org feisty/e17 libecore1 0.9.9.037+cvs20070428-1
  404 Not Found
Err http://edevelop.org feisty/e17 libecore1-con 0.9.9.037+cvs20070428-1
  404 Not Found
Err http://edevelop.org feisty/e17 libecore1-ipc 0.9.9.037+cvs20070428-1
  404 Not Found
Err http://edevelop.org feisty/e17 libeet0 0.9.10.037+cvs20070428-1
  404 Not Found
Err http://edevelop.org feisty/e17 libevas1 0.9.9.037+cvs20070428-1
  404 Not Found
Err http://edevelop.org feisty/e17 libecore1-config 0.9.9.037+cvs20070428-1
  404 Not Found

```

....and so on for another few pages.

Yes I followed the instructions to the letter, and of course I did the update frst :).

---

### Post by kvonb on 2007-05-04
Ah, just saw this on edevelop.org:


                                     
                          
                          
                                               **Welcome to edevelop.org**

                                   
                                                                                                         **[Unexpected outage.]("http://edevelop.org/node/3008")**

        Submitted by [shadoi]("http://edevelop.org/user/1") on Wed, 2007-01-31 05:45.
      Very sorry about the surprise downtime folks, the hosting I had worked out for the server got yanked out from under me with no warning. The server has been installed in a new datacenter. All the sites hosted here should be coming back up. 
 In related news I'm planning to purchase a second server that can serve as a mirror and allow some nice things like load-balanced mirrors for the debian package repository.

---

### Post by ju^ju on 2007-05-04
Yes, but: Submitted by shadoi on Wed, 2007-01-31 (!)

---

### Post by BarneyRubble on 2007-05-05
I'm having difficulty downloading/installing e17 from the e17.dunnewind.net/ubuntu feisty repo. I seem to be connecting correctly, because aptitude can retrieve the package names and I can browse the directories on the server, but running aptitude install just generates a whole load of 404 errors?

Checking the output from aptitude against the filenames in the repo, I noticed that there were slight differences, e.g. aptitude tries to download 
libecore1 0.9.9.037+cvs20070**428**-1, but it's libecore1_0.9.9.037+cvs20070**317**-1_i386.deb in the repository.

Output from aptitude is below. **Any** suggestions gratefully received :) 

xxxxx@Linux-desktop:~$ sudo aptitude install e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-forecasts emodule0-language emodule0-mail emodule0-mem 
  <snip>

The following NEW packages will be installed:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-forecasts emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
<snip>

0 packages upgraded, 66 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.5MB of archives. After unpacking 37.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 libecore1 0.9.9.037+cvs20070428-1
  404 Not Found [IP: 193.34.16.167 80]
Err [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 libecore1-con 0.9.9.037+cvs20070428-1
  404 Not Found [IP: 193.34.16.167 80]
Err [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 libecore1-ipc 0.9.9.037+cvs20070428-1
  404 Not Found [IP: 193.34.16.167 80]
Err [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 libeet0 0.9.10.037+cvs20070428-1
  404 Not Found [IP: 193.34.16.167 80]

...and so on for all packages.

---

### Post by foxy123 on 2007-05-05
does anyone know why they do not package emphasis? I cannot find it in the Elbuntu repos...

---

### Post by ju^ju on 2007-05-05
Seems noone really knows why. Two days ago I was able to download all the packages on another system.
Strange...

---

### Post by skroll on 2007-05-05
@BarneyRubble

It seems like they planned on updating the repository but never put the files.  I'm getting the same thing, the db for the files is updated for the 04/28 binaries, but they do not exist on the site.

Hopefully it gets fixed.

---

### Post by BarneyRubble on 2007-05-05
Thanks for the replies Skroll and Ju^Ju

Eventually, I tried installing using the edgy repo at the same address (just substituted edgy for feisty in the relevant /etc/apt/sources.list lines), and that (mostly) worked - some themes and emodules missing, installed later. It wasn't pretty, though :) 

And I don't think they're the latest packages because the Gnome Update manager says it knows about 60 updates to e17, but can't access them. Sigh.

I'm back to Gnome and Beryl for now. Although Enlightenment's definitely worth a look, I'm not sure it's for me.

Anyway, thanks again for the replies - good luck!

---

### Post by skroll on 2007-05-05
> **BarneyRubble said:**
> Thanks for the replies Skroll and Ju^Ju

Eventually, I tried installing using the edgy repo at the same address (just substituted edgy for feisty in the relevant /etc/apt/sources.list lines), and that (mostly) worked - some themes and emodules missing, installed later. It wasn't pretty, though :) 

And I don't think they're the latest packages because the Gnome Update manager says it knows about 60 updates to e17, but can't access them. Sigh.

I'm back to Gnome and Beryl for now. Although Enlightenment's definitely worth a look, I'm not sure it's for me.

Anyway, thanks again for the replies - good luck!

I'll throw an email at one of the maintainers for the repo and see what's up.  It seems that there is a newer version of the cvs that has been compiled for the repos, but hasn't been uploaded yet.  Using the feisty repository should result in less broken packages as well.

---

### Post by 1975H2C on 2007-05-05
I used "deb [http://edevelop.org/~lut1n/ubuntu](http://edevelop.org/~lut1n/ubuntu) feisty e17" and it installed  .

And it seems to be working fine with the "Darkness Theme" , flames , rain and  snow  work.

But I do have a problem with "Milky Theme" ......... so I'm also going back to Gnome until this gets fixed.

---

### Post by skroll on 2007-05-05
> **1975H2C said:**
> I used "deb [http://edevelop.org/~lut1n/ubuntu](http://edevelop.org/~lut1n/ubuntu) feisty e17" and it installed  .

And it seems to be working fine with the "Darkness Theme" , flames , rain and  snow  work.

But I do have a problem with "Milky Theme" ......... so I'm also going back to Gnome until this gets fixed.

It must've just been fixed, since I tried it a few hours ago and wasn't working.  Thanks!

---

### Post by Lut!n on 2007-05-06
Thanks for your reports, this is fixed
About miky : with the last version of e17, a bunch of themes have been broken, and milky is one of them. Milky is being worked on, but you might have a look at get-e.org to find another theme until this is fixed ;) (some are really good)
Cheers

---

### Post by JMO707 on 2007-05-06
Fantastic. I was using Beryl in Gnome, but what the hell..., e17 is beautiful and uses almost the half of resources =)

Just one question: anyway to get Entropy around here?

I couldnt find any .deb and dont like the way gtk apps look on e17.

---

### Post by litemotiv on 2007-05-07
i tried e17 for the first time last night, and even with the current theme-breakage i have to admit i was pleasantly surprised. ;) it's very fast and responsive, and seems to be really focused on usability and adaptability. i will surely be checking for updates now and then to see where it's going.

one small question i might as well ask here right away: does anyone know how to make the filemanager open new directories in the same window? i'm not really digging the extra windows per click. ;)

---

### Post by b9anders on 2007-05-07
I just installed enlightenment now and I have a couple of questions:

Is there a way I can make the windows in the ibox, ibar and pager transparent the same way they are in elive?

How can I set the pager to change desktops simply by scrolling the mousewheel over the desktop?

**All the entries in the System menu folder in GNOME have gone missing in enlightenment - there's no GUI way for me to access synaptic, network settings etc. Help!**

Is there a way for me to edit the menus to add applications not recognised and added to the menu automatically?

I downloaded eterm through synaptic but it wasn't added to the menu now have I been able to start it through the terminal. How do I run it?

How do I change the GTK theme?

---

### Post by JMO707 on 2007-05-07
> **b9anders said:**
> 
I downloaded eterm through synaptic but it wasn't added to the menu now have I been able to start it through the terminal. How do I run it?


Haha, I just know this one because I couldnt at firsth neither ;)

Is "Eterm" the command, no "eterm"

---

### Post by hornett on 2007-05-07
Anybody else have problems getting VLC to stop full screen? On my pc it leaves the screen blank and unresponsive :(

 But i can switch to another desktop with the keys and run a terminal, so its not all bad :)

---

### Post by kvonb on 2007-05-08
Excellent, all installed and working.

It's extremely fast compared to gnome, and I really like the menus.

Anyone know how to create a custom menu item?  I want to create a launcher for Nautilus but can't seem to find how to do it!

---

### Post by b9anders on 2007-05-08
> **kvonb said:**
> Excellent, all installed and working.

It's extremely fast compared to gnome, and I really like the menus.

Anyone know how to create a custom menu item?  I want to create a launcher for Nautilus but can't seem to find how to do it!

My not so elegant workaround was to simply add some utility to the ibar, then rightclick it and change the launcher properties to the program I wanted that I couldn't find.

If you're liking the speed, try and install the PCMan file manager. Incredibly fast.

Would like to try entropy but it doesn't seem to be made for Ubuntu yet and I am not keen on compiling myself.

> **JMO707 said:**
> Haha, I just know this one because I couldnt at firsth neither ;)

Is "Eterm" the command, no "eterm"

Cheers for that. I worked out how to change the gtk theme as well. And that transparency thing seems to be there just not working properly.

I wanted to try a new theme, accidentally chose the milky one and it seems to be of the buggy kind that I can't select anything in enlightenment windows. That means I can't select a new theme to replace it.:( 

Any idea how I can change this another way?

---

### Post by kvonb on 2007-05-08
> **b9anders said:**
> My not so elegant workaround was to simply add some utility to the ibar, then rightclick it and change the launcher properties to the program I wanted that I couldn't find.

excellent idea, 10 out of 10 for ingenuity :)

---

### Post by Lut!n on 2007-05-08
> **b9anders said:**
> My not so elegant workaround was to simply add some utility to the ibar, then rightclick it and change the launcher properties to the program I wanted that I couldn't find.

If you're liking the speed, try and install the PCMan file manager. Incredibly fast.

Would like to try entropy but it doesn't seem to be made for Ubuntu yet and I am not keen on compiling myself.



Cheers for that. I worked out how to change the gtk theme as well. And that transparency thing seems to be there just not working properly.

I wanted to try a new theme, accidentally chose the milky one and it seems to be of the buggy kind that I can't select anything in enlightenment windows. That means I can't select a new theme to replace it.:( 

Any idea how I can change this another way?

[http://ubuntuforums.org/showpost.php?p=2586743&postcount=197](http://ubuntuforums.org/showpost.php?p=2586743&postcount=197)

---

### Post by b9anders on 2007-05-09
> **Lut!n said:**
> [http://ubuntuforums.org/showpost.php?p=2586743&postcount=197](http://ubuntuforums.org/showpost.php?p=2586743&postcount=197)

Thanks for that. I did look through the thread for an answer, but I must have missed that one.

---

### Post by n00b@linux on 2007-05-11
I just upgraded to Feisty from Edgy.
I have a VIA UniChrome Pro GPU so I can't use Beryl or Compiz - E17 is my only chance at some desktop 'bling'.
I followed the instructions per tcrroadie's very first post and it worked without a hitch.  Thanks to all the Elbuntu devs and to the Enlightenment devs as well!
Another satisfied (and thankful!) Ubuntu + E17 user.

I like to give back what I can (even though it's not much) so I thought I'd post _[this link]("http://bsdtalk.blogspot.com/2006_05_01_archive.html")_ to an interview with Rasterman (from the Enlightenment project).   Although the interview is 12 months old, it's nonetheless interesting, particularly for its views on E17 and OpenGL.

---

### Post by nlogax on 2007-05-12
> **b9anders said:**
> My not so elegant workaround was to simply add some utility to the ibar, then rightclick it and change the launcher properties to the program I wanted that I couldn't find.

Another way is to press ALT+ESC to bring up the run dialog, then type part of the name of the progam and select it from the list that is displayed.

Once it's running, there's a 'Create icon' option if you click on the box at the top left of the window.

Once you have an icon you should be able to add it to your favourites by clicking the box at the top left.

---

### Post by Ledah on 2007-05-25
The installation diesn't work for me :(
I added the repositories for Feisty and updated the sources list, but apt-get gives me an error. e17 deponds on enlightenment (>= 0.16.999), but it should not be installed. The same for emodules0-all (>= 0.16.999). It also depends on libevas1-loaders-all, but this package is not installable.
The /etc/apt/preferences is emty.

---

### Post by Ledah on 2007-05-26
It seems that all 64bit packages of the libevas-libraries are missing.

*Edit:* The problem is solved. I sent a mail and the missing packages are available now.

---

### Post by adamJ5 on 2007-05-26
Isn't there a notification area or systray or something ine E17?

---

### Post by Ledah on 2007-05-26
I was also looking for it, but I didn't find one :-k

[QUOTE=http://www4.get-e.org/Main/FAQs/#57]Does E17 have systray support ?
No, there will be no tray icon support in E17 until the systray icon standard is changed. 
Carsten 'Rasterman' Haitzler wrote: 

"The Systray specification that somehow users seem to ask for and applications seem to use that is specified here primarily, is not as nice as you may think. It is in fact rather ugly and limited. It leads to awful interfaces and inconsistent behavior and display." 

For the full text of this article, along with a screenshot, please see Rasterman.com. 

Most people end up using trayer or engage.[/QUOTE]

---

### Post by foxy123 on 2007-05-27
> **Ledah said:**
> I was also looking for it, but I didn't find one :-k
it is Rasterman's belief that > The Systray specification... is in fact rather ugly and limited. and as he stated on e17 mail list > there is, and will be, no system tray support in e17. use something else like trayer.

you can also try stalonetray:[http://stalonetray.sourceforge.net](http://stalonetray.sourceforge.net) or even itask NG, which is an unofficial e17 module devised to replace engage. Engage itself is dead.

---

### Post by sonicborg on 2007-06-03
would like to get iTask NG but dont seem to be able to find a download for it ?

really need a nice friendly menu editor too :)

---

### Post by sonicborg on 2007-06-03
i noticed that alot of people have really nice Icon launchers along one side, or bottom of their screens (bit like the one on apples) how are you getting this? because if i add a 2nd shelf, make it transparent, with the ibar gadget in it, i can not add custom applications, i am only limited to the select few that enlightenment has automaticly found. everying in my own personal apps menu etc i can not select.

---

### Post by SAMW on 2007-06-04
Ummmm I'm pretty sure I haven't messed anything up, but I keep getting e16 instead of 17....

I used this repo:

## E17 repository "edevelop.org"
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

---

### Post by tcrroadie on 2007-06-04
First remove e16.
```

sudo aptitude purge enlightenment
```

Then could you please post your screen output when you try to install E17?
```

sudo aptitude install e17
```

Thanks.

---

### Post by Hatchetfish on 2007-06-06
So here's an odd one.  According to apt the install went wonderfully, and the sessions are there in the menu, but logging in with E17 tells me /opt/e17/bin/enlightenment can't be found.  Which makes sense.  It isn't there.  I searched and found post 401, saying it's changed to /opt/e17/bin/enlightenment-start. (or _start, can't remember)  Fine, but that's not there either.  In fact, here's ls in /opt/e17/bin.  note the lack of enlightement-anything-whatsoever:  

```
ls /opt/e17/bin/
compare_results    embryo_cc                etk_test
ecore_alloc        embryo-config            evas-config
ecore_config       emotion-config           ewl_config
ecore-config       emotion_test             ewl-config
edb-config         engrave_canvas_test      ewl_embed_test
edb_ed             engrave-config           ewl_simple_test
edb_gtk_ed         engrave_test             ewl_test
edb_vt_ed          epeg                     imlib2_bumpmap
edje_cc            epeg-config              imlib2_colorspace
edje-config        epsilon                  imlib2-config
edje_decc          epsilon-config           imlib2_conv
edje_recc          epsilon_thumbd           imlib2_grab
efreet_alloc       epsilon_thumb_test       imlib2_poly
efreet_cache_test  esmart-config            imlib2_show
efreet-config      esmart_file_dialog_test  imlib2_test
efreet_menu_alloc  esmart_test              imlib2_view
efreet_spec_test   etk-config
efreet_test        etk_prefs
```

so, question is, where has it gone/what's it called now?  Since everything seems to have installed fine, I'm inclined to think it's been moved again and the session file not updated with it.

---

### Post by quazi on 2007-06-12
> **jharbert said:**
> Thanks for the howto, it worked great.  I'm having an issue with the fonts.  The basic system font sizes are fine, but the font size in most of my applications is really big.  See the picture to see what I'm talking about.  Any ideas on how to make them smaller.

I'm having the same issue, but this doesn't seem to be resolving it.  To clarify, I should make a file (Installed with Kubuntu, so there's no gtkrc file there initially) ,gtkrc-2.0 and include the following lines:

```

gtk-font-name = "Bitstream Vera Sans 7"
gtk-theme-name = "Gant" 
gtk-icon-theme-name = "Gant"

```
where Gant is the theme I'm using?

Since I don't have the Gnome desktop installed is there another way I should be trying to solve this?  

EDIT: Well after I restarted X I've managed to fix gtk programs, but Firefox is still hideous.
EDIT: And reinstalling firefox fixed that.

---

### Post by hybernate20 on 2007-06-27
E: Failed to fetch [http://e17.dunnewind.net/ubuntu/pool/feisty/e17/i386/enlightenment-data_0.16.999.038+cvs20070606-1_all.deb:](http://e17.dunnewind.net/ubuntu/pool/feisty/e17/i386/enlightenment-data_0.16.999.038+cvs20070606-1_all.deb:) MD5Sum mismatch


I get that every time with both repos

---

### Post by airtonix on 2007-07-09
Feisty install went well.

still a few crashes though.

---

### Post by Sp4rKy on 2007-07-09
> **hybernate20 said:**
> E: Failed to fetch [http://e17.dunnewind.net/ubuntu/pool/feisty/e17/i386/enlightenment-data_0.16.999.038+cvs20070606-1_all.deb:](http://e17.dunnewind.net/ubuntu/pool/feisty/e17/i386/enlightenment-data_0.16.999.038+cvs20070606-1_all.deb:) MD5Sum mismatch


I get that every time with both repos

really strange. You can get this kind of error during the update, but not every time ...
Do you update before ?

---

### Post by Brian96 on 2007-07-10
> **airtonix said:**
> Feisty install went well.

still a few crashes though.

I had quite a few the first few days I used it, but it seems to behave itself lately. And I haven't had any fatal crashes in quite a while.

---

### Post by Carbon Tiger on 2007-07-12
The install worked great its a very interesting GUI. I do have one question is there a way to make my desktop folders invisible ? I don't want to move them just make it so they don't list on the desktop.

---

### Post by worldwithoutgurus on 2007-07-12
Drag and drop them into the Files (favorites) window.

---

### Post by yosef on 2007-07-24
I installed e17 as per tutorial, loggedout. logged in. It was great!  Until I changed themes... then all menus were blank,rightclick menu, leftclick menu, centerclick mennu... even the taskbar/panel thingy had no icons on it whatsoever!  I really like e17 but I barely got to play with it! How can I fix it when I cant even open up a commandline or change themes or anything!  Please help!

---

### Post by Perfex on 2007-07-25
Hmm.

Seems like the latest version has problems displaying the thumbs of images..

none via file manager or change wall, etc

---

### Post by picpak on 2007-07-25
> **yosef said:**
> I installed e17 as per tutorial, loggedout. logged in. It was great!  Until I changed themes... then all menus were blank,rightclick menu, leftclick menu, centerclick mennu... even the taskbar/panel thingy had no icons on it whatsoever!  I really like e17 but I barely got to play with it! How can I fix it when I cant even open up a commandline or change themes or anything!  Please help!

Ugh, I'm having the same problem! It came from the latest updates. Any help?

---

### Post by yosef on 2007-07-26
I just aptitude purged and then installed anew... to no avail!

---

### Post by thexaspect on 2007-07-28
Yeah, same problem here. I changed themes just screwing around, and apparently the "Dark" theme doesnt change the text color from black to, well, anything readable, hence, I can't see anything. Relog and back into plain old gnome again woopie!

---

### Post by eode on 2007-07-28
..well, it looks like the 'bling' theme still works.  Maybe they changed how themes are handled, and most themes have yet to switch over.

---

### Post by Freddy on 2007-07-30
I suggest that you never use themes found at the repository or those installed with the e17 package, instead visit [get-e]("http://www.get-e.org"), they list those themes that currently work with Enlightenment.

/Freddan

---

### Post by Freddy on 2007-07-30
Hi all.
I have a couple of question and hopefully someone with some more knowledge sees them here.

What is the lib packages etk and ewl more exactly? I thought etk themes should theme those applications written for Enlightenment, but what do they do? How do I change the theme etk are currently using, I installed a etk theme named Detour but have found no way to select that theme.

/Freddan

---

### Post by TravMan63 on 2007-07-31
I tried this - and MANY things broke!

1) wireless 
2) mouse (touchpad and stick - laptop)
3) when I log in - this error (to gnome/enlightenment)
error creating the child process for this terminal 

4) can't connect via ssh (ssh server) <-- is all that is ok now
5) entrance STILL is just a grey screen with an X (that's all I needed 'fixed')
 ---- I had removed e17 then tried to reinstall it - there were packages that wouldnot install (enlightenment and enlightenment-data) - and then....

This isn't going to be fun....

--------------

---

### Post by sirtimbly on 2007-08-03
> **AgenT said:**
> but E17 has been in the works for a very long time now (at least two years).


Hah! More like 7 years.

---

### Post by hyperair on 2007-09-18
Hmm I'm just wondering if Engage is still available..? I tried installing it, but it depended on some libecore1-dbus package which I didn't have. Also, the sound doesn't work for me on Enlightenment (apps have sound, but system sounds missing), and the mixer applet doesn't control my volume. Also, I'm looking for a suitable system tray alternative and still haven't found one, as well as a method to turn on compositing in E17. =\ Someone please help.

---

### Post by yabbadabbadont on 2007-09-18
I believe that engage was abandoned a year or so ago...

No clue on the sound issue.  Sorry.

Which trays have you tried?  If you list them, then people won't suggest ones that you have already tried.  ;)

I'm fairly certain that the E devs poo-pooed the compositing idea, but it seems like I read about a "bling" module somewhere that adds it.  Check out the "E17 is coming" mega-threads on the Gentoo forums as they seem to stay fairly up to date on E17 happenings.

---

### Post by hyperair on 2007-09-18
The bling module's missing, at least for me. Also I've tried trayer, and stalonetray. Sticking with stalonetray for the moment.

---

