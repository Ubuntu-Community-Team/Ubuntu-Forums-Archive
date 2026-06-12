---
title: "pipe man output to some decent word processor"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Frederick J. Harris on 2008-08-04
I find man pages to be very useful.  Up to now I laboriously copy 25 line chunks to gedit, paste there, return to terminal, copy 25 more lines, etc.  There has got to be a better way.  I like to print stuff out and save what I find useful.  I tried this but it didn't work...

man iwconfig | gedit

gedit opens but the output didn't go there.  How should I do this?

---

### Post by jimv on 2008-08-04
Try:

man iwconfig > somefile.txt

Then open the text file.

---

### Post by sisco311 on 2008-08-04
```
man *man *> manual-page && gedit manual-page && rm manual-page
```

EDIT:
you can create a script:
> #!/bin/bash
man $1 > /tmp/manpage
gedit /tmp/manpage
rm /tmp/manpage
save the file as *gman*, make it executable,
and copy it ti the /usr/bin directory.

---

### Post by coffeecat on 2008-08-04
Install Konqueror, and type 'man:iwconfig' (no quotes and note the use of a colon) in the address bar. Looks good, doesn't it? Properly formatted with good use of fonts so that you can actually read it. Now print out from konqueror.

---

### Post by sisco311 on 2008-08-04
> **coffeecat said:**
> Install Konqueror, and type 'man:iwconfig' (no quotes and note the use of a colon) in the address bar. Looks good, doesn't it? Properly formatted with good use of fonts so that you can actually read it. Now print out from konqueror.

if you type man:<command> in the firefox address bar,
gnome-help pops up with the man page.

i don't have gnome-help installed. but i think this works with every 
mozzila based browser.

EDIT: I'm stupid :(.
OP try:
```
gnome-help man:<command>
```

---

### Post by coffeecat on 2008-08-04
> **sisco311 said:**
> ```
gnome-help man:<command>
```

Hmmm... well.... sniff..... :wink: Doesn't look a patch on konqueror. I'm in Mint on my laptop atm and tried to install konqueror to get a screenshot but the repo servers are down. :(

I'll boot up Ubuntu on my desktop and post a konqueror screenshot.

Back in a tick....

---

### Post by Frederick J. Harris on 2008-08-04
Hey Thanks jimv, sisco311 & coffeecat!  Believe it or not I've been doing that ridiculous copy 25 lines at a time on and off for over a year, and finally had enough of it.  I'll try some of these ideas tonight!

Fred:)

---

### Post by coffeecat on 2008-08-04
Here you go - screenshot below with gnome-help man:iwconfig and man:iwconfig in konqueror side-by-side.

Actually, I'll concede the output of konqueror is not that much better after all, so thanks for that **sisco311**. However, when I tried to print out from the two, konqueror produced some very pretty documentation, but gnome-help just kept crashing. Have you managed to get gnome-help to print, **sisco311**?

---

### Post by sisco311 on 2008-08-04
> **coffeecat said:**
> Here you go - screenshot below with gnome-help man:iwconfig and man:iwconfig in konqueror side-by-side.

Actually, I'll concede the output of konqueror is not that much better after all, so thanks for that **sisco311**. However, when I tried to print out from the two, konqueror produced some very pretty documentation, but gnome-help just kept crashing. Have you managed to get gnome-help to print, **sisco311**?

I don't have any printer.:-?

---

