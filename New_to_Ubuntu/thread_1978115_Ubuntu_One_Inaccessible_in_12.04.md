---
title: "Ubuntu One Inaccessible in 12.04"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by farumphry on 2012-05-11
Greetings,

I have been using Ubuntu 11.10 for a few months and recently I updated to 12.04. It's been running smoothly so far except for one thing: I can't access Ubuntu One. Every time I try I get this error message: 

CredentialsError
DBusException(dbus.String(u'Traceback (most recent call last):\n  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb\n    retval = candidate_method(self, *args, **keywords)\n  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/credentials/linux.py", line 185, in find_credentials\n    reply_handler=reply_handler, error_handler=error_handler)\n  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 137, in __call__\n    **keywords)\n  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 584, in call_async\n    message.append(signature=signature, *args)\nValueError: Unable to guess signature from an empty dict\n'),)

Am very much a newbie, would love it if someone could help explain this.
Cheers,
Farah x

---

### Post by kc1di on 2012-05-11
here's something you can try:
go to a terminal and type the following commands

```
sudo apt-get purge ubuntuone-client
``` it will ask you for your password. When that is finished type this command:
```
sudo apt-get install ubuntuone-client
```
then try to acess unbuntu one again. see if that works if not try running ubuntu one in the terminal by issuing the command :
```
ubuntuone-control-panel-qt
```
and post here any error messages you get.

---

### Post by marty331 on 2012-05-17
I followed your exact instructions.  It 'installed' and when ubuntu one attempted to launch I got the following error:

CredentialsError
DBusException(dbus.String(u'Traceback (most recent call last):\n  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb\n    retval = candidate_method(self, *args, **keywords)\n  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/credentials/linux.py", line 185, in find_credentials\n    reply_handler=reply_handler, error_handler=error_handler)\n  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 137, in __call__\n    **keywords)\n  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 584, in call_async\n    message.append(signature=signature, *args)\nValueError: Unable to guess signature from an empty dict\n'),)

---

