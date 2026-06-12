---
title: "How to fix Broken Desktop"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by LoungeLizard on 2011-12-15
ok - I made a fatal mistake...  I wanted to install  a simple program that required TK and TCL 8.5-dev  - so I ran synaptic to install them - and it couldn't find the packages.  Being smarter than the average bear, I searched and found the .deb files and sudo apt-get them only to find a broken dependency in my libfontconfig1 which depended on fontconfig-config.  Apparently, the repository I was looking at didn't match what I wanted and synaptic burped a message that I had broken dependencies and should try apt-get update -f

So, I dutifully did just that and my entire system began a systematic removal of all my software to the point that nothing on the Ubuntu desktop works except the terminal window that's currently open.  I can't open another term window - it doesn't exist.  Nothing exists in my menus...  I killed it all...

Now what?  I tried 
  sudo apt-get update
and I get a list of repositories' folders from us.archive.ubuntu.com intrepid/whatever...
followed by a huge list of 404 Not Found errors with a final line containing a message 'Some index files failed to download, they have been ignored or the old ones used instead'

And nothing happens...

I have a number of distro disks - can I use one of those to repair my machine without a complete rebuild?  Dammit...  this really sucks...  all I wanted was to load a stupid graphic and totally hosed my file server!

please help!  I have a terminal window, most commands seem to work fine.  I can mount my DVD distros but I have no experience in recovering this kind of a calamity and have no clue what to do at this point...

-- tia

---

### Post by Sigma1 on 2011-12-15
Have you tried this:
```
dpkg --configure -a
```
From memory, I think that's the command which should get everything back up and running.

---

### Post by The Cog on 2011-12-15
Or maybe "sudo apt-get install ubuntu-desktop" which should re-install stuff that has been uninstalled, but to be honest I'm only guessing.

---

### Post by Sigma1 on 2011-12-15
Ah, I think I've understood. Intrepid is no longer maintained. You're best bet might be to use the original CD and do a ```
sudo apt-get install ubuntu-desktop
``` as suggested (provided the CD is given in /etc/apt/sources.list), or to try editing sources.list (changing intrepid to lucid... perhaps) and upgrading to Lucid, with ```
sudo apt-get dist-upgrade
``` I say "perhaps", because upgrades are supposed to run one step at a time, i.e. intrepid > jaunty > karmic > lucid, so the original CD is by far the safest option. Good luck.
P.S. Message me if you need help with the CD.

---

