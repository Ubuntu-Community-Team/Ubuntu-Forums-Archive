---
title: "Brief system freeze and strange syslog msgs"
date: 2016-04-01
forum: New to Ubuntu
---

### Post by zephyr2 on 2016-04-01
Running 15.10 UbuntuMATE on a System76 laptop. I woke my machine from suspend, edited a few files in nano and a couple of simple 'diff' commands, and within 15 min. the system seemed to freeze (e.g., mouse didn't move, a help window opened but froze before completion). Within maybe 60 seconds, the freezing stopped. I tried to skim through /var/log/syslog, but I really don't know what I'm looking at. :confused: Did see a few curious phrases: "call trace" (which is maybe associated with a kernel panic?), references to sleeping CPUs, a message about a dependency failing for Suspend, but really I just don't know what's relevant. 

I imagine I should post lines here from my syslog; I tried looking for a command / set of instructions for easily copy/pasting select lines from a syslog to a gedit file--so I can do a find/replace in order to anonymize the log output--but came up empty handed. Surely there is a better way than copypasting one terminal screen at a time into gedit to grab the relevant lines for posting here?

ETA: happened again when I again tried to suspend the machine. Seems odd, since I 

(1) updated via System Updater yesterday (no reboot required)
(2) successfully suspended the machine last night
(3) successfully woke it once today before this issue became apparent

That said, I frequently do not reboot / shut down but just suspend the machine overnight.  Is that bad? A contributing factor to the present problem?

---

