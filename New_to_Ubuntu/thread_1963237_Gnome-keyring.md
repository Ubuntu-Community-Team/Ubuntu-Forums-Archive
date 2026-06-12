---
title: "Gnome-keyring"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by skra on 2012-04-22
Hi, Im new to linux and new to this forum, so I hope I have found the right place. So I have the problem that I ve got ubuntu running on my laptop-dell m6400 in 64bit - ive had it running fine for the last 3 months, however yesterday i uninstalled something called a keyring or gnome keyring...not sure of the exact name... and i cant start the OS any more...there is just a purple screen arter logging in with my password. Is it possible to recover the installation? Any help would be greatly appreciated.....

---

### Post by mcduck on 2012-04-22
Are you sure uninstalling the keyring didn't take any other packages with it? It's a part of the Gnome desktop and most likely many other packages depend on it...

Logging in a TTY or recovery mode and reinstalling the *ubuntu-desktop* package should solve the problem.

---

### Post by skra on 2012-04-22
Thank you for the suggestion, could you explain to a novice ubuntu user how to reinstall the desktop-package.... i do see how to get to the terminal window.... with thanks..

found one suggestion... 
sudo apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}' | \ sed '/^$/d' | xargs sudo apt-get \ install --reinstall --install-recommends --yes

would this be ok to try?

---

### Post by skra on 2012-04-22
Ok - so to answer myself..... I used sudo apt-get install --reinstall ubuntu-desktop   and that got me back into the ubuntu i had setup .. but with some changes made to the buttons on the left of the floating bar.    Some thoughts then.... WHY is it possible to disable the entire system by uninstalling a packag/app ... surely for someone like me its very important like in windows to HIDE important system apps/folders.... seems to me like it needs to be changed....

---

### Post by robbie 348 on 2012-04-22
Just curious, why did you want to uninstall the keyring anyway?

---

### Post by skra on 2012-04-22
In response... i wanted to uninstall the keyring app because every time the update program would start it wouldnt allow me to update because the aratereao was not authenticated ... so i guessed that aratereao was not a recognised ubuntu program source ... hence i uninstalled all the aratereau programs and update was working fine, until i restarted... I guess Im not cut out for this Ubuntu stuff.... Windows seems to be more user friendly....

---

### Post by mcduck on 2012-04-22
> **skra said:**
> Ok - so to answer myself..... I used sudo apt-get install --reinstall ubuntu-desktop   and that got me back into the ubuntu i had setup .. but with some changes made to the buttons on the left of the floating bar.    Some thoughts then.... WHY is it possible to disable the entire system by uninstalling a packag/app ... surely for someone like me its very important like in windows to HIDE important system apps/folders.... seems to me like it needs to be changed....

Well, unlike many people might say, Ubuntu is not intended only for beginners but instead to be usable by *everybody*, which would include advanced users, companies, organizations and so on. So the user should have all the power and control over the computer he wants (which is pretty much the Linux ideology, giving people all the rope they want, even enough to hang themselves with it). And it's generally considered that the user is responsible of what they do with their computer, and therefore the users are also expected to either know what they are doing or do a bit of research.

Anyway, you didn't "disable the entire system", only a single part of it. A part which many users might actually want to disable on purpose. And anyway,  *every* operating system allows users with admin rights to break it, the control over the system that makes computers configurable for many different purposes also meaks them breakable, you can't have one but not the other.

If you want to feel safer around the OS, use a non-admin account for your daily use. However I'd simply recommend not running commands or making configurations if you aren't sure what they actually do (which is a good idea with pretty much every operating system and program anyway ;)). And you can always ask here before doing something if you want to make sure it's not going to cause problems.

---

