---
title: "HowTo : Install Pidgin 2.0.0 on Ubuntu Feisty (with all plugins)"
date: 2007-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by kalpik on 2007-05-12
You can get the vanilla Pidgin 2.0 .deb (installation file for Ubuntu Feisty) here.

The only thing i was missing badly were the plugins! I was really used to the libnotify and autoreply plugins. Anyway, so i&#8217;ve compiled a .deb here for ALL plugins imaginable for Pidgin 2.0.0.

Plugins in the Plugin Pack

   1. Album
   2. Auto Accept
   3. Auto-rejoin
   4. Auto Reply
   5. awaynotify
   6. Bash.org
   7. Buddy Icon Tools
   8. Buddy List Options
   9. Buddy Note
  10. buddytime
  11. chronic
  12. convcolors
  13. Dice
  14. DiffTopic
  15. Magic 8 Ball
  16. Flip
  17. gRIM
  18. Group Message
  19. Hide Conversation
  20. IRC Helper
  21. Irssi Features
  22. Last Seen
  23. List Handler
  24. Marker Line
  25. My Status Box
  26. napster
  27. New Line
  28. Nick Said
  29. Offline Message
  30. Old Logger
  31. Plonkers
  32. Schedule
  33. Separate and Tab
  34. Show Offline
  35. Sim Fix
  36. Slash Exec
  37. SSL Info
  38. Stocker
  39. Switch Spell
  40. Talk Filters
  41. XMMS Remote
  42. XChat-Chats

[Download Pidgin 2.0.0 here]("http://www.getdeb.net/app.php?name=Pidgin").
[Download Libnotify plugin here]("http://www.getdeb.net/app.php?name=pidgin-libnotify").
[Download Plugin Pack here]("http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/").

[COLOR="Red"]Edit:[/COLOR] Site back up, and now 64 bit debs for pidgin and the plugin pack available too!
[COLOR="Red"]Edit2:[/COLOR] Some people are shamelessly copying this article and posting it on their blogs/sites. They were even hot linking to my .deb files. So now i am using box.net to distribute the deb files. Please do let me know if anyone faces issues with that :)

---

### Post by ManasT on 2007-05-12
Thanks .

It works. :)

---

### Post by haricharan on 2007-05-12
thank you....this time it worked :D

---

### Post by finferflu on 2007-05-12
Very good! now I'm not missing anything! I just needed the plugins really, since Pidgin, libnotify and guifications were already on GetDeb... Thanks!

---

### Post by kalpik on 2007-05-13
My pleasure! :)

---

### Post by Eversmann on 2007-05-13
Awesome!!! Thanks for the work :-D

---

### Post by cborga1985 on 2007-05-13
[SIZE="3"]**[COLOR="Red"]If you are inpatient like me use mlind's repo [http://ubuntuforums.org/showpost.php?p=2649312&postcount=7](http://ubuntuforums.org/showpost.php?p=2649312&postcount=7) . He has backported the debs from Gutsy to Feisty and they work quite well.[/COLOR]**[/SIZE]

---

### Post by honeydew on 2007-05-13
Thanks works for me! =]

---

### Post by darthchaosofrspw on 2007-05-13
> **cborga1985 said:**
> Here is a fake gaim package to satisfy Ubuntu-Desktop dependencies. You do have to remove  nautilus-sendto but I never have found that to be of any use anyway. This is just a meta-package that tells apt gaim and nautilus-sendto is installed. Also, update notifier will not keep trying to update gaim because I changed the version number to 1:9.9.9 which is not a real version.

```
firefox http://ubuntuforums.org/attachment.php?attachmentid=32503&stc=1&d=1179077467
tar -zxf gaim_9.9.9_all.deb.tar.gz
sudo dpkg -P --force-all gaim gaim-data nautilus-sendto
sudo dpkg -i gaim_9.9.9_all.deb

```

Got Pidgin installed on here as well. It's working great.

---

### Post by cborga1985 on 2007-05-14
> **darthchaosofrspw said:**
> Got Pidgin installed on here as well. It's working great.

i made that so you can remove gaim

---

### Post by kalpik on 2007-05-14
I suggest people dont remove gaim as of yet. Cuz gaim is going to be replaced by pidgin in a couple of days.. Anyway, it doesnt harm keeping gaim anyway..

