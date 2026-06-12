---
title: "Looking for popup command"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by bustard on 2012-05-28
Is there a command I can run that will create a popup using whatever
text I entered in the parameter?

I would then run it in a cron job, or run it in a script called by
the cron job, to pop up messages at certain times.

I can not use kalarm because I refuse to have akonadi cluttering
up my hard drive, since I am running gnome and using only two kde
programs. But kalarm doesn't work unless akonadi is running.

I figured a little popup program or command would work in the place
of kalarm but there does not seem to be anything.

Thanks for any advice.

---

### Post by hakermania on 2012-05-28
Hey, have you tried zenity?
There are a couple of good references in the web:
[http://linuxlibrary.org/command-line/zenity-simple-gui-creation-tool/](http://linuxlibrary.org/command-line/zenity-simple-gui-creation-tool/)
[http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity](http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity)
You can also look the man page of zenity
```

man zenity

```

---

### Post by Azdour on 2012-05-28
Hi,

You may also want to look at notify-osd:

[https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)
[http://www.barregren.se/blog/pop-notification-command-line](http://www.barregren.se/blog/pop-notification-command-line)

---

### Post by bustard on 2012-05-28
Thank you for the replies. Zenity looks powerful and I can get it to display messages, but it waits until the user clicks on the OK button in the message. I don't want to have that happen whenever a popup occurs.

notify-send is exactly what I want.

But, neither utility will display a popup when I run them as a cron job. I can have cron run a script which runs notify-send, and the script works if I run it myself from a terminal, but when the script is called by the cron job, there is no popup.

I made sure to specify the full path to the script.

---

### Post by hakermania on 2012-05-28
> **bustard said:**
> Thank you for the replies. Zenity looks powerful and I can get it to display messages, but it waits until the user clicks on the OK button in the message. I don't want to have that happen whenever a popup occurs.

notify-send is exactly what I want.

But, neither utility will display a popup when I run them as a cron job. I can have cron run a script which runs notify-send, and the script works if I run it myself from a terminal, but when the script is called by the cron job, there is no popup.

I made sure to specify the full path to the script.

I don't have experience with cron jobs, but according to this [http://ubuntuforums.org/archive/index.php/t-105250.html](http://ubuntuforums.org/archive/index.php/t-105250.html) you will have to put 'DISPLAY=:0 &&' infront of your script to run a Graphical User Interface application!

---

### Post by bustard on 2012-05-28
> **hakermania said:**
> I don't have experience with cron jobs, but according to this [http://ubuntuforums.org/archive/index.php/t-105250.html](http://ubuntuforums.org/archive/index.php/t-105250.html) you will have to put 'DISPLAY=:0 &&' infront of your script to run a Graphical User Interface application!

Thank you, that worked. Here is the cron entry:
32 13 * * * export DISPLAY=:0 && /home/joe/bin/test3

Test3 ran the notify-send command and this time it popped up.

---

### Post by bustard on 2012-05-28
To follow up: you can use the -t milliseconds switch to keep the popup displaying for as long as you want. This might be useful if you run it via cron and may be away from the pc.

Here is an example of the cron command
11 15 * * * export DISPLAY=:0 && notify-send -t 10800000 'Some Reminder'

The -t 10800000 will keep the popup displayed for 3 hours.

---

### Post by hakermania on 2012-05-28
Please mark the thread as solved!

---

