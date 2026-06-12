---
title: "Howto: Install Wine applications for Multiple Users"
date: 2008-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by rsay on 2008-09-11
**Background:**
Some proprietary windows programs only allow a limited number of installations, making it desirable to install to a common location in the &#8220;windows style&#8221;, instead of  installing separately for each user in the &#8220;wine style&#8221;. In addition, it may be more efficient for an administrator to install a program once, even if the license allows for unlimited installations. Codeweavers refers to this type of multi-user installation as Shared Global Mode.

**Outline of method:**
We are going to create a new user, &#8220;windows&#8221;, that will host the system-wide wine installation. We will then give some of our users permission to run windows programs as the user windows, with wine, on their own desktop, without having to switch accounts or enter passwords.

**Estimated time**
15-20 minutes

**Preparation:**
Install wine if you haven't already done so.
```
sudo apt-get install wine
```
Run winecfg to test your installation
```
winecfg
```
You should see a window pop up with multiple tabs. Applications, Drives, Graphics, Audio, etc. 
Close the window

**STEP 1. Add a new user without a password.**
Pick a user name that doesn't exist on *your* system
```
sudo adduser --disabled-password windows
```
Just hit enter to accept defaults for name, office, phone etc., then answer Y.

**STEP 2. Backup /etc/sudoers and use visudo to edit /etc/sudoers**

2.1 Backup /etc/sudoers in case something bad happens.
```
sudo cp /etc/sudoers /etc/sudoers.bak
```

2.2 Edit /etc/sudoers, but only with visudo.
```
sudo visudo
```
Pay careful attention to syntax here. This file isn't very forgiving to editing mistakes.
I used [_this_]("http://www.cs.colostate.edu/helpdocs/vi.html") page to figure out how to edit with vi. I got a log of mileage out of i, o, x, dd and :wq.

If you're a nano user, you can do this:
```
sudo EDITOR=nano visudo
```

If you want something more graphical, you can use xedit:
```
sudo EDITOR=xedit visudo
```

2.3 In the User alias section, define which users will administrate the computer. (Have root privileges)
This will probably be all the people currently in your admin group
```
User_Alias ADMIN = ron
```

2.4  In the User alias section, define which users can run the wine/windows programs.

```
User_Alias WINDOWS_USERS = kim,ian,mason,collin,ron
```
* no spaces between the names

2.5 In the command alias section, define which programs the windows user can run
```
Cmnd_Alias WINDOWS = /usr/bin/wine,/usr/bin/winecfg
```

2.6 In the defaults section, add the following commands so that we will be able to use our current X windows display
```
Defaults:WINDOWS_USERS env_reset
Defaults:WINDOWS_USERS env_keep += DISPLAY
Defaults:WINDOWS_USERS env_keep += XAUTHORITY
```

2.7 Change the line that defines who gets admin privileges
Delete this:
```
%admin ALL=(ALL) ALL
```
This gave admin privileges to anybody in the admin group defined in /etc/group

Replace it with this:
```
ADMIN ALL=(ALL) ALL
```
This gives admin privileges to anybody listed in the ADMIN alias defined in step 2.3. The difference is subtle but important. Without this change the people in the admin group will *always* have to supply their password before they can run windows programs.

2.8 Add a line at the bottom that gives WINDOWS_USERS permission to run WINDOWS programs, without a password, as user windows
```
WINDOWS_USERS ALL = (windows) NOPASSWD: WINDOWS
```

Here is what my /etc/sudoers file looks like after making these changes:
```
# User alias specification

# define which users can run the wine/windows programs
User_Alias WINDOWS_USERS = kim,ian,mason,collin,ron

# define which users can administrate (become root)
User_Alias ADMIN = ron

# Cmnd alias specification

# define which commands the WINDOWS_USERS may run
Cmnd_Alias WINDOWS = /usr/bin/wine,/usr/bin/winecfg

# Defaults
Defaults:WINDOWS_USERS env_reset
Defaults:WINDOWS_USERS env_keep += DISPLAY
Defaults:WINDOWS_USERS env_keep += XAUTHORITY
Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin user_alias, defined above, may gain root privileges
ADMIN ALL=(ALL) ALL

# The WINDOWS_USERS may run WINDOWS programs as user windows without a password
WINDOWS_USERS ALL = (windows) NOPASSWD: WINDOWS
```
There's really not much too it without the comments

