---
title: "[SOLVED] Create a separate home partition in Ubuntu, Problem"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by germanix on 2008-10-03
I have been trying to create a separate home partition in Ubuntu by using the "How to" on this website [www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)
All went well until I came to this part:

Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

You'll then be taken to the nano text editor. Add in this line:
/dev/hda7 /home ext3 nodev,nosuid 0 2

I was not taken to the nano text editor and could not add this line !!!

Then save (Control-X), confirm (Y), and exit (Enter)

After you reboot, you should be now using your new /home partition. 

I have not re-booted as I am afraid if I reboot without adding that line to the nano text editor my files could be gone or all the work I had done so far. 
Any ideas?

---

### Post by shifty_powers on 2008-10-03
try

```
sudo gedit /old/etc/fstab
```

---

### Post by germanix on 2008-10-03
here the output of sudo gedit /old/etc/fstab

jacques@jacques-desktop:/old/home$ sudo gedit /old/etc/fstab
[sudo] password for jacques: 
No protocol specified
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
jacques@jacques-desktop:/old/home$

---

### Post by drs305 on 2008-10-03
With graphical apps, try:
```
gksudo gedit /old/etc/fstab
```

---

### Post by germanix on 2008-10-03
jacques@jacques-desktop:/old/home$ gksudo gedit /etc/fstab
No protocol specified

(gksudo:6122): Gtk-WARNING **: cannot open display: :0.0
jacques@jacques-desktop:/old/home$

---

### Post by shifty_powers on 2008-10-03
do me a favour,

```
cd /etc
```

```
ls
```

and post the output...

---

### Post by germanix on 2008-10-03
I have now managed to enter the nano text editor, entered the missing line, saved it and exit. I now need to reboot, the problem is I cannot reboot as the option to restart or shut down has gone missing from my desktop???

---

### Post by drs305 on 2008-10-03
> **germanix said:**
> I have now managed to enter the nano text editor, entered the missing line, saved it and exit. I now need to reboot, the problem is I cannot reboot as the option to restart or shut down has gone missing from my desktop???

You can reboot using the command:
```
sudo reboot
```
or
```
sudo shutdown -r now
```

---

### Post by germanix on 2008-10-03
Could not launch menu item
I cannot get into the terminal to shut it down
output when trying to open the terminal:
Could not launch menu item
Failed to change to directory '/home/jacques' (No such file or directory)

---

### Post by germanix on 2008-10-03
Well it does not look as if anyone has any more ideas at this time. I quess the only option left is to cut the power and do a new installation. I would still like to create a separate home partition though. It is after midnight in Germany so I will call it a day and try again tommorow. Thank you all for your help.

---

