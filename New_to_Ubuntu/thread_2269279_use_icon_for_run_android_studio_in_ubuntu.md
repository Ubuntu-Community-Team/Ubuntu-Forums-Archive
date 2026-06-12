---
title: "use icon for run android studio in ubuntu"
date: 2015-03-14
forum: New to Ubuntu
---

### Post by programmer2 on 2015-03-14
when i want to run android studio i must go to terminal and then go to androidstudio/bin then type ./studio.sh . how can i use a icon for run android studio in my desktop or luncher ?!

---

### Post by Holger_Gehrke on 2015-03-14
[Create a .desktop file]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") for it and put it in '~/.local/share/applications'. Then the Dash will find it and after starting the program you can right click on the icon in the launcher and choose 'Keep in Starter'.

---

### Post by yetimon_64 on 2015-03-14
> **Holger_Gehrke said:**
> [Create a .desktop file]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") for it and put it in '~/.local/share/applications'. Then the Dash will find it and after starting the program you can right click on the icon in the launcher and choose 'Keep in Starter'.
+1 to this OP.

Just make sure in the "Exec=" line you use the full (absolute) path to the studio.sh file eg /home/<yourusername>/androidstudio/bin/studio.sh.

If you want to use just the name in the "Exec=" line or launch from the terminal by just the name only the file has to be in the system path. To easily launch a file like studio.sh create a link to it in ~/bin (~ is your users home folder) and rename the link to "studio". If you need to create the ~/bin folder do a log out and log back into the desktop so it will be activated in the system path (important to logout/in if you don't already have the bin folder in home). Then the "Exec=" line or terminal will launch studio.sh by just using "studio" (or whatever you name the link in ~/bin). Cheers.

Edit: I should also note an easy way to link is to drag and drop the studio.sh file into ~/bin using the _*center mouse button*_, on dropping the file a menu will pop up, choose "Link Here" and then rename the link to whatever you want to launch it with in terminal or the Exec= line.

---

