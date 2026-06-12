---
title: "Subversion File Browser Integration?"
date: 2007-05-04
forum: Programming Talk
---

### Post by Xangis on 2007-05-04
I've recently switched from WinXP to Ubuntu as my main OS.  Since I'd already been using open source almost exclusively, there's not much I'm missing, but there's one thing I'm missing that's driving me crazy:

I use subversion extensively, not just for code backups but as a file backup system (documents, etc.)   I'm thorougly addiced to the convenience of being able to right click on a file or folder to add to svn, update folders, commit changes, etc.  So far I've been unable to find anything to integrate subversion into the file browser GUI.  Is this possible?  What are my options?

---

### Post by cwaldbieser on 2007-05-05
> **Xangis said:**
> I've recently switched from WinXP to Ubuntu as my main OS.  Since I'd already been using open source almost exclusively, there's not much I'm missing, but there's one thing I'm missing that's driving me crazy:

I use subversion extensively, not just for code backups but as a file backup system (documents, etc.)   I'm thorougly addiced to the convenience of being able to right click on a file or folder to add to svn, update folders, commit changes, etc.  So far I've been unable to find anything to integrate subversion into the file browser GUI.  Is this possible?  What are my options?

Kubuntu has the kdesvn and kdesvn-kio-plugins packages that do this.  For the gnome desktop, I know there is some ability to add your own scripts to the context menus.  It probably would not be too difficult to add the functionality you want by creating such scripts that call the command line svn client.

---

