---
title: "HOWTO: Functional eyecandy for GNOME with Compiz Fusion"
date: 2007-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by smartboyathome on 2007-07-03
[CENTER][COLOR="Navy"][SIZE="4"]**_My first Guide for Ubuntu, I hope you like it. :)_**[/SIZE][/COLOR][/CENTER]

I have been trying to create an eyecandy desktop on my GNOME desktop for a long time. I finally got a break when Compiz Fusion was released, and many new effects were featured. Now, I also like to keep it organized (as I work on the desktop as well) so these are (to me) great for showing off to your friends AND working.

A preview of some of the stuff I will teach you to install and use in this guide (you will even get to make your GNOME Panel like mine!):
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=37155&stc=1&thumb=1&d=1183421754[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=37155&d=1183421754")
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=37156&stc=1&thumb=1&d=1183421754[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=37156&d=1183421754")

***DISCLAIMER:** Compiz Fusion is still in alpha, and I would recommend you stay away from it until it becomes stable. This guide is for those who still want to use it, even with all the bugs.*



Table of contents:
1. Install Compiz Fusion
2. Configure Compiz Fusion
3. Ready the desktop for Avant Window Navigator
4. Install Avant Window Navigator
5. Configuring Avant Window Navigator
6. Install Screenlets
7. Start & Add screenlets
8. Make these programs start at startup
9. Making your gnome bar more compact (and making it autohide better)



**_1. Install Compiz Fusion_**
[INDENT]I feel no need to repeat what someone else has done, so I will just direct you to Vorian's thread on how to install Compiz Fusion:
[http://ubuntuforums.org/showthread.php?t=481314]("http://ubuntuforums.org/showthread.php?t=481314")[/INDENT]



**_2. Configuring Compiz Fusion_**
[INDENT]When you first get compiz fusion, there will not be a lot of stuff enabled. Here, I will show you some stuff that I find useful when enabled.
To configure Compiz Fusion, open the CompizConfig Settings Manager via System > Preferences > CompizConfig Settings Manager. You can navigate to different catigories by using the catagory layout on the side.
You can now customize Compiz Fusion! I would play with some of the settings. Here on some tips on configuring some of the useful ones (I would look in the actions tab for every one mentioned to get to know how they work):
[LIST][*]The first thing to do is to make sure the wall plugin is on. You can do this by checking the checkbox next to its name (leave it checked if it is), which is in the desktop catigory. It may tell you "x uses the same plugin, are you sure you want to disable it?", click ok for this. This is useful for dragging windows from one workspace to another. When you want to show Compiz Fusion off to your friends, simply check the checkbox next to Rotate Cube (in the Desktop Catigory) and Cube Reflection (in the Effects catigory).
[*]Next, in the Desktop catagory, make sure the Expo plugin is checked. This makes it easier to move multiple windows between workspaces easily.
[*]Go to the window management catagory and check to make sure Place Windows is checked, and uncheck Snapping Windows if it is checked. Go inside Place Windows (by clicking on the name) and make sure Workarounds is checked and Placement Mode is set to Smart. This will make it so that your windows will not open under your GNOME panels.
[*]In the same catagory (Window Management) check the checkbox next to Group and Tab Settings. This enables you to "combine" windows in a tab-like effect. Go inside the plugin, and click on the Actions tab. Set the key bindings to whatever you want (something that will be easy to remember). I used Alt+Super+C for changing the glow color, and left everything else as default.
[*]Now, in the same catagory as the last two, check the checkbox next to Ring Switcher (I find this more useful then the Application Switcher) and uncheck the Application Switcher. Now just use the default settings to switch windows (you can switch Super+Tab to Alt+Tab in the Actions tab if you want).
[*]If you play a lot of video, you may want it to play while you are using these effects. To do this, go to the Utility catagory, and make sure Video Playback is checked.
[*]Window Previews allows you to preview a window by hovering over its slot in the Window bar. To enable this, check the box in Extras.
[*]If you do presentations (or would like to present parts of your desktop to an audience), you can enable the Annotate plugin (in the extras catagory) by checking its checkbox.
[*]If you are using this to show off to your friends AND using it to do work, you may want to have separate profiles for each setting. To do this, click Backend & Profile (in the bottom left corner). Then, Export your profile and give it a name. Make a new profile (give this one a name, too) and explore compiz fusion with no fears of loosing your settings! When you want to get back to your old profile, simply click default in this same window, and all the settings you set up are restored.
[*]You can change the number of desktops to another amount than the default 4. This will also solve problems where you only have 2 desktop and a plane to switch between them. To change it, open up CompizConfig Settings Manager, and choose General options. Now, choose the Desktop Size tab. Change horizontal size to the number of desktops you want to see, and change vertical size to change the number of rows that the desktops are shown in.[/LIST][/INDENT]



**_3. Ready the desktop for Avant Window Navigator_**
[INDENT]Avant covers the bottom panel, so to use it, you may want to follow the instructions in this section.
First, delete your bottom GNOME panel by right clicking it and selecting "Delete panel". Since this contains your Show your desktop and Workspace Navigation, we will add those to the bar by right-clicking the top panel and clicking "Add to panel". Now, add the Workspace Switcher and Show your desktop items to wherever you want on the panel.[/INDENT]



**_4. Install Avant Window Navigator_**
[INDENT]Avant Window Navigator is a dock like OSX, and a good one at that. To install it, simply type (in a terminal) (it is in the same repo as Compiz Fusion for Feisty):
```
sudo apt-get install avant-window-navigator
```
Now, you can start Avant by going up to Applications > Accessories > Avant Window Navigator. You can change the preferences for it by either right-clicking the open bar or going to System > Preferences > Avant Preferences.[/INDENT]



**_5. Configuring Avant Window Navigator_**
[INDENT]To configure Avant, first right click it, and select Preferences. Here, you can configure Avant. I don't like the border for Avant Window Navigator, so I turned it off by setting the opaque to 0 and color to white (do this by going to Bar Appearence tab and changing the both the main and internal corners). Now, you can change the colors of the bar itself by going to Glass engine and changing the gradients and changing them. I find that using the same (or similar) color(s) but changing the opacacy (for mine, I used HEX #454545 color and opacity level 125 for the first step color and HEX #000000 color and opacity level 224 for the second step color, which gives it a smooth 3d look).
Now, to add the trash can to the bar, right-click Avant and click Configure applets. Now, click the add button and add the trash applet. Now, the trashbin should show up. You can now drag items onto it or right click > empty it (or click it and open the trash can). I have not had sucess with the Notification bar or Workspace switcher (the applets are still in early development).
To add launchers to Avant, simply drag the item from the applications menu (or settings menu) to the dock. When you start one of these launchers, the launcher will convert into a window icon, and the triangle underneith will dissapear. You can now use the window like a normal window on the dock. PLEASE NOTE: you can only do this with items in the menus, and not with custom launchers.[/INDENT]


**_6. Install Screenlets_**
[INDENT]Screenlets are little programs that sit on your desktop. Since we are using Avant, we will have to use the development repository for installing the screenlets (if you don't, you will have errors with Avant).

To install them, add the following line to your sources.list:
```
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets
```
and execute the following in a terminal:
```
wget http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install screenlets
```

You now have screenlets installed. You must do a quick restart (CONTROL + ALT + Backspace) in order to see the icon in the Applications > Accesories menu.[/INDENT]



**_7. Start & Add Screenlets_**
[INDENT]To start screenlets, click on the icon in Applications > Accesories. A tray application will start up. To get screenlets, right click it, and click Add ControlScreenlet. Now, right click the screenlet that comes up and add your screenlets from there. You can customize any screenlet by right clicking on that screenlet.[/INDENT]



**_8. Make these programs start at startup_**
[INDENT]To make these programs start at startup is not that hard. To do this, you will need to open the session manager via System > Preferences > Session.

To add Compiz Fusion to the startup, make a new entry with this as the command:
```
compiz --replace
```
or (if you use the emerald theme manager)
```
compiz --replace -c emerald --replace
```

To add Avant Window Navigator to the startup, make a new entry with this as the command:
```
avant-window-navigator
```

To add Screenlets to the startup, make a new entry with this as the command:
```
screenlets-tray
```[/INDENT]



**_9. Making your gnome panel more compact (and making it autohide better)_**
[INDENT]To make your gnome panel more compact, first delete the Applications/Places/System menu and add the main menu. Then, delete any launchers. Now, right click the panel and click properties. Uncheck Expand and check autohide.
Next, to fix the autohide option, use this guide:
[http://ubuntuforums.org/showthread.php?t=170864](http://ubuntuforums.org/showthread.php?t=170864)[/INDENT]

I hope this howto helps you! Please post your problems, and I will try to help you!

**_Changelog:_**
07-04-07: Fixed some typos and added how to change the number of desktops for Compiz Fusion.

---

### Post by oliverb4ss on 2007-07-04
Thanks for the great tutorial, I really love to look and feel of my desktop now!

But I still have a problem with adding launchers to the window navigator.

After pressing configure launchers the windows dialog comes up, but when clicking "Add" it does nothing, it doesn't freeze, not anything.
Dragging applications onto the launchers dialog window doesn't do anything, either.

Any suggestions?

---

### Post by kushelmex on 2007-07-04
very good job!!

---

### Post by AndrewGene on 2007-07-04
> **oliverb4ss said:**
> Thanks for the great tutorial, I really love to look and feel of my desktop now!

But I still have a problem with adding launchers to the window navigator.

After pressing configure launchers the windows dialog comes up, but when clicking "Add" it does nothing, it doesn't freeze, not anything.
Dragging applications onto the launchers dialog window doesn't do anything, either.

Any suggestions?

...same problem

---

### Post by smartboyathome on 2007-07-04
Launchers can only be added if it was automatically added to the applications or system menu. Is this where you are dragging from?

---

### Post by oliverb4ss on 2007-07-04
I have the launchers dialog right in front of me and I drag the application from the menu.

E.g. Main Menu -> Accessories-> Terminal

I drag it straight from the applications menu and nothing happens.

---

### Post by smartboyathome on 2007-07-05
that is really weird. Try running it in a terminal and see if there is any output. Alternatively, you could try to right click > configure launchers (which doesn't always work).

---

### Post by mrgnash on 2007-07-05
Thanks for this guide :) Just a couple of questions though:

Is it possible to configure Compiz-Fusion so that it rotates the cube when you roll the mousewheel while hovering the cursor over any empty space on the desktop?

Secondly, is it also possible to view all open windows by hovering the cursor in the top right-hand corner of the screen (a-la Beryl)?

---

### Post by smartboyathome on 2007-07-05
> **mrgnash said:**
> Thanks for this guide :) Just a couple of questions though:

Is it possible to configure Compiz-Fusion so that it rotates the cube when you roll the mousewheel while hovering the cursor over any empty space on the desktop?

This has not been implimented yet, but once it is implimented, it will be available through the "Viewpoint Mouse Switcher".

> **mrgnash said:**
> Secondly, is it also possible to view all open windows by hovering the cursor in the top right-hand corner of the screen (a-la Beryl)?

This should already be available by default. I tried it with a fresh profile (which sets the settings back to default) and it works still.

---

### Post by oliverb4ss on 2007-07-05
When running in terminal, dragging launchers works perfectly, but the "Add" button still doesn't do anything.

Thanks for your help :)

---

### Post by smartboyathome on 2007-07-05
Welcome! And like I said before, the add button doesn't always work, since that feature is still under development.

---

### Post by oliverb4ss on 2007-07-06
Another quick question.

I do get updates on the window navigator through the update manager when they are available, don't I?

I should, because I installed it through apt-get.

Just asking to be sure :)

---

### Post by yang2iu on 2007-07-06
```
$ wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add - && sudo apt-get update
--16:23:52--  http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
           => `-'
Resolving hendrik.kaju.pri.ee... failed: Name or service not known.
gpg: no valid OpenPGP data found.

```

that's what I got when I was trying to install screenlets
=/

---

### Post by anandanbu on 2007-07-06
Thanks for such a wonderful guide :)

---

### Post by smartboyathome on 2007-07-06
> **oliverb4ss said:**
> Another quick question.

I do get updates on the window navigator through the update manager when they are available, don't I?

I should, because I installed it through apt-get.

Just asking to be sure :)

You use the Ubuntu Update Manager? If so, then you would get it as normal through the system tray (notification area).

> **yang2iu said:**
> ```
$ wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add - && sudo apt-get update
--16:23:52--  http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
           => `-'
Resolving hendrik.kaju.pri.ee... failed: Name or service not known.
gpg: no valid OpenPGP data found.

```

that's what I got when I was trying to install screenlets
=/

I cannot reproduce the error. Please make sure you are connected to the internet while doing this. Other than that, I do not know.

---

### Post by anandbhushan on 2007-07-07
this was a great guide. very newbie friendly. were u able to get screenlets to work as a widget (Compiz fusion + F9) like the dashboard feature on OSX. i've had no luck thus far. works occasionally. most of the time screenlets dissapear when i click "treat as widget" and with the widget plugin enabled on compiz fusion.

---

### Post by smartboyathome on 2007-07-08
I have not tried this feature, as I have had no need to. I would not know what you are talking about, as I have not used the dashboard on OSX. Maybe someone else could help? :-\

---

### Post by DC@DR on 2007-07-08
I can't wait till Compiz/Fusion to be stable. Damn, it must be awesome. Btw, thanks for the HOWTO :-)

---

### Post by smartboyathome on 2007-07-08
Welcome! :)

---

### Post by smartboyathome on 2007-07-09
See the first post for any updates concerning this guide.

---

### Post by Matuku on 2007-07-12
At the top right of my screen shot you can see that the bars you click to drag are grey; how can I change the colour of these? I just can't think which options it would be under.

EDIT Its also the colour on the desktop thing in the bottom right; I would like to change all of them.

---

### Post by smartboyathome on 2007-07-12
> **Matuku said:**
> At the top right of my screen shot you can see that the bars you click to drag are grey; how can I change the colour of these? I just can't think which options it would be under.

EDIT Its also the colour on the desktop thing in the bottom right; I would like to change all of them.

I would suggest you look at your GTK theme's file. I would nott know how to change that (since I don't need to customize my GTK theme) but you can probably find a good guide on these forums.

