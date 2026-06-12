---
title: "Untrusted Application Launcher Ubuntu 18.04"
date: 2019-10-04
forum: New to Ubuntu
---

### Post by ephemeralCodex on 2019-10-04
Hey everyone, 
this is my first post on the forums so I apologize for any bad formatting. (I'll learn with time). 

I am running into the same issue as in a previous closed ticket. ([https://ubuntuforums.org/showthread.php?t=1179488&page=2](https://ubuntuforums.org/showthread.php?t=1179488&page=2))
I am running Ubuntu 18.04 with gnome with 3 desktop icons with the following properties. 

User = admin
Parent Folder /home/admin/Desktop
-rwxr-xr-x 1 admin users 252 Oct 4 16:34 atom.desktop
-rwxr-xr-x 1 admin users 642 May 30 2018 gnome-terminal.desktop
-rwxr-xr-x 1 admin users 322 Oct 4 15:46 Instructions.desktop
As you can see the files are set to executable and the owner is the currently logged in user as well. 
When I click on each of the icons I get the following message. 

"Unstrusted application launcher
The application launcher 'atom.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe."

I have also tried the following troubleshooting steps to get around this and each has been unsuccessful.
1) chmod +x *.desktop (repetitive, I know the files are already set to x)
2) gio set /path/to/your/launcher.desktop "metadata::trusted" yes (I verified the file was updated by running gio info atom.desktop with the correct entry) [https://stackoverflow.com/questions/51747456/is-it-possible-to-modify-gnome-desktop-file-metadata-from-non-gui-session-using](https://stackoverflow.com/questions/51747456/is-it-possible-to-modify-gnome-desktop-file-metadata-from-non-gui-session-using)
3) From the applications dropdown menu, atom opens perfectly fine. So I looked into /usr/share/applications and noticed the atom file has root ownership. I CP to the desktop and it became locked. I changed the perms
again same issue. 
4) I also looked into disabling both SELinux and App Armor and rebooting (for testing only). This did not work either.
5) Lastly, I tried looking into "Security Context" which is currently label to "unknown". I read that this is part of the SELinux app which ubuntu does not use. So that was a dead end. 


MY GOAL: I need a way to programatically bypass this warning label. I just want to respective applications to open. 
All my current research points to instances that are from Ubuntu 16 and below. 

If anyone has any insight it would be really appreciated. 
Many thanks, from a random Jr admin.

---

### Post by deadflowr on 2019-10-05
It's a function of the nautilus file manager.
Here's a somewhat related bug report
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1687179]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1687179")
I would guess the functionality could be reset by removing the patch(es).
That would,of course, require building nautilus yourself.

Maybe possible to switch to another file manager to handle the desktop, like nemo.
[https://www.linuxuprising.com/2018/07/how-to-replace-nautilus-with-nemo-file.html]("https://www.linuxuprising.com/2018/07/how-to-replace-nautilus-with-nemo-file.html")

---

### Post by ephemeralCodex on 2019-10-07
I'll give this a try. Updates soon

---

