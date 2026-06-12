---
title: "Python, dbus  and using the right method"
date: 2013-02-09
forum: Programming Talk
---

### Post by losername on 2013-02-09
OK this is probably quite simple but  I'm stuck.

Command
```
qdbus org.kde.kmail /KMail | grep openComposer 
```Prints this
```
method QDBusObjectPath org.kde.kmail.kmail.openComposer(QString to, QString cc, QString bcc, QString subject, QString body, bool hidden)
method int org.kde.kmail.kmail.openComposer(QString to, QString cc, QString bcc, QString subject, QString body, bool hidden, QString attachName, QByteArray attachCte, QByteArray attachData, QByteArray attachType, QByteArray attachSubType, QByteArray attachParamAttr, QString attachParamValue, QByteArray attachContDisp, QByteArray attachCharset, uint identity)
method int org.kde.kmail.kmail.openComposer(QString to, QString cc, QString bcc, QString subject, QString body, bool hidden, QString messageFile, QStringList attachmentPaths, QStringList customHeaders)
```My code:


```
import dbus

bus = dbus.SessionBus()
msg = bus.get_object('org.kde.kmail', '/KMail')
msg.openComposer("huge bunch of argument goes here" , dbus_interface='org.kde.kmail.kmail')

```How to get an access to the lowest method on  the list?

Thanks!

---

