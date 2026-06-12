---
title: "Automatic Disk Check - counting boots"
date: 2007-01-28
forum: Programming Talk
---

### Post by musther on 2007-01-28
A while ago I developed a script to set up disk checks and then turn off the computer, this meant users could avoid the forced boot up check, see the wiki page at:
[https://wiki.ubuntu.com/fsckdown](https://wiki.ubuntu.com/fsckdown)

I also wrote an automated version for my own use, it just checks the number of times I log in and then after 25 it asks me and then sets up the shut down checks.  

I believe this would be much more useful if it counted boots rather than logins, for obvious reasons.  At present the script creates a file /home/***/.fsckdown and stores a number in it, every time I log in the script it called and it checks the number and increments it etc.  

I actually need two solutions, firstly I need a place to store my count file which is writable by all users, and secondly I need some way to call the script every boot, and only once every boot.  

I've attached the current script.

Any suggestions welcome - Thanks.

---

### Post by moon2js on 2007-01-30
I've been looking for something like this script for a while. The auto disk check on startup never fails to happen only at times when I'm specifically need the computer.

The counting version of the script would be good for me because I won't remember to use the script to avoid the boot up surprise.

This is beyond the scope of your script, but I think it would be more user intuitive if there were another option for a special maintenance shutdown on that shutdown/log-off menu, showing how desperately the system needs the maintenance, so that every time you go to shut down, you'd see something like "25 boots till next disk check" or something like that.

Usually you aren't in a hurry to shut down and you can always have the computer do a 'maintenance shutdown' while you're washing up for bed.

Sorry I don't have any suggestions for your script though.

---

