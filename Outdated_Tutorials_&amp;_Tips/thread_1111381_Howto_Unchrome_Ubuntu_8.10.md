---
title: "Howto: Unchrome Ubuntu 8.10"
date: 2009-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by chuckmoney on 2009-03-30
The following is a copy & paste of my own blog post [here]("http://chuckslist.blogspot.com/2009/03/howto-unchrome-ubuntu-810.html").  Please visit and leave a comment there, or just here, if you like my work.  I'm not going to re-add the links here, so visit my blog if you need those but if someone else wants to post them as a reply here feel free to.  Enjoy.

Ever since I read the powerpoint-like slideshow for the beta of Google Chrome, I've been infected with some kind of bug that makes me want to oversimplify every program on every operating system that I use. A browser should be about the web pages, not the browser. An emai aclient should be about the email, not the client. A window manager should be about what's in the windows, not switching between them. Anything and everything should be about the content itself, not the method used to present it. In that spirit, I'm wiriting this guide as a sort of step-by-step tutorial on how to minimize the amount of extrainious junk eating precious screen real estate, and maximize the number of pixels dedicated to what you actually want to see, in Ubuntu 8.10.

So, if you also like your system to be a mean clean focus-on-whatever-you're-actually-doing machine, try out the following steps. Please note that you should not type the quotes around any commands I give you. These are only to denote where the command starts and ends.

The first procedure is to setup the Ubuntu Netbook Remix Launchpad PPA Repository. I'd walk you through this part, but the best directions for this are here and here. Once you have access to the software that'll make this work, you're going to install the core software packages you'll need to unchrome GNOME.

[LIST=1]
[*]Open a terminal by going to Applications > Accessories > Terminal.
[*]Type in "sudo apt-get install window-picker-applet maximus" and press Enter/Return
[*]As above, if prompted, type in your password
[*]If asked a yes or no question, simply press the "Y" key then Enter/Return Some of these packages may depend upon others, so you'll have to press "Y" to install the dependencies too.
[*]BONUS STEP: If you do a lot of terminal work, you might also consider installing Tilda. You can use the command "sudo apt-get install tilda" to install it now, or add it any time later. Tilda gives you a drop-down terminal you can access with a single key press at any time, which can optionally be transparent, have a pull down animation, or tons of other unique features.
[*]Type "exit" in the terminal and press Enter/Return.
[/LIST]

Ok, now you have all you need installed, because Ubuntu includes everything else. Time to begin the conversion process!

[LIST=1]
[*]First, right click on the panel at the bottom of your screen and select "Delete this panel" and click Yes or Delete when asked to confirm it
[*]Our goal is to have a single, blank panel at the top of the screen, so next, right click each and every applet on the Panel at the top of your screen and select "Remove from panel"
[*]Once all the applets have been removed, right click on the right end of the panel and click "Add to panel"
[*]In exactly this order, click the applet listed and then click the add button:
**Lock Screen, Force Quit, Clock, Volume Control, Notification Area, Trash, Inhibit Applet, CPU Frequency Scaling Monitor, Deskbar, Window Picker, Run Application, Main Menu**
*(Note: Skip the Inhibit Applet if you're using a desktop and add a second CPU Frequency Scaling Monitor if you're using a dual core processor)*
[*]Close the Add to panel window.
[*]Go through every applet you just added, right click each one, and select "Lock to Panel"
[*]Go to Main Menu > System > Preferences > Sessions
[*]Click the Add button, and in the next window, for name, type in "Maximus" and for command type in "maximus"
[*]Click the Add Button, then the Close Button.
[*]Reboot
[/LIST]

Congrats, you just unchromed GNOME, the window manager in Ubuntu. But you're not done yet! There are a few more small tweaks you should run, and of course you can't call it unchromed until you unchrome Firefox, too!

[LIST=1]
[*]Go to Main Menu > System > Preferences > Appearance
[*]On the Theme tab, try out the Darkroom theme, which is easier on the eyes than the default Human theme and also requires less screen brightness, thus helping laptop battery life slightly.
[*]On the Interface tab, change Toolbar Button Labels to "Icons Only"
[*]Right-click your CPU Frequency Scaling Monitor Applet(s) and select Preferences. Change its/their Appearance to "Graphic" and then click Close.
[*]Right-click your Clock applet, and select Preferences. Uncheck all four boxes under "Panel Display" then click Close.
[/LIST]

Almost there! Next, we'll unchrome firefox. You can skip this procedure entirely if you like, but it helps.

[LIST=1]
[*]Use the following 4 links to install extensions into firefox: Adblock Plus, Fission, Smart Stop/Reload, and Compact Menu 2.
[*]Restart Firefox
[*]Right click on your new Stop or Reload button Linkand select "Customize"
[*]Drag the Compact Menu button to the far left side if your toolbar
[*]Drag the Adblock Plus button into the Customise window
[*]Drag the Link Activity Indicator from the top right corner down to the right of your Search box
[*]Drag the New Tab button from the Customise window just to the left of your Address box
[*]Close the Customise window
[*]Right click the Stop or Reload button again and click "Menubar" to remove it
[*]Repeat step 9 to remove the Bookmarks Toolbar unless you want to keep it.
[*]OPTIONAL: Restart firefox to be sure it all loads properly
[/LIST]

That's all! You did it! You have now totally unchromed GNOME and Firefox! If you'd like, you can try your luck at unchroming other applications, such as Evolution, Pidgin, Rhythmbox, or Transmission. If I get enough feedback from this I'll certainly write guides for those too, but for now, try this out and see how you like it.

---

### Post by dmizer on 2009-03-30
Thanks for submitting this tutorial. If you would, please take the time to post how to reverse these changes in case someone want's the "chrome" back.

---

