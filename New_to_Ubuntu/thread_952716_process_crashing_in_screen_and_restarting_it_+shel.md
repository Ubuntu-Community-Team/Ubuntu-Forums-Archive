---
title: "process crashing in screen and restarting it? +shell script?"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by iason on 2008-10-19
I run a game server which likes to crash alot.  The server runs in a screened environment and I am wondering what the best way to write a quick shell script to check for the process and run it back in the screen if it crashes, then run that batch script in a cronjob.

Im not sure if you can bring the screen backup and run a command in it, or is it just best to kill all screens and restart it.

this is what i was thinking:

ls | grep ac_server
if (ac_server = 1) exit

else
killall screen
screen | ./run.sh

---

