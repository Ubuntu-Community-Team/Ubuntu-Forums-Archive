---
title: "HowTO: Comprehensive Guide to Customising GDM and XSplash"
date: 2009-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by ibuclaw on 2009-11-21
[CENTER]
[IMG]http://img27.imageshack.us/img27/5962/screenshotpl.png[/IMG]
[SIZE="5"]Comprehensive Guide to Customising
GDM and XSplash[/SIZE]
[/CENTER]


[COLOR="Sienna"][SIZE="4"]Preface[/SIZE][/COLOR]
This guide is my statement to those people who think that the new GDM login screen is un-customisable.

At the beginning of this month, I started playing around with a Netbook I bought back in August. Installed Karmic UNR, and started playing about with it.

One thing I was looking for in the first place was a consistency across the UI. From Splash Screen, to Login Screen, to Desktop.
Once that was sorted, and I picked up a thing or two about how GDM actually functions now, I then had the mad idea of turning GDM into a minimal desktop for the most basic functions I use everyday - XChat, Empathy and Browsing - and if I need to get to anything else - just login and I have the usual full control to the system and applications again.

[COLOR="Red"]**Before you run anything. I regard all material in this guide to be reasonably safe in terms of security. If you do find a hole or flaw, please contact me with an appropriate fix, if possible.**[/COLOR]


[COLOR="Sienna"][SIZE="4"]Changing XSplash Background[/SIZE][/COLOR]
Unfortunately, xsplash has the location of where the background it uses hard coded into the application. So you cannot alter this via changing a setting in a config file.

Fortunately for us though, we use a Debian system, and such systems are capable of a certain administrative feature called "diverting".
```
sudo dpkg-divert --local --rename --add /usr/share/images/xsplash/bg_2560x1600.jpg
```
This renames the file 'bg_2560x1600.jpg' to 'bg_2560x1600.jpg.distrib', and sets the package manager config in such a way that if an update of xsplash were to come through, it will save the file as the diverted name (so the locally created file will not be overwritten).

So that sorted out, just copy the image you want to that location:
```
sudo cp /usr/share/backgrounds/TheRainbowisDead.jpg /usr/share/images/xsplash/bg_2560x1600.jpg
```
And logout/login to see your new xsplash.

To restore this setting.
```

sudo unlink /usr/share/images/xsplash/bg_2560x1600.jpg
sudo dpkg-divert --rename --remove /usr/share/images/xsplash/bg_2560x1600.jpg

```


[COLOR="Sienna"][SIZE="4"]Backup GDM Default settings[/SIZE][/COLOR]
Before making any changes, first we need to divert and backup the gconf settings file
```

sudo dpkg-divert --local --add /var/lib/gdm/.gconf.defaults/%gconf-tree.xml
sudo cp /var/lib/gdm/.gconf.defaults/%gconf-tree.xml /var/lib/gdm/.gconf.defaults/%gconf-tree.xml.distrib

```
If at all you need to reset these changes back to the Ubuntu defaults
```
sudo cp /var/lib/gdm/.gconf.defaults/%gconf-tree.xml.distrib /var/lib/gdm/.gconf.defaults/%gconf-tree.xml
```


[COLOR="Sienna"][SIZE="4"]Changing GDM Background and Theme[/SIZE][/COLOR]
Now this could probably be done in a gconftool-2 command, but I prefer this method:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
Then logout, and you'll see an appearance window pop up.
Change it to how you prefer it, then close and login as usual.

When you have logged in after finishing the customising. Just remove the file to prevent it starting up every time.
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```


[COLOR="Sienna"][SIZE="4"]Hacking GDM[/SIZE][/COLOR]
GDM still has configuration options that you can edit in gconf. You can get the list [here.]("http://library.gnome.org/admin/gdm/2.26/configuration.html.en_GB")
To run through what I consider to be the "interesting" ones in brief:

[COLOR="Sienna"][SIZE="3"]Disable User List[/SIZE][/COLOR]
```

sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true

```
Disables the name list in the login screen.
Valid Values: true - false

[COLOR="Sienna"][SIZE="3"]Change Logo[/SIZE][/COLOR]
```

sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/logo_icon_name --type string "distributor-logo"

```
Changes the logo on the Login Window
Default Value: "computer"

[COLOR="Sienna"][SIZE="3"]Enable Compositing[/SIZE][/COLOR]
```

sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/wm_use_compiz --type bool true

