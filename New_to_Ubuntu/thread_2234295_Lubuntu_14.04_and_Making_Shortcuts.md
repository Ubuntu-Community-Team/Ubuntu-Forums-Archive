---
title: "Lubuntu 14.04 and Making Shortcuts"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by megazell2 on 2014-07-13
Hey,

I am trying to make a shortcut for a game. I am new to Lubuntu but very familiar with Linux Mint. I don't see anyway to create a application launcher. Any help?

---

### Post by vasa1 on 2014-07-13
> **megazell2 said:**
> Hey,

I am trying to make a shortcut for a game. ...
Details?

---

### Post by Dennis N on 2014-07-13
> **megazell2 said:**
> Hey,

I am trying to make a shortcut for a game. I am new to Lubuntu but very familiar with Linux Mint. I don't see anyway to create a application launcher. Any help?

If the game shows up in the Main Menu, you can right-click on the game and select "add to desktop" which creates a launcher on the desktop.

If you want a launcher on a panel, right-click on the panel, select "Panel Settings", then the "Panel Applets" tab. Select "Application Launch Bar", then click the Edit button. In the next window, select the game from the Available Applications on the right, the click the "+ Add" button. Finally, you can position it on the launch bar with the Up and Down Buttons. Close the windows.

---

### Post by megazell2 on 2014-07-14
> **vasa1 said:**
> Details?

Right - So I have the latest version of AssaultCube which is different from the Software Manager's version.

I would like to made an icon/shortcut for it on the DESKTOP and the Menu. As it stands right now, I am unable to bring up any editor or launcher menu to make one.

---

### Post by megazell2 on 2014-07-14
> **Dennis N said:**
> If the game shows up in the Main Menu, you can right-click on the game and select "add to desktop" which creates a launcher on the desktop.

If you want a launcher on a panel, right-click on the panel, select "Panel Settings", then the "Panel Applets" tab. Select "Application Launch Bar", then click the Edit button. In the next window, select the game from the Available Applications on the right, the click the "+ Add" button. Finally, you can position it on the launch bar with the Up and Down Buttons. Close the windows.

What about for games that I downloaded and are not available in PPA or Software Center. The games work when I click the .sh file but I would like to make a desktop icon and menu icon for them.

---

### Post by Dennis N on 2014-07-14
> **megazell2 said:**
> What about for games that I downloaded and are not available in PPA or Software Center. The games work when I click the .sh file but I would like to make a desktop icon and menu icon for them.

Create a Main Menu Entry for an Application

If you have no entry in the main (application) menu for the program, you need to create a .desktop file to have it appear there. Once in the main menu, you can create a Desktop or panel launcher using methods of post #3. Any program which appears in the menu has a .desktop file stored in two possible places:

1) /usr/share/applications
2) ~/.local/share/applications

If you should have one in both places, location 2 is used.

Example of a .desktop file:

```
[Desktop Entry]
Name=Machinarium
Comment=Play Machinarium
Exec=/opt/games/Machinarium/Machinarium
Categories=Game;
Icon=/opt/games/Machinarium/machinarium-icon-3a.png
Type=Application

```
note - Categories line should end with a ;

Make one for your game, then save it with the extension .desktop in **~/.local/share/applications**
Log out and back in and it should be in the main menu under games.

Reference on possible categories:
[http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

Reference for study on technical details:
[http://standards.freedesktop.org/desktop-entry-spec/latest/index.html](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html)
[http://www.freedesktop.org/wiki/Specifications/menu-spec/](http://www.freedesktop.org/wiki/Specifications/menu-spec/)

---

### Post by megazell2 on 2014-07-14
^ Most excellent. Ty very much. This did the trick.

---

### Post by megazell2 on 2014-08-11
I just recently tried to do this again and I am unable to save the .desktop files in the [COLOR=#000000]/usr/share/applications [/COLOR]  due to write protection. How do I overcome this in the GUI? I know of a way to do it in terminal via PICO but I am hoping for a GUI method for speed as I have a ton of games I need to do this for.

---