**STEP 3: Move your .wine directory over to the windows user's .wine directory** 
```
sudo mv ~ron/.wine ~windows/.wine -iv
sudo chown windows:users ~windows/.wine/ -Rfv
```

**STEP 4: Let the windows user have access to your display**
This command has to be issued from the user shell (not root)
```
xhost +local:windows
```
Issuing this command will only work until you log out. To make things permanent, add the command to System>Preferences>Sessions>Startup Programs in the desktop of each of the Windows_Users

**STEP 5: Run your windows programs with sudo, no password required.**
```
sudo -u windows -H wine notepad
``` 
You can use variations of this command in your graphical menus for any wine program that you want to run from the system wine. You *will* have to edit the menus of each indivial windows_user for any system wine programs that you want them to be able to run. 
If you want to run or install programs for yourself (not for all the windows_users) just use wine without sudo like this:
```
wine notepad
``` 

**What should I do if things go horribly wrong?**
```
sudo mv ~windows/.wine ~ron/.wine -iv
sudo chown ron:ron ~ron/.wine/ -Rfv
sudo deluser --remove-home --backup windows
sudo cp /etc/sudoers.bak /etc/sudoers
```
Remove the xhost +local:windows from your startup programs if you put it there.
Remove the sudo -u windows -H from any menu items that you edited

This moves your wine directory back, puts the file ownership back in your name, completely removes the new user and replaces your sudoers file. Remember that you can even replace the sudoers file from a live disk if things go horribly wrong and you can't log in or get root privileges.

**Broader applications**
After looking at the above information, it should be a simple exercise to modify my steps to run any program, including a browser like firefox, as a different user on your desktop.

**Closing Thoughts**
a. Remember to add the windows user to the appropriate groups so that wine can access the necessary system resources: cdroms, sound, floppies etc.
b. Remember that if you want to add a new system administrator that you not only have to add them to the admin group, you will have to edit /etc/sudoers to add them to the ADMIN user alias.

**Test Systems**
Ubuntu Hardy 8.04 on Dell Inspiron 5100
Ubuntu64 Hardy 8.04 on a homebuilt quadcore
Ubuntu Intrepid 8.10 circa 9/11/08 on a homebuilt quadcore (I got nano as the editor for visudo instead of vi)
Ubuntu Jaunty 9.04

**Credits**:)
Link:[_Running Firefox as another user, using sudo_]("http://calum.org/posts/running-firefox-as-another-user-using-sudo")
Link:[_Running firefox as a different user_]("http://ubuntuforums.org/showthread.php?t=690102") Thanks Gaten for post #5
Link:[_suauth and pam.d_]("http://ubuntuforums.org/showthread.php?t=913755")   Thanks HalPomeranz for post #16

**Disclaimer**
As always, this worked for me, but YMMV. Read, think and remember that I am "just some guy on the internet" before you apply changes to an important system.

---

### Post by wdypdx1 on 2008-09-29
Excellent! Even though I haven't tried it yet.

