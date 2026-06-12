---
title: "Firefox 3.0 &amp; Animations"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by thinch on 2008-06-18
I recently installed Firefox 3.0 on Gutsy, using the good tutorial on [http://ubuntuforums.org/showthread.php?t=833036](http://ubuntuforums.org/showthread.php?t=833036), and the post by ubukool.

It works well, but my only problem is this:
The new "awesome bar"- i.e address bar with bookmarks "built-in" uses the same effects as when opening and closing program windows: "Glide 1" and "Glide 2".

When I begin typing an address in, instead of appearing quickly, like before, it fades in (and out, when selecting the correct URL). This is quite annoying, and I would like to stop it.

I presume I will have to change the settings in my CompizConfig Settings Manager, but I have no idea how to do it.
Any help would be greatly appreciated.
thinch:)

p.s: This is a repeat of another thread I accidentally posted in another section.

---

### Post by Hospadar on 2008-06-18
I would suspect (because i think firefox is drawn with GTK) that there really isn't a way to make firefox not use those effects, but the rest of your programs use them.  (which is what I'm assuming you want to do).  Probably the only real solution is to pick a different effect, or speed up that effect to what you want it to be.

I might be totally wrong on this, but I'm pretty sure that's how it is.  Maybe you could find some firefox addons that alter the behavior of the awesome bar such that it will not be affected by those effects

---

### Post by thinch on 2008-06-18
Really?  That doesn't sound too good..  I don't get how it worked before, but not now..  It's not just the address bar, it's drop down menus too.

Is there really no solution to this? It's quite off-putting.

---

### Post by philinux on 2008-06-18
Ok so you're using the mozilla version rather than the version in synaptic.

I've got compiz on and FF3 from synaptic and not having this bother. 

It might be something to do with gnome integration.

---

### Post by thinch on 2008-06-18
Ahh.. I get what you mean now..  The reason why I didn't download the synaptic version was because it wasn't the final version.
Shall I wait until 3.0 is available through synaptic then?

---

### Post by philinux on 2008-06-18
I mean it's weird, this sort of thing doesn't happen with other apps does it?

---

### Post by thinch on 2008-06-18
No, and this is the only app I have installed that wasn't through synaptic or Add/Remove applications (I find it too hard to do)
Shall I bite the bullet and go for the synaptic version? There shouln't be *that* much of a difference, surely?

---

### Post by philinux on 2008-06-18
> **thinch said:**
> No, and this is the only app I have installed that wasn't through synaptic or Add/Remove applications (I find it too hard to do)
Shall I bite the bullet and go for the synaptic version? There shouln't be *that* much of a difference, surely?

Well you could try rebooting. 
Turn off animations, that would be a shame.
Use the synaptic version. Which will get updated to the final in a few days.

---

### Post by thinch on 2008-06-18
Aaagh!  Tried installing the suggested version through synaptic, but it didn't appear to work.  I then rebooted, and uninstalled 3.0 through synaptic, and marked the old version (2.x) for reinstallation.


This was carried out, but now the 3.0 version that I installed earlier runs instead.  In fact, I think that it ran instead of your suggested version, which is why it appeared not to work.


I am a total linux/ubuntu luddite, so is there a way I can get rid of my 3.0 version for good? (and hopefully install your recommended version)

Thanks, 
thinch

---

