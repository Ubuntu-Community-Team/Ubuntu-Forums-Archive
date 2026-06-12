---
title: "shutdown script without  entering password"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by rburkartjo on 2008-11-27
i have made a shutdown script sudo halt. however how can i modify it so i dont have to type in my password to use. should be an easy one for the more advanced users. it is already exe just want to be able to open and run in terminal and it will work. happy turkey day/cheesemaker

---

### Post by unutbu on 2008-11-27
To run a command as root without having to type the password:

Open a terminal (Applications>Accessories>Terminal) and run
```

EDITOR=gedit gksu visudo
```

(This command allows you to edit the /etc/sudoers file more safely. It runs some checks to make sure you don't botch the syntax. Botching the syntax can make you lose the ability to use sudo until /etc/sudoers is fixed.)

Add this to the file:
```

Cmnd_Alias MYCOMMANDS=/path/to/script.sh
the_user ALL=NOPASSWD: MYCOMMANDS
```

Change the_user to your real username.

This information comes from [http://ubuntuforums.org/showpost.php...8&postcount=15](http://ubuntuforums.org/showpost.php...8&postcount=15)

---

### Post by Michael.Godawski on 2008-11-27
I guess you have somehow to modify the sudoers file. to permit the script to be executed as su.

But playing with the sudoers file should only be done if you are 100% of what you are doing. I am not sure if this information is not again the forum policy...

So mods correct me if I am wrong...:)

Surely there is a reason why the shutdown and restart is only permitted to root.

Try this:
in /etc/sudoers 
```
Username ALL=NOPASSWD:/home/Username/path/to/script/skript.sh
```
Start the script with 
```
sudo /home/Username/path/to/script/skript.sh
```


But once again you compromise your security by playing around with the sudoers file.
PS:

Tell me if it works...:)

---

### Post by rburkartjo on 2008-11-27
unutbu, where  have i gone wrong
gksudo reboot

Cmnd_Alias MYCOMMANDS=/path/to/script.sh
ray ALL=NOPASSWD: MYCOMMANDS

note i still have to enter password to get it to work./tks cheesemaker

---

### Post by unutbu on 2008-11-27
Did you change /path/to/script.sh to the real path to your script?

What is "gksudo reboot"? Is it the command you are typing? If so, then change /path/to/script.sh to /sbin/reboot. Then run it with 
```

sudo reboot
```
rather than```

gksudo reboot
``` since it is a non-graphical app.

---

### Post by rburkartjo on 2008-11-27
unutbu,
still no luck did i do this right
sudo reboot

Cmnd_Alias MYCOMMANDS=/path/to/sbin/reboot
ray ALL=NOPASSWD: MYCOMMANDS
only reason i am trying to do this is 8.10 really hangs up on restart and shutdown and i the above works great in stopping this. enjoy your turkey day i can live with typing in my password. just trying to learn/cheesemaker

---

### Post by unutbu on 2008-11-27
Thanks rburkartjo, happy Thanksgiving to you to!

Try this:
```
Cmnd_Alias MYCOMMANDS=/sbin/reboot
ray ALL=NOPASSWD: MYCOMMANDS
```

---

### Post by ibuclaw on 2008-11-27
Using dbus, you can suspend/hibernate without the use of a password...

I am 70% confident, that if you have a look round, you can shutdown without a password using dbus too :)

Heres the reference:
[http://bbs.archlinux.org/viewtopic.php?pid=445642](http://bbs.archlinux.org/viewtopic.php?pid=445642)


[EDIT]
[http://people.freedesktop.org/~david/hal-spec/hal-spec.html#interface-device-systempower](http://people.freedesktop.org/~david/hal-spec/hal-spec.html#interface-device-systempower)

Try this:
```

dbus-send --system --print-reply --dest=org.freedesktop.Hal \
 /org/freedesktop/Hal/devices/computer \
 org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown

```
If it works, you can either set it as an **alias** or **function** in your **~/.bashrc** file.

Regards
Iain

---

### Post by ibuclaw on 2008-11-27
Yep, I can confirm that this is working:
```
alias canhaz-shutdown='dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown'

```

Regards
Iain

---

