---
title: "I wonder..."
date: 2008-08-09
forum: New to Ubuntu
---

### Post by nintendorulz55 on 2008-08-09
Just a random wondering.. is there a way to make it so that a program (in this case, Rhythmbox) can start itself and open when i log into the desktop? Im always opening it right when i turn my computer on, and if it would automatically open.... well, that'd be awesome!

---

### Post by bpowell2005 on 2008-08-09
> **nintendorulz55 said:**
> Just a random wondering.. is there a way to make it so that a program (in this case, Rhythmbox) can start itself and open when i log into the desktop? Im always opening it right when i turn my computer on, and if it would automatically open.... well, that'd be awesome!

Yes.

Go to System, Preferences, Sessions, start-up programs tab, and add Rythmbox. Works like a champ!

---

### Post by InfinityCircuit on 2008-08-09
System -> Preferences -> Sessions

This sets what starts when you log into GNOME.  You can add something here by just clicking "Add". Of course, the program name is Rhythmbox, the rest is up to you.

---

### Post by nothingspecial on 2008-08-09
You can do that for any app you like

---

### Post by nintendorulz55 on 2008-08-09
i can't seem to think up a code.. i know that my rythmbox folder is is usr/lib, but when i go to usr/lib/rythmbox the only thing there is rythmbox-metadata and a folder titled "plugins"... rythmbox-metadata didn't work when i tried it as the command. is there something i'm missing?

---

### Post by bpowell2005 on 2008-08-09
> **nintendorulz55 said:**
> i can't seem to think up a code.. i know that my rythmbox folder is is usr/lib, but when i go to usr/lib/rythmbox the only thing there is rythmbox-metadata and a folder titled "plugins"... rythmbox-metadata didn't work when i tried it as the command. is there something i'm missing?

Just typing "Rhythmbox" gets the program running for me...that should work for you...no need to include a path.

---

### Post by nothingspecial on 2008-08-09
The command is 
```
rhythmbox
```

So in Name - type Rhythmbox

In Command - type rhythmbox

And in comment - type whatever you like, Music Player would be good but it`s up to you.

---

### Post by nothingspecial on 2008-08-09
Note that it`s not a capital 'R' in rhythmbox. All letters are lower case.

---

### Post by nintendorulz55 on 2008-08-09
> **bpowell2005 said:**
> Just typing "Rhythmbox" gets the program running for me...that should work for you...no need to include a path.

0_0 don't i feel like a n00b. haha, but thanks!

---

### Post by netghoul on 2008-08-09
Go to system then prefs and then sessions. click add and put in rythombox in the name. Or else you can get a nice program called _**avant window navigator**_ which takes the place of your bottom taskbar and looks really good. its modeled after mac.
:p[SIZE="4"][/SIZE]

---

### Post by maoglone on 2008-08-10
> **nothingspecial said:**
> The command is 
```
rhythmbox
```

So in Name - type Rhythmbox

In Command - type rhythmbox

And in comment - type whatever you like, Music Player would be good but it`s up to you.

If I wanted to open other programs at startup, how could I best find/figure out what the commands are?  Are they ALWAYS just the names of the programs all in lowercase?  I'm assuming that I need to know the exact filenames.  Is this correct?

---

### Post by nothingspecial on 2008-08-10
> **maoglone said:**
> If I wanted to open other programs at startup, how could I best find/figure out what the commands are?  Are they ALWAYS just the names of the programs all in lowercase?  I'm assuming that I need to know the exact filenames.  Is this correct?

They're not always the program names in lower case although they usually are.
For example

```
firefox gimp vlc
``` etc etc

If not thet are usually similar with hyphons. For example
```

avant-window-navigator gtkpod-aac
```

You could open a terminal and try them out before entering them in your startup programs.

```
dpkg -l
``` (lower case L not number one), will list all your installed programs and most of the names listed there will be the command to open them. This is not always the case though. 
For example in my list of programs is openoffice.org, however the command to open it is simply
```
openoffice
```

None of them will be to hard to figure out though.

---

