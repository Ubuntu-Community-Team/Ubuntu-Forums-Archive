---
title: "HOW TO: Create a tty user who's only purpose is to display a log file"
date: 2008-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Co.Sinecure on 2008-04-14
This how-to describes the creation of a severely restricted user, that is locked into viewing a particular log file.

[I][SIZE=2]This is a bit of a pet project, tied to the log file of a jabber bot that I've created. 
The Jabber bot tracks the arrival times of our local coffee van which comes every morning, and attempts to estimate the time it should arrive based on historical data.
I'm going on leave from work for a few of weeks, so I decided to allow some co-workers watch over my coffee-bot, and allow them to see its status via the logs. I did not particularly want to leave my machine completely open to them, while trustworthy, they would never miss a pranking opportunity![/SIZE]

[/I]Basically the idea is the user is given a shell that is actually a bash script that runs a watch and tail command.

Written using Feisty 7.04

[SIZE=3]**Step 1: **[/SIZE]
Write the script that will be executed
```
sudo vim /usr/bin/coffee-watch 
```> 
#! /bin/bash

watch tail -n 80 /home/cosinecure/etc/jabber-bot/logfile.log
What this script does is call the watch command, which is a program that executes its parameters periodically. It defaults to 2 seconds, and so every 2 seconds it will run [FONT=Courier New]tail -n 80 /.../logfile.log[/FONT]. This echos the last 80 lines of the logfile to the terminal.

```
sudo chmod +x /usr/bin/coffee-watch
```[SIZE=3]**Step 2:**[/SIZE]
Set the script as a shell-able command
```
sudo vim /etc/shells 
```Add the line
> 
/usr/bin/coffee-watch
[SIZE=3]**Step 3:**[/SIZE]
Create the user.
Either use the menu System > Administration > Users and Groups
Or the command line [SIZE=1]*I didn't do this way so not sure if this is all you need..[/SIZE]
```
sudo adduser --shell /usr/bin/coffee-watch
```Important thing to remember is that your user has their shell set to ```
/usr/bin/coffee-watch
```[SIZE=3]**Step 4:**[/SIZE]
Make sure your log file and the *path* to the log file has the right permissions! I actually added the user to my username's group so that it could access that file.

[B][SIZE=3]Step 5: Test it![/SIZE]
[/B]Switch to tty 1 and attempt to log in
```
Ctrl+Alt+F1
```[B][SIZE=3]Step 6:[/SIZE]
[/B]Leave me feedback if you used this and any problems/ideas you had!

I apologise for the lack of screenshots. Didn't have long to write this up!

---

### Post by wootah on 2008-05-22
Why not use *tail -f* so that as the file grows, it just updates the screen?

Also, what if the user presses CTRL-C? :)

---

### Post by Co.Sinecure on 2008-05-22
> **wootah said:**
> Why not use *tail -f* so that as the file grows, it just updates the screen?

Also, what if the user presses CTRL-C? :)

*tail -f* or *-F* didn't work for me.. I looked up *man tail* and I get what you mean but it wasn't printing out anything when the log was being added to.

Ctrl-C defiantly logs out the user completely :) yes that occurred to me while building it!
While bash is running the script, there's no command line actually accessible from the users' perspective, so there's nowhere to go except out completely.

---