---

### Post by krimson on 2007-08-11
im getting a 404 error when trying to get to your key file.

---

### Post by smartboyathome on 2007-08-12
Is this for the screenlets repo? If so, that repo is down now.

---

### Post by maduranga on 2007-08-13
thanks. i got them working. and i got screenlets installed by giving the same command until all needed packages are fully downloaded. now they work perfectly. thanks :)

---

### Post by dmlc133 on 2007-08-16
Hi

Thanks for this, I've been trying to find a good write up of compiz configuration options since starting with Ubuntu - my desktop is much improved.

Now, I realise this may be a stupid question, but in the CompizConfig Settign Manager it refers to a Super option in lots of places - what does this actually mean? Is there any documentation anywhere about all the options as the settings manager doesn't really say much about them.

I have a minor issue: I followed the installation guide in the linked forum topic, and since installing compiz fusion my update manager constantly shows there is an update for compiz-core available - however it has the same version name (1:0.5.2-0ubuntu2~ppa1) as the installed version, and when I install it nothing happens (i.e. it's still there in update manager). Any idea what is going on?

Thanks again

---

### Post by smartboyathome on 2007-08-17
> **dmlc133 said:**
> Hi

Thanks for this, I've been trying to find a good write up of compiz configuration options since starting with Ubuntu - my desktop is much improved.

Now, I realise this may be a stupid question, but in the CompizConfig Settign Manager it refers to a Super option in lots of places - what does this actually mean? Is there any documentation anywhere about all the options as the settings manager doesn't really say much about them.

This refers to (usually) your windows key on a PC and (sometimes) the command (apple) key and sometimes the alt key on macs.

> **dmlc133 said:**
> 
I have a minor issue: I followed the installation guide in the linked forum topic, and since installing compiz fusion my update manager constantly shows there is an update for compiz-core available - however it has the same version name (1:0.5.2-0ubuntu2~ppa1) as the installed version, and when I install it nothing happens (i.e. it's still there in update manager). Any idea what is going on?

Thanks again

I would not know how to fix this (i haven't been getting the error myself), but you might want to post a topic about it in the general help forum. One thing I would try is clicking the "check for updates" button one the update manager opens and seeing if that helps (that re-checks your installed packages with those in the repos).

---

### Post by isaacj87 on 2007-08-17
> **dmlc133 said:**
> 

I have a minor issue: I followed the installation guide in the linked forum topic, and since installing compiz fusion my update manager constantly shows there is an update for compiz-core available - however it has the same version name (1:0.5.2-0ubuntu2~ppa1) as the installed version, and when I install it nothing happens (i.e. it's still there in update manager). Any idea what is going on?



This is a problem they're currently having and they're working on fix. But, until the fix...there isn't anything you can do. I guess if the update manager icon really annoys you (like it does me) you can go into synaptic and lock it...then the notification icon will go away.

---

### Post by dmlc133 on 2007-08-17
Cheers for the replies guys

I have an old Compaq keyboard that has neither the WIndows key nor the Apple key. I swear I've pressed everything looking for the "Super" key! Guess I'm going to have to reconfigure all those shortcuts!

---

### Post by dmlc133 on 2007-08-17
OK one last question

When I try to get compiz and avant to start automatically, I don't see System > Preferences > Session I have System > Preferences > Sessions (similar I know) and it won't save my additions - how can I make it remember the new settings?

Thanks

---

### Post by staib on 2007-08-18
I often need help with installs and graphics issues but I just thought I would mention that this time all went very smoothly and Compiz Fusion is now running impressively and seems perfectly stable so far.   So a big thanks for taking the trouble to explain how the set-up works. A great helpful guide :-)

Nick

PS - Oh wait - there was one question - LOL - when running VLC in full screen mode there is now some unwanted transparency - how can I get rid of that?!

---

### Post by smartboyathome on 2007-08-20
> **dmlc133 said:**
> OK one last question

When I try to get compiz and avant to start automatically, I don't see System > Preferences > Session I have System > Preferences > Sessions (similar I know) and it won't save my additions - how can I make it remember the new settings?

Thanks

Hm... sometimes the setting manager's GUI has problems with Compiz running. Have you tried it with Metacity? What about restarting? I am not currently using GNOME right now (trying to reconfigure Xubuntu for a friend to make it lighter) so I will not be able to help any more than this. :(

---

### Post by absolut352 on 2007-11-02
Does anyone know why my themes have this gradient in the titlebar instead of matching the current selected theme? I have emerald set as theme manager and i have played with settings in the edit theme section and tried different engines and it only seems to get worse.

---

### Post by smartboyathome on 2007-11-02
I think that border is set by the theme. What engine does it use?

---

### Post by absolut352 on 2007-11-02
You can see which engines are used next to the theme in emerald. See the screenie i took.  In feisty the themes looked the same as the included screenshots u see in theme settings. Now in gusty see how my titlebar looks nothing like the selected theme? Ive made no changes but id like to get make my titlebar look like the selected theme.

---

### Post by russ_armst on 2007-11-03
It seems the Gutsy repos are back up, see [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) and follow instructions. 

Russell.

---

### Post by smartboyathome on 2007-11-03
> **absolut352 said:**
> You can see which engines are used next to the theme in emerald. See the screenie i took.  In feisty the themes looked the same as the included screenshots u see in theme settings. Now in gusty see how my titlebar looks nothing like the selected theme? Ive made no changes but id like to get make my titlebar look like the selected theme.

Is this on Gutsy? If so, I think the screenshot was made on Emerald with Beryl, and I think Emerald changed somewhat with coming to compiz fusion. I will look up the theme you have and see if it reacts in the same way as your screenshot. :)

> **russ_armst said:**
> It seems the Gutsy repos are back up, see [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) and follow instructions. 

Russell.

Thanks, I will add that it is back up to my HOWTO. :)

---

