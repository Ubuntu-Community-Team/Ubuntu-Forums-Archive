---
title: "General questions - how to easily modify something in the /opt folder?"
date: 2016-08-25
forum: New to Ubuntu
---

### Post by one+one+one on 2016-08-25
I'm new to Linux, although I extensively used those NeXT computers from the 1990s including some use of the Unix-like command prompt, but that was 20 years ago.  I'm switching back to Linux now because I don't like any recent Windows operating system.  Right now I'm trying to do something specific, but maybe not advisable.

I've installed a program called Eagle, an electronic circuit design automation tool, and by default it wanted to install itself in the /opt folder, so I went ahead and let it install there even though I had no idea what that folder was for.  I have read a bit about it in the past few days, and it is my understanding that the /opt folder is for shared programs so that they can be used by any user logged in to the computer.  It's probably not necessary to do it that way, since anybody using this computer generally uses it under the same single username, "amie."  In addition there is a root user with a password, and a few other users for special purpose software.

Since I installed Eagle I upgraded from Ubuntu 14.04.1 to 16.04.1.

My problem is that Eagle comes with parts libraries, in /opt/eagle-7.6.0/lbr, and I want to easily be able to edit those libraries.  I already figured out that Eagle is easily configurable for which libraries to use or not use, so it is mostly unnecessary to delete libraries since you can effectively turn them off from the Eagle control panel.  It is also easy to specify another location for user libraries, so that if I spend a lot of time creating symbols and footprints for new parts, I can save them in my own user folder and still easily access them from within the software.  And, I suspect that any changes made in the /opt/eagle-7.6.0/lbr directory might be overwritten when Eagle is updated.  For all these reasons, it may be foolish to want to edit the libraries in that folder, but I still would like to do it, let's say just for experimentation purposes.

So, first specific question: how do I unzip compressed files into a folder that requires root access?  There is one group of libraries in there in a folder called "seeed," and recently I was on seeed's web site, and I noticed that they have a newer version of their open parts library than the one I had in my libraries, so I thought I would go ahead and update it.  I downloaded a .zip file.  I right-clicked on it in my Downloads folder, and opened with Archive manager.  I tried to extract all the new library files to /opt/eagle-7.6.0/lbr/seeed, but permission was denied.  I got on this web site and found [this thread]("https://ubuntuforums.org/showthread.php?t=1560543") from 2010, where someone was able to do it by typing [COLOR=#008000][FONT=fixedsys]sudo file-roller[/FONT][/COLOR] in the terminal window.  So, I did the same thing, and typed in my root password, and the Archive Manager GUI came up, but there were no menus.  On all my applications, the menus show up when I hover over the title bar, so they also do it on Archive Manager, but not when I run it as root using sudo.  The extract button is grayed out, everything is either grayed-out or not even there, Archive Manager becomes a useless box on the screen that does nothing.  So, did something change in the past six years so that it worked in 2010, but no longer works?  Is there a way to get it to work?

I worked around the lack of ability to extract files to that folder by extracting them where they were, then using sudo mv to move them into the folder where I wanted them.  Then I wanted to delete some of the old files that looked like duplicates, and rename some that looked like they weren't duplicates, but again it looks like I'll have to use sudo for each operation, and it would be a lot easier if I could just use the GUI to delete and rename things.  When I list the files, I see the ones I added are owned by amie (again that is my username on this computer) and have permissions [FONT=courier new]-rw-rw-r--[/FONT], whereas the original ones are owned by root and have permissions [FONT=courier new]-rwxrwxr-x[/FONT].  What do I need to do so that I can work with all the files, and Eagle can still work with them too?  It's been about 20 years since I used chmod and I don't remember what all that stuff stands for.

---

### Post by CantankRus on 2016-08-25
Install nautilus-admin and gksu.
nautilus-admin will give you right click menus in nautilus to open directories and certain files with admin privileges.
gksu allows you to open graphical applications in terminal as root.
```
sudo apt install nautilus-admin gksu
```

Just open a root window of nautilus....
[ATTACH=CONFIG]270865[/ATTACH]

or

I'm not competent with permissions via terminal but
using... 
```
gksudo nautilus /opt
```
You could then use the right click **menu > properties > permissions** to give yourself read and write privileges for your eagle folder.
[ATTACH=CONFIG]270866[/ATTACH]
*****Press the button to "Apply permissions for enclosed files"**

---

### Post by grahammechanical on 2016-08-25
> So, did something change in the past six years so that it worked in 2010, but no longer works?

6 years ago. Why, that is like going back to the times of myths & legends. Since then, Gnome.org dropped Gnome 2 DE and Gnome 2 panel and switched to Gnome 3 DE and Gnome 3 shell. Ubuntu accepted Gnome 3 DE but rejected Gnome 3 shell in favour of Unity shell. You missed all the fun.

Ever since then Gnome developers have been making improvements to all their utilities. Not everyone agrees with the Gnome developers that they are improvements. But there you go.

I think that it is intentional that File Roller does not work with root privileges. Otherwise, all files extracted would be owned by root. Even those put into a user's home folder. As you have found out by using "sudo mv."

Extract the files into a folder in your home directory and move them using Nautilus loaded with gksu or sudo -H but not simply "sudo." It is much too dangerous. So, children, do not do this at home. :) Well, this is the New to Ubuntu section and I do not think that this is a subject for new to Ubuntu users.

Regards

---

### Post by HermanAB on 2016-08-26
$ sudo vi /opt/filename

---

### Post by mc4man on 2016-08-26
You could have (and still can) installed to your $HOME dir. - screen. Then no permission issues.

---

