---
title: "How to install themes in Ubuntu 14.04.1 LTS 64-bit Unity, what is the easiest way?"
date: 2015-01-03
forum: New to Ubuntu
---

### Post by Vesnog on 2015-01-03
Greetings,

I just installed Ubuntu 14.04.1 LTS 64-bit with Unity desktop environment a few days ago and I would like to customize it with **GTK, cursor, icon and window themes.  **First of all, where can I download themes compatible with my OS and how I can understand whether they are compatible or not if there is no explicit statement(I also know that there is a GNOME desktop environment for Ubuntu). Apart from that some themes install from **PPAs **whereas some of them are supplied as zipped/compressed files which are to be extracted into the correct directory. Some threads I read here and on AskUbuntu state that I should extract **icon **themes into ***~/.icons ***and **GTK and window **themes into ***~/.themes*** inside my home directory. Moreover, other tutorials say that I should extract them somewhere over ***/usr/share/themes*** for regular **GTK **and **windows **themes and over ***/usr/share/icons ***for **icon and cursor **themes. Furthermore I also installed **Ubuntu Tweak Tool **to be able to change themes easily but although **icon themes **could be changed; I observed that when I changed the **cursor theme** the appeareance of the cursor changed as I hovered it between different application windows and Desktop. This situation was remedied by running the following commands:

```
$ sudo update-alternatives --config x-cursor-theme
There are 7 choices for the alternative x-cursor-theme (providing /usr/share/icons/default/index.theme).

  Selection    Path                                       Priority   Status
------------------------------------------------------------
  0            /usr/share/icons/DMZ-White/cursor.theme     100       auto mode
  1            /etc/X11/cursors/core.theme                 30        manual mode
  2            /etc/X11/cursors/handhelds.theme            20        manual mode
  3            /etc/X11/cursors/redglass.theme             20        manual mode
  4            /etc/X11/cursors/whiteglass.theme           20        manual mode
  5            /usr/share/icons/DMZ-Black/cursor.theme     30        manual mode
  6            /usr/share/icons/DMZ-White/cursor.theme     100       manual mode
* 7            /usr/share/icons/mac-cursors/cursor.theme   90        manual mode

Press enter to keep the current choice
[*], or type selection number: 

```

However, I also noticed that this list lacked some of the **cursor themes** I extracted into the ***~/.icons*** ****directory, these were visible under **Ubuntu Tweak Tool **though. Did I mess my system up? I also have unhidded **~/icons** and **~/themes **directories inside my home directory filled with zipped versions of theme files. Do these have any effect on system themes? Note that, I had this particular home directory mounted as home on my previous *Ubuntu 12.04.5 LTS 32-bit *system and I do not remember whether I created them or not. I would really appreciate your assistance and guidance through installing themes the proper way.

N.B: I also noticed that changing the **window theme **did not have much effect and the program **Unity Tweak Tool **forced change of the **GTK theme **together with the **windows **theme, why is this so?

---

### Post by thiebaude on 2015-01-03
Are you trying to install a mac osx theme

---

### Post by Frogs Hair on 2015-01-03
Themes extracted in .themes/icons only appear for individual users and themes usr/share/themes or icons are available for all users.14.04 requires GTK 3.10 themes.. PPA's are pretty easy to use and linked is a well known one. If not using a PPA I download thepackage right click and select extract here and manually move the themes to .themes or usr/share/themes . 

