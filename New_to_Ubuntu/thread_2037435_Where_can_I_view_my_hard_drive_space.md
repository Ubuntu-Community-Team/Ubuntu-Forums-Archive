---
title: "Where can I view my hard drive space?"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by mcimafonte on 2012-08-04
Hello,

I can't seem to find my hard drive space. How can I view the free memory on my HD? Thank you.

---

### Post by robtygart on 2012-08-04
Open the terminal and type this. 

```
sudo fdisk -l
```

---

### Post by Cheesemill on 2012-08-04
> **robtygart said:**
> Open the terminal and type this. 

```
sudo fdisk -l
```
This doesn't show your used space, it just shows your partition layout.

Too see hard drive space you can use:
```
df -h
```

If you want a graphical application you can use 'Disk Usage Analyser', I think that it's installed by default.

---

### Post by robtygart on 2012-08-04
> **Cheesemill said:**
> This doesn't show your used space, it just shows your partition layout.

Too see hard drive space you can use:
```
df -h
```

If you want a graphical application you can use 'Disk Usage Analyser', I think that it's installed by default.

Cool! Thank you for the correction. I will add it to my list of commands :).

---

### Post by robtygart on 2012-08-04
You also can right click on any folder and go to properties.

---

### Post by mcimafonte on 2012-08-04
> **Cheesemill said:**
> This doesn't show your used space, it just shows your partition layout.

Too see hard drive space you can use:
```
df -h
```

If you want a graphical application you can use 'Disk Usage Analyser', I think that it's installed by default.

Thank you!:)

---

### Post by deadflowr on 2012-08-04
There are several ways to view your disk usage in Ubuntu.
One way is as mentioned Disk Usage Analyzer. To open, on the left-side of your screen is the launcher pane. At the top is an icon that looks like the Ubuntu logo. Click on it and a windowy environment will open up. At the top is a search bar, you can use this to quickly find the application by typing in its name. Another thing to do, would be while in same window look at the bottom of the window and you will see several icon(usually white)By default you will be in the first icon, the second icon lists applications, the third list files and folders, the fourth lists music, and the fifth lists videos. Clicking on the application icon will allow you to manually search through all the loaded programs on your system.

Another rather simple way to view your system free disk space, is to enable the status bar in the home folder. In the launcher pane, by default the icon just below the Ubuntu logo icon will be a folder or house like icon(depending on the icon theme being used) Click on it and your home folder will open. Make sure the home folder is in focus(click on the title bar, focused windows will look normal, where as unfocused will look greyed out.) Now move your cursor to the top of you screen to the top panel. There you will see the menu for the home folder, click on view and move down to status bar. click it, and now at the bottom of the home folder window a bar will show you free space as well as other info such as items and depending on what has been selected file size, etc,etc. This should remain set so every time you open your home folder the status bar will be shown.

---

### Post by DarkAmbient on 2012-08-04
Even though terminal-emulators is awesome!

Assuming you'r on Unity? 
Dash > Details 
or "The Indicator-menu up right" > systemsettings > Details

Or in Nautilus, activate the statusbar, then as long as you you don't have focus on some file in Nautilus, the statusbar will tell you disc-space available for current partition. 

*Correct me if I'm wrong on the name Details... I got swedish language in Ubuntu.*

Edit: deadflowr beat me to it. ;-)

---

### Post by Bufeu on 2012-08-04
[http://imgur.com/a/K2tjt](http://imgur.com/a/K2tjt)
Hmm.. a little bit of confusing here. Are some programs displaying the size in GiB, but displays GB as unit? Or does some includes/excludes other partitions than */* is mounted on?

DarkAmbient: Glad to hear I'm not the only one from Sweden here! ;)

EDIT: This is what BOINC Manager says: [http://i.imgur.com/okVPx.png](http://i.imgur.com/okVPx.png)
Why are the numbers so different?

---

### Post by Paqman on 2012-08-04
A nice quick way to see how much free space you've got on the partition(s) your system is on is System Monitor.

---

