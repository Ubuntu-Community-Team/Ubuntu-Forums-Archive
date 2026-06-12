---
title: "need help with Broadcom BCM43231"
date: 2011-08-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-08-28
friends computer, he just bought a netgear Broadcom BCM43231(dooohh) wireless usb for his system that has no built in wireless.....

jockey isn't working 
> sudo jockey-kde
[sudo] password for robert: 
Error: "/var/tmp/kdecache-robert" is owned by uid 1000 instead of uid 0.
ERROR:dbus.proxies:Introspect error on :1.46:/DeviceDriver: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/bin/jockey-kde", line 472, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 465, in run
    self.ui_show_main()
  File "/usr/bin/jockey-kde", line 159, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-kde", line 315, in update_tree_model
    self.mw.label_heading.setText('<b>%s</b><br/><br/>%s' % self.main_window_text())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 219, in main_window_text
    for h_id in self.backend().available(self.argv_options.mode):
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 127, in backend
    self._check_repositories()
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 839, in _check_repositories
    if self._dbus_iface.has_repositories():
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 143, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.46 was not provided by any .service files


so how do i go about installing broadcom bcm43231 usb without jockey working? I have no broadcom myself so i'm new at this one.

help please

he's a very new convert from vista (doooh! lol) and he's really liking it for how 'smokin fast' it is.  gotta get this thing working if we can. 

thanks

---

### Post by buzzmandt on 2011-08-29
ok, got it to work with ndisgtk and ndisrapper w/windows .inf.

works but doesn't auto load itself at boot

can anyone tell me how to set ndisdriver to load at boot time?

---

### Post by buzzmandt on 2011-08-29
ok, got it working.  posting my how to here for future reference.

as far as i can tell there isn't a linux driver yet for this particular setup.
> robert@robert-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

I used ndiswrapper as so:
download the netgear .inf file from here [http://matthew-4gl.wikispaces.com/file/view/Netgear.tar.gz/190342998/Netgear.tar.gz](http://matthew-4gl.wikispaces.com/file/view/Netgear.tar.gz/190342998/Netgear.tar.gz)

you can then right click it from your file browser and extract it, it will extract bcmwlhigh5.inf and bcmwlhigh5.sys.  I only used the .inf for this.

install ndiswrapper and ndisgtk
```
sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-dkms

```

run ndisgtk (I ran from menu, not sure if it should be run from terminal)

select install windows driver and select the bcmwlhigh5.inf.  It should show supported hardware in the ndisgtk window.

my wireless immediately began to work.


Now, we need to load it at boot to be at the ready when the desktop loads.

edit /etc/modules
in kubuntu:
```
kdesudo kate /etc/modules

```
or in ubuntu
```
gksudo kate /etc/modules

```
and add the line
```
ndiswrapper
```
at the end.

I haven't worked with ndiswrapper since around 2007, much may have changed and there might be an easier way.  but i can confirm this works pretty darn good from here.

sure do wish there was a linux driver for this one though. (poo poo broadcom corp. lol)

---

