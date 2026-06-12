---
title: "Weird directory things going on... no desktop?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-05-13
Alright, so I was playing Sauerbraten for the first time (fullscreen) and after a death, I took a break and left the computer for a while; the screen was still up.  I came back a while later and the mouse was not responding, and neither were any keyboard commands.  So I did a hard reset.

Upon rebooting, I saw icons on my desktop of the 6 directories I have in my /home/user folder (those icons weren't there before; I don't use any icons).  So I went into the command line to see why they were on my desktop, and my desktop claimed that it was empty.  All of my other directories have their correct contents, though.

When I open those directories in the GUI, they are listed as being in /home/directoryName , rather than /home/Desktop/directoryName .

Also, a few days ago, I changed the names of those 6 folders to being all lowercase, including Desktop to desktop.  I have changed them back since the hard reboot, but still nothing in Desktop.

And one last thing, I went to take a screenshot of this and when the save prompt came up, two things were wrong.  The icon next to my username is the same as the little desktop icon seen in the lower left of the screen, rather than a blue folder.  When I click on Desktop to save it there, it switches it automatically to my home folder.

Anyone know how to restore my desktop?

---

### Post by bumanie on 2008-05-13
Can't explain what happened, but this is the standard method of reinstalling the desktop. Can't promise that it will work in your situation.
> sudo dpkg-reconfigure ubuntu-desktop

---

### Post by sdennie on 2008-05-13
I'm not sure how that happened but, you should be able to fix it by starting gconf-editor and unselecting desktop_is_home_dir in /apps/nautilus/preferences.  You may also want to go to System->Preferences->Sessions and uncheck User Folders Update to prevent the folders from getting renamed.

---

### Post by ConMan318 on 2008-05-13
> **vor said:**
> I'm not sure how that happened but, you should be able to fix it by starting gconf-editor and unselecting desktop_is_home_dir in /apps/nautilus/preferences.  You may also want to go to System->Preferences->Sessions and uncheck User Folders Update to prevent the folders from getting renamed.

The description of that is "If set to true, then Nautilus will use the user's home folder as the desktop. If it is false, then it will use ~/Desktop as the desktop. "

Don't I not want to do that?  Since Documents, Pictures, etc. are in my home directory, I do not want my home directory to be my desktop.  I checked it to test it but it didn't change anything.

The problem is this:
```

connor@connor-laptop:~$ pwd
/home/connor
connor@connor-laptop:~$ ls
Desktop  Documents  Music  Pictures  Public  Videos
connor@connor-laptop:~$ cd Desktop
connor@connor-laptop:~/Desktop$ ls
connor@connor-laptop:~/Desktop$ 

```

So my home directory is where those 6 folders are located, yet they are displayed on the desktop rather than the empty Desktop folder.  And bumanie, I tried that too, unfortunately it didn't work. :(

Thank you both for trying to help though, any other ways?

EDIT: Wow apparently I can't read, I thought the above post said to **check** that box rather than to uncheck it.  Either way, it was unchecked from the start, but I checked/unchecked it again and nothing changed.

---

### Post by canthus13 on 2008-05-13
Maybe your desktop is set to your home folder?  Install Ubuntu Tweak and look under desktop settings... There may be other ways to do this, but this is the only way I know right off hand.

--Me

---

### Post by Clancy_s on 2008-05-13
> **ConMan318 said:**
> EDIT: Wow apparently I can't read, I thought the above post said to **check** that box rather than to uncheck it.  Either way, it was unchecked from the start, but I checked/unchecked it again and nothing changed.

PMJI: I have the same problem on a Ubuntu 7.10 64 bit install, with all upgrades.  

I've had it for a couple of months but have been too busy to look in to it.  I wanted to fix it before upgrading to Hardy, I thought I'd join in here rather than starting a new thread.

As you mention it started out of the blue one boot, and *desktop_is_home_dir in /apps/nautilus/preferences* is not selected.  I did try selecting and unselecting it to see if that helped, it didn't.

I tried renaming my .nautilus folder to see if the problem went away when nautilus generated a new config file, that didn't help.

When the problem started the *Desktop* folder disappeared from Nautilus and my home folder has the little desktop icon instead of a standard folder one.  I tried making a new empty one, all that happened was a new folder called *Desktop* appeared on my desktop.

It behaves as though home and desktop have fused somehow but without selecting *desktop_is_home_dir* :confused:

I'd not heard of Ubuntu tweak, I'll look at that tonight.

eta: I found another thread from someone having the same problem (it started a different way but the end problem seems the same), that suggests a possible solution, here:

[http://ubuntuforums.org/showthread.php?t=581498](http://ubuntuforums.org/showthread.php?t=581498)

There's also a lauchpad report on this which is where they found the solution:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037)

I'll try that tonight first I think.

---

### Post by ConMan318 on 2008-05-14
That first thread link you posted did the trick; thank you for posting that.

---

### Post by itsjustarumour on 2008-05-14
> **ConMan318 said:**
> Alright, so I was playing Sauerbraten for the first time (fullscreen) and after a death, I took a break and left the computer for a while; the screen was still up.  I came back a while later and the mouse was not responding, and neither were any keyboard commands.  So I did a hard reset.

Upon rebooting, I saw icons on my desktop of the 6 directories I have in my /home/user folder (those icons weren't there before; I don't use any icons).  So I went into the command line to see why they were on my desktop, and my desktop claimed that it was empty.  All of my other directories have their correct contents, though.

When I open those directories in the GUI, they are listed as being in /home/directoryName , rather than /home/Desktop/directoryName .

Also, a few days ago, I changed the names of those 6 folders to being all lowercase, including Desktop to desktop.  I have changed them back since the hard reboot, but still nothing in Desktop.

And one last thing, I went to take a screenshot of this and when the save prompt came up, two things were wrong.  The icon next to my username is the same as the little desktop icon seen in the lower left of the screen, rather than a blue folder.  When I click on Desktop to save it there, it switches it automatically to my home folder.

Anyone know how to restore my desktop?

Just a quick "+ one" to say I've been having some similar problems... will try the fixes in this thread and report back!

---

### Post by Clancy_s on 2008-05-14
> **ConMan318 said:**
> That first thread link you posted did the trick; thank you for posting that.

You're welcome. :)

I used the slightly simpler method posted at lauchpad (ie omitting the fiddling with *desktop_is_home_dir *):

1. First, enter this code into a Terminal:

```
sudo gedit ~/.config/user-dirs.dirs
```

2. Look for this entry: XDG_DESKTOP_DIR="$HOME/". Make it like this: XDG_DESKTOP_DIR="$HOME/Desktop"

3. Now log out and log back in.

For me that fixed the problem, no Nautilus crash, no need to fiddle with processes nor run Nautilus from a terminal.  Whilst looking at *user-dirs.dirs* I noticed that XDG_PUBLIC, XDG_MUSIC and XDG_DOWNLOADS all also pointed to HOME.  I hadn't noticed any effect from those but on spec I changed them to point to the appropriate directories.

---