Today I posted this,
[http://ubuntuforums.org/showthread.php?p=5878033#post5878033](http://ubuntuforums.org/showthread.php?p=5878033#post5878033)

over in the wine forum.

For some reason my forum search didn't get me to your thread. I found it over on the WineHQ forums searching for an answer to the multi-user question.

I'll be trying your method later this evening.

wdy

---

### Post by binbash on 2008-09-29
Awesome howto, i will give a try

---

### Post by wdypdx1 on 2008-09-30
Question on this Howto...

I already have wine installed and just a couple of apps so far, and no worries about any data, etc. So, do I need to uninstall/re-install wine, etc, so that I have a fresh start for this Howto? 

Also, I'm assuming that I do this through my primary admin user account.

- wdy

---

### Post by rsay on 2008-09-30
You can go through the howto in any account that has sudo access. This means anybody in your "admin" group. This will certainly include your primary user but could include others that you have added to the admin group. 

As far as your current wine installation you just have to decide what you want to have where. 

If you want your current wine installation to become available to all users and to start a new "personal" wine installation then move the .wine from your home directory into the /home/windows directory. (This is the way I did step 3, by moving my personal wine into the system wide wine.)

If I wanted to start a clean shared wine installation, I could simply copy the .wine folder of any user that had not installed anything in their personal wine yet when I got to step 3. On my system Mason doesn't have any programs installed on wine. In fact he's never even run winecfg so he doesn't have a .wine folder. I would switch to his account, run winecfg, come back to my account with sudo access and then copy his .wine directory over to the shared wine install. 
**Alternate Step 3**
```
 
su - mason 
winecfg
exit
sudo mv ~mason/.wine ~windows/.wine -iv
sudo chown windows:users ~windows/.wine/ -Rfv
```

If I didn't have any user without wine programs installed I would skip step 3 altogether and do the following in step 5.

**Alternate Step 5.**
```
sudo -u windows -H winecfg
sudo chown windows:users ~windows/.wine/ -Rfv
sudo -u windows -H wine notepad
```

---

### Post by snkiz on 2008-10-16
> **rsay said:**
> **Background:**
2.2 Edit /etc/sudoers, but only with visudo.


why this program is the most god awful thing I've seen in linux to date can't you just use nano or gedit?

---

### Post by rsay on 2008-10-17
The reason to use visudo is so it can do syntax checking. As I mentioned, the sudoers file is important to the functioning of your system and not forgiving when it comes to errors. Fortunately, the syntax checking isn't tied to a specific editor.

If you're a dyed-in-the-wool nano user, you can do this:
```
sudo EDITOR=nano visudo
```

Xedit is probably the closest command line editor to gedit.
```
sudo EDITOR=xedit visudo
```

I'll update the guide with those options. Thanks.

---

### Post by snkiz on 2008-10-17
hey thanks digging deeper for me. Google only works if you know what to look for, some posters forget that sometimes. lol I was mad when I wrote that, I did manage to find a reference to using other editors in the man pages but couldn't figure out how. I did finaly figure out vi, after throwing my mouse once or twice. I'd like to suggest you add in that the order of the text is important. And the default is wrong if you try to add the new lines under the headers as they are. Once I figured that out it was a matter of deleting everything under the ##info, paste in yours and edit the users. Hope you don't mind. But hey it was an achivement to do all that with vi. Just a thought, sorry if its been said before. But it would be nice if wine could be made to place launchers in usr/share/local/applications so they show up for everyone. I'll see if I can find out how after the hockey game. Cheers!

---

### Post by rsay on 2008-10-20
Let me know if you find out how to get wine to place the menu items. That would be a great addition for the howto.

---

### Post by snkiz on 2008-11-18
> **rsay said:**
> Let me know if you find out how to get wine to place the menu items. That would be a great addition for the howto.
Sorry for the wait life gets busy some times. My firstlook has reveled that wine places .desktop files here ~/.local/share/applications/wine/Programs and desktop directories here ~/.local/share/desktop-directories and icons here ~/.local/share/icons so could we  simply just simply symlink into /usr/share/applications/wine/Programs, /usr/share/desktop-directories, and /usr/share/icons? any thoughts?

---

### Post by crazier22 on 2008-12-12
First of all, congrats for the good job!  I've found another solution where you should symlink everything but the .reg files, but it was difficult to implement and dangerous to the data.  Yours is a more elegant solution by far.

I'm using this solution to install msoffice on my eeepc (my spouse hates openoffice :().  Once it has just 4GB, any disk space saving is welcome!

I want to help you improving it, so let me tell you what is happening here...

In order to open any .xls with Excel and using your solution, for example, I use "open with" pointing to a little shell script file.
```
#!/bin/bash
sudo -u windows -H wine "C:\Program Files\Microsoft Office\OFFICE11\EXCEL.EXE" "`winepath -w "$@"`"
```
You can adapt it to your own windows' programs.

Following snkiz's directions, I found the gnome menu information under ~windows/.local/share but wasn't able to make it appears on another user's menu yet, but found some some useful information here (I'll spend some time on it later): [http://automatthias.wordpress.com/2005/11/22/create-a-custom-gnome-menu/](http://automatthias.wordpress.com/2005/11/22/create-a-custom-gnome-menu/)

Regards

---

### Post by snkiz on 2008-12-12
I read the link seems the poster never found the /etc/xdg directory in ubuntu but I believe that is only used for new user setups. I tried to put a script there to run nvidia settings on startup but it did not transfer into existing user directories. Ubuntu puts all the .desktop files in /usr/share/applications or /usr/share/apps (kde) You can use /usr/local/share  to add extra .desktop files, they will be added to the menu according to how the file is written. I don't yet know where ubuntu keeps the menu configs of if they can be  mirrored in /usr/local/ On an eailer note everything I found about getting wine to do this for us is either wayy over my head. or not possible by design. (The whole multi access to files go boom thing)

---

### Post by crazier22 on 2008-12-12
I suppose the menu configs are under ~windows/.config/menus/applications-merged/ .  Is that what you were looking for?

Sorry if I can't help much, but I'm still learning about the gnome menu system.  It's not totally clear for me.

Till I can see, we need to symlink something like:
~windows/.config/menus/applications-merged <- ~/.config/menus/applications-merged
~windows/.local/share/[applications,desktop-directories,icons] <- ~/.local/share/[applications,desktop-directories,icons]
; and edit .desktop files changing the "env wineprefix=.../" to "sudo -u windows -H" (I'm sure about this part, at least :))

What do you think?

---

### Post by snkiz on 2008-12-13
that would get sticky because if you symlink into the user config folders in the home directory you will get permissions conflicts. The wine menu configs need to placed in a folder where they will be the system can use them

---

### Post by rsay on 2008-12-13
I have made progress on the menu problem.

Based on your suggestions, I created a link from the the wine menu folder of the windows user to a shared system folder that I named Wine_global. I chose this folder to try and make this work for gnome and kde.

```
sudo ln -s /home/windows/.local/share/applications/wine/ /etc/X11/applnk/Wine_global

```

Now, when wine installs programs to the menu, they propagate to all users.

I installed PokerStars.exe as an example, since it was a platinum app on Wine HQ. 

Of course, the default wine menu install doesn't account for running the program as the windows user so I have to edit the PokerStars.desktop file in the /etc/X11/applnk/Wine_global/Programs/PokerStars directory as follows.

Original:
```
[Desktop Entry]
Name=PokerStars
Exec=env WINEPREFIX="/home/windows/.wine" wine "C:\\Program Files\\PokerStars\\PokerStarsUpdate.exe" 
Type=Application
StartupWMClass=Wine
Path=/home/windows/.wine/dosdevices/c:/Program Files/PokerStars
Icon=/home/windows/.local/share/icons/6604_pokerstarsupdate.0.xpm

```

Fixed:
```
[Desktop Entry]
Name=PokerStars
Exec=env WINEPREFIX="/home/windows/.wine" **sudo -u windows -H** wine "C:\\Program Files\\PokerStars\\PokerStarsUpdate.exe" 
Type=Application
StartupWMClass=Wine
Path=/home/windows/.wine/dosdevices/c:/Program Files/PokerStars
Icon=/home/windows/.local/share/icons/6604_pokerstarsupdate.0.xpm

```

Basically just adding "sudo -u windows -H" in front of "wine" in the Exec line. 

Now, all the users have a Wine_global menu (or whatever you called it), that can run the programs as the windows user. This keeps the shared wine menu distinct from the users local wine if they have it installed.

I would like to have a gui like alacarte to edit the menu, but even when I tried sudo -u windows -H alacarte, the changes didn't propagate back to the /etc/X11/applnk.

---

### Post by crazier22 on 2008-12-15
If I'm not wrong, if you set wineprefix, it's going to use and modify the registry of the user you set.

Looking at your orginal .desktop file I noted that your test was done with wineprefix = ~/windows/.wine and it should work once the registry is the same (sudo -u windows points you to the user windows itself).

I'm going to travel in 2 days and can't have my computer in trouble, so I can't test it right now.  For now it's working.  If someoneelse could test it with another user it would be great!

Regards

---

### Post by rsay on 2008-12-16
crazier22, remember that in this scheme, we aren't running another users wine, we are running wine AS the other user. The wineprefix wasn't something I put in btw, it was generated by wine when the example program (PokerStars) installed. My goal here was to alter things as little as possible because I don't want to learn the intricacies of wine.

---

### Post by Craig73 on 2009-01-13
Could you expand your HowTo to clarify the implications of such a configuration so users understand what they are choosing.  It might be appropriate to refer to other possible configurations.

This is a setup where users are all using a common Windows folder.  Without digging into it, my initial gut reaction is that the following are potential exposures:

User Experience:
1) Since all users are running Windows programs at the same user, they may not be able to personalize their Windows applications (depending if the data is stored in the registry or in a relocatable file)

Stability:
1) Users are not restricted from updating or installing new windows updates.  They could mess up the configuration and or change applications that others depend on.

