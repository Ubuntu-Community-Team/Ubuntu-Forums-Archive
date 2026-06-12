---
title: "QtBus help!"
date: 2011-02-05
forum: Programming Talk
---

### Post by hakermania on 2011-02-05
Well the story has as follow:
I have created an app, which has only one instance (it can opened only one time concurrently), so, when the app opens, it checks if the process is already running, and if it is, it displays a MessageBox warning.
Well, what I want is, if it detect that the process is running to send a message through DBus and then the already running process to listen to this interface and capture the message and proceed to some action (e.g. focus to the already running process). I've found how to send a signal, but I don't know where and how to listen in order to receive it!
This is the code to send a String message(it does work(i watch dbus-monitor), I don't know if the xml file is needed, though):```
    QDBusMessage msg = QDBusMessage::createSignal("/", "open.album", "message");
    msg << "Hey, Please focus to the already running process and i'll exit!";
    QDBusConnection::sessionBus().send(msg);
```
and open.album.xml is:
```
<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
 <node>
   <interface name="open.album">
     <signal name="message">
       <arg name="album" type="s" direction="out"/>
     </signal>
     <signal name="action">
       <arg name="album" type="s" direction="out"/>
     </signal>
   </interface>
 </node>
```
I'd really like to know how to catch this signal and do some action!
Thanks in advance!

---

### Post by hakermania on 2011-02-05
Ok, solved here: [http://www.qtcentre.org/threads/38453-Send-and-receive-a-signal-between-2-Qt-applications.?p=176731#post176731](http://www.qtcentre.org/threads/38453-Send-and-receive-a-signal-between-2-Qt-applications.?p=176731#post176731)

---

