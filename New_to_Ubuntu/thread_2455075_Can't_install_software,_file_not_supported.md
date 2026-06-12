---
title: "Can't install software, file not supported"
date: 2020-12-11
forum: New to Ubuntu
---

### Post by llmunro on 2020-12-11
Hi forum!

I'm on Ubuntu 20.04 after a long hiatus and I have some software that I'd like to install (specifically, ClickUp, Slack, and Chrome). I can download the .deb files for each, but when I try to install them with the Ubuntu Software manager, I get an error: "file not supported." I know I've been able to easily install these in the past. What am I missing?

Thank you!

Lisa

---

### Post by grahammechanical on 2020-12-11
I install Chrome web browser through the command line.

This to get the Chrome package

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```
This to install it

```
sudo apt install ./google-chrome-stable_current_amd64.deb
```

[https://linuxize.com/post/how-to-install-google-chrome-web-browser-on-ubuntu-20-04/](https://linuxize.com/post/how-to-install-google-chrome-web-browser-on-ubuntu-20-04/)

There is a snap packaged version of Slack (team communications) in the Ubuntu 20.04 software store.
Double clicking on the deb file should open the software store which will then install it. If double click the deb file opens the Archive manager then right click the deb file and choose Open With option. Or we can use the command line.

```
sudo apt install path_to_deb_file
```

Or

```
sudo dpkg -i path_to_deb_file
```

[https://itsfoss.com/install-deb-files-ubuntu/](https://itsfoss.com/install-deb-files-ubuntu/)

Regards

---

### Post by CelticWarrior on 2020-12-11
> [COLOR=#000000]I get an error: "file not supported." I know I've been able to easily install these in the past. What am I missing?[/COLOR]

You're trying to open the downloaded .deb files directly by the browser. This no longer works. You need to save the file then double-click it.

The reason is snap confinement/limitations: The GUI software, the "app store" which is as usual the default association with .deb files is itself a snap. Snaps can access users' folders and at best what's under /media or /mnt. When you tell the web browser to "open with <app>" instead of "save as" it first downloads the file to a temporary folder and this one is outside the allowed locations of the software you told it to open with so it can't and, in this case only, gives a very misleading error message.

---