2) If a user switches users while running a Windows app and tries to run a Windows app under the other user, are key files locked? or is there a risk of data corruption?

Security Risks:
1) I expect it could allow a non-privileged user to trick a privileged user into executing malicious code. (Say by replacing a windows exe that an admin would run with a malicious one, or by inadvertently installing malware into the common Windows folder)

2) Since the windows folder is shared, nothing there is confidential.  Even if users store their data in their own folder, backup data, temp files, registry data, user preferences all could contain confidential information.

-------------------------

It's amusing that someone stated that this solution is more elegant.  But they perhaps didn't realize what the drawbacks might be.  It is perhaps easier than creating a bunch of symlinks, but it does not protect and separate application from the user configurable data.  And it exposes the system to significant security and privacy risks.

---

### Post by rsay on 2009-01-14
Craig73,

I appreciate you looking at the howto. I will try to respond to your points. To give you more background information: I don't run very much windows software; 3 applications total. 2 of them are for my personal use only, but 1 is used by my whole family. I use this setup in my home to run Rosetta Stone language software. The program only allows 3 installations and I have 5 users. The program is way too expensive to buy a second license and the software that allows me to monitor the kids individual progress wouldn't work if I installed it for individual users.

User experience:
1. I agree that nobody should "personalize" a shared program. The changes will be seen by everybody. In my case, however, the software I am sharing has its own user management so learning progress, microphone settings etc. are individualized.