### Post by lswest on 2008-06-18
go to system-->administration-->advanced desktop effects (if it's not there, install it with *sudo apt-get install compizconfig-settings-manager*)  There go to "animations" and select the opening and closing effects.  From there go to edit and add "&!(name=firefox)" (without the quotes) to the end of the open and close animations.  That SHOULD remove any animations for firefox (it's an ugly fix, but it should work, if it does not, I'll have a play with it when i get back to a linux box)

---

### Post by thinch on 2008-06-18
I have "Advanced Desktop Effects Settings" installed, if that's what you mean.

I added the code to the end of the close animation so it now reads:
((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)& !(name=firefox)

And the open animation "window match" reads:
((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)& !(name=firefox)

But it still hasn't fixed the problem, even after restarting firefox..

---

### Post by lswest on 2008-06-18
hmm, then I'm not sure, I'm not at a linux box at the moment, so I can't check.  However, you can try changing "firefox" to different variations to see if that's the problem.  (also, if there are no spaces in the line of code originally, there should be none in the added section either).  Basically what it does is tell Compiz to ignore windows of the name "firefox" when applying animations (&=and !(name=firefox) means the name of the program is NOT firefox), and it's a list of requirements windows need to fulfill to gain animations.  Possibly change "firefox" to "firefox-3.0" and see if that helps.

---

### Post by philinux on 2008-06-18
The thing is apps like open office writer aren't mentioned in ccsm and their pull down menu's are not affected like this.

---

### Post by thinch on 2008-06-18
In System Monitor, the process appears as "firefox", if that's any help..
And any variations on firefox havent worked- firefox-3.0 or Mozilla Firefox.

I'm not desperate to have 3.0 installed for now, so is there a (fairly) easy way to uninstall it?

---

### Post by lswest on 2008-06-18
> **philinux said:**
> The thing is apps like open office writer aren't mentioned in ccsm and their pull down menu's are not affected like this.

I know, I thought it'd be a fix until the final release is in the repos.  If it doesn't work, sorry, guess my idea doesn't work.

---

### Post by thinch on 2008-06-18
Sorry, I need to go now, but I'll be back tomorrow.

Thanks for all the help everyone:)

---

### Post by thinch on 2008-06-20
Any ideas anyone?

---

### Post by lswest on 2008-06-20
Not yet.  I really can't see what the problem would be.  Also, uninstalling it completely would just consist of going into Synaptic and choosing to mark the package for "complete removal" (providing you installed it as a .deb) or running ```
sudo dpkg --purge *packagename*
``` (I'd write down the actual packagename but I'm running arch and not 100% sure what the package is called in Ubuntu right now).  This will remove the configurations files too (ALL of them) so that the chances are your bookmarks and such will be gone, so I recommend exporting your browser's bookmarks by going to boomarks-->organize bookmarks-->import and backup-->export html.  Sorry I can't be of more help.

---

### Post by thinch on 2008-06-27
Using synaptic I have uninstalled all firefox applications, as shown in the screenshot attached.  The firefox logo has now dissapeared from my desktop and top bar, but by clicking on either, it still launches firefox 3.0 (the one that I installed manually)

How can I uninstall the version that I installed manually?
I have absolutely no idea how, and any help would be appreciated.

---

### Post by lswest on 2008-06-27
how do you mean "manually"? with sudo make install?  If so, go back to the sources folder where you ran that command and run "sudo make uninstall" (without the quotes).  Otherwise please explain what you mean with "manually".

---

### Post by thinch on 2008-06-27
"Hi,

You can easily install Firefox 3 in Gutsy using this tutorial:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

All you need to do is to cut and paste these commands in your terminal:

First, back up your bookmarks and settings:

cp -R ~/.mozilla ~/.mozilla.backup


Download Firefox from the [WWW] Firefox website, and change to the directory you downloaded it to.

(e.g., download it to desktop, the open a terminal and type:

cd /[your home directory name]/Desktop)


Install it to /opt/firefox (make sure the /opt directory exists first):

sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
rm firefox-3.0.tar.bz2

*

Link to your plugins and remove totem-mozilla as it doesn't seem to work with Firefox 1.5.x or 2.x:

sudo mv /opt/firefox/plugins /opt/firefox/plugins.bak
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sudo rm /usr/lib/firefox/plugins/libtotem_mozilla.*

*

To ensure it is used as the default version, modify the symbolic link in /usr/bin:

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

The dpkg-divert command will move the original system-wide /usr/bin/firefox to a new name. The ln command will place a symlink to the newly installed Firefox in /usr/bin.
*

Try it out:

firefox &

*

Running Firefox in terminal may cause errors to show but don't worry about that, it will still work once Firefox is restarted. The reason for these errors is because Firefox 3 is checking for updates, which is not abnormal activity. Also, running this command make take a some time to execute. Please be patient.
*

If you want to keep the original Ubuntu icon for Firefox, enter this command:

sudo cp /usr/share/pixmaps/firefox.xpm /opt/firefox/chrome/icons/default/default.xpm

Some users may find the icon with a different extension, they should use this command:

*

sudo cp /usr/share/pixmaps/firefox.png /opt/firefox/chrome/icons/default/default.xpm


Don't be daunted - it's literally a few cut and pastes in your terminal to get it all to work. Then, when you click on your Firefox icon, you'll get a brand spanking new release of Firefox 3 on your desktop It rocks!

Please ask if there's something you're not sure about.

All the best!

Ubukool
Last edited by ubukool; 1 Week Ago at 03:49 PM. "

from: [http://ubuntuforums.org/showthread.php?t=833036](http://ubuntuforums.org/showthread.php?t=833036)

My linux terminology and mental dictionary isn't quite up to scratch, so i don't quite know what that would be classed as.

---

### Post by lswest on 2008-06-27
okay, basically for every cp and ln -s command, do "rm" instead, and then it should no longer be used, and then for the dpkg-divert ones, just switch around the names, so /usr/bin/firefox /usr/bin/firefox.ubuntu instead of the way it was there originally.  After that you can (if you want to) remove the firefox3 folder by doing ```
sudo rm -r /opt/firefox
```

one small note: you can ignore the cp -R ~/.mozilla step at the start, it doesn't affect you at all, it's just the backup of your bookmarks.

Disclaimer: I'm not sure if this will work, but it's the only answer I can think of.  Try at your own risk.

---

