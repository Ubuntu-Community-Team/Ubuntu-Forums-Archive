---
title: "Desktop launchers"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by mijdrawoh on 2012-04-20
12.04.  How do you create URL desktop launchers in 12.04?  Right clicks on the desktop no longer offer that capability.

---

### Post by lincoln32 on 2012-04-20
if you open the program in dash it will add the icon while it is open
then you can right click on the icon and keep it in the lancher
but I have not yet found a app that has no defult icon in dash:KS

---

### Post by mijdrawoh on 2012-04-20
I want to put shortcuts for URL's on the desktop, not apps, e.g. the Ubuntu Forum or my bank.

---

### Post by Dngrsone on 2012-04-20
Unfortunately, it is a matter of creating your own.

[This site](http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available) has an extensive list of custom launchers and quicklists to choose from, but are a little short on details of creating your own; also there are a few differences between the formats used in 11.x and 12.04.

Here's a quick rundown, from my experience:

Open your text editor, gedit by clicking Dash Home (the top icon on your launcher bar) and entering **gedit**.  There should be an icon labelled 'Text Editor', select that.  You will want to save your file as *something*.desktop (whatever you want to name your launcher, with a .desktop suffix).

Use the following as a template:

```

[Desktop Entry]
Version=1.0
Type=Link
Name=Link to Ubuntu Forums
Comment=The best forums there are!
URL=ubuntuforums.org
Icon=/home/username/.icons/url.png

```

The items should be self-explanatory.  Since this is a launcher for an Internet link, it is not as complex as an application launcher. the item **Name** will be the name of the link when you hover your mouse over it.  **URL** of course points your browser to the sire you want, and the **Icon** item will point to the icon you want to use on your launcher bar.

The best resource I have for Launchers is the [Launcher Specifications Reference](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html)

Oh, if you want to launch an URL with a specific browser, then you will need to create an application launcher with an optional target url.

---

### Post by hakermania on 2012-04-21
Shame. Shame. Shame :(

I know how to create launchers and such things but how can't developers of ubuntu not that desktop launchers aside from unity bar are essential for many users?

---

### Post by NikTh on 2012-04-21
```
sudo apt-get install --no-install-recommends gnome-panel
``````
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```a familiar window will appear that allows you to create your launcher.

---

### Post by hakermania on 2012-04-21
> **NikTh said:**
> ```
sudo apt-get install --no-install-recommends gnome-panel
``````
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```a familiar window will appear that allows you to create your launcher.


Sorry for the 'correction', but shouldn't it be:
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```providing that he wants the launcher to be to desktop?

[greek]E filaraki?[/greek]

---

### Post by NikTh on 2012-04-21
> **hakermania said:**
> Sorry for the 'correction', but shouldn't it be:
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```providing that he wants the launcher to be to desktop? E filaraki?

For desktop yes . You're right. 
swstos ! :p

---

### Post by ex_isp on 2012-04-21
> **hakermania said:**
> Sorry for the 'correction', but shouldn't it be:
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```providing that he wants the launcher to be to desktop?

[greek]E filaraki?[/greek]

Wow!  Thank you for this!  This issue has been my main gripe about Lisa (Mint).  Anyone have any thoughts on why this has not been incorporated into right button functionality yet?

I do truly miss drag-n-drop from the menu!

---

### Post by goblue62 on 2012-04-21
That works. :p  However,In a Mint posting, I found out how to establish the capability to right click on the desktop and create a launcher once gnome is installed. The solution is to put a document containing "gnome-desktop-item-edit ~/Desktop/ --create-new"  in the /home/username/.gnome2 nautilus-scripts folder (.gnome2 is a hidden file). The document first has to have "allow executing file as program" checked in Properties/Permissions. After the appropriate saves and closes, a right desktop click gives the option of "Scripts>Create New Launcher" which has options to create launchers for both Locations and Applications.

---

### Post by hakermania on 2012-04-21
> **ex_isp said:**
> Wow!  Thank you for this!  This issue has been my main gripe about Lisa (Mint).  Anyone have any thoughts on why this has not been incorporated into right button functionality yet?

I do truly miss drag-n-drop from the menu!

Hey, hold your horses ;) All credits go to NikTh, he suggested this command.

Anyway, I also believe that it is tragic not to have something in order to create a simple launcher. :(

I really don't know what they are thinking!

---