---

### Post by cborga1985 on 2007-05-14
> **kalpik said:**
> I suggest people dont remove gaim as of yet. Cuz gaim is going to be replaced by pidgin in a couple of days.. Anyway, it doesnt harm keeping gaim anyway..

well the package i made was just a simple way of doing it. it's easily reversible.
```
sudo dpkg -P --force-all gaim
sudo apt-get -f install
```

Also, has it been officially announced?

---

### Post by kalpik on 2007-05-14
Yes, i know that! But the average joe would face problems you know, and then he would not remember to check back on this thread :)
And yes, it was officially announced that pidgin would be included into feisty repos on the mailing lists..

---

### Post by cborga1985 on 2007-05-14
> **kalpik said:**
> Yes, i know that! But the average joe would face problems you know, and then he would not remember to check back on this thread :)
And yes, it was officially announced that pidgin would be included into feisty repos on the mailing lists..

Well, it's good to know that they are going to put pidgin in the Feisty repository but what about Edgy? I was under the impression that they were not going to update the repository until Gutsy.

---

### Post by kaede on 2007-05-14
nicely done :D thanks buddy.

---

### Post by kalpik on 2007-05-14
@cborga1985: No, they wont update the edgy repo :(

@kaede: My pleasure :)

---

### Post by Ghostlove on 2007-05-14
I installed this and it seems to be great - except it keeps randomly chucking me out of MSN, a problem I didn't have with GAIM. Any ideas?

---

### Post by kalpik on 2007-05-14
Umm.. Im not having any issues with MSN.. Maybe just a temporary problem?

---

### Post by Ghostlove on 2007-05-14
Very possible, it seems to be okay now. I kept GAIM installed as well just in case anyway. :)

---

### Post by cborga1985 on 2007-05-15
anybody else experience a crash when sending a message to yourself using the Oscar protocol (Aim)?

---

### Post by Ghostlove on 2007-05-16
It was obviously a network problem, not a problem with Pidgin as I'm staying logged in all the time now.

Now I have another problem though; not sure if everyone's Pidgin is like this or if it's just mine, but I appear to have no menu bar at the top? Where previously I had drop-down menus titled Buddies, Accounts, Tools, Help, now I don't have anything. Is it just me, or has that menu bar really been removed?!

---

### Post by kalpik on 2007-05-16
We all have menu bars here! Can you post a screenshot?

---

### Post by omegazepher on 2007-05-17
Hey,

I noticed this post too late, so I made my own little script that gets the source, compiles and installs it.

Script -> [pidgin-2.0.0.sh]("http://zephernet.dyndns.org/pidgin-2.0.0.sh")

```

cd to where the script is and hit: 

sudo sh ./pidgin-2.0.0.sh

```

