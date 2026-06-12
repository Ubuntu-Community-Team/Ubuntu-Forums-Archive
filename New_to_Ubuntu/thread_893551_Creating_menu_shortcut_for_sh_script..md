---
title: "Creating menu shortcut for sh script."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by vocalstud69 on 2008-08-18
I have an sh script, and I want to create a menu shortcut in the Applications Menu for it, so all I have to do is click on it and it launches the script and the things that the script is supposed to do.  I know the script works because when I type in ```
sh anathema.sh
``` in the command line, it works perfectly.  Can anyone help me?

---

### Post by Too Late on 2008-08-18
Go to System -> Preferences -> Main Menu and create a new item there.

---

### Post by cdtech on 2008-08-18
> **vocalstud69 said:**
> I have an sh script, and I want to create a menu shortcut in the Applications Menu for it, so all I have to do is click on it and it launches the script and the things that the script is supposed to do.  I know the script works because when I type in ```
sh anathema.sh
``` in the command line, it works perfectly.  Can anyone help me?

Open a terminal and type:
```
**alacarte**
```
Select the "Menu" you want it under and then select "New Item". You'll get a popup to fill in the information, use the full path to the script and your set.

Hope this helps.....

---

### Post by vocalstud69 on 2008-08-18
Okay, I tried that, and this is what it gives me when I click on it.  The terminal pops up, then I get a window popup saying this:

"There was an error creating the child process for this terminal"

I have no idea what this means.  I tried setting it as Application and as Application In Terminal.  The Application selection brings up:


Could  not launch menu item.
Failed to execute child process "/home/richard/Exalted/Anathema/anathema.sh" (Permission denied)

In a popup window.  Please help.

---

### Post by cdtech on 2008-08-18
> Could not launch menu item.
Failed to execute child process "/home/richard/Exalted/Anathema/anathema.sh" (Permission denied)

Be sure the file has the correct permissions set:
```
la anathema.sh
```
could be you need to set permissions:
```
sudo chmod 775 /home/richard/Exalted/Anathema/anathema.sh
```

---

### Post by vocalstud69 on 2008-08-18
Well, now it doesn't give me any error at all, it just flashes a command prompt for a second, then nothing.  Bash says that the 'la' command does not exist, and I've never heard of it before.  I tried is both as an Application and as an Application in Terminal.  Sorry, I'm still kinda new at this scripting stuff.

Edit:  I did get it to the point where I could click on the script, and it would load the program.  I'm hoping that'll fix the problem.

---

### Post by cdtech on 2008-08-18
> **vocalstud69 said:**
> Well, now it doesn't give me any error at all, it just flashes a command prompt for a second, then nothing.  Bash says that the 'la' command does not exist, and I've never heard of it before.  I tried is both as an Application and as an Application in Terminal.  Sorry, I'm still kinda new at this scripting stuff.

My bad, I have that as an aliase. It should be "ls -al"

Try adding a sudo in front of the command line within your launcher and see if it will work.

---

### Post by vocalstud69 on 2008-08-18
This is what I get when I put in ls -al

```
-rwxrwxr-x 1 richard richard 925 2007-09-21 20:43 anathema.sh
```

Tried adding sudo at the beginning, and it'll ask me for my password, then the command line will disappear and nothing else will happen.  It does work when I just double click on the sh file, but creating a link to it does not, if I put it on the desktop.

If it helps at all, the program that I'm trying to run with the sh script can be downloaded here, if you're willing to go through the hassle:

[http://sourceforge.net/project/downloading.php?group_id=122320&use_mirror=voxel&filename=anathema_v1.3.1.zip&32050370](http://sourceforge.net/project/downloading.php?group_id=122320&use_mirror=voxel&filename=anathema_v1.3.1.zip&32050370)

The sh script is included in the .zip file.

Thanks.

Edit:  When I double click on the sh script, it asks me if I want to Run in Terminal, Display, or just Run.  I'm wondering that since it's giving me that, when I did chmod +x, I needed to add something else to it to just run the script.  Is that right?

---

