---
title: "Gnome-terminal equivalent to &quot;konsole --noclose -e&quot;"
date: 2006-12-26
forum: Programming Talk
---

### Post by 454redhawk on 2006-12-26
Greetings

Can someone tell me the Gnome-terminal equivalent to "konsole --noclose -e"

I want to launch a terminal and command in gnome and have the window stay open after the command is finished. I prefer to use gnome-terminal.

I know how to do it with xterm and konsole.

Thanks

---

### Post by 454redhawk on 2006-12-28
Anyone?

---

### Post by maddog39 on 2006-12-28
I took a quick look at gnome-terminal --help and it didnt turn up any answers which leads me to believe this isn't possible in gnome-terminal unfortunetly.
> 
addog39@maddog39-laptop:~$ gnome-terminal --help
Usage: gnome-terminal [OPTION...]
  --load-modules=MODULE1,MODULE2,...              Dynamic modules to load

Help options
  -?, --help                                      Show this help message
  --usage                                         Display brief usage message

Application options
  -e, --command=STRING                            Execute the argument to this
                                                  option inside the terminal.
  -x, --execute                                   Execute the remainder of the
                                                  command line inside the
                                                  terminal.
  --window                                        Open a new window containing
                                                  a tab with the default
                                                  profile. More than one of
                                                  these options can be
                                                  provided.
  --window-with-profile=PROFILENAME               Open a new window containing
                                                  a tab with the given
                                                  profile. More than one of
                                                  these options can be
                                                  provided.
  --tab                                           Open a new tab in the
                                                  last-opened window with the
                                                  default profile. More than
                                                  one of these options can be
                                                  provided.
  --tab-with-profile=PROFILENAME                  Open a new tab in the
                                                  last-opened window with the
                                                  given profile. More than one
                                                  of these options can be
                                                  provided.
  --window-with-profile-internal-id=PROFILEID     Open a new window containing
                                                  a tab with the given profile
                                                  ID. Used internally to save
                                                  sessions.
  --tab-with-profile-internal-id=PROFILEID        Open a new tab in the
                                                  last-opened window with the
                                                  given profile ID. Used
                                                  internally to save sessions.
  --role=ROLE                                     Set the role for the
                                                  last-specified window;
                                                  applies to only one window;
                                                  can be specified once for
                                                  each window you create from
                                                  the command line.
  --show-menubar                                  Turn on the menubar for the
                                                  last-specified window;
                                                  applies to only one window;
                                                  can be specified once for
                                                  each window you create from
                                                  the command line.
  --hide-menubar                                  Turn off the menubar for the
                                                  last-specified window;
                                                  applies to only one window;
                                                  can be specified once for
                                                  each window you create from
                                                  the command line.
  --full-screen                                   Set the last-specified
                                                  window into fullscreen mode;
                                                  applies to only one window;
                                                  can be specified once for
                                                  each window you create from
                                                  the command line.
  --geometry=GEOMETRY                             X geometry specification
                                                  (see "X" man page), can be
                                                  specified once per window to
                                                  be opened.
  --disable-factory                               Do not register with the
                                                  activation nameserver, do
                                                  not re-use an active terminal
  --use-factory                                   Register with the activation
                                                  nameserver [default]
  --startup-id=STRING                             ID for startup notification
                                                  protocol.
  -t, --title=TITLE                               Set the terminal's title
  --working-directory=DIRNAME                     Set the terminal's working
                                                  directory
  --default-working-directory=DIRNAME             Set the default terminal's
                                                  working directory. Used
                                                  internally
  --zoom=ZOOMFACTOR                               Set the terminal's zoom
                                                  factor (1.0 = normal size)
  --active                                        Set the last specified tab
                                                  as the active one in its
                                                  window

GTK+
  --gdk-debug=FLAGS                               Gdk debugging flags to set
  --gdk-no-debug=FLAGS                            Gdk debugging flags to unset
  --display=DISPLAY                               X display to use
  --screen=SCREEN                                 X screen to use
  --sync                                          Make X calls synchronous
  --name=NAME                                     Program name as used by the
                                                  window manager
  --class=CLASS                                   Program class as used by the
                                                  window manager
  --gtk-debug=FLAGS                               Gtk+ debugging flags to set
  --gtk-no-debug=FLAGS                            Gtk+ debugging flags to unset
  --g-fatal-warnings                              Make all warnings fatal
  --gtk-module=MODULE                             Load an additional Gtk module

