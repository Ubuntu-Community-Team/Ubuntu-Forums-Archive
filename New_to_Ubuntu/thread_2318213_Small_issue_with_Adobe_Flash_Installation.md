---
title: "Small issue with Adobe Flash Installation"
date: 2016-03-24
forum: New to Ubuntu
---

### Post by Eric_Knudson on 2016-03-24
Brand new to Linux, but a quick learner. Had to install adobe flash to do some online courses for school and went to their website, downloaded the tar.gz file for the plugin. It came with a readme. I did everything that the file said and it does work, however there are two files that were unpacked in my downloads directory that I cannot delete due to permission issues. I'm not sure if I even should delete them, but why would they be locked in the first place? Anyone else had this experience? Your advice is welcome.

The Files in question are usr and LGPL

Eric

---

### Post by sammiev on 2016-03-24
Hi and Welcome,

Press Ctrl + Alt + T

type in:

```
sudo apt-get update
```

```
sudo apt-get install flashplugin-installer
```

You can also find the package using "Ubuntu Software Center"

---

### Post by Eric_Knudson on 2016-03-24
Oh I have installed it, and it works, but it left two locked files "usr" and "LGPL" in my downloads folder that I can't get rid of now. It says I don't have permission.

---

### Post by sandyd on 2016-03-24
What is your username?

For those two folders (only), you can use chown to change the ownership of the folders. Currently, they are owned by another user which is why you do not have permissions. You can change the ownership using the chown command so that the folder is owned by you, then it can be deleted using the GUI.

Assuming your username is *eric*, and the folder is called "usr" and is in your Downloads folder, run
```

sudo chown -R eric:eric /home/eric/Downloads/usr

```

If your username is not eric, replace all occurrences of it in the above command.

---

### Post by buzzingrobot on 2016-03-24
> **Eric_Knudson said:**
> Had to install adobe flash to do some online courses for school and went to their website, downloaded the tar.gz file for the plugin.

This works, but it is not the preferred way to install Flash, or anything else in Linux.

The current Flash plugin for Firefox is always available in the Ubuntu repositories.  It can be installed just as any other package is installed.

One important consequence of installing Flash from Adobe's tar archive is that you become responsible for installing the frequent updates that Adobe releases.  When Flash is installed from the repos, then it is updated when necessary during routine system updates.

The Flash plugin itself, I believe, has no dependencies.  Installing other software from tar archives will, most likely, however, leave you identifying and chasing down dependencies needed before it works. The entire structure of package managers, repositories, and dependency resolution was created years ago to remove that requirement from users.   it's something that does not exist in Windows.

---

### Post by grahammechanical on 2016-03-24
> why would they be locked in the first place?

That depends on the instructions in the readme file. To install anything we need to be an administrator or as it is called in Linux "root."

If we install from the command line we prefix the command with "sudo" and then enter our password. We have now instructed apt-get to act as root. So, it is not surprising that apt-get creates files owned by root.

If we instruct the software centre to install something we are instructing it to act as root. There are some kinds of software the software centre will not install unless we authenticate the action. Again we are giving power to software centre to act as root.

Those two files are not in any of the / folders. It is my guess that the install process that you used failed to remove those two files while it was still working as root.

Regards

---

### Post by Eric_Knudson on 2016-03-24
You are awesome! Thank you maam.Another question for you since you are a mod and probably know more than you'd like to admit. I purchased a book from amazon called Linux Ultimate guide for beginners... and it's horrible. Not for beginners and really doesn't teach anything useful. Do you have any recommended reading material to get me started? Thank you :)

---

### Post by Eric_Knudson on 2016-03-24
Thank you for the advice. Really it was just me practicing with the gnome terminal more than anything :)

---

