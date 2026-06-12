---
title: "HOWTO: Change the Folder You Use For Your Desktop With a Right Click"
date: 2009-02-09
forum: Outdated Tutorials &amp; Tips
---

### Post by kamni on 2009-02-09
I've always thought of the Desktop as a great way to get easy access to whatever I'm working on, and to visually organize those files so I can tell which files are related.  I tend to get distracted pretty easily when I have too many things to look at, and that includes my Desktop.  So as a general rule, I only want files on my Desktop that I'm working with at that very moment.

The problem is, I often have multiple projects going, and it's a nightmare to keep moving project files back and forth between folders.  I sometimes end up with files getting mixed up or put in the wrong folder when switching between projects.  So I came up with a fun solution that lets me have multiple Desktops that I can switch between by simply right-clicking on the folder.  It even allows me to put custom launchers (Firefox, Audacity, etc.) on each Desktop, so I only see the icons for the applications I need for that project.

[SIZE="5"][COLOR="SandyBrown"]The Basic Idea[/COLOR][/SIZE]

While it's not yet possible in GNOME to have real multiple Desktops, it can be simulated by making the Desktop a simple link to the folder that you want, then deleting the link and re-linking to a new folder when you're ready to switch.  The linked Desktop is treated exactly the same way your normal Desktop folder is treated, so you can download files from Firefox or your email client to whichever Desktop you happen to be using without making any special changes.

[SIZE="5"][COLOR="SandyBrown"]What You'll Need[/COLOR][/SIZE]

This tutorial was written using Intrepid Ibex.  First, you'll need to bring up a command line ( 'Applications -> Accessories -> Terminal') and install Nautilus-Actions (ignore the 'user@ubuntu:~$' and only type the code that follows it):

```
user@ubuntu:~$ sudo apt-get install nautilus-actions
```

This tutorial uses Zenity to give pop-up notices of errors (or success).  If you want to be notified, make sure that you have Zenity installed by typing:

```
user@ubuntu:~$ sudo apt-get install zenity
```

If it's already installed, you should get a message saying that zenity is already the latest version. 

[SIZE="5"][COLOR="SandyBrown"]Setting Up The New Desktop System[/COLOR][/SIZE]

You may want to make a directory to keep all your desktop folders in, so you don't forget where you put them.  I called my folder "Desktops", but you can substitute whatever name is easiest for you to remember.

```
user@ubuntu:~$ mkdir Desktops
```

You need to make at least one folder that is going to be your default desktop, and move all the files from your current Desktop to this folder.  **It's important that you do this step!  In a moment we're going to delete your current Desktop folder, and it's important that you don't lose the files that are already there.  In fact, it couldn't hurt to copy those files to a USB stick, then do the following (substituting whatever your default folder name and location is going to be):**

```
me@ubuntu:~$ mkdir Desktops/Main-Desktop
user@ubuntu:~$ mv Desktop/* Desktops/Main-Desktop/
```

You might also want to create a few extra desktop folders, based on the projects you're currently working on (and you can always create more later).

```
me@ubuntu:~$ mkdir Desktops/Ruby_Projects
user@ubuntu:~$ mkdir Desktops/Love_Songs_For_Mara
user@ubuntu:~$ mkdir Desktops/Matts_Surprise_Party
```

...and so on.  Now we're going to delete your old Desktop.  Make sure that you've backed up your files to USB stick or wherever, do a visual check that there's nothing still sitting on your current Desktop that you might have forgotten to move to the new folder, and then do the following:

```
user@ubuntu:~$ rm -r Desktop/
```

If it asks you if you want to delete it, type "y".  Then link the new folder to the Desktop.  It's very important that the link has the full path to your new desktop directory in order for later steps to work, so do the following:

```
user@ubuntu:~$ ln -s `echo ~`/Desktops/Main-Desktop/ Desktop
```

