---
title: "Have 2 versions of Libreoffice installed - Can oldest be uninstalled"
date: 2017-08-19
forum: New to Ubuntu
---

### Post by sprinterdriver on 2017-08-19
Hi.

I have installed a newer version of Libre Office, but the version of LibO that was pre-installed with Xubuntu is not uninstalled, so I have two versions simoultanesly by now.

The question is - can the oldest version (the one that was pre-installed with Xubuntu) be uninstalled - without the new version being affected?

---

### Post by vocx on 2017-08-19
> **sprinterdriver said:**
> Hi.

I have installed a newer version of Libre Office, but the version of LibO that was pre-installed with Xubuntu is not uninstalled, so I have two versions simoultanesly by now.

The question is - can the oldest version (the one that was pre-installed with Xubuntu) be uninstalled - without the new version being affected?
Most probably yes. The question is, how did you install the newer version?

The old version is the one that came in the repositories so it can be removed or purged with "apt".
```

sudo apt remove libreoffice

```

LibreOffice is composed of many parts, and individual packages, for example Writer, Impress, Calc, Math, etc. So you can install them and remove them individually. There are also some "common" packages of LibreOffice which provide functionality to the the other packages. You could remove these as well. But there's a caveat, if the newer version you got needs some of these "common" packages, then you should not remove them.

However, if this newer version that you installed is completely "self contained", that is, it does not require other dependencies, then you can just remove all other packages of LibreOffice that came with your Xubuntu installation. So again, to know if it's possible to remove all traces of the old LibreOffice you need to indicate how you installed the newer version, and what parts of LibreOffice you use or not.

---

### Post by sprinterdriver on 2017-08-21
Thank you.

To be honest I don't remember excactly how I installed the new version, probably by downloading a .deb file.

Maybe I just uninstall both and then install the newest one avaiable.

---

### Post by deadflowr on 2017-08-21
You should only ever have one deb packaged version installed.
If you have two libreoffices installed , then you more likely installed the snap package through the software store.
To find out simply open a terminal and run
```
snap list
```
does libreoffice  show?

> To be honest I don't remember excactly how I installed the new version, probably by downloading a .deb file.

Installing LibreOffice (from the document foundation) takes more than simply installing a deb file. You actually need to run a few simple commands to install several dozen deb files.

---

### Post by sprinterdriver on 2017-08-31
Thanks.

I have managed to remove the oldest version of LibO, the one that was installed from the beginning. I simply opened Gnome Software, and clicked the "Installed" button.

Then I removed LibO in this succession:
* Found the item named "libreoffice". It was two items with the same name, so I found the one that is NOT version 5.3.4.2, and removet it.
* For all remaining LibO tools (Calc, Writer, Math) I made sure they had a version number different than 5.3.4.2, and then I removed them.

So far, running the remaining LibO version seems to work just fine ;)

I did not run the command before I removed the old LibO version (I was supposed to just post an update, unaware of the reply).
Anyway - after removing the oldest LibO, the command yelds
```
sprinterdriver@dell-laptop:~$ snap list
Name         Version     Rev   Developer  Notes
core         16-2.26.14  2462  canonical  -
libreoffice  5.3.4.2     21    canonical  -

```

---

