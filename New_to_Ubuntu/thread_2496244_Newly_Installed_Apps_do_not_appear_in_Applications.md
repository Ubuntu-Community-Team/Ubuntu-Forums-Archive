---
title: "Newly Installed Apps do not appear in Applications Menu"
date: 2024-03-19
forum: New to Ubuntu
---

### Post by taneal1 on 2024-03-19
Newly Installed Apps do not appear in Applications Menu

I installed Blender. I can run it from the file Folder, but it does not appear in the desktop applications.

---

### Post by Holger_Gehrke on 2024-03-19
How did you install Blender ? If you installed it from the Software Center / Snap-store / Ubuntu Store (or whatever it's called now ...) it should have set up a menu item.

For a program to show in the menu there needs to be a desktop file for it in one of the places the system searches for them. Desktop files are simple text files with a [well documented structure]("https://specifications.freedesktop.org/desktop-entry-spec/latest/") and a name ending in '.desktop'. The system expects them to be in directories named applications/ in the directories listed in the environment variable XDG_DATA_DIRS or in $HOME/.local/share/applications.

Holger

---

### Post by taneal1 on 2024-03-19
[COLOR=#000000]How did you install Blender ? If you installed it from the Software Center / Snap-store / Ubuntu Store (or whatever it's called now ...) it should have set up a menu item.[/COLOR]

[COLOR=#000000]For a program to show in the menu there needs to be a desktop file for it in one of the places the system searches for them. Desktop files are simple text files with a [/COLOR][well documented structure]("https://specifications.freedesktop.org/desktop-entry-spec/latest/")[COLOR=#000000] and a name ending in '.desktop'. The system expects them to be in directories named applications/ in the directories listed in the environment variable XDG_DATA_DIRS or in $HOME/.local/share/applications.[/COLOR]

[COLOR=#000000]Holger


[/COLOR][COLOR=#000000]Ubuntu store. Yes, it should have set up a menu, but it didn't.[/COLOR][COLOR=#000000]
Thanks for the response, but as a brand new Ubuntu user I don't know enough about anything you mention to actually fix the issue without a lot more info.

 I thought I'd try Ubuntu because everyone says its easy, it's simple to use, and runs reliably, whereas Windows get worse with every iteration. My first impressions of Ubuntu are it's buggy, difficult to install, very limited on apps (which are difficult to install) and virtually impossible to get a clear answer to a simple question.

I'll start off looking for the [/COLOR][COLOR=#000000]$HOME/.local/share/applications...[/COLOR]

---

### Post by pantazi on 2024-03-19
Have you opened the applications menu and typed Blender in to the search bar?   If you installed it from the software centre it should then be shown and you can then add the icon to the dash.
As for Ubuntu being 'buggy, difficult to install and limited on apps' , this is simply not true as I, as a 76 year old has proved.  Admittedly there is a learning curve, but taking small steps (and not running before walking) pays dividends.

---

### Post by taneal1 on 2024-03-20
> **taneal1 said:**
> [COLOR=#000000]How did you install Blender ? If you installed it from the Software Center / Snap-store / Ubuntu Store (or whatever it's called now ...) it should have set up a menu item.[/COLOR]

[COLOR=#000000]For a program to show in the menu there needs to be a desktop file for it in one of the places the system searches for them. Desktop files are simple text files with a [/COLOR][well documented structure]("https://specifications.freedesktop.org/desktop-entry-spec/latest/")[COLOR=#000000] and a name ending in '.desktop'. The system expects them to be in directories named applications/ in the directories listed in the environment variable XDG_DATA_DIRS or in $HOME/.local/share/applications.[/COLOR]

[COLOR=#000000]Holger


[/COLOR][COLOR=#000000]Ubuntu store. Yes, it should have set up a menu, but it didn't.[/COLOR][COLOR=#000000]
Thanks for the response, but as a brand new Ubuntu user I don't know enough about anything you mention to actually fix the issue without a lot more info.

 I thought I'd try Ubuntu because everyone says its easy, it's simple to use, and runs reliably, whereas Windows get worse with every iteration. My first impressions of Ubuntu are it's buggy, difficult to install, very limited on apps (which are difficult to install) and virtually impossible to get a clear answer to a simple question.

I'll start off looking for the [/COLOR][COLOR=#000000]$HOME/.local/share/applications...[/COLOR]


[COLOR=#000000]There is a file named "blender.desktop" in the  Blender folder. Per the above instructions, I copied it into  HOME/local/share/applications. This folder was empty prior to my action.  Blender still does not appear in Show/Applications.[/COLOR]

---

### Post by taneal1 on 2024-03-20
[COLOR=#000000]There is a file named "blender.desktop" in the  Blender folder. Per the above instructions, I copied it into  HOME/local/share/applications. This folder was empty prior to my action.  Blender still does not appear in Show/Applications.[/COLOR]

---

### Post by Dennis N on 2024-03-20
> **taneal1 said:**
> [COLOR=#000000]There is a file named "blender.desktop" in the  Blender folder. Per the above instructions, I copied it into  HOME/local/share/applications. This folder was empty prior to my action.  Blender still does not appear in Show/Applications.[/COLOR]

The location you give here for the .desktop file is not correct. It should be **~/.local/share/applications**

---

### Post by taneal1 on 2024-03-20
[COLOR=#000000]*[QUOTE There is a file named "blender.desktop" in the Blender folder. Per the above instructions, I copied it into HOME/local/share/applications. This folder was empty prior to my action. Blender still does not appear in Show/Applications.*[/COLOR][/QUOTE]

> **Dennis N said:**
> The location you give here for the .desktop file is not correct. It should be **~/.local/share/applications**

Are you saying the file *was* in the wrong folder, or that I copied it into the wrong folder?

Is** ~/.local/share/applications **"not" the folder under HOME? If not, where is it located? If it's actually "/.local and not /local, Search is not finding it...

---

### Post by Dennis N on 2024-03-20
> ...Are you saying the file *was* in the wrong folder, or that I copied it into the wrong folder? 
Is** ~/.local/share/applications **"not" the folder under HOME? If not, where is it located? If it's actually "/.local and not /local, Search is not finding it...

You copied it to a wrong folder. There are two places where .desktop files are detected. 
One is ~/.local/share/applications and the other is /usr/share/applications.
Ubuntu Software would put .desktop files in this 2nd location, so look and see if one already exists there. 

Since you post in the "New" forum, here are a few more comments.

~/.local/share/applications and ~/local/share applications are both in your home folder, and they are not the same. ~/.local/share/applications is inside a **hidden folder** (namely, ~/.local). Hidden folder names start with a . (dot).  ~/local/share/applications is inside ~/local, which is not a hidden folder. 

Ctrl+H when using the file manager will toggle the display of hidden folders and their contents (and hidden files) that are within your working directory. **ls -a**  in your terminal will list all folders and files, including hidden ones.

Also,  /.local is not the same as ~/.local because 

~/ stands for your home folder and
/ by itself is the root folder of the file system.

Big difference, so you have to take care about naming folders in commands.

---

### Post by taneal1 on 2024-03-20
> **Dennis N said:**
> You copied it to a wrong folder. There are two places where .desktop files are detected. 
One is ~/.local/share/applications and the other is /usr/share/applications.
Ubuntu Software would put .desktop files in this 2nd location, so look and see if one already exists there.

Thanks, Dennis.

When I attempt to move or copy the blender.desktop into the **/usr/share/applications** folder produces a 'You don't have permission to copy here...' Shades of the dreaded Windows OS.

EDIT: After 30+ minutes or so of screwing around with the "sudo cp" command and getting "no such directory" I tried going to the individual folders 'open in terminal' and using those paths - still didn't work... I finally got it to work. Now I have the blender.desktop file in the /usr/showapplications with all the other apps. It still does not show in "show applications." As an homage to windows and its never-ending reboot requirements, I rebooted. Still no Blender in show applications...

When I have gathered my strength for another fight to the death I'll attempt to copy the blender file to the other folder...

EDIT 2: Both files given above now contain the Blender.desktop file. Blender is *still* not available from show applications...

---

### Post by ajgreeny on 2024-03-21
There is no folder named /usr/showapplications/ unless you created it yourself and you would need sudo command to do that. However it wouldn't work even if you'd done it as that's the wrong destination folder.

You should have used command ```
sudo cp blender.desktop /usr/share/applications
``` using the pathway to the .desktop file in your home. This will give you temporary root permissions and allows you to move or copy files into the root filesystem.

If that desktop file was in a blender folder in your home it sounds as you have a version of blender that was downloaded as a compressed archive, not a normal installed package. Give us all the details of how you installed blender as I'm still confused. 

It also seems that you need a better understanding of Linux permissions so find one of the many sites that are around that will explain that more fully than we can in this forum. It will serve you very well throughout your Linux life.

---

### Post by Dennis N on 2024-03-21
**@taneal1**
You wrote in post #3:
> Ubuntu store. Yes, it should have set up a menu, but it didn't.


O.K. 
First question: let's see which "Ubuntu Store" you actually used to install it. Use your terminal, run the command shown below, then copy and paste the entire line of output in a reply. Please use code tags around your output by selecting it after pasting and then pressing the # from the tool bar.
```
snap list | grep snap-store
```

Second question: What version of Ubuntu are you running, 22.04, 23,10 or ?

---

### Post by Dennis N on 2024-03-21
> There is a file named "blender.desktop" in the Blender folder. 

As ajgreeny observes in post #11, it does sound like you must have downloaded some files. If you had used the Ubuntu Software application to install, there would be nothing placed in your home folder by the installer.  

Did you download files from the Blender website?  I checked there and see there is a download option there for a file **blender-4.0.2-linux-x64.tar.xz**
This contains a version intended for any Linux, but I would suggest using Ubuntu's software store to install it - you would get you a package designed for your Ubuntu system and integrated with Ubuntu's package management. Just click on the "Install" button on Blender's page and everything is put in the right place automatically without any user intervention.   

The software store installed on you system is either named "Ubuntu Software" or "App Center", depending on your Ubuntu version.

Screenshot attached: Blender's page in App Center (from Ubuntu 23.10)

---

### Post by taneal1 on 2024-03-21
> **Dennis N said:**
> **@taneal1**
You wrote in post #3:


O.K. 
First question: let's see which "Ubuntu Store" you actually used to install it. Use your terminal, run the command shown below, then copy and paste the entire line of output in a reply. Please use code tags around your output by selecting it after pasting and then pressing the # from the tool bar.
```
snap list | grep snap-store
```

Second question: What version of Ubuntu are you running, 22.04, 23,10 or ?


```
$ snap list | grep snap-store
snap-store                 41.3-71-g709398e  959    latest/stable/…  canonical**
```

22.04 LTS

---

### Post by Dennis N on 2024-03-22
> **taneal1 said:**
> ```
$ snap list | grep snap-store
snap-store                 41.3-71-g709398e  959    latest/stable/…  canonical**
```

22.04 LTS

The versions of snap-store beginning with 41 are named "Ubuntu Software". Find it in your applications. So that's you source for finding new applications to install in Ubuntu 22.04.

You can install Blender with "Ubuntu Software". Use the search button in the initial screen to search for it. There will be two results. One is a .deb package, the other is a snap package. Click the first one - it should lead to the .deb package. See screenshot.

Ubuntu promotes "Ubuntu Software". It additionally gives you the choice of snap packages, and you can browsing about various categories, but another way to install things is from the terminal if you know beforehand what you want to get.
```
sudo apt install blender
```
That all.

---

### Post by taneal1 on 2024-03-22
> **Dennis N said:**
> The versions of snap-store beginning with 41 are named "Ubuntu Software". Find it in your applications. So that's you source for finding new applications to install in Ubuntu 22.04.

You can install Blender with "Ubuntu Software". Use the search button in the initial screen to search for it. There will be two results. One is a .deb package, the other is a snap package. Click the first one - it should lead to the .deb package. See screenshot.

Ubuntu promotes "Ubuntu Software". It additionally gives you the choice of snap packages, and you can browsing about various categories, but another way to install things is from the terminal if you know beforehand what you want to get.
```
sudo apt install blender
```
That all.

Thanks for the info, but remember, I am brand new to Linux, Ubunto...

Paragraph 2 is telling me to install Blender via a .deb package, rather than the snap package that I have currently installed. Presumably, that will solve my current issue, but I still don't know why the snap install didn't work - and should I never use snap install?

Via Ubuntu software I am getting about a dozen snap options for installing Blender, but *no* ".deb packages..."

---

### Post by Dennis N on 2024-03-22
> **taneal1 said:**
> Thanks for the info, but remember, I am brand new to Linux, Ubunto...

Paragraph 2 is telling me to install Blender via a .deb package, rather than the snap package that I have currently installed. Presumably, that will solve my current issue, but I still don't know why the snap install didn't work - and should I never use snap install?

Up to your most recent post, I didn't see any mention that your package is a snap package. Let's find out: Run run command below in the terminal and post the output inside code tags like you did before. If the snap package was installed, it will show up in the output. That should settle that question.

```
snap list
```

Ubuntu Software could install either a snap package or a .deb package depending the source. Note the "source" box at the top (see post #15). When it says "ubuntu-mantic-..." this is a standard ubuntu repository with only .deb files. ("universe" is a section for packages that are not expected to be updated or supported by ubuntu after install.) You can switch sources (to install a snap package) by clicking on the drop-down arrow beside the box.


The "snap-store" that people talk about here is the file name of "Ubuntu Software". Ubuntu Software is itself a snap package, but it can install both .deb and snap packages. So it is not solely a "store" for snap packages.

Ubuntu invented snap packages a few years ago ostensibly to provide more secure packages that will work on any Linux distro. Prior to that invention, only .deb packages were offered by previous software stores. You can learn all about snap packages by doing a Google search.

If you gain experience and know what you want, you tend to use the terminal more often. The command I gave at the end of post #15 would install the .deb package of Blender. "apt" is the name of the underlying package manager which "Ubuntu Software" also uses behind the curtain to install your .deb software. So the "apt" command effectively bypasses "Ubuntu Software".  Note that apt cannot install snap packages.

---

### Post by ajgreeny on 2024-03-23
However be warned, using **apt install package name** commands will occasionally install a transitional package which itself then installs the snap version of that package, eg firefox, chromium, and in the dev version 24.04, also thunderbird.
There is very little warning that this will happen unless you follow closely what is happening in terminal or synaptic when installing packages.
I can't tell you how much information the other software managers give you as I've never used anything other than terminal or occasionally  synaptic.t

---

### Post by monkeybrain20122 on 2024-03-23
But then for blender you don't need either the deb (which is outdated) or the snap (which is probably buggy has too much unnecessary overhead). [Blender]("https://www.blender.org/download/") provides a binary for Linux. Just download it, extract, get into the folder and click the file called blender  (which is the executable) to launch. that's it. 

There is a blender.desktop file in the folder. If you want a launcher, edit it (right click and choose open with gedit) and change the Exec= blender line to Exec =/path/to/blender_folder/blender (for example, if the blender folder is in your $HOME, then Exec=/home/your_user_name/blender-4.0.2/blender) I would change the folder name to 'blender' instead of 'blender-version-no' because then you won't have to edit your .desktop file if you upgrade. Now copy this .desktop file to ~/.local/share/applications (don't use sudo!!), then right click it, in permission, choose allow to execute as a program. If needed, log out and log in and you should find the launcher in your dash.

---

### Post by taneal1 on 2024-03-23
> **Dennis N said:**
> Up to your most recent post, I didn't see any mention that your package is a snap package. Let's find out: Run run command below in the terminal and post the output inside code tags like you did before. If the snap package was installed, it will show up in the output. That should settle that question.

```
snap list
```

```
taneal1@Tom-Precision-3541:~$ snap list
Name                       Version           Rev    Tracking         Publisher      Notes
bare                       1.0               5      latest/stable    canonical&#10003;     base
core18                     20231027          2812   latest/stable    canonical&#10003;     base
core20                     20240111          2182   latest/stable    canonical&#10003;     base
core22                     20240111          1122   latest/stable    canonical&#10003;     base
ddgr                       2.2               846    latest/stable    snapcrafters&#10026;  -
firefox                    116.0.2-1         2987   latest/stable/&#8230;  mozilla&#10003;       -
gnome-3-38-2004            0+git.efb213a     143    latest/stable/&#8230;  canonical&#10003;     -
gnome-42-2204              0+git.ff35a85     141    latest/stable/&#8230;  canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/&#8230;  canonical&#10003;     -
snap-store                 41.3-71-g709398e  959    latest/stable/&#8230;  canonical&#10003;     -
snapd                      2.61.2            21184  latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.9               83     latest/stable/&#8230;  canonical&#10003;     -
vlc                        3.0.19            3721   latest/stable    videolan&#10003; 
```

I tried several different install methods with Blender, and I don't recall which one actually "worked." I don't see Blender listed here, so I must have used something else. I do see VLC and Duck Duck that I installed. They also do not appear in Show Applications...

---

### Post by Dennis N on 2024-03-23
> I tried several different install methods with Blender, and I don't recall which one actually "worked." I don't see Blender listed here, so I must have used something else. I do see VLC and Duck Duck that I installed. They also do not appear in Show Applications... 

So snap is eliminated as a possibility.
Let's check if you have the .deb version. Run the command below in the terminal, and paste the entire output in code tags. This will tell us if it is installed or not.
```
apt-cache policy blender
```

If not, you probably went to the Blender website and downloaded the file mentioned in post #13, and referred to by user monkeybrain20122 in post #19. He also gives you instructions on how to get it recognized by the system to appear in your menu or searches.

As to your installed snaps ddgr and vlc, I don't know for sure if all snap applications you install must provide .desktop files. Any .desktop files that exist are not in the places we have mentioned. Perhaps look here: /var/lib/snapd/desktop/applications

---

### Post by Dennis N on 2024-03-23
Also, in your list of snaps, the core snaps like core18, core20, core22 remain installed even if no longer used. On my system, I remove the older ones when possible. If something needs it, it will tell you it can't be removed and why. 

for example try:
```
sudo snap remove core18
```

---

### Post by taneal1 on 2024-03-25
> **Dennis N said:**
> Also, in your list of snaps, the core snaps like core18, core20, core22 remain installed even if no longer used. On my system, I remove the older ones when possible. If something needs it, it will tell you it can't be removed and why. 

for example try:
```
sudo snap remove core18
```

```
taneal1@Tom-Precision-3541:~$ sudo snap remove core18
[sudo] password for taneal1: 
error: cannot remove "core18": snap "core18" is not removable: snap is being
       used by snap vlc.
taneal1@Tom-Precision-3541:~$ sudo snap remove core20
error: cannot remove "core20": snap "core20" is not removable: snap is being
       used by snaps firefox and gnome-3-38-2004.
taneal1@Tom-Precision-3541:~$ sudo snap remove core22
error: cannot remove "core22": snap "core22" is not removable: snap is being
       used by snaps ddgr, gnome-42-2204, snap-store and
       snapd-desktop-integration.
taneal1@Tom-Precision-3541:~$ 
```

---

### Post by Dennis N on 2024-03-26
In your system, you still need them all. We see only **vlc** uses core18. If you notice vlc updating, the newer version may also switch to a newer core.  Then you can remove the unused core18. You can recover some disk space by doing that. Its optional, of course but why not?

---

