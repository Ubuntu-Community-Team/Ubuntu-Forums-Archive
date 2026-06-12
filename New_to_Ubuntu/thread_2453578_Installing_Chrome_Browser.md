---
title: "Installing Chrome Browser"
date: 2020-11-13
forum: New to Ubuntu
---

### Post by gmseed on 2020-11-13
I'm trying to install Chrome on Ubuntu Desktop 20.04LTS.

1) Go to:
[https://www.google.co.uk/chrome/thank-you.html?installdataindex=empty&statcb=0&defaultbrowser=0&brand=MRUS](https://www.google.co.uk/chrome/thank-you.html?installdataindex=empty&statcb=0&defaultbrowser=0&brand=MRUS)
2) Click "Download Chrome"
3) Select the 64bit Debian/Ubuntu package and click "Accept and Install"
4) Open with the default software installer
5) And guess what - it doesn't work and reports back the error message "Failed to install file: not supported"
6) This is amusing because during installation it states that chromium is supported, or would that be different to chrome? 

I've just installed a new version of Ubuntu and already encountered 3 issues in the first 3 tasks I've done.

This is why I hate Linux and Ubuntu. It's so amateurish and always ends in having to seek help for the simplest of tasks.

***
Chromium

So even though Google Chrome suggests a .deb package for Ubuntu 20.04LTS, the installation appears to fail.

Using the "Ubuntu Software" toolbar app I searched for Chroumium and installed that, which appears to have worked.

---

### Post by ActionParsnip on 2020-11-13
Never had a single issue installing Chrome.....ever.
```

wget -O ~/Downloads/chrome.deb https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i ~/Downloads/chrome.deb
sudo apt-get -f install
rm ~/Downloads/chrome.deb

```

4 commands, dead easy

---

### Post by T6&amp;sfpER35% on 2020-11-13
> [COLOR=#000000]This is why I hate Linux and Ubuntu.[/COLOR]

go away 


](*,)

---

### Post by grahammechanical on 2020-11-13
@3nd

+1

I installed Google Chrome using the method suggested by ActionParsnip. It never fails. I actually do not use Chrome as a web browser. I make use of its ARCWelder extension to run an Android app that is not available as a Linux app.

Regards.

---

### Post by QIII on 2020-11-13
And yet ... millions of people have installed Chrome without the slightest hint of an issue.

---

### Post by gmseed on 2020-11-13
dito

---

### Post by gmseed on 2020-11-13
Funny how installing Chrome on 17.04 and 20.04 doesn't work for me, but Chromium does.

---

### Post by T6&amp;sfpER35% on 2020-11-13
```
sudo apt-get update -y
```
```
sudo apt upgrade
```
and try your procedure again

---

### Post by CelticWarrior on 2020-11-13
Post back any error message that might come up when running the above commands.

---

### Post by daniewicz on 2020-11-13
[QUOTE=.[COLOR=#000000]This is why I hate Linux and Ubuntu.[/COLOR][/QUOTE]

Very robust way to ensure a negative response on a Ubuntu linux forum. Best to show more maturity next time.

---

### Post by wildmanne39 on 2020-11-13
The OP has left the building so thread has been closed to prevent our volunteers from wasting anymore time on this issue.

Thanks everyone!

---

