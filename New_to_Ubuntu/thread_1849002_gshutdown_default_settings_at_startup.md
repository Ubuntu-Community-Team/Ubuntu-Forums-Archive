---
title: "gshutdown default settings at startup"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by blatzer on 2011-09-23
unbuntu 11.04
I have set gshutdown to start automatically.
It doesn't really start automatically, just brings up the startup screen for the program.

The default setting that is displayed at startup is "at date and time", but I would like this to be "after a delay".
In addition it would be nice if, let's say, 30 minutes were default.
And, if I forget to press "start", it would automatically start.
I have tried to find settings like this without success.
Is there any way to do this?

---

### Post by Chiel92 on 2011-09-23
> **blatzer said:**
> unbuntu 11.04
I have set gshutdown to start automatically.
It doesn't really start automatically, just brings up the startup screen for the program.

The default setting that is displayed at startup is "at date and time", but I would like this to be "after a delay".
In addition it would be nice if, let's say, 30 minutes were default.
And, if I forget to press "start", it would automatically start.
I have tried to find settings like this without success.
Is there any way to do this?

I suppose those defaults you mentioned are customizable in /usr/share/gshutdown/gshutdown.glade

---

### Post by blatzer on 2011-09-23
thank you for replying.

> **Chiel92 said:**
> I suppose those defaults you mentioned are customizable in /usr/share/gshutdown/gshutdown.glade

As suggested I searched  in  the above file for anything that looked like those buttons but found nothing referring to "after a delay".
Since I have not programmed in this language and if this is the only way I won't pursue this.

---

### Post by Chiel92 on 2011-09-24
> **blatzer said:**
> thank you for replying.



As suggested I searched  in  the above file for anything that looked like those buttons but found nothing referring to "after a delay".
Since I have not programmed in this language and if this is the only way I won't pursue this.

I will have a closer look. 
But could you explain why you would use gshutdown? I think the program shutdown fits to your needs. Although it is not a gui program but a commandline program.

---

### Post by blatzer on 2011-09-24
> **Chiel92 said:**
> I will have a closer look. 
But could you explain why you would use gshutdown? I think the program shutdown fits to your needs. Although it is not a gui program but a commandline program.

I have no problem using command-line when it's the only way.
Program shutdown seems to require  root. Also terminal procedure not as self-evident. For instance, if I want to extend the time for the session it is very easy to do with a graphic display as opposed to "how did I do this last time?'.

---

### Post by Chiel92 on 2011-09-24
> **blatzer said:**
> I have no problem using command-line when it's the only way.
Program shutdown seems to require  root. Also terminal procedure not as self-evident. For instance, if I want to extend the time for the session it is very easy to do with a graphic display as opposed to "how did I do this last time?'.

It seems that gshutdown is not so configurable. I could not get defaults working easily, so I suggest you use commandline, which is in this case user-friendly, in my opinion.

```
sudo halt
```
valid argument formats are +m, where m is the number of minutes to wait until shutting down and hh:mm which specifies the time on the 24hr clock.

If you want this to startup automatically, put it in your '.profile'.

---

### Post by blatzer on 2011-09-25
> **Chiel92 said:**
> It seems that gshutdown is not so configurable. I could not get defaults working easily, so I suggest you use commandline, which is in this case user-friendly, in my opinion.

```
sudo halt
```valid argument formats are +m, where m is the number of minutes to wait until shutting down and hh:mm which specifies the time on the 24hr clock.

If you want this to startup automatically, put it in your '.profile'.

Thank you for looking into this.

halt command does not have time option - just shuts down. Confirmed by  the description in "man halt", and trying your suggestion.

I will just continue to use gshutdown.

---

### Post by Chiel92 on 2011-09-25
> **blatzer said:**
> Thank you for looking into this.

no problem :)
> 
halt command does not have time option - just shuts down. Confirmed by  the description in "man halt", and trying your suggestion.


Sorry, I was confused. I always thought "halt" was literally the same as 'shutdown -h'. :) Never realized it was a different thing, lol. So I actually meant 

```
sudo shutdown -h
``` 
still with the same argument formats +m, where m is the number of minutes to wait until shutting down and hh:mm which specifies the time on the 24hr clock.

> I will just continue to use gshutdown.
Sure, if that's okay for you.

---

### Post by blatzer on 2011-09-26
> **Chiel92 said:**
> I.
If you want this to startup automatically, put it in your '.profile'.

Continuing  just for education.

 I  searched for .profile and found three files in the system.
I haven't figured out how to put any code into them.
Isn't this method replaced by Preferences>Startup Applications?

Also tried putting code for shutdown into Preferences>Startup Applications, but  without a terminal screen coming up how would you enter the password?

Perhaps shutdown can be altered so that is not restricted to root? 
I changed ownership of /sbin/shutdown but password still needed.

---

### Post by Chiel92 on 2011-09-26
> **blatzer said:**
> Continuing  just for education.

 I  searched for .profile and found three files in the system.
I haven't figured out how to put any code into them.
Isn't this method replaced by Preferences>Startup Applications?

Also tried putting code for shutdown into Preferences>Startup Applications, but  without a terminal screen coming up how would you enter the password?

Perhaps shutdown can be altered so that is not restricted to root? 
I changed ownership of /sbin/shutdown but password still needed.

I also encounter problems like that, i did not expect.
Now I'm getting interested :P

---

### Post by Chiel92 on 2011-09-26
If you want to shutdown your computer at a fixed time, this is what could help you:

[http://ubuntuforums.org/archive/index.php/t-473173.html](http://ubuntuforums.org/archive/index.php/t-473173.html)

---

### Post by Krytarik on 2011-09-26
How about this?:

[http://www.tuxgarage.com/2011/09/shutdown-timer-tool-for-linux.html](http://www.tuxgarage.com/2011/09/shutdown-timer-tool-for-linux.html)

And if you want to apply a default shutdown timer upon startup, you can just add it to "/etc/rc.local", like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

shutdown -h +30

exit 0
```Basically, just contributing to the fun and learning part here, as it does seem like GShutdown is fitting your needs better.

Greetings.

---

### Post by Chiel92 on 2011-09-27
> **Chiel92 said:**
> I also encounter problems like that, i did not expect.
Now I'm getting interested :P

The answer to these root problems has just been posted here:
[http://ubuntuforums.org/showthread.php?t=1850463&page=2](http://ubuntuforums.org/showthread.php?t=1850463&page=2)

So to overcome the root permission problems, you can modify the permissions of shutdown, just as you said earlier.

---

### Post by blatzer on 2011-09-27
Thank you for your reply too.

> **Krytarik said:**
> How about this?:

[http://www.tuxgarage.com/2011/09/shutdown-timer-tool-for-linux.html](http://www.tuxgarage.com/2011/09/shutdown-timer-tool-for-linux.html)

This works pretty good. I like the slider to set the time. There may be problems returning from suspend.
Also I would add warning when coming down.


And if you want to apply a default shutdown timer upon startup, you can just add it to "/etc/rc.local", like this:
  (code here)

No doubt about this one. No warning tho.

exit 0[/CODE]Basically, just contributing to the fun and learning part here, as it does seem like GShutdown is fitting your needs better.

Agreed.

.

---

