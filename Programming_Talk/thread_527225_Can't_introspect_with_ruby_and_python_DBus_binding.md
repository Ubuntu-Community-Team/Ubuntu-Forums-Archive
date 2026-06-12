---
title: "Can't introspect with ruby and python DBus bindings on Gutsy"
date: 2007-08-16
forum: Programming Talk
---

### Post by jhemono on 2007-08-16
Hello,
I want to do a ruby hack with tracker via DBus. I'm on Gutsy.
When I was on feisty, I used RBus DBus ruby binding to play with DBus and It worked well.
However, on Gutsy, RBus and ruby-dbus, another binding, tell me DBus doesn't respond to the "inspect" messages it sends.
Then I tried a python program that does lots of "inspect" calls, [Dbus-inspector]("http://www.vitavonni.de/projekte/dbus-inspector.html.en").
I extract-run it and here's what i get : 
> **ERROR:dbus.proxies:Introspect error on :1.19:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.DBus.Introspectable" member "Introspect" error name "(unset)" destination ":1.19")**
Introspection failed for com.redhat.NewPrinterNotification (:1.19), /
ERROR:dbus.proxies:Introspect error on :1.8:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.DBus.Introspectable" member "Introspect" error name "(unset)" destination ":1.8")
Introspection failed for com.redhat.dhcp (:1.8 ), /
ERROR:dbus.proxies:Introspect error on :1.6:/org/freedesktop/ConsoleKit/Session1: dbus.exceptions.IntrospectionParserException: Error parsing introspect data: <class 'xml.parsers.expat.ExpatError'>: mismatched tag: line 84, column 6
Traceback (most recent call last):
  File "/home/jhemono/dbus-inspector/dbus-inspector", line 108, in refresh
    sysresult = dbusinspect.discover(dbus.SystemBus())
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 347, in discover
    servicelist.append(service(bus, None, "/", aliases))
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 78, in __init__
    self._expand()
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 112, in _expand
    self.children.append(service(self, c, cpath, self.aliases))
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 78, in __init__
    self._expand()
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 112, in _expand
    self.children.append(service(self, c, cpath, self.aliases))
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 78, in __init__
    self._expand()
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 112, in _expand
    self.children.append(service(self, c, cpath, self.aliases))
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 78, in __init__
    self._expand()
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 112, in _expand
    self.children.append(service(self, c, cpath, self.aliases))
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 77, in __init__
    self._introspect()
  File "/home/jhemono/dbus-inspector/dbusinspect.py", line 139, in _introspect
    dom = minidom.parseString(ispect)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1925, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 942, in parseString
    return builder.parseString(string)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: mismatched tag: line 84, column 6


---

### Post by jhemono on 2007-08-16
I can now inspect classes with ruby except tracker but maybe it s not introspectable, i'm pretty new to dbus.
However th python progam still desnt work.
thans in advance.

---

### Post by cjbehm on 2007-10-31
This still seems to be the case (7.10 and non-functioning Python dbus-inspector) and it's rather frustrating. Did you happen to find a solution somewhere for the dbus-inspector software?

---

### Post by shm on 2008-04-15
There is a solution
[[IMG]http://img217.imageshack.us/img217/6338/screenshot13ys4.th.png[/IMG]](http://img217.imageshack.us/my.php?image=screenshot13ys4.png)
[http://gitweb.freedesktop.org/?p=dbus/dbus-glib.git;a=commit;h=3f6e2c0c76d3643a1823b5ea7c8f5486a6b448de](http://gitweb.freedesktop.org/?p=dbus/dbus-glib.git;a=commit;h=3f6e2c0c76d3643a1823b5ea7c8f5486a6b448de)
compiled packages [ftp://80.86.249.14/dbus/dbus-glib](ftp://80.86.249.14/dbus/dbus-glib)
you should reboot after install the packages (to reload dbus libs)

---

### Post by nealmcb on 2008-04-19
Thanks, shm.  I just ran into this problem in the libdbus-glib-1-2 package also.
For reference for others, the ubuntu source package is at

 [https://edge.launchpad.net/ubuntu/+source/dbus-glib/](https://edge.launchpad.net/ubuntu/+source/dbus-glib/)

and I guess it is fixed in hardy.

---

### Post by stijngysemans on 2008-07-13
This is error is still in Hardy. The fix is in version 0.74-4 and higher.
More details see here: [https://edge.launchpad.net/ubuntu/+source/dbus-glib/](https://edge.launchpad.net/ubuntu/+source/dbus-glib/)

---

### Post by nealmcb on 2008-07-13
Thanks for the correction.  So it looks like it is fixed in Intreped, not Hardy.  The particular patch in question is for "Make dbus-binding-tool ignore namespaced nodes & attributes " at

 [https://bugs.freedesktop.org/show_bug.cgi?id=14429](https://bugs.freedesktop.org/show_bug.cgi?id=14429)

and the debian bug (now closed) is at 
 [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478265](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478265)

---

