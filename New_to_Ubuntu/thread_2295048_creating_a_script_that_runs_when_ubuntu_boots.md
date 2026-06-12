---
title: "creating a script that runs when ubuntu boots"
date: 2015-09-15
forum: New to Ubuntu
---

### Post by Baxter_Stockman on 2015-09-15
Hi, 

I am new to Ubuntu 14.04. I am trying to write a script that is being executed when ubuntu boots. 

so my script file gunicorn.sh looks like this 

> [COLOR=#000000]cd [/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]path[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]to[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]folder[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#00008B]with[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]manage[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]py[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#00008B]exec[/COLOR][COLOR=#000000] gunicorn [/COLOR][COLOR=#000000]--[/COLOR][COLOR=#000000]env DJANGO_SETTINGS_MODULE[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000]app[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]my_settings app[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]wsgi[/COLOR]

I made it excutable and now when I run it using this 
> [COLOR=#000000]./[/COLOR][COLOR=#000000]gunicorn[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]sh

[/COLOR]it works. Now I placed it into 

> /etc/init.d

and did this 

> sudo update-rc.d -f gunicorn.sh defaults

and I got this message 

> update-rc.d: using dependency based boot sequencing
insserv: warning: script 'gunicorn.sh' missing LSB tags and overrides

which I found out is not important. 

However, when I boot it doesn't work, it's not executing the script

---

### Post by TheFu on 2015-09-15
Look at the other scripts in the /etc/init.d/ directory. Notice they have start/stop/status/restart options.  Your script **must** support these too.

I did not validate the update-rc.d options used were correct.

---

### Post by JKyleOKC on 2015-09-16
It appears to me that /etc/init.d is not really the right place to be launching a user-written script. That folder is specifically intended for launching system services that are expected to run for the duration of a power-up session, and which will be controlled primarily by the system administrator using the "service" command.

What's more, it was essentially superseded quite a few years ago by the "upstart" boot system, which in its turn is being replaced by "systemd" integration.

For launching one-time scripts such as this one seems to be, the place to look is /etc/rc.local which defaults to a do-nothing script. It's supposed to be executed as the very last step of booting up, and you can insert calls to launch your own scripts -- or just the two lines of code that you posted -- immediately before the "exit 0" line that's at the end of the default version.

The newer init actions such as upstart and, I presume, systemd concentrate on doing as much as possible in parallel, so there's no longer any guarantee that rc.local will be the final action of initialization -- but it's still the place to put one-time-launch actions...

Hope this helps!

---

### Post by TheFu on 2015-09-16
I disagree with the use of rc.local.  /etc/init.d/ is the correct location - user written or not.
rc.local is a hack.

[https://www.debian.org/doc/debian-policy/ch-opersys.html](https://www.debian.org/doc/debian-policy/ch-opersys.html) - ref 9.3

Init is used to support the different runlevels. rc.local doesn't do that properly.

---

### Post by sandyd on 2015-09-16
To startup at boot automatically, see [here]("http://gunicorn-docs.readthedocs.org/en/latest/deploy.html#monitoring") for startup options including runit, upstart, supervisord, etc.

---

