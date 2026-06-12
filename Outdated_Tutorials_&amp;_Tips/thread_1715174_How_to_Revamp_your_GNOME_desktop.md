---
title: "How to: Revamp your GNOME desktop"
date: 2011-03-26
forum: Outdated Tutorials &amp; Tips
---

### Post by adam22 on 2011-03-26
I've had a few requests for this, so I am gonna go ahead and write up the tutorial for this.

We all know what the standard desktop looks like. You have the double panels on the top and the bottom, the plain looking icons and toolbars, and a standard background. People like to use the included themes to give a more personal touch, but there's so much more you can do. Here is what my desktop currently looks like:

_[[IMG]http://img812.imageshack.us/img812/5387/screenshotws.th.png[/IMG]]("http://img812.imageshack.us/i/screenshotws.png/")_

Let's begin:

First thing is first, you're going to want to grab yourself a nice wallpaper. While you can grab one from a source of your choice, I often turn to [Gnome-look]("http://www.gnome-look.org"). On the left you will see wallpapers, just go ahead and click that. You can sort by various subcategories like 'highest rated' or you can just type in what you are looking for. When you find your wallpaper, just click the **download** button and a larger image that will fit your screen resolution should appear. You can just apply this as your wallpaper by using the right-click>Set As Desktop Background, but I prefer to save the images as you never know when they will be taken down. I have uploaded my background (I can't find the original URL) [here]("http://img717.imageshack.us/img717/60/spacev.jpg"). Note that many of the themes you download may come with their own background you can elect use, including the theme I use below.

Now, it's time to grab a new theme. Once again we're going to turn to Gnome-Look and use a theme from there. [Here]("http://gnome-look.org/content/show.php/Aero+Space?content=113553") is the Aero Space theme I am currently using. To apply this theme, click the download button and save the .tar.gz to the desktop (or a directory  of your choice). *Right-Click* the file and choose **extract here**.  A file will be placed on your desktop, labeled Aerospace. Now, open up  your Display Menu, in Ubuntu do this by selecting  System>Preferences>Display. Simply drag the gtk theme file into the  window (make sure the theme tab is selected) and then choose apply new  theme. You may get a warning saying you do not have the matching icon  package, but you can disregard that.

