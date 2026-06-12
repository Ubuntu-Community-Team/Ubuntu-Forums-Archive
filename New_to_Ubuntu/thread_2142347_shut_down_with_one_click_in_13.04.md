---
title: "shut down with one click in 13.04?"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by bob brazie on 2013-05-05
I am wondering if I can make a desktop icon with a command that will shut down 13.04 with one click and not need to use the three click method that is needed now. 

Thanks in advance. Bob.

---

### Post by Impavidus on 2013-05-05
In Xubuntu there is a one-click way using a big red button in the corner of the screen. Best not to put it in the same corner as the "close window" button.

---

### Post by bob brazie on 2013-05-05
Thanks but I am usiing ubuntu 13.04. And if it wasn't clear as to what I was asking I would like to shut the whole computer down with just one click.

Thanks, Bob.

---

### Post by pianist16 on 2013-05-05
Well, since you have the "poweroff" command to shutdown the computer, you can create a launcher icon on desktop and specify this command line. Not sure if gonna work, though.

---

### Post by gerowen on 2013-05-05
You could just make a script that executed:

```

sudo shutdown -h now

```

You'll still get prompted for your password since it has to launch with sudo.  You could get around this, although it isn't advised, by editing sudoers so you don't have to provide your password when using sudo.

---

### Post by Frogs Hair on 2013-05-05
Any of many the commands used to create a desktop launcher for shutdown  are going to require a password, so existing option is faster.   [http://www.cyberciti.biz/faq/shutdown-ubuntu-linux-computer/](http://www.cyberciti.biz/faq/shutdown-ubuntu-linux-computer/)

---

### Post by BrunoLotse on 2013-05-05
Just for a thought.I am running 12.04.2 LTS with GNOME Shell 3.4.2.1.There is Alternative Status Menu extension[https://extensions.gnome.org/extension/5/alternative-status-menu/](https://extensions.gnome.org/extension/5/alternative-status-menu/)Having installed this extension I have Power Off... option to shut the system down.

---

### Post by bob brazie on 2013-05-06
I put this command in a jumper and I get the message that there was an error in launching the application.

$ sudo shutdown -h now

---

### Post by zemega on 2013-05-06
why not 'sudo shutdown 0' ? Don't include the '$' in your command.

---

### Post by matt_symes on 2013-05-06
Hi

Use dbus instead.

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

Pop it in a script. 

As it uses policy/console kit, you should not need to enter a password or mess with your sudoers file.

Kind regards

---

### Post by bob brazie on 2013-05-06
Nothing happens with that command.

---

### Post by bob brazie on 2013-05-06
Wow! thanks Matt. That really does the trick! I will use ti wisely.

Bob

---

### Post by BrunoLotse on 2013-05-06
Thanks Matt from myself too.However, when I tried to use instead Stop Reboot the system notified me that I need to be a root. Is there the way to reboot using dbus without root authority and sudo? How could we do it?Cheers, BrunoDo not read newspapers on an empty stomach ~ Russian Proverb :)

---

### Post by matt_symes on 2013-05-06
Hi

> **BrunoLotse said:**
> Thanks Mat from myself too.However, when I tried to use instead Stop Reboot the system notified me that I need to be a root. Is there the way to reboot using dbus without root authority and sudo? How can we do it.

Try this... (Restart)

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.**Restart**
```

> Cheers,BrunoDo not read newspapers on an empty stomach ~ Russian Proverb :)

Great proverb :popcorn:

Kind regards

---

### Post by BrunoLotse on 2013-05-06
Thank you Matt!!!Works like a charm :)Bruno

---

### Post by bob brazie on 2013-05-07
How do I mark this as solved?

---

### Post by matt_symes on 2013-05-07
Hi

I'll do it for you :D

Kind regards

---

### Post by bob brazie on 2013-05-07
Thanks I will let you do that but can you tell me where to locate that in this new format?

Thanks. Bob.

---

### Post by matt_symes on 2013-05-07
Hi

You have to edit your first post title in the thread and there you should be able to change the prefix to solved.

We're waiting on a new 'solved' plugin i believe.

Kind regards

---

### Post by bob brazie on 2013-10-24
Now it is not working in 13.10. Says there was an error launching the application.
Any thoughts?

---

### Post by monkeybrain20122 on 2013-10-24
"sudo poweroff" will shut it down, but of course you need to supply your password.

Sorry, I don't really get it. What is so complicated to shut down the default way??? Seems to be much to do about nothing,  Well, unless you are using the computer to do something dubious and afraid someone would accidentally catch you in action (watching porn??) so need a hasty exit  :) In that case maybe just press the power button when you hear footsteps approaching. :)

---

### Post by bob brazie on 2013-10-25
Not sure what you do on your computer either.

Why not one click when you are the only user of the machine and no one else needs to log on? One click or three? I would rather click once. The option should be a built in choice I would think.

---

### Post by monkeybrain20122 on 2013-10-25
> **bob brazie said:**
> Not sure what you do on your computer either.

Why not one click when you are the only user of the machine and no one else needs to log on? One click or three? I would rather click once. The option should be a built in choice I would think.

You can always submit a patch or make a ppa. It is open source. ;) I just can't understand the point of going through all that troubles to save one or two clicks* (* in Windows it is 2 clicks if I remember correctly)

---

### Post by Habitual on 2013-10-25
```
dbus-send --print-reply --system --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```
"may" work as a launcher with that as the command.

---

### Post by bob brazie on 2013-10-26
Sorry Habitual. Didn't do the trick.

I would love to write a patch but I don't know programing and am just a very interested user.

---

