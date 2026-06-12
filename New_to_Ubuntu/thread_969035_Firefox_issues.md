---
title: "Firefox issues"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by guy_ho on 2008-11-03
First post, so please ask me for more info about my set-up if I don't provide it.

I switched from Fedora Red Hat last week to Ubuntu 8.10, so I understand a few things about Linux. My computer has a Intel Q6600 Quad Core Processor.

Yesterday I was having issues getting Flash to work on Firefox 3.0.3, and followed instructions on just about any blog, forum and other kind of site in order to resolve the problem. At some point I uninstalled Firefox, and lost all my settings. In addition the back/forward buttons don't work (they're grey), sometimes the file, edit, view etc. menus don't work (also grey), I can't use buttons on websites (such as search), and the loading icon in tabs always looks as if it's loading. Basically, I'm posting from work as it's too frustrating to use the web at home.

Suggestions as to how to fix the problems would be greatly appreciated!

---

### Post by skymera on 2008-11-03
Install Flash like this

```
 sudo apt-get install flashplugin-nonfree 
```

---

### Post by tuxxy on 2008-11-03
**ubuntu-restricted-extras **is a great package for a new install will install java, flash, mp3/dvd codecs, fonts etc

---

### Post by guy_ho on 2008-11-03
Thanks for the fast responses, but Flash works just fine, ironically enough - it's just the rest of the browser that's giving me problems! The grey buttons, Foxmarks not stalling during installation etc.

---

### Post by OffAxis on 2008-11-03
Did you purge it? 

```
sudo apt-get purge firefox-3.0
```

and then you can try reinstalling.

```
sudo apt-get install firefox-3.0
```


Firefox 2 is still in the repos, you can install that alongside 3, or instead of it if it's still giving you problems.

```
sudo apt-get install firefox-2
```

---

### Post by kansasnoob on 2008-11-03
Assuming you have nothing saved in Firefox that you need to save go to Places > Home > View > Show Hidden Files. Then look for .mozilla. Right click .mozilla and move it to trash.

*Note: I know I said it already but that only applies if you have nothing to save, ie; bookmarks, Thunderbird mail, etc.*

Then go to terminal and run these commands:

```
sudo apt-get install --reinstall firefox
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get -f install
```

And finally:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Then restart Firefox by going to File > Quit. Then start Firefox again. You may have to restart the desktop but I doubt it.

---

### Post by guy_ho on 2008-11-04
Thanks again for the responses. In the end I did a full re-installation of Ubuntu, followed one of the suggestions to get the Flash plug-in working, and it's fine now. 

I've got an issue with screen resolution being too small, but I'm reading up on that and hope to sort it later.

---

### Post by Marvindreyer on 2008-11-04
I am new to this forum and I am quite sure that will stay here for a long time as plenty of knowledgeable people post here!

---

