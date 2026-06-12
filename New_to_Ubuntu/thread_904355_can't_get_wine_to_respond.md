---
title: "can't get wine to respond"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-08-29
I installed wine 1.0.0 with the synaptic package manager. Then I ran winecfg to configure wine. Every thing looks OK, but when I click on the Wine "Browse C: Drive" icon nothing happens. The virtual drive C: does not open. If I run the terminal command from the "Browse C: Drive" icon in a terminal, I get the following result:

$  sudo xdg-open ~/.wine/drive_c

Warning: unknown mime-type for "/root/.wine/drive_c" -- using "application/*"
Error: no "view" mailcap rules found for type "application/*"

Does anyone have any idea how I can get Wine to work properly?

JBA2337

---

### Post by quibbler on 2008-08-29
I think you have to first install a windowns progran and the drive_c will be made.
It is a folder under the folder .wine in your home directory.
You installed wine in order to run a windows program...then run the setup file with wine and see how it goes.

Regards quibbler

---

### Post by Thelasko on 2008-08-29
> **JBA2337 said:**
> 
$  sudo xdg-open ~/.wine/drive_c

Warning: unknown mime-type for "/root/.wine/drive_c" -- using "application/*"
Error: no "view" mailcap rules found for type "application/*"

Does anyone have any idea how I can get Wine to work properly?

JBA2337
First of all, don't use sudo for looking in your .wine folder.
```
xdg-open ~/.wine/drive_c
```
is what you wanted.  The .wine folder is a actually a hidden folder in your /home directory.  Therefore you don't need root privileges to view and edit those files.  You can see them by pressing ctrl+h in nautilus.  

By using sudo you were technically logged in as root, so you were trying to view the .wine folder in the /root folder (which is the /home directory for the root user) instead of in the /home folder.  Make sense?

---

### Post by JBA2337 on 2008-08-29
To: quibbler and Thelasko

Thank you very much. My problem with getting Wine to run properly is now solved!

In the launcher icon for "Browse Wine Drive C", I changed the launcher command from "sudo xdg-open ~/.wine/drive_c"   to
"xdg-open ~/.wine/drive_c". Now it works perfectly. When I click on this icon it opens up /home/jim/.wine/drive_c.

Apparently, when wine is installed from the synaptic package manager, it automatically inserts the command "sudo xdg-open ~/.wine/drive_c ", which is wrong.

I am now able to run the Act! contact manager program (which is designed for Windows) in Wine, which is running in Ubuntu.

The only way that I can start the Act! program is to go to  
/home/jim/.wine/drive_c/Program Files/ACT and click on the Act.exe file.
I made a link to the Act.exe file, and the link starts the Act! program as long as the link is in the /home/jim/.wine/drive_c/Program Files/ACT
folder. But if I copy the link to anywhere else, it does not work. 

How can I make a link to the Act.exe file that will work, even if I place it somewhere other than in /home/jim/.wine/drive_c/Program Files/ACT   ???

JBA2337     :)

---

