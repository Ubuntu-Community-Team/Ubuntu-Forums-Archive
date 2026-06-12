---
title: "Newly installed programs don't show in Applications Menu?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Gael33 on 2008-08-01
Some of the newly installed programs are not listed in the Applications Menu, for example; File-Roller. How do I get these programs listed in the Menu for easy usage.
Thanks,
Gael.

---

### Post by t0p on 2008-08-01
If you right-click on, say, Applications, you will get an option to **Edit Menus** - this will then enable you to add items to your menus.

---

### Post by tuxxy on 2008-08-01
System > Prefs > Main Menu 

Select your desired location and then click Add item, add your newly installed app, the command to launch it is usually just the appname for example firefox would launch your browser.

---

### Post by Gael33 on 2008-08-01
> **t0p said:**
> If you right-click on, say, Applications, you will get an option to **Edit Menus** - this will then enable you to add items to your menus.

Hmmm! I've done that bit and they're not even listed although Synaptic Package Manager tells me they are installed, very odd :confused:

Gael.

---

### Post by Gael33 on 2008-08-01
> **tuxxy said:**
> System > Prefs > Main Menu 

Select your desired location and then click Add item, add your newly installed app, the command to launch it is usually just the appname for example firefox would launch your browser.

Thanks for that, but isn't that the same as right clicking on the Applications Icon?
The needed programs are not listed in the menu :(

Gael.

---

### Post by Diabolis on 2008-08-01
Not all the programs are designed to be listed in the menu, thats how the developers made them. If you want them to show up, you'll have to craft custom launchers and then add them to you menu.

You may also run this command if you think that something should be showing and is not.
```
update-menus
```

---

### Post by oldos2er on 2008-08-01
> **Gael33 said:**
> Some of the newly installed programs are not listed in the Applications Menu, for example; File-Roller. How do I get these programs listed in the Menu for easy usage.
Thanks,
Gael.

 Isn't File Roller called Archive Manager (or something similar) in the menus?

---

### Post by Gael33 on 2008-08-01
> **Diabolis said:**
> Not all the programs are designed to be listed in the menu, thats how the developers made them. If you want them to show up, you'll have to craft custom launchers and then add them to you menu.

You may also run this command if you think that something should be showing and is not.
```
update-menus
```

I appreciate that not all programs will be listed in Applications, especially programs that work behind the scenes. Having said that, I would expect to find most first line programs like Wine, File-Roller etc listed in the menu for ease of use.
I get the feeling that using the Packet Manager is not always the best way to install these programs.
If you have any more ideas I would be grateful to receive them.

Gael.

---

### Post by Gael33 on 2008-08-01
> **oldos2er said:**
> Isn't File Roller called Archive Manager (or something similar) in the menus?

Yes, your quite correct ... File-Roller is listed as Archive Manager ... unfortunately, it isn't listed in my Applications by any name :(
I'll try to install them again using the Terminal (not a name I particularly like) and see if I am successful. Either way I'll let you know ;)

Gael keeping fingers crossed :)

---

### Post by oldos2er on 2008-08-01
Can't you simply create a launcher for /usr/bin/file-roller ?

---

### Post by Gael33 on 2008-08-01
> **oldos2er said:**
> Can't you simply create a launcher for /usr/bin/file-roller ?

That sounds like a good idea ... how do I do that?
As an absolute beginner working with Ubuntu the concept of typing commands is fairly new to me, so my question "how do I do that" is founded on inexperience.
Is a "launcher" the same as a "Shortcut" in Windows?

Thanks in advance for your help ;)

gael.

---

### Post by Diabolis on 2008-08-01
Yes, a launcher is like windows shortcut.

The menus that appear in your menu are stored in this folder: **/usr/share/applications**

The files contained in this folder have the extension **.desktop**. They are actually plain text documents with a "special" format.

Just to give you an idea, this is the one that is created when you install emesene:
```

**cat /usr/share/applications/emesene.desktop **
[Desktop Entry]
Name=Emesene
GenericName=Emesene
Comment=MSN Messenger client
Exec=emesene
Icon=emesene
Terminal=false
Type=Application
Categories=Network;InstantMessaging;

```

You can create any desktop configuration file to suit your needs. Doing this is kind of hackish because gnome already has the tools to achieve this with your mouse.

For a quick solution, just right click in your gnome panel and create a launcher.

---

### Post by oldos2er on 2008-08-02
> **Gael33 said:**
> That sounds like a good idea ... how do I do that?
As an absolute beginner working with Ubuntu the concept of typing commands is fairly new to me, so my question "how do I do that" is founded on inexperience.
Is a "launcher" the same as a "Shortcut" in Windows?

Thanks in advance for your help ;)

gael.

This assumes you're using Gnome: Right-click on a free spot on your top panel, click 'Add to Panel'. Then click 'Custom Application Launcher', then 'Add'. In Name: type in Archive Manager, in Command, type in /usr/bin/file-roller then Ok.

---

### Post by SunnyRabbiera on 2008-08-02
Yeh some apps dont have menu entries for some odd reason.

---

### Post by photoman64 on 2008-08-05
I have some problem.Even Wine do not show up. How do I switch to KDE?
Gnome look like do not perform well.

---

### Post by Diabolis on 2008-08-05
> **photoman64 said:**
> I have some problem.Even Wine do not show up. How do I switch to KDE?
Gnome look like do not perform well.

If you want to use KDE, just install it.
```
sudo apt-get update
sudo apt-get install kubuntu-kde4-desktop
```

Which version of wine are you using?
```
wine -version
```

---

### Post by photoman64 on 2008-08-06
When I did the wine -version I was told that the wine it is not installed and then I was told that type apt-get install wine and so I did.
The wine it is installed and show in menu. I installed the first time usin Synaptic and then I was told that program it is installed.
I think that Synaptic have a problem. Any other package installer I can use?
Is ther any program that will scan my HD and put installed programs on my menu?
Thanks

---

### Post by gioland71 on 2008-08-06
That's odd. Synaptic is only a gui front end to apt-get...

---

