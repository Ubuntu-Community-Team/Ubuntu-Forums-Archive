---
title: "HOWTO: Setup Desktop/Eyecandy. Tips'n'Tricks."
date: 2005-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2005-10-17
**Also work in Ubuntu 5.10, but the 8. category might be a little diffrent**
**Works on Dapper and Edgy (+beryl)**

I write this HOWTO, I got alot of PMs on how to do this and how to that  because of my Screenshots I've added to the Gallery. So I made this simple HOWTO on the basics changes to make a desktop look mean, clean killing machine. I'll add some more to the howto continuesly.

Make sure before you start to set up universe/multiverse in your sourcelist.

NB. Don't Pm me about the icons. All of them I've gathered throughout the web and added to my desktop manually. Most of them are copyrighted/trademarked etc. So I won't transfer them. Sorry.

_The Index_
1. Howto setup semi-transparent panels.
2. Howto Eyecandy -gdesklets.
3. Howto Change icon size & make icons without name on the desktop.
4. Howto change GTK themes and icons for root application.
5. Howto install cursor themes on ubuntu/gnome.
6. Howto change login splash.
7. Howto change desktop themes (a.k.a GTK & Metacity).
8. Howto change login screen (GDM).
9. Howto: change skins on bmp and xmms (music player).
10. Howto advanced eyecandy.

====================================================

**1. HOWTO SETUP SEMI-TRANSPARENT PANELS**

[img]http://www.imageviper.com/displayimage.php?id=24951&name=Howto-Trans-panels.jpg[/img]

This does not require extra files or applications.
1. Right click on the upper panel and select **New Panel**.
2. Drag it down so it's is vertical. You can do it with middle mouse button or left+right mouse button.
3. Right click on it and select **Properties**.
4. In **General** tab: Unselect **Expand** and select **Show hide buttons**. Eventually change pixels size to your likening.
5. In **Background** tab: Select **Solid color** and change **Style** to your are saticefied with the outcome. I have mine on default.
6. Now move the panel to the place on your desktop you want it.

**[color=red]NOTE:[/color]*** Horizontal panels can't auto hide. Only hope is that the Gnome developers adds  it. Also you can't see your windows behind the panels, only your desktop wallpaper.*

====================================================

**2. HOWTO EYECANDY - GDESKLETS**


[IMG]http://www.imageviper.com/displayimage.php?id=24949&name=Howto-Gdesklets.jpg[/IMG]
*[size=1]From up to down - LTNotify, LTPager and Psi-tasklist. Click the picture to enlarge.*[/size]

This requires some files and application.
1. Open the terminal and write:
```
sudo aptitude install gdesklets gdesklets-data
```