```
Change default window manager from Metacity to Compiz. Probably just me, but that doesn't seem to take effect?
Valid Values: true - false

If your system's graphics card doesn't support 3D Acceleration (Older than 5 years?) then you can always enable simple compositing in Metacity.
```

sudo -u gdm gconftool-2 --set /apps/metacity/general/compositing_manager --type bool true

```
Valid Values: true - false


[COLOR="Sienna"][SIZE="4"]GDM and Compiz[/SIZE][/COLOR]
If the above key change didn't make any difference to you (didn't to me). Don't worry, there is another way!

Now, to give a brief background, when gdm loads, it opens up all desktop applications inside the directory:
/usr/share/gdm/autostart/LoginWindow/

So any .desktop file kept in that directory will run whenever gdm loads.

So! Using the same divert trick as earlier, divert the metacity.desktop file.
```
sudo dpkg-divert --local --rename --add /usr/share/gdm/autostart/LoginWindow/metacity.desktop
```
Then copy over the compiz.desktop file.
```
sudo cp /usr/share/app-install/desktop/compiz.desktop /usr/share/gdm/autostart/LoginWindow
```
This should be doable with any window manager within reason. (ie: mutter). Although feel free to see if any other will work too.


[COLOR="Sienna"][SIZE="4"]GDM and Network Connectivity[/SIZE][/COLOR]
Before we can connect to the Net, we need the Network Manager applet.

Simple to install:
```
sudo cp /usr/share/app-install/desktop/nm-applet.desktop /usr/share/gdm/autostart/LoginWindow
```
[Then to set it up]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/"), logout and enter in the passphrase/key for your network (presuming you are wireless). Then when asked for a password for a default keyring, leave it blank and just press 'Create'.
You will be prompted with the message: "**Store passwords unencrypted?**", just select "Use Unsafe Storage" and the password will be kept in clear text.

This is essential if you don't want to be bugged by entering in a keyring password every time - and it isn't quite as insecure as it seems. Although the password will be in clear text, permissions deny any user except 'root' and 'gdm' from reading the file.


[COLOR="Sienna"][SIZE="4"]GDM and Firefox, XChat, Empathy[/SIZE][/COLOR]
This little trick in this guide is essentially turning GDM into a minimal desktop session, useful for doing quick web searches, or asking quick questions to friends without the need to login entirely!

First, we insert Firefox. Now, I prefer to put it into the taskbar using 'alltray'.
```
sudo apt-get install alltray
```
Then copy over the desktop icon.
```
sudo cp /usr/share/app-install/desktop/firefox.desktop /usr/share/gdm/autostart/LoginWindow/
```
And alter it so it open firefox with alltray:
```
sudo sed -i 's/^Exec=/Exec=alltray /' /usr/share/gdm/autostart/LoginWindow/firefox.desktop
```
Now, when you come to the login screen, Firefox will be in a tray icon.

The exact same procedure is used for XChat and Empathy too.
```

sudo cp /usr/share/app-install/desktop/xchat.desktop /usr/share/gdm/autostart/LoginWindow/
sudo sed -i 's/^Exec=/Exec=alltray /' /usr/share/gdm/autostart/LoginWindow/xchat.desktop

```
Although, in the case of Empathy, you will have two tray icons if you run the 'sed' command.
```

sudo cp /usr/share/app-install/desktop/empathy.desktop /usr/share/gdm/autostart/LoginWindow/
sudo sed -i 's/^Exec=/Exec=alltray /' /usr/share/gdm/autostart/LoginWindow/empathy.desktop

```
Of the above though - realistically you should only be needing firefox, as you can use it as both an IRC and IM client through either addons or web-based services.


[COLOR="Sienna"][SIZE="4"]GDM Hardening[/SIZE][/COLOR]
This last section of this is all about hardening GDM and reducing as many security breaches as possible.

[COLOR="Sienna"][SIZE="3"]What is already restricted?[/SIZE][/COLOR]
GDM itself already comes as pretty restrictive by default.
[LIST]
[*]GDM's Home Directory has the permission 750.
[*]URL Handlers are disabled.
[*]Save to Disk is disabled.
[*]Printer Setup and Printing is disabled.
[*]Lock Screen is disabled.
[*]Command Line is disabled. Shell is set to /bin/true
[*]The Majority of Keybindings are disabled.
[*]Desktop and File Browsing is disabled.
[/LIST]

[COLOR="Sienna"][SIZE="3"]What else can be done?[/SIZE][/COLOR]
If anyone has anything more to add, please comment.

[COLOR="Sienna"][SIZE="2"]**Firefox Tweaking**[/SIZE][/COLOR]
[LIST]
[*]Install security addons. I recommend [No Script]("http://noscript.net/").
[*]Open about:config and set '**browser.privatebrowsing.autostart**' to **True**.
[/LIST]

[COLOR="Sienna"][SIZE="2"]**Disallow Root Logins**[/SIZE][/COLOR]
For reasons beyond me, GDM doesn't seem to deny root logins.
This can be fixed though.
```
gksu gedit /etc/pam.d/gdm
```
And put below the **#%PAM-1.0**
```

