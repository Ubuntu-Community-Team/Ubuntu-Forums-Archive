---
title: "How to edit your right click menu in Xfce 4.6+"
date: 2009-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Fixel on 2009-03-24
Hey guys, switched to the new Xfce today. The only thing I found to my disliking was that the right click menu was not being easily customizable. Took me about an hour to customize it to my needs so I thought I'd give a quick tut on how to change it and also share my own config. (Check bottom)

First thing you need to do is: backup your xfce-applications.menu-file.

Open a terminal and type:
```
cd /etc/xdg/xubuntu/menus/
sudo cp xfce-applications.menu xfce-applications.menu_bak
```

To verify progress open thunar (or whatever file manager you're using) and browse to "/etc/xdg/xubuntu/menus/" and there should be these two files:
```
xfce-applications.menu
xfce-applications.menu_bak
```

Next step is to edit the actual file. This is where the easy part ends. Open the file as root with your favorite text editor.

```
cd /etc/xdg/xubuntu/menus/
sudo mousepad xfce-applications.menu
```

The top of the document should look like this: 
```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
  "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>
    <Name>Xfce</Name>
    
    <DefaultAppDirs/>
    <DefaultDirectoryDirs/>
    
    <Include>
        <Filename>gnome-app-install-xfce.desktop</Filename>
        <Filename>xubuntu-help.desktop</Filename>
        <Filename>xfce4-about-xfce.desktop</Filename>
        <Filename>xfce4-logout.desktop</Filename>
    </Include>

    <Layout>
        <Filename>gnome-app-install-xfce.desktop</Filename>
        <Separator/>
        <Menuname>Settings</Menuname>
        <Separator/>
        <Merge type="all"/>
        <Separator/>
        <Filename>xubuntu-help.desktop</Filename>
        <Filename>xfce4-about-xfce.desktop</Filename>
        <Filename>xfce4-logout.desktop</Filename>
    </Layout>
    
    <Menu>
        <Name>Settings</Name>
        <Directory>xfce-settings.directory</Directory>
        <Include>
            <Category>Settings</Category>
        </Include>
        <Exclude>
            <Category>System</Category>
        </Exclude>
        
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

```

Now the part we want to focus on is understanding how the file works so that we can edit the different parts. This is what I did:

[B]1) Removed the "Add/Remove...", "Help", "About XFCE" menu items.

2) Moved the Application menus (Accessories, Games, Graphics, Multimedia, Network, Office) into a Application menu.

3) Added shortcuts for most common applications.

4) Made my own launcher. (xkill)[/B]

[SIZE="4"][B][U]
Step 1. Removing entrys:[/U][/B][/SIZE]

At the top of the document there is an <Include> section (originally line 10-15). To remove entrys we first want to remove them from here and then from the <Layout> section just beneath the <Include> section (originally line 17-27).

I removed these three entrys from both the Include and the Layout clauses:
```
<Filename>gnome-app-install-xfce.desktop</Filename>
<Filename>xubuntu-help.desktop</Filename>
<Filename>xfce4-about-xfce.desktop</Filename>
```

Save your file to see if the changes worked. Don't be alarmed if it takes 15 secs to update the menu. If you rightclick on the desktop and the menu doesn't show up it means that you've done something that breaks the app. So:

[SIZE="4"]**_In case of a broken menu:**_[/SIZE]

```
cd /etc/xdg/xubuntu/menus/
sudo rm xfce-applications.menu
sudo cp xfce-applications.menu_bak xfce-applications.menu
```
This restores the original menu. If you're extremely paranoid about your progress I would make a second backup. (Or press ctrl+z in the text editor, save, try the menu again and repeat until it works.)


[B][U]
Step 2. Moving the Accessories, Games, Graphics, Multimedia, Network and office menus into a Application menu[/U][/B]

Open your menu file and go to the part where it says:
```
    <Menu>
        <Name>Accessories</Name>
```
Now you want to add a menu on top of this entry so it looks like this:
```
  [b]<Menu>
             <Name>Applications</Name>[/b]
          <Menu>
        <Name>Accessories</Name>
```
You also have to add a </Menu> below the last sub-menu, which should be "Office" and furthermore look something like this:
```
    <Menu>
        <Name>Office</Name>
        <Directory>xfce-office.directory</Directory>
        <Include>
            <Category>Office</Category>
        </Include>
    </Menu>
**</Menu>**
```

Now you should end up with an "Applications" menu that contains the 6 sub-menus.

**I also did this with the two menus called "System" and "Settings" but added them into a menu called "Options"**

[SIZE="4"][B][U]
Step 1. Adding shortcuts:[/U][/B]
[/SIZE]
Open a new file manager and browse to:
```
/usr/share/applications
```

Open your xfce-applications.menu-file and go to the section called <Include> near the top. Now look in the /usr/share/applications for the program you want to include. 

Now Right-click on the launcher-> Properties -> General (tab)

In file name it should say something like "firefox.desktop"

