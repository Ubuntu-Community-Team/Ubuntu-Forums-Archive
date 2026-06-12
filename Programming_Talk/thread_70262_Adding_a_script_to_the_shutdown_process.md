---
title: "Adding a script to the shutdown process"
date: 2005-09-29
forum: Programming Talk
---

### Post by Zotova on 2005-09-29
Sorry if this is in the wrong section - it seemed the most relevant section to my question.

Anyhow, I have a laptop which I use in various places, some in which I do not want to have the volume very high. But I constantly forget to turn the volume down when I quit Ubuntu. So I have written a script which basically mutes the volume when it is run.

My question is basically what file should I add my script too or is there a program which will allow me to add custom startup/shutdown commands. (Similar to a Windows style startup folder)

---

### Post by adwait on 2005-09-29
I dunno about running scripts on shutdown, but if you want to run it on start up, add it to /etc/init.d

the use
```

sudo rcconf

```

Make sure you have set the execute permissions on that script.
Find your script name and check the box next to it (using space bar).

---

### Post by sas on 2005-10-23
Put your script in /etc/rc.d/rc0.d/ and call it KXXturnvoldown

where turnvoldown is your script name and xx is a number.

When the system is shutdown (aka init 0) it goes into /etc/rc.id/rc0.d/ and executes all scripts that have a name starting with K in the order of the numbers in the script names.

To have the script run on startup add it to /etc/rc.d/rc5.d/ and call it Sxxturnvoldown 

S is for start script, K is for kill script.

---

### Post by LordHunter317 on 2005-10-23
[QUOTE=sas]To have the script run on startup add it to /etc/rc.d/rc5.d/ and call it Sxxturnvoldown[/quote]This isn't redhat, default startup level is **2**.

And you need to link your shutdown script to runlevel 6 as well, to have it occur on reboot (not poweroff, they're distinct).

---

### Post by sas on 2005-10-23
So it is, I never noticed that.

Surely having the script run on reboot is pointless? unless he/she sets the computer to reboot whilst running from a volume place to a mute one or something.

I just set the volume control to mute and saved settings on logout, now I turn it up if I need it, but if not, it's ready muted.

---

### Post by majikstreet on 2005-10-23
[QUOTE=adwait]I dunno about running scripts on shutdown, but if you want to run it on start up, add it to /etc/init.d

the use
```

sudo rcconf

```

Make sure you have set the execute permissions on that script.
Find your script name and check the box next to it (using space bar).[/QUOTE]
I was just randomly trying that, and I noticed that it isn't installed on my system. Apt-get it first :P

---