Bonobo activation Support
  --oaf-ior-fd=FD                                 File descriptor to print IOR
                                                  on
  --oaf-activate-iid=IID                          IID to activate
  --oaf-private                                   Prevent registering of
                                                  server with OAF

GNOME Library
  --disable-sound                                 Disable sound server usage
  --enable-sound                                  Enable sound server usage
  --espeaker=HOSTNAME:PORT                        Host:port on which the sound
                                                  server to use is running
  --version                                       2.16.0

Session management
  --sm-client-id=ID                               Specify session management ID
  --sm-config-prefix=PREFIX                       Specify prefix of saved
                                                  configuration
  --sm-disable                                    Disable connection to
                                                  session manager

GNOME GUI Library
  --disable-crash-dialog                          Disable Crash Dialog


---

### Post by po0f on 2006-12-28
454redhawk,

Open a new gnome-terminal.  Navigate to Edit->Preferences.  Click on the "Title and Command" tab.  There's a spinbox labeled "when command exits", change it from "exit the terminal" to "hold the terminal open".

---

### Post by 454redhawk on 2006-12-28
> **po0f said:**
> 454redhawk,

Open a new gnome-terminal.  Navigate to Edit->Preferences.  Click on the "Title and Command" tab.  There's a spinbox labeled "when command exits", change it from "exit the terminal" to "hold the terminal open".

That works. Thanks

However, What if I wanted to include that into a script? Is there an option I could use to create a profile with that option so it will run on any gnome computer? (without using read)

Thanks

---

### Post by po0f on 2006-12-28
454redhawk,

Bash:
```
[FONT="Courier New"]echo "Hit any key to continue..."
read[/FONT]
```

[EDIT]

I guess I was posting as you were editing.  ;)

Is there any reason you can't use read?

---

### Post by 454redhawk on 2006-12-29
> **po0f said:**
> 454redhawk,

Bash:
```
[FONT="Courier New"]echo "Hit any key to continue..."
read[/FONT]
```

[EDIT]

I guess I was posting as you were editing.  ;)

Is there any reason you can't use read?

One example comes to mind

Without writing a script I could associate *.par2 files (in nautilus) with a command executed in a terminal and have that window stay open to see the results. By double clicking a par2 file the window will open and the command executed.


In konquer I select settings-->configure konqueor-->File associations--->Add--->par2--->Add----> I add *.par2 and then in all caps *.PAR2------>Click Add under application preference order---->"konsole --noclose -e par2 r" 

That will enable me to double click par2 files and a konsole window will open and verify and repair if needed. The window will stay open when finished so I can be sure all went well.

How can I accomplish this in Gnome? Without a script. 
I have already created a nice little GUI zenity script to Verify , Repair & Create par2 files but would like to simply double click a par2 file.

Thanks

---

### Post by po0f on 2006-12-29
454redhawk,

I don't think you'll be able to accomplish this without scripts in GNOME.

Nautilus can be extended with scripts through [nautilus-actions](http://packages.ubuntu.com/edgy/gnome/nautilus-actions), just in case you haven't heard of it.

---

### Post by 454redhawk on 2006-12-29
> **po0f said:**
> 454redhawk,

I don't think you'll be able to accomplish this without scripts in GNOME.

Nautilus can be extended with scripts through [nautilus-actions](http://packages.ubuntu.com/edgy/gnome/nautilus-actions), just in case you haven't heard of it.

I Am checking out nautilus-actions right now.

A guy over in the Gnome forums suggested

```
gnome-terminal -x bash -c "ls; cat"
```

 where "ls" is the command you want to run.

That has the desired effect

Thanks

---

### Post by stani on 2007-03-13
Thanks, I needed this for SPE to launch python files so that users still can see the output. It works like a charm.

Stani

---

### Post by Mockskin on 2007-03-13
Is there any reason for not setting up an alternate profile for tasks like that and using:
```

gnome-terminal --window-with-profile=xxxxx

```

?

---

### Post by stani on 2007-03-13
> **Mockskin said:**
> Is there any reason for not setting up an alternate profile for tasks like that and using:
```

gnome-terminal --window-with-profile=xxxxx

```

?

This is something you can do on your own computer, but when you distribute a program for others, you don't want to interfere by adding profiles in their system.

---

### Post by Mockskin on 2007-03-13
Ahh, ok. Didn't catch the context. (Brain's in learning-common-lisp-land today)

---

