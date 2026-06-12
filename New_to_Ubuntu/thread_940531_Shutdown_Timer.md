---
title: "Shutdown Timer"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Mad_Max_1412 on 2008-10-07
Guys,

Is there any application available for Ubuntu where you can tell the system to power down either after a certain amount of time or at a specific time?

Sometimes I am downloading some torrents and want to go to bed, but don't want it running all night, so I would like to have some application where I can say "Shut Down system at 1:00am" or "Shut Down system after 2 hours".

Thanks

---

### Post by neilengineer on 2008-10-07
To shut down in 60 minutes, use:
#sudo shutdown -h +60


Or considering "cron" for more complicated tasks.

---

### Post by ronnielsen1 on 2008-10-07
[http://micrux.net/?p=42](http://micrux.net/?p=42)
[http://www.computerhope.com/unix/ushutdow.htm](http://www.computerhope.com/unix/ushutdow.htm)
The following will tell you how to automate it
[http://stillstup.blogspot.com/2008/09/shutdown-timershutdown-timer.html](http://stillstup.blogspot.com/2008/09/shutdown-timershutdown-timer.html)

---

### Post by billgoldberg on 2008-10-07
To shutdown the computer at a fixed hour, lets say at 23:15h, use this command in the terminal:

```
sudo shutdown 23:15
```

To shutdown the system after x minutes, lets say 30, use this command in the terminal:

```
sudo shutdown +30
```

extra options:

add -r at the end of the command if you want the system to be rebooted instead of shutdown, it would look like this:

```
sudo shutdown 23:15 -r
```

To cancel the shutdown command use this:

```
sudo shutdown -c
```

---

### Post by Mad_Max_1412 on 2008-10-07
Thanks Everyone.  You've all been great.

---

### Post by Mad_Max_1412 on 2008-10-09
Guys,

Apologies, but I hadn't tested the suggestions given before my last post.

I have tried using

> sudo shutdown +1

and it brings up a message saying the system is coming down for maintenance in 1 minute.

Unfortunately it takes me to a non-gui message which says

> Recovery Menu

Resume -  Resume Normal Boot
dpkg -    Repair Broken Packages
root -    Drop to root shell prompt
xfix -    Try to fix X server

Ok   Cancel

So it's not actually shutting down the system.  

Regards

---

### Post by chaosdesigner on 2008-10-09
Why don't you just look at the help page, so just type:

```


shutdown --help


```

That should give you information on how to use it.

---

### Post by robert shearer on 2008-10-09
There is a package called "gshutdown" that you can install using Synaptic package Manager.
System=>Admin=>Synaptic
When this opens use the search function and type in gshutdown.
Once the search finds it then highlight it and right click. Choose Mark for installation.

Once it is installed close Synaptic and look for the app.(Might be in Admin or Applications=>System tools or Applications=>Accessories)

From memory it is a simple GUI timer where you can enter the shutdown time you want.

---

### Post by jken146 on 2008-10-09
```
sudo shutdown -h +60
``` will shut it down in 60 minutes.  The -h option should do the trick.

---