Stability:
1. A user with permissions to access windows programs as the windows user can install windows application updates that are accessible from within the application. Any desirable or undesirable changes would be shared by all the users. 
2. I think the risk of data corruption would be the same as opening a second copy of the same application in any wine installation. Obviously, the risk would vary with each windows program. I have everybody just close the Rosetta Stone program when they are done with their lesson, because I worry about possible data corruption too. I haven't specifically tried to mess it up, but I haven't had any problems either. I suppose  fast-user-switching could be disabled if the program you are working with is prone to data corruption. Somebody really good could probably even write a wrapper around the fast user switcher to check if the shared windows user was running a program before allowing a switch. You might be able to have your cake and eat it too.

Security:
1. You cannot trick a user into running a program with elevated privileges. You probably saw *sudo* and got concerned that we were running as root. Everybody, who is given access, will run the programs with the privileges of the windows user that you configure. If you check the first two links under the credits, you will see that I derived this method from users who wanted to run firefox as an unprivileged user, outside of their normal account, for *more secure* internet browsing. I recommend in the howto that the windows user be given only the privileges required to run the programs you share. My windows user can access the cd and play/record sound. My windows user can't read/write to any other users directories. I believe the risk to my system is actually less when running applications in the shared wine than under my personal wine, because the windows user has less system privileges than my normal user account does.

