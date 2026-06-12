---
title: "Synce error: can't sync with HTC Touch Pro"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by lenn-art on 2008-09-25
After following the installation steps of 

I still can't sync.

When i run $ msynctool --sync synce-sync (with ~$ synce-sync-engine in another cli-window) i get this error message at the end:
```
Member 2 of type evo2-sync just sent all changes
Member 1 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 1 of type synce-opensync-plugin just disconnected
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error synchronizing: Unable to read from one of the members
Pipe closed! Exiting.
Pipe closed! Exiting.

```

AFAISee the connection between my HTC touc Pro <> msync does not work. However, synce-pls gives a nice tree with folders on my phone. So, there is at least a connection. 

Running $ msynctool --showgroup synce-sync gives output:```

Groupname: synce-sync
Member 1: synce-opensync-plugin
	No Configuration found: Member has not been configured
Member 2: evo2-sync
	Configuration : <config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>
```
So, the synce-opensync-plugin isn't configured? :confused: 

I googled a lot, but i can't find the right solution.

---

### Post by Bigdaddy_62 on 2008-12-09
Hi,

I have exactly the same error message with my **HTC P3300** connected on my Ubuntu 8.04 laptop : 

When I try to sync : 

```
Member 2 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
```


And when I use msynctool --showgroup evolution

```
arnaud@arnaud-laptop:~$ msynctool --showgroup evolution
Groupname: evolution
Member 2: synce-opensync-plugin
	No Configuration found: Member has not been configured
Member 1: evo2-sync
	Configuration : <?xml version="1.0"?>
<config>
  <address_path>default</address_path>
  <calendar_path/>
  <tasks_path/>
</config>

arnaud@arnaud-laptop:~$ 
```

Didi someone can help us ? :confused:

Thanks,
Arnaud

---

### Post by Kevbert on 2008-12-09
I think you may be out of luck with HTC phones as generally they don't seem to work with Ubuntu. Gammu/Wammu doesn't work either. I have an HTC Lobster 700TV and that doesn't work. Even bluetooth will only work one way.

---

### Post by knoodrake on 2009-01-09
Hi, i had exactly the same problem with a samsung i900, and resolved it by installing **synce-multisync-plugin**. Once installed, msynctool --sync group worked as excepted !
So, I'll advice you to verify that you have it.
++
(please excuse my english)

---

### Post by Sigilium on 2009-01-17
Hi, I had the same problem. Creating partnership with synce-create-partnership helped.

---

### Post by Runamok on 2009-01-27
Ok, I got this to work.  I used the information found on this page...
[http://smealko.blogspot.com/2008/10/htc-touch-pro-ubuntu-should-work-for.html]("http://smealko.blogspot.com/2008/10/htc-touch-pro-ubuntu-should-work-for.html")

In Summary, you need to go System>Administration>Synaptic Package Manager
and make sure all of the following programs are installed. 
 
multisync-tools multisync0.90 opensync-module-python opensync-plugin-evolution opensync-plugin-google-calendar opensync-plugin-synce python-opensync synce-gnomevfs synce-gvfs synce-hal synce-sync-engine synce-trayicon

Also, I did open an terminal and type "sudo modprobe ipaq"  Not sure if this made a difference....

Reboot and the synce-trayicon should start.  Right click to browse files, works like a charm. 

- Enjoy :D
Runamok81

---

### Post by loongye on 2009-03-04
Hi there,

I'm on Intrepid and I'm having the following problem syncing with my Touch Pro:

```
$ msynctool --sync synce-sync
Synchronizing group "synce-sync" 
The previous synchronization was unclean. Slow-syncing
DEBUG:SynCE:Connect() called
Member 1 of type synce-opensync-plugin just connected
Member 2 of type evo2-sync just connected
All clients connected or error
DEBUG:SynCE:get_changeinfo() called
DEBUG:SynCE:slow sync requested for Contacts
DEBUG:SynCE:slow sync requested for Calendar
DEBUG:SynCE:slow sync requested for Tasks
INFO:SynCE:initiating device synchronization
Member 2 of type evo2-sync just sent all changes
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 152, in get_changeinfo
    self._TriggerSync()
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 117, in _TriggerSync
    self.engine.Synchronize()
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.synce.SyncEngine.Error.NoBoundPartnership: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 696, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.5/site-packages/SyncEngine/kernel.py", line 641, in Synchronize
    pship = self._CheckAndGetValidPartnership()
  File "/usr/lib/python2.5/site-packages/SyncEngine/kernel.py", line 358, in _CheckAndGetValidPartnership
    raise errors.NoBoundPartnership
NoBoundPartnership: org.synce.SyncEngine.Error.NoBoundPartnership: 

Member 1 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 1 of type synce-opensync-plugin just disconnected
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
Error while synchronizing: Unable to read from one of the members

```

---

### Post by loongye on 2009-03-04
Hmm I followed this guide and got it to work: [http://ubuntuforums.org/showthread.php?p=6808083](http://ubuntuforums.org/showthread.php?p=6808083)

---

