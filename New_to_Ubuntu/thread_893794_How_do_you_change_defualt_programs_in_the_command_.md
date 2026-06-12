---
title: "How do you change defualt programs in the command line?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by mike941 on 2008-08-18
For example how would i change my default audio program or my default battery monitor? do i enter the name of the program or something? Currently the graphical method for using a battery monitor don't work.

---

### Post by boblemur on 2008-08-18
i dont understand ur question, could u please post an example of 

-a command
-how it runs
-how you would want it to run

so we can see what you mean

---

### Post by freak42 on 2008-08-18
on the commandline you don't have default applications (afaik).. you usually specify the appname and afterwards commands (or files) so, for instance
```
audacious ~/Desktop/bla.mp3 
```

will make audacious play the bla.mp3 file that is lying on my desktop.

--
for gnome (gui) you can specify some default applications:

1. in a nautilus (filebrowser) window go to edit->preferences->media to select the default application for a wide range of media.

2. or rightlick on any file and choose "open with other application" if you want to open it only once with the application (it won't stick as default)

3. on a file rightlick-> properties -> open with : there you can add applications as defaults as well

hth

---

### Post by nicedude on 2008-08-18
If you mean the dea=fault program that plays your audio files then you right click on an MP3 and choose properties then click the open-with tab and there will be a list of programs you can choose from, you can always add new ones too.

As for the battery applet, do you mean the one in the top menubar? You could try using "conky" to see all your system info as it is pretty in depth but not sure it has a batt monitor by default.

I have an Acer 5520 and my top menubar batt applet works Ok so I don't know why yours doesn't we are pretty close in laptops.

---

### Post by pauper on 2008-08-18
In some cases (visudo; crontab -e; man man; Ctrl-x/Ctrl-e in bash; $TERM; etc.)
you could define what program to use (see /etc/alternatives), by running
"sudo update-alternatives --config <program>". To view all:

```
update-alternatives --display 

# Press <TAB> trice and y.
```

Or add to ~/.bashrc "export EDITOR=/usr/bin/vim.basic", for example.

I don't know, if there are any discrepancies between gutsy and hardy regarding
this one, but in the former one there are /etc/gnome/defaults.list and
~/.local/share/applications/defaults.list files, that maintain what would
launch what, if you double-click on some file. You could pick something from
/usr/share/applications/mimeinfo.cache and paste into ~/.local/.../defaults.list

For example,

> audio/x-mp3=rhythmbox.desktop

Default battery applet comes with "Notification Area"; see if "Always display
an icon" is checked ("General" tab):

```
gnome-power-preferences
```

Try invoking it from command line:

```
gnome-power-manager
```

Other applet is "Battery Charge Monitor" (Right-click on the panel and select
"Add to Panel...").

---

