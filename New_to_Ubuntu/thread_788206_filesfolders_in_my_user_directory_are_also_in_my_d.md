---
title: "files/folders in my user directory are also in my desktop. Don't want that"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by hanzj on 2008-05-09
In my home/hanzj/ folder, I have  the ff:

audio folder,
documents folder,
pubic folder
Templates folder
jpilot.log file.

[I accidentaly deleted Desktop shortcut/link/file. Please help me get it]

In my desktop, I have the ff:

iPod icon
audio folder,
documents folder,
pubic folder
Templates folder
jpilot.log file.


When I make changes one on, it changes the other. In other words, one set is not merely links. What's going on? In the past (yesterday), I had just the iPod icon on my desktop. I was doing some spring cleaning, moving stuff from one folder to another, deleting stuff I didn't need. I must have accidentally deleted the desktop folder/link in my home/hanz/ folder.

Please help.

---

### Post by dstew on 2008-05-09
Maybe the rule is that if your /home folder does not have a Desktop folder, then the desktop displays the contents of your /home folder. Did you try to create a Desktop folder?```
mkdir ~/Desktop
```

---

### Post by llamakc on 2008-05-09
[http://ubuntuforums.org/showpost.php?p=4870985&postcount=3](http://ubuntuforums.org/showpost.php?p=4870985&postcount=3)

---

### Post by hanzj on 2008-05-09
1) would it make a difference if Desktop had a small "d"... as in "mkdir ~/desktop"

I created both "desktop" and "Desktop" but they seem to be just regular folders.

2) There _was_ a desktop folder originally, before I did my spring cleaning.

---

### Post by llamakc on 2008-05-09
If you're using GNOME the answer on how to fix it is in the link I posted (where I answered it for someone else earlier).

---

