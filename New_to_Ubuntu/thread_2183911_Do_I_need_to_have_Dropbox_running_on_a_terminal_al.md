---
title: "Do I need to have Dropbox running on a terminal all the time?"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by zeynel2 on 2013-10-26
I have this running on a terminal
 
$ .dropbox-dist/dropboxd

If I close this terminal I don't see the Dropbox icon on the status bar. Is this how it should be? Anytime I want to use Dropbox I need to open a terminal and run the server?

---

### Post by warp99 on 2013-10-26
Just use a '&' after the command and it will split off the process. 
```
$ .dropbox-dist/dropboxd &
```
Why don't you just click the option "Start Dropox on system startup" in Preferences?

---

### Post by fantab on 2013-10-26
> **zeynel2 said:**
> I have this running on a terminal
 
$ .dropbox-dist/dropboxd

If I close this terminal I don't see the Dropbox icon on the status bar. Is this how it should be? Anytime I want to use Dropbox I need to open a terminal and run the server?

No need to use the terminal at all if Dropbox can start normally.
From DASH search for Dropbox, drag the Dropbox icon to the launcher. Selecting the dropbox icon in the launcher should start dropbox.
If you want or don't want dropbox to start with Ubuntu, then right click on the dropbox icon in the top-bar, select Preferences and uncheck/or check 'start dropbox on system startup'.

---

### Post by zeynel2 on 2013-10-27
> **warp99 said:**
> Just use a '&' after the command and it will split off the process. 
```
$ .dropbox-dist/dropboxd &
```

What does "split off the process" mean?

> **warp99 said:**
> 
Why don't you just click the option "Start Dropox on system startup" in Preferences?


I don't have this option in Dropbox preferences.

---

### Post by zeynel2 on 2013-10-27
> **fantab said:**
> No need to use the terminal at all if Dropbox can start normally.
From DASH search for Dropbox, drag the Dropbox icon to the launcher. Selecting the dropbox icon in the launcher should start dropbox.

When I search for Dropbox in DASH I only see the folder, I don't see the icon.

> **fantab said:**
> 
If you want or don't want dropbox to start with Ubuntu, then right click on the dropbox icon in the top-bar, select Preferences and uncheck/or check 'start dropbox on system startup'.

I don't have the option 'start dropbox on system startup' in preferences.

---

### Post by fantab on 2013-10-27
How did you install dropbox? From the dropbox website or from Ubuntu repository?

---

### Post by zeynel2 on 2013-10-27
I don't remember. Is there a way to find out?

---

### Post by stankopp on 2013-10-30
I am having trouble getting Dropbox to install in 13.10.  It goes through the setup just fine and then says must restart nautilus.  Clicking on the restart button does absolutely nothing.  Any ideas?

---

### Post by whatthefunk on 2013-10-30
> **stankopp said:**
> I am having trouble getting Dropbox to install in 13.10.  It goes through the setup just fine and then says must restart nautilus.  Clicking on the restart button does absolutely nothing.  Any ideas?

Did you close Nautilus and then open it again?

---

### Post by fantab on 2013-10-30
> **stankopp said:**
> I am having trouble getting Dropbox to install in 13.10.  It goes through the setup just fine and then says must restart nautilus.  Clicking on the restart button does absolutely nothing.  Any ideas?

Close dropbox. And:
```
dropbox start -i
```

---

### Post by zeynel2 on 2013-10-31
I reinstalled Dropbox from their site and the problem resolved.

---

### Post by stankopp on 2013-11-01
> **whatthefunk said:**
> Did you close Nautilus and then open it again?

What I am saying is that the button to restart Nautilus does absolutely nothing, i.e. does not restart Nautilus.

---

### Post by buzzingrobot on 2013-11-01
I'd guess that the OP installed Dropbox using the command line example at dropbox.com.   If so, Dropbox needs to be manually added to Startup Applications. The command is the same as shown in that first post.  Best to navigate to it via the Startup Apps GUI to ensure the full path is in there.

I always install the deb at dropbox.com because the repo version has been problematic across several Ubuntu releases.

Restarting Nautilus is necessary for it to display the Dropbox-specific indicators when that folder is displayed. The initial install can proceed without it.

---

### Post by fantab on 2013-11-01
> **buzzingrobot said:**
> 

I always install the deb at dropbox.com because the repo version has been problematic across several Ubuntu releases.



Not really. I have always used the repo version of dropbox... currently using it on "Trusty Thar" Development. No big issue.

Note: when you get to dialog where it asks you to "Restart Nautilus", just Close the dialog. Open Terminal and run:
```
 dropbox start -i
```

---

### Post by buzzingrobot on 2013-11-02
> **fantab said:**
> Not really. I have always used the repo version of dropbox... currently using it on "Trusty Thar" Development. No big issue.

Note: when you get to dialog where it asks you to "Restart Nautilus", just Close the dialog. Open Terminal and run:
```
 dropbox start -i
```

The repo version has often failed to install the Dropbox package, so typically things don't get that far.  Perhaps the issue has been addressed recently.

---

