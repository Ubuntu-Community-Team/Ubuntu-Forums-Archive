---
title: "Gnome system monitor"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by grewolf on 2008-07-16
Does anyone know how to change the system monitor.  When I open it it shows no "X" to close no "-" to minimize and no "box" to maximize When I try to use my re size command nothing happens.  I have looked but have not found any similar issues for the Gnome system monitor.  I have added screen shot of system monitor

I am using Gutsy Gibbon.  Kernal  2.6.22-15-generic

Also I just was reading through some help files and found the command ```
lsb_release -a
``` can any one tell me what this out put means 

```
LSB Version:    core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-2.0-ia32:core-3.0-ia32:core-3.1-ia32:cxx-2.0-noarch:cxx-3.0-noarch:cxx-3.1-noarch:cxx-2.0-ia32:cxx-3.0-ia32:cxx-3.1-ia32:graphics-2.0-noarch:graphics-3.0-noarch:graphics-3.1-noarch:graphics-2.0-ia32:graphics-3.0-ia32:graphics-3.1-ia32:desktop-3.1-noarch:desktop-3.1-ia32
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
```

---

### Post by maddog39 on 2008-07-16
Hmm.. I dont really know what the problem is with the window controls. You should try launching the system monitor from the command line and post the output. Enter "gnome-system-monitor" into a terminal window (without quotes) to launch from the command line.

---

### Post by PmDematagoda on 2008-07-16
Did you kill the window manager such as metacity or compiz by any chance? You need to have the window manager running to have such things.

---

### Post by grewolf on 2008-07-16
> **maddog39 said:**
> Hmm.. I dont really know what the problem is with the window controls. You should try launching the system monitor from the command line and post the output. Enter "gnome-system-monitor" into a terminal window (without quotes) to launch from the command line.

This is the output from the command line


```
jwilson@Crash-Burn:~$ gnome-system-monitor

** (gnome-system-monitor:19749): WARNING **: SELinux was found but is not enabled.
```

---

### Post by maddog39 on 2008-07-16
Yea, you could try running the command:
```

metacity &

```
from Alt+F2 or a terminal window and see if that solves the problem.

---

### Post by grewolf on 2008-07-17
> **PmDematagoda said:**
> Did you kill the window manager such as metacity or compiz by any chance? You need to have the window manager running to have such things.

> Yea, you could try running the command:
Code:

```
metacity &
```

from Alt+F2 or a terminal window and see if that solves the problem. 

I believe that I have Compiz Fusion running as the window manager.  Here is the out put from command ```
metacity &
``` I have also added another print screen as attatchment

```
jwilson@Crash-Burn:~$ metacity &
[1] 23736
jwilson@Crash-Burn:~$ Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```

---

### Post by PmDematagoda on 2008-07-17
I believe you should use the --replace option as given, so the command is:-
```
metacity --replace
```

---

### Post by grewolf on 2008-07-17
> **PmDematagoda said:**
> I believe you should use the --replace option as given, so the command is:-
```
metacity --replace
```

Thank you this fixed it.  

Thank you to PmDematagoda and Maddog39  :)

Do you mind if I ask what led you to believe that this was the problem.  I would like to learn what to look for.

---

### Post by PmDematagoda on 2008-07-17
> **grewolf said:**
> Thank you this fixed it.  

Thank you to PmDematagoda and Maddog39  :)

Do you mind if I ask what led you to believe that this was the problem.  I would like to learn what to look for.

The compiz window manager may not have the Window Decorations plugin loaded, you can load the Window Decorations plugin through CCSM which can be installed through:-
```
sudo apt-get install ccsm
```

---

### Post by grewolf on 2008-07-17
> **PmDematagoda said:**
> The compiz window manager may not have the Window Decorations plugin loaded, you can load the Window Decorations plugin through CCSM which can be installed through:-
```
sudo apt-get install ccsm
```

I ran the code and received 

```
E: Couldn't find package ccsm
```

But I do have CompizConfig Settings Manager

---

### Post by PmDematagoda on 2008-07-17
> **grewolf said:**
> I ran the code and received 

```
E: Couldn't find package ccsm
```

But I do have CompizConfig Settings Manager

Yes, CompizConfig Settings Manager is what you need.

---

