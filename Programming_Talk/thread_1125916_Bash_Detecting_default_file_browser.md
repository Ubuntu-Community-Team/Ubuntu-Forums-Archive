---
title: "Bash: Detecting default file browser"
date: 2009-04-14
forum: Programming Talk
---

### Post by Jesdisciple on 2009-04-14
I have a Bash script which, at the end, opens a directory in Nautilus.  I think my script may be useful to others, so I'm wondering how I can tell whether the user prefers Konqueror or what not?  I'm pretty sure there must be an env var or something...

Thanks. :)

---

### Post by cszikszoy on 2009-04-14
you could just use 
```
$ xdg-opn <path>
```
and the path will open in whatever file browser the user uses, be it konquerer, nautilus, or anything else.

---

### Post by kerry_s on 2009-04-15
```
$ xdg-**open** <path>
```

---

### Post by cszikszoy on 2009-04-15
> **kerry_s said:**
> ```
$ xdg-**open** <path>
```

Right, oops!  Typos :mad:

---

### Post by kerry_s on 2009-04-15
> **cszikszoy said:**
> Right, oops!  Typos :mad:

:lolflag: happens to me all the time, damn that fat finger syndrome! ;)

---

### Post by Jesdisciple on 2009-04-15
Thanks to both of you!

---

### Post by Jesdisciple on 2009-04-15
Oops...  I thought it worked and then stopped working when [I sudo'ed the script]("http://ubuntuforums.org/showthread.php?p=7076521"), but it actually gives this error regardless of privileges:```
Warning: unknown mime-type for "gnome-pilot/new" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
```

Does anyone know why?  Thanks.

---

### Post by Jesdisciple on 2009-04-15
And...  I was right the first time.  There's no problem if the script is not executed as root.  Still, does anyone happen to know why?

---

### Post by Reiger on 2009-04-15
Knowing? No. 

Still, you may be able to make progress from observing the output of the following:
```

cd ~/.gnome2
ls -A
cd /root
sudo su
cd .gnome2
ls -A

```

---

### Post by Jesdisciple on 2009-04-15
The only significant difference I see is nautilus-sendto, but its manpage is a disappointment.```
cd ~/.gnome2
chris@Jesdisciple-laptop:~/.gnome2$ ls -A
accels        backgrounds.xml  epiphany     gedit               glchess              gnome-sudoku          gok       main              panel2.d   yelp
accelsevince  deskbar-applet   evince       gedit-2             gnomemeeting         gnometris.d           iagno     nautilus-scripts  rhythmbox
accelsgedit   eog              file-roller  gedit-metadata.xml  gnome-power-manager  gnome-volume-control  keyrings  nautilus-sendto   share
chris@Jesdisciple-laptop:~/.gnome2$ cd /root
chris@Jesdisciple-laptop:/root$ sudo su
[sudo] password for chris: 
root@Jesdisciple-laptop:~# cd .gnome2
root@Jesdisciple-laptop:~/.gnome2# ls -A
accels  accelsgedit  file-roller  gedit-2  gedit-metadata.xml  main  nautilus-scripts  network-admin-locations  yelp
```

Thanks bunches.

---

### Post by Reiger on 2009-04-15
This is mine:
```

accels        backgrounds.xml  file-roller  gedit-metadata.xml   keyrings  nautilus-scripts         rhythmbox
accelsevince  eog              f-spot       gnome-pilot.d        main      network-admin-locations  share
accelsgedit   evince           gedit-2      gnome-power-manager  meld      panel2.d                 yelp

```

On Jaunty, upgraded from Intrepid which was in turn upgraded from Hardy. Atlough I have stripped Gnome (because I run KDE as my main DE, and I have no need for Gnome stuff interfering with my KDE).

---

### Post by Jesdisciple on 2009-04-15
Here's something:  I've determined that the issue comes from the combination of *sudo* and *xdg-open*, regardless of **all** other factors.

I don't get the error if I:[list]
[*]run the command directly without *sudo*
[*]run the command without *sudo* from a script run without *sudo*
[/list]

I do get the error if I:[list]
[*]run the command directly with *sudo*
[*]run the command directly with *sudo -u chris*
[*]run the command with *sudo* from a script run without *sudo*
[*]run the command without *sudo* from a script run with sudo
[*]run the command with *sudo* from a script run with *sudo*
[*]run the command with *sudo -u chris* from a script run with *sudo*
[*]run the command with *sudo -u chris* from a script run without *sudo*
[/list]

---

### Post by Jesdisciple on 2009-04-16
I've filed [Bug #362121]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/362121") for this.

---

