---
title: "How To: Mint Style Gnome Menu in Ubuntu"
date: 2010-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by KdotJ on 2010-08-14
For those of you who ave ever tried Linux Mint, a distro which is run off the back of Ubuntu, you will have noticed that it has it's own special and somewhat unique gnome menu to select your applications to run, folders to browse etc...

Here is a screen shot of what I mean:

[IMG]http://techmiso.com/wp-content/uploads/2009/05/linux-mint-7-menu.jpg[/IMG] 

NOTE: This is **not** the same menu as the "gnome-main-menu" which can be installed via the official Ubuntu repos. Although it is very similar, the Mint one is much more customisable and innovative.

If you wish to have this menu on your Ubuntu machine... here is the instructions...

**[SIZE="4"]INSTRUCTIONS[/SIZE]**

Fire up your terminal...

**Optional Step**
**0. Create a temporary folder**
If you're like me, and don't like having your /home folder full of odd bits and pieces and like having things organised, then create a temporary folder download the files to, and cd to it.

```
mkdir temp && cd temp
```

**1. Download the Debian files**
These files are from the Mint repos. Copy the commands line by line allowing each one to finish first:

```
wget http://packages.linuxmint.com/pool/main/m/mint-translations/mint-translations_2010.02.02_all.deb
wget http://packages.linuxmint.com/pool/main/m/mint-common/mint-common_1.0.5_all.deb
wget http://packages.linuxmint.com/pool/main/m/mintmenu/mintmenu_4.9.9_all.deb
```

**2. Unpack and Install**
Copy these command one by one, allowing each one to finish first:

```
sudo dpkg -i *.deb
```
```
sudo apt-get install -f
```

**3. Add to gnome panel**
OK, so now you have it installed. If you wish (which I recommend), remove the normal menu from the gnome panel (the "Applications Places System" menu).

- Right click on the gnome panel and select "Add to panel..."
- Choose the "mintMenu" and click on add.

You will notice when you add it the it has the mint menu and some text, I'm guessing you will want to change all this.

**4. Ubuntuize it**
If you right-click on the menu button and select "Preferences" you will see the menu with a whole bunch of stuff. On the first tab which is shown, named "Main Button" you can change how the button looks in the gnome pane. For me, I deleted the button text as I just wanted to have a logo, but of course the choice is yours.

As for the icon, if you want an ubuntu logo, here are the paths to copy in (NOTE: paths are based of Ubuntu 10.04)

If you're using a light theme:
> /usr/share/icons/ubuntu-mono-light/apps/24/start-here.svg

If you're using a dark theme:
> /usr/share/icons/ubuntu-mono-dark/apps/24/start-here.svg

**5. Play around!**
Have a good look around the preferences and what you can do. There is quite a lot you can play with.
You can choose what items you have in the "Favourites" section but right clicking on a menu item (from "All Applications") and choose "Show in my favourites". You can remove items from your favourites by right clicking on them and selected "Remove from favourites".


**6. Known Issue...**
After you ave added it to the panel, you will notice that if you select "All Applications", that there is nothing there, or that there are no sub-menus. No problem, all should be fine and working after a the next reboot.


So there you have it, the Mint Menu in Ubuntu. And remember, Mint is made off Ubuntu so everything is pretty much interchangeable, so don't worry that you're using a menu made for a different 
distro.

ENJOY!

---

### Post by fooey on 2010-08-19
nice write up. thanks!

---

### Post by beameup on 2010-08-19
Thanks for the instructions. Isn't this similar to the menu in OpenSuse Gnome?

---

### Post by rogerdean on 2010-08-19
There's an unbranded version of mintmenu available in the remastersys repo here [http://www.geekconnection.org/remastersys/repository/karmic/](http://www.geekconnection.org/remastersys/repository/karmic/). It doesn't require the mint repo or dependencies

In software sources...
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

then

```
sudo apt-get update
sudo apt-get install mintmenu
```

---

### Post by METZGERR on 2010-08-19
Any way to adjust the colors of the menu?
The bg color, border and topics can be changed, however the text keeps beeing black.

---

### Post by nilarimogard on 2010-08-19
Here is a PPA for this: [https://launchpad.net/~webupd8team/+archive/mintmenu]("https://launchpad.net/~webupd8team/+archive/mintmenu")

And while we're at Mint, here's a PPA for MintBackup too: [https://launchpad.net/~webupd8team/+archive/mintbackup]("https://launchpad.net/~webupd8team/+archive/mintbackup")

---

### Post by fillintheblanks on 2010-08-19
I don't like it.

---

### Post by beameup on 2010-08-19
Ok, it's somewhat similar.


[IMG]http://news.opensuse.org/wp-content/uploads/2008/02/gnome-desktop.png[/IMG]

---

### Post by SoFl W on 2010-08-19
> **beameup said:**
> Thanks for the instructions. Isn't this similar to the menu in OpenSuse Gnome?

I thought that was KDE?  I am not sure.
 I know that is why I stopped using OpenSuse, I disliked the menu.

---

### Post by noob555 on 2010-08-20
Awesome! Thanks!

---

### Post by KdotJ on 2010-08-21
> **beameup said:**
> Thanks for the instructions. Isn't this similar to the menu in OpenSuse Gnome?

Similar, the one in openSUSE I believe is the gnome-main-menu which I mentioned in my post. I like it, but you have to click to get to "Places" and if you want to see all of the applications, you have to open the application browser window.  This is the reason I don't like it, it then becomes not really a menu

---

### Post by JK3mp on 2010-08-28
Made it on lifehacker, congrats. [http://lifehacker.com/5624445/get-the-linux-mint-gnome-menu-in-ubuntu]("http://lifehacker.com/5624445/get-the-linux-mint-gnome-menu-in-ubuntu")

---

### Post by M4570D0N on 2010-10-06
> **nilarimogard said:**
> Here is a PPA for this: [https://launchpad.net/~webupd8team/+archive/mintmenu]("https://launchpad.net/%7Ewebupd8team/+archive/mintmenu")

And while we're at Mint, here's a PPA for MintBackup too: [https://launchpad.net/~webupd8team/+archive/mintbackup]("https://launchpad.net/%7Ewebupd8team/+archive/mintbackup")

There was an update from this ppa yesterday for mintmenu 5.1.3-1~webupd8~maverick .

After installing the update, I no longer have icons displayed for anything in the menus. I checked the preferences and everything looks the same as it was before and the "show category icons" box is still checked. Is anyone else having this issue? How do I resolve this?

---

### Post by M4570D0N on 2010-10-06
^^Issue resolved. I'm apparently half retarded for not noticing what changed.

> Hi,
Yes, this is a known regression, but also an expected one.

mintmenu used to use icon sizes such as 1, 2, 3 or 4.
 
Since yesterday, mintmenu now uses pixels from 1, all the way to 128.  The default values are fine, but the ones you have are still somewhere  between 1 and 4... which now means between 1 and 4 pixels! :)
 
Solutions:

- Right click on the menu, select "Preferences", and change the icon  size for applications, favorites, places and system. Good default values  are respectively 22, 48, 16 and 16.
 
or

- Drop to a terminal. Remove mintmenu from the panel. Type "mintmenu reset". Re-add mintmenu to the panel.

The second solution has the advantage of using all the default values (including the new button icon).

[https://bugs.launchpad.net/linuxmint/+bug/646447](https://bugs.launchpad.net/linuxmint/+bug/646447)

---

### Post by nilarimogard on 2010-10-07
I was just about to reply with the fix. Thanks for posting it :)

---

### Post by sandrafax on 2010-10-23
I like your style. Here are some scarves online you can use it.

---