2. I agree with you entirely here. No data used in a shared environment can be confidential. Remember, that *you* are choosing the group of people who will have access to your information. You have multiple options here. As mentioned in the howto, if you want to work with something really confidential, you would install it to your personal wine. If you have something that should only be shared with a subset of users, you can go through the process a second time and define a more limited group. You can make it as granular as you want. One of the elegant things is that this shared wine environment is not a replacement for a more secure and more stable single user wine environment. It is used *in addition* to the single user wine environment, to solve specific problems. 

If you haven't tried to create a multiuser wine environment in a while, you might not know that the "tried and true" symlink method stopped working. (That's what got me started on this project.)  If the symlink method were feasible (or becomes feasible again), I hope you have a better understanding of how this method would  provide you with a *more secure* environment by running  applications as an unprivileged user. 

Although I disagree with the harshness of your conclusion, I believe that you have made some valid points about data privacy and how each user could mess things up for the others. These points would be applicable to any shared user environment. I will edit the howto to reinforce these cautions. I hope I have provided you some insight into how you can mitigate or eliminate your concerns and still have the benefit of a shared wine environment, if you need it.

---

### Post by synss on 2009-01-17
Hi, that is nice, but I believe there is a simpler way: instead of creating a **user** windows, why not simply create a **group**? This avoids requiring sudo and feels more appropriate to me.

In short, create a group 'wine' (I call it wine, and not windows, but it does not matter)
```
sudo addgroup wine
```
add whoever needs to be part of this group
```
sudo gpasswd -a <USER> wine
```
where <USER> is a user who should have permission to use wine
move .wine/drive_c away (I suppose wine is already installed!) and set the correct permissions
```
sudo -s
mkdir -p /usr/local/wine
mv ~/.wine/drive_c /usr/local/wine
chown -R root:wine /usr/local/wine
chmod g+r /usr/local/wine
exit
```
the chown line says /usr/local/wine and all of its contents belong to group wine;
the chmod line says every member of the group wine can read the files within /usr/local/wine (it is probably the default, anyway, so I guess it is not necessary; one may want to check that the group has execute permission on the exe files and the directories)
finally, symlink the users ~/.wine/drive_c to /usr/local/wine
e.g., ```
mv ~/.wine/drive_c{,.bak}; ln -s /usr/local/wine_c ~/.wine/drive_c
```
the mv thing backs up ~/.wine/drive_c. There should not be any ~/.wine/drive_c anymore since we moved it to /usr/local/wine, so if it gives an error, it is a good sign! However, if you do it for several users, and they have already run wine, you need to move their drive_c out of the way. The ln thing actually creates the symlink.

Done, no need to use sudo later, when you run windows apps.

NB: you had better use your own user with the chown command, e.g., ```
chown -R synss:wine /usr/local/wine
``` so that you can install (you and only you, by the way) windows apps without root permissions.

---

### Post by rsay on 2009-01-21
synss,

I was trying to test your technique and I think I'm close. I can run notepad as different users but I am getting the following error when I try to install pokerstars:

```
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\ron\\Desktop".
```

Do you have any idea where I went wrong?

---

### Post by qmax on 2009-09-21
this method will not work for application that want to be single windowed per user.

