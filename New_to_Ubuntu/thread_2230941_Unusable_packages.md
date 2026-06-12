---
title: "Unusable packages"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by gordon99 on 2014-06-22
I have tried to install Wine but met a problem. I think the  message below relates to Wine but am not 100% sure. Nevertheless i need to do something about removing the unusable packages and I would be obliged if someone could tell me how I should go about removing and re-installing them. I do not think I have an internet connection problem however.

"Data files for some packages could not be downloaded

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem".

---

### Post by Impavidus on 2014-06-22
ttf-mscorefonts-installer is a package that downloads some Microsoft fonts for you. Wine needs those font, or better, programs you run with wine expect those fonts to be there. Because of license issues this all works quite indirectly. When installing the ttf-mscorefonts you have to agree with some user license. There should be a pop-up or a menu in the terminal if you installed from the terminal. If in the terminal, use tab to select OK and hit enter. If using the GUI, click OK. It sometimes happens that the pop-up window stays hidden behind the software centre window, so you have to minimise that first. Without agreeing, the MS fonts won't install.

It's also possible that you can't reach the server to download the fonts from. If you don't have network problems, the problem is on the side of of the server. The update manager should ask you to try again later. Or try to configuere the package again.

---

### Post by ajgreeny on 2014-06-22
Install ubuntu-restricted-extras apckage and the mscorefonts will normally be installed as a dependency (actually a recommended package, not a dependency) of that.

---

### Post by Vladlenin5000 on 2014-06-22
There is *apparently* a recent bug that prevents the correct installation of that package because the aforementioned license accepting dialog DOESN'T appear, thus leaving the installation incomplete and broken. This is happening in 14.04 only, AFAIK.

Solution: Purge and reinstall.

```
sudo apt-get purge ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer
```

This second time the license pops-up. Use <TAB> to move the cursor to OK in that Windows and in the next dialog use also the arrow keys in order to select "Yes" (you must agree with the EULA). Then everything that needs to be done will happen quickly and you'll no longer see that error.

Obs.: TT fonts are required for WINE and the Windows software you might want to try/install but also for better font matching in documents made in Microsoft Office that use such fonts. It isn't required in a strict sense - your office apps, LibreOffice or other, will select the closest match whenever it doesn't find the exact font - but you better have them if you intend to work in professional documents.

---

