---
title: "SSH Logging with timestamp via bash script"
date: 2006-06-01
forum: Programming Talk
---

### Post by boozer_2 on 2006-06-01
I have a small script that ssh's to a host and tee's the output to a file for logging purposes.  How would one go about adding a timestamp in the log file which will show the time that the line printed on screen through the SSH session?

I'm using SSH to access a router.  When troubleshooting problems, a log becomes very helpful, however when i use the command in my script like this

ssh x@y.y.y.y | tee ~/logs/$logname

it logs all the output from the ssh session, however, I want to add a timestamp to each line or every x lines so I have a general idea when the output occurred.  How do I accomplish this?

---

### Post by yaaarrrgg on 2006-06-03
I thought that xterm had logging abilities built in, with the -l option.  Although this seems to be disabled in my version (for security reasons).

---

### Post by simplyw00x on 2006-06-04
Use "sed" to modify the stream that "tee" produces, replacing newline characters with a newline followed by the output of "date" and maybe a colon.

---

### Post by boozer_2 on 2006-06-12
Alright, I got this to work, however if I'm in an active ssh session, it doesnt echo the current line....  meaning i can't see any command i type until after i hit return... however, once I hit return the command executes and the date is prepended to the line.... is there a way to echo the currently displayed line and characters i'm typing in?

---