auth    required        pam_succeed_if.so user != root quiet
```
Alternatively, you could use what I believe to be the default behaviour of GDM 2.20
```

auth    required        pam_succeed_if.so uid >= 1000 quiet
auth    required        pam_succeed_if.so user != nobody quiet

```


[COLOR="Sienna"][SIZE="4"]Last Words[/SIZE][/COLOR]
As GDM is part of the boot process, you may want to optimise all the changes you've made. Ubuntu Karmic uses ureadahead to carry out the profiling, and all you have to do to schedule a re-profile of the preload cache is by running:
```
sudo rm /var/lib/ureadahead/*pack
```
Then reboot twice, and your boot process with be optimised again.

So! turns out if you put your mind to it, you **can** make something out of nothing much. Hope you all enjoy the guide as much as I did creating it.

Thanks for reading.

Regards
Iain

TODO:
[LIST]
[*]AppArmor :D
[*]Firefox doesn't close cleanly by itself.
[*]Rather than alltray - perhaps tray shortcuts instead?
[*]Enable window switching.
[*]Login Sounds
[/LIST]

---

### Post by paultag on 2009-11-21
Heyya Iain, 

Working OUTSTANDING. I have it working away!

One small protip for any dual-screeners --

The background will do some funny things with resizing, but all in all, works great!

Godspeed folks!

---

### Post by Wiebelhaus on 2009-11-21
Thanks mate!

---

### Post by Spectre5 on 2009-11-22
Very interesting - care to post a short video (youtube?) of everything in work?

---

### Post by joecrow on 2009-11-24
thanks!

---

### Post by dzon65 on 2009-12-04
Hi.This worked out fine,but for some reason I'm unbable to set the windowdecorator.Used to use emerald but now it's stuck in clearlooks and I can't change it to whatever.Any ideas?

---

### Post by dzon65 on 2009-12-04
????It's back now (did another reboot).Sorry about that.

---

### Post by deanhopkins on 2009-12-04
Hey mate, awesome thread.

Ive got a problem though, not really related to this, but you seem the guy to ask.

I have a dual monitor setup, using nVidias twinview setting. When I start my PC, the login window is displayed on my secondary monitor (which is a TV screen, and is off when im not using it).. The primary monitor is still enabled on the login screen (GDM is across both monitors, its just the actual login part is on the second).

Is there anyway I can change this so the login window is displayed on my primary monitor (which would be the logical way to do it anyway..)

I know I could just disable the secondary monitor unless im using it, but that really screws with my wallpapers.

So basically, GDM is displayed on the wrong monitor. I think the best option would be to just disable the second monitor on gdm. Sorry if i've explained this badly (I have :p)

Thanks

---

### Post by Defiant Rat on 2009-12-04
Awesome guide thanks a lot :D

I have one problem though, when i run
```
sudo rm /var/lib/sreadahead/pack
```I get:
```
dave@dave-laptop:~$ sudo rm /var/lib/sreadahead/pack
rm: cannot remove `/var/lib/sreadahead/pack': No such file or directory

```Any ideas what i need to do?

Cheers :)

---

### Post by dzon65 on 2009-12-04
Hi.First of all,this a wubi install.After following the guidelines,reboot,one of the first things was the unability to change the window borders.Somehow they were stuck in a clearlooks theme.Rebooted and emerald was back again.However,after a few seconds,the screenresolution went to 800X600.Without the ability to do anything.I had no other option than to install ubuntu again.Changing the xsplash and gdm is no problem at all but installing the rest seems to have stuck the system.Couldn't find a solution this morning so..In order not to have a reinstall again if this might occur once more,what should I do when it's stuck.By the way,no errors were given during the install.
Regards,John.

---

### Post by ibuclaw on 2009-12-04
> **dzon65 said:**
> Hi.This worked out fine,but for some reason I'm unbable to set the windowdecorator.Used to use emerald but now it's stuck in clearlooks and I can't change it to whatever.Any ideas?
Emerald isn't really covered in the scope of this guide.

And I don't really intend to look into it - sorry.

> **Defiant Rat said:**
> Awesome guide thanks a lot :D

I have one problem though, when i run
```
sudo rm /var/lib/sreadahead/pack
```I get:
```
dave@dave-laptop:~$ sudo rm /var/lib/sreadahead/pack
rm: cannot remove `/var/lib/sreadahead/pack': No such file or directory

```Any ideas what i need to do?

Cheers :)
Aah! sreadahead has been deprecated and removed already!?

New location (if it exists) is **/var/lib/ureadahead/pack**
I've updated the guide.