It needs root for "apt-getting build-essential" and the "make install"
It could be missing some dependencies, let me know and i`ll put them in.

So if anybody wants to make from source...
Oh, if you find any flaws, or know ways to better it, feedback is very welcome.
My first script, you see :)

Kind greets,

Zepher

#zepher @ irc.azzurra.org

---

### Post by Ghostlove on 2007-05-17
> **kalpik said:**
> We all have menu bars here! Can you post a screenshot?

Um... no I can't, because I've already uninstalled it. :( It looks just like everyone else's screenshots, just with no menu bar. :P

---

### Post by nightwalker on 2007-05-19
> **Ghostlove said:**
> It was obviously a network problem, not a problem with Pidgin as I'm staying logged in all the time now.

Now I have another problem though; not sure if everyone's Pidgin is like this or if it's just mine, but I appear to have no menu bar at the top? Where previously I had drop-down menus titled Buddies, Accounts, Tools, Help, now I don't have anything. Is it just me, or has that menu bar really been removed?!

You probably have enabled the "Buddy list options" plugin. Try disabling it ;-)

---

### Post by finferflu on 2007-05-21
> **nightwalker said:**
> You probably have enabled the "Buddy list options" plugin. Try disabling it ;-)
Thanks, it worked, I had the same problem.
What I did is, I unselected the option "*Hide menu in the buddy list window*" in the configuration options of the *Buddy List Options* plugin. 

Thanks! :)

---

### Post by ahawks on 2007-05-21
Ever since upgrading from gaim 2.0 to pidgin 2.0, I have no notification area icon for pidgin (in Windows it would be called the systray icon).  I have reinstalled Feisty (for other reasons), and the problem still persists.  My home directory has stayed the same though.

I have other things in my notification area, and I've removed and re-added the applet, but Pidgin still won't show up. 

Anybody else having this problem? Can anyone speak up and say that they DO have the icon with this package? That would at least let me know it's something in my environment.\

**UPDATE:**
I renamed .gaim and .purple (so they'd be out of the way) and re-ran pidgin.  The notification icon has returned! 
If anyone else has this problem, try that.  You can move your logs directory and stuff back in once it's fixed.

---

### Post by threespacemen on 2007-05-21
Looks like we've been a bit reckless with kalmik's bandwidth... ;)

For anyone who missed out on the plugin pack, it's available here, along with the pidgin deb:

[http://download.ubuntu.pl/_Feisty_Fawn/pidgin/](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/)

It's unfortunate that the pack doesn't contain the OTR plugin, however it is fairly easily compiled from source, and pretty much Just Works.

---

### Post by nerdman978 on 2007-05-21
thanks, works great!

---

### Post by DougieFresh4U on 2007-05-21
I am very glad for the .deb, however when I went to install it wanted me to get rid of gaim as there were dependency from hell problem. So I removed (a mistake??) gaim and also gaim data and ubuntu desktop went out as well. Now how do I put ubuntu desktop back as I have tried doing so in synaptic and it has dependency from hell drama again. So I am kind of  :confused:  here? Thanks for any help any one can provide

---

### Post by kalpik on 2007-05-22
> **threespacemen said:**
> Looks like we've been a bit reckless with **kalmik's** bandwidth... ;)

For anyone who missed out on the plugin pack, it's available here, along with the pidgin deb:

[http://download.ubuntu.pl/_Feisty_Fawn/pidgin/](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/)

It's unfortunate that the pack doesn't contain the OTR plugin, however it is fairly easily compiled from source, and pretty much Just Works.
Its Kalpik :) Hehe.. Actually googlebot ate up my bandwidth, not you people! Anyway, my admin has gone for a holiday to kashmir, so cant do anything about it till he returns :)

---

### Post by Dr. Nick on 2007-05-22
dont worry about ubuntu-desktop for now, if you install it, it will always try to install gaim until its updated to reflect the gaim-pidgin name change. Not having it installed shouldnt cause any problems now, just remember to install it before you update your system to the next release.

---

### Post by kalpik on 2007-05-22
> **DougieFresh4U said:**
> I am very glad for the .deb, however when I went to install it wanted me to get rid of gaim as there were dependency from hell problem. So I removed (a mistake??) gaim and also gaim data and ubuntu desktop went out as well. Now how do I put ubuntu desktop back as I have tried doing so in synaptic and it has dependency from hell drama again. So I am kind of  :confused:  here? Thanks for any help any one can provide
The debs provided here dont conflict with gaim! Just try sudo apt-get install ubuntu-desktop and then sudo apt-get dist-upgrade.

---

### Post by threespacemen on 2007-05-22
> **kalpik said:**
> Its Kalpik :) Hehe.. Actually googlebot ate up my bandwidth, not you people! Anyway, my admin has gone for a holiday to kashmir, so cant do anything about it till he returns :)

Oops, sorry mate! You know how close those M and P keys can be on your keyboard sometimes... ;)

I've had my own issues with googlebot chewing up extreme amounts of bandwidth lately (good excuse to brush up on my iptables skills...) so I can empathise with you!

As far as the OTR plugin for Pidgin goes, people can obtain the ported source from here:

[http://www.cyberdyne.org/~icebrkr/2007/05/04/unofficial-off-the-record-otr-port-to-pidgin-2-beta-7/](http://www.cyberdyne.org/~icebrkr/2007/05/04/unofficial-off-the-record-otr-port-to-pidgin-2-beta-7/)

It does say for the final beta, but it works fine on the 2.0 release proper (thanks to this post for the heads up - [http://ubuntuforums.org/showthread.php?t=437139](http://ubuntuforums.org/showthread.php?t=437139)). You'll need to apt-get a few libs for it to compile, such as libotr2 and libglib2. The ./configure errors are informative enough for the average user to figure out what's missing. Once you've done ./configure && make && make install, the two plugin files install to /usr/local/lib/pidgin - just copy them both to /usr/lib/pidgin and OTR should show up in your plugin list.

Looks as though some kind soul has made a .deb for the plugin, although I haven't tried it to confirm whether or not it works:

[http://gnome-look.org/content/show.php/Pidgin+2+DEB?content=57356](http://gnome-look.org/content/show.php/Pidgin+2+DEB?content=57356)

Probably not the right place to be asking this, but what are the chances of OTR becoming an official Pidgin plugin?

---

### Post by NotoriousTF on 2007-05-22
Anyone experience this error message when trying to connect to MSN?:
> 
Connection error from Notification server:
Reading error

Sometimes it connects, shows my buddy list with who is online and offline but after a few seconds it disconnects displaying the same above message.

---

### Post by kalpik on 2007-05-22
That's a problem with MSN's side.. Not the fault of pidgin :)

---

### Post by NotoriousTF on 2007-05-22
> **kalpik said:**
> That's a problem with MSN's side.. Not the fault of pidgin :)
I'm not sure, MSN on pidgin is working perfectly from my home connection but in college, even with the college proxy details I'm still having problems. A friend of mine is using it ok through the college network, I just can't get it to work.

EDIT: Ok now once I leave Pidgin running in online mode, it keeps connecting and disconnecting automatically. Sometimes is remains connected for a long-ish period (maybe 5 mins.), but eventually it disconnects.

---

### Post by ernstblaauw on 2007-05-23
I have Feisty 64-bit. Does anyone know if a plugin package exists for 64-bit?

---

### Post by kalpik on 2007-05-23
My site back up, and now i've put up the 64 bit deb for the plugin pack too :)

---

### Post by jdmcg on 2007-05-28
> **nightwalker said:**
> You probably have enabled the "Buddy list options" plugin. Try disabling it ;-)

Umm, how do I do that if I have no menu bar?

Edit:
NM found it in: /home/XXXXX/.purple/prefs.xml

---

### Post by threespacemen on 2007-05-28
> **jdmcg said:**
> Umm, how do I do that if I have no menu bar?

Do you have the Pidgin icon (green circle, white speech bubble) in your systray? If so, right-click it and select "plug-ins", then either un-tick the "Buddy List Options" plug-in, or click on that line and then click "Configure Plugin", and unselect "Hide the menu in the buddy list window".

If you don't have a systray icon, see the post a few back on renaming your .gaim and .purple folders, or try moving the blistops.la and blistops.so from out of the /usr/lib/pidgin directory. Haven't tried this, though, so YMMV...

---

### Post by colonels1020 on 2007-05-29
Awesome. Thanks. :)

---

### Post by z0mbi3 on 2007-05-30
Installed Pidgin no probs, but I don't have any sound. Has anyone got any ideas on this?

Also under adept I now have pidgin in the repository. I can uninstall it from there but I can't reinstall it. Is this because it's picked up that I installed it from deps, but that theres no actual online repository for it?

Thanks in advance.

---

### Post by navneeth on 2007-05-31
When will Pidgin make it to the Feisty repos?

---

### Post by kalpik on 2007-05-31
Only god knows! :P

---

### Post by navneeth on 2007-05-31
> **kalpik said:**
> Only god knows! :P

So do I contact RMS? :)

---

### Post by navneeth on 2007-05-31
Just one question...I don't have to remove GAIM, right?

---

### Post by kalpik on 2007-05-31
No.. And its actually better if you dont :)

---

### Post by navneeth on 2007-05-31
> **kalpik said:**
> No.. And its actually better if you dont :)
Okay, thanks. :)

---

### Post by navneeth on 2007-05-31
One more positive review! Glad to know that the Google Talk issue has been settled. Never was able to create an account in GAIM. 

Thanks, kalpik.

---

### Post by kalpik on 2007-05-31
My pleasure :)

---

### Post by sibot on 2007-06-02
Hey i downloaded pidgin from the provided link, however when i try to install it, it gives me an error....

Error: Dependancy is not satisfiable: libavahi-compat-howl0

can anyone help me out here?

---

### Post by schumifer on 2007-06-09
kubuntu edgy 64bit
Tried 2 different 64bit packages, and one 32bit with --force-architecture. And i always get this answer

dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.12.3-0ubuntu1.
 pidgin depends on libavahi-compat-howl0 (>= 0.6.0); however:
  Package libavahi-compat-howl0 is not installed.
 pidgin depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.4-1ubuntu12.3.
 pidgin depends on libcairo2 (>= 1.4.2); however:
  Version of libcairo2 on system is 1.2.4-1ubuntu2.
 pidgin depends on libdbus-1-3 (>= 0.94); however:
  Version of libdbus-1-3 on system is 0.93-0ubuntu3.1.
 pidgin depends on libdbus-glib-1-2 (>= 0.73); however:
  Version of libdbus-glib-1-2 on system is 0.71-1ubuntu1.
 pidgin depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-7ubuntu2.
 pidgin depends on libgadu3 (>= 1:1.7~rc2); however:
  Version of libgadu3 on system is 1:1.6+20060616-1.
 pidgin depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.12.4-0ubuntu1.
 pidgin depends on libgstreamer0.10-0 (>= 0.10.12); however:
  Version of libgstreamer0.10-0 on system is 0.10.10-1ubuntu2.
 pidgin depends on libgtkspell0 (>= 2.0.2); however:
  Package libgtkspell0 is not installed.
 pidgin depends on libnm-glib0; however:
  Package libnm-glib0 is not installed.
 pidgin depends on libpango1.0-0 (>= 1.16.2); however:
  Version of libpango1.0-0 on system is 1.14.5-0ubuntu1.
 pidgin depends on libpng12-0 (>= 1.2.13-4); however:
  Version of libpng12-0 on system is 1.2.8rel-5.1ubuntu0.1.
 pidgin depends on libsilc-1.0-2; however:
  Package libsilc-1.0-2 is not installed.
 pidgin depends on libsqlite3-0 (>= 3.3.13); however:
  Version of libsqlite3-0 on system is 3.3.5-0.2.
 pidgin depends on libxml2 (>= 2.6.27); however:
  Version of libxml2 on system is 2.6.26.dfsg-2ubuntu4.
 pidgin depends on libxrandr2 (>= 2:1.2.0); however:
  Version of libxrandr2 on system is 2:1.1.1-0ubuntu1.
dpkg: error processing pidgin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin

---

### Post by cong06 on 2007-06-09
how does this work with a remote configurations folder?
I have pidgin set up so that it goes to my external for it's Logs, config files, etc.

Where are the plugins stored?

---

### Post by jdarr5000 on 2007-06-12
What is broken or not working properly for pidgin support of SILC 

I've tried manual compiles and each time i have issues with the silc part of pidgin.

and i've tried with debs but still no luck.

Any suggestions ?

---

### Post by victorbrca on 2007-10-04
I spent some time yesterday trying to install guifications on Edgy. If anyone is having problem (most likely a noob like me), you can find a little instruction here!!!

[**_LINK_**]("http://wazem.blogspot.com/2007/10/how-to-install-pidgin-guifications-on.html")


Vic.

---

### Post by dmber on 2007-10-05
i must be missing something obvious.  i have no idea how to install the plugin pack.  i have it downloaded, but it just unarchived as a folder full of the plugins.  the .deb manager or whatever didn't open like i expected it to.

what am i missing?  how do i install it?  i went to[ this page ]("http://plugins.guifications.org/trac/downloads") to download it, and i just downloaded the top one.  now what?

---

### Post by victorbrca on 2007-10-05
> **dmber said:**
> ..i must be missing something obvious.  i have no idea how to install the plugin pack.  i have it downloaded, but it just unarchived as a folder full of the p...

I'm not sure if you followed my how to because of the link you are using. Don't know how much I can help too cz I'm a noob. 

The file I downloaded was the guifications only... [_This one._]("http://downloads.guifications.org/plugins//Guifications2/pidgin-guifications-2.14.tar.gz://")

Them just "untar" it using CLI and compile it. It should start working right after that....


Vic.

---

