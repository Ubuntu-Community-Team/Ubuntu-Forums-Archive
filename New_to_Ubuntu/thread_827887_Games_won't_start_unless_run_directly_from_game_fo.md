---
title: "Games won't start unless run directly from game folder?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by OpposingForce on 2008-06-13
Hi, I have the games "Urban Terror" and "Vega Strike" they work, but they won't start unless I use the icon that's actually in the folder.  Running it from the command line (not cd'ing) or using a desktop link yields errors and/or won't start the game.

Urban Terror using a desktop link, the Q3 console comes up and gives this

```
ioQ3 1.35urt win-x86 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
0 files in pk3 files
Couldn't load default.cfg

```

Using the ioUrbanTerror.exe that's in the game folder starts and plays the game perfectly fine.

Vega Strike using command line:

```
vegastrike
```

just flickers like it's going to start the game, then says on the console

"failed to open faction.xml"

or something to that effect, I would be able to copy and paste it from the terminal except one thing.  After it exits the game and shows that message, my mouse is dead! I can't even move the mouse at all.  The only way to fix it is to restart X (ctrl-alt-bksp).  Creating a desktop link to the game does the same thing.  However, if I go into vega strike's bin folder and click the startup icon the game starts fine.  Except that it does not run totally fullscreen (gnome bars are still visible).

Any help is appreciated.

---

### Post by Het Irv on 2008-06-13
How did you install the games? It seems like the games were not installed correctly.
Have you tried uninstall/ Reinstalling the games?

---

### Post by sdennie on 2008-06-13
I think this is a pretty common problem with games that you install in your home directory.  If you see this with a lot of games, you could just make a script called like "run_from.sh" and use that in the launchers instead of whatever they use by default.  Something like this:

```

#!/bin/bash

cd `dirname $1`
exec $@

```

Then, just change your launchers to use run_from.sh before the actual command (make sure the commands have full path or the script won't work).

---

### Post by OpposingForce on 2008-06-13
> **vor said:**
> I think this is a pretty common problem with games that you install in your home directory.  If you see this with a lot of games, you could just make a script called like "run_from.sh" and use that in the launchers instead of whatever they use by default.  Something like this:

```

#!/bin/bash

cd `dirname $1`
exec $@

```

Then, just change your launchers to use run_from.sh before the actual command (make sure the commands have full path or the script won't work).

Thanks but I tried it and made a launcher that runs that script.  And set the script to be allowed to execute.  When I click it it doesn't do anything, and if I try to run the script in terminal it just literally does nothing, just moves onto the next line of the terminal like nothing happened.  I then changed it to "exec 'ioUrbanTerror.exe'" and it said

```
/home/cory/Scripts/urban_run.sh: line 4: ioUrbanTerror.exe: command not found

```

But when I changed the script to this:

```
#!/bin/bash

cd '/home/cory/Games/UrbanTerror'
'/home/cory/Games/UrbanTerror/ioUrbanTerror.exe' 
```

It runs.  It seems a little unneccesary to have to have the whole directory there again, but it works.

---

