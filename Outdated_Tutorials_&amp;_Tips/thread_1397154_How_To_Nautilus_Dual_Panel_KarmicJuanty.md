---
title: "How To: Nautilus Dual Panel Karmic/Juanty"
date: 2010-02-02
forum: Outdated Tutorials &amp; Tips
---

### Post by 2hot6ft2 on 2010-02-02
If you like krusaders dual panel view (or PowerDesk in Windows) and want it in nautilus I found the information for doing it in Jaunty 9.04 and Karmic 9.10 and after doing it myself I decided to share the information in a simpler how to.
[COLOR="DarkRed"]**[SIZE="3"]Keep in mind this is still in Beta (so use it at your own risk).[/SIZE]**[/COLOR]

The sources were here:
**Karmic 9.10**
[http://www.webupd8.org/2009/11/dual-panel-nautilus-for-ubuntu-karmic.html](http://www.webupd8.org/2009/11/dual-panel-nautilus-for-ubuntu-karmic.html)
[https://launchpad.net/~berndth/+archive/ppa](https://launchpad.net/~berndth/+archive/ppa)

**Jaunty 9.04**
[http://www.webupd8.org/2009/09/how-to-install-dual-panel-nautilus-for.html](http://www.webupd8.org/2009/09/how-to-install-dual-panel-nautilus-for.html)
[https://launchpad.net/~berndth/+archive/ppa](https://launchpad.net/~berndth/+archive/ppa)

**[SIZE="3"]The short version of doing this is as follows[/SIZE]**

**[SIZE="3"]For Karmic 9.10[/SIZE]**
To add the PPA to our sources list open a terminal.
Applications > Accessories > Terminal
Use this in it:
---
EDIT: This section can be shortened to this in Karmic 9.10 to 
```
sudo add-apt-repository ppa:berndth
```
Hit Enter
Thanks to littlepeon for the tip.
END EDIT
---
Now to update and upgrade use the following 2 commands one at a time in the still open terminal.
(Note if for some reason you don't want to upgrade other things and just want to activate the dual panel ONLY run the first command below and see **Another way to activate dual panel** below).
```
sudo apt-get update
sudo apt-get install libnautilus-extension1 nautilus nautilus-data
```
Once it finishes you can close the terminal.

Restarting nautilus from the terminal makes my desktop items vanish so I recommend closing everything and going like you're going to reboot and selecting **Logout** this will log you out real fast and you can log right back in.

**[SIZE="3"]For Jaunty 9.04[/SIZE]**
To add the PPA to our sources list open a terminal.
Applications > Accessories > Terminal
Use this in it:
```
gksu gedit /ect/apt/sources.list
```
Hit Enter and it will ask for your password. Type it in and hit Enter (your password will not be displayed).
Add the following 2 lines to the bottom of the file.
> deb [http://ppa.launchpad.net/berndth/ppa/ubuntu](http://ppa.launchpad.net/berndth/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/berndth/ppa/ubuntu](http://ppa.launchpad.net/berndth/ppa/ubuntu) jaunty main
Save and close the file.
The terminal should still be open so put this in it to add the key for the PPA.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 246BF391
```
Hit Enter
Now to update and upgrade use the following 2 commands one at a time in the still open terminal.
(Note if for some reason you don't want to upgrade other things and just want to activate the dual panel ONLY run the first command below and see **Another way to activate dual panel** below).
```
sudo apt-get update
sudo apt-get install libnautilus-extension1 nautilus nautilus-data
```
Once it finishes you can close the terminal.

I haven't used Juanty but restarting nautilus in Karmic from the terminal makes my desktop items vanish so I recommend closing everything and going like you're going to reboot and selecting **Logout** this will log you out real fast and you can log right back in.

**[SIZE="3"]Another way to activate dual panel[/SIZE]**
After running apt-get update go to
System > Administration > Synaptic Package Manager
Search for
> libnautilus-extension1
Right click on it and select Upgrade
This should also mark these (if not search for them and mark them for upgrade the same way).
> nautilus-data
nautilus
Click on Mark then on Apply
Once it finishes you can close Synaptic

**[SIZE="3"]How to make use of the new dual pane nautilus[/SIZE]**

Open a folder/directory such as Places > Home
You can either click on View > Extra Pane
And check or uncheck the box to enable/disable dual pane view.
Or just hit the F3 key to do the same thing.

If you want it to start in dual pane mode each time you open a folder.
Open a terminal (or press Alt + F2) and put in
```
gconf-editor
```
Hit Enter, this will open the gconf-editor
Navigate to
apps > nautilus > preferences
and enable the option called **start_with_extra_pane**.

**[SIZE="3"]Removing Dual Pane[/SIZE]**
The PPA for it can be removed with
```
sudo rm /etc/apt/sources.list.d/berndt*
```
then
```
sudo apt-get update
```
then go to
System > Administration > Synaptic Package Manager
and search for
libnautilus-extension1
nautilus
and
nautilus-data
select each one and click on Package > Force Version
and select an older version from the drop down then click on Force Version, then on Apply.

Below is a pic of how it looks. I hope that some people find this useful.
:popcorn:

---

### Post by tonywhelan on 2010-02-18
Thanks very much for this information.

The tabbed feature in Nautilus does nothing for me and I have been waiting for a dual-pane feature in Nautilus for years. So was pleasantly surprised to find your posting today.:p

---

### Post by 2hot6ft2 on 2010-02-20
> **tonywhelan said:**
> Thanks very much for this information.

The tabbed feature in Nautilus does nothing for me and I have been waiting for a dual-pane feature in Nautilus for years. So was pleasantly surprised to find your posting today.:p
You're very welcome. I'm glad that the information was helpful.

---

### Post by x-shaney-x on 2010-02-20
I have always preferred dual pane file managers and despite using Gnome for a while now I have only just switched to using Nautilus, before I would use konqi or dolphin.

I haven't tried this howto yet though, I'm not keen on updating major apps from 3rd party repos.

---

### Post by littlepeon on 2010-02-20
hey there...

love this feature...just a quick note...if u are using karmic, you can combine the first few steps (edit apt-source.list add keyring) with the new add-apt ppa cli code:

```

sudo add-apt-repository ppa:berndth
```then all u have to do is an update/install then a reboot/logoff-login:


```

sudo apt-get update
sudo apt-get install libnautilus-extension1 nautilus nautilus-data
```then reboot/logoff-login

just showing off the new karmic feature add-apt-repository (wish it was backported to jaunty/hardy)....thank you for showing us this feature!

-peon

---

### Post by 2hot6ft2 on 2010-02-25
> **littlepeon said:**
> hey there...

love this feature...just a quick note...if u are using karmic, you can combine the first few steps (edit apt-source.list add keyring) with the new add-apt ppa cli code:

```

sudo add-apt-repository ppa:berndth
```then all u have to do is an update/install then a reboot/logoff-login:


```

sudo apt-get update
sudo apt-get install libnautilus-extension1 nautilus nautilus-data
```then reboot/logoff-login

just showing off the new karmic feature add-apt-repository (wish it was backported to jaunty/hardy)....thank you for showing us this feature!

-peon
Took me a while to check back. Thanks littlepeon. I have made the change to the How To. I knew there was a new way to do it but wasn't sure how to format it.

---

### Post by edmondt on 2010-02-26
WOW Awesome!!!!!!!!

> **2hot6ft2 said:**
> If you like krusaders dual panel view (or PowerDesk in Windows) and want it in nautilus I found the information for doing it in Jaunty 9.04 and Karmic 9.10 and after doing it myself I decided to share the information in a simpler how to.
Keep in mind this is still in Beta (so use it at your own risk).

The sources were here:
**Karmic 9.10**
[http://www.webupd8.org/2009/11/dual-panel-nautilus-for-ubuntu-karmic.html](http://www.webupd8.org/2009/11/dual-panel-nautilus-for-ubuntu-karmic.html)
[https://launchpad.net/~berndth/+archive/ppa](https://launchpad.net/~berndth/+archive/ppa)

**Jaunty 9.04**
[http://www.webupd8.org/2009/09/how-to-install-dual-panel-nautilus-for.html](http://www.webupd8.org/2009/09/how-to-install-dual-panel-nautilus-for.html)
[https://launchpad.net/~berndth/+archive/ppa](https://launchpad.net/~berndth/+archive/ppa)

**[SIZE="3"]The short version of doing this is as follows[/SIZE]**

**[SIZE="3"]For Karmic 9.10[/SIZE]**
To add the PPA to our sources list open a terminal.
Applications > Accessories > Terminal
Use this in it:
---
EDIT: This section can be shortened to this in Karmic 9.10 to 
```
sudo add-apt-repository ppa:berndth
```
Hit Enter
Thanks to littlepeon for the tip.
END EDIT
---
Now to update and upgrade use the following 2 commands one at a time in the still open terminal.
(Note if for some reason you don't want to upgrade other things and just want to activate the dual panel ONLY run the first command below and see **Another way to activate dual panel** below).
```
sudo apt-get update
sudo apt-get install libnautilus-extension1 nautilus nautilus-data
```
Once it finishes you can close the terminal.

Restarting nautilus from the terminal makes my desktop items vanish so I recommend closing everything and going like you're going to reboot and selecting **Logout** this will log you out real fast and you can log right back in.

**[SIZE="3"]For Jaunty 9.04[/SIZE]**
To add the PPA to our sources list open a terminal.
Applications > Accessories > Terminal
Use this in it:
```
gksu gedit /ect/apt/sources.list
```
Hit Enter and it will ask for your password. Type it in and hit Enter (your password will not be displayed).
Add the following 2 lines to the bottom of the file.

Save and close the file.
The terminal should still be open so put this in it to add the key for the PPA.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 246BF391
```
Hit Enter
Now to update and upgrade use the following 2 commands one at a time in the still open terminal.
(Note if for some reason you don't want to upgrade other things and just want to activate the dual panel ONLY run the first command below and see **Another way to activate dual panel** below).
```
sudo apt-get update
sudo apt-get install libnautilus-extension1 nautilus nautilus-data
```
Once it finishes you can close the terminal.

I haven't used Juanty but restarting nautilus in Karmic from the terminal makes my desktop items vanish so I recommend closing everything and going like you're going to reboot and selecting **Logout** this will log you out real fast and you can log right back in.

**[SIZE="3"]Another way to activate dual panel[/SIZE]**
After running apt-get update go to
System > Administration > Synaptic Package Manager
Search for

Right click on it and select Upgrade
This should also mark these (if not search for them and mark them for upgrade the same way).

Click on Mark then on Apply
Once it finishes you can close Synaptic

**[SIZE="3"]How to make use of the new dual pane nautilus[/SIZE]**

Open a folder/directory such as Places > Home
You can either click on View > Extra Pane
And check or uncheck the box to enable/disable dual pane view.
Or just hit the F3 key to do the same thing.

If you want it to start in dual pane mode each time you open a folder.
Open a terminal (or press Alt + F2) and put in
```
gconf-editor
```
Hit Enter, this will open the gconf-editor
Navigate to
apps > nautilus > preferences
and enable the option called **start_with_extra_pane**.

Below is a pic of how it looks. I hope that some people find this useful.
:popcorn:

---

### Post by Deadite81 on 2010-03-03
This is a cool extension and seems to work pretty well.

Two things though:

1. When I try to drag and drop something, like an icon, from a root owned folder to my home folder (which normally would automatically copy the file) I get an error box about permissions, even though half the time it still does the copy.  But if I choose the copy to other pain context option there are no errors.  Not that big a deal, but drag and drop is such a prominent point of the extension, and when I'm in dual-pane mode my context menu is so buggy....

2. What I did find a big deal, and why I uninstalled it:(, is it breaks the gloobus-preview spacebar shortcut.  Of course this is meaningless if you don't use gloobus (or even know what it is;)), but since I use it constantly I had to choose between the two.  After I install the dual pain extension spacebar opens whatever the file's default program is (gedit, gthumb, etc.) instead of gloobus.  When I uninstall, spacebar goes back to gloobus.  I did this a few times to be sure.

I looked around in gconf and Nautilus preferences, Google, various conf files and found no immediate solution.  Somehow, somewhere, this extension writes over/blocks where gloobus-preview modifies Nautilus to add the spacebar shortcut.

That being said, this is a great addon and long overdue. But be wary if you use gloobus, however. Can't wait for newer versions.

---

### Post by 2hot6ft2 on 2010-03-03
> **2hot6ft2 said:**
> 
Keep in mind this is still in Beta (so use it at your own risk).

Sorry it didn't work out for you. Time will tell how it matures. There are other dual pane browsers like krusader. Now we know it has issues with gloobus.

---

### Post by randiroo76073 on 2010-03-21
Thanks for the dual-pane Nautilus. I always install Krusader for heavy work and use Nautilus for day to day quickie stuff, it'll be nice to have dual-pane in it too !
Great work !

---

### Post by sasagundul on 2010-03-21
hey thanks for the tutorial.
but i can't find the option to enable the panel.
i've nautilus version higher than in the PPA. 
mine is 1:2.28.1-0ubuntu5

can you help me ?

---

### Post by IstvanL on 2010-03-22
First add the repositories as described above, update Synaptic,then go to 'force version' , downgrade the 3 packages (nautilus, nautilus.data,libnautilus-extension).
When ready, lock version for the packages.

---

### Post by sasagundul on 2010-03-22
> **IstvanL said:**
> First add the repositories as described above, update Synaptic,then go to 'force version' , downgrade the 3 packages (nautilus, nautilus.data,libnautilus-extension).
When ready, lock version for the packages.

thanks dude :D 
it solve my problem

---

### Post by 2hot6ft2 on 2010-03-22
> **randiroo76073 said:**
> Thanks for the dual-pane Nautilus. I always install Krusader for heavy work and use Nautilus for day to day quickie stuff, it'll be nice to have dual-pane in it too !
Great work !
Glad you found it useful. It will be in 10.04 from what I understand but you wont be able to set it to start up as dual pane from what I've seen.

---

### Post by 2hot6ft2 on 2010-03-22
> **IstvanL said:**
> First add the repositories as described above, update Synaptic,then go to 'force version' , downgrade the 3 packages (nautilus, nautilus.data,libnautilus-extension).
When ready, lock version for the packages.
Thanks for stepping in and solving that. I just checked my mail and it looks like I missed a few posts. I was looking at the first page when I responded above.

---

### Post by yasir.elsharif on 2010-04-13
Thanks Guys, but it doesn't work for me at all although I followed all the steps.
and when I tried the  gconf-editor, I could not found **start_with_extra_pane** in **apps/nautilus/preferences **also.
any sugesstions?
can I just remove all the settings like deleting .gnome2 folder?

---

### Post by 2hot6ft2 on 2010-04-13
> **yasir.elsharif said:**
> Thanks Guys, but it doesn't work for me at all although I followed all the steps.
and when I tried the  gconf-editor, I could not found **start_with_extra_pane** in **apps/nautilus/preferences **also.
any sugesstions?
can I just remove all the settings like deleting .gnome2 folder?
Strange that you don't have that option. Have you rebooted to see if it shows up?
Does the dual pane work by pressing the F3 key?
Does it show up under View as Extra Pane?
If not then it wasn't installed.
I don't know exactly what deleting the .gnome2 folder would do.

To undo it
The PPA for it can be removed with
```
sudo rm /etc/apt/sources.list.d/berndt*
```
then
```
sudo apt-get update
```
then go to
System > Administration > Synaptic Package Manager
and search for
libnautilus-extension1
nautilus
and
nautilus-data
select each one and click on Package > Force Version
and select an older version from the drop down then click on Force Version, then on Apply.

It is a new feature and will be included in Lucid 10.04 just without the start as dual pane option.

---

### Post by yogieza on 2010-04-13
thanx brother for your article.my Ubuntu looking amazing now :grin:

---

### Post by 2hot6ft2 on 2010-04-13
> **yogieza said:**
> thanx brother for your article.my Ubuntu looking amazing now :grin:
You're welcome and welcome to the forum.

---

### Post by B00R4dL3y on 2010-04-14
I tried it out in Karmic and when I rebooted/relogin my CPU was showing a high load.  The desktop pointer got stuck in the busy state - like it still was trying to complete something before handing me back my desktop.  

I uninstalled and things are back to normal.

---

### Post by kamatschka on 2010-04-14
Maaan.. Thank you.

Its working flawelessly here on Karmic ..

But with the feature of Windows 7 you can get any window to the size of the half display with a mousemove. This feature would be very nice for ubuntu. This is the only feature wich I am considering as good in Windows7.

---

### Post by 2hot6ft2 on 2010-04-14
> **kamatschka said:**
> Maaan.. Thank you.

Its working flawelessly here on Karmic ..

But with the feature of Windows 7 you can get any window to the size of the half display with a mousemove. This feature would be very nice for ubuntu. This is the only feature wich I am considering as good in Windows7.
Glad to hear it, and I think you mean this.
Win 7 snap windows
[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

---

### Post by timur_ba on 2010-10-13
> **2hot6ft2 said:**
> Glad you found it useful. It will be in 10.04 from what I understand but you wont be able to set it to start up as dual pane from what I've seen.

I have 10.10 now. Extra pane is here, but without the option to set it to start up as dual pane. Also, it doesn't remember location. Any solution?


Here is the comparison I made: 
Krusader 2.0: Best manager with diverse options, but for KDE. Few right click options missing.
+: folder tabs, tab location editable, multi rename, compare contents, compare directories, synchronize directories, bookmarks, pack/unpack, terminal emulator, root mode; right click: open with, user actions (edit as root..); drag&drop details on replace; connect 
-: tabs on bottom, tab location not clickable; right click: no zip, no extract, no remember open with; no copy with sudo/cut with sudo, no password on copy/cut permission error; 
Double Commander 0.4.5.1 beta: Potent manager with some good options. Exit errors. No real terminal emulator. A lot of right click options missing.
+: folder tabs, tabs on top, tab location clickable, folder history, multi rename, compare contents, directory hotlist (bookmarks), pack/extract, terminal window; right click: configurable view/edit (edit as root); plugins 
-: tab location not editable, no terminal emulator-command line only (passwords visible), no root mode, no compare directories, no synchronize directories, no back button; right click: no zip, no extract, no open with, no remember open with, no directory hotlist, no copy filenames; no right click menu on empty space: no new file, no new folder; drag&drop without details on replace; no copy with sudo/cut with sudo, no password on copy/cut permission error; no connect; no contrast toolbar text/background on a dark theme; exit error: futex_wait_queue_me
Gnome Commander 1.2.8.5: Stable manager with basic options. No folder tabs. No terminal emulator. Some right click options missing.
+: tab location clickable, root mode, advanced (multi) rename, diff (compare contents?), synchronize directories?, bookmarks; right click: open with; connect, plugins
-: no folder tabs; no terminal emulator-command line only; right click: no zip, no extract, no remember open with, no edit as root; drag&drop without details on replace; no copy with sudo/cut with sudo, no password on copy/cut permission error; 
Nautilus 2.32: 
+: tabs 
-: tabs and extra pane not remembered, no terminal emulator

---

### Post by 2hot6ft2 on 2010-10-31
No solution. I am running Ultimate Edition 2.7 and haven't played with 10.10 much other than some beta testing of Ultimate Edition 2.8. I think I'll be sticking with 2.7 for now since it works great.

As you already know this was for having it in 9.04, and 9.10 so it's rather outdated now.

I wish you luck.
:popcorn:

---

