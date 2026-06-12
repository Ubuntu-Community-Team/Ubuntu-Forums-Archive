---
title: "Package Installer problem"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by peter1128 on 2008-06-18
I'm trying to install a .deb file via the package installer but I keep getting the following error.

" Only one software management tool is allow to run at the same time
Please close the other application eg 'Update manager', 'aptitude' or 'synaptic' first. "

It seem to be telling me that a program is already running, but this is none???

Is there a way a seeing what is running and stopping any thing that needs stopping... some kind of task manager?.

HELP :(

many thank

---

### Post by Nikitas350 on 2008-06-18
If you want a task manager you can go to System--->Administration--->system monitor. But to solve the problem you should probably run this command in terminal (application-->accessories--->terminal):
sudo rm /var/cache/apt/archives/lock

---

### Post by hyper_ch on 2008-06-18
run:
```

ps aux > ~/Desktop/processes.txt

```

and post the text file then here.

Or you can directly search
```

ps aux | grep synaptic

```

```

ps aux | grep adept

```

```

ps aux | grep aptitude

```

```

ps aux | grep ....

```

---

### Post by aktiwers on 2008-06-18
You can only have one package-manager open at a time. This means if you are installing updates you can't use Synaptic package manager at the same time. Or if you are sudo apt-get installing anything you can't run another package manager at the same time.

Make sure you have no other instance of Synaptic open, that it's not updating your system and that you are not usint apt-get. Then you should have no problem.

---

### Post by designateduser on 2009-08-12
I have the same issue! after closing an installer script I am now not able to run anything that edits my software

---

