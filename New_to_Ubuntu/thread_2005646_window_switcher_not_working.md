---
title: "window switcher not working"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by shubham1 on 2012-06-18
the window switcher is not working i mean when i click on a window icon in launcher which has 2 or more windows it does not shows all the windows the way it showed before it takes me to one window even i click later on it does not works please help me i cant use unity beacuase of this

---

### Post by shubham1 on 2012-06-20
any one plese

---

### Post by duracella on 2012-06-20
Hi.

Do you mean the quicklists for the icons?

Then [this]("http://www.webupd8.org/2012/06/unity-window-quicklists-switch-between.html") might be what you are looking for?

-Andrew

---

### Post by zombifier25 on 2012-06-20
Did you try clicking the icon two times? It should bring up all the windows of that application.

---

### Post by shubham1 on 2012-06-20
> **zombifier25 said:**
> Did you try clicking the icon two times? It should bring up all the windows of that application.
yes many times

---

### Post by shubham1 on 2012-06-20
> **duracella said:**
> Hi.

Do you mean the quicklists for the icons?

Then [this]("http://www.webupd8.org/2012/06/unity-window-quicklists-switch-between.html") might be what you are looking for?

-Andrew
this is not i mean

---

### Post by shubham1 on 2012-06-20
> **shubham1 said:**
> this is not i mean
i mean when you lick on an application icon and if many windows are running together then it shows them all i tried clicking many times nothing works

---

### Post by Xerxes314 on 2012-07-11
I have had the same problem since upgrading to 12.04, so I might as well describe it here.

Setup: I have multiple windows open of a program (say, Firefox) in multiple workspaces. Let's say I have 2 windows open in each of 3 workspaces for a total of 6 windows. Initially, some other window (say, Terminal) has focus.

When I click on the Firefox icon in the launcher, the last-used Firefox window in the current workspace gains focus, which is the correct behavior.

When I click on the Firefox icon in the launcher a second time, an Expo-style spread of windows appears for the 2 windows in the current workspace. If I had only 1 window open, nothing would happen. This is incorrect behavior. The correct behavior is to display an Expo-style spread of all 6 open windows of the selected program.

From reading the latest [Unity discussion of task switching]("https://docs.google.com/document/d/1EdrlUuZvA9P8-BZufUU2KlHGjg49p9UacF4MCL0U5uA/edit"), I can't quite tell if this behavior is considered a feature or a bug, but I would very much like to restore the correct behavior I used constantly in the last version. Honestly, I'm not sure how one is expected to pull up a window that happens to be on another workspace now.

EDIT: Ack, wouldn't you know: a few more minutes of searching reveals [this extensive thread]("http://ubuntuforums.org/showthread.php?t=1976347") on the topic. I guess this is an intentional bug after all...

---

### Post by shubham1 on 2012-07-12
but in my when i click on firefox icon for the second time then even the windows on same workspace do not appear this is even worse

---

### Post by lolpenguin on 2012-07-12
Super + W will show all windows on the current workspace in the same style.

---

### Post by shubham1 on 2012-07-13
i know that it works but it isnt the solution

---

### Post by Kopkins on 2012-07-13
You could try restarting compiz, which is your window manager. 
```
compiz --replace
```

I used to have to do this all the time as none of my compiz functions would work after resuming from suspend. 

Hope this helps,
Kopkins

---

### Post by stinkeye on 2012-07-13
Firstly make sure your running **unity** and not **unity 2d**.
In the terminal...
```
echo $DESKTOP_SESSION
```
The compiz scale plugin does the window spread.

If your in the **Ubuntu 2d** session, check your GFX driver in use....
```
sudo lshw -c video
```

eg my output..
```
[COLOR="Olive"]glen@Precise:~$[/COLOR] **sudo lshw -c video**
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR="Red"]driver=nvidia[/COLOR] latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
```

---

### Post by shubham1 on 2012-08-13
my problem is solved after some upgrade but very late thanks allllllllll:)

---

