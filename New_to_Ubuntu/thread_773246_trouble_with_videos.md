---
title: "trouble with videos"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Ketson on 2008-04-28
seem to be having a bit of an issue with watching videos and i belive flash too.

it is always appearing with large play symbols on the selections which have to be selected before being allowed to view what the are.

---

### Post by arseniy on 2008-04-28
lol Hitler gets banned from XBOX Live...

For youtube, you need to install flash. Fortunately, Macromedia has a Flash plugin for Ubuntu. Installing the [FONT="Courier New"]flashplugin-nonfree[/FONT] package actually downloads and installs the Linux Flash player from their website (adobe). After installing, you need to run the [FONT="Courier New"]update-flashplugin[/FONT] command to configure the browser.

```
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
```

**Make sure the multiverse repositories are enabled.

Unfortunately, the [FONT="Courier New"]flashplugin-nonfree[/FONT] package is only available for PCs. As an alternative, the [FONT="Courier New"]swf-player[/FONT] package provides basic SWF (Flash file) support in Ubuntu.

```
sudo apt-get install swf-player
```

A limitation is that newer Flash animations may not play using [FONT="Courier New"]swf-player[/FONT].

---

