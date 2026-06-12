---
title: "Creating menu with favourites apps in XFCE."
date: 2009-12-14
forum: Outdated Tutorials &amp; Tips
---

### Post by szamot83 on 2009-12-14
Favourites Apps Menu it was something that (for me) always missing in XFCE. I have some apps which I using everyday, and I don't want to search them in menu. I have decided to make my own menu and share this “HOW TO” with you. 

All menu entries are in those folders:
```
/usr/local/share/applications
/usr/share/applications
~/.local/share/applications
```
(~/ - means your home directory)

When you look into one of those folders you will find plenty of “.desktop” files. Those are all programs which are shown in menu. Every file has similar to each other content. It looks sth. like this.

```
[Desktop Entry]

Version=1.0

Name=Firefox Web Browser

Exec=firefox %u

Terminal=false

X-MultipleArgs=false

Type=Application

Icon=firefox-3.5

Categories=Application;Network;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;

StartupWMClass=Firefox

StartupNotify=true

```

I think that there is nothing to explain – it is easy, so keep focus on “Categories” line. I f you want to make Firefox your favourite application just edit firefox.desktop file (as root) and add “favourite;” word to “categories” line.

Before:
```
Categories=Application;Network;
```
After:
```
Categories=Application;Network;favourite;
```

Now add this word in the same place to several apps which you want to have in favourites menu. 

Now you have to make a choice:
1.I want to have submenu favourites in my XFCE menu
[img]http://img709.imageshack.us/img709/2383/menue.jpg[/img]
2.I want to have menu favourites on panel.
[img]http://img683.imageshack.us/img683/6950/panel.jpg[/img]

[size=150]1[/size]

If you want to do this you'll have to edit xfce-applications.menu. You should find this file in:
```
/etc/xdg/menus/

or 

~/.config/menus
```

If you have file in ~/.config/menus, than do not edit xdg file. The xdg file should be edited as root. In both cases make backup. 

Now this file contains your menu structure. If you want to have favourites submenu in XFCE menu just add those lines:
```

    <Menu>
        <Name>Favourite</Name>
        <Include>
            <Category>favourite</Category>
        </Include>
    </Menu>
```


Before:
```

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
  "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>
    <Name>Xfce</Name>
    
    <DefaultAppDirs/>
    <DefaultDirectoryDirs/>
    
    <Include>
        <Category>X-Xfce-Toplevel</Category>
    </Include>

    <Layout>
        <Filename>xfce4-run-program.desktop</Filename>
        <Separator/>
        <Filename>xfce4-term.desktop</Filename>
        <Filename>xfce4-file-manager.desktop</Filename>
        <Filename>xfce4-web-browser.desktop</Filename>
        <Separator/>
        <Menuname>Settings</Menuname>
        <Separator/>
        <Merge type="all"/>
        <Separator/>
        <Filename>xfce4-help.desktop</Filename>
        <Filename>xfce4-about-xfce.desktop</Filename>
        <Filename>xfce4-logout.desktop</Filename>
    </Layout>
    
    <Menu>
        <Name>Settings</Name>
        <Directory>xfce-settings.directory</Directory>
        <Include>
            <Category>Settings</Category>
        </Include>
        
        <Layout>
            <Filename>xfce-settings-manager.desktop</Filename>
            <Separator/>
            <Merge type="all"/>
        </Layout>
        
        <Menu>
            <Name>Screensavers</Name>
            <Directory>xfce-screensavers.directory</Directory>
            <Include>
                <Category>Screensaver</Category>
            </Include>
        </Menu>
    </Menu>
    
    <Menu>
        <Name>Accessories</Name>
        <Directory>xfce-accessories.directory</Directory>
        <Include>
            <Or>
                <Category>Accessibility</Category>
                <Category>Core</Category>
                <Category>Legacy</Category>
                <Category>Utility</Category>
            </Or>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Development</Name>
        <Directory>xfce-development.directory</Directory>
        <Include>
            <Category>Development</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Education</Name>
        <Directory>xfce-education.directory</Directory>
        <Include>
            <Category>Education</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Games</Name>
        <Directory>xfce-games.directory</Directory>
        <Include>
            <Category>Game</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Graphics</Name>
        <Directory>xfce-graphics.directory</Directory>
        <Include>
            <Category>Graphics</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Multimedia</Name>
        <Directory>xfce-multimedia.directory</Directory>
        <Include>
            <Category>Audio</Category>
            <Category>Video</Category>
            <Category>AudioVideo</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Network</Name>
        <Directory>xfce-network.directory</Directory>
        <Include>
            <Category>Network</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Office</Name>
        <Directory>xfce-office.directory</Directory>
        <Include>
            <Category>Office</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>System</Name>
        <Directory>xfce-system.directory</Directory>
        <Include>
            <Category>System</Category>
        </Include>
    </Menu>

    <Menu>
        <Name>Favourites</Name>
        <Include>
            <Category>favourite</Category>
        </Include>
    </Menu>

</Menu>
```
After:
```

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
  "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>
    <Name>Xfce</Name>
    
    <DefaultAppDirs/>
    <DefaultDirectoryDirs/>
    
    <Include>
        <Category>X-Xfce-Toplevel</Category>
    </Include>

    <Layout>
        <Filename>xfce4-run-program.desktop</Filename>
        <Separator/>
        <Filename>xfce4-term.desktop</Filename>
        <Filename>xfce4-file-manager.desktop</Filename>
        <Filename>xfce4-web-browser.desktop</Filename>
        <Separator/>
        <Menuname>Settings</Menuname>
        <Separator/>
        <Merge type="all"/>
        <Separator/>
        <Filename>xfce4-help.desktop</Filename>
        <Filename>xfce4-about-xfce.desktop</Filename>
        <Filename>xfce4-logout.desktop</Filename>
    </Layout>
    
    <Menu>
        <Name>Settings</Name>
        <Directory>xfce-settings.directory</Directory>
        <Include>
            <Category>Settings</Category>
        </Include>
        
        <Layout>
            <Filename>xfce-settings-manager.desktop</Filename>
            <Separator/>
            <Merge type="all"/>
        </Layout>
        
        <Menu>
            <Name>Screensavers</Name>
            <Directory>xfce-screensavers.directory</Directory>
            <Include>
                <Category>Screensaver</Category>
            </Include>
        </Menu>
    </Menu>
    
    <Menu>
        <Name>Accessories</Name>
        <Directory>xfce-accessories.directory</Directory>
        <Include>
            <Or>
                <Category>Accessibility</Category>
                <Category>Core</Category>
                <Category>Legacy</Category>
                <Category>Utility</Category>
            </Or>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Development</Name>
        <Directory>xfce-development.directory</Directory>
        <Include>
            <Category>Development</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Education</Name>
        <Directory>xfce-education.directory</Directory>
        <Include>
            <Category>Education</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Games</Name>
        <Directory>xfce-games.directory</Directory>
        <Include>
            <Category>Game</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Graphics</Name>
        <Directory>xfce-graphics.directory</Directory>
        <Include>
            <Category>Graphics</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Multimedia</Name>
        <Directory>xfce-multimedia.directory</Directory>
        <Include>
            <Category>Audio</Category>
            <Category>Video</Category>
            <Category>AudioVideo</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Network</Name>
        <Directory>xfce-network.directory</Directory>
        <Include>
            <Category>Network</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>Office</Name>
        <Directory>xfce-office.directory</Directory>
        <Include>
            <Category>Office</Category>
        </Include>
    </Menu>
    
    <Menu>
        <Name>System</Name>
        <Directory>xfce-system.directory</Directory>
        <Include>
            <Category>System</Category>
        </Include>
    </Menu>

    <Menu>
        <Name>Favourites</Name>
        <Include>
            <Category>favourite</Category>
        </Include>
    </Menu>

</Menu>
```

