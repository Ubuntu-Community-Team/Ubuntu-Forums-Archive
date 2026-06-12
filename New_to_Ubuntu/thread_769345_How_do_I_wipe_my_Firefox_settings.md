---
title: "How do I wipe my Firefox settings?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by belovedmonster on 2008-04-26
I've managed to screw up Firefox 3 and I'd like to restore it to its default state but I dont know how to do this. Being a noob I tried to uninstall Firefox with a "complete removal" but that didnt seem to do it, as soon as I installed it again I had all the same settings as before. Is there some folder somewhere I can just delete to get back to the defaults for everything?

---

### Post by hackle577 on 2008-04-26
Run this in terminal:

```
rm -r ~/.mozilla/firefox/*.default
```

---

### Post by tamoneya on 2008-04-26
```
rm -rf ~/.mozilla/firefox
```That will delete all personal settings for firefox.

---

### Post by Joeb454 on 2008-04-26
If you don't mind losing bookmarks then simply ```
rm -rf ~/.mozilla
``` will do the trick.

Though don't run that if you use Thunderbird as well ;)

---

### Post by belovedmonster on 2008-04-26
None of these are having the desired effect. I've still got bookmarks, saved tabs, and the problem I cant fix. :(

Im running Xubuntu 8.04 if it helps.

---

### Post by tamoneya on 2008-04-26
thunderbird has its own directory so that would erase your settings.
What happened when you run```
sudo apt-get remove --purge firefox
```

---

### Post by belovedmonster on 2008-04-26
```
root@james-desktop:/home/james#  sudo apt-get remove --purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  firefox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 123kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 95146 files and directories currently installed.)
Removing firefox ...

```

Started it up again and its the same as ever.

---

### Post by scorp123 on 2008-04-26
> **belovedmonster said:**
> ```
[COLOR="Red"]root[/COLOR]@james-desktop:/home/james[COLOR="Red"]#[/COLOR]  sudo apt-get remove --purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  firefox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 123kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 95146 files and directories currently installed.)
Removing firefox ...

```

Started it up again and its the same as ever. Under which user account are you starting Firefox??  That shell prompt above tells me you logged into the "root" account? So whose Firefox settings are you trying to wipe? Root's? You should never ever start a web browser as "root" to begin with! Or are you trying to wipe your normal user account's Firefox settings? The fact that you did execute those commands and that yet the settings seem to remain suggests that you have not wiped the correct user's settings.

---

### Post by scorp123 on 2008-04-26
> **tamoneya said:**
> What happened when you run```
sudo apt-get remove --purge firefox
``` That will purge the system-wide settings in /etc and other places (e.g. system-wide plugin configs, etc.) but it has no influence on the settings in every user's $HOME ...

---

### Post by belovedmonster on 2008-04-26
I am wanting to remove the settings for my user account. When I start a new user account it has a virgin firefox which works great. I want to get back to that virgin state.

What happened was...

I just installed the latest version of Xubuntu 8.04 which comes with Firefox Beta 5. Everytime I was downloading a file it was asking me to set which software to use, I assumed this meant for the individual file type so I set it to Xubuntu's zip software as I had downloaded a zip file.

I obviously didn't read carefully enough as now every download is opening with the file zipping software. Even clicking on "Open Containing Folder" opens up the Zip software. I dunno how to fix this.

I thought it might be under preferences, but going into the Application section lists no software for me to change. But either way, the fact that open the containing folder opens up the zip software to me suggests its a different sort of setting.

Creating a new user account with a fresh firefox asks me that same question again each time I download a file, and once I select Thunar as the app the downloads then open as they should. I need to be able to reset Firefox so I can get this fixed.

---

### Post by belovedmonster on 2008-04-26
Problem solved. I deleted the mimeTypes.rdf file as discussed here:

[http://forums.mozillazine.org/viewtopic.php?p=3352489#3352489](http://forums.mozillazine.org/viewtopic.php?p=3352489#3352489)

---

