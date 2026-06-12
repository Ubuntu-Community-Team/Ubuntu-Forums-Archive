---
title: "Where is Archive Manager?"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by Inisfad on 2012-04-14
I am now on Precise Pangolin, and have downloaded a script for 'force quit' which I want to install - a tar.gz file.  When I click on the download, I am being asked to choose an application to open/extract the file.  Where do I find Archive Manager (file roller) in the list of applications?  Thanks!

---

### Post by Curtis6767 on 2012-04-14
Open Dash

 type in Archive Manager

---

### Post by Shadius on 2012-04-14
Hi, 

Try opening Dash and typing in Archive Manager. It should come up. That's how I get to it in Ubuntu 11.10, but I don't know if that applies to Ubuntu 12.04. I'm fairly new to Ubuntu Linux, so if that doesn't work, I'm sorry!

---

### Post by Frogs Hair on 2012-04-14
If you right click om the file the option to open with Archive Manager should appear in the context menu . You just select the option .

---

### Post by Inisfad on 2012-04-14
Thanks for the replies - and that is exactly the problem - Archive Manager does show up in dash, but there are no 'properties' to indicate where it is located in the file system.  When I click on the downloaded file, Archive Manager is NOT showing up.  Instead it says 'choose application' and when I click on that, my file system loads up.  I do not know how to locate Archive Manager in order to choose it.  Can you tell me where it's located, so I can add it to the 'choose application' request?  Thanks.

---

### Post by Curtis6767 on 2012-04-14
file system/usr/share/applications

---

### Post by Shadius on 2012-04-14
Ohhhh, I think I understand what you're saying now. You need to browse for the Archive Manager in order to choose it as the application to open that downloaded file. Correct?

---

### Post by Inisfad on 2012-04-14
Yes, correct!!  And thanks, found it listed in usr/share/applications - was looking in local.  Will try it now and see if this works....

---

### Post by Inisfad on 2012-04-14
Um, no.  It doesn't. When you open usr/share/applications in the 'choose application' window of the download, Archive Manager doesn't show up (and there is only file-roller.desktop).  Eck.

---

### Post by oldos2er on 2012-04-14
If I remember correctly, it's /usr/bin/file-roller

---

### Post by Shadius on 2012-04-14
> **oldos2er said:**
> If I remember correctly, it's /usr/bin/file-roller

Yes, was just about to tell him that.

---

### Post by Inisfad on 2012-04-14
Bingo, thanks Oldos2er.  That's where it is - problem solved.  Thank you!!

---

### Post by Shadius on 2012-04-14
This thread might help you in the future....

[http://ubuntuforums.org/showthread.php?t=1191067]("http://ubuntuforums.org/showthread.php?t=1191067")

Example:
```
which file-roller
```


Output:
```
/usr/bin/file-roller
```

Hope that helps you.

---

### Post by Inisfad on 2012-04-14
Well, I have found Archive Manager, and have opened up and extracted my download (the script for ForceQuit), I found the icon and when I go to drag it to the launcher, nope, it won't stay there.  I have copied it on to my desktop and tried to drag it, but again, it won't stay in the launcher.  So although the first part of my adventure here has been solved, it has opened up a new problem.  Anyone have an answer??

---

### Post by Shadius on 2012-04-14
> **Inisfad said:**
> Well, I have found Archive Manager, and have opened up and extracted my download (the script for ForceQuit), I found the icon and when I go to drag it to the launcher, nope, it won't stay there.  I have copied it on to my desktop and tried to drag it, but again, it won't stay in the launcher.  So although the first part of my adventure here has been solved, it has opened up a new problem.  Anyone have an answer??

When Archive Manager was running, was it showing up in Launcher? If so, you can right click on it and select "Keep in launcher".

---

### Post by Inisfad on 2012-04-14
No, when Archive Manager was running, there was no icon - when I installed it, Nautilus (I think) opened and prompted me down the list to get the Force Quit icon.  I now have force quit on the desktop, but cannot drag it to the launcher, although I can do this with other programs.  I can live with it on the desktop, just thought perhaps someone knew of a reason why the launcher will not accept it.

---

### Post by Shadius on 2012-04-14
> **Inisfad said:**
> No, when Archive Manager was running, there was no icon - when I installed it, Nautilus (I think) opened and prompted me down the list to get the Force Quit icon.  I now have force quit on the desktop, but cannot drag it to the launcher, although I can do this with other programs.  I can live with it on the desktop, just thought perhaps someone knew of a reason why the launcher will not accept it.

Take a look here: 
[http://ubuntuforums.org/showthread.php?t=1750127]("http://ubuntuforums.org/showthread.php?t=1750127")

---

### Post by Inisfad on 2012-04-14
Thanks, already saw that and tried it - Nautilus crashed when I followed the instructions.  Anyway, I just restarted my computer, and lo and behold, suddenly force quit is on the launcher.  So, for some unknown reason, this post is truly solved!  Thanks for your help and suggestions.

---

