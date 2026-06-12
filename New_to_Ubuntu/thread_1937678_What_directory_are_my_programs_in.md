---
title: "What directory are my programs in?"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by ubunt10 on 2012-03-08
Hello:
I installed Google Chrome. I am trying to make a shortcut to Google Chrome on my desktop in Ubuntu 11.10. Where is Chrome? I clicked on "Dash Home" to do a search and entered "chrome" (without quotes) but it just directly opened Chrome when I did that. 

I also installed WINE but I don't know where it is.

---

### Post by Lalaith on 2012-03-08
When you see the chrome icon on the dash (write chrome but don't press enter), did you try to drag it and drop it on the unity bar? I think this is the way you create a shortcut on ubuntu 11.10 if you use Unity (the left bar).

---

### Post by EzioAuditore on 2012-03-08
In ubuntu 10.10, chrome is at /opt/google/chrome

There's also a command which you can use to find the location of any program, type in terminal whereis <program name>.

For eg. ```
whereis firefox
``` gives output as:

```
firefox: /usr/bin/firefox /etc/firefox
```

---

### Post by ubunt10 on 2012-03-08
Lailaith:

I clicked the "Dash home" button and then I typed "chrome". It did display the Chrome icon. When I clicked and dragged it to the Unity bar, it did not stay there. However, it does show up in the actual Dash icons rather than the Unity bar icons. I am definitely curious to know why it would not stay in the Unity bar when I clicked and dragged to the Unity bar. And even when I figure that out, I am still more interested in how I can get a normal desktop icon like in Windows XP. The Unity bar is simply not big enough to store all the shortcuts I want. 

EzioAuditore:

That command worked when I typed "whereis wine" and it showed the path. For "whereis chrome" it did not. Instead of displaying "chrome:  PATHHERE" it just displayed "chrome: " with no path afterward. Of course, it is good to know this command. 

I was able to find a directory like the one you mentioned. The directory is
> /opt/google/chrome/

But as a native Windows user, it is still unclear which file in that directory is actually Chrome. The only files in the folder that had the Chrome logo for an icon were actually called "chrome_logo" or something similar. I have no idea which icon to click and drag to the desktop.

---

### Post by Paqman on 2012-03-08
On Linux you don't actually need to specify the whole path to the executable like you do on Windows. The command to launch an application is just the name of that appliction.

For example, Firefox might be in /usr/bin/firefox, but you can launch it simply with:
```
firefox
```
Linux is smart enough to know where the files are.

Creating desktop launchers is not straightforward on Unity, but [it does seem to be possible]("http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html").

> **ubunt10 said:**
> 
I also installed WINE but I don't know where it is.

Wine is a compatibility layer, not an application as such. Once you've got Wine installed you should find you can click on any Windows .exe and opt to "open with Wine". You can also set that to be the default behaviour if it isn't already.

---

### Post by oldos2er on 2012-03-08
> **ubunt10 said:**
> 
I was able to find a directory like the one you mentioned. The directory is


But as a native Windows user, it is still unclear which file in that directory is actually Chrome. The only files in the folder that had the Chrome logo for an icon were actually called "chrome_logo" or something similar. I have no idea which icon to click and drag to the desktop.

The executable is named google-chrome, so try **whereis google-chrome**

---

### Post by Lalaith on 2012-03-09
> **oldos2er said:**
> The executable is named google-chrome, so try **whereis google-chrome**

This is why I never managed to execute chromium from the cli, I guess... it's google-chromium, as well.

ubunt10, what you say of your icons not staying in the unity bar didn't happen to me O_o. Could it be that because you don't have space on the bar, the shortcut is situated "under" the icons that are displayed on the unity bar? you can check it if you hover the mouse over the bar and go down without clicking. you should see new icons appearing. I hope I made myself understandable =)
and I don't know nothing about shortcurts on the desktop, sorry.

---

### Post by forrestcupp on 2012-03-09
If you install **gnome-tweak-tool**, run it, and go to "Desktop", you can set it to "Have file manager handle the desktop". After doing that, you can make shortcuts of binaries or scripts in Nautilus, and just drag them to the desktop, and you'll have your shortcut icons on the desktop.

---

### Post by ubunt10 on 2012-03-09
Just to follow up:  I found Chrome in /usr/bin/google-chrome and made a shortcut to the desktop. I learned that WINE is not a program. I opened Firefox with Terminal just by entering Firefox. I pretty much used every suggestion in this thread and all went well.

---

### Post by grahammechanical on 2012-03-09
You should also find utilities for wine in the Dash.

They should be Configure wine, Uninstall Wine Programs (which, by the way is used to install a Windows Program under wine), and Browse C: Drive. This last one gives a Windows Explorer type file browser that lets you explore the fake C: Drive that wine created. 

Another way to install a Windows program with wine is to right click it and select open with wine or something like that. I cannot say for sure as I am not using at the moment my Ubuntu that has wine installed.

Regards.

---

