---
title: "Why does Ubuntu shut down so &quot;brutally&quot;?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by kajman on 2008-11-30
When I shut down the system, and restart it applications like firefox 3 or vuze report that they were shut down improperly. As if I sent them a kill command, not closed "nicely". Is this always like that? What can I do to change it?

---

### Post by OrangeCrate on 2008-11-30
If I understood your question correctly, you should close Firefox and any other applications you have open prior to shutting down. That would alleviate the warnings you get when you boot up.

---

### Post by kajman on 2008-12-01
I know that, but I was wondering why isn't it done automatically as it was on XP for example. Is there a way to change the way in which Ubuntu behaves in that matter?

---

### Post by OrangeCrate on 2008-12-01
> **kajman said:**
> I know that, but I was wondering why isn't it done automatically as it was on XP for example. Is there a way to change the way in which Ubuntu behaves in that matter?

Not that I'm aware of.

Xfce, which is the WM for Xubuntu, does allow shutting down as you describe, but so far, I've never found a way to do it with Gnome which is the desktop for Ubuntu.

That would be nice. Hopefully, someone will come along with an answer for both of us...

---

### Post by unutbu on 2008-12-01
Perhaps try this:

Step 0: Run firefox3 and vuze. Open a terminal and type```

pkill firefox
pkill vuze
```

Are these programs terminated cleanly? If so, we are in business. If not, we'll have to fuss around a bit to learn the proper terminal commands. If the pkill commands don't work as desired, try
```

kill -s TERM $(pgrep firefox)
kill -s TERM $(pgrep vuze)
```

Step 1: Write a script that shuts down firefox3 and vuze cleanly
```

gksu gedit /etc/init.d/at_shutdown
```

```
#!/bin/bash
echo 'Shutdown script was executed at' $(date '+%Y-%m-%d %H:%M') > /root/at_shutdown.out
pkill firefox
pkill vuze

```
Replace the pkill commands if necessary (based on your experiment in step 0). Save the script. 

Make it executable:
```

sudo chmod 755 /etc/init.d/at_shutdown
```

Step 2: Inject the script into the shutdown process
```
sudo update-rc.d at_shutdown stop 01 0 .
```

That's it. When you shutdown, the at_shutdown script will be run. You can check that 
it really does run by looking inside the file "/root/at_shutdown.out" next time you reboot. You should see something like this:

```
Shutdown script was executed at 2008-12-01 08:39
```

---

### Post by kajman on 2008-12-03
I tried both commands with firefox, and both of them close it in the untidy way.
When I tried to use them to vuze I realized that there is no process of this name. There's no process named azureus or anything like it. I know that process named java (vuze is running on java) is responsible for taking care of vuze, but it may do some other things so I didn't try to close it.
How can I determine what process is directly related to vuze (or any other app that I started, but the process name is not the obvious one)?

---

### Post by nvteighen on 2008-12-03
I'd bet this is not Ubuntu, but the Linux kernel. One of the last steps the computer takes to be halted is precisely sending the KILL signal to any remaining process.

XP behaivor is a bit weird. Actually, that's one of the reasons why it needs more to shutdown than any GNU/Linux system.

---