### Post by hanzj on 2008-05-09
There was no "check mark" to begin with. In other words, [http://ubuntuforums.org/showthread.php?p=4870985&mode=linear#post4870985](http://ubuntuforums.org/showthread.php?p=4870985&mode=linear#post4870985) does not apply to my problem.

---

### Post by llamakc on 2008-05-09
> **hanzj said:**
> There was no "check mark" to begin with. In other words, [http://ubuntuforums.org/showthread.php?p=4870985&mode=linear#post4870985](http://ubuntuforums.org/showthread.php?p=4870985&mode=linear#post4870985) does not apply to my problem.

Okay. So give more information. Are you using GNOME, KDE? What else?

This 'spring cleaning' you were doing—was it inside of the terminal, or by dragging/dropping folders?

---

### Post by hanzj on 2008-05-09
Using gnome.
Spring cleaning was done with 2 nautilus windows side by side.

---

### Post by llamakc on 2008-05-09
Were they both opened as JUST you the user, or were one of them with superuser privileges? Have you already dumped the Trash yet?

---

### Post by hanzj on 2008-05-09
both were opened as regular user. Yes, trash is empty.

---

### Post by llamakc on 2008-05-09
The directory ~/Desktop is an actual directory so you want to recreate it.

```

mkdir ~/Desktop

```

Next, you very well may have to log out and back in. 

Were you removing any hidden directories while you were spring cleaning?

---

### Post by hanzj on 2008-05-09
I made the ~/Desktop and logged out and in, but it's still a regular folder.
In the top panel, I go to Places/Desktop, but, funny, it leads me to my home/hanzj folder.
No, I wasn't removing any hidden directories, I don' t think.

---

### Post by llamakc on 2008-05-09
That earlier suggestion I made (that you said did not apply) please try CLICKING that checkbox, and then UN-CHECKING it. See if that helps. 

~/Desktop is and should be a regular folder. Your problem is that Nautilus is acting up.

---

### Post by hanzj on 2008-05-09
I did the Uncheck then Check plan, even logging out and then in after Unchecking, but now, when the check is gone from "show_desktop", my desktop is completely clean. Even the iPod icon is gone.

---

### Post by llamakc on 2008-05-09
> **hanzj said:**
> I did the Uncheck then Check plan, even logging out and then in after Unchecking, but now, when the check is gone from "show_desktop", my desktop is completely clean. Even the iPod icon is gone.

Cool. Make sure there is a directory in /home/hanzj called Desktop. If you have the terminal open do this:

```

cd

```Now you'll be in your home directory /home/username

Next, check if a directory named Desktop is in there:

```

ls -l

```If you do not see an entry like the below, 

```

drwxr-xr-x 11 ken ken    4096 2008-05-09 11:41 Desktop

```Of course "ken" refers to myself in the above. So if you DO NOT SEE THAT when running `ls -l` in your /home/username do this:

```

mkdir ~/Desktop

```I recommend you cut and paste the above snippet. Of course since you are already in your home directory the ~/ is unneeded, but I want to make sure you're creating the correct directory in the appropriate location.

NOW, after you have done that, let's 'touch' a blank file in that directory.

```

touch ~/Desktop/I_CAN_BE_DELETED.txt

```In GNOME, you should see a file pop up with that name. It may be deleted.

Nautilus uses the Directory ~/Desktop for what is shown on the graphical "desktop" when you are logged into GNOME by default.

Whatever you did when you were doing your spring cleaning removed this functionality.

---

### Post by hanzj on 2008-05-09
I did all that. 
Yes I see the entry similar to your when I do "[FONT=monospace]ls -l". when i do "mkdir ~/Desktop", it says that "file exists" already.
I then do the touch command, and yes, I see the txt file in the Desktop folder (in Nautilus), but not on the real Desktop.
[/FONT]

---

### Post by llamakc on 2008-05-09
I can be of no further help. If it were my system I would move the 'stuff' I want to keep and put it somewhere else, then I would either create a new user with admin privileges (and move my stuff to that account's directories) or reinstall.

---

### Post by KIAaze on 2008-05-09
One simple thing to test if it's a system problem or just a user setting problem:
Create a new user account and log into it to see if the Desktop behaves normally.
System->Administration->Users and groups->Unlock->Add user

If the new user account has a normally working desktop, you might be able to solve the problem by removing the .nautilus folder in your home directory.
However, this will also remove all kinds of nautilus settings. So it might be better to rename it.
```
mv .nautilus .nautilus.backup
```

Then log out and in again to see if it worked.
If there's still a problem, you could try the same with the .metacity, .gnome and .gnome2 folders.
(careful: .gnome/.gnome2 contains theme settings, shortcuts, etc, so you should really back it up)

---

### Post by hanzj on 2008-05-09
just wanted you to know that the "testing" new user account i created had  a normal desktop. I'll now go through your further steps.

"mv .nautilus .nautilus.backup" (with log-out- log-in) doesn't help.

---

### Post by hanzj on 2008-05-09
> **KIAaze said:**
> 
However, this will also remove all kinds of nautilus settings. So it might be better to rename it.
```
mv .nautilus .nautilus.backup
```Then log out and in again to see if it worked.
If there's still a problem, you could try the same with the .metacity, .gnome and .gnome2 folders.
(careful: .gnome/.gnome2 contains theme settings, shortcuts, etc, so you should really back it up)

Will doing mv .gnome .gnome.backup be considered a backup?

---

### Post by hanzj on 2008-05-09
I don't have a .metacity folder. Is that a problem?

---

### Post by KIAaze on 2008-05-09
**Try gconftool-2 command below first. This is most likely to solve the problem.**

> **hanzj said:**
> Will doing mv .gnome .gnome.backup be considered a backup?
Yes.

And I don't think it's a problem if you don't have a .metacity folder unless the new user you created has one by default.

If the new user account has a .metacity folder, you can copy it to your user account. You could do the same with all hidden folders actually.
I don't know exactly where the Desktop stuff is handled.

Eventually you could also simply reset your gnome registry settings with this command:
```
cp .gconf .gconf.backup
gconftool-2 --recursive-unset /apps/
```

I just found this while searching for the command again:
[http://www.linuxinsight.com/how-to-cleanup-your-gnome-registry.html](http://www.linuxinsight.com/how-to-cleanup-your-gnome-registry.html)

Might also be helpful. :)

Actually, this reminds me that **the problematic user settings might be in the .gconf folder and not in .gnome,etc.** ^^'

---

### Post by hanzj on 2008-05-09
There is a .metacity folder in the "testing" user account.

---

### Post by KIAaze on 2008-05-09
And did you try the gconftool-2 unset command?

Also, make sure you always have a ~/Desktop folder when trying the different things I suggested.
Because I don't think it will be recreated automatically if missing unlike the hidden .* folders.

---

### Post by hanzj on 2008-05-09
maybe i should just migrate my personal files (docs, media, etc) into a brand new account.

---

### Post by hanzj on 2008-05-09
What are the negative repercussions of doing
 gconftool-2 unset command
?

---

### Post by KIAaze on 2008-05-09
It resets everything in the gconf registry to default.
This can go from keybindings to pannel applets and desktop background.

So nothing dangerous actually. It'll just be as if you just installed Ubuntu (or created a new account) except that your files and installed programs will still be there.
I used it once and the only thing that really bothered me were that all the special launchers I had created in the panel had disappeared.

You can use gconf-editor to edit the registry manually:
```
gconf-editor
```

---

### Post by hanzj on 2008-05-09
:~$ cp .gconf .gconf.backup
cp: omitting directory `.gconf'


Is that the output we should have?

---------
:~$ gconftool-2 --recursive-unset /apps/
Failure during recursive unset of "/apps/": Bad key or directory name: "/apps/": Key/directory may not end with a slash '/'


I then removed that slash that came after apps:
		:~$ gconftool-2 --recursive-unset /apps
and I got no "printout".

---

### Post by KIAaze on 2008-05-10
oops, sorry, it should be:
```
cp -r .gconf .gconf.backup
```
For directories, you must use the "-r" (recursive) option.

Of course, you could also rename using "mv .gconf .gconf.backup" and at the next login, it should be recreated automatically with the default values as far as I know.
> 
I then removed that slash that came after apps:
:~$ gconftool-2 --recursive-unset /apps
and I got no "printout".
Yes, the slash must be removed.
It could be normal that there's no printout.
I don't want to try it again on my gconf right now. ^^

---

### Post by hanzj on 2008-05-10
I've done the unset command now. I've rebooted the computer. The change is that now I can see the "Desktop" folder from the Places menu in panel. 
But still the _real_ desktop still just shows the contents of my home folder.

And yes, the Desktop folder was there in all this.

---

### Post by KIAaze on 2008-05-10
Then I really don't know what to do. :/
You could move all your data to a new user account of course...

---

### Post by hanzj on 2008-05-10
that's what i'll do.
For regular users, they should be prevented from doing this. 
Stuff like this is a barrier to Windows users getting to Ubuntu/Linux.

This thread will remain unsolved until the solution is posted.

---

### Post by KIAaze on 2008-05-10
I think I found something:
[https://bugs.launchpad.net/ubuntu/+bug/151576](https://bugs.launchpad.net/ubuntu/+bug/151576)
[http://pythonide.blogspot.com/2007/11/how-to-change-or-recreate-your-desktop.html](http://pythonide.blogspot.com/2007/11/how-to-change-or-recreate-your-desktop.html)
(Now why didn't I use google right away to find out how to change the Desktop folder?)

```
[76][~]$  cat ~/.config/user-dirs.dirs
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
#
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

So maybe you should try editing that "~/.config/user-dirs.dirs" file.
If it still doesn't work, try the radical folder renaming again:
```
mv .config .config.backup
```

Hidden folders (.*) are used to save application user settings most of the time. (or game saves)
So if it's a user setting issue, it's likely to be solved by renaming/removing them.

edit:
An interesting little discussion I found while searching about this:
[https://wiki.ubuntu.com/HomeAsDesktop](https://wiki.ubuntu.com/HomeAsDesktop)
Soon your problem might be a feature! xD

---