2. Now we want gdesklets to start automatically every time we boot up. Click **System** tab in the upper panel. Then **Preferences** ---> **Sessions**.
3. Click the **Startup Programs** tab and click the **Add** button.
4. In the startup Command write: **gdesklets** and click **OK**.
5. To choose and run the gdesklets stuff. Click the **Applications** tab in the upper panel. Then **Accessories** ---> **gDesklets**.
6. Have a look around and pick a gdesklet you like, to add it select the gdesklet. Then go to the **file** tab and select **Run selected desklet**.
7. Now the choosen gdesklet appears and will follow your mouse until you make a left click. To move it again click with middle mouse button or left+right mouse button.
8. To configure the choosen gdesklet, simply right click on it and menu will pop up.
9. For more gdesklets: [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

**[color=red]NOTE:**[/color]* Some gdesklets might need that you have some extra libs. installed. A good way is to find the gdesklets at [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) and check up on what you need to get the gdesklet you have choosen to work.*

====================================================

**3. HOWTO: CHANGE ICON SIZE & MAKE ICONS WITHOUT NAME ON DESKTOP**


[img]http://www.imageviper.com/displayimage.php?id=24950&name=howto-icon.jpg[/img]


This does not require extra files or applications.
1. To have an launcher with no name on it on the desktop. Right click on the launcher erease the name. Now hit the **Space** button and press **Enter** afterwards.
2. To resize the icon on you desktop. Right click on the launcher and choose **Stretch Icon**. Four square appears in each corner.
3. Hold left mouse button down and move back and forth to change the size.
4. To exit the resize, simple left click outside the launcher.

====================================================

**4. HOWTO: CHANGE GTK THEMES AND ICONS FOR ROOT APPLICATIONS**
Are you tired of that your root applications doesn't match your desktop theme?

[[img]http://ubuntuforums.org/attachment.php?attachmentid=621&stc=1&thumb=1&d=1112604992[/img]](http://ubuntuforums.org/attachment.php?attachmentid=621&d=1112604992) [[img]http://ubuntuforums.org/attachment.php?attachmentid=622&stc=1&thumb=1&d=1112605599[/img]](http://ubuntuforums.org/attachment.php?attachmentid=622&d=1112605599)
[size=1]*Click to enlarge the screenshots*[/size]

Here's the answer, with these codes your root applications gets the same theme, icons and fonts.

```

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

```

Thanks to [angrykeyboarder]("http://ubuntuforums.org/member.php?u=12487") for showing an easier way to do this.

====================================================

**5. HOWTO: INSTALL CURSOR THEMES ON UBUNTU/GNOME**  

[img]http://www.imageviper.com/displayimage.php?id=24947&name=Gcursor.jpg[/img]
[size=1]*Click to enlarge the screenshots*[/size]

This does require extra files or applications.
1. First we have to install gcursor application on Ubuntu. Open the terminal and write:
```
sudo aptitude install gcursor
```

2. Go to [Gnome-look.org]("http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=00c93645b63d36656e0bb060cdb0212e") and pick the cursor(s) you want.
3. Go to **System** tab ---> **Preferences** ---> **Cursor Selection**.
4. Push the **Install Theme** button, browse and select the cursor. No need to unpack the cursor files. Gcursor will do that for you.
5. Now pick the cursor you want in the Xcursor menu and press the **Close** button. The new cursor will first appear when you log in next time.


**[color=red]NOTE:**[/color]* If the cursor you have selected in gcursor don't appear in the menu then press the **Go To Theme Folder** button, click the folder named after the cursor. There should be a new folder with the name of you cursor in there. Right click it and choose **cut**. Press the **Up** button in your file browser and **Paste** the file here. That should do the trick.*

====================================================

**6. HOWTO: CHANGE LOGIN SPLASH.** 

[img]http://www.imageviper.com/displayimage.php?id=24952&name=Screenshot-GNOME_Splash_Screen_Preferences.png[/img]
[size=1]*Click to enlarge the screenshots*[/size]

This does require extra files or applications.
1. Getting the boot splash application. Open the terminal and write:
```
sudo aptitude install gnome-splashscreen-manager
```
2. Find a suitable splash screen at [Gnome-look.org]("http://gnome-look.org/index.php?xcontentmode=160&PHPSESSID=4e511a66ca60b940fb2d146784fd5881") or [http://gnome-look.org/]("http://gnome-look.org/").   Download your choosed splash.
3. Click the **System** tab ---> **Preferences** ---> **Splash Screen**.
4. Press the **Install** button, browse and pick your splashscreen.
5. In the **Installed Splash Screens** window left click the one you want and press the **Activate** button.
6. Now next time you login, you'll see the new splash. Enjoy ^^.

Thanks to [aboe](http://ubuntuforums.org/member.php?u=9449) for the notice of the splashscreen manager.

====================================================

**7. HOWTO: DESKTOP THEMES (A.K.A GTK & METACITY).**


1. First you need to find you a theme(s) you like at [http://art.gnome.org/](http://art.gnome.org/) or [http://gnome-look.org](http://gnome-look.org) and download it. Look under the GTK 2 to find your theme(s). Though at art.gnome.org it's split up in windowborder (metacity) and application (gtk).
2. Next go to **System** tab ---> **Preferences** ---> **Theme**.
3. Click the **Install Theme** button and browse and select the theme you want to install.
4. Now you can choose the theme in the **Theme Preferences** viewer. 
5. If that's not the case you have to click **Theme Details** and select the theme manually. **Control** tab for GTK themes and **Window border** for Metacity.

====================================================

**8. HOWTO: CHANGE LOGIN SCREEN (GDM).**

[IMG]http://www.imageviper.com/displayimage.php?id=24953&name=Screenshot-Login_Screen_Setup.jpg&thumb=0[/IMG]
[size=1]*Click to enlarge the screenshots*[/size]

1. You can download GDM themes at [http://art.gnome.org/](http://art.gnome.org/) or [http://gnome-look.org](http://gnome-look.org).
2. To open Login Screen Setup: **System** tab ---> **Adminstration** ---> **Login Window** or in terminal:
```
gksudo gdmsetup
```
3. In **local** tab. Push the **add** button and browse to the downloaded GDM theme.

====================================================

**9. HOWTO: CHANGE SKIN ON BMP AND XMMS (MUSIC PLAYER).**

[Screenshot](http://www.imageviper.com/displayimage.php?id=27887&name=bmp.jpg)

1. Download a skin from [www.gnome-look.org](www.gnome-look.org) under xmms section.
2a. if you're using bmp copy the file to **/home/<username>/.bmp/Skins**
2b. if you're using xmms copy the file to **/home/<username>/.xmms/Skins**
```
cd /where/you/saved/the/file
cp XXXXXXXX /home/<username>/.bmp/Skins
```
Or use nautilus to manouvre (the file browser) around.
3a. Open bmp and press **<ctrl>+<p>** and select the skin under appreance.
3.b  Open Xmms and press **<ctrl>+<s>** and select your skin.

====================================================

**10. HOWTO: ADVANCED EYECANDY.**

[Howto Beryl & Compiz - Ultimate Eyecandy](http://ubuntuforums.org/showthread.php?t=272104)
[Knome Guide: Stealing KDE's Eye Candy]("http://ubuntuforums.org/showthread.php?t=115974") 
[Make QT apps look more Gnome'ish]("http://ubuntuforums.org/showthread.php?t=76633") 
[Change the default usplash colors]("http://ubuntuforums.org/showthread.php?t=82835") 
[conky 1.3.0 -- lightweight system monitor for X]("http://ubuntuforums.org/showthread.php?t=61297") 
[Gtk1.2 not so ugly]("http://ubuntuforums.org/showthread.php?t=107135")

 
------------------------------
HOWTOs by Artificial Intelligence:
[HOWTO: Use 'Create Document' option. Open Office and custom files.]("http://ubuntuforums.org/showthread.php?t=76419")
[HOWTO: Automatically play CDs and DVD when inserted.]("http://ubuntuforums.org/showthread.php?t=77146")
[HOWTO: Install F-Prot with GTK frontend (anti-virus)]("http://ubuntuforums.org/showthread.php?t=88357")
[HOWTO: Install AVG free anti-virus]("http://ubuntuforums.org/showthread.php?t=136064")
[HOWTO: Install Azureus (newest, non-repo way)]("http://ubuntuforums.org/showthread.php?t=144546")

---

### Post by henrypootel on 2005-10-17
Another Great Tip.
Ubuntu is starting to make XP look decidedly 'rustic'(see also: butt ugly).
Thanks

---

### Post by nehalem on 2005-10-18
Wierd, can't install gdesklets and several other packages.  The version it says is a available is really not there.  Furthermore it depends on libcairo1 (the version that is actually there) and that's not available in the repositories.  Are they updating the servers?

---

### Post by Perfect Storm on 2005-10-18
Updated the Howto.

Added: HOWTO: Change GTK themes for root application & GTK greeter

---

### Post by Perfect Storm on 2005-10-19
Updated the howto:

Added: Howto install cursor themes on ubuntu/gnome.

---

### Post by shankin on 2005-10-19
Thanks for writing this.  I've been looking at your desktop pictures and drooling, but never knew how to set things up.

I noticed that after I installed gdesklets and gdesklets-data, though, that I didn't seem to have all the desklets I was looking for.  The Psi-tasklist you showed, for example, wasn't included.

How do I get additional gdesklets?  I'm assuming the gdesklets-data package doesn't include all that is available.

Update:  I learned from the gdesklets site that the Psi desklets apparently no longer work.  A pity - the tasklist in the screenshot looks much nicer than the normal Ubuntu/Gnome one.

---

### Post by Muhammad on 2005-10-19
I need to know the name of the icon theme please!

---

### Post by LaSSarD on 2005-10-19
nice :)
there's a better way to change themes for root applications (at least I think so):
just move the folders inside ~/.themes to to /usr/share/themes

I think you could give some advices for desklets, like ones you like or ones which are nice but don't work well...

anyway, nice how-to :)

---

### Post by Perfect Storm on 2005-10-19
Thanks for the reply.


@LaSSarD

It's just what I told /usr/share/themes, but I thought It's easier to understand it  that way. This Howto is aimed for newbies who wants to set up their desktop :)

About advising what is nice or not of thet gdesklets, I won't. Everyone have diffrent taste ;)

@Muhammad

Both the GTK theme and Icon theme is called D3a.

@shankin

Just follow the howto on thte gdesklet if you want to install downloaded gdesklets.
Psi-desklet do work despite what they are saying. I'm using it right now on Breezy without any tweaking ^^
The reason why I havn't added the gdesklets I have shown for download is that I used all my ubuntu-forums space and I have limited bandweight on my site.



.:=The AI Dude=:.

---

### Post by DoeRayMe on 2005-10-19
Do you know where we could get the psi-tasklist from anywhere else?

---

### Post by Nomearod on 2005-10-20
Thanks for this how-to. It's excelente!

---

### Post by Perfect Storm on 2005-10-20
As people have requested I have uploaded Psi-tasklist. It's attached to the first post. Use it wisely.

---

### Post by Perfect Storm on 2005-10-21
Updated the howto.

Added: Howto change login splash.

---

### Post by dlpfmVfH on 2005-10-21
[quote=Artificial Intelligence]Updated the howto.

Added: Howto change login splash.[/quote]

isn't it easier to install gnome-splashscreen-manager from universe??

---

### Post by Caboto on 2005-10-21
How about adding **torsmo** or even better **conky** and some example configuration?
I really like this little progs.

---

### Post by Perfect Storm on 2005-10-21
#aboe
isn't it easier to install gnome-splashscreen-manager from universe??

#Caboto
How about adding torsmo or even better conky and some example configuration?


I'll take a look at it.

---

### Post by Perfect Storm on 2005-10-21
The Howto Splash is changed.

---

### Post by Gandalf on 2005-10-21
I've installed conky since i saw the post above and i've been playing a bit with the ~/.conkyrc file
I have done one that fits my needs, it is a changed version of:
[[img]http://conky.sourceforge.net/conky-thumb-1.png[/img] ](http://conky.sourceforge.net/conky.png) 

the version posted [here](http://conky.sourceforge.net/screenshots.html) which i did change was for mpd, i change it to fit XMMS, you need to install the package xmms-infopipe and enable it via XMMS preferences though...

screenshot and .conkyrc attached

---

### Post by Perfect Storm on 2005-10-21
Testing conky. Seems nice, but there's some irrating bugs in it.
Like disappearing and dwaring you mouse over it with left mouse button makes cut into it.

---

### Post by Gandalf on 2005-10-21
[QUOTE=Artificial Intelligence]Testing conky. Seems nice, but there's some irrating bugs in it.
Like disappearing and dwaring you mouse over it with left mouse button makes cut into it.[/QUOTE]
Also it flickers a lot but it's nice, hope bugs will be fixed in future releases

---

### Post by merlyn on 2005-10-21
I know that this is somewhat off topic, but could you produce a howto on compiling the nitro kernel.

Cheers.

---

### Post by Perfect Storm on 2005-10-21
I could add a conky howto in here, but I think it should have its own howto, a howto which go deep into configuration of it, because of the possibilties that newbies will have trouble setting it up to their likening.

---

### Post by Perfect Storm on 2005-10-21
[QUOTE=merlyn]I know that this is somewhat off topic, but could you produce a howto on compiling the nitro kernel.

Cheers.[/QUOTE]

Perhaps in the future, I have to many projects rolling at the moment.

---

### Post by merlyn on 2005-10-21
[quote=Artificial Intelligence]Perhaps in the future, I have to many projects rolling at the moment.[/quote]

Thankyou for responding so quickly.

I'll keep my eyes open for any new howto's from you, and should you get the time the possibility of a nitro howto.

Thanks once again.

Cheers.

---

### Post by DoeRayMe on 2005-10-21
Hmmm i installed the LTNotify, however it does not show my notification icons, my one on the gnome-panel does, but this one doesnt

How do i get it to work?

---

### Post by Perfect Storm on 2005-10-21
You need to remove the notify in the panel and make a logout and a login before it works perfect.

---

### Post by gabhla on 2005-10-21
This is great stuff....thanks.

---

### Post by GoA on 2005-10-23
Change of the root applications theme didn't work for me. I copied my Vista theme to the usr/share/themes folder and changed the settings accordingly to your guide and it doesn't show anything. :(

---

### Post by sailor420 on 2005-10-23
When I try to install the splashscreen manager, apt/synaptic can't find the package. Is that package in some other repository?

BTW, I'm still running hoary, if that helps.

---

### Post by Perfect Storm on 2005-10-23
If you've added the universe to your source list then it's not there for Hoary.



@GoA
Make sure that you spelled it right. Linux is case sensitive, if that don't work try with another theme.

---

### Post by sailor420 on 2005-10-23
Yeah, it's spelled right. Guess its just not there for Hoary. That's OK, ill be upgrading in the next couple of days. Thanks for the help anyways.

---

### Post by anaoum on 2005-10-24
[QUOTE=merlyn]I know that this is somewhat off topic, but could you produce a howto on compiling the nitro kernel.

Cheers.[/QUOTE]

May i ask what a *nitro kernel* is??

thanks

---

### Post by Perfect Storm on 2005-10-24
Quote:Nitro-sources is a linux kernel patchset based around the -ck patchset by Con Kolivas and is considered to be experimental, it contains numerus user-requested features and other things gathered from various sources.

---

### Post by GoA on 2005-10-24
Another theme helped. Thanks for the tip. :)

---

### Post by yesplease on 2005-10-28
A playfull variation on 1. HOWTO SETUP SEMI-TRANSPARENT PANELS by ArtificialIntelligence is to add drawers. One can make a maze of horizontal and vertical panels by adding drawers in drawers. Drawers can be made transparent too. Drawers do not autohide, but all drawers can be closed simultaneously by clicking the hide buttons of the first horizontal panel.

Right-clicking a panel gives the add to panel option, where drawers can be found  (lots of them :) ).

---

### Post by ntony on 2005-10-29
Great HOWTO !!! Appreciate your work!


```
ntony@ubuntu:~$ sudo apt-get install gdesklets gdesklets-data
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets
```


The package doesn't exist for Breezy:(

---

### Post by Wolki on 2005-10-29
[QUOTE=ntony]
The package doesn't exist for Breezy:([/QUOTE]

It does. Make sure you have the unierse repository enabled. Look here for how to do it: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by tnq13 on 2005-10-29
is there any way to make the panels(tray,pager and the task bar) to still always on top?

tks...

---

### Post by Blue1k on 2005-10-29
How do I change the background color for the splash screen?

Thanks!

---

### Post by angrykeyboarder on 2005-10-30
**Re #4**. A much simpler alternative:

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

This has nothing to do with GTK Greeter, but what it will do is have the root user's themes, icons and fonts follow/match whatever ones you're using. 

** Re #6**.  Before checking for themes @ [http://gnome-look.org/]("http://gnome-look.org/") why not first try "the home team" at [http://art.gnome.org]("http://art.gnome.org").

Or you could also install the gnome-art package and check the site from your desktop.

---

### Post by ntony on 2005-11-03
Really great HOWTO ! Thanks AI !!!



[QUOTE=tnq13]is there any way to make the panels(tray,pager and the task bar) to still always on top?

tks...[/QUOTE]

Yeah, taskbar should be always on top. I tried to configure it but got no option to make it always on top. Any suggestion?

---

### Post by maltje on 2005-11-03
try to do this sudo apt-get install gdesklets gdesklets-data
but got back that he can't find gdklets

---

### Post by benplaut on 2005-11-04
thanks a million on the nameless icon thing... never occured to me to just space :P

tip: if you have a solid background, or one with solid colors, make SVG icons of that color (only that color!), make them nameless, strech them to make them big and hard to miss, and place them. they seem invisible, but mouse over to make them work :)

---

### Post by yesplease on 2005-11-04
@benplaut: I had a similar idea, but with transparent icons on a wallpaper background (havent tried it yet).

---

### Post by Vidar on 2005-11-04
Should work fine with just transparent icons.

---

### Post by ^NoX on 2005-11-05
[QUOTE=merlyn]I know that this is somewhat off topic, but could you produce a howto on compiling the nitro kernel.

Cheers.[/QUOTE]

Well, someone has wrote a howto just for you :)
[http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174)

(the -cK patch is the one called "Nitro" (AFAIK) the one which you asked for)

---

### Post by Joch on 2005-11-09
It has been asked 2 times yet, but no answer.
How can you set the gdesklets 'always on top'. Because otherwise it's not really useful.

Can somebody help us ?

---

### Post by Perfect Storm on 2005-11-09
To have the Psi-tasklist above:

```

cd /home/<username>/.gdesklets/Displays/psi-tasklist
gedit psi-tasklist.display

```

Change:
<display window-flags="sticky, below">

to 

<display window-flags="sticky, above">

restart Psi-tasklist

---

### Post by onesojourner on 2005-11-11
where do I get the Psi-tasklist? I have googled it and I come up with nothin.

---

### Post by ConnyBK on 2005-11-11
Have a look at post #12 ;)

---

### Post by canadianwriterman on 2005-11-11
[QUOTE=Joch]It has been asked 2 times yet, but no answer.
How can you set the gdesklets 'always on top'. Because otherwise it's not really useful.

Can somebody help us ?[/QUOTE]

If you mean, literally "stay on top" I believe there is a setting for that in the preferences if you right click on the gdesklets icon in the top panel

---

### Post by onesojourner on 2005-11-11
I must be missing where it is in the first post then.

---

### Post by onesojourner on 2005-11-11
is there some other way to get Psi-tasklist?

---

### Post by Perfect Storm on 2005-11-12
[QUOTE=onesojourner]is there some other way to get Psi-tasklist?[/QUOTE]

Its attached on the first post.

---

### Post by onesojourner on 2005-11-12
ok sorry about that. I dont know if my browser is not displaying it correct or not but I finally got it by copying the attachement lines (witch is just text in the browser) and pasting it into an openoffice document.

---

### Post by erikpiper on 2005-11-19
This is sweet! Thanks!

I was looking at your desktops and have 2 questions,

Where did you get the box wallpaper?
And how do you get the good looking disk mounter/ volume changer?

Thanks!

---

### Post by dude2425 on 2005-11-19
For those who wan't true nameless icons, without even the highlighted space, just drag the launcher into a text editor like gedit, and remove everything after the '=' on the line begining "Name[en_US]="

Also, instead of using whole panels, try just adding drawers to an existing panel, and customizing it. This way you can have a purty little icon you can click on.

---

### Post by Perfect Storm on 2005-12-07
Updated with Howto change Desktop themes.

---

### Post by renzokuken on 2005-12-16
Hi there. Sweet desktop by the way.

I'm trying to get the "pop-out" panels on the lower left hand side of the screen working properly. I have the panels sorted, and with all the launchers for the apps working perfectly, however, i'm having alot of difficulty changing the icons for the apps (mplayer, amarok, k3b, etc etc) to some newer ones i downloaded from gnome-look.org. I've been right clicking on the launchers --> properties, then on the icon change button but i cannot select the icons i want to change them to, they are all "greyed" out so i cant select them.

Do they have to be a certain size or file type (they are all PNG 48x48 though)?

What am i doing wrong? It's one of those minor quibbles that can quickly turn highly annoying, he he >_< !

Thanks

---

### Post by Perfect Storm on 2005-12-16
Usually I just drag the icon instead of browsing. You may try that and see if it works.

---

### Post by renzokuken on 2005-12-16
Thanks dude, worked like a charm.

Who says theres never a simple answer. >_<

---

### Post by Ðrehmini on 2005-12-16
[QUOTE=Artificial Intelligence][[url]http://gnome-loook.org]([url]http://gnome-loook.org)[/quote]

Tad bit of a typo there.

---

### Post by Bloot on 2005-12-16
[QUOTE=angrykeyboarder]**Re #4**. A much simpler alternative:

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

This has nothing to do with GTK Greeter, but what it will do is have the root user's themes, icons and fonts follow/match whatever ones you're using. [/QUOTE]

Hey many thanks, I didn't know how to match my icons and that worked fine!.

---

### Post by godvalve on 2005-12-16
I didn't notice any info on how to change the login manager. Perhaps this could be added to the guide?

Thx for the guide btw.

---

### Post by Perfect Storm on 2005-12-18
Updated: rewritten and changed titel 4. Howto change GTK themes and icons for root application. Thanks to Angrykeyboarder.

---

### Post by Perfect Storm on 2005-12-18
[QUOTE=godvalve]I didn't notice any info on how to change the login manager. Perhaps this could be added to the guide?

Thx for the guide btw.[/QUOTE]

Comming soon.

---

### Post by nhisyam on 2006-01-08
is there any safe way to restore default settings for all the changes being made on the desktop? just in case i don't like it  ... or i made things go wrong..

thanks in advance

---

### Post by lizardking on 2006-01-08
you have to delete the hidden folder .gnome .gnome2 .metacity .gnome-private etc and you will got the default ubuntu desktop

---

### Post by abyssspecter on 2006-01-17
[QUOTE=Artificial Intelligence]**7. HOWTO: DESKTOP THEMES (A.K.A GTK & METACITY).**

[img]http://thilockdominus.freehomepage.com/images/newfoldeHowto/GTKnMetacity.jpg[/img]

1. First you need to find you a theme(s) you like at [http://art.gnome.org/](http://art.gnome.org/) or [http://gnome-loook.org](http://gnome-loook.org) and download it. Look under the GTK 2 to find your theme(s). Though at art.gnome.org it's split up in windowborder (metacity) and application (gtk).
2. Next go to **System** tab ---> **Preferences** ---> **Theme**.
3. Click the **Install Theme** button and browse and select the theme you want to install.
4. Now you can choose the theme in the **Theme Preferences** viewer. 
5. If that's not the case you have to click **Theme Details** and select the theme manually. **Control** tab for GTK themes and **Window border** for Metacity[/QUOTE]

Im having a problem installing my Metacity themes i got from gnomre-look. i hit install theme, and nothing came up in the prefrences, so i went to Theme Details, and its not under either Controls or  Icons. I dont see a 'Window Border' tab either. 

If someone could help, id appreciate it

---

### Post by Perfect Storm on 2006-01-17
A link to the metacity theme you're trying to use.

---

### Post by RaptorRaider on 2006-01-19
Can someone please post a download link to LTPager?
I can't seem to find one through Google.

---

### Post by Perfect Storm on 2006-01-19
It's within gdesklets-data

---

### Post by shane2peru on 2006-01-20
Ok, I followed this, and some other Howto guide that now I can't find.  I changed everything to a nice blue - Grub screen, The booting up screen (blue text)  the login-screen, and then after that I get a brown background witha usplash screen that I can change, and currently have a blue one.  How do I ditch the ugly brown screen behind the splash screen?  Thanks!

Shane

---

### Post by era86 on 2006-01-20
i dont know if this is what you mean.. afterall im new to this myself.. but you can try going to Apps>Sys Tools>Configuration Editor

then go to apps>nautilus>preferences on the left side.. in the window to the right, find background_color (somewhere near the top)... and replace that val with watever color you want..

i could be wrong

-ERA

edit: or go to the login screen setup?

---

### Post by TrinitronX on 2006-01-20
I'm using kde as my default desktop, and I chose in my kde config to use my current kde theme to style gtk applications too.  The fix for changing root's theme for gtk seems to work, but with one flaw.
It seems this works when I start programs with sudo, but not gksudo for some reason.  If anyone can find a fix for the gksudo still using the ugly gtk theme, that'd be great.

EDIT: I just tried using kdesu instead of gksudo, and still any application launched from either will take on the default gtk theme, and not my kde one.

---

### Post by thoffmeyer on 2006-01-23
great howto, thanks :)

---

### Post by abyssspecter on 2006-01-23
[QUOTE=Artificial Intelligence]A link to the metacity theme you're trying to use.[/QUOTE]

here you go: [http://gnomelook.org/content/show.php?content=26050]("http://gnomelook.org/content/show.php?content=26050")

---

### Post by Perfect Storm on 2006-01-29
[QUOTE=abyssspecter]here you go: [http://gnomelook.org/content/show.php?content=26050]("http://gnomelook.org/content/show.php?content=26050")[/QUOTE]

It's because there's 4 diffrent themes in the packages. Just extract them to /home/<username>/.themes

[quote=shane2peru]
Ok, I followed this, and some other Howto guide that now I can't find. I changed everything to a nice blue - Grub screen, The booting up screen (blue text) the login-screen, and then after that I get a brown background witha usplash screen that I can change, and currently have a blue one. How do I ditch the ugly brown screen behind the splash screen? Thanks![/quote]

**System** ---> **Adminstration** ---> **Login Screen Setup**

**GTK greeter** tab. Background color box.

---

### Post by Perfect Storm on 2006-01-29
Added:

8. Howto change login screen (GDM).
9. Howto advanced eyecandy.

---

### Post by ketan on 2006-01-31
This looks good,

Thanks\\:D/

---

### Post by gerbman on 2006-02-05
I downloaded the psi-tasklist file and ran the installer. It said the install was successful, but I don't see psi-tasklist anywhere in the gdesklets shell. Any thoughts?

Thanks.

---

### Post by Perfect Storm on 2006-02-05
Check under Toolbar/Misc category


OT: The images is down at the moment due to I havn't renewed webspace...

---

### Post by gerbman on 2006-02-05
[QUOTE=Artificial Intelligence]Check under Toolbar/Misc category[/QUOTE]

Odd. It's not there. Did I need to install anything else beforehand? You mention that it requires the PSI theme, but I have been unable to locate that.

Thanks for your help.

EDIT:  just to be clear...the entry will read "psi-tasklist" correct?

---

### Post by Perfect Storm on 2006-02-05
Let's take this from the beginning :)

Open gdesklets, file tab, choose Install package (and browse). Then psi-tasklist should show in the box. Select it go back to the file tab and pick run selected desklet.

---

### Post by gerbman on 2006-02-05
[QUOTE=Artificial Intelligence]Let's take this from the beginning :)

Open gdesklets, file tab, choose Install package (and browse). Then psi-tasklist should show in the box. Select it go back to the file tab and pick run selected desklet.[/QUOTE]

Oh geez...I've been noobified. I wasn't installing it through the gdesklets shell, but unpacking it and running the installer myself. Sheesh...thanks :-)

---

### Post by Perfect Storm on 2006-02-05
Live and learn ^^

Enjoy gdesklets :)


.:=The AI Dude=:.

---

### Post by endersshadow on 2006-02-05
Solid beginner's guide, AI.  Would just like to suggest another link...if only because once you do it you'll be playing with it for hours on end:

[Switch desktops in 3D](http://ubuntuforums.org/showthread.php?t=100167) by anil_robo

---

### Post by Perfect Storm on 2006-02-05
Thanks :)
I've added the link.
Also the images are now displaying again, found a good place to storage images cheap.

---

### Post by halfvolle melk on 2006-02-07
:oops:

---

### Post by jamesford on 2006-02-07
i cant get LTnotify to work. i mean, it works but no icons show up in it..isnt it supposed to 'replace' the systray?

---

### Post by Perfect Storm on 2006-02-07
[QUOTE=jamesford]i cant get LTnotify to work. i mean, it works but no icons show up in it..isnt it supposed to 'replace' the systray?[/QUOTE]

You need to log out and log in before it works, also you need to remove the standard notify before it work correctly.

---

### Post by maxdevis on 2006-02-09
[QUOTE=DoeRayMe]Do you know where we could get the psi-tasklist from anywhere else?[/QUOTE]

for what use is this psi-tasklist?

---

### Post by Perfect Storm on 2006-02-09
[QUOTE=maxdevis]for what use is this psi-tasklist?[/QUOTE]

To show application windows etc. like the standard in ubuntu but just more eye candy-ish.

[img]http://www.imageviper.com/displayimage.php?id=24949&name=Howto-Gdesklets.jpg[/img]
The one in the buttom.

---

### Post by maxdevis on 2006-02-09
i want to install corner xmms, with gdesklets, but i get always this error:

/home/michiel/.gdesklets/Displays/CornerXMMS/cornerxmms-bottomright.display         
>   1 xmms = get_control('IKXmms:4qz2i6vxsrqcia2mbt1lf2ca1-2')

---

### Post by Perfect Storm on 2006-02-09
I get the same errors and havn't been able to solve it yet. A bug report to the maker of the theme would be a nice idea.

---

### Post by KCMiller3 on 2006-02-20
Thanks for the great guide...

I am currently using psi-tasklist and followed your advice to get it to stay on top and it does just that but is it possible to allow windows to snap to it so that it isn't above important windows.  Thanks!

~Kevin

---

### Post by Perfect Storm on 2006-02-22
Not what I know of.

---

### Post by Perfect Storm on 2006-02-25
Updated:
Added: 9. HOWTO: CHANGE SKIN ON BMP AND XMMS (MUSIC PLAYER).

---

### Post by bluevoodoo1 on 2006-02-26
[QUOTE=Artificial Intelligence]
**4. HOWTO: CHANGE GTK THEMES AND ICONS FOR ROOT APPLICATIONS**
Are you tired of that your root applications doesn't match your desktop theme?

Here's the answer, with these codes your root applications gets the same theme, icons and fonts.

```

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

```

Thanks to [angrykeyboarder]("http://ubuntuforums.org/member.php?u=12487") for showing an easier way to do this.[/QUOTE]

I attempted that to use that link to my .themes/.icons/.fonts and still I can't get root themes to work, (the link has now been removed). I tried installing some themes with gksudo gnome-theme-manager and when I close it and run 'sudo nautilus --no-desktop' or synaptic there are no changes. I'm running blackbox so any metacity problems are fine, but even in GNOME I can't get root themes to work. Changing themes as a regular user work fine. Any ideas?

```

brian@ubuntu:~$ sudo gnome-theme-manager
- using device default
- using device default

(gnome-theme-manager:10823): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:10823): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed
Window manager warning: Failed to read theme from file /usr/share/themes/metacity-1/metacity-theme-1.xml: Failed to open file '/usr/share/themes/metacity-1/metacity-theme-1.xml': No such file or directory

(gnome-theme-manager:10823): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:10823): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed

(gnome-theme-manager:10823): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:10823): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed

(gnome-theme-manager:10823): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:10823): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed

```

You have an awesome desktop.

---

### Post by AlexR1 on 2006-02-26
Why don`t you move your theme to /usr/share/themes/
To be more clear when i download theme Test i exctract them to desktop.so now i have directory Test on my desktop.
cd Desktop
sudo mv Test /usr/share/themes/
enter password
and then i change to theme Test trough theme preferences.
Like this i got root application skied too.

---

### Post by Perfect Storm on 2006-02-27
Or

(just change d3a with the theme you want)
```
cd /home/<username>/.themes
sudo cp -r  d3a /usr/share/themes
sudo gedit /etc/gdm/gdm.conf

```

Now I changed under [gui]

GtkTheme=d3a
GtkThemesToAllow=d3a

---

### Post by benplaut on 2006-02-27
include a link to one of the E17 howtos under advanced eye candy?

---

### Post by Perfect Storm on 2006-02-27
Can you post a link to the specific you had in mind?

---

### Post by bluevoodoo1 on 2006-02-27
[QUOTE=AlexR1]Why don`t you move your theme to /usr/share/themes/
To be more clear when i download theme Test i exctract them to desktop.so now i have directory Test on my desktop.
cd Desktop
sudo mv Test /usr/share/themes/
enter password
and then i change to theme Test trough theme preferences.
Like this i got root application skied too.[/QUOTE]

Tried that too, still nothing. I'd really like to get the icons in sudo nautilus working more than anything else. Still getting errors like...

```

(gnome-theme-manager:8429): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:8429): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed

(gnome-theme-manager:8429): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

```

Any ideas?

---

### Post by NoWhereMan on 2006-03-01
what do you think of this?
[http://forgeftp.novell.com//greent/homepage/screenshots.html](http://forgeftp.novell.com//greent/homepage/screenshots.html)
A console which comes down from the top of the screen pressing an hotkey, like the QuakeIII one! Sweet! :mrgreen:

---

### Post by Perfect Storm on 2006-03-15
Nice one,but I havn't be able to find the config file for to change background and/or making it transparent.

---

### Post by Perfect Storm on 2006-03-15
[QUOTE=bluevoodoo1]Tried that too, still nothing. I'd really like to get the icons in sudo nautilus working more than anything else. Still getting errors like...

```

(gnome-theme-manager:8429): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:8429): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed

(gnome-theme-manager:8429): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

```

Any ideas?[/QUOTE]

Did you try my way? (posted above). There might be some complication when doing it with one of the default themes that comes with ubuntu.

---

### Post by NoWhereMan on 2006-03-15
[QUOTE=Artificial Intelligence]Nice one,but I havn't be able to find the config file for to change background and/or making it transparent.[/QUOTE]

it shares the same settings of gnome-terminal

bye

---

### Post by styven on 2006-03-18
Hi there,

Whilst trying to change my some resolotion settings in properties for the panel, I lost all taskbar panels, they flash up at start up and keep on flashing up, then dissapear, how do i get them back. All i was doing was changing the resolution, not setting them to hide or anything.

Steve.

---

### Post by Perfect Storm on 2006-03-18
Sounds like bug.

Okay first try <alt>+<F2> and write

```
gnome-panel
```

---

### Post by styven on 2006-03-18
Thanks for such a prompt response, sadly pressing alt/f2 does nothing, do i take it that i need to open a teminal, is that the only way from the keyboard? if it is i am stuffed!!

---

### Post by Perfect Storm on 2006-03-18
It should give you the Run Application box.

Okay we just make a launcher then. Right click on the desktop ---> Create launcher.

Name: terminal
command: gnome-terminal

Try this way.

---

### Post by bluevoodoo1 on 2006-03-18
[QUOTE=Artificial Intelligence]Did you try my way? (posted above). There might be some complication when doing it with one of the default themes that comes with ubuntu.[/QUOTE]

Yes, I just tried it, and no luck.... hmmmmm.

---

### Post by styven on 2006-03-18
okay...........

I have a terminal up now, what do i need to do next?

Steve

---

### Post by Perfect Storm on 2006-03-18
try with

```

gnome-panel

```

---

### Post by styven on 2006-03-18
Okay......

It does the same thing as a at strat up, flashes on and off, i have the followwing error message in the terminal..............

styven@edubuntu:~$ gnome-panel
/home/styven/.themes/T-ish-Brushed/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
Segmentation fault
styven@edubuntu:~$

Is there a command i can type that will set the taskbar/icon resolution back to default?

Steve.

---

### Post by styven on 2006-03-18
Have sorted it....

It was the pixels that i changed, and to changing it back sorted it, i gad only changed it from 25 to 26.

Bear in mind that the tasbar only flashed up for a second, in that time i had to right click, hit properties then the panel properties box opens for about a second in which time i had to change the pixels back to 25 and all is back to normal:D 

Took about 4 goes but i got it!!

Thanks for all your help\\:D/

---

### Post by kaks on 2006-03-20
do any of these commands work on dapper 64bit?

Thanks in advance

---

### Post by Perfect Storm on 2006-03-21
In theory, yes. If you want you can test it if you like and report back.

Thanks.

---

### Post by Perfect Storm on 2006-03-26
Update: 
Added LTPager desklet to attachment.

---

### Post by digitalkarabao on 2006-04-08
i tried all methods on changing the themes of the root applications but i am still stuck with the gray, boring theme for root applications.  the issue is selective though. i noticed that i can change the theme of the root application to themes that have 'gtk', 'metacity' folders inside the theme folders.  i am trying to use a theme which only contains 'index.theme' file inside it. 

am i doing something wrong?

---

### Post by Perfect Storm on 2006-04-09
I don't think you can do it if it only contains a index.theme file. Well none of what I know off.

---

### Post by x5452 on 2006-04-19
a couple questions on splash and gdm, first off, from gnome-look i downloaded a splash 'grub' screen, so it makes a cool screen where it shows the choose kernel and os page, how do you get to the menus where you are supposed to edit stuff so those work?  
Installation:

Copy the file (*.xpm.gz) to e.g. /boot/grub/

Then add the following line to your /boot/grub/menu.lst:

splashimage=(hd1,0)/boot/grub/Debian_Ent_GRUB.xpm.gz

Change the (hd1,0) if you have a different setup.

Also, are those splash screens ONLY for the grub part, or will it be the same pic after? Are there splash screens that FILL the screen? I only find ones that are small little rectangles.

Is there any screens you can get to change where, on boot up, it says ubuntu, and lists all the stuff as it is loading it up?:confused:

---

### Post by RRS on 2006-04-19
Haven't spent much time on "eye candy" yet, just a couple things from gDesklets, still learning how to use Linux in general.

Main question on the subject is should I wait till final version of Dapper is out? Just wondering if any pre-release bugs will cause me difficulty I can avoid by waiting.

Thanks

---

### Post by Perfect Storm on 2006-04-20
Well...if you dist upgrade with apt-get you might run into problem. But if you make a clean install you should be save. Just remember the golden rule number one: backup your stuff first. :)
Oh...Dapper just hit Beta.

---

### Post by oyvindaa on 2006-04-20
I've installed several new login screens like described in the first post of this subject, but it crashes when I try to log out and log in. It happens with all of the newly installed themes. Anyone know why?
I'm using ubuntu breezy badger.

---

### Post by x5452 on 2006-04-21
Hey there, I was linked earlier to a thread of yours where you told how to change the 'main menu' icon from that orange thing, and it worked, cool.  I am curious if there is a way also, to change things like, screenshot, lockscreen, volume, trash can ect.. the ones where you right click but dont have the option. How do you find out where the icon is located to change it?  also, I was following the instructions here:
[http://gmail-notify.sourceforge.net/faq.php](http://gmail-notify.sourceforge.net/faq.php)
to change the icon for the gmail notifier, but when i open gimp, find the icon and replace it with what i want then click save, it says it cant save, permission denied... any ideas?  thanks a lot!

---

### Post by Perfect Storm on 2006-04-21
It's a bit tricky...well time consuming to find all the icons and change them manually. But the easist way is download a theme from gnome-look.org install it and go to the folder where the icons is /home/<username>/.icons/<icon theme name> and look there for eventually if it have the icon that change the specific icon you want to change. Then replace it.
Another way is to use the "Search for files" application and search under system. Eg. search for gmail and a list of files shows up and properly also the icons of that application.

Other places to look is commenly 
/usr/share/pixmaps
/usr/share/icons/hicolor

> to change the icon for the gmail notifier, but when i open gimp, find the icon and replace it with what i want then click save, it says it cant save, permission denied... any ideas? thanks a lot!]

As it says you don't have permission ;). It's a security thing that you don't have access to the root/system as an user (a reason why linux is way much secure than windows by default). So if you want to change the icons, find a new icon or make your own and name it after the icon you want to change.
Lets take the gmail as an example again. I've found the gmail notify icon in /usr/share/pixmaps and its name is gmail-notify-icon.png so the icon I want to replace it with shall have the same name. To replace it, Open the terminal:
```
sudo cp gmail-notify-icon.png /usr/share/pixmaps
```

or if you have many icons and want to move them all in ones to the same location:
```
sudo cp *.png /usr/share/pixmaps
```
Which makes it easier.

---

### Post by x5452 on 2006-04-21
ah i get, so its like the same advice i saw you gave for chaning the main menu icon, ....time consuming, lol.  I found a bunch in usr/share/icons/hicolor, so ill start there.  Im curious though, if the one that is standard is named icon-name.png, and you change the name of the one you want to the same thing, then move it to the folder, how does it know to use the new one?

---

### Post by Perfect Storm on 2006-04-21
It have to be the same name. Surely you could hack the specific application and make it look for another icon. But frankly that's a more time consuming.

---

### Post by newpants2003 on 2006-05-08
thanx a lot

---

### Post by shurguywutt on 2006-05-15
word...

---

### Post by gauravmakin on 2006-05-28
I am new to linux and had a question. I installed gdesklets and have been trying ever since to get the desklets to be transparent. How can i make the desklets to be transparent. Most of them dont give that option but the screen shots show transparent desktops. 
    I have been trying on the weather desklet for example, a common transparent desklet, but for me, i can not seem to get it to be set to transparent. 

please please please help me on this as soon as possible. I would really appreciate your help

---

### Post by Perfect Storm on 2006-05-28
Gdesklets aren't real transparent, only for the background/wallpaper)

---

### Post by Perfect Storm on 2006-06-01
Changed the howto to 6.06, some minor changes to fit it.
The howto still works for ubuntu 5.10 except category 8 that might be a little diffrent.

---

### Post by Gaurav on 2006-06-02
[QUOTE=Artificial Intelligence]Gdesklets aren't real transparent, only for the background/wallpaper)[/QUOTE]

I have been trying to get the transparent desklets. If you can :confused: please help me out in getting some transparent desklets on my desktop. What do i need to install and using what commands. Please please if you can help me out here.

I was using gdesklets and uninstalled them due to not been able to acheive transparency. Is there anyway i can get transparent desklets like in your screenshots. I am willing to change stuff that i am using to be able to acheive transparent desklets. 

Please help me out. I shall be really grateful. Thank you
Waiting for your reply

---

### Post by Perfect Storm on 2006-06-02
Can you provide a screenshot at the current state of your gdesklet?

---

### Post by JGKC9AYC on 2006-06-03
I'm using Gnome.
I didn't have much luck figuring out Gdesklets.
I like the way you have your desktop set up w/the weather & system monitor...was that done w/Gdesklets?
Also, I tried getting rid of the Ubuntu logo beside "Applications" using the "killall" command, but that didn't work.  Is there a way to use other logos besides the Ubuntu & the Gnome?
Is there a way to combine "Applications", "Places", & "System" by using a "Start"-like button?
That's all I can think of for now.
Thanks!  :)

---

### Post by Perfect Storm on 2006-06-03
Yes, it's gdesklets.

> I didn't have much luck figuring out Gdesklets.

By running it? Or setting it up?


> Also, I tried getting rid of the Ubuntu logo beside "Applications" using the "killall" command, but that didn't work.

Which method did you use?

> Is there a way to combine "Applications", "Places", & "System" by using a "Start"-like button?

right click on the panel ---> add to panel. Select Main Menu.

---

### Post by JGKC9AYC on 2006-06-03
[QUOTE=Artificial Intelligence]

By running it? Or setting it up?[/quote]

Both


> Which method did you use?

I went to [this]("http://doc.gwos.org/index.php/Gnome_Icon") site & followed the instructions...it worked w/Breezy.

---

### Post by Some_Bored_Dude on 2006-06-03
Just on a note for new 6.06 Installs. You need to uncomment the universe repositories from the sources list located in /etc/sources.list to install gdesklets & gdesklets-data. Unsure about any others =)

You'll find the following 2 lines:
```
deb http://archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe
```

This will vary depending where you live. Mine has au. infront of archive (Due to living in Australia), so Im assuming without au. is the default.

Nice how-to by the way :mrgreen:

---

### Post by Perfect Storm on 2006-06-03
> Both

Installation:
```
sudo apt-get install gdesklets
```
If you are on Dapper it also installs gdesklets-data, if not you need also to install this.
Now a launcher is made in applications ---> Accessories (if not killall gnome-panel) click it.
Now choose a gdesklets you want to use (left click the desklet) and go to **file** tab and select run **selected Desklet** (Note some of them might need extra libs to work, like HDD temp etc.) [http://doc.gwos.org/index.php/Lm-sensors_hddtemp](http://doc.gwos.org/index.php/Lm-sensors_hddtemp)
Also check gdesklets homepage for more desklets.
To make gdesklets to startup on every boot go to System tab ---> Preferences ---> Sessions. 
Click the **startup** tab and afterwards the **add** button. Write **gdesklets**

> I went to this site & followed the instructions...it worked w/Breezy.
If you use a custom icon theme. Rename the the icon you want to use to **distributor-logo.png** and move it to **/home/<username>/.icons/<name-of-the-theme>/128x128/apps**

---

### Post by JGKC9AYC on 2006-06-03
[QUOTE=Artificial Intelligence]
Now choose a gdesklets you want to use (left click the desklet) and go to **file** tab and select run **selected Desklet** (Note some of them might need extra libs to work, like HDD temp etc.) [http://doc.gwos.org/index.php/Lm-sensors_hddtemp](http://doc.gwos.org/index.php/Lm-sensors_hddtemp)[/quote]

I got this message:

[I]No i2c device files found. Use prog/mkdev/mkdev.sh to create them.
[/I]

> Also check gdesklets homepage for more desklets.

Couldn't get the temps working & for the weather, all I got was Tokyo...that's too far east of me.  :)  I ended up installing a different (iWeather) one, but it's size can't be adjusted, I don't think.  I can go up to a 10 day forecast, but it takes up the entire bottom of my desktop if I do that, so I keep most of it hid.

> If you use a custom icon theme. Rename the the icon you want to use to **distributor-logo.png** and move it to **/home/<username>/.icons/<name-of-the-theme>/128x128/apps**

Got that taken care of...thanks!

---

### Post by sandpaperback on 2006-07-04
[QUOTE=angrykeyboarder]**Re #4**. A much simpler alternative:

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

[/QUOTE]

The reason this doesn't work for some people is because it actually creates an extra directory.  Like this:

/root/.themes/.themes

So, change the command line to this and your root apps should have the proper theme:

```
sudo ln -s /home/<your name here>/.themes /root
```

You'll probably have to delete any /root/.themes, /root/.icons, /root/.fonts that you've tried to make work before.

---

### Post by Perfect Storm on 2006-07-04
Thanks for the input, sandpaperback. I'll suggest that for people who have trouble with it :)

---

### Post by JGKC9AYC on 2006-07-04
I'm still having problems w/gDesklets disappearing from my desktop only to leave a gray box in their place.  The icon also disappears from the toolbar.  I can't seem to find an answer for this.

---

### Post by foxjwill on 2006-08-01
I'm trying to install this one theme from gnome-look.org, and it keeps saying that the file format is invalid. Here's the link: [http://www.gnome-look.org/content/show.php?content=43354](http://www.gnome-look.org/content/show.php?content=43354)

---

### Post by Perfect Storm on 2006-08-01
Extract the package to /.themes then go to the theme selector and click theme details. Now you can select Murrina in Controls (gtk theme).

---

### Post by argie on 2006-08-05
Thank you so much. I was looking the themes bit.

There's a little typo there though, in section 7. Gnome-look.org has one too many o's.

---

### Post by spiral777 on 2006-08-06
How do I change the fonts for my root applications back? I like the rest, but for some reason the fints in all my webpages are messed up now.

---

### Post by Perfect Storm on 2006-08-06
cd /root
sudo rm -rf .fonts

---

### Post by zeroaquarius on 2006-08-07
Thanks for the very detailed guide! :-D . I am new to linux and had a bit of a tough time changing some of the eye-candy (especially the splash-screen!) and thanks to your guide here, I'm well on my way to customisation heaven! Kudos!:-D

---

### Post by Special K on 2006-08-10
Hi Guys, i found this to be a very informative and helpful thread.....but boy my eyes are aching now:D 

I have a question, which i cant see on here, so apologies if i missed it.

I am running all gdesklets i need and have them config'd and running ok....except one of them and its proving very frustrating.

No matter what weather desklet i use, i just cannot get any of them to work!

The ones that advise to use the direct yahoo http/xml/rss feed address i simply cannot get to work. I have restarted desklets, removed and re-added and still no output.

I have used the 4 letter aviation codes and the 4/5 digit weather station codes abd still no joy.

There has got to be a simple answer to this.....

Has anyone got it please?

Cheers

Spesh

the address i am using from yahoo is below, as copied from their site...can anyone see any errors in it, which would cause it not to work

[http://weather.yahoo.com/forecast/UKXX0078.html](http://weather.yahoo.com/forecast/UKXX0078.html)

---

### Post by foxjwill on 2006-08-10
I've had the same problem. I found it was a heck of a lot easier just to stick to the gnome weather panel applet

---

### Post by Special K on 2006-08-10
Yup! i'm begining to think that too!!

Someone must have come across this problem and solved it though.

Spesh

---

### Post by talrasha on 2006-08-24
This tutorial is nice.
I can't wait on trying this until I completely finished my Drapper server setup.

I just want to try this art skills coz I'm not into designing desktop themes. This one motivates me. Good work! :D

---

### Post by hoagie on 2006-09-06
Really nice guide, now I have a wonderfull desktop, thanks to you. Thanks alot

---

### Post by Perfect Storm on 2006-09-21
updated added link to XGL and compiz.

---

### Post by Marsan on 2006-09-21
Nice howto :D Can i suggest u take a look at kiba-dock? It`s the best dock i have tried. You should add that in your howto imo :D

---

### Post by _simon_ on 2006-09-22
I can't drag any desklets below approx half way of the screen. They shake a lot and refuse to move any lower.

I'm using XGL and compiz.

Any ideas?

---

### Post by Perfect Storm on 2006-09-22
The current version of gdesklets doesn't work with compiz and XGL.

---

### Post by Dinerty on 2006-09-23
Thanks for this guide, got my desktop looking very proffessional, thanks for this brilliant guide **Artificial Intelligence**

---

### Post by Dinerty on 2006-09-23
> **_simon_ said:**
> I can't drag any desklets below approx half way of the screen. They shake a lot and refuse to move any lower.

I'm using XGL and compiz.

Any ideas?

If you have a seperate gnome session:

Have excatly the same annoying problem, one way I found which works "sometimes", is to boot into a normal gnome session (without xgl/compiz) and place gdesklets where you want them, then log into xgl/compiz and pray there are there. Has worked quite a few times for me

EDIT: Sorry for double post, this can be merged with my other one, it's getting late :(

---

### Post by bugz0r on 2006-09-23
What are the themes and such in each of the screenshots?

---

### Post by Perfect Storm on 2006-09-24
GTK2/metacity: D3a
Icon theme: D3a

---

### Post by Perfect Storm on 2006-10-19
Tested in Edgy....works on Edgy.

---

### Post by jhenager on 2006-10-19
> **henrypootel said:**
> Another Great Tip.
Ubuntu is starting to make XP look decidedly 'rustic'(see also: butt ugly).
Thanks

Same with cutting edge Vista :p :-D

---

### Post by Perfect Storm on 2006-10-21
updated:
Cleaned up in advance eyecandy
added link
removed obsolited links.

---

### Post by noktekniq on 2006-12-12
this is soome cool tricks

---

### Post by hotbrainz on 2006-12-20
thanks for the excellent HOW-To Artificial Intelligence. Really nice stuff.

Just one thing. When putting a new panel from gdesklets with the minimised windows in it, it is a major hassle to move it around. Everytime i do that ... windows open up and i cant do the positioning properly.

---

### Post by Aaron Whisman on 2007-01-15
Hey, thanks for those. Do you, by any chance, know how to put web content onto the Gnome desktop? I want to put my Xbox Live Gamercard on there and it's possible in Windows but I can't seem to find how to insert web content onto the GKT desktop. [This is the Xbox website with how to do it on Windows.]("http://www.xbox.com/en-US/myxbox/desktopgamercard.htm")

Thanks if you can help please.

---

### Post by Aaron Whisman on 2007-01-16
Please, anyone at all know? I really would love to have my gamercard on my desktop...

---

### Post by Perfect Storm on 2007-01-17
Sorry, don't know.

I can advise you to make a new thread about it.

---

### Post by NoWhereMan on 2007-01-17
if that card is an rss you can use a gdesklet for that

---

### Post by Mazehero55 on 2007-01-23
the gDesklets site isn't working form me, So I can't find any gdesklets to install from anywhere. is this a bad link or something. it says permission denied.

---

### Post by jeyaganesh on 2007-02-01
Very helpful thread. I changed my desktop into eyecatching environment. Thank you very much.:D

---

### Post by wxnker on 2007-02-09
> the gDesklets site isn't working form me, So I can't find any gdesklets to install from anywhere. is this a bad link or something. it says permission denied.

[http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)

---

### Post by Nikron on 2007-02-09
[http://gdesklets.org/]("Offical new gdesklets site I believe.")

Side note:  gdesklets doesn't really work well with beryl

---

### Post by adam.tropics on 2007-02-17
I use this on my Gnome install and it's a great guide, thanks.

I am having a play with kde, and I was wondering if there happens to be any Kubuntu users here who might know the equivalent for the symbolic links in the guide that keep root themes etc consistent with your user....as below.

```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

---

### Post by establishment on 2007-07-12
Extremely helpful guide! Bravo! :)

---

### Post by boob11 on 2007-09-03
thanks

---

### Post by Depressed Man on 2007-09-16
Any idea where to get new panels (or plugins for panels). Or are the ones that shipped with Gnome all the panels there are?

---

### Post by AnasGul on 2007-09-23
Sorry, how can i delete this.
I can find only "edit"

---

### Post by breakerr on 2007-09-23
This a very helpful topic....THAKS a lot, I just wanted to ask something....after playing so much with the desktop and all those settings in case that for any X reason I have to get back to my usual Gnome interface and get to defaults without clicking swtching and flying around how could I or we set panels to defaults...I mean is there a command or something to make all get back to the first confirguration from when you first  installed ubuntu.

right now I cant get my panel to show me the little icon with 2computer monitors together showing that I'm connected to internet and also cant find the way to make gaim or any other apllication show in the systray as it was before...apparently I changed something and know I don't know how to fix it.

THANKS A LOT FOR THIS WONDERFUL THREAD

---

### Post by betawind on 2007-10-05
Would anyone happen to have the d3a theme by chance?  I've searched high and low for it to no avail.

---

### Post by Perfect Storm on 2007-10-05
It have been taken down. Try go to the art forum of this board and ask if anyone have a copy of it.

---

### Post by betawind on 2007-10-05
> **Artificial Intelligence said:**
> It have been taken down. Try go to the art forum of this board and ask if anyone have a copy of it.

Wouldn't happen to have a copy of it lying around?  Hehehe.  I'll check there.

EDIT: Yeah..I apparently can't read.

---

### Post by Perfect Storm on 2007-10-05
Nope, I don't have it anymore. Been 2 years since I last used it.

[http://ubuntuforums.org/forumdisplay.php?f=16](http://ubuntuforums.org/forumdisplay.php?f=16)

---

### Post by silvar on 2007-10-08
ok i've followed the instructions at the beginning of this thread, got everything to work fine, but there was a bit of flickering etc, so i stopped using beryl, uninstalled, but now have problems.

i was using a dark theme before and did the thing that makes a symbolic link between themes/icons etc on ur desktop, and the ones used in programs.

since removing beryl and switching to a light theme, my main menu, drop down boxes and main menu in firefox are all the wrong colour.
(main menu - black, firefox drop boxes - black, firefox top menu bar text - white)
screens:

[IMG]http://www.britishbombing.com/images/ffox.png[/IMG]
[IMG]http://www.britishbombing.com/images/menu.png[/IMG]

---

### Post by goonies on 2007-10-13
```
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_3/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_3/prefs/num_rows' stores a non-schema value
```

I am getting the following error after removing LTPager and trying to reload the default gnome workspace switcher.  Anyone have any idea whats going on here and how can i fix it?

---

### Post by NoVista on 2007-10-30
If i follow the guide on page 1, with regard to changing my root theme, does that still work for Gutsy, and are there any drawbacks to it?

---

### Post by Genotrius on 2007-11-12
on Gusty; I can't seem to get gcursor to do it's job- pressing the Install button does nothing. Just, nothing.

---

### Post by Phiber_tek on 2007-12-06
> **henrypootel said:**
> Another Great Tip.
Ubuntu is starting to make XP look decidedly 'rustic'(see also: butt ugly).
Thanks


Alright so this may be from 2 years ago none the less, Ubuntu is now making Vista look 'rustic' lol this is amazing something free looking, feeling, and for me being more stable then the biproduct of a bureaucratic $300 piece of software hmm...

---

### Post by faical117 on 2007-12-20
wow thanks :-)

---

### Post by marekj7 on 2008-09-10
> **Genotrius said:**
> on Gusty; I can't seem to get gcursor to do it's job- pressing the Install button does nothing. Just, nothing.

It's a bug in gcursor [https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491]("https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491") All of buttons is not working...

I have repaired it. Here is a .deb package: [http://ubuntu.marcik.cz/gcursor-bugfix.deb]("http://ubuntu.marcik.cz/gcursor-bugfix.deb")

Installing:
[PHP]dpkg -i gcursor-bugfix.deb[/PHP]

With regards, Marcik

---

### Post by Jackp90 on 2008-10-25
Thank you i was wondering how to do alot of what you just said and then there was some more that i am going to try . . .

Thanks again

---

### Post by NipplesAndLicks on 2009-05-04
when i open Xcursors it wont let me click install or go to theme?

and when i GNOME splash screen it will let me go to the file then it closes and help?

---

### Post by ReyPorUnDia on 2009-06-30
WOW!
Great Topic, Added to my favs!

---

### Post by cjmabry25 on 2009-08-06
This is a great guide. I'm doing some of these right away. Thanks so much!

---

### Post by hyperddude on 2009-09-23
That's weird, I don't have a theme button. I go to System > Preferences , and then there's no theme.

EDIT: Ohhhh it's appearances for me, not theme. Gah. Sorry.

---

### Post by Fancycakes on 2009-10-15
> **Artificial Intelligence said:**
> Updated the howto:

Added: Howto install cursor themes on ubuntu/gnome.


I installed gcursor and I changed the cursor, but it' switches back to the default cursor when I move the cursor outside of windows, like the status bar or the desktop.

Is this a normal thing that I'll just have to live with or is there something I'm just not getting?

---

### Post by Perfect Storm on 2009-10-15
> **Fancycakes said:**
> I installed gcursor and I changed the cursor, but it' switches back to the default cursor when I move the cursor outside of windows, like the status bar or the desktop.

Is this a normal thing that I'll just have to live with or is there something I'm just not getting?

Try logout and login again.

---

### Post by Fancycakes on 2009-10-15
Oh, there we go. Thanks a bunch. I really loved the walk-through.

---

### Post by Perfect Storm on 2009-10-15
It's very old and lot have changed since.

---

### Post by faical117 on 2009-10-16
thanks but gcursor not working well i can't change or add any cursor :(

---

### Post by vault55 on 2009-12-20
[IMG]http://s454.photobucket.com/albums/qq261/clintnatx/[/IMG]

[SIZE=3]I've searched the depths of the net to find this cursor and cant seem to locate it.  Does anyone know what its called and where I can get it?  It glows particles similar to fire and trails some with the cursor.  It looks to be aesthetically pleasing as well as functional.  Thanks[/SIZE] 

I originally found the video on youtube when searching for WINE [http://www.youtube.com/watch?v=jlO_aAb1CMI](http://www.youtube.com/watch?v=jlO_aAb1CMI)

---

### Post by Rambo III on 2010-09-11
[COLOR=DarkRed]**Thanks alot**[/COLOR]

---

