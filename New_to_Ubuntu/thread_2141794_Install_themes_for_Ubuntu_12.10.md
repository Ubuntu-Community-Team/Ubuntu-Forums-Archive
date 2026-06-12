---
title: "Install themes for Ubuntu 12.10 ?"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by Niemil on 2013-05-03
Well, I have been googling for tutorials of how I can install themes on Ubuntu 12.10 but I cannot find anything working. Am I retard or what?

Like this one
[http://www.upubuntu.com/2012/11/install-15-best-ubuntu-1210-themes-for.html](http://www.upubuntu.com/2012/11/install-15-best-ubuntu-1210-themes-for.html)

At the stage when I am gonna download a theme, like "sudo apt-get install delorean-dark-theme"

Then I get this up:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package delorean-dark-theme

Anyway, the theme I do want is the MacOS one [http://gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548](http://gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548)
Is that possible with Ubuntu 12.10?

When I follow the steps, I don't get it working. I downloaded the tar.gz file, then made the command in terminal, but getting this error:


tar (child): 13548-Gnome_MacOS-X_Aqua_Theme_20040730.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


I have checked and the filename shall be correct.
How to install themes? why shall it be so hard?

---

### Post by Cheesemill on 2013-05-03
> **Niemil said:**
> At the stage when I am gonna download a theme, like "sudo apt-get install delorean-dark-theme"

Then I get this up:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package delorean-dark-theme
Did you run the commands at the top of that page to add the PPA and update first?
```
sudo add-apt-repository ppa:upubuntu-com/gtk3
sudo apt-get update
```

That theme definitely exists in the PPA, you can see it on the website.
[https://launchpad.net/~upubuntu-com/+archive/gtk3?field.series_filter=quantal](https://launchpad.net/~upubuntu-com/+archive/gtk3?field.series_filter=quantal)

> Anyway, the theme I do want is the MacOS one [http://gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548](http://gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548)
Is that possible with Ubuntu 12.10?

That theme wont work on 12.10, if you look at the date it's a 9 year old theme. A lot has changed since then.

If you want to browse for themes on [http://gnome-look.org](http://gnome-look.org) then look for GTK3 themes if you are using Unity, or for GTK3 and Gnome Shell themes if you are using GNome Shell.

---

### Post by Frogs Hair on 2013-05-03
Here is a newer take on the theme posted.  [http://gnome-look.org/content/show.php?content=147061](http://gnome-look.org/content/show.php?content=147061)

Manual Installation : [http://ubuntuforums.org/showthread.php?t=2134319&highlight=install+themes](http://ubuntuforums.org/showthread.php?t=2134319&highlight=install+themes)

---

### Post by Niemil on 2013-05-03
Thanks, though I don't get the last step
This is how it looks like atm [IMG]http://emilniemi.com/storage/ubuntu/Workspace%201_011.jpg[/IMG]
[I]also this editor on the forums is weird, thanks for editing away the fail in big text that I got by copying from other sites etc, that I could't somehow shut off.
[/I]
I cannot see where I am gonna put those files in. I don't find any folder that are named .themes or something in this theme folders I got. I did create the .themes folder after pressing CTRL+H in the home folder, and well it's impossible to understand what files gonna go in there.

---

### Post by Cheesemill on 2013-05-03
Just cut the Gnome-Cupertino folder from your desktop and paste it into your .themes folder

---

### Post by Niemil on 2013-05-04
Ah, thank you! I got it work quite well,
except that the menu is still the old one to the left.
This is how it looks:
[IMG]http://emilniemi.com/storage/ubuntu/Workspace%201_013.jpg[/IMG]


I wonder if it might be the shell option that will do my menu for me? However, I don't seem be able to even change that one.
Also been looking around on the other drop down menus to find the name of this theme, but can't find any more to change.

And the icons on the [COLOR=#000000][FONT=Verdana]**Gnome Cupertino **[/FONT][/COLOR]theme I don't understand how to even download. The link gets me to deviantart and from there I've clicked the other links in the description of the image, but cannot find any download link for it.

---

### Post by Cheesemill on 2013-05-04
Gnome Shell themes only work if you are actually running Gnome Shell, from your screenshot I can see that you are running Unity.

Gnome Shell and Unity are two different desktop environments that are both based on GTK3, so GTK3 themes will work on both of them to change the appearance of the windows and their contents. To change the appearance of the rest of your desktop (including the menu on the left) you have to use a gnome shell theme if you are running gnome shell or just stick with the default if you are running Unity (AFAIK Unity doesn't have any additional themes available).

If you want to try using Gnome Shell then you can install it by doing...
```
sudo apt-get install gnome-shell
```

Next time you log in you will have gnome shell available as an option on the login screen.

---

### Post by Niemil on 2013-05-04
Hm, it seems like it doesn't work for me with that command.

When I type it I get up this:


*Reading package lists... Done*
*Building dependency tree       *
*Reading state information... Done*
*gnome-shell is already the newest version.*
*The following packages were automatically installed and are no longer required:*
*  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic*
*Use 'apt-get autoremove' to remove them.*
*0 upgraded, 0 newly installed, 0 to remove and 5 not upg*


And when I then restarted the computer nothing came up than usually.

---

### Post by Cheesemill on 2013-05-04
You already have gnome-shell installed, to try it out just select GNOME from the session chooser on the login screen (click the Ubuntu icon next to your name).

---

### Post by Niemil on 2013-05-04
Thank you!
But, now it's not at all this MacOS theme, even though I got it selected in both Tweak Tool and Ubuntu Tweak:

[IMG]http://emilniemi.com/storage/ubuntu/Workspace%201_023.jpg[/IMG]

---

### Post by Niemil on 2013-05-04
I have been reading through on the readme file, but still I don't got it to work. Also I installed the Nautilus or whatever it is called.
And installed the user themes, but cannot find any shell for this theme.

---

### Post by Niemil on 2013-05-04
Well, I now started follow this tutorial:
[http://www.youtube.com/watch?v=MpENgOt0_JI](http://www.youtube.com/watch?v=MpENgOt0_JI)

Sure, I got that menu down now, but still I got the one at the side/top (it popups when I go with mouse to left top or clicking the "activities" button).
Didn't come further with the tutorial when he went to Advanced settings, I don't have advanced settings, I guess it's tweak tool for me, and still I don't got the options he got. 

Guess I have messed up all this theme

---

### Post by Frogs Hair on 2013-05-04
_Install the Tweak Tool from the software center if not already_. Open the terminal and copy and paste the following 




```
sudo add-apt-repository ppa:webupd8team/themes

```

```
sudo apt-get update

```

```
sudo apt-get install gnome-cupertino-gtk-theme
``` 


Open the Tweak Tool and look under themes for the new themes. 
More Themes: [http://www.webupd8.org/2013/02/mediterraneannight-gtk36-theme-pack.html](http://www.webupd8.org/2013/02/mediterraneannight-gtk36-theme-pack.html)

---

### Post by Niemil on 2013-05-05
> **Frogs Hair said:**
> _Install the Tweak Tool from the software center if not already_. Open the terminal and copy and paste the following 




```
sudo add-apt-repository ppa:webupd8team/themes

```

```
sudo apt-get update

```

```
sudo apt-get install gnome-cupertino-gtk-theme
``` 


Open the Tweak Tool and look under themes for the new themes. 
More Themes: [http://www.webupd8.org/2013/02/mediterraneannight-gtk36-theme-pack.html](http://www.webupd8.org/2013/02/mediterraneannight-gtk36-theme-pack.html)

Well, I already have the Tweak tool.
And now by doing all this, I just got duplications of what I had before, nothing new really.

And the MacOS dock on bottom doesn't open on startup. I've to search on Cairo and open it everytime I restart computer.
And there is still no shell for me to pick that's this Cupertino/MacOS. Instead I am using a shell from the theme Zukitwo, but I want the MacOS one.

Also there is no minimize button anymore on the MacOS theme. I can only close windows.

Else everything seems to work after the commands I did on the YouTube tutorial, because from there I got the icons, the mouse pointer and the dock.


But this is what I want to fix:
- Make the minimize and maximize button on windows to appear
- Get the MacOS/Cupertino shell (that top bar) to appear
- Get the left dock in Gnome that popups under "Activites" to be gone
- Get the MacOS dock to appear on startup

---

### Post by Frogs Hair on 2013-05-05
Select Gnome Classic during log-in and you will not have the dock on the left, but you will only have the top panel that comes with the theme and no option to apply a shell theme in Classic. Cairo/GLX dock has an auto start option in preferences and as I remember it can be found by right clicking the dock. The shell theme is applied in the Tweak Tool and  only in the Gnome session and not Classic or Unity. The window button options are changeable in the Tweak Tool as well, you can also right click the title bar for window actions until you change the setting.

---

### Post by Frogs Hair on 2013-05-05
Examples.

---

### Post by Niemil on 2013-05-09
Ah thank you!

Well, I found out some cairo-dock to choose on the login page. So I using that one and it's good.
Only problem now may be that I got no bar on the top at all. And the only thing I miss there is the clock. So I really got nowhere to see the clock on the computer right now other than going on google searching for a online clock which will take time. So that's the only now missing.

---

