---
title: "Zenity popup for another user"
date: 2009-09-24
forum: Programming Talk
---

### Post by falconindy on 2009-09-24
Is it possible to create a popup with Zenity for another user? My goal is to give a quick report after a cronjob finishes (as root) for the user who's currently logged in (or I can identify them by name if need be). I understand that using prefixing zenity with "DISPLAY=:0.0" works if you're running the command for yourself, but I'm not sure how to identify and output to the display for another user.

---

### Post by unutbu on 2009-09-24
falconindy, 

You might try:

[php]#!/bin/bash
pids=$(pgrep -u "$1" gnome-panel)
for pid in $pids; do
        # find DBUS session bus for this session
        DISPLAY=$(grep -z DISPLAY \
                /proc/$pid/environ | sed -e 's/DISPLAY=//')
        DISPLAY=$DISPLAY \
            zenity --info --text 'Hi falconindy!'
done[/php]

If you call the script above test.sh, then you would run it like this:
```

test.sh falconindy
```

You might also be interesting in checking out the libnotify-bin package. It provides notify-send to display messages in the corner of your screen that can be set to disappear after a few seconds. I think they blend into the GNOME desktop a little nicer than zenity windows.

notify-send relies on the DBUS_SESSION_BUS_ADDRESS environment variable. When you run it from cron, this variable is typically not set. Moreover, if you run it as root, you'll need to set it to correspond to a different user. The following script performs that job:

alt-notify-send:
[PHP]#!/bin/sh
# Source: http://gnome-hacks.org/hacks.html?id=82
user=$1
pids=$(pgrep -u $user gnome-panel)
title=$2
text=$3
timeout=$4

if [ -z "$title" ]; then
        echo You need to give me a title >&2
        exit 1
fi
if [ -z "$text" ]; then
        text=$title
fi
if [ -z "$timeout" ]; then
        timeout=60000
fi

for pid in $pids; do
        # find DBUS session bus for this session
        DBUS_SESSION_BUS_ADDRESS=$(grep -z DBUS_SESSION_BUS_ADDRESS \
                /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//')
        # use it
        DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
            notify-send -u low -t $timeout "$title" "$text"
done[/PHP]

Then you can put stuff like this in your /etc/crontab (or root) crontab:
```

*/10 5-8   * 	 *   3   root alt-notify-send falconindy 'Reminder' 'Garbarge Day' 

```

---

### Post by falconindy on 2009-09-24
> **unutbu said:**
> falconindy, 

You might try:

[php]#!/bin/bash
pids=$(pgrep -u "$1" gnome-panel)
for pid in $pids; do
        # find DBUS session bus for this session
        DISPLAY=$(grep -z DISPLAY \
                /proc/$pid/environ | sed -e 's/DISPLAY=//')
        DISPLAY=$DISPLAY \
            zenity --info --text 'Hi falconindy!'
done[/php]If you call the script above test.sh, then you would run it like this:
```

test.sh falconindy
```You might also be interesting in checking out the libnotify-bin package. It provides notify-send to display messages in the corner of your screen that can be set to disappear after a few seconds. I think they blend into the GNOME desktop a little nicer than zenity windows.
Hmm, this works great if I modify it to run under the assumption that there's only 1 instance of gnome-panel for the user. If not, it just hangs. Even with multiple panels on my desktop, I still only see 1 instance of gnome-panel running for myself. Do you know of an scenario where a second instance of gnome-panel would be running? Even if there was a second instance, wouldn't using either one to find the display work?

Also, while this works from a command line (in the modified state), it doesn't work from cron. I noticed that the result placed into $DISPLAY is the same :0.0 that I had been playing around with...

The windows created by libnotify-bin **are** much nicer. However, this is going to show output (tail of a log file) for a backup script that runs overnight, so a temporary window will be missed by the user. 

That said, this isn't absolutely necessary because said user has cron setup to email him anything written to standard output. I figured it might be a nice touch for him to see the relevant log every morning without having to go looking for it. I'm also not bent on using Zenity. If there's another elegant (but simple) solution that I've overlooked, then I'm interested.

Thanks, I appreciate your time.

---

### Post by geirha on 2009-09-25
You could perhaps do it another way. Having the users themselves decide whether to get the report displayed or not. You could for example run the following script (automatically when logging in): ```
#!/bin/sh
echo "$DISPLAY" > ~/.inform_me

```

Then in your cron-script read .inform_me from all homedirs, and run zenity on those displays.

```
for file in /home/*/.inform_me; do
  DISPLAY=$(<"$file") zenity --info ... &
done

```

EDIT: On second thought though, this is a bad idea as you'll have to make sure the file gets deleted when you log out, and if that doesn't happen, you'll be running many zenitys, and probably on the same display. If only one user should recieve this report at any given time though, having everyone write to the same file may be an option. E.g. /tmp/inform_me instead. And possibly also add the PID of the gnome-session, so you can check if it's actually running.

---

### Post by unutbu on 2009-09-25
Like what geirha suggested, perhaps it would be better for the user to 
control the display of the log file.

If you install the incron package, you can monitor the directory that contains the log file, and run a script or command whenever a file in that directory gets modified. For example, putting something like this in your "incrontab"
```

/path/to/log/directory IN_CLOSE_WRITE xdg-open $#
```
will run "xdg-open" on the file that has been modified. 

xdg-open will open the log file with the user's preferred text editor.

PS. notify-send is probably not the right tool for displaying log files since logs tend to be long, and the notify-send window does not provide scrollbars as far as I know.

---

### Post by falconindy on 2009-09-25
> **unutbu said:**
> Like what geirha suggested, perhaps it would be better for the user to 
control the display of the log file.

If you install the incron package, you can monitor the directory that contains the log file, and run a script or command whenever a file in that directory gets modified. For example, putting something like this in your "incrontab"
```

/path/to/log/directory IN_CLOSE_WRITE xdg-open $#
```will run "xdg-open" on the file that has been modified. 

xdg-open will open the log file with the user's preferred text editor.

PS. notify-send is probably not the right tool for displaying log files since logs tend to be long, and the notify-send window does not provide scrollbars as far as I know.
Provided he's willing to use incrontab, this will be a very workable solution.

Just going to mark this solved. Thanks for your help, both of you.

---

