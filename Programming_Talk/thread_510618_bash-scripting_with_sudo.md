---
title: "bash-scripting with sudo"
date: 2007-07-26
forum: Programming Talk
---

### Post by indytim on 2007-07-26
I'm developing a small bash script.  The script will run a partimage partition archive.  I need to run at the sudo level.  My question is what is the protocol for invoking sudo level in a bash script without going interactive prompt for a password?

Once this script is working, I want to move it to a scheduled cron job.

Many Thanks,

IndyTim

---

### Post by NeuralEskimo on 2007-07-26
Here is a different solution. Don't put sudo calls in your script, instead run the script using sudo while developing it and then add the script to /etc/cron.daily (or whatever) or root's crontab. In this way, the script runs as root and you won't need a complex skirting of sudo or passwords stored on the disk (readable by others). I hope this helps...

---