[http://www.noobslab.com/p/themes-icons.html](http://www.noobslab.com/p/themes-icons.html)

[http://gnome-look.org/](http://gnome-look.org/)

---

### Post by Vesnog on 2015-01-03
> **thiebaude said:**
> Are you trying to install a mac osx theme

One of my aims is to achieve that. By the way although applications such as Unity Tweak Tool recognize different cursor-themes, I cannot set them by running the following command:

```
sudo update-alternatives --config x-cursor-theme
```

Hence, the cursor changes theme while moving from window to window which is really distracting and annoying.

---

### Post by Vesnog on 2015-01-03
> **Frogs Hair said:**
> Themes extracted in .themes/icons only appear for individual users and themes usr/share/themes or icons are available for all users.14.04 requires GTK 3.10 themes.. PPA's are pretty easy to use and linked is a well known one. If not using a PPA I download thepackage right click and select extract here and manually move the themes to .themes or usr/share/themes . 

[http://www.noobslab.com/p/themes-icons.html](http://www.noobslab.com/p/themes-icons.html)

[http://gnome-look.org/](http://gnome-look.org/)

I have installed a few themes through PPAs but not all themes I find appealing are available on PPAs; therefore I might have to manually download and extract them. By the way where does the themes installed via PPAs get installed into. Furthermore, while manually installing do you extract the window and GTK theme into the themes directory right, what about the icon and cursor themes? The application Unity Tweak Tool recognize more cursor themes than the following command:

```
sudo update-alternatives --config x-cursor-theme
``` 

If I cannot set the cursor theme through **update-alternatives **to a particular one and set it only using GUI programs such as UTT or Gnome Tweak Tool etc. my cursor theme changes while hovering the mouse over.

---

### Post by Frogs Hair on 2015-01-03
PPA'a use the usr/share/themes directory. To manually add themes to that location  the file system needs to be opened with elevated privileges.```
 gksudo nautilus  
```

---

### Post by Vesnog on 2015-01-03
> **Frogs Hair said:**
> PPA'a use the usr/share/themes directory. To manually add themes to that location  the file system needs to be opened with elevated privileges.```
 gksudo nautilus  
```

Thanks but what about the cursor changing theme as hovering over different applications/windows when set to a particular **cursor-theme **via **Unity Tweak Tool **etc. How can I avoid this behaviour?

---

### Post by Dennis N on 2015-01-03
Your cursor theme folders have to be in **/usr/share/icons** before update-alternatives can be used. 

Before you can select them with
```
sudo update-alternatives --config x-cursor-theme
```
you need to install them with
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/CursorName/cursor.theme 20
```
replace **CursorName** in this command with the name shown on the cursor folder.

more on next post:

---

### Post by Dennis N on 2015-01-03
More Information:

You may also still have to select the cursor with Ubuntu Tweak after doing the above. The above commands make the chosen cursor the default. You need to check inside the cursor's folder to be sure it has a **cursor.theme** file before using them. If it doesn't you have to make one and put it in the folder. It's a text file that looks like this:

```
[Icon Theme]
Inherits=CursorName
```

Again, CursorName is the name that appears on the cursor folder.

After doing all this, the cursor should not vary.

---

### Post by Vesnog on 2015-01-03
> **Dennis N said:**
> More Information:

You may also still have to select the cursor with Ubuntu Tweak after doing the above. The above commands make the chosen cursor the default. You need to check inside the cursor's folder to be sure it has a **cursor.theme** file before using them. If it doesn't you have to make one and put it in the folder. It's a text file that looks like this:

```
[Icon Theme]
Inherits=CursorName
```

Again, CursorName is the name that appears on the cursor folder.

After doing all this, the cursor should not vary.

Thanks for the information apart from **GUI  **tools how can I change everything manually from the **CLI **the GTK theme, window theme, cursor and icon themes? What about the priority number by the way does it set anything or may it be the cause of varying cursor? Furthermore, I sometimes get errors as follows when I launch **UTT  **and some of the features of this tool does not work although I installed a newer version from a PPA and tried running it with superuser privileges(the older one never launched at all). 

One more question: Why do I have to alter the cursor theme from both the update-alternatives menu and a tweak tool? Why altering it from one is not sufficient?

---

### Post by Dennis N on 2015-01-03
Good questions. I don't believe you can change any theme only from the command line. It requires a gui dialog. Usually under system settings there is an Appearance dialog. Unity does not offer much in its standard settings - they really don't seem to want users to change much. That's why others have made the tools such as Ubuntu Tweak. The information about themes given here seems correct. After the folder is located in the right place, you have to use a gui dialog to change it. Maybe the Appearance dialog will work, or else Ubuntu Tweak. Not all themes will work with Unity and they don't show up in the dialogs! You can't use them. 

Much easier to change themes and cursors with some of the other distros - especially Ubuntu Mate, which uses the same dialogs as the old Gnome2 Ubuntu that was used before Ubuntu 11.04.

Your last question I cant answer, but Ubuntu Mate is one distro where all this can be done from the Appearance dialog - no command line needed. if you use Unity, you have to accept reality.

---

### Post by Dennis N on 2015-01-03
Forgot part about the "priority number" - It has to be in the command, but what it is has no effect. It can be lower than on the other choices but still used, because what is important is that when the user manually changes the cursor himself, that choice is used by the system as default regardless of priority until it is changed again.

---

### Post by Vesnog on 2015-01-04
I think I have messed up with **update-alternatives** after trying the following commands(I created a .theme file inside the /etc/X11/cursors directory):

```
sudo update-alternatives --install /usr/share/icons/ComixCursors-Opaque-Black/cursor.theme x-cursor-theme /etc/X11/cursors/comixcursors-opaque-black.theme 30
sudo update-alternatives --install /etc/X11/cursors/comixcursors-opaque-black.theme x-cursor-theme /usr/share/icons/ComixCursors-Opaque-Black/cursor.theme 40
sudo update-alternatives --config x-cursor-theme
compiz --replace
sudo update-alternatives --remove x-cursor-theme /usr/share/icons/ComixCursors-Opaque-Black/cursor.theme
cd /etc/X11/cursors/
```

Create a file named `comix-opaque-black.theme` in */etc/X11/cursors* and then 

```
sudo update-alternatives --install /etc/X11/cursors/comix-opaque-black.theme x-cursor-theme /usr/share/icons/ComixCursors-Opaque-Black/cursor.theme 40
update-alternatives: warning: forcing reinstallation of alternative /usr/share/icons/DMZ-White/cursor.theme because link group x-cursor-theme is broken
```
$ sudo update-alternatives --config x-cursor-themes
update-alternatives: error: no alternatives for x-cursor-themes


> **Dennis N said:**
> Forgot part about the "priority number" - It has to be in the command, but what it is has no effect. It can be lower than on the other choices but still used, because what is important is that when the user manually changes the cursor himself, that choice is used by the system as default regardless of priority until it is changed again.

---

### Post by CantankRus on 2015-01-04
Deleted so as not to confuse.

---

### Post by Dennis N on 2015-01-04
> **Vesnog said:**
> 
$ sudo update-alternatives --config x-cursor-themes
update-alternatives: error: no alternatives for x-cursor-themes

**sudo update-alternatives --config x-cursor-themes**

should be:

**sudo update-alternatives --config x-cursor-theme**

there is no 's' on the end.

---

### Post by Dennis N on 2015-01-04
You are also getting two different procedures given as responses, so that is probably going to cause confusion.

---

### Post by Dennis N on 2015-01-04
> I think I have messed up with update-alternatives after trying the following commands(I created a .theme file inside the /etc/X11/cursors directory):

I don't know why you are doing this - the cursors belong in **/usr/share/icons**.

```
warning: forcing reinstallation of alternative /usr/share/icons/DMZ-White/cursor.theme because link group x-cursor-theme is broken
```

This looks ominous. Not sure what it implies. Is the cursor still working? Sorry, I don't understand the steps you took - they are not what I suggested (post #8).
You might try:
```
sudo update-alternatives --config x-cursor-theme
```
again, to see what the status is, but note there is no 's' on theme (post #15).

---

### Post by CantankRus on 2015-01-04
Sorry didn't realize it was a private thread.
I'll opt out then.

---

### Post by Dennis N on 2015-01-04
I was just advising the OP that two different methods are being suggested. That all. Sorry that may have come across the wrong way.

---

### Post by Vesnog on 2015-01-04
Yeah you are right I was a bit confused and I wanted to be able to all the options possible when I typed ```
sudo update-alternatives --config x-cursor-theme
``` Actually when I type the code I get entries as follows, but I also the **ComixCursor series** to show up in this list as well so I decided to do something like that. Apart from that my theme files are placed in */usr/share/icons *but **Tweak Tools** are not able to distinguish between cursor-themes and icon-themes; how can I have them make that distinction? One of my motivations in placing the .theme file in the etc directory was to prevent this interference.

```
$ sudo update-alternatives --config x-cursor-theme
There are 46 choices for the alternative x-cursor-theme (providing /usr/share/icons/default/index.theme).

  Selection    Path                                                     Priority   Status
------------------------------------------------------------
  0            /usr/share/icons/DMZ-White/cursor.theme                   100       auto mode
  1            /etc/X11/cursors/core.theme                               30        manual mode
  2            /etc/X11/cursors/handhelds.theme                          20        manual mode
  3            /etc/X11/cursors/oxy-black.theme                          40        manual mode
  4            /etc/X11/cursors/oxy-blue.theme                           40        manual mode
  5            /etc/X11/cursors/oxy-bluecurve.theme                      30        manual mode
  6            /etc/X11/cursors/oxy-brown.theme                          30        manual mode
  7            /etc/X11/cursors/oxy-cherry.theme                         30        manual mode
  8            /etc/X11/cursors/oxy-chrome.theme                         30        manual mode
  9            /etc/X11/cursors/oxy-desert.theme                         30        manual mode
  10           /etc/X11/cursors/oxy-emerald.theme                        30        manual mode
  11           /etc/X11/cursors/oxy-green.theme                          30        manual mode
  12           /etc/X11/cursors/oxy-grey.theme                           30        manual mode
  13           /etc/X11/cursors/oxy-honeycomb.theme                      30        manual mode
  14           /etc/X11/cursors/oxy-hot_orange.theme                     30        manual mode
  15           /etc/X11/cursors/oxy-lilac.theme                          30        manual mode
  16           /etc/X11/cursors/oxy-midnight_meadow.theme                30        manual mode
  17           /etc/X11/cursors/oxy-navy.theme                           30        manual mode
  18           /etc/X11/cursors/oxy-norway.theme                         30        manual mode
  19           /etc/X11/cursors/oxy-obsidian-hc.theme                    30        manual mode
  20           /etc/X11/cursors/oxy-obsidian.theme                       30        manual mode
  21           /etc/X11/cursors/oxy-olympus-inv.theme                    30        manual mode
  22           /etc/X11/cursors/oxy-olympus.theme                        30        manual mode
  23           /etc/X11/cursors/oxy-orchid.theme                         30        manual mode
  24           /etc/X11/cursors/oxy-oxygen.theme                         30        manual mode
  25           /etc/X11/cursors/oxy-peach.theme                          30        manual mode
  26           /etc/X11/cursors/oxy-purple.theme                         30        manual mode
  27           /etc/X11/cursors/oxy-red-argentina.theme                  30        manual mode
  28           /etc/X11/cursors/oxy-red.theme                            30        manual mode
  29           /etc/X11/cursors/oxy-sea_blue.theme                       30        manual mode
  30           /etc/X11/cursors/oxy-steel.theme                          30        manual mode
  31           /etc/X11/cursors/oxy-terra.theme                          30        manual mode
  32           /etc/X11/cursors/oxy-terra_green.theme                    30        manual mode
  33           /etc/X11/cursors/oxy-violet.theme                         30        manual mode
  34           /etc/X11/cursors/oxy-viorange.theme                       30        manual mode
  35           /etc/X11/cursors/oxy-white.theme                          50        manual mode
  36           /etc/X11/cursors/oxy-whitewater.theme                     30        manual mode
  37           /etc/X11/cursors/oxy-wonton.theme                         30        manual mode
* 38           /etc/X11/cursors/oxy-yellow.theme                         40        manual mode
  39           /etc/X11/cursors/oxy-zion.theme                           40        manual mode
  40           /etc/X11/cursors/redglass.theme                           20        manual mode
  41           /etc/X11/cursors/whiteglass.theme                         20        manual mode
  42           /usr/share/icons/Adwaita/cursor.theme                     90        manual mode
  43           /usr/share/icons/ComixCursors-Opaque-Black/cursor.theme   40        manual mode
  44           /usr/share/icons/DMZ-Black/cursor.theme                   30        manual mode
  45           /usr/share/icons/DMZ-White/cursor.theme                   100       manual mode
  46           /usr/share/icons/mac-cursors/cursor.theme                 90        manual mode

Press enter to keep the current choice
[*], or type selection number: 
```

> **Dennis N said:**
> I don't know why you are doing this - the cursors belong in **/usr/share/icons**.

```
warning: forcing reinstallation of alternative /usr/share/icons/DMZ-White/cursor.theme because link group x-cursor-theme is broken
```

This looks ominous. Not sure what it implies. Is the cursor still working? Sorry, I don't understand the steps you took - they are not what I suggested (post #8).
You might try:
```
sudo update-alternatives --config x-cursor-theme
```
again, to see what the status is, but note there is no 's' on theme (post #15).

---

### Post by Vesnog on 2015-01-04
> **CantankRus said:**
> Sorry didn't realize it was a private thread.
I'll opt out then.

This is not a private thread you are always welcome and we would definitely like to hear your advice too. We did not mean anything like that.

---

### Post by Dennis N on 2015-01-04
> Apart from that my theme files are placed in /usr/share/icons but Tweak Tools are not able to distinguish between cursor-themes and icon-themes; how can I have them make that distinction?

Here is my Ubuntu Tweak window and my icons and cursor theme are separate. What tool are you using?

---

### Post by Vesnog on 2015-01-04
I am currently using Gnome Tweak Tool while also experimenting with Ubuntu Tweak Tool and Unity Tweak Tool. I noticed that some of the features of these tools are not working even when granted root privileges. My screen is similar to yours when I launch Ubuntu Tweak Tool but cursor themes get also listed under icon themes, that was my point in my earlier post; I apologize for the ambiguity.

---

### Post by Dennis N on 2015-01-08
There is also a GUI tool named "Alternatives Configurator" to do the work of update-alternatives in the terminal. The package name is **galternatives**. Unfortunately, it is broken in 14.04. It is working again in 14.10 releases.

---

### Post by Li_Wu on 2015-02-22
> **Vesnog said:**
> 
  39           /etc/X11/cursors/oxy-zion.theme                           40        manual mode


Though the GUI says the above theme cannot be deleted you just have to use     
find  /  -name \*zion\* 
   and delete it. Looks tidier that way. :KS

---

