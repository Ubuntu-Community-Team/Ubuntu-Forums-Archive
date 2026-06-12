---
title: "Silly request - applications centred at launch"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by zaklinux on 2008-06-08
This may seem trivial, but I was wondering if anyone knew how to get applications (like Firefox) to launch in the middle / centre of the screen / desktop as opposed to tacked to a corner.

Thanks

---

### Post by niteshifter on 2008-06-08
Hi,

No, not trivial. A principle point of FOSS is control belongs with the user, not some suit in a cube ;) FF state information is contained a file located at ~/.mozilla/firefox/XXXXXXX.default/localstore.rdf where XXXXXXX will be some sequence of random characters. 

In that file look for this section:
```
<RDF:Description RDF:about="chrome://browser/content/browser.xul#main-window"
                   sizemode="normal"
                   width="1044"
                   height="798"
                   screenY="52"
                   screenX="4" />

```

Change your positions and sizes there.
**Important:** Backup the file first and do not have FF open while 
editing it.

Edited again: Wow, that'll teach me ... I pulled the above from my notes from when I ran Edgy, sans compiz. I just tried it on Gutsy with compiz - no joy. Methinks FF gets placed by compiz? As this entry does get updated by FF when it's manually moved yet stubbonly insists on far left top corner on FF start.

---

### Post by zaklinux on 2008-06-08
Awesome thanks, but what does ~ mean?

---

### Post by ConMan318 on 2008-06-08
> **zaklinux said:**
> Awesome thanks, but what does ~ mean?

It's short for your home directory, just a shortcut.

```

home/yourname/directory  =  ~/directory

```

---

### Post by Grishka on 2008-06-08
run ccsm and check the options in "place windows" plugin.

---

### Post by Anduu on 2008-06-08
This has been a long standing point of contention between the Gnome devs and the app devs since time began.

The app devs believe it is the window manager's job to set/remember the placement of app windows while the Gnome devs believe otherwise.

---

### Post by niteshifter on 2008-06-09
Hi,

> This has been a long standing point of contention between the Gnome devs and the app devs since time began.

The app devs believe it is the window manager's job to set/remember the placement of app windows while the Gnome devs believe otherwise.

I think they're both correct: It's someone else's job. Which means, of course, that we need a windows registry :twisted:

<ducking, running>

To recap for anyone following this thread:

Use the technique I posted if you don't use compiz (or similar?)
Use Griska's method if you do run compiz (ccsm, aka System/Preferences/Advanced Desktop Effects Settings)

---

### Post by kpkeerthi on 2008-06-09
And there is also Window Manager and Application independent way of controlling the window attributes: **devilspie & wmctrl**

[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)
[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)
[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)
(wmctrl) [http://www.linux.com/feature/122471?theme=print](http://www.linux.com/feature/122471?theme=print)

---

