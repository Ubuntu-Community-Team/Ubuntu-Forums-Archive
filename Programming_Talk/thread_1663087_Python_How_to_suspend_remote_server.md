---
title: "Python: How to suspend remote server?"
date: 2011-01-09
forum: Programming Talk
---

### Post by produnis on 2011-01-09
Hi folks,

I wrote a Python-Script for my music-server, which checks wether music is played. If no music is played, the server is put to suspend via dbus.
This is the python-function for suspending:
```
def GeheSchlafen():
		bus = dbus.SystemBus()
		proxy_object = bus.get_object('org.freedesktop.UPower','/org/freedesktop/UPower')
		pm = dbus.Interface(proxy_object,'org.freedesktop.UPower')
		pm.Suspend()
```

This all works fine...
BUT ONLY if the script is started during boot, or (afterwards) using VNC and terminal.

MY PROBLEM:
If I connect to the server via ssh, and then start the script, the server won't suspend. It gives back the following error:
```
Traceback (most recent call last):
  File "/home/produnis/bin/SuspendIfQuiet.py", line 327, in <module>
    GeheSchlafen()
  File "/home/produnis/bin/SuspendIfQuiet.py", line 164, in GeheSchlafen
    pm.Suspend()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: **org.freedesktop.UPower.GeneralError: not authorized**
```


So, I tryed to export the current dbus-session to the script.
I wrote another script, which is startet during boot and which saves the dbus-info into a file:
```
set | grep DBUS_SESSION_BUS_ADDRESS > ~/.DBUS_temp
```

...and then I wrote another script called "dbus.run.sh", which is thought to export the needed dbus-session, and which looks like this:
```
source /home/produnis/.DBUS_temp
export DBUS_SESSION_BUS_ADDRESS
$*
```

So, now I start my original script with the following command:
```
dbus.run.sh MyScript.py
```

BUT IT WON'T WORK...
I still get this dbus-exception.

Is there any way to somehow "import" the dbus-session within my Python-Script?
Or does anyone know an alternative way to suspend the server via ssh and python?

---

### Post by produnis on 2011-01-10
I modified the script to make sure that the correct dbus-adress is used:
```
f = open("/home/produnis/.DBUS_temp", "r")
session = f.readline()
session = session.replace('DBUS_SESSION_BUS_ADDRESS=','')
session = session.replace('\r','')
session = session.replace('\n','')
os.environ["DBUS_SESSION_BUS_ADDRESS"] = session
```

The var is correctly set.

BUT I still get that error...
```
org.freedesktop.UPower.GeneralError: not authorized
```

Does anyone know how to configure dbus-server in order to allow ssh-users to suspend the machine?

---

### Post by vik_2010 on 2011-01-10
I don't know too much about dbus, but your stacktrace indicates that it is a permissions error rather than syntax/code one.

Maybe it has something to do with your login rights with ssh.

If you find an answer, I'd be interested in knowing it. 

Best,

-V

---

### Post by wmcbrine on 2011-01-11
Yes, it runs as root at startup, and presumably not when you launch it from the shell. Try it with "sudo".

---

