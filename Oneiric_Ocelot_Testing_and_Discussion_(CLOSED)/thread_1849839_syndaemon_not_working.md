---
title: "syndaemon not working?"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-09-25
syndaemon -i 2 -d -t -K

Have been trying to solve my touchpad problems with syndaemon but it appears to not be running. There are no errors. 

if i do pkill syndaemon or killall syndaemon i get "no process found" message.

---

### Post by x-shaney-x on 2011-09-25
I use syndaemon on startup to disable touchpad while typing (synclient -i 2 -d).
It's working fine here on 3 different laptops and the same if I type it into a terminal so I would assume something has gone wrong your end rather than a bug.

---

### Post by sonicb00m on 2011-09-25
I have a three clean installs on 3 different machines and syndaemon isnt visible in any process list so I have no idea what I might have done.

Do you get a process ID if you type pgrep syndaemon ??

In fact typing your command you mentioned I get this error

synclient -i 2 -d


 synclient -i 2 -d
synclient: invalid option -- 'i'
Usage: synclient [-s] [-m interval] [-h] [-l] [-V] [-?] [var1=value1 [var2=value2] ...]
  -m monitor changes to the touchpad state (implies -s)
     interval specifies how often (in ms) to poll the touchpad state
  -l List current user settings
  -V Print synclient version string and exit
  -? Show this help message
  var=value  Set user parameter 'var' to 'value'.

---

### Post by x-shaney-x on 2011-09-25
Yup.

```
$ pgrep syndaemon
1671
```

The command I listed before was syndaemon, not synclient

---

### Post by sonicb00m on 2011-09-26
Erm it wasn't :P

> I use syndaemon on startup to disable touchpad while typing (synclient -i 2 -d).

But neither solves my problem. There is no process ID running syndaemon on any of my clean installs. It just does nothing :(

xserver-xorg-input-synaptics | 1.4.1-1ubuntu1

---

### Post by x-shaney-x on 2011-09-26
Ok you got me on that one :)  I MEANT to put syndaemon.

Maybe something went a bit wrong during an update.  Have you tried re-installing the package?

---

### Post by sonicb00m on 2011-09-26
Yeah I have. It just does nothing. There's no error message, nothing.

---

### Post by sonicb00m on 2011-09-27
I think the actual issue is with the driver...i have a dell vostro laptop


synclient -l | grep TouchpadOff | awk '{ print $3 }'
Couldn't find synaptics properties. No synaptics driver loaded?

I can't get it working.

[http://en.gentoo-wiki.com/wiki/Dell_Vostro_V13](http://en.gentoo-wiki.com/wiki/Dell_Vostro_V13)
Problem: Synaptics driver does not load, kernel/X11 thinks it's a generic PS/2 mouse.
Solution: no solution yet.

---

### Post by sonicb00m on 2011-09-27
If anyone else experiences a similar problem I created a small workaround script

```

                ID=$(xinput list | grep 'ALPS' |  awk '{print $6}' | sed 's/id=//g')

		if xinput list | grep 'USB Mouse' > /dev/null ; then
			echo "touch disabled"
			xinput set-prop "$ID" "Device Enabled" 0
		else
			echo "touch enabled"
			xinput set-prop "$ID" "Device Enabled" 1
		fi

```

If anyone knows how to tell if the keyboard is in use using bash then please let me know so I can replicate the "disable touchpad when typing" thing.

---