Now save file and favourites submenu should appear. If not – click RMB on XFCE menu, chose properties, then “menu file”, and choose menu file that you have edited. 


[size=150]2[/size]

Make file (in terminal):
```
touch ~/.config/menus/Favourites.menu
```

Edit this and add those lines:

```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
  "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>
    <Name>favourite</Name>
    
    <DefaultAppDirs/>
    <DefaultDirectoryDirs/>
    
    <Include>
        <Category>favourite</Category>
    </Include>
</Menu>
```


Now add “XFCE Menu Panel plugin” to your panel. Click RMB on this menu and choose  properties, then “menu file” and choose favourites.menu which you have edited (~/.config/menus/Favourites.menu). Now it should work.
[b]
-----------------------------------------------------------------------------------------------------[/b]


The worst defect in this tutorial is, that every time you upgrade app the new .desktop file will be written, so you will have to edit this again. To prevent this, just copy your favourites apps .desktop files to "~/.local/share/applications directory", edit them, delete every word after = in categories line and paste there word “favourite”
It should look like this:
Categories=favourite;


That's all.

P.S. I know that my English is poor. If you notice some errors or “hard to understand sentences” just post here. 
P.S.2 Administrator – feel free to edit this.

---

### Post by TheHimself on 2010-01-11
You can just add a launcher to the panel. An xfce launcher can have more than one items in it so it works like a menu. And when you upgrade an application, there is no need to do anything this way.

---

### Post by szamot83 on 2010-01-11
Yes, you have right. But launcher don't have menu funcion, every icon appears on panel - for me menu is better than having 5 icons on panel.


Maybe you would like to add wine submenu to your menu. Lines added to menu file:
```
    <Menu>
        <Name>Wine</Name>
        <Directory>wine-wine.directory</Directory>
        <Include>
            <Category>Wine</Category>
        </Include>
            <Menu>
                <Name>Accesory</Name>
                <Directory>wine-Programs.directory</Directory>
                <OnlyUnallocated/>
                <Include>
                    <All/>
                    <Category>Wine-Programs</Category> 
                </Include>
            </Menu>
    </Menu>

```

I know that there shouldn't be <OnlyUnallocated/, but when I have added category
```
<Category>Wine-Programs-Accessories</Category>
```
Programs not showing, so I decided to add there unallocated files, because on my system only wine programs are showing in "others submenu". 

[img]http://img683.imageshack.us/img683/2141/menuu.jpg[/img]


regards

---

