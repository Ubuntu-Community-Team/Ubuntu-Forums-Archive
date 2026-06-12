---
title: "What is equivale of Windows/Task Manager in Ubuntu?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by abcuser on 2008-08-15
Hi,
time to time some application is hanged out in Ubuntu 8.04 and I would like to kill application/process. In Windows XP there is Task Manager tool that makes it easy to kill hanged applications. What is the equivalent in Ubuntu?
Thanks,
Abcuser

---

### Post by iaculallad on 2008-08-15
> **abcuser said:**
> Hi,
time to time some application is hanged out in Ubuntu 8.04 and I would like to kill application/process. In Windows XP there is Task Manager tool that makes it easy to kill hanged applications. What is the equivalent in Ubuntu?
Thanks,
Abcuser

Equivalent would be your System Monitor:

System->Administration->System Monitor

---

### Post by Crafty Kisses on 2008-08-15
Yeah either System Monitor, there's also a command line equivalent to it as well, called "top", just run "top" in the Terminal
```
top
```

---

### Post by zzzonked on 2008-08-15
Actually, I found that Ubuntu kills not responding programs much more effectively than Windows. In Windows, when you try to End Task or End Process, the program might hang in the "Ending" process -.-" In Ubuntu, this is what I did: right click the panel on top of the screen > Add to Panel > Force Quit > Add. Very nice. Instant kill :p

---

### Post by iaculallad on 2008-08-15
> **zzzonked said:**
> Actually, I found that Ubuntu kills not responding programs much more effectively than Windows. In Windows, when you try to End Task or End Process, the program might hang in the "Ending" process -.-" In Ubuntu, this is what I did: right click the panel on top of the screen > Add to Panel > Force Quit > Add. Very nice. Instant kill :p

As you last resort to kill would be to add the -9 option, as in:

```
sudo kill -9 process_ID
```

Or you could do:

```
sudo killall application_name
```

---

### Post by fiddler616 on 2008-08-15
Is there a nifty keyboard shortcut?
(I tried <Alt>+<F2> "top" <Enter>, and nothing happened...)

---

### Post by iaculallad on 2008-08-15
> **fiddler616 said:**
> Is there a nifty keyboard shortcut?
(I tried <Alt>+<F2> "top" <Enter>, and nothing happened...)

Nothing will appear because "top" is a terminal application. After inputting 'top' you should check the box w/c says "Run in Terminal" and then click on "Run".

---

### Post by mrsudo on 2008-08-15
```
gnome-system-monitor
```

---

