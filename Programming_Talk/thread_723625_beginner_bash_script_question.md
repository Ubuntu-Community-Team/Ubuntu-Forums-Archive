---
title: "beginner bash script question"
date: 2008-03-13
forum: Programming Talk
---

### Post by flowevd on 2008-03-13
hi

elementary q.

i'm playing with bash scripts and i'm totally new to them.
i thought I'd start by writing a short script to execute mpd then ncmpc.

This has proven very simple. However, when i quit ncmpc, mpd continues to run. how can i tell it to kill mpd on exit of the frontend?

after a little research i attempted the following

#! bin/bash/
mpd
ncmpc || mpd --kill

this doesn't work, natch.:-\"

please help a complete novice.
thanks!
flowevd

---

### Post by ruy_lopez on 2008-03-13
I don't know what mpd or ncmpc do. But bash scripts are usually begun with this:

eg "bash_file.sh"
```

#!/bin/bash

```

Then:
```

chmod +x bash_file.sh

```

To run:
```

./bash_file.sh

```

---

### Post by mssever on 2008-03-13
> **flowevd said:**
> #! bin/bash/
mpd
ncmpc || mpd --kill
What your code currently does:[LIST=1]
[*]Execute mpd. I'm guessing that this is a daemon?
[*]Execute ncmpc
[*]If ncmpc exits with a nonzero exit status (generally due to an error condition), then run mpd --kill. If you exit ncmpc normally, then it will exit 0 and mpd won't get killed.[/LIST]I think you're after something more like this:
```
#!/bin/bash
mpd
ncmpc
mpd --kill
```

---

### Post by Jeff24K on 2008-03-13
Error messages?

I'm not so sure your problem is related to bash scripting as much as it is the particular programs/processes you're trying to script, but...

```
#! bin/bash/
```

This should be

```
#! /bin/bash
```

You have a misplaced "/" that should be giving you a "bad command interpreter" errror.

```
mpd
```

mpd is a service or "daemon" that typically  gets started using the init script found in /etc/init.d. Trying to start it "manually" as a non-root user without having generated a working a config file named .mpdconf in your $HOME (or specifying one on the command line) should get you a warning about creating a PID file, setting GID, or the like.

```
ncmpc || mpd --kill
```

This sort of command chaining should be done using the "&&" operator. The"||" is a conditional OR test, and to be honest I'm not sure if it "waits" to execute the right side until the left side finishes. If it doesn't then "mpd --kill" will run and the daemon will die leaving ncmpc reading dead air or some such other foolishness. ;)

FWIW, I made the following changes to your script and created a user copy of .mpdconfig that pointed to my music collection in ~/Music, and everything appears to work just dandy. mpd starts, ncmpd opens and makes all the right noises, and when you exit ncmpd the mpd dameon is shut down properly...

```
#! /bin/bash
mpd
ncmpc && mpd --kill
```

---

### Post by flowevd on 2008-03-13
thank you, that works!! told you i was new :wink:

yes, it is a daemon, Music Player Daemon, which can be interfaced with via the pretty text-only frontend ncmpc.

is there any way of stipulating in the script that the commands be run in the terminal, rather than having to click on 'run in terminal' in the dialog box? If i just 'run' nothing happens...

flowevd

---

### Post by flowevd on 2008-03-13
thanks Jeff24K too, i was writing whilst you posted

---

### Post by mssever on 2008-03-13
> **Jeff24K said:**
> mpd is a service or "daemon" that typically  gets started using the init script found in /etc/init.d. Trying to start it "manually" as a non-root user without having generated a working a config file named .mpdconf in your $HOME (or specifying one on the command line) should get you a warning about creating a PID file, setting GID, or the like.I used mpd once as a normal user and didn't get a warning... But, since I only used it once, I might be wrong.

> This sort of command chaining should be done using the "&&" operator. The"||" is a conditional OR test, and to be honest I'm not sure if it "waits" to execute the right side until the left side finishes. If it doesn't then "mpd --kill" will run and the daemon will die leaving ncmpc reading dead air or some such other foolishness. ;)
The && operator runs the following command if the previous command's exit status is 0. The || command executes on a nonzero exit status. Obviously, you can't test the exit status until the process exits. You might be confusing && with &, which puts the process in the background. Neither && nor || is appropriate in this situation, even though the && will work in most (but not all) cases.

> **flowevd said:**
> is there any way of stipulating in the script that the commands be run in the terminal, rather than having to click on 'run in terminal' in the dialog box? If i just 'run' nothing happens... The preferred way is to make a .desktop file (similar to a Windows shortcut). You can find examples in /usr/share/applications, and you can find a spec on freedesktop.org. There's an option to run it in a terminal. (To look at .desktop files,  you'll have to do it through the terminal. Nautilus won't allow you to see the internals.)

I'm sure there's a way for the script to determine whether it's running in a terminal, but using a .desktop file is more flexible.

---

### Post by flowevd on 2008-03-13
> **mssever said:**
> 
 The preferred way is to make a .desktop file (similar to a Windows shortcut). You can find examples in /usr/share/applications, and you can find a spec on freedesktop.org. There's an option to run it in a terminal. (To look at .desktop files,  you'll have to do it through the terminal. Nautilus won't allow you to see the internals.)

thanks, I'll have a look at these...

---

### Post by flowevd on 2008-03-13
For the purposes of posterity, here's my new ncmpc.desktop file, which works...

```

[Desktop Entry]
Encoding=UTF-8
Version=0.11.2
Name=NCMPC
Comment=Music Player
Exec=sh ncm.sh
Icon=/usr/share/icons/gnome/scalable/mimetypes/audio-x-generic.svg
Terminal=true
Type=Application
Categories=Application;AudioVideo;Player;

```

this is brilliant. however, success throws up two more questions about terminal integration...

1. when i quite ncmpc with 'q', MPD 'kills' as intended. However, if I alt-f4 out of the terminal, i have to open another terminal to kill MPD. Is it possible to patch this up so quitting the terminal kills the Daemon?

2. can I change the window-list name - or even the icon - for the window thus opened? It's currently 'terminal' and a picture of a black screen. might i have to direct it to another script to start a special flavour of terminal?

---

### Post by flowevd on 2008-03-13
> **flowevd said:**
> 
2. can I change the window-list name - or even the icon - for the window thus opened? It's currently 'terminal' and a picture of a black screen. might i have to direct it to another script to start a special flavour of terminal?

sorted this one out: launch with

```

gnome-terminal --command="sh ncm.sh" --title="NCMPC Music Player"

```

all good... could the icon change too?

---

### Post by stroyan on 2008-03-14
gnome-terminal doesn't have an option to set an icon directly.
But you can specify a profile.
A profile can have both a command and an icon associated with it.
You set that up with the "Edit->Profiles..." menu item in gnome-terminal.
Then you start a gnome-terminal with a specific profile with a command like-
gnome-terminal --window-with-profile=NCMPC

---

### Post by mssever on 2008-03-14
You can also set the title from your script using terminal escape codes. Here, for example, is a wrapper around ping that I use which sets the title appropriately (I used to have major network trouble and would leave ping running constantly so I could monitor the situation easily): ```
#!/bin/bash

[[ $TERM =~ "xterm" ]] && echo -ne "\033]0;ping $@\007"
exec /bin/ping "$@"
```

(Note that $@ means all the command line arguments, separated by spaces. If in double quotes, eash argument is quoted separately.)

---

### Post by flowevd on 2008-03-14
i'll try em both.

thank you!

---

