---
title: "Howto: Get a new mail notification by you thinklight"
date: 2006-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by magisterludi on 2006-03-27
This howto assumes that you are using gkrellm. 
If you know any tool that fullfils the requirements stated at the end of
this how to let me now please.

What it does:
If you get new mail you will be notified by the thinklight of your thinkpad.
Then you may click on the gkrellm mail plugin button to open you mail programm
and read your mail. If you close your mail programm the thinklight will be turned of. This solution will turn on your thinklight again when you resume from suspend since it is turned off when suspending.

This should work with any standard breezy kernel.

First we have to setup writing permissions to enable/disable the light for your user:
Create a the file /etc/init.d/setlightperms as root:
```

#!/bin/sh
chown root:yourgroupname /proc/acpi/ibm/light
chmod g+w /proc/acpi/ibm/light

```
make it executeable```
sudo chmod +x /etc/init.d/setlightperms
```
and link it from you default runlevel:
```
ln -s /etc/init.d/setlightperms /etc/rc2.d/S99setlightperms
```

Go to you gkrellm preferences (right click on gkrellm)
Set up your maildirs in gkrellm. If you have many edit ~/.gkrellm2/user-config
directly (it is easier to copy&paste then the gkrellm interface)

As mail notification programm use the following script which turns on you thinklight on
any new mail. If you remove the comments the thinklight will blink instead
of being just turned on.
I put it into ~/scripts/ and called it maillight.pl (make it executeable)
```

#!/usr/bin/perl

for($runs=1; $runs<2; $runs++){
system("echo on > /proc/acpi/ibm/light");
#system("sleep 1");
#system("echo off >/proc/acpi/ibm/light");
#system("sleep 1")
system("touch ~/.gotnewmail.cookie"); 
#the last line is about to know if the light should be turned on after
#suspend
}

```

As script to read mail use this which I called ownmutt.sh since I use mutt
```

#!/bin/bash
aterm -e ~/scripts/m  #enter your favourite terminal here

```

The m script looks as follows:
```

#!/bin/bash
mutt&&
echo off >/proc/acpi/ibm/light
if [ -f ~/.gotnewmail.cookie ]
then
rm ~/.gotnewmail.cookie
fi

```
It calls mutt. Turns off the light when mutt is closed and removes the indication file.
That's enoght for gkrellm.

Now append follwing to you /etc/acpi/resume.sh
```

if [ -f /home/olliwolli/.gotnewmail.cookie ]
then
echo on >/proc/acpi/ibm/light
fi

```
This will turn on light after suspend if there still is new mail.

So this all works together. If you have a better solution, like using more basic
tools please let me know.

Here the requirements for an alternative tool:

-runs fine with any wm (for me especially larswm)

-supports recursive checking of multiple maildirs

-supports executing a command when new mail arrived

-has buttons for every maildir you defined so you can execute a command by clicking on the button (use case example: I have new mail in my university folder, I get notified by the programm that there is new mail. I click on a button and mutt is opened in a terminal with the correct maildir)

(maybe a number how many new mails, it would be fancy to have the subject displayed, but I don't know any tools  accomplishing that. mail-notification of gnome does this but you can only define one command for all maildirs and it only works with gnome)

---

