---
title: "Ubuntu, to set a notification with notify-send"
date: 2020-11-19
forum: New to Ubuntu
---

### Post by dunivixs on 2020-11-19
Hello,
After having looking for sending a notification, I launched the command in my terminal : notify-send "Hello World" ; that's work
Then I tried to set a notification, like sending "Hello World" to tomorrow at 9 am.
For that I used *cron* : crontab -e
Then I added the line : * * 19 11 4 notify-send "Hello World"
But this one did not work, so I added this at the end for seeing if there was an error : >> /home/dunivixs/Desktop/cron.log 2>&1
The file is adding but empty.

I also tried this line : * * 19 11 4 touch /home/dunivixs/Desktop/file.txt
The file is created.

What I want is creating a notification established for another moment.

Thank you very much for you help

---

### Post by Holger_Gehrke on 2020-11-19
cron is started before the GUI and programs started by cron run outside the GUI-session and don't know what display to send their output to. Running GUI programs from cron is possible if you're using the crontab of the user logged into the GUI (**not **root's crontab) by prefacing the command with 'env DISPLAY=:0.0 ' (starting the program in an environment with the variable DISPLAY set to ':0.0' - that's the standard/default name for the local display; if you've got multiple X-sessions running or are using a remote X-server you'll need a different value). So that line in the crontab should be something like '* * 19 11 4 env DISPLAY=:0.0 notify-send "Hello World" ' or you could add a line to the crontab defining the DISPLAY-variable before the line(s) with commands that need it.

Holger

---

### Post by dunivixs on 2020-11-19
I tried what you said :  replace the line by * * 19 11 4 env DISPLAY=:0.0 notify-send "Hello World" 
That does not work but that works with 'touch file.txt'

After I launched in my terminal:  env | grep "DISPLAY" ; it replies : "DISPLAY=:0"

What do you suggest ?
Thanks

---

### Post by Holger_Gehrke on 2020-11-19
Sorry, wrong variable (and a slight mistake in my thinking). 'notify-send' does not actually display anything by itself, it just sends the notification via dbus to a notification daemon which displays it. To do this it needs to have the address of the bus (and doesn't care about the DISPLAY at all, you can remove that from the crontab line). You can find that address in the variable DBUS_SESSION_BUS_ADDRESS (usually 'unix:path=/run/user/1000/bus' ; the '1000' is the uid of the user as displayed by 'id'). So try this instead:
```

* * 19 11 4 /usr/bin/env DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus /usr/bin/notify-send 'Hello World'

```
(the absolute paths' to the executables are a good idea in general, especially if one isn't certain what is or isn't in the $PATH)

Holger

---

### Post by dunivixs on 2020-11-19
Nice,
What you said to me works very well, 
Thank you very much
It is just a little bit too complicate for me.

Dunivixs

---

### Post by ActionParsnip on 2020-11-20
Why do you want a cron'd notification? Is it like "take your medication" and so on?

---

