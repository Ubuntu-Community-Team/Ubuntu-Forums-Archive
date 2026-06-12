---
title: "Why doesn't my crontab work"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-10-23
crontab -e gives the following
```
* * * * *     export DISPLAY=0 && /usr/bin/gnome-terminal
```
It's just a proof of concept. As I understand it, this should open a terminal every minute. It does nothing as far as I can tell. crontab seems extremely useful, I can think of hundreds of ways it would make my life easier but I can't figure it out. Any help is appreciated.

---

### Post by Bölvaður on 2008-10-23
I have never used it, but arent you missing some time interval parameters in front of your code?

---

### Post by JohnGalt131 on 2008-10-23
> **Bölvaður said:**
> I have never used it, but arent you missing some time interval parameters in front of your code?

# +---------------- minute (0 - 59)
# |  +------------- hour (0 - 23)
# |  |  +---------- day of month (1 - 31)
# |  |  |  +------- month (1 - 12)
# |  |  |  |  +---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
  *  *  *  *  *  command to be executed
* means every minute, every hour, etc.

i think...

---

### Post by Sarmacid on 2008-10-23
Did you restart the service after editing the crontab?
```
/etc/init.d/cron restart
```

---

### Post by JohnGalt131 on 2008-10-23
> **Sarmacid said:**
> Did you restart the service after editing the crontab?
```
/etc/init.d/cron restart
```

I tried just now. I waited a few minutes and nothing. Also I'd rebooted several times since initially modifying it.

---

### Post by alphaniner on 2008-10-23
Try something that doesn't require interaction with the gui.  Like 'dmesg > ~/crontab.ent.broke'

---

### Post by JohnGalt131 on 2008-10-23
> **alphaniner said:**
> Try something that doesn't require interaction with the gui.  Like 'dmesg > ~/crontab.ent.broke'

that worked.
Would it be better to have a script somewhere and just have the crontab execute that?

---

### Post by Sarmacid on 2008-10-23
> **alphaniner said:**
> Try something that doesn't require interaction with the gui.  Like 'dmesg > ~/crontab.ent.broke'

I'd try with
```
echo "`date`" >> ~/crontest.txt
/etc/init.d/cron restart
```

Then check the file to see if it is updated.

---

### Post by JohnGalt131 on 2008-10-23
> **Sarmacid said:**
> I'd try with
```
echo "`date`" >> ~/crontest.txt
/etc/init.d/cron restart
```

Then check the file to see if it is updated.

I updated my crontab to execute the particular script I wanted it to run.  In the process manager I could see that it was running only the zenity gui in the script never opened.

---

### Post by bodhi.zazen on 2008-10-23
I think your display is off.

It should be :0 not 0

```
* * * * *     export DISPLAY=**[COLOR=red]:[/COLOR]0** && /usr/bin/gnome-terminal
```

---

### Post by alphaniner on 2008-10-23
You could try it, but I don't think it would work.  I think crontab is for some reason unable to interact with the userspace without some special settings.

---

### Post by MrWES on 2008-10-23
Don't you need the user in there?

* * * * * [username] export DISPLAY=0 && /usr/bin/gnome-terminal

---

### Post by alphaniner on 2008-10-23
There are different crontabs for every user, and when you run crontab -e you edit your own.

---

### Post by JohnGalt131 on 2008-10-23
> **bodhi.zazen said:**
> I think your display is off.

It should be :0 not 0

```
* * * * *     export DISPLAY=**[COLOR=red]:[/COLOR]0** && /usr/bin/gnome-terminal
```

Still nothing

---

### Post by bodhi.zazen on 2008-10-23
give it a command to run.

gnome-terminal -e /bin/bash

---

### Post by The Cog on 2008-10-23
Feed the output to a log file. I suspect it's not hooking up to the display, but I don't understand X well enough to know how to fix it.
```
* * * * * export DISPLAY=:0 && /usr/bin/gnome-terminal >> /home/username/cron.log 2>&1 &
```
I'm not sure that ~ expands properly under cron so I suggest using the full pathname.

---

### Post by JohnGalt131 on 2008-10-24
> **The Cog said:**
> Feed the output to a log file. I suspect it's not hooking up to the display, but I don't understand X well enough to know how to fix it.
```
* * * * * export DISPLAY=:0 && /usr/bin/gnome-terminal >> /home/username/cron.log 2>&1 &
```
I'm not sure that ~ expands properly under cron so I suggest using the full pathname.

cannot open display: 
Run '/usr/bin/gnome-terminal --help' to see a full list of available command line options.

---

### Post by bluefrog on 2008-10-24
you must make sure about your display.

```

env | grep DISPLAY

```

will give you your exact display.

cron works without problem with the command you wrote if you are using the correct display.

---

### Post by JohnGalt131 on 2008-10-24
> **bluefrog said:**
> you must make sure about your display.

```

env | grep DISPLAY

```

will give you your exact display.

cron works without problem with the command you wrote if you are using the correct display.

DISPLAY=:0.0 which is what is in my crontab file.

---

### Post by bluefrog on 2008-10-24
```
* * * * * export DISPLAY=:0.0 && /usr/bin/gnome-terminal

```

does not work?

2 minutes went away, and I have 2 new terminals opened.

---

### Post by JohnGalt131 on 2008-10-24
> **bluefrog said:**
> ```
* * * * * export DISPLAY=:0.0 && /usr/bin/gnome-terminal

```

does not work?

2 minutes went away, and I have 2 new terminals opened.

