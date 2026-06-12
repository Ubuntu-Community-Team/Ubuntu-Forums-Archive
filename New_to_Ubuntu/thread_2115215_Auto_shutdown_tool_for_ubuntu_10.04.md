---
title: "Auto shutdown tool for ubuntu 10.04"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-02-12
Hi,

I need a tool which automatically shutdown the system in specified time with a popup of warning message.

kindly refer some best tool works in ubuntu.

---

### Post by Frogs Hair on 2013-02-12
Gshutdown is worth a a try but only works with Gnome 2 releases  you will be looking for a replacement if you upgrade in April when 10.04 reaches EOL.

---

### Post by GameX2 on 2013-02-12
Just wondering: is the end-of-life date (Not the month, the day random, or fixed?  It sound pretty random:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I'm using 12.04, but out of curiosity, assuming I'm still using 11.04 one month before end-of-line, does any popup show up to warn me I should upgrade, or not?

---

### Post by tgalati4 on 2013-02-12
Open a terminal:

```
man shutdown
man crontab
```

Lots of tutorials around on how to set up *crontab* with a *shutdown* command.  You include the message as one of the *shutdown* arguments.  You can use the *wall* command to send an earlier message or use one of the notify commands like *notify-send*.

---

### Post by sudodus on 2013-02-12
Try according to this link

[COLOR=Red][http://ubuntuforums.org/showthread.php?t=2073106](http://ubuntuforums.org/showthread.php?t=2073106)[/COLOR]

---

### Post by pmohankumar on 2013-02-14
Hi,

pls give a script to brings up a popup text mes like this " system will shutdown in 5 mins, Kindly close all your applications. Go safe to home" and command to set in cronjob to execute that script.

i planned to set like this in root user:

55 21 * * * (command or exec file path)
00 22 * * * /sbin/shutdown -h now

---

### Post by sudodus on 2013-02-14
> **pmohankumar said:**
> Hi,

pls give a script to brings up a popup text mes like this " system will shutdown in 5 mins, Kindly close all your applications. Go safe to home" and command to set in cronjob to execute that script.

i planned to set like this in root user:

55 21 * * * (command or exec file path)
00 22 * * * /sbin/shutdown -h now
Try this one for the message from terminal
```
/usr/bin/notify-send -t 15000 'shutdown in 5 min !!!'
```

To run it from cron you may need a whole script according to this link

[[COLOR="Red"]http://superuser.com/questions/342626/notify-send-to-other-user-on-the-same-system[/COLOR]]("http://superuser.com/questions/342626/notify-send-to-other-user-on-the-same-system")

---

### Post by pmohankumar on 2013-02-14
Hi,

when i try to execute the following command i got error as 'commond not found'.

 /usr/bin/notify-send -t 15000 'shutdown in 5 min !!!'

Pls find the attachment.

---

### Post by sudodus on 2013-02-14
> **pmohankumar said:**
> Hi,

when i try to execute the following command i got error as 'commond not found'.

 /usr/bin/notify-send -t 15000 'shutdown in 5 min !!!'

Pls find the attachment.

You need to install the package containing it if you don't have it already.

```
sudo apt-get install libnotify-bin
```

I found that the plain command works well from a terminal window, but not from cron. You probably need to

- save the script from the link in my previous post to a file,
- modify it to print the message you want,
- make it executable and
- call that file with the full path from ```
sudo crontab -e
```

---

### Post by sudodus on 2013-02-14
I did not manage to make it run as root (with sudo crontab), but it works like this with your user's crontab

```
crontab -e
```
Add this line to test every minute
```
* * * * * /path-to-script/script4cron
```
Add this line to run at 21:55
```
55 21 * * * /path-to-script/script4cron
```

Where you need to have the actual path to the script and the script can be something like this.
```

#!/bin/sh

DISPLAY=":0"
export DISPLAY
header="Go to bed"
message="it's already $(/bin/date "+%H:%M")"

#/bin/echo -e "$header\n\n$message" |/usr/bin/wall -n
/usr/bin/notify-send "$header" "$message" -t 36000
/usr/bin/xterm -hold -display :0 -e /bin/echo -e "$header\n\n$message"

```
You need to make the script executable.

Finally, you can choose between xterm (which will stay until you close it) and a notify message (which will go away after a few seconds).

An alternative is wall, that can be sent from root (created by sudo crontab -e) and to everybody logged in, but its message will be shown only in terminal windows.

---

### Post by pmohankumar on 2013-02-15
Thanks sudodus and i am really thankful to this ubuntuforum.
It worked for me.

One query: 
shutdown command will only execute as root, i am right?

---

### Post by sudodus on 2013-02-15
> **pmohankumar said:**
> Thanks sudodus and i am really thankful to this ubuntuforum.
It worked for me.

One query: 
shutdown command will only execute as root, i am right?
Yes, that's right. So you should enter it to cron's table with
```
sudo crontab -e
```

while the other command, which sends the notification, will only execute for the logged in user. So you should enter it to cron's table with
```
crontab -e
```

---

