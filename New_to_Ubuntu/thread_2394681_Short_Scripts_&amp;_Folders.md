---
title: "Short Scripts &amp; Folders"
date: 2018-06-19
forum: New to Ubuntu
---

### Post by electrosteam on 2018-06-19
Lubuntu 17.10(.1) waiting for 18.04.1 LTS, a single user very plain old Dell laptop used for CAD and office work.

I am feeling my way through script writing and just a little confused.
What would be the best arrangement for me to organise simple scripts ?

Two existing short scripts are on the desktop and held as Desktop Entries, each with a single line of commands, work great.

A third is similar with multi-part commands, but it won't run, even though the commands in the terminal run fine.
In the process of trying to run it from a folder - /home/john/scripts, and running into make exec, set background and permission learning challenges. - just seems too hard for such a simple task.

A forth script is a longer one held in /usr/share/applications with a desktop icon link and it works fine.

What is the best way for me (single user machine) to organise short scripts, and what folder is recommended ?
I am up to the learning challenge, just need guidance on how to organise.

John

---

### Post by again? on 2018-06-19
I just place my scripts in ~/scripts.
A couple I use all the time I copy to ~/bin so they can be run without specifying the path.
```
glen@Bionic:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/glen/.local/bin:**/home/glen/bin**
```

Often used scripts I add to a .desktop file utilising a quicklist.
The .desktop file is placed in ~/.local/share/applications
eg this is my ~/.local/share/applications/MyScripts.desktop file.
```
[Desktop Entry]
Version=1.0
Name=Scripts
Exec=xdg-open /home/glen/scripts
Type=Application
Icon=/home/glen/Pictures/icons/coloured_folders/scripts-folder-flipped.png
Comment=My personal scripts
StartupNotify=false

# This sets the content and order of the Quicklist. Must match the [Desktop Action xxxxxxx]
Actions=Background;Buckle;network-restart;Ping;reloadPlank;Speed;swap;Test Script;RunTest;reloadtint2;Upper2lower;VivaldiCSS;VivaldiPatch;zsync;separator;edit-launcher;


[Desktop Action term-kill]
Name=xfce4-terminal kill   
Exec=killall xfce4-terminal

[Desktop Action Background]
Name=Background Reset   
Exec=/home/glen/scripts/background-reset-gradient.sh

[Desktop Action Whatismyip]
Name=Whatismyip
Exec=/home/glen/scripts/whatismyip

[Desktop Action zsync]
Name=Zsync Daily Iso
Exec=xfce4-terminal --tab --drop-down --title "Zsync" -e "/home/glen/scripts/zsync.sh"

[Desktop Action Cursor]
Name=Change Cursor
Exec=xfce4-terminal --tab --drop-down -e "/home/glen/scripts/change-cursor-trusty"

[Desktop Action Test Script]
Name=Test Script Edit
Exec=gedit /home/glen/scripts/aatest.sh

[Desktop Action Screensaver]
Name=Screensaver  OFF/ON
Exec=/home/glen/scripts/toggle_screen_blanking.sh

[Desktop Action Notes]
Name=Notes
Exec=gedit "/media/Data/Notes"

[Desktop Action open-command]
Name=Open command in Terminal
Exec=/home/glen/scripts/xsel-terminal.sh

[Desktop Action RunTest]
Name=Test Script Run
Exec=gnome-terminal -e "/home/glen/scripts/aatest.sh"

[Desktop Action ClockToggle]
Name=Clock-Toggle
Exec=/home/glen/scripts/toggle-clock.sh


[Desktop Action TooltipToggle]
Name=Tooltip-Toggle
Exec=/home/glen/scripts/tooltips-toggle-trusty.sh

[Desktop Action Brightness]
Name=Brightness
Exec=/home/glen/scripts/brightness.py

[Desktop Action Reboot]
Name=XP Reboot
Exec=/home/glen/scripts/Reboot_to_Windows

[Desktop Action reloadtint2]
Name=Tint2 Reload
Exec=sh -c "killall tint2 && tint2 &"

[Desktop Action reloadPlank]
Name=Plank Reload
Exec=sh -c "killall plank && plank &"

[Desktop Action separator]
Name=______________________________________
Exec=

[Desktop Action edit-launcher]
Name=Edit Launcher
Exec=gedit /home/glen/.local/share/applications/MyScripts.desktop

[Desktop Action Ping]
Name=Ping Test
Exec=/home/glen/scripts/pingtest.sh

[Desktop Action Speed]
Name=Speed Test
Exec=/home/glen/scripts/speedtest.sh

[Desktop Action Upper2lower]
Name=Upper to Lower
Exec=/home/glen/scripts/upper2lower.sh

[Desktop Action getip]
Name=Get-IP Loop
Exec=sh -c "killall get-ip-loop.sh; sleep 2 && /home/glen/scripts/get-ip-loop.sh"

[Desktop Action game]
Name=Game-Settings On/Off
Exec=/home/glen/scripts/game-settings.sh

[Desktop Action poker-fix]
Name=Poker Fix
Exec=xfce4-terminal --tab --drop-down -e "/home/glen/scripts/pokerth-sound-fix.sh"

[Desktop Action Buckle]
Name=Buckle On/Off
Exec=/home/glen/scripts/buckle-toggle.sh

[Desktop Action unilogout]
Name=Universal Logout
Exec=/home/glen/scripts/universal-logout.sh

[Desktop Action gnome-shell-replace]
Name=gnome-shell-replace   
Exec=/home/glen/scripts/gnome-shell-replace.sh

[Desktop Action network-restart]
Name=Network-restart   
Exec=xfce4-terminal --tab --drop-down --title "Network Restart" -e "/home/glen/scripts/network-restart.sh"

[Desktop Action swap]
Name=Swap On/Off 
Exec=xfce4-terminal --tab --drop-down --title "Network-restart" -e "/home/glen/scripts/swap_toggle.sh"

[Desktop Action VivaldiPatch]
Name=VivaldiPatch   
Exec=xfce4-terminal --tab --drop-down --title "VivaldiPatch" -e "sudo /home/glen/MEGAsync/configs/vivaldi/VivaldiPatch/vivaldi-patch.sh"

[Desktop Action VivaldiCSS]
Name=VivaldiCSS   
Exec=gedit /home/glen/MEGAsync/configs/vivaldi/VivaldiPatch/custom.css

```

