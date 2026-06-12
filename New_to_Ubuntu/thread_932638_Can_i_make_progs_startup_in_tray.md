---
title: "Can i make progs startup in tray?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by adobrakic on 2008-09-28
I have pidgin and amsn to open on startup, but they open maximized. can i make them open but be in the system tray?

---

### Post by kansasnoob on 2008-09-28
> **adobrakic said:**
> I have pidgin and amsn to open on startup, but they open maximized. can i make them open but be in the system tray?

If the program does not require a password the answer is yes. You have to know the command necessary to open from command line, then go to System > Administration > Sessions. There you can click on add and add whatever.

You may also want to add the program to the panel which may require adding alltray from synaptic.

Sorry I can't help you with the specific commands to add in sessions. I'm still learning commands.

I might add that you can actually add even programs that require a password but you must edit sudoers, not such a good idea unless you're very sure of yourself.

---

### Post by unutbu on 2008-09-28
If there is a simple method to do this, I don't know it. 
However, if you install a package called devilspie ([https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)) it is possible:
```

sudo apt-get install devilspie

mkdir ~/.devilspie
gedit ~/.devilspie/config.ds
```
Put this in config.ds:
```
(debug)
( if 
  ( is ( application_name ) "pidgin" )
  ( minimize )
)
( if 
  ( is ( application_name ) "amsn" )
  ( minimize )
)

```
Save and exit.

Quit pidgin and amsn (if they are open).

In a terminal run 
```

devilspie &
```

Then run pidgin and amsn:
```

pidgin &
amsn &

```
I'm guessing the command for amsn.

If they start minimized, great. To make this behavior happen with every session
add devilspie to the list of programs to start upon log in by going to System>Preferences>Sessions and adding an item with the command "devilspie" (no ampersand (&) necessary).

If not, post the devilspie output from the terminal.

---

### Post by adobrakic on 2008-09-28
pidgin works fine, but amsn still opens up normally 
```

ado@ado-desktop ~ $ amsn&
[1] 7773
ado@ado-desktop ~ $ 

```

---

### Post by unutbu on 2008-09-29
Please post the output from devilspie when you run it from the terminal:

```
devilspie &
amsn &
```

---

### Post by MrWES on 2008-09-29
Try a program called Alltray:

[http://alltray.sourceforge.net/downloads.html]("http://alltray.sourceforge.net/downloads.html")

Bill

---

### Post by kansasnoob on 2008-09-29
> **MrWES said:**
> Try a program called Alltray:

[http://alltray.sourceforge.net/downloads.html]("http://alltray.sourceforge.net/downloads.html")

Bill

alltray is in the repos so you can just:

```
sudo apt-get install alltray
```

Then you should be able to move anything in the menus to the tray, of course you'll still have to have the proper command in sessions to get it to launch at start-up.

---

### Post by adobrakic on 2008-09-29
> 
Please post the output from devilspie when you run it from the terminal


```

ado@ado-desktop ~ $ devilspie &
[1] 15016
ado@ado-desktop ~ $ Window Title: 'Terminal'; Application Name: 'Terminal'; Class: 'Gnome-terminal'; Geometry: 669x465+161+535
Window Title: '[ubuntu] Can i make progs startup in tray? - Ubuntu Forums - Mozilla Firefox'; Application Name: 'Firefox'; Class: 'Firefox'; Geometry: 1280x977+0+23
Window Title: 'Desktop'; Application Name: 'File Manager'; Class: 'Nautilus'; Geometry: 1280x1024+0+0
Window Title: 'Top Expanded Edge Panel'; Application Name: 'Top Expanded Edge Panel'; Class: 'Gnome-panel'; Geometry: 1280x23+0+0
Window Title: 'Top Panel'; Application Name: 'Top Panel'; Class: 'Gnome-panel'; Geometry: 1280x24+0+1000

ado@ado-desktop ~ $ amsn &
[2] 15023
ado@ado-desktop ~ $ Window Title: 'aMSN - Offline'; Application Name: 'aMSN - Offline'; Class: 'Amsn'; Geometry: 286x883+994+23
Window Title: 'si'; Application Name: 'si'; Class: ''; Geometry: 11x29+0+23

```

I already alltray and as far as my knowledge goes, I know that I can only use alltray to minimize programs that are already maximized on my computer. For example, my firefox, in which I'm typing right now. 
If there's a way that I can make alltray minimize something by itself at startup, please let me know. :p

---

### Post by glennric on 2008-09-29
You can type
```
alltray program &
```
to have the program start in the system tray.
To do this at startup add "alltray program" to the session startup programs list.

---

### Post by adobrakic on 2008-09-29
amsn seems to be the culprit of this issue. Pidgin still opens in the tray fine, but amsn is a different story. The icon that alltray is trying to make amsn stay as shows in the tray, but then amsn still opens maximized and then the default amsn icon shows in the system tray, alongside the one alltray made.

---

### Post by unutbu on 2008-09-30
Okay, let's try this: Edit ~/.devilspie/config.ds

Edit the amsn clause with:
```
( if 
  ( is ( application_name ) "aMSN - Offline" )
  ( minimize )
)

```

---

