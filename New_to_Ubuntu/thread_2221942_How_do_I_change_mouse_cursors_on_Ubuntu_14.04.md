---
title: "How do I change mouse cursors on Ubuntu 14.04?"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by renato3 on 2014-05-04
I downloaded Comix Cursors, extracted it to ~/.icons, installed Unity Tweak Tool, opened "Cursor" tab, selected Comixcursors-slim-black but nothing happens. Whatever cursor I select in this tab won't change anything. Here is a screnshoot:




[IMG]http://s15.postimg.org/qi3bdf9uz/Screenshot_from_2014_05_04_12_41_37.png[/IMG]




I'm using Ubuntu 14.04. Can someone help me, please?

---

### Post by joe_cool2 on 2014-05-06
I'm having the same problem. Is this feature working on Unity? Is there a manual text-mode way of doing this?

---

### Post by gifford on 2014-05-06
Where did you download from?

---

### Post by joe_cool2 on 2014-05-08
> **gifford said:**
> Where did you download from?

I downloaded it from here:

[http://gnome-look.org/content/show.php/ComixCursors?content=32627](http://gnome-look.org/content/show.php/ComixCursors?content=32627)

It's the most downloaded cursor theme on the site and there is no complain. I've already used it in other distros (it's my all time favorite cursor theme) and never had I a problem. Also, all other cursor themes, even the default installed ones, are not working. I select them and they simply won't change. I guess it's an Unity issue.

---

### Post by gifford on 2014-05-08
I am not sure what your problem is. The only recommendation I have is to use Synaptic package manager to do the install. The Comixcursers are in the ppa.
You may be right about it being a Unity issue. I tried changing mine and got mixed results, sometimes the the DMZ-black shows up as opposed to the DMZ-white.
Not sure what the issue is..

---

### Post by joe_cool2 on 2014-05-08
> **gifford said:**
> I am not sure what your problem is. The only recommendation I have is to use Synaptic package manager to do the install. The Comixcursers are in the ppa.
You may be right about it being a Unity issue. I tried changing mine and got mixed results, sometimes the the DMZ-black shows up as opposed to the DMZ-white.
Not sure what the issue is..

Yeah, me too. I installed Comix Cursors from repositories and now I've gotten mixed cursor themes, it's totally bugged... what is going on??

---

### Post by grumblebum2 on 2014-05-08
When changing a mouse cursor theme as well as using a tweak tool you need to install the theme to alternatives and select in alternatives.
You may want to uninstall the comix cursors you installed from the ubuntu repos.

To install to alternatives the downloaded theme needs to have a **cursor.theme** file and in many themes you need to create this file.

eg from your link I downloaded  **ComixCursors-Opaque-0.8.2.tar.bz2** and extracted the archive to my desktop.
I want to install **ComixCursors-Opaque-Slim-Orange** but it doesn't have a **cursor.theme** file.
I need to create by opening gedit and pasting in the following.....
```
[Icon Theme]
Inherits=[COLOR="#FF0000"]ComixCursors-Opaque-Slim-Orange[/COLOR]
```
Use your [COLOR="#FF0000"]theme's name[/COLOR] which will be the same as the folder name.
Save as **cursor.theme** to your themes folder.
[ATTACH=CONFIG]253005[/ATTACH]


Now you need to move your theme to /usr/share/icons 
Open another instance of nautilus as root
```
gksu nautilus /usr/share/icons
```
and copy or move your cursor theme folder to **/usr/share/icons**

 

You need to add your theme to and select with alternatives.
Normally here I would use galternatives (GUI for alternatives) but doesn't seem to work in 14.04  so need to use terminal.

Open a terminal and enter (use the same terminal for all commands as the first command is a variable and will be lost once terminal is closed)
```
CURSOR=[COLOR="#FF0000"]<NAME OF THEME>[/COLOR]
```

eg in this example I would use 
```
CURSOR=[COLOR="#FF0000"]ComixCursors-Opaque-Slim-Orange[/COLOR]
```

Then copy and paste and run the following commands one at a time.
The second gsettings command does the same as using a tweak tool to change cursor so no need to use a tweak tool as well.
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```

You need to logout to complete the change.

PS lol @ the original poster now banned and his beans are** burnt**. :)

---

### Post by joe_cool2 on 2014-05-15
This isn't working no matter what. Whatever theme I select, I get a mixed theme from the one I selected and Dmz-white.

---

### Post by grumblebum2 on 2014-05-15
Check your theme has a cursor.theme file and is installed to /usr/share/icons. Is your theme listed?
```
find /usr/share/icons -name "cursor.theme" | cut -f 5 -d '/' | sort
```


Check what theme is set in dconf.
```
gsettings get org.gnome.desktop.interface cursor-theme
```


Check your cursor theme is installed to and selected in alternatives...
```
sudo update-alternatives --config x-cursor-theme
```

eg mine...
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **find /usr/share/icons -name "cursor.theme" | cut -f 5 -d '/' | sort**
Adwaita
[COLOR="#FF0000"]ComixCursors-Opaque-Slim-Orange[/COLOR]
ComixCursors-Slim-Black
ComixCursors-Slim-Orange
DMZ-Black
DMZ-Black-Medium
DMZ-White
DMZ-White-Large
DMZ-White-Medium
RezoBlack
RingOrange
XenonBlue

[COLOR="#008000"]glen@Trusty:~$[/COLOR] **gsettings get org.gnome.desktop.interface cursor-theme**
'[COLOR="#FF0000"]ComixCursors-Opaque-Slim-Orange[/COLOR]'

[COLOR="#008000"]glen@Trusty:~$[/COLOR] **sudo update-alternatives --config x-cursor-theme**
[sudo] password for glen: 
There are 6 choices for the alternative x-cursor-theme (providing /usr/share/icons/default/index.theme).

  Selection    Path                                                           Priority   Status
------------------------------------------------------------
  0            /usr/share/icons/ComixCursors-Opaque-Slim-Orange/cursor.theme   20        auto mode
[COLOR="#FF0000"]* 1            /usr/share/icons/ComixCursors-Opaque-Slim-Orange/cursor.theme   20        manual mode[/COLOR]
  2            /usr/share/icons/DMZ-Black-Medium/cursor.theme                  20        manual mode
  3            /usr/share/icons/DMZ-Black/cursor.theme                         20        manual mode
  4            /usr/share/icons/DMZ-White/cursor.theme                         20        manual mode
  5            /usr/share/icons/RezoBlack/cursor.theme                         20        manual mode
  6            /usr/share/icons/XenonBlue/cursor.theme                         20        manual mode

Press enter to keep the current choice[*], or type selection number:
```

---

### Post by joe_cool2 on 2014-05-16
There are only 2 cursor themes listed, but I installed a lot of themes _from the repositories_. Could you help, me??

```
find /usr/share/icons -name "cursor.theme" | cut -f 5 -d '/' | sort
DMZ-Black
DMZ-White


```

```
$ gsettings get org.gnome.desktop.interface cursor-theme
'DMZ-White'


```

```
$ sudo update-alternatives --config x-cursor-theme
There are 12 choices for the alternative x-cursor-theme (providing /usr/share/icons/default/index.theme).


  Selection    Path                                     Priority   Status
------------------------------------------------------------
* 0            /usr/share/icons/DMZ-White/cursor.theme   100       auto mode
  1            /etc/X11/cursors/core.theme               30        manual mode
  2            /etc/X11/cursors/handhelds.theme          20        manual mode
  3            /etc/X11/cursors/moblin.theme             50        manual mode
  4            /etc/X11/cursors/oxy-black.theme          40        manual mode
  5            /etc/X11/cursors/oxy-blue.theme           40        manual mode
  6            /etc/X11/cursors/oxy-white.theme          50        manual mode
  7            /etc/X11/cursors/oxy-yellow.theme         40        manual mode
  8            /etc/X11/cursors/oxy-zion.theme           40        manual mode
  9            /etc/X11/cursors/redglass.theme           20        manual mode
  10           /etc/X11/cursors/whiteglass.theme         20        manual mode
  11           /usr/share/icons/DMZ-Black/cursor.theme   30        manual mode
  12           /usr/share/icons/DMZ-White/cursor.theme   100       manual mode


Press enter to keep the current choice
[*], or type selection number:

```

Here are my installed cursor themes from the repositories (all Comix Cursos + some other):

[IMG]http://s10.postimg.org/n0gpvawjt/Screenshot_from_2014_05_16_07_12_01.png[/IMG]

---

### Post by grumblebum2 on 2014-05-16
All those comix cursors need a **cursor.theme** file to register with alternatives.
Tell me exactly which cursor you want to use and I'll help.

The key to having a consistent theme is installing it to alternatives.
To do this the theme whether installed through the repos or downloaded **must have a cursor.theme file**
as explained in post #7.

The comix cursors in the repos draw with a box shadow here, and they do not have cursor.theme files.
[ATTACH=CONFIG]253202[/ATTACH]
I would uninstall and use the ones from the download link posted earlier.

Extract the downloaded archive then choose one of the themes to install.
[ATTACH=CONFIG]253203[/ATTACH]

The rest of the procedure is in post #7 remembering the key is to first create a **cursor.theme**  file
for any theme you chose to move to **/usr/share/icons**
[ATTACH=CONFIG]253204[/ATTACH]

P.S. I don't need replies like "this xxxx isn't working".
I don't work for canonical and I'm not a developer.
I have just found a way to make something that is broken work for me.
It may seem a little complicated but that's just the way it is because
no-one seems to give a crap about cursors in the new world of touch devices.

---

### Post by joe_cool2 on 2014-05-16
My notebook has a touch screen and I hate it, these "new world of touch devices" are pure crap. They are iinaccurately as hell and they are definitely not suitable for FPS games. Anyway, I want **Comixcursors-black-small-slim**. When I select it, I get 2 problems:

1. This box shadow you mentioned
2. The theme is mixed with some Dmz-White cursors.

---

### Post by grumblebum2 on 2014-05-17
Firstly use synaptic or the software center to uninstall the comix cursors you installed from the repos.

I downloaded from your previous gnome-look link the **ComixCursors-Opaque-0.8.2** themes archive.
I extracted to reveal the themes and added a cursor.theme file to the **ComixCursors-Opaque-Slim-Black** theme.
I have attached an archive of the theme with the added cursor.theme file.

Download the attachment and extract the theme.
Place the **ComixCursors-Opaque-Slim-Black** folder in your home folder.
[ATTACH=CONFIG]253233[/ATTACH]

Move the **ComixCursors-Opaque-Slim-Black** folder to **/usr/share/icons** 
Terminal....
```
sudo mv ComixCursors-Opaque-Slim-Black /usr/share/icons
```

Now you need to install and select the theme to alternatives and set the theme in dconf
Terminal... 3 commands to run.
The first command sets the variable [COLOR="#FF0000"]$CURSOR[/COLOR] which is used in the next 2 commands.
```
CURSOR=ComixCursors-Opaque-Slim-Black
```
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/[COLOR="#FF0000"]$CURSOR[/COLOR]/cursor.theme 20
```
```
gsettings set org.gnome.desktop.interface cursor-theme "[COLOR="#FF0000"]$CURSOR[/COLOR]" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/[COLOR="#FF0000"]$CURSOR[/COLOR]/cursor.theme
```

The cursor may be smaller than what you want but let's deal with that once you've logged out/in
and confirm you have a consistent cursor.

---

### Post by Kurt_Alan on 2014-05-17
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

Sorry if this is a repeat.  To change a cursor in Unity 14.04: ```
  sudo update-alternatives --config x-cursor-theme 
```

An * will mark the default.  Select a number of your choice. Enter. Log off, on.

To make that cursor larger: ```
  echo "Xcursor.size:48" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 2 
```

Log off, on.

Thanks to sudodus and grumblebum2 for this.

---

### Post by grumblebum2 on 2014-05-17
**@Kurt_Alan** those commands are part of a set of commands to change the theme and size.
To be listed in the **update-alternatives** command, a downloaded theme needs to first be installed to alternatives which we 
are dealing with now.

---

### Post by joe_cool3 on 2014-05-19
> **Kurt_Alan said:**
> 

Sorry if this is a repeat.  To change a cursor in Unity 14.04: ```
  sudo update-alternatives --config x-cursor-theme 
```

An * will mark the default.  Select a number of your choice. Enter. Log off, on.

To make that cursor larger: ```
  echo "Xcursor.size:48" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 2 
```

Log off, on.

Thanks to sudodus and grumblebum2 for this.

By doing this I do not see comix cursor option :(

---

### Post by joe_cool3 on 2014-05-19
> **grumblebum2 said:**
> Firstly use synaptic or the software center to uninstall the comix cursors you installed from the repos.

I downloaded from your previous gnome-look link the **ComixCursors-Opaque-0.8.2** themes archive.
I extracted to reveal the themes and added a cursor.theme file to the **ComixCursors-Opaque-Slim-Black** theme.
I have attached an archive of the theme with the added cursor.theme file.

Download the attachment and extract the theme.
Place the **ComixCursors-Opaque-Slim-Black** folder in your home folder.
[ATTACH=CONFIG]253233[/ATTACH]

Move the **ComixCursors-Opaque-Slim-Black** folder to **/usr/share/icons** 
Terminal....
```
sudo mv ComixCursors-Opaque-Slim-Black /usr/share/icons
```

Now you need to install and select the theme to alternatives and set the theme in dconf
Terminal... 3 commands to run.
The first command sets the variable [COLOR=#FF0000]$CURSOR[/COLOR] which is used in the next 2 commands.
```
CURSOR=ComixCursors-Opaque-Slim-Black
```
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/[COLOR=#FF0000]$CURSOR[/COLOR]/cursor.theme 20
```
```
gsettings set org.gnome.desktop.interface cursor-theme "[COLOR=#FF0000]$CURSOR[/COLOR]" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/[COLOR=#FF0000]$CURSOR[/COLOR]/cursor.theme
```

The cursor may be smaller than what you want but let's deal with that once you've logged out/in
and confirm you have a consistent cursor.
 
It finally worked and size is perfect, thanks. But does it have to be opaque?? I prefer the translucent ones, but when I installed them the last time, they had a strange square around them.

---

### Post by grumblebum2 on 2014-05-19
The semitransparent cursors are in the  **ComixCursors-0.8.2.tar.bz2** download on the gnome-look page.
You have more than enough info now to
understand how to do it yourself.

[SIZE=3]**1)**[/SIZE] Download and extract the theme.

[SIZE=3]**2)**[/SIZE] Look in the theme folder for a **cursor.theme** file and create one if necessary.
[ATTACH=CONFIG]253300[/ATTACH] [ATTACH=CONFIG]253301[/ATTACH]

