---
title: "Why can't I make a folder?"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by kohl2 on 2014-11-21
Hey everyone, its been a couple years since I've played with Ubuntu and I'm having some extremely novice seeming problems. 

I want to use this custom cursor that I downloaded. I found the folder it's supposed to go in (Computer>Usr>Share>Icons) but I don't seem to have permission to do anything inside this folder. I am looking to simply make a new folder, name it, and extract the files to that folder.

Thank you for your wisdom!

---

### Post by zircon_34 on 2014-11-22
you can try to fire up the terminal (Alt+Ctrl+T), then open your file manager as root:

```
sudo nautilus
```

try again to make a new folder. 

You can then also right click the path and change permission, but am not sure how wise this is.

---

### Post by mc4man on 2014-11-22
Don't use "sudo nautilus", causes issues.

Open up the folder containing items to be copied in an unmaxed window
Then open a terminal (ctrl+alt+t), copy & paste below command, press enter.
```
sudo -H nautilus
```
Navigate to computer > /usr/share/icons, r. click > New Folder, name & then  go to your other nautilus window, copy the file(s) & paste into  the newly created folder. 
Then close both nautilus windows, terminal,  ect.

---

### Post by yancek on 2014-11-22
Generally,  pretty much anything outside the /home/user directory requires root (sudo) privileges as these are system files.  Y

---

### Post by zircon_34 on 2014-11-23
> **mc4man said:**
> Don't use "sudo nautilus", causes issues.

Why, what type of issues?

---

### Post by bapoumba on 2014-11-23
> **zircon_34 said:**
> Why, what type of issues?

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)
[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

---

### Post by zircon_34 on 2014-11-23
thanks for the links, just learned something

---

### Post by kohl2 on 2014-11-23
So I managed to get the files into a created folder in the 'icons' menu, however unity tweak doesn't seem to read them! theres still only the few options that came with the program! How do I refresh the list it sees/make it visible to the program? Are there any better programs to manage custom cursors?

---

### Post by CantankRus on 2014-11-23
Post a link to where you downloaded cursor from, or the name so I can test here.
Cursor themes need a cursor.theme file.
Does your theme show when running this command...
```
find /usr/share/icons -name "cursor.theme" | cut -f 5 -d '/' | sort
```

---

### Post by deadflowr on 2014-11-23
For what it's worth, you can do the same thing with icons as with themes and install them in the user's home folder.
Open up the Files program, then right click make folder and name it .icons.(include the dot in the front)
Then you can extract the folder into it, without the need for root(sudo).
You can also create the folder during the extraction. 
[The dot will make the folder hidden, but you can enable viewing by either going to the menu item View, and then show hidden files. or simply press ctrl + h]

As for the cursor icons not showing up, did you restart unity-tweak?(I guessing unity tweak tool, though you could mean Ubuntu tweak as well(?))
And, yes, let us know what cursor icon it is...

---

### Post by kohl2 on 2014-11-23
CantankRus - no, that didnt apply the cursor pack.   =(

I downloaded it here: [http://jacksmafia.deviantart.com/art/Knot-Vista-180322118](http://jacksmafia.deviantart.com/art/Knot-Vista-180322118)

Thank all of you guys for the time your putting into this!

---

### Post by CantankRus on 2014-11-23
That's a cursor pack for Windows.
Have a look [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://gnome-look.org/index.php?xcontentmode=36") for cursor themes.

Here is a link describing how to install a downloaded Xcursor theme.
[**_[COLOR="#B22222"]Change mouse cursors on Ubuntu 14.04[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2221942&p=13028225#post13028225")

Unfortunately installing a cursor theme nowadays involves more than just selecting it in a tweak tool.

---

### Post by CantankRus on 2014-11-23
I found the same theme for Linux.
[http://gnome-look.org/content/show.php/KnotVista?content=104468](http://gnome-look.org/content/show.php/KnotVista?content=104468)

Make sure downloaded file "104468-KnotVista.tar.gz" is in your Downloads directory. (important for commands to work)
Open your Downloads folder in the file browser, right click on the downloaded theme and select "extract here" which will extract to a folder named KnotVista.

[U][B]The theme does not have a cursor.theme file.
Create one via terminal...[/B][/U] 
```
gedit ~/Downloads/KnotVista/cursor.theme
```
Copy and paste in to gedit... 
```
[Icon Theme]
Inherits=KnotVista
```
Save and close the gedit file.


_**Move the theme to /usr/share/icons**_
```
sudo mv ~/Downloads/KnotVista /usr/share/icons
```


_**Add to alternatives and select theme**_ (Run each line one at a time)
```
CURSOR=[COLOR="#FF0000"]**KnotVista**[/COLOR]
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```
Log out and backin and you should have new theme.


To reset cursor theme to default just substitute [COLOR="#FF0000"]**KnotVista**[/COLOR] with **[COLOR="#FF8C00"]DMZ-White[/COLOR]**
and run all 3 commands again
ie
```
CURSOR=**[COLOR="#FF8C00"]DMZ-White[/COLOR]**
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```

---

