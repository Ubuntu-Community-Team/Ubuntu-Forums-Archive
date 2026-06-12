---
title: "Gnome-Shell/Gnome-Shell-Extensions/Mutter Daily Git News"
date: 2011-09-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tista on 2011-09-17
Hi guys,

I'm willing to report "daily build/testing news" for those who loves Gnome-Shell experiences!! :P

**[Sun, Sep 18 9:00AM GMT+9]**

[gnome-shell]
* Version - 3.1.91.1
* Committed: [700f7fbaf382304977ca14fba11e11e3f1959d3b]("http://git.gnome.org/browse/gnome-shell/commit/?id=700f7fbaf382304977ca14fba11e11e3f1959d3b")
* Build status - need some patch like this: [http://paste.ubuntu.com/691942/]("http://paste.ubuntu.com/691942/")
* Test run - OK
* Extensions - 2 extensions were broken (Workspace Indicator, Alternative-status-menu). Since the cody had changed on "userMenu.js" and "panel.js", so Workspace Indicator could be fixed soon, but A-s-m isn't so easy to sync to upstream changes...

[gnome-shell-extensions]
* Version - 3.1.91
* Committed: [39e5bd238a0cb301772cc5615f19edc84a89542a]("http://git.gnome.org/browse/gnome-shell-extensions/commit/?id=39e5bd238a0cb301772cc5615f19edc84a89542a")
* Build status - OK
* Test run - 2 extensions were broken.
* Patches for Workspace Indicator extension: [http://paste.ubuntu.com/691948/]("http://paste.ubuntu.com/691948/")
* Alternative-status-menu didn't fixed yet... -> already posted to bugzilla: [https://bugzilla.gnome.org/show_bug.cgi?id=659308]("https://bugzilla.gnome.org/show_bug.cgi?id=659308")

---

### Post by tista on 2011-09-17
**[Sun, Sep 18 9:47AM GMT+9]**

[mutter]
* Version - 3.1.91.1
* Committed: [6087a719516255ed7b35784bd8e2cbc960898878]("http://git.gnome.org/browse/mutter/commit/?id=6087a719516255ed7b35784bd8e2cbc960898878")
* Build status -OK
* Test run - OK

---

### Post by tista on 2011-09-18
**[Sun, Sep 18 5:26PM GMT+9]**

[gnome-shell]
* Version - 3.1.91.1
* Committed: [6375724196935738f71ab1c3a1d1ad56ea5383f2]("http://git.gnome.org/browse/gnome-shell/commit/?id=6375724196935738f71ab1c3a1d1ad56ea5383f2")
* Build status - need some patch like this: [http://paste.ubuntu.com/691942/]("http://paste.ubuntu.com/691942/")
* Test run - OK
* Extensions - 2 extensions were broken (Workspace Indicator, Alternative-status-menu). Since the cody had changed on "userMenu.js" and "panel.js", so Workspace Indicator could be fixed soon, but A-s-m isn't so easy to sync to upstream changes...

/* Changed from previous */
* _userMenu codes had been compeletely removed from panel.js.
* new appearances on gdm 3.1.90 had been polished a bit.
* some translations updated.

** The build issue on src/shell-global.c had been remaining from previous post #1.

---

### Post by tista on 2011-09-18
**[Mon, Sep 19 11:10AM GMT+9]**

[gnome-shell]
* Version - 3.1.91.1
* Committed: [d3e35028ca01cab2455cda1df8b9732f08372735]("http://git.gnome.org/browse/gnome-shell/commit/?id=d3e35028ca01cab2455cda1df8b9732f08372735")
* Build status - still need some patch like this: [http://paste.ubuntu.com/691942/]("http://paste.ubuntu.com/691942/")
* Test run - OK
* Extensions - 2 extensions were broken (Workspace Indicator, Alternative-status-menu). Since the cody had changed on "userMenu.js" and "panel.js", so Workspace Indicator could be fixed soon, but A-s-m isn't so easy to sync to upstream changes...

/* Changed from previous */
* Translations were updated:
[LIST]
[*]Tamil translation
[*]Bulgarian translation
[*]Spanish translation
[*]Latvian translation
[*]Swedish translation
[*]Hungarian translation
[/LIST]
* Updated/added profiles for Shutdown menu on gdm login screen.

** The build issue on src/shell-global.c had been remaining from previous post #1.

---

### Post by cariboo on 2011-09-18
This thread really has nothing to do with testing Oneiric.

---

### Post by tista on 2011-09-18
> **cariboo907 said:**
> This thread really has nothing to do with testing Oneiric.

@cariboo907,

you mean all we have to do is only "testing existed packages"? really?

---

### Post by cariboo on 2011-09-19
Aside from your post in this thread, nobody has posted any comments, so I'm wondering if there is any interest in this news.

---

### Post by Wise Ferret on 2011-09-19
Personally I would like to know what changes are introduced in each commit going into gnome-shell, but I do fail to see how the building status should be of any interest to anybody but the developers.

---

### Post by tista on 2011-09-19
> **cariboo907 said:**
> Aside from your post in this thread, nobody has posted any comments, so I'm wondering if there is any interest in this news.

Ah I know.... Yep, this news isn't so interesting. ;)

---

### Post by tista on 2011-09-19
> **Wise Ferret said:**
> Personally I would like to know what changes are introduced in each commit going into gnome-shell, but I do fail to see how the building status should be of any interest to anybody but the developers.

@Wise Ferret,

Thanks.

Actually from now, nobody had reported such "development states" even from contributors... So I thought somebody "like me" might need such states on heavy development new commers.

Because Unity presents the  problem only for Ubuntu, but Gnome-Shell shows the Gnome's widely decisions...

cheers.

---

### Post by dino99 on 2011-09-19
> **tista said:**
> @Wise Ferret,

Thanks.

Actually from now, nobody had reported such "development states" even from contributors... So I thought somebody "like me" might need such states on heavy development new commers.

Because Unity presents the  problem only for Ubuntu, but Gnome-Shell shows the Gnome's widely decisions...

cheers.

Thanks for your research, i really hope GS & extensions be as friendly as gnome2 was. I suppose your ppa changelist have enough comments, and this thread is like a dupe.

---

### Post by tista on 2011-09-19
**[Mon, Sep 19 4:56PM GMT+9]**

[gnome-shell]
* Version - 3.1.91.1
* Committed: [391a220dc197b94da3a5c51f94892bfa92faa800]("http://git.gnome.org/browse/gnome-shell/commit/?id=391a220dc197b94da3a5c51f94892bfa92faa800")
* Build status - OK
* Test run - OK
* Extensions - 2 extensions were broken (Workspace Indicator, Alternative-status-menu). Since the cody had changed on "userMenu.js" and "panel.js", so Workspace Indicator could be fixed soon, but A-s-m isn't so easy to sync to upstream changes...

/* Changed from previous */
* Added fingerprint support for gdm:
[https://bugzilla.gnome.org/show_bug.cgi?id=657823]("https://bugzilla.gnome.org/show_bug.cgi?id=657823")
* Added user-logo on gdm login-screen:
[https://bugzilla.gnome.org/show_bug.cgi?id=658062]("https://bugzilla.gnome.org/show_bug.cgi?id=658062")

** The build issue on src/shell-global.c had fixed by patched gjs:
[http://osdir.com/ml/commits.gnome/2011-09/msg06891.html]("http://osdir.com/ml/commits.gnome/2011-09/msg06891.html")
** So now we might need to run this git released gnome-shell wirh gjs-1.29.18+git20110916 or higher. because "gjs_context_gc" function was used as memory cleaner on gs and this function had appeared from such newer gjs...

---

### Post by tista on 2011-09-19
> **dino99 said:**
> Thanks for your research, i really hope GS & extensions be as friendly as gnome2 was. I suppose your ppa changelist have enough comments, and this thread is like a dupe.

Hi dino99,

I agree...
To be honest, I could live with only gtk2, AWN and metacity... ;)
But at the same time we might have to see what's going on the upstream. Because always we're concerning whether our own resources could be carried to the next generation desktops and workspaces when newbie desktop experiences were comming...

P.S:
Soon "1-Click installation for gs-extensions" might come... if so, what a great usability on Gnome-Shell comes with "user-friendly".

cheers.

---

### Post by sanderd17 on 2011-09-19
> **tista said:**
> 
Soon "1-Click installation for gs-extensions" might come... if so, what a great usability on Gnome-Shell comes with "user-friendly".



Isn't that already released? [http://www.webupd8.org/2011/09/gnome-shell-31911-released-with-one.html](http://www.webupd8.org/2011/09/gnome-shell-31911-released-with-one.html)

I did not test it since I prefer stable Gnome 3.0.2

---

### Post by pressureman on 2011-09-19
> **tista said:**
> Ah I know.... Yep, this news isn't so interesting. ;)

I for one always find tista's posts interesting, and I also enjoy reading tista's blog.

I hope that some of that bleeding edge GS stuff eventually lands in Ubuntu, and I hope that Ubuntu does not become so engrossed in Unity, that it forgets that about half the user base prefer GS.

I haven't seen something polarize a community like that for a quite a while. Probably not since somebody changed the window controls from the right side to the left side ;-)

---

### Post by tista on 2011-09-19
> **sanderd17 said:**
> Isn't that already released? [http://www.webupd8.org/2011/09/gnome-shell-31911-released-with-one.html](http://www.webupd8.org/2011/09/gnome-shell-31911-released-with-one.html)

I did not test it since I prefer stable Gnome 3.0.2

Yep, it didn't released. ;) But browser-plugins had prepared alrealy!!

And agree... 3.0.x is now stable. 3.1.91.x is the beta2(or so?) release of 3.2, so today we almost could see the features of 3.2. 1-Click would be released on early 3.2 I hope...

cheers.

---

### Post by tista on 2011-09-19
> **pressureman said:**
> I for one always find tista's posts interesting, and I also enjoy reading tista's blog.

I hope that some of that bleeding edge GS stuff eventually lands in Ubuntu, and I hope that Ubuntu does not become so engrossed in Unity, that it forgets that about half the user base prefer GS.

I haven't seen something polarize a community like that for a quite a while. Probably not since somebody changed the window controls from the right side to the left side ;-)

Hi Pressureman,

Really thanks! ;)

and that's correct. then more saying, exactly most users love Gnome2! :P LoL
but now ubuntu seems to force us to live with Unity... yeah every developments focused on unity/compiz only... it means "Ubuntu becomes Windows?!" 

Ubuntu is only one distribution under the free-software, and we may have a lot of possibilities to employ our own favorite DE even on bleeding edge stuff... I really hope this words: "Do it as you like". ;)

regards.

---

### Post by karmila on 2011-09-19
Hi tista,

I add and then update from the ppa and now i have "elementary-style" lightdm.
How to revert it to default?

Thank you.

---

### Post by tista on 2011-09-19
> **karmila said:**
> Hi tista,

I add and then update from the ppa and now i have "elementary-style" lightdm.
How to revert it to default?

Thank you.

Hi karmila,

OK... today I didn't fix the revert to default...
So sorry and could you purge my PPA via "ppa-purge"?

or override my package using an official package...
1. download that one from here:
[amd64][https://launchpad.net/ubuntu/+source/unity-greeter/0.0.8-0ubuntu1/+build/2786017]("https://launchpad.net/ubuntu/+source/unity-greeter/0.0.8-0ubuntu1/+build/2786017")
[i386][https://launchpad.net/ubuntu/+source/unity-greeter/0.0.8-0ubuntu1/+build/2786019]("https://launchpad.net/ubuntu/+source/unity-greeter/0.0.8-0ubuntu1/+build/2786019")
2. install it via "sudo dpkg -i PACKAGE_FILE_NAME" from deb file.
3. restart the machine or restart lightdm via "sudo service lightdm restart".

cheers.

---

### Post by karmila on 2011-09-19
> **tista said:**
> Hi karmila,

OK... today I didn't fix the revert to default...
So sorry and could you purge my PPA via "ppa-purge"?

or override my package using an official package...
1. download that one from here:
[amd64][https://launchpad.net/ubuntu/+source/unity-greeter/0.0.8-0ubuntu1/+build/2786017](https://launchpad.net/ubuntu/+source/unity-greeter/0.0.8-0ubuntu1/+build/2786017)
[i386][https://launchpad.net/ubuntu/+source/unity-greeter/0.0.8-0ubuntu1/+build/2786019](https://launchpad.net/ubuntu/+source/unity-greeter/0.0.8-0ubuntu1/+build/2786019)
2. install it via "sudo dpkg -i PACKAGE_FILE_NAME" from deb file.
3. restart the machine or restart lightdm via "sudo service lightdm restart".

cheers.

Hi,

I installed gnome-shell-extensions from your ppa and still want to keep them, so i just override(downgrade) unity-greeter. It's work okay :)

Thank you.

---

### Post by makitso on 2011-09-19
Actually, I found this post to be interesting since I am testing the Gnome 3 shell on a daily basis.  I am also interested in the extensions that work with it since my comparison platform is Fedora 15.  With Fedora, I can right click on the desktop and the "create launcher" options shows.  This is a BIG issue for me and so am waiting for that to show up on Unity/Gnome 3.

---

### Post by tista on 2011-09-19
> **karmila said:**
> Hi,

I installed gnome-shell-extensions from your ppa and still want to keep them, so i just override(downgrade) unity-greeter. It's work okay :)

Thank you.

@Karmila,

OK... you're welcome. ;)
But don't forget that today we couldn't run "alternative-status-menu" extension... :sad: If really you guys want it, I could suggest the workaround (maybe hackish way :/):
1. backup this file:
```
sudo mv /usr/share/gnome-shell/js/ui/userMenu.js /usr/share/gnome-shell/js/ui/userMenu.js.org
```
2. put my patched userMenu.js into "/usr/share/gnome-shell/js/ui/":
[userMenu.js]("http://paste.ubuntu.com/693111/")
3. restart gs via Alt+F2 and "r" command.

Have a nice day!! ;)

---

### Post by tista on 2011-09-19
> **makitso said:**
> Actually, I found this post to be interesting since I am testing the Gnome 3 shell on a daily basis.  I am also interested in the extensions that work with it since my comparison platform is Fedora 15.  With Fedora, I can right click on the desktop and the "create launcher" options shows.  This is a BIG issue for me and so am waiting for that to show up on Unity/Gnome 3.

Hi Makitso,

Wow fedora man comming?! :P

and sounds cool features about "create launcher"... I suppose its feature wasn't included git extensions branch, so fedora made it as something like hack the nautilus's context menu? or context menu on desktop with right click were provided gnome-shell somehow?

cheers.

---

### Post by karmila on 2011-09-19
> **tista said:**
> @Karmila,

OK... you're welcome. ;)
But don't forget that today we couldn't run "alternative-status-menu" extension... :sad: If really you guys want it, I could suggest the workaround (maybe hackish way :/):
1. backup this file:
```
sudo mv /usr/share/gnome-shell/js/ui/userMenu.js /usr/share/gnome-shell/js/ui/userMenu.js.org
```2. put my patched userMenu.js into "/usr/share/gnome-shell/js/ui/":
[userMenu.js]("ttp://paste.ubuntu.com/693111/")
3. restart gs via Alt+F2 and "r" command.

Have a nice day!! ;)

Ah yes, i didn't see that extension on the list.
I'll try that tomorrow... since it is already late night here.
see ya.

---

### Post by tista on 2011-09-19
> **karmila said:**
> Ah yes, i didn't see that extension on the list.
I'll try that tomorrow... since it is already late night here.
see ya.

@karmila,

If you wanna apply my workaround, please use updated version:
[userMenu.js]("http://paste.ubuntu.com/693425/")

Since recently huge upstream changes had come!! ;)

cheers.

---

### Post by tista on 2011-09-19
**[Tue, Sep 20 8:26AM GMT+9]**

[gnome-shell]
* Version - 3.1.91.1
* Committed: [http://git.gnome.org/browse/gnome-shell/commit/?id=9f41f5c740172aae473fa5913e325f3aa14ea883]("http://git.gnome.org/browse/gnome-shell/commit/?id=9f41f5c740172aae473fa5913e325f3aa14ea883")
* Build status - OK
* Test run - OK
* Extensions - 2 extensions were broken (Workspace Indicator, Alternative-status-menu). Since the cody had changed on "userMenu.js" and "panel.js", so Workspace Indicator could be fixed soon, but A-s-m isn't so easy to sync to upstream changes...

/* Changed from previous */
* A lot of minor bug fixes had been applied:
[http://git.gnome.org/browse/gnome-shell/log/]("http://git.gnome.org/browse/gnome-shell/log/")
( See above comitted entries for 12 hours...)

/* Remarkables */
** If you guys provided any gnome-shell theme, me too, please sync to the latest codes especially panel section! padding codes had been changed. see my theme's diff:
[https://launchpadlibrarian.net/80379073/gnome-shell-theme-pantheon_3.1.91.1~oneiric21_3.1.91.1~oneiric22.diff.gz]("https://launchpadlibrarian.net/80379073/gnome-shell-theme-pantheon_3.1.91.1~oneiric21_3.1.91.1~oneiric22.diff.gz")

---

### Post by tista on 2011-09-19
**[Tue, Sep 20 8:29AM GMT+9]**

[mutter]
* Version - 3.1.91.1
* Committed: [http://git.gnome.org/browse/mutter/commit/?id=c1368155fccb0677c74616cbb7366c02c24323b6]("http://git.gnome.org/browse/mutter/commit/?id=c1368155fccb0677c74616cbb7366c02c24323b6")
* Build status - OK
* Test run - OK

/* Changed from previous */
* Updated Japanese translation
* Updated Danish translation
* Updated Catalan translation
* Fixed minor bug:
[https://bugzilla.gnome.org/show_bug.cgi?id=659477]("https://bugzilla.gnome.org/show_bug.cgi?id=659477")
> When a window loses its frame we must unset any overlay path previously set on
the shaped texture.

Not doing so would cause rendering glitches near the window corners in
e.g. chrome/chromium by changing the Appearance preference "Use system title
bar and borders" &#8594; "Hide system title bar and use compact borders".


---

### Post by jbicha on 2011-09-19
> **tista said:**
> Hi Makitso,

Wow fedora man comming?! :P

and sounds cool features about "create launcher"... I suppose its feature wasn't included git extensions branch, so fedora made it as something like hack the nautilus's context menu? or context menu on desktop with right click were provided gnome-shell somehow?

cheers.

Create launcher was removed in GNOME 3.2. Fedora 15 still uses GNOME 3.0 so that's why it's still there.

---

### Post by karmila on 2011-09-19
> **tista said:**
> @karmila,

If you wanna apply my workaround, please use updated version:
[userMenu.js]("http://paste.ubuntu.com/693425/")

Since recently huge upstream changes had come!! ;)

cheers.

Thank you, i have "power off" option now :D

I need to lock unity-greeter from upgrading to elementary-greeter. 
Since now is still in beta i don't want to lock any package/s from upgrade.

Will i have option not to lock unity-greeter but still using your ppa and default unity-greeter?

---

### Post by jbicha on 2011-09-19
> **tista said:**
> 
but now ubuntu seems to force us to live with Unity... yeah every developments focused on unity/compiz only... it means "Ubuntu becomes Windows?!" 

Ubuntu is only one distribution under the free-software, and we may have a lot of possibilities to employ our own favorite DE even on bleeding edge stuff... I really hope this words: "Do it as you like". ;)


Just because Unity is default doesn't mean that you can't install your favorite desktop instead.

Since GNOME Shell 3.2 will be final next week, this thread probably won't be needed at least not until 3.3 starts cooking.

---

### Post by tista on 2011-09-20
> **jbicha said:**
> Create launcher was removed in GNOME 3.2. Fedora 15 still uses GNOME 3.0 so that's why it's still there.

Hi jbicha,

A lot of thanks for your info all the time... :P
OK.. I finally knew what's happening on fedora15.

cheers.

---

### Post by tista on 2011-09-20
> **jbicha said:**
> Just because Unity is default doesn't mean that you can't install your favorite desktop instead.

@jbicha,

Yeah I know... and your hard work as well...
But actually Ubuntu makes some side effectiveness to any other gtk desktop environments via developping unity... its situation seems completely(or slightly?) different from other distro...

> Since GNOME Shell 3.2 will be final next week, this thread probably won't be needed at least not until 3.3 starts cooking.

Yep, but I wish the time had come soon to start cooking 3.3... ;)

Regards.

---

### Post by tista on 2011-09-20
> **karmila said:**
> Thank you, i have "power off" option now :D

I need to lock unity-greeter from upgrading to elementary-greeter. 
Since now is still in beta i don't want to lock any package/s from upgrade.

Will i have option not to lock unity-greeter but still using your ppa and default unity-greeter?

@karmila,

You have synaptic?
if so, 
1. search and select the "unity-greeter" from list.
2. following MainMenu -> Package -> Lock Version and click it.

But I really don't know how USC did... to tell the truth, I've never loaded USC. lol

cheers.

---

### Post by tista on 2011-09-20
**[Wed, Sep 21 8:37AM GMT+9]**

[gnome-shell]
* Version - 3.1.92
* Committed:[e9282c39870963a9a0e9e0cc0acadb9babe02989]("http://git.gnome.org/browse/gnome-shell/commit/?id=e9282c39870963a9a0e9e0cc0acadb9babe02989")
* Build status - OK
* Test run - not yet...
* Extensions - 2 extensions were broken (Workspace Indicator, Alternative-status-menu). Since the cody had changed on "userMenu.js" and "panel.js", so Workspace Indicator could be fixed soon, but A-s-m isn't so easy to sync to upstream changes...

/* Changed from previous */
* See details on NEWS:
> 3.1.92
======

* Login screen
  - Add the ability to set a logo at the top of the user list [Ray; #658062]
  - Add fingerprint reader support [Ray; #657823]
  - Add a power button offering the choice of Suspend/Restart/Power off
    [Ray; #657822]
  - Remove the option to view the current keyboad layout [Matthias; #659164]
  - Make Control-Alt-Tab work for full keyboard access [Ray; #659177]
* Frequently initiate a full garbage collection; Spidermonkey isn't very good
  at tracking the amount of resources we have allocated so this hopefully will
  improve memory usage without affecting performance too much [Colin; #659254]
* Stop adding a notification when the network connection is lost
  [Colin; #658954]
* When disabling notifications; display a notification
  "Your chat status will be set to busy" [Florian; #652718]
* Fix keynav in network dialogs [Florian; #659133]
* Improve calendar styling [Sean; #641135, #651299]
* Shrink padding around panel buttons for narrow screens [Dan; #651299]
* Allow enabling the onscreen keyboard through the accessibility menu
  [Dan; #612662]
* Fix problem that was causing VPN secret dialogs to be delayed before showing
  [Florian; #658484]
* Make custom-keybindings for the window switcher that don't use alt
  work correctly [Florian; #645200]
* Fix duplicate application icons in the Activities Overview [Colin; #659351]
* Bug fixes for dimming windows with attached modal dialogs
  [Jasper, Owen; #659302, 659634]
* Add build-time support for BROWSER_PLUGIN_DIR environment variable
  [Vincent; #659123]
* Build fixes [Vincent; #659194]
* Code cleanups and test cases
  [Adel, Dan, Florian, Jasper; #651299, #658092, #658939]
* Misc bug fixes
  [Adel, Colin, Cosimo, Dan, Florian, Giovanni, Jasper, Ray, Xavier;
  #651299, #652837, #657249, #658004, #658150, #658239, #658469, #658598,
  #658605, #659050, #659159, #659210, #659270, #659370, #659633]

Contributors:
 Giovanni Campagna, Cosimo Cecchi, Xavier Claessens, Matthias Clasen,
 Rui Matos, Florian Müllner, Jasper St. Pierre, Owen Taylor,
 Vincent Untz, Colin Walters, Sean Wilson, Dan Winship

Translations:
 Ihar Hrachyshka [be], Alexander Shopov, Ivaylo Valkov [bg],
 Mario Blättermann [de], Jorge González, Daniel Mustieles [es],
 Arash Mousavi [fa], Ville-Pekka Vainio [fi], Fran Dieguez [gl],
 Sweta Kothari [gu], Gabor Kelemen [hu], Jiro Matsuzawa [ja],
 Luca Ferretti [it], Rudolfs Mazurs [lv], Kjartan Maraas [nb], A S Alam [pa],
 Piotr Dr&#261;g [pl], Duarte Loreto [pt], Yuri Myasoedov [ru],
 Daniel Nylander [se], Matej Urban&#269;i&#269; [sl], Miroslav Nikoli&#263; [sr, sr@latin],
 Michal &#352;trba [sv], Tirumurti Vasudevan [ta], Ph&#432;&#417;ng Lê Hoàng [vi],
 Aron Xu [zh_CN], Chao-Hsiung Liao [zh_HK, zh_TW]

**EDIT**

Test run - OK

P.S:
I've noticed now... one thing... "where did the contact search go away?" :/

---

### Post by tista on 2011-09-20
**[Wed, Sep 21 8:42AM GMT+9]**

[mutter]
* Version - 3.1.92
* Committed: [d1a87288a4d83c13cadecc96e75e58d09016a62f]("http://git.gnome.org/browse/mutter/commit/?id=d1a87288a4d83c13cadecc96e75e58d09016a62f")
* Build status - OK
* Test run - not yet...

/* Changed from previous */
See details on NEWS:
> 3.1.92
======
* Fix bug with unredirecting full-screen windows on multi-monitor -
  notably affected gnome-screensaver [Adel; #657869]
* Disable top resizing of attached dialogs [Jasper; #657795]
* Code cleanup [Jasper, Rui]
* Misc bug fixes [Adel, Florian, Jasper, Rui;
  #658069, #659266, #659523, #659477]

Contributors:
 Adel Gadllah, Rui Matos, Florian Müllner, Jasper St. Pierre

Translations:
 Joan Duran [ca], Joe Hansen [dk], Jiro Matsuzawa [ja], Daniel Korostil [uk]

**EDIT**

Test run - OK

---

### Post by tista on 2011-09-21
**[Thu, Sep 22 8:57AM GMT+9]**

[gnome-shell]
* Version - 3.1.92
* Committed: [http://git.gnome.org/browse/gnome-shell/commit/?id=74c2074d5a5ac9bdb29701092c88fe143f362dab]("http://git.gnome.org/browse/gnome-shell/commit/?id=74c2074d5a5ac9bdb29701092c88fe143f362dab")
* Build status - Local seems OK
* Test run - not yet...
* Extensions - 2 extensions were broken (Workspace Indicator, Alternative-status-menu). Since the cody had changed on "userMenu.js" and "panel.js", so Workspace Indicator could be fixed soon, but A-s-m isn't so easy to sync to upstream changes...

/* Changed from previous */
* Developers added build dependencies related to the latest gjs 1.29.18 or higher... but our main repository still stayed with 1.29.17, so it might be failed to build on Launchpad...

---

### Post by tista on 2011-09-22
**[Fri, Sep 23 10:45AM GMT+9]**

[gnome-shell]
* Version - 3.1.92
* Committed: [5f6dce2b5ca7ef07c6c6b43020390f2a6143c53e]("http://git.gnome.org/browse/gnome-shell/commit/?id=5f6dce2b5ca7ef07c6c6b43020390f2a6143c53e")
* Build status - OK
* Test run - OK

[mutter]
* Version - 3.1.92
* Committed: [1b71eeb02a32b44b6d4511a975f209fbead4e5a1]("http://git.gnome.org/browse/mutter/commit/?id=1b71eeb02a32b44b6d4511a975f209fbead4e5a1")
* Build status - OK
* Test run - OK

/* Changed from previous */
* From this commit, we have to update libcogl2 to libcogl5 for both gs/mutter because of their dependencies. and strongly gs/mutter must be pared each other in this period...

---

### Post by tista on 2011-09-26
**[Tue, Sep 27 10:48AM GMT+9]**

[gnome-shell]
* Version - **3.2.0**
* Committed: [337b399a753e4a5df757d9899a0ed14748def593]("http://git.gnome.org/browse/gnome-shell/commit/?id=337b399a753e4a5df757d9899a0ed14748def593")
* Build status - OK
* Test run - not yet...

[mutter]
* Version - **3.2.0**
* Committed: [d2ca160ea346a593bbf12bc04e5a97bb37041c20]("http://git.gnome.org/browse/mutter/commit/?id=d2ca160ea346a593bbf12bc04e5a97bb37041c20")
* Build status - OK
* Test run - not yet...

/* Changed from previous */
* See details for gnome-shell 3.2:
> 3.2.0
=====
* Prevent the fallback on-screen keyboard from showing up while
  GNOME Shell is running [Dan, #659865]
* Disable code to reposition windows around the on-screen keyboard;
  it wasn't finished or working properly. [Dan; #659643]
* Fix interaction between on-screen keyboard and notifications
  [Dan; #658603]
* Fix menu-sizing problems in right-to-left locales. [Florian; #659827]
* Update chat icons in the message tray when an avatar image changes
  [Marina; #659768]
* Fix problem with empty notification bubbles being left [Marina; #659862]
* Fix problem with chat notifications bouncing when new messages come in.
  [Marina; #659768]
* Fix bug that was causing SIP calls to automatically be accepted in some
  circumstances [Guillaume; #660084]
* Fix string that should have been marked translatable [Frédéric]
* Fix a crash that could happen during CSS transitions [Florian; #659676]
* Build fixes [Colin, Florian]

Contributors:
 Guillaume Desmottes, Florian Müllner, Frédéric Péters, Colin Walters,
 Dan Winship, Marina Zhurakhinskaya

* See details for mutter 3.2:
> 3.2.0
=====
* Fix _NET_WM_FRAME_EXTENTS not to include invisible borders [Jasper; #659848]
* Fix application-specified window placement (-geometry) for
  invisible borders [Jasper; #659848]

Contributors:
 Jasper St. Pierre

Translations:
 Nilamdyuti Goswami [as], Carles Ferrando [ca@valencia], Petr Kovar [cz],
 Mario Blättermann [de], Inaki Larranaga [eu], Gabor Kelemen [hu],
 Takayoshi Okano [ja], Changwoo Ryu [ko], Djavan Fagundes [pt_BR]

---

### Post by tista on 2011-10-03
**[Tue, Oct 04 11:15AM GMT+9]**

[gnome-shell-extensions]
* version - 3.2
* Committed: [4d803fce0ffa470c847d70b82aa4611dee8276d7]("http://git.gnome.org/browse/gnome-shell-extensions/commit/?id=4d803fce0ffa470c847d70b82aa4611dee8276d7")
* Build Status - OK
*Test Run - OK

** From this commit, these extensions had been fixed a lot of issues!! :P
* Alternate-tab
* Alternative-status-menu
* Dock
* Workspace-indicator

So these must work on current gnome-shell 3.2.0...

---

### Post by tista on 2011-10-05
**[Thu, Oct 06 09:36AM GMT+9]**

[gnome-shell]
* Version - 3.2.0
* Committed : [d862c0879b1fe3dffaa2a993340dd42c216b31b4]("http://git.gnome.org/browse/gnome-shell/commit/?id=d862c0879b1fe3dffaa2a993340dd42c216b31b4")

* Build Status - OK
* Test Run - OK

** This commit has succeeded to get back "Contacts Search" again!! :P
Now it seems to run well contact-search on overview search.

---