---

### Post by Holger_Gehrke on 2018-06-19
The '/usr/share' hierarchy of directories is meant for data, possibly data shared across applications. Not quite the right place for an executable ...

The place for self-written (or self compiled) programs is '/usr/local/bin/'. It's even on the PATH, so you can call your scripts no matter what your current working directory is. Another option is to create a directory for this purpose in your home directory and put it on the path by putting a line like
```

PATH=$PATH:/home/myusername/myscriptdirectory

```
into ~/.profile or ~.bashrc. If you call your script directory 'bin', you can save yourself that trouble, a line to put it on the path is already in .profile ...

Holger

---

### Post by oldfred on 2018-06-19
If using Nautilus.

       Scripts here will appear in scripts menu
~/.local/share/nautilus/scripts/

Or:
        
 Note that it is a good idea to put your scripts in one place, so you can run them without requiring a path. If you create a bin directory in your home ( mkdir ~/bin ) the next time you login, that will automatically be included in your PATH. Then you could make a panel or desktop launcher as "Application in Terminal" to run your script with a click or double click of the mouse.
 Re: Starting multiple programs at once


[LIST=1]
[*]Do you have a bin directory in your home folder? If you do, skip forward to step 2. Otherwise, do the following:
[/LIST]
    mkdir ~/bin
chmod 755 ~/bin
gksudo gedit ~/.bashrc
[https://ubuntuforums.org/showthread.php?t=2233393&highlight=pkexec](https://ubuntuforums.org/showthread.php?t=2233393&highlight=pkexec)

---

### Post by electrosteam on 2018-06-20
It will take me a few days to absorb all the good advice.
Oldfred,
My file manager is PCManFM, not Nautilus.

I rather like the idea of a /bin folder in my home directory, but cannot generate ~/bin - permission denied.
Checked as follows, does this show that some of my problem is incorrect permissions on my home folder ?
I can fix, just need to know what it should be.
Is this a case for sudo ?

```

john@bluebox:~$ mkdir ~/bin
mkdir: cannot create directory ‘/home/john/bin’: Permission denied
john@bluebox:~$ cd ..
john@bluebox:/home$ ls -lt
total 12
dr-xr-xr-x 37 john john 12288 Jun 18 11:46 john
john@bluebox:/home$ 


```

John

---

### Post by Holger_Gehrke on 2018-06-20
Not having write permission on your home directory would explain a lot of problems. How did you manage to get anything done that way ?
```
chmod u+w /home/john
``` should fix it. 'You should not need to use 'sudo' for this, since you do still own the directory.

Holger

---

### Post by electrosteam on 2018-06-20
Holger,
Thanks for the confirmation, did as you suggested, then generated the ~/bin, no problems, 

Now to sort out my scripts.
Plan to have my scripts in ~/bin with a link for each common (daily) one on the desktop (old XP habits die hard), and absorb/understand the arrangement used by guber2.

John.

---

