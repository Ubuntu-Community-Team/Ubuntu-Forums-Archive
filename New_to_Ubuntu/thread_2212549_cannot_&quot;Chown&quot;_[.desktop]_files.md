---
title: "cannot &quot;Chown&quot; [.desktop] files"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by Sean_Daniel on 2014-03-21
In an attempt to work around the ridiculously non-useful Unity desktop. I figured on creating a few quicklinks on the desktop for easier access to some of the programs I use, (especially those that are in wine). I cannot change the names or icons of any of them. (because they are root owned) I'm attempting to use chown but not completely sure if it's my usage or the wrong way to fix the problem altogether. 

root@Miibuntu:/home/nef/Desktop# chown root:nef pcsx.desktop
root@Miibuntu:/home/nef/Desktop# chown nef:root pcsx.desktop
root@Miibuntu:/home/nef/Desktop# chown root:nef /home/nef/Desktop/pcsx.desktop
root@Miibuntu:/home/nef/Desktop# chown nef:nef /home/nef/Desktop/pcsx.desktop
root@Miibuntu:/home/nef/Desktop# chown nef:nef pcsx.desktop

None of these seem to do anything whatsoever! I'm not really certain of the exact usage, so I tried many. To no avail!

---

### Post by varunendra on 2014-03-21
Welcome to the forums Sean_Daniel!

If the commands returned no errors, it means the command was accepted and did what it was expected to do.

By the way, why are you using a windows version of PCSX at all (judging by you mentioning "wine")?? Not only PCSX is available in default repositories of Ubuntu, it also provides a ready-to-use ".desktop" file that you can use.

---

### Post by deadflowr on 2014-03-21
root shouldn't own any .desktop files for wine.
wine files should be owned locally, by the user.

Are you trying to run the system as root?

also +1 to the pcsx in the Ubuntu software center.

---

### Post by Sean_Daniel on 2014-03-22
For some reason, though I'm not certain why, the chown is accepting the syntax. However, the files themselves are still coiming up as root owned in the GUI properties window. I made the links with a middle click drag if that helps explain the root ownership in the first place.

Thumbs up to the Linux version of pcsx
Is there a way to create links that aren't root in the first place? or a reason the files are staying root owned even after chown?

---

### Post by Impavidus on 2014-03-22
You created symbolic links from your directory to a system directory. chmod silently ignores symbolic links, as symlinks always use the permissions and owner of their target. Therefore the symlink stays root-owned. If you want to change the files, don't use symlinks but copy the files to your own directory and then change them.

---