Though - btw - this step isn't really needed. It's just to force a new pack file to be generated the next time you boot.

If you skip deleting it, doesn't really make a difference as a new one is generated once every month as standard.

---

### Post by deanhopkins on 2009-12-07
> **deanhopkins said:**
> Hey mate, awesome thread.

Ive got a problem though, not really related to this, but you seem the guy to ask.

I have a dual monitor setup, using nVidias twinview setting. When I start my PC, the login window is displayed on my secondary monitor (which is a TV screen, and is off when im not using it).. The primary monitor is still enabled on the login screen (GDM is across both monitors, its just the actual login part is on the second).

Is there anyway I can change this so the login window is displayed on my primary monitor (which would be the logical way to do it anyway..)

I know I could just disable the secondary monitor unless im using it, but that really screws with my wallpapers.

So basically, GDM is displayed on the wrong monitor. I think the best option would be to just disable the second monitor on gdm. Sorry if i've explained this badly (I have :p)

Thanks

bump :(

---

### Post by ibuclaw on 2009-12-07
> **deanhopkins said:**
> bump :(

When you are logged in:
```
gksu nvidia-settings
```

Set everything up correctly, then select "Save Config" and it should save it to /etc/X11/xorg.conf.
That should make the settings you have for your login session global.

Regards
Iain

---

### Post by Junkieman on 2009-12-08
I never knew you could divert in Debian systems, or at all, until I read your guide :) 

I'll try this out on my Netbook these hols. Good job!

---

### Post by ret3 on 2009-12-23
Any ideas about how to change the order of users on the login screen?

---

### Post by AlexanderDGreat on 2009-12-27
Hi thanks for this tutorial.Now I can fix the bug and customize gdm.

Disable User List:
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true

And fixing the bug, Enhance Contrast In Colors:
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Unlinking it:
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

PS  I have a question, why do they have to make it complicated every distribution? I'm using Karmic Koala now. What if I'm just a regular user and don't know these commands? I've spent a good whole morning just customizing a login screen the way I wanted? I just don't find it productive, it's saddening. :(

---

### Post by lemmy999 on 2009-12-28
Nice work. I can finally get rid of the ugly "standard" GDM.

---

### Post by ibuclaw on 2009-12-28
> **AlexanderDGreat said:**
> PS  I have a question, why do they have to make it complicated every distribution? I'm using Karmic Koala now. What if I'm just a regular user and don't know these commands? I've spent a good whole morning just customizing a login screen the way I wanted? I just don't find it productive, it's saddening. :(

Yeah - the default look is somewhat of a letdown for what it is worth.

Though the new GDM is a huge redesign - and best to think of it now as a very minimal/restricted login session - hence why it can be fixed using the Gnome Appearance properties.

Regards
Iain

---

### Post by AlexanderDGreat on 2009-12-28
@tinivole

Thank you for understanding my opinion. You're the type of Ubuntu teacher that can seem to understand us "regular guys" out there.

Thanks man! Keep up your good work! God Bless You! :)

---

### Post by echo6 on 2009-12-29
> **AlexanderDGreat said:**
> why do they have to make it complicated every distribution? .. I've spent a good whole morning just customizing a login screen the way I wanted? I just don't find it productive, it's saddening. :(DEVELOPERS take note!!!

I appreciate documenting things is boring, but at least please provide some pointers.  Like what binaries, services are used and what config files are utilized ?

---

### Post by Mahngiel on 2009-12-29
Awesome job. Now i have a complete boot -> shutdown theme.  Love it.  Great job.

---

### Post by exosyst on 2009-12-29
Hey guys, I just saw this thread and thought i'd share a little python tool I wrote and [posted here]("http://ubuntuforums.org/showthread.php?t=1358026"). It doesn't cover everything mentioned here but after all the effort to get my login looking pretty I wanted an easy way for mates/family to do it so it covers things like login sound, display user list, autologin with user, appearance and wallpaper.

Hopefully it should be of some use, I've seen one person had an issue already though after they changed settings using gksudo -u gdm gnome-appearance-properties so check your results if you've already customised it!

Patches and fixes are always welcome! :P

---

### Post by AlexanderDGreat on 2009-12-30
Because of this tutorial I've found out the GUI way of disabling user list via the ALT+F2 - gconf-editor or sudo gconf-editor for ROOT changes. Here's what it looked like for me in apps > gdm > simple-greeter > disable_user_list

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/gconf-editor.png[/IMG]

> Edited: Oh this process did not WORK. I will put different values on the settings and they won't get applied. Pls. don't try this, sorry for the bad info.

---

### Post by Shnatsel on 2009-12-31
What about changing the hardcoded settings? I'm maintaining an Ubuntu remix and I need to set custom XSplash by default, without tweaking configs etc. I can build a custom XSplash package from source to change the hardcoded configs, but I couldn't find them in the source code. Would anybody explain me where are they, please?

---

### Post by ibuclaw on 2010-01-02
> **Shnatsel said:**
> What about changing the hardcoded settings? I'm maintaining an Ubuntu remix and I need to set custom XSplash by default, without tweaking configs etc. I can build a custom XSplash package from source to change the hardcoded configs, but I couldn't find them in the source code. Would anybody explain me where are they, please?

Have a look at any xsplash-image-theme package in the repositories.

One that I helped build is available here: [http://ppa.launchpad.net/zenix-shravaka/ppa/ubuntu/pool/main/z/zenix-xsplash/zenix-xsplash_1.0~ppa1.tar.gz](http://ppa.launchpad.net/zenix-shravaka/ppa/ubuntu/pool/main/z/zenix-xsplash/zenix-xsplash_1.0~ppa1.tar.gz)

Regards
Iain

---

### Post by Shnatsel on 2010-01-05
> **tinivole said:**
> Have a look at any xsplash-image-theme package in the repositories.

One that I helped build is available here: [http://ppa.launchpad.net/zenix-shravaka/ppa/ubuntu/pool/main/z/zenix-xsplash/zenix-xsplash_1.0~ppa1.tar.gz](http://ppa.launchpad.net/zenix-shravaka/ppa/ubuntu/pool/main/z/zenix-xsplash/zenix-xsplash_1.0~ppa1.tar.gz)

Regards
Iain

Thanks, but they just replace the images in /usr/share/images/xsplash, and I need to change amount of frames. Is there any way to implement this via DEB package? Also it would be great if I could add some throbber sizes, too.

---

### Post by ibuclaw on 2010-01-06
> **Shnatsel said:**
> Thanks, but they just replace the images in /usr/share/images/xsplash, and I need to change amount of frames. Is there any way to implement this via DEB package? Also it would be great if I could add some throbber sizes, too.

Can't exactly remember, but I *think* it is an -f option that you can add to the xsplash command in the /etc/gdm/Init/Default and /etc/gdm/PreSession/Default scripts.

ie:
```
xsplash -f 30
```

Regards
Iain

---

### Post by mocoloco on 2010-01-06
You're missing a piece before you can really say this guide is comprehensive :D

How do you change the pre-xsplash image (and what's displaying that, is it sill usplash)?  I'm talking about the white Ubuntu logo that slightly pulsates.  On Xubuntu it's the XFCE mouse.  I've searched through all images and can't find those to be able to replace them.

---

### Post by ibuclaw on 2010-01-06
> **mocoloco said:**
> You're missing a piece before you can really say this guide is comprehensive :D

How do you change the pre-xsplash image (and what's displaying that, is it sill usplash)?  I'm talking about the white Ubuntu logo that slightly pulsates.  On Xubuntu it's the XFCE mouse.  I've searched through all images and can't find those to be able to replace them.

Pfft - Usplash is not part of the **X** startup. :)

I'm pretty certain you can look up many Usplash guides, (I think you just edit /etc/usplash.conf). And you can probably find many themes on gnome-look.org.

Regards
Iain

---

### Post by Shnatsel on 2010-01-07
> **mocoloco said:**
> You're missing a piece before you can really say this guide is comprehensive :D

How do you change the pre-xsplash image (and what's displaying that, is it sill usplash)?  I'm talking about the white Ubuntu logo that slightly pulsates.  On Xubuntu it's the XFCE mouse.  I've searched through all images and can't find those to be able to replace them.

That's USplash. You can find a comprehencive guide to customizing it [here]("https://help.ubuntu.com/community/USplash") and [here]("https://help.ubuntu.com/community/USplashCustomizationHowto").

> **tinivole said:**
> Can't exactly remember, but I *think* it is an -f option that you can add to the xsplash command in the /etc/gdm/Init/Default and /etc/gdm/PreSession/Default scripts.
Tweaking configs won't work for me. Is there any way to hardcode that into the app?

---

### Post by mocoloco on 2010-01-08
> **tinivole said:**
> Pfft - Usplash is not part of the **X** startup. :)

I'm pretty certain you can look up many Usplash guides, (I think you just edit /etc/usplash.conf). And you can probably find many themes on gnome-look.org.

Regards
Iain

Touché, I retract my statement :), comprehensive it is.  I'll look at theming usplash.

---

### Post by swoody on 2010-01-11
Great guide Iain =D>

I just used it to add a custom xsplash theme, and it worked perfectly. I appreciate all the effort you put into this guide, and it shows that xsplash really is customizable.

-Woody

---

### Post by ABCC on 2010-01-12
When using Openbox XSplash significantly seems to slow down the login time significantly. As such, I wasn't so much interested in customizing it as I was in completely disabling it. There wasn't any obvious way, here's a bit of a hack to accomplish it:

```

cp /etc/dbus-1/system.d/xsplash.conf ~/xsplash.conf 
sudo rm /etc/dbus-1/system.d/xsplash.conf
sudo touch /etc/dbus-1/system.d/xsplash.conf

```

---

### Post by ibuclaw on 2010-01-12
> **ABCC said:**
> When using Openbox XSplash significantly seems to slow down the login time significantly. As such, I wasn't so much interested in customizing it as I was in completely disabling it. There wasn't any obvious way, here's a bit of a hack to accomplish it:

```

cp /etc/dbus-1/system.d/xsplash.conf ~/xsplash.conf 
sudo rm /etc/dbus-1/system.d/xsplash.conf
sudo touch /etc/dbus-1/system.d/xsplash.conf

```
How about uninstalling xsplash?

---

### Post by superTP on 2010-01-23
Hi.  Great tutorial.  One question I had is if there is any way to control which monitor the GDM login prompt shows up on in a dual-head setup?  I have an ATI-Radeon and my Xrandr dual-head settings are set in my xorg.conf file so GDM does see both monitors.  The problem is that one monitor is the primary monitor and I would like to always have the login prompt/chooser show up on that monitor.  Instead, it almost always shows up on the secondary monitor.  I have found that if I move the mouse to the primary monitor while GDM is loading, the chooser will show up on the primary monitor.  Is there a way to hard code this?  In Jaunty and earlier, GDM just did the right thing and always chose the primary(left) monitor so I never had to mess with it.

---

### Post by bburkert517 on 2010-03-16
Hey, I followed your tutorial and so far it has worked great, gdm2setup never worked for me and this finally allowed me to configure gdm. But I do have one question though, I made compiz the window manager by using the second method listed but now that I have done that some things on my desktop are little messed up an I cannot figure out how to fix it. For instance, in my window title bar my minimize maximize and close buttons are messed up. They are in reversed order. Also the title bar font is different. In rhythmbox, just rhythmbox, the menu bar has disappeared. When I revert back to metacity the problems are cleared up but then my gdm doesn't work the way I wanted. A minor issue but I thought I would ask nonetheless.

Thanks

---

### Post by trorion on 2010-03-22
> **AlexanderDGreat said:**
> Hi thanks for this tutorial.Now I can fix the bug and customize gdm.

Disable User List:
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true

And fixing the bug, Enhance Contrast In Colors:
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Unlinking it:
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

PS  I have a question, why do they have to make it complicated every distribution? I'm using Karmic Koala now. What if I'm just a regular user and don't know these commands? I've spent a good whole morning just customizing a login screen the way I wanted? I just don't find it productive, it's saddening. :(


ditto.  It seems that now that I've upgraded to 9.10 I am spending way too much time trying to configure simple stuff that used to be easy to configure.

this gdm tweak is awesome.  I'm trying it with mythtv now to see if I can have a login-free version.

---

### Post by waveOSBeta on 2011-07-21
How do you make the login box transparent?

---