[SIZE=3]**3)**[/SIZE] Move the chosen theme to /usr/share/icons ....You can do this by opening another instance of nautilus as root and 
drag and drop your theme folder to /usr/share/icons.
[ATTACH=CONFIG]253302[/ATTACH]
```
gksudo nautilus /usr/share/icons
```


[SIZE=3]**4)**[/SIZE] Run the 3 commands substituting **your theme name**  for [COLOR="#FF0000"]<NAME OF THEME>[/COLOR] in the first command.
```
CURSOR=[COLOR="#FF0000"]<NAME OF THEME>[/COLOR]
```

```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```

[SIZE=3]**5)**[/SIZE] Log out.


P.S.  What happened to joe_cool**2**

---

### Post by bzhao on 2015-02-19
ComixCursors-Opaque-0.8.2.tar.bz2 is downlaoded at:
[http://gnome-look.org/content/download.php?content=32627&id=2&tan=54753354](http://gnome-look.org/content/download.php?content=32627&id=2&tan=54753354)

---

### Post by cmcanulty on 2015-05-11
This is crazy complicated for a simple mouse cursor. I have tried everything mentioned to have a consistent DMZ-Black-Large at 48pt it never shows as an option in the alternatives. I think the issue is getting my theme into the .themes list I have no clue how to do that. This has been a Ubuntu bug for many years. Here is my .index.themes file, but it never shows as an option in alternatives I need large black to see and only firefox will do it

```
[Icon Theme]
Inherits=DMZ-Black-Large
```

---

### Post by CantankRus on 2015-05-15
> **cmcanulty said:**
> This is crazy complicated for a simple mouse cursor. I have tried everything mentioned to have a consistent DMZ-Black-Large at 48pt it never shows as an option in the alternatives. I think the issue is getting my theme into the .themes list I have no clue how to do that. This has been a Ubuntu bug for many years. Here is my .index.themes file, but it never shows as an option in alternatives I need large black to see and only firefox will do it

```
[Icon Theme]
Inherits=DMZ-Black-Large
```
Is the  **DMZ-Black-Large** theme in /usr/share/icons ?
```
ls /usr/share/icons
```

What happens when you run...
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/DMZ-Black-Large/cursor.theme 20
```

---

### Post by cmcanulty on 2015-05-15
yes but I didn't know the number, where does the 20 come from?

---

### Post by CantankRus on 2015-05-15
> **cmcanulty said:**
> yes but I didn't know the number, where does the 20 come from?
It's just a priority number.
The number value itself isn't that important, the command just needs one to work.
> update-alternatives: --install needs <link> <name> <path> <priority>

---

### Post by Novitk on 2015-08-21
> **grumblebum2 said:**
> Firstly use synaptic or the software center to uninstall the comix cursors you installed from the repos.

I downloaded from your previous gnome-look link the **ComixCursors-Opaque-0.8.2** themes archive.
I extracted to reveal the themes and added a cursor.theme file to the **ComixCursors-Opaque-Slim-Black** theme.
I have attached an archive of the theme with the added cursor.theme file.

Download the attachment and extract the theme.
Place the **ComixCursors-Opaque-Slim-Black** folder in your home folder.
[ATTACH=CONFIG]253233[/ATTACH]

Move the **ComixCursors-Opaque-Slim-Black** folder to **/usr/share/icons** 
Terminal....
```
sudo mv ComixCursors-Opaque-Slim-Black /usr/share/icons
```

Now you need to install and select the theme to alternatives and set the theme in dconf
Terminal... 3 commands to run.
The first command sets the variable [COLOR=#FF0000]$CURSOR[/COLOR] which is used in the next 2 commands.
```
CURSOR=ComixCursors-Opaque-Slim-Black
```
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/[COLOR=#FF0000]$CURSOR[/COLOR]/cursor.theme 20
```
```
gsettings set org.gnome.desktop.interface cursor-theme "[COLOR=#FF0000]$CURSOR[/COLOR]" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/[COLOR=#FF0000]$CURSOR[/COLOR]/cursor.theme
```

The cursor may be smaller than what you want but let's deal with that once you've logged out/in
and confirm you have a consistent cursor.

Thanks, it helped me too!

---

### Post by william_morgan on 2015-08-21
Thank you all - very helpful .

---

### Post by Novitk on 2015-08-21
By the way, why is it so difficult to change mouse theme in Ubuntu 14.04 and its flavors? Is there an easier way?

---

### Post by Dennis N on 2015-08-21
> **Novitk said:**
> By the way, why is it so difficult to change mouse theme in Ubuntu 14.04 and its flavors? Is there an easier way?

I wouldn't generalize from Ubuntu to other flavors. In Ubuntu MATE for example, all that's necessary is to choose the cursor in the Appearance Preferences, and your choice is good over all windows and panels. This is what you would want to happen. The one exception is the log in window, which uses the default cursor (DMZ-White) and if you care about changing that, considering the brief time it is in use, the alternatives setting for x-cursor-theme will take care of that as well!

Enjoy your new cursor. May it serve you well.

---

### Post by danang2 on 2015-10-15
this the one i do... 
```
sudo nano /usr/share/icons/default/index.theme
```

and change the line 

```
[Icon Theme]
Inherits=DMZ-Black
```

to 

```
[Icon Theme]
Inherits=[COLOR=#FF0000]ComixCursors-Opaque-Slim-Orange[/COLOR]
```

---