[U][[IMG]http://img859.imageshack.us/img859/6756/screenshotz.th.png[/IMG]]("http://img859.imageshack.us/i/screenshotz.png/")
[/U]
We aren't done with the themage yet though. You're going to need the Emerald Theme Manager for this part, and you can get that by opening up Synaptic Package Manager and searching for Emerald, and installing the main package with any dependencies.

[U][[IMG]http://img11.imageshack.us/img11/681/screenshotgd.th.png[/IMG]]("http://img11.imageshack.us/i/screenshotgd.png/")

[/U]
Now go to System>Preferences>Emerald Theme Manager. After ETM opens up, click **import** and bring in one of the Emerald themes in the Aerospace>Emerald directory.

[[IMG]http://img691.imageshack.us/img691/5504/screenshot1lu.th.png[/IMG]]("http://img691.imageshack.us/i/screenshot1lu.png/")

Now, here is what I have done. I **removed** the top panel, which can be done by right clicking and then clicking _Delete This Panel_. I then **resized** the bottom panel. To do this, right-click the bottom panel and then hit *Properties* and change the size to **32 pixels**. The next panel customization is to change the background. This is easily done by going back into the Properties menu for the panel and then selecting the **background** tab. Hit _background image_ and select one of the backgrounds in your Aero Space folder. I selected the **Moretransparent** image.

[[IMG]http://img51.imageshack.us/img51/8923/screenshotfzr.th.png[/IMG]]("http://img51.imageshack.us/i/screenshotfzr.png/")


Now we need a good icon package, the default ones just do not cut it  for me. Once again head over to Gnome-Look and on the left you will see  _Icons_. You can browse through these and sort by the 'Most  Downloaded' for the most popular themes. I use the 'Black-White 2 Gloss'  theme, but the download directs you to Deviant Art. Go [here]("http://dbgthekafu.deviantart.com/art/black-white-2-Gloss-73274930") and click the download link is on the left. Save the .tar file to the desktop and then **Right-Click** and select **extract here**.  Open up the file and then you will see a .tar.gz and a ReadMe. Extract  the .tar.gz and a new folder should appear. You need to drag this file  into the appearance window and then click to apply theme now.

[[IMG]http://img12.imageshack.us/img12/6057/screenshotie.th.png[/IMG]]("http://img12.imageshack.us/i/screenshotie.png/")

The next thing is to get a new application launcher. You can choose a dock like the 
Avant Window Navigator, but I prefer to use GnoMenu. The easiest way to install that is to grab the latest .deb [here]("http://www.getdeb.net/software/GnoMenu"). You may have to reboot in order to see the launcher, but to apply it to the panel, right-click and select _Add to Panel_ and select GnoMenu. If you right click the icon for it and click 'Move' you will be able to move it over to the bottom left corner.

[[IMG]http://img163.imageshack.us/img163/8461/screenshotkhm.th.png[/IMG]]("http://img163.imageshack.us/i/screenshotkhm.png/")

You can customize GnoMenu by adding favorites (just right click an application in the menu and select 'add to favorites' and also by changing themes, which can be found at Gnome-Look. You can also change the button and any installed themes by right clicking the GnoMenu button and selecting *Properties*. I'm using the default Vista theme that comes with GnoMenu.

*Note: You may have to replace the theme manager with emerald by hitting alt+F2 and typing **emerald --replace**. This will have to be done every time you reboot though, so in order to prevent this go to System>Preferences>Startup Applications and click **Add**. Add the command _emerald --replace_ and name it whatever you like, and save your changes.*

[[IMG]http://img88.imageshack.us/img88/9738/screenshotpgm.th.png[/IMG]]("http://img88.imageshack.us/i/screenshotpgm.png/")

The last thing is to add a few more personal touches of your choice. I like to use **Screenlets** which are similar to the widget programs you often see on Windows desktops. Simply go to the Synaptic Package Manager and search for 'Screenlets' and install the package. 

First, let's get the system monitor up and running. Click SysMonitor and then on the left tick **Start/Stop**. I also tick **Start on login**. You can drag the system monitor to anywhere you like and if you right click, you can change the theme for it, the size, and if you select properties a menu will pop up. This allows you to modify what the screenlet will show and how big it is as well as how it looks. *Each screenlet will have a properties menu allowing it to customize as you see fit. Also, if you right-click and select window, you can choose to lock the screenlet and you want to select **keep below** so it does not interfere with any windows you have open*. 

This is the only screenlet I am currently using, but as you can see there are several of them that are included with the program. If you want more, you can use the 'Get More Screenlets' button in the screenlets daemon, or you can go to Gnome-Look. It is easy to install a third party screenlet, the general procedure is:

Save the .tar.bz2 (or similar file) to your machine. Extract and the [your screenet's name here] folder will appear. Now, open up your Home folder and select View>Show Hidden Files and scroll down to the .screenlets directory. Drag the new screenlet folder into that and close the window. Now open up the Screenlets Daemon and you should see the newly installed one listed. Launch it and through the properties you can customize it to your liking.

You can also add several different things to your panel. I have added the **CPU Frequency Scaling Monitor** and the **Main Menu**. Just like for the GnoMenu launcher, you just have to right-click the panel and hit 'Add to Panel' and select from the various items.

And that's it. You just gave your desktop a big refresher. The emerald theme will provide some new little features (hover over one minimize, maximize, or close buttons, or double click the window pane to see what I'm talking about) and you now have the tools and knowledge to create whatever desktop look you desire. Have fun!

---