I have copied and pasted exactly what you have and restarted the daemon and still nothing after a few minutes

---

### Post by JohnGalt131 on 2008-10-24
If I change it to ```
* * * * * export DISPLAY=:0.0 && /usr/bin/gnome-terminal --help > /home/user/.outtest
```

I get :

```
Usage:
  gnome-terminal [OPTION...] GNOME Terminal Emulator

Help Options:
  -?, --help                                      Show help options
  --help-all                                      Show all help options
  --help-gtk                                      Show GTK+ Options
  --help-bonobo-activation                        Show Bonobo Activation options
  --help-gnome                                    Show GNOME options
  --help-gnome-session                            Show session management options

Application Options:
  -e, --command                                   Execute the argument to this option inside the terminal.
  -x, --execute                                   Execute the remainder of the command line inside the terminal.
  --window                                        Open a new window containing a tab with the default profile. More than one of these options can be provided.
  --window-with-profile=PROFILENAME               Open a new window containing a tab with the given profile. More than one of these options can be provided.
  --tab                                           Open a new tab in the last-opened window with the default profile. More than one of these options can be provided.
  --tab-with-profile=PROFILENAME                  Open a new tab in the last-opened window with the given profile. More than one of these options can be provided.
  --window-with-profile-internal-id=PROFILEID     Open a new window containing a tab with the given profile ID. Used internally to save sessions.
  --tab-with-profile-internal-id=PROFILEID        Open a new tab in the last-opened window with the given profile ID. Used internally to save sessions.
  --role=ROLE                                     Set the role for the last-specified window; applies to only one window; can be specified once for each window you create from the command line.
  --show-menubar                                  Turn on the menubar for the last-specified window; applies to only one window; can be specified once for each window you create from the command line.
  --hide-menubar                                  Turn off the menubar for the last-specified window; applies to only one window; can be specified once for each window you create from the command line.
  --full-screen                                   Set the last-specified window into fullscreen mode; applies to only one window; can be specified once for each window you create from the command line.
  --geometry=GEOMETRY                             X geometry specification (see "X" man page), can be specified once per window to be opened.
  --disable-factory                               Do not register with the activation nameserver, do not re-use an active terminal
  --use-factory                                   Register with the activation nameserver [default]
  --startup-id                                    ID for startup notification protocol.
  -t, --title=TITLE                               Set the terminal's title
  --working-directory=DIRNAME                     Set the terminal's working directory
  --default-working-directory=DIRNAME             Set the default terminal's working directory. Used internally
  --zoom=ZOOMFACTOR                               Set the terminal's zoom factor (1.0 = normal size)
  --active=ZOOMFACTOR                             Set the last specified tab as the active one in its window
  --display=DISPLAY                               X display to use

```
in the .outtest file

---

### Post by bluefrog on 2008-10-24
so it does work but not on your screen. sorry don't know how to solve that then.

---

### Post by JohnGalt131 on 2008-10-25
I found that if I run
```
xhost +
```
it will work. However, I don't know if this is safe or not. Is it?

---

### Post by bodhi.zazen on 2008-10-25
xhost is less then ideal (although I do not have a better option for you at the moment).

See here for a brief explanation :

[http://laurentschneider.com/wordpress/2007/03/xhost-is-a-huge-security-hole.html](http://laurentschneider.com/wordpress/2007/03/xhost-is-a-huge-security-hole.html)

I guess I would ask, why are you running a terminal ? Why not just add your command to crontab or test with an alternate X application such as xeyes ?

Also I suggest you try running your commands for a your console (Ctrl-alt-F1)

from there you will get error messages.

You can start applications, including gnome-terminal, with the --display flag as well. So I can start a terminal WITHOUT exporting the display with :

```
gnome-terminal --display=:0.0
```Last suggestion, check ownership and permissions of ~/.Xauthority. If needed change it from root to your user

```
sudo chown user.user ~/.Xauthority
```where user = you log in name.

---

### Post by JohnGalt131 on 2008-10-25
> **bodhi.zazen said:**
> xhost is less then ideal (although I do not have a better option for you at the moment).

See here for a brief explanation :

[http://laurentschneider.com/wordpress/2007/03/xhost-is-a-huge-security-hole.html](http://laurentschneider.com/wordpress/2007/03/xhost-is-a-huge-security-hole.html)

I guess I would ask, why are you running a terminal ? Why not just add your command to crontab or test with an alternate X application such as xeyes ?

that command was just a proof of concept. I will, however be running an rsync script and will be wanting the output in a terminal.

---

### Post by bodhi.zazen on 2008-10-25
While you were typing, I was busy adding a little to my response :twisted:

Personally I would put the output in rsync either into a file (using tee if necessary) or display it with something like xmessage or zenity rather then opening a terminal.

---

### Post by JohnGalt131 on 2008-10-25
> **bodhi.zazen said:**
> While you were typing, I was busy adding a little to my response :twisted:

Personally I would put the output in rsync either into a file (using tee if necessary) or display it with something like xmessage or zenity rather then opening a terminal.

I would rather use zenity list, but I can't figure out how to make the output stay at the current line. I have to continuously scroll down to see what is happening at that instant. Do you know how to make it display the bottom/most recent line; and if I want I can scroll up to see what's already been done?

---

### Post by detoj on 2008-11-12
I had a similar problem with my crontab not working, but post number 12 in [this thread]("http://ubuntuforums.org/showthread.php?t=952452") had a workaround that seems to be working for me.  It might be worth giving it a shot if you're still having problems.

---

