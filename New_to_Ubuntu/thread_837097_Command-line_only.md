---
title: "Command-line only"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by JazonEsti on 2008-06-22
Just for fun -- and to stump my office mates -- can I boot Ubuntu to command line only like DOS?

If that's possible, how can I...

1. Start OpenOffice?
2. Shut down the PC?

Thanks!

---

### Post by rockerphil on 2008-06-22
i'm not sure exactly how to BOOT in to the command line only, but i know that from your graphical desktop if you hit Ctrl+Alt+Backspace it'll kill your X session thus dropping you to a command line only, but the drawback is you can't start any graphical interfaces without restarting X using the startx command thus bringing you back to your graphical desktop. but from the command line you can type this to shut it down

sudo shutdown -h now

hope the info helps

---

### Post by Oldsoldier2003 on 2008-06-22
> **JazonEsti said:**
> Just for fun -- and to stump my office mates -- can I boot Ubuntu to command line only like DOS?

If that's possible, how can I...

1. Start OpenOffice?
2. Shut down the PC?

Thanks!

yes
1. you'll need to start the gui before you can start open office start
```
startx
```
2. shutting down from the command line
```
sudo shutdown -P
```

---

### Post by Oldsoldier2003 on 2008-06-22
> **rockerphil said:**
> i'm not sure exactly how to BOOT in to the command line only, but i know that from your graphical desktop if you hit Ctrl+Alt+Backspace it'll kill your X session thus dropping you to a command line only, but the drawback is you can't start any graphical interfaces without restarting X using the startx command thus bringing you back to your graphical desktop. but from the command line you can type this to shut it down

sudo shutdown -h now

hope the info helps

 add ```
textonly quiet
``` to your kernel line in menu.lst for a commandline boot

---

### Post by Dedoimedo on 2008-06-22
Hi,

Yes you can do that. In general, in Linux, the default runlevel is governed by the /etc/inittab file. Graphical environment is runlevel 5, normally.

However, Ubuntu is different and kind of breaks the Linux standards a little by booting in non-standard runlevel.

In Ubuntu, you'll have to edit this file:

/etc/event.d/rc-default file

Back this file first:

sudo cp /etc/event.d/rc-default /etc/event.d/rc-default-backup

Then, open it in a text editor:

sudo gedit /etc/event.d/rc-default

Find the entries that read telinit 2 and change to telinit 3. When you reboot the next time, you'll be without GUI.

However, you can also use command line and do all the command line stuff from any terminal, even if you're booted into GUI.

Just open a terminal and write commands.

Furthermore, you can switch between consoles by pressing Ctrl-Alt-F1-6, up to 6 different text consoles. You'll be able to work in command line without seeing GUI.

All that said, to start OpenOffice from command line:

1. Look for it:
which openoffice --> to see if it's in the default path
2. Start by typing the name of the relevant executable

To shut down the computer, read about the shutdown command by typing man shutdown or info shutdown in terminal.

Cheers,
Dedoimedo


P.S. You can also look into an application called rcconf, which allows you to change the default runlevel (with or without GUI).

---

### Post by WitchCraft on 2008-06-22
To stop gdm from loading on when the machine starts up, simply type:
```

sudo update-rc.d -f gdm remove

```

More importantly to set gdm to automatically start again
```

sudo update-rc.d gdm defaults 13 01

```

The important part here is the numbers on the end, which tell the system where gdm goes in the boot up and shutdown order. It's 13th to start up, and 1st to shut down. And the leading 0 on 01 is important, because update-rc.d only works with two digit numbers.


Also, you can then manually start and stop gdm. The easist way is to open a terminal:
```

sudo /etc/init.d/gdm stop

```

And then ctrl+alt+backspace to end your current session

To restart the gui
```

sudo /etc/init.d/gdm start

```

To shutdown and restart your PC
```

shutdown -r now

```

To shutdown and halt your PC
```

shutdown -h now

```

To run openoffice you have to start the x server:
To start X:
```

startx

```

---

### Post by acidsolution on 2008-06-22
You can boot in graphical mode and than switch to command line mode by pressing 
CTRL+ALT+F2  
this doesnot kill your x session . you can switch back to graphical mode by pressing
CTRL+ALT+F7

I dont think u can open openoffice in command line mode you have to switch to graphical mode .

if you want to shutdown your pc than 
```
 shutdown -P now 
to shutdown immediately or you can give time in minutes 
shutdown -P 2 
will shutdown pc in 2 minutes if u dont cancel it 
```

---

### Post by Lakefall on 2008-06-22
> **WitchCraft said:**
> Simply type:
sudo update-rc.d -f gdm remove
You should also be able to use services-admin, which is in the system menu. Use it to disable "Graphical login manager (gdm)". After you have disabled gdm, you should be able to start X by logging in and typing "startx".

> **Oldsoldier2003 said:**
> 2. shutting down from the command line
```
sudo shutdown -P
```
The time is mandatory: ```
sudo shutdown -P now
```

---

