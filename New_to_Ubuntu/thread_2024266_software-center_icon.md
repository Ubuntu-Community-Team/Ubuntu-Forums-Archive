---
title: "software-center icon"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by westcoast01 on 2012-07-13
[FONT=Arial][SIZE=3]I was in main menu and sneezed, saw something get deleted, today I do not have an icon on the unity bar for my software-center. I can access the software-center via downloads in dash and I have reinstalled all the software-center items via Synaptic package manager, also in terminal I uninstalled, purged, and installed but still do not have an icon or listing in dash applications. I do not know the "command" in main menu so I have not tried that. Any help getting a software-center icon for Ubuntu 12.04 X64 would be greatly appreciated. Thanks.[/SIZE][/FONT]

---

### Post by MG&amp;TL on 2012-07-13
The command is just "software-center". Hope that helps. :)

---

### Post by westcoast01 on 2012-07-13
OK that gave me the funny little spring loaded icon that I dragged and dropped to the unity bar so at least I can access software-center but it would be really cool to have the original icon back. Any ideas? And thank you MG&TL for the command.

---

### Post by MG&amp;TL on 2012-07-13
> **westcoast01 said:**
> OK that gave me the funny little spring loaded icon that I dragged and dropped to the unity bar so at least I can access software-center but it would be really cool to have the original icon back. Any ideas? And thank you MG&TL for the command.

Not a problem. :)

The icon I have for my launcher is located in /usr/share/icons/hicolor/48x48/apps/softwarecenter.svg

(You can change the icon by clicking on it in the properties dialog.)

---

### Post by Frogs Hair on 2012-07-13
Below is a shot of the main menu and the bottom item is the software center. Make sure check box is selected. Selecting the Line where the software center is listed will open properties also displayed. By selecting the icon image on the left you can navigate to the folder of the icon set in use and open the path to the launcher icon. You may have log out and back in. 

If the main menu entry was deleted select + New Item and add the information in the code tags. ```
Type: Application

Name: Ubuntu Software Center 

Command: /usr/bin/software-center %u

Comment:Lets you choose from thousands of applications available for Ubuntu
```

---

### Post by westcoast01 on 2012-07-14
[SIZE=3][FONT=Arial]Hurray!!! Thanks to MG&TL and Frogs Hair I got the icon back on the unity bar. I do not have root privileges (still learning that one) so that did not work but what did work was ... placing software-center back onto Main Menu, (both commands seem to work), L clicking home folder ... R clicking File System, select open ... R clicking USR, select open ... R clicking Share, select open ... R clicking Application, select open ... R clicking Ubuntu Software-Center, select open ... move cursor to the right to show unity bar ... R click Ubuntu Software-Center icon and lock to launcher. So easy with the help of the great folks here on the forums. Thanks again, West.
[/FONT][/SIZE][ATTACH]221229[/ATTACH]

---