just like firefox or openoffice.
each instance of such app should be started as separate user.

---

### Post by rsay on 2009-09-22
qmax,

Can you give me some more details about what you mean? I don't think I understand your post. 

As described in the first post, this method was derived from techniques that people use to run firefox as a separate (typically unprivileged) user on their regular desktop. If you wish to use it that way, you just wouldn't give anyone else access to that user profile. 

Example:
sudo -u qmax_unprivileged -H firefox

---

### Post by snkiz on 2009-09-22
you need to setup fake windows users, I been trying of and on. I don't think wine is equipped to handle that right now as the registry keeps getting over-written when ever I try.

---

### Post by rsay on 2009-09-23
snkiz,

In the original post, you will see that this method does use a fake user called "windows" to host the shared wine installation. Your real users can still use their regular wine installation just like before. 

> I been trying of and on. I don't think wine is equipped to handle that right now as the registry keeps getting over-written when ever I try. 

I wasn't able to tell from your post exactly what you have been trying or why your registry was being overwritten. I am guessing that you are talking about trying to simply symlink the .wine folder between users. That method became depracated some time ago, which is why this workaround/howto was developed.

---

### Post by snkiz on 2009-09-23
No no I meant Iv'e been trying to create windows users under wine. as I have a couple programs that don't like the  method described in this thread. I add the users in the reg It all looks like it should work.. but wine she is stubburon. It "corrects" all my changes. I did how ever manage to symlink the menus so they just show up when you install something, and to make life easier I copied the main wine launchers replaced the launch command, and set the new launchers as default to open exe files. All very tidy.

---

### Post by richfeat on 2009-10-03
Hi rsay, many thanks for the posts - works pretty well.
One question ... my .desktop file looks like

[Desktop Entry]
Name=Watchtower Library 2008 - English
Exec=env WINEPREFIX="/home/windows/.wine" sudo -u windows -H wine "C:\\Program Files\\Watchtower\\Watchtower Library 2008\\E\\WTLibrary.exe" 
Type=Application
StartupWMClass=Wine
Path=/home/windows/.wine/dosdevices/c:/Program Files/Watchtower/MEPSCommon
Icon=40f6_wtlibrary.0

If I link this into a user's ~/Desktop folder it does work. However the desktop link has a big red X superimposed on it, and when it is clicked a dialogue comes up saying "Untrusted Application Launcher" with only "Launch anyway" or "Cancel" options. The "Untrusted Application Launcher" does work OK, but do you know how to mark the launcher as "trusted"? Also, the desktop does not show the assigned icon, but that may be OK when the launcher has been marked as "trusted". If the app is installed as usual in the user's home directory, the launcher is also flagged up as "Untrusted" - but the dialogue has an extra button allowing it to be marked as "Trusted", and then the correct icon shows up. Eeebuntu 3.01 (Jaunty based?).

Thanks if you can help

---

