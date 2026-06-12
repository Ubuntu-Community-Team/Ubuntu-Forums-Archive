---
title: "changing the menu in Lubuntu 12.04"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by s1wood on 2012-12-04
How do I change the main menu in Lubuntu 12.04?  in Xubuntu it's under Settings but I don't seem to have that on Lubuntu.
I really need to get 'Games' off until after Christmas!

Susan

---

### Post by Justin C on 2012-12-04
Does this thread help you?

[http://ubuntuforums.org/showthread.php?t=1676020](http://ubuntuforums.org/showthread.php?t=1676020)

---

### Post by mike555 on 2012-12-04
menu-libre

---

### Post by s1wood on 2012-12-05
The thread suggests deleting things from directories , which sounds a bit permanent.
menu-libre I assumed was a command but comes back 'command not found'. Have I got that wrong?

Susan

---

### Post by mike555 on 2012-12-05
menu-libre should be in the package manager to install.

 opp's, it is " menulibre "

---

### Post by s1wood on 2012-12-09
Well,I installed it but I can't make it take anything offthe menu,it just wants me to add new items!

I'll just have to exert self-control instead.

Susan

---

### Post by zombifier25 on 2012-12-09
Have you tried Alacarte? You can hide/remove entries with it. I use it extensively, but I'm not sure if it works with LXDE, so give it a try.
```
sudo apt-get install --no-install-recommends alacarte
```
The --no-install-recommends flag is for NOT pulling in gnome-shell and gnome-panel.

---

### Post by vasa1 on 2012-12-09
If you don't mind editing xml (text) files using gksudo leafpad or sudo nano or whatever, you could just comment out entries you don't want.
In a standard Lubuntu install there are **two** files that need to be edited:
/etc/xdg/menus/lxde-applications.menu
and
/etc/xdg/lubuntu/menus/lxde-applications.menu

In both, you just comment out entries you don't want to see. The comments for xml files begin with **<!--** and end with **-->**

So, look for the games section and comment it out entirely in both files. Once you're done editing both the files, the change will be visible. No need to log out and back in.

---

### Post by mike555 on 2012-12-09
menulibre works for me ... lets say you want to hide "game-x" , you open menulibre click on games ,click on game-x, uncheck the checkmark at the bottom of the categorizes window, click Menu and save ..... should work.

---

### Post by s1wood on 2012-12-10
I think the problem may be that this is my netbook, with a tiny screen and I am not getting the bottom of the page.
Thanks for all the advice guys, but I think they all amount to more trouble than I want to get into - the aim was to save time!

Thanks anyway,

Susan

---

### Post by agxryt on 2012-12-10
> **s1wood said:**
> How do I change the main menu in Lubuntu 12.04?  in Xubuntu it's under Settings but I don't seem to have that on Lubuntu.
I really need to get 'Games' off until after Christmas!

Susan

Is it just games you want gone? Or do you actually want to change the menu? 

If you remove the default gameset from lubuntu, the menu space will disappear.

```
sudo apt-get purge ace-of-penguins
```

I don't like having games on my laptop either. haha

---

### Post by s1wood on 2012-12-11
I don't want to uninstall my precious games,  just put them out of easy reach  for a while, 

Susan

---

### Post by agxryt on 2012-12-11
> **s1wood said:**
> I don't want to uninstall my precious games,  just put them out of easy reach  for a while, 

Susan

What games are there? 

I think perhaps you can edit .desktop files to hide them.

---

### Post by clarenceweaver on 2013-04-12
The OP want's to know how to change the Main Menu in Lubuntu 12.04. I don't see that question answered so I'll try to explain how to do it manually
without installing any extra packages that you may not need or want. In /etc/xdg/lubuntu/menus/lxde-applications.menu there is a section for each item
in the Main Menu so for example to remove Games from the menu, you look for

    ```

<Menu>
  <Name>Games</Name>
    <Directory>lxde-game.directory</Directory>
    <Include>
      <Category>Game</Category>
    </Include>
</Menu>

```
If you change
```
<Category>Game</Category>
```
to
```
<Category>Games</Category>
```
(note the s) or anything other than 'Game' the item will immediately drop off the Main Menu.
To restore the item, change the Category back to 'Game' and the item will immediately re-appear.

The reason for this is, at least to me, obscure. The short answer is that in the directory
/usr/share/desktop-directories there is a file named lxde-game.directory. Everything between the - and the . in the filename is the category. i.e. 'game'
(The lxde- part is the vendor ID) Any file in /usr/share/applications that has the line Categories=Game; (note the capital G and semicolon) will show up as a submenu
to Games. To find them all go to that directory and type grep Game *

This may seem complicated, but remember the L in LXDE and Lubuntu stands for 'Lightweight' so it's not full of point and click stuff like Gnome and KDE.
The xdg website offers more explanations.

Hope this helps

---