Be sure that you use slanted quotes ( ` ) instead of straight quotes ( ' ) for the echo command, or it won't work.  The slanted quote is often located in the upper left corner of the keyboard with the ~ symbol.  Also, pay attention to the trailing slash on the end of "/Desktops/Main-Desktop/" -- if you forget it, you may get an error the first time you use the script and have to recreate your desktop using the steps listed above.

To refresh your Desktop so that the new files show up, click somewhere on your Desktop and hit F5.  Make sure all the files that were on your original Desktop are still showing up (although they may have been rearranged a bit).

[SIZE="5"][COLOR="SandyBrown"]Making the Right-Click Magic[/COLOR][/SIZE]

If you like doing things the hard way, you can easily keep switching desktops by typing the following (where "{name of new folder}" is the actual name of the folder), and then refreshing the Desktop with F5:

```
me@ubuntu:~$ rm Desktop
user@ubuntu:~$ ln -s `echo ~`/Desktops/{name of new folder}/ Desktop
```

But if you're like me and prefer to do everything with point-and-click, there's a much better way to do it.  Instead, we're going to be writing a script, so you may want to create a folder to keep it in.  You can put the script almost anywhere you want, but I highly recommend that you don't put it on your Desktop or it may not work at a later date.  For my script, I created a folder called "Scripts":

```
user@ubuntu:~$ mkdir Scripts
```

Open up a new text file called "change_desktop" in the scripts folder:

```
user@ubuntu:~$ gedit Scripts/change_desktop
```

Cut and paste the following code into the text file:

```
#!/bin/bash
if [ ! -z "$1" -a -d "$1" ]
then
    desktop_location=`echo ~`/Desktop/                  # get the home directory
    desktop_str_len=`expr length "$desktop_location"`   # calculate the length of the home directory string

    ##
    # If a folder on the Desktop is used for the script, Nautilus-Actions
    # will send the linked path '/home/{user}/Desktop/{sub-folder}/' 
    # instead of the complete path.  This causes an error when the script
    # removes the old Desktop link and tries to create the new one.  To
    # avoid this, the script checks if the new folder is a subfolder of the 
    # Desktop and expands the path before deleting the old link.
    ##
    
    new_path_len=`expr length "$1"`
    if [ $new_path_len -lt $desktop_str_len ]
    then
        new_path="$1"
    else
        test_path=${1:0:$desktop_str_len}
        if [ "$test_path" = "$desktop_location" ]
        then
            new_path=`readlink "${desktop_location:0:desktop_str_len-1}"`"${1:desktop_str_len}"
        else
            new_path="$1"
        fi
    fi
    
    # remove the old Desktop, and replace with a link to the new folder
    rm Desktop
    ln -s "$new_path" Desktop
    
    # optional confirmation message
#    /usr/bin/zenity --info --text="Desktop set to $new_path"
    
else
    # the script was run without a folder argument
    /usr/bin/zenity --info --text="No folder was selected for the new Desktop"
fi

# refresh desktop
#killall nautilus

```

**EDIT: See GMWeezel's comment below for a modification of the script.  If you use GMWeezel's version, you can ignore the following lines about uncommenting "/usr/bin/zenity..." and "killall nautilus".**

Right now the script only gives you a popup if you try to run the script without giving it a folder.  But if you also want it to tell you when it's done switching desktops, uncomment the following line:

```
#    /usr/bin/zenity --info --text="Desktop set to $new_path"
```

The way you uncomment the code is simply to delete the "#" at the beginning of the line.

Additionally, if want to avoid manually refreshing the desktop every time you run the script, uncomment the line at the end:

```
#killall nautilus
```

There is one downside to uncommenting this line: if your computer is slow the first time you run "killall nautilus" (see "Adding the Script to Nautilus Actions" below), you'll probably have that same wait every time you change folders.  Because my computer can be a little slow at times, I usually leave this commented out, and just refresh using the "F5" key, which is much faster.

And one final note: if you chose not to install Zenity, you'll want to make sure all lines that mention "/usr/bin/zenity" are commented out.  There should be two lines, both toward the end of the script.

Now save the code, close the editor, and make the script executable:

```
user@ubuntu:~$ chmod u+x Scripts/change_desktop
```

[SIZE="5"][COLOR="SandyBrown"]Adding the Script to Nautilus Actions[/COLOR][/SIZE]

Go into "System -> Preferences -> Nautilus Actions Configuration".  If you just installed Nautilus-Actions for the first time, it's possible it doesn't show up in your menu yet.  To get it to show up, type the following [WARNING: This will close any open file browser windows you have, and it will temporarily make the icons on your Desktop disappear]: 

```
user@ubuntu:~$ killall nautilus
```

It might take a minute or two, but after nautilus restarts you should see "Nautilus Actions Configuration" as an option.  When the "Nautilus Actions" dialogue is open, click "Add".  Now fill out the "Menu Item & Action" tab this way:

[INDENT]**Label:** Change Desktop to This Folder
**Tooltip:** Switches Desktop to the Folder Selected 
**Icon:** gtk-home (or another one, if you want)

**Path:** /home/jen/Scripts/desktop_scripts/change_desktop
**Paramenters:** %d/%f/[/INDENT]

On the "Conditions" tab make this change:

[INDENT]**Appears if selection contains:** [Only folders][/INDENT]  

Click "Ok", and close the "Nautilus Actions" dialogue.  

If you'd like to test it out and see how it works, open up "Places -> Home -> Desktops".  Find a folder that isn't your current Desktop (something other than "Main-Desktop", if you've been using the same names that I have), or create one if you didn't make one earlier.  Copy something from your current Desktop to the new folder by right clicking on the item (maybe a text file, or a picture), selecting "Copy", and then right-clicking on the new folder and selecting "Paste Into Folder".

Right-click again on the new folder, and you should see an option towards the bottom that says "Change Desktop to this Folder".  Select that option, and voila!  If you uncommented the line "killall nautilus", just wait for nautilus to finish restarting.  If you left the line commented out, left-click anywhere on your Desktop background.  Hit F5 to refresh it, and you should now see the new folder with only the file that you just copied over.

Congratulations! You've switched your desktop!

[SIZE="5"][COLOR="SandyBrown"]A Last Warning[/COLOR][/SIZE]

The script you put in the right click assumes that the link to the Desktop is always the full path (something like /home/user/Desktops/Main-Desktop/).  If you decide to manually change the Desktop at a later date (by typing 'rm Desktop' and then 'ln -s <new folder>') be sure you use the full path and not a relative path like "Desktops/New-Desktop", and don't forget to include a "/" at the end.

[SIZE="5"][COLOR="SandyBrown"]Rescuing a Bad Folder Change[/COLOR][/SIZE]

If something goes wrong, you might get an error message like 'Nautilus could not create the required folder "/home/user/Desktop"' next time you try to open a file browser or create something on your desktop.  Don't panic. :P This can be fixed with just two lines in the terminal.  First, figure out which folder you were trying to switch to, and replace {new desktop} with the name of that folder in the following commands:

```
user@ubuntu:~$ rm Desktop
user@ubuntu:~$ ln -s `echo ~`/Desktops/{new desktop}/ Desktop
```

Remember to use the slanted quotes ( ` ) instead of straight quotes ( ' ), and don't forget the trailing "/" at the end.  Click on the Desktop background, and hit F5 to refresh.

[SIZE="5"][COLOR="SandyBrown"]Getting Rid of the Script[/COLOR][/SIZE]

If the code doesn't work the way you expect it, or if you decide you just want a normal non-changing desktop again, it's only a few steps to get you back to your old setup.  First, delete the link to whatever folder you're using for your Desktop right now, and make a real 'Desktop' folder:

```
user@ubuntu:~$ rm Desktop
user@ubuntu:~$ mkdir Desktop
```

Move your files from your previous desktop (assuming you were using Desktops/Main-Desktop/):

```
user@ubuntu:~$ mv Desktops/Main-Desktop/* Desktop
```

Left-click on the Desktop background and hit F5 to refresh.  Now go into "System -> Preferences -> Nautilus Actions Configuration".  Select the "Change the Desktop to This Folder" script and hit "Delete".  If you want to delete the source of the script, also do this:

```
user@ubuntu:~$ rm Scripts/change_desktop
```

---

### Post by GMWeezel on 2009-12-29
This is a great idea but there is a simple change that can greatly improve this script: to refresh the desktop, replace the "killall" line with the following code:```
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true
```
This toggles the icon visibility which will force the desktop to refresh.

EDIT: Alright, I couldn't resist but your script could have been optimized a lot more. Here is my version:

```
#!/bin/bash
if [ ! -z "$1" -a -d "$1" ]
then
    # Hide the desktop
    gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false

    # remove the old Desktop, and replace with a link to the new folder

    new=$(readlink -f "$1") # comes first incase it's inside ~/Desktop which
                            # will be removed shortly.
    rm "$HOME/Desktop"
    echo $new
    ln -s "$new" "$HOME/Desktop"

    # Show the desktop. Will now be different
    gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true

else
    if [ "$(which zenity)" ]; then
        zenity --info --text="No folder was selected for the new Desktop"
    fi
fi
```

Eventually, I think I will may write my own tutorial because there are a number of improvements and simplifications that could be made to this script.

---

### Post by kamni on 2010-01-10
Thanks for the input -- I'd been looking for an easier way to refresh the desktop from within a script for quite some time, and everyone's always given me the "killall" answer or some version of simulating key presses.

The simplification looks good, thanks to an option in readlink that I hadn't known existed -- I hope your tutorial comes out well!

---