### Post by qmax on 2009-11-04
(sorry for lat, it's on abandoned mail acc)

RT @rsay:
what i meant is that some application can be launched only once from the same user.
it will resuse to start second instance from the same user.
for instance, if you open 2 x-sesions on different tty, u cannot run firefox on both.
another example is openoffice, and i've met some windows stuff.

RT @reachfeat:
see above comment.
for some app this shortcut will be usable only once
(will not work for second user at the same time, but that's probably not you case unless you have x-terminals)

much better solution is similar to what @synss tell
(and there's more detailed very good HOWTO somewhere on wine wiki):

let each user have each own ~/.wine with user.reg for personal preferences, 
and let ~/wine/drive_c be symlinked to shared folder.
(userdef.reg is also good think to be linked)

NOTE:
this folder (/usr/local/wine in @snyss example)
should be readable by all, and writable by admin only (maybe not root)
BUT:
drive_c/windows/temp and probably drive_c/temp should be writable by all - some apps may want to use them.
also, directory drice_c/profiles/ also should be writable for users, 
some apps may want to store stuff there and create profile directories.

Finally,
I have sucesfully set up callcenter for about 20 x-terminals to work under ltsp, with kde, firefoxen and wine stuff.
But i had to create separate user account for each terminal and make symlinks as described above.

---

### Post by rsay on 2009-11-05
As I posted in reply #21. I thought that the method synss posted looked quite promising. I tried to implement it the same day it was posted. Unfortunately, it gave me the errors I posted, the first time I tried to install new software. It has two other drawbacks that I don't think I like:

1. I think I lose some control over user access. For example, using synss' technique, how do I set it up so Rosetta stone is installed to a wine shared by my whole family; a finance program is installed to a wine useable only by my wife and I; and a poker program is installed only for me? 

2. If I understand synss' technique, I think my wine programs would run with my regular user privileges and not the limited privileges of the windows user. I prefer to run windows programs in their own little sandbox, without giving them access to my data. 

I tried to find information on the wine wiki for clarification of synss' method, but I failed. Some posts on the wine forums talk about his method or something similar, without giving a step-by-step guide that I could locate. If I could find a good howto, I would link to it in the first post so people could consider alternatives.

---

### Post by IkeLewis on 2010-01-11
OK, I am trying to do something similar. I have a ton of educational software that I am installing with wine, and it needs to be shared between several users. In this case, a lot of the software is personalized, but it needs to be separate for each user. Could I just copy the .wine directory into each user's home directory? 

The only problem I could see with that would be that I would have to mantain each individual user's wine configuration and installations separately.

Does anyone have any thoughts about this idea?

---

### Post by rsay on 2010-01-12
IkeLewis,

I originally started using this technique for Rosetta Stone. I have it installed once for the windows user and then each user launches the software from their desktop. The Rosetta Stone program then keeps track of each individual's progress. For me, this was a licensing issue. Rosetta Stone only allows three installs. Unfortunately, if you install it seperately for three users, with wine, on one computer, you have used up all your licenses.

---

### Post by TheDudeAlex on 2011-02-17
Hi everyone,
Just wanted to check if by now (feb 2011) there isn't a better way of doing this?

To me, this seems like a pretty basic feature wine should have...
I find it strange that programs are installed in ~/home
I've done some googling and I think I'll give this a try.

Greetings, Alex

---

### Post by snkiz on 2011-02-17
good luck I gave up on it, wasn't worth the trouble.

---

### Post by Aeonis on 2011-03-21
Can't wait!

---

### Post by Aeonis on 2011-03-22
> **Aeonis said:**
> Can't wait!

Tried it...getting this now:

boyd@Prometheus:~$ sudo -u 'windows' wine '/home/windows/.wine/dosdevices/c:/Program Files/StarCraft II/StarCraft II.exe'
wine: /home/boyd/.wine is not owned by you


I went through it step by step.  It's possible I missed something, but I double checked and I don't feel like I am.

Any pointers?

---

### Post by Aeonis on 2011-03-22
> **Aeonis said:**
> Tried it...getting this now:

boyd@Prometheus:~$ sudo -u 'windows' wine '/home/windows/.wine/dosdevices/c:/Program Files/StarCraft II/StarCraft II.exe'
wine: /home/boyd/.wine is not owned by you


I went through it step by step.  It's possible I missed something, but I double checked and I don't feel like I am.

Any pointers?


I had to do this to run it under my login (which I used to go through this process):

sudo -u windows env WINEPREFIX="/home/windows/.wine" wine C:\\windows\\command\\start.exe /Unix /home/windows/.wine/dosdevices/c:/users/Public/Start\ Menu/Programs/StarCraft\ II/StarCraft\ II.lnk

After that, it works under my name, but when I switch to my brother's, it says he doesn't have permission to run that.  He's in the "admin" group for this setup.  Also, when I tried to run that command, I got prompted to type in sudo password for my brother (now referred to as seth).

---