In the <Include> section you now need to make an entry (in firefox's case) called:

<Filename>firefox.desktop</Filename>

Next step is to add the same thing to the <Layout> section just below. This gives you a "Firefox Web Browser" entry to your right-click menu.

I added the terminal, file manager, firefox, pidgin, banshee to my right-click menu. And they all gave me their "/usr/share/applications" icon name. **DO NOT WANT!**

To change their names in the menu open the launcher in a text editor using using this command for firefox.
```
cd /usr/share/applications/
sudo mousepad firefox.desktop
```

To know the launchers actual file names you can enter this into a terminal:
```
cd /usr/share/applications/
ls
```
This lists the contents of /usr/share/applications/

Moving on to the actual editing, the file you opened should look something like this:

```
[Desktop Entry]
Exec=banshee-1 --redirect-log --play-enqueued %U
Version=1.0
Name=Banshee Media Player
GenericName=Media Player
Comment=Play and organize your media collection
Icon=media-player-banshee
StartupNotify=true
Terminal=false
Type=Application
Categories=GNOME;Audio;Music;Player;AudioVideo;X-Ximian-Main;X-Novell-Main;X-Red-Hat-Base;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=banshee
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=1.4.3
MimeType=application/musepack;application/ogg;application/rss+xml;application/x-ape;application/x-democracy;application/x-extension-m4a
```

What you want to change is the part where it says "Name=Banshee Media Player" to something like this:
```
[Desktop Entry]
Exec=banshee-1 --redirect-log --play-enqueued %U
Version=1.0
**Name=Banshee**
GenericName=Media Player
Comment=Play and organize your media collection
Icon=media-player-banshee
StartupNotify=true
Terminal=false
Type=Application
Categories=GNOME;Audio;Music;Player;AudioVideo;X-Ximian-Main;X-Novell-Main;X-Red-Hat-Base;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=banshee
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=1.4.3
MimeType=application/musepack;application/ogg;application/rss+xml;application/x-ape;application/x-democracy;application/x-extension-m4a
```

If there are many language specific names you'll need to either remove all of them so that you only have "Name=X" left or you need to edit the one for the language you're using.

[SIZE="4"]
[B][U]
Step 4. Add your own launchers:[/U][/B][/SIZE]

Copy an existing *.desktop file and rename it, this example uses the firefox.desktop to create an xkill.desktop. Just substitute xkill for whatever you want your launchers name to be:
```
cd /usr/share/applications/
sudo cp firefox.desktop xkill.desktop
```

Now open the one you created as root with a text editor:
```
cd /usr/share/applications/
sudo mousepad xkill.desktop
```

Remove everything in the text pad and add this instead:
```
[Desktop Entry]
Name=Force Quit
Comment=Force Quit an application 
TryExec=**xkill**
Exec=**xkill**
Icon=utilities-terminal
Type=Application

```


The bold part executes a bash command. There you can insert anything, for instance I modded the terminal to open with "Exec=xfce4-terminal --geometry=70x16"

So go nuts.

Don't forget to change the "Name=X" to whatever you want it to appear as in your menu.

Now just add:
```
<Filename>xkill.desktop</Filename>
```
To both the Include and Layout sections near the top. To add separators just add "<Separator/>" wherever you want it in the Layout section.

This tutorial should give you a good perception of how the new Xfce right-click menu works. Config and screenshot are attached!

---

### Post by BaboonLingo on 2009-03-25
Awesome tut! Been searching far and wide for a guide regarding this. Is there a way to edit the sub-menus? (For instance the Office menu)

From what I can see they don't contain the <Filename>*.desktop</Filename> entries.

---

### Post by Fixel on 2009-03-25
The sub-menus are comprised of *.directory files. Which I haven't tried editing myself. Alas you can always remove (or comment out) the *.directory line and enter all the <Filename>*.desktop</Filename> lines you want for that specific sub-menu.

I reccommend not editing the *.directory files (if this is even possible) since that would take longer to restore. Using the above method you'd get a custom menu that would easily be restorable by just commenting out the *.desktop lines and adding the old *.directory.

To comment something out I do believe you make it look somewhat like this:

```
**<!**[THIS WILL BE COMMENTED OUT]**>**
```

Finally: welcome to the forum!

---

### Post by pneukamp on 2009-04-19
Congratulations for the post! I wonder if the XFCE is to merge as the Gnome menus? I have a custom menu in gnome in (/etc/xdg/menus/applications-merged/forensic.menu) Which is automatically inserted in the main menu. Can this work in XFCE?

---

### Post by Person98 on 2009-05-02
Thanks for the tips they have been a great help, i just have one question, I have been editing my menus and was wondering if you knew where the .directory files are kept i can't seem to find them.

---

### Post by Brandon Williams on 2010-01-15
This thread is kind of old, but I just saw it for the first time because someone else referred to it in another thread. The tutorial is good in terms of the mechanics of editing the menu XML file and/or application launchers. However, it is advisable not to edit the installed version of these files. Instead, make copies of your own and edit those.

For editing the menu, do this first:
```
[ -d ~/.config/menus ] || mkdir -p ~/.config/menus
cp /etc/xdg/xubuntu/menus/xfce-applications.menu ~/.config/menus/
```
Log out. Log back in. And then:
```
mousepad ~/.config/menus/xfce-applications.menu
```
The rest of the details about editing this file are the same as in the original post.

For editing applications launchers, do this:
```
[ -d ~/.local/share/applications/ ] || mkdir -p ~/.local/share/applications
```
Now, for any existing .desktop file in /usr/share/applications/ that you want to modify, first copy it to ~/.local/share/applications/ and copy that file instead. For example, to edit the firefox launcher, as in the original post:
```
cp /usr/share/applications/firefox.desktop ~/.local/share/applications/
mousepad ~/.local/share/applications/firefox.desktop
```
Now, you can edit the file as indicated in the original post.

If you want to add custom launchers, add them to ~/.local/share/applications/ instead of /usr/share/applications/, and don't use sudo when opening them, since you will own the files yourself.

This method is better protected against accidental over-writes when packages are updated.

---

### Post by Chiapo on 2010-01-17
Cool! 

Thanks for sharing!

---

### Post by nzjethro on 2011-06-14
This is awesome dude, good on you.

---

