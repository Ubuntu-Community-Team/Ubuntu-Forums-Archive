---
title: "Hard breakage after updates"
date: 2011-06-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-06-29
```
Elaborazione dei trigger per python-support...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 502, in <module>
    post_change_stuff(py)
  File "/usr/sbin/update-python-modules", line 333, in post_change_stuff
    os.remove(abspath)
OSError: [Errno 30] Read-only file system: '/usr/lib/pymodules/python2.7/paramiko/client.pyc'
dpkg: errore nell'elaborare python-support (--unpack):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1
Segnalazione apport non scritta poiché è stato raggiunto il valore massimo di MaxReports
        Elaborazione dei trigger per man-db...
dpkg: errore fatale non recuperabile, uscita:
 impossibile eseguire flush dello stato aggiornato di "man-db": File system in sola lettura
E: Sub-process /usr/bin/dpkg returned an error code (2)
Installazione di un pacchetto non riuscita. Tentativo di ripristino:
dpkg: error: impossibile accedere all'area di stato di dpkg: File system in sola lettura

E: Failed to write commit log

E: dpkg è stato interrotto. È necessario eseguire "sudo dpkg --configure -a" per correggere il problema. 
E: _cache->open() failed, please report.

W: Blocco disabilitato per il file di blocco in sola lettura /var/lib/dpkg/lock

```

Filesystem corrupted, fixed with fsck at boot time, now I try to figure out was wrong!
Luckily is a virtualbox image, so not a great problem.

If I recall updates were about: udisk, gnome-menus and evdev.. don't know which is the cause, maybe udisk.

---

### Post by MacUntu on 2011-06-29
Nothing bad happened here. Maybe just coincidence?

---

### Post by Harry33 on 2011-06-29
No problems here either.
Also the python2.7 packages were updated today.

> 
Python2.7 (2.7.2-2) unstable; urgency=low
  * Update to 20110628, taken from the 2.7 branch.
  * Add profile/pstats to the python2.7 package, update debian copyright.
  * Don't run the bsddb3 tests on kfreebsd-amd64.
  * Don't run the benchmark on hurd-i386.

---

### Post by fjgaude on 2011-06-29
I'm running latest updates without issue in VMware Player.

---

### Post by lucazade on 2011-06-29
who knows, just a coincidence seems plausible and also funny..
it is always solid as rock ;)

---

### Post by ranch hand on 2011-06-29
> **lucazade said:**
> Filesystem corrupted, fixed with fsck at boot time, now I try to figure out was wrong!
Luckily is a virtualbox image, so not a great problem.

If I recall updates were about: udisk, gnome-menus and evdev.. don't know which is the cause, maybe udisk.
This is a good reason to use apt-get and make sure you have the profile preferences set to "unlimited" under the "scrolling" tab.  At least for us grumpy geezers that may be getting forgetful.

It may be a pain but you can find the update and check.

If I remember too, on any OS I am testing, I copy/paste that info to a text file (gedit) and keep it for a couple days along with any messages that may have popped up while running the update/upgrade.  Doesn't seem worth it most of the time and then you get that one upgrade that it is just TOO handy to have and that makes the effort worth while.

---

### Post by fjgaude on 2011-06-30
I spoke too soon... today's upgrade killed the VM in Player. I zsynced today's daily and tried a new install: it failed. I await another day! <smile>

---

### Post by lucazade on 2011-06-30
> **fjgaude said:**
> I spoke too soon... today's upgrade killed the VM in Player. I zsynced today's daily and tried a new install: it failed. I await another day! <smile>

Same issue also for you?


> **ranch hand said:**
> This is a good reason to use apt-get and make sure you have the profile preferences set to "unlimited" under the "scrolling" tab.  At least for us grumpy geezers that may be getting forgetful.

It may be a pain but you can find the update and check.

If I remember too, on any OS I am testing, I copy/paste that info to a text file (gedit) and keep it for a couple days along with any messages that may have popped up while running the update/upgrade.  Doesn't seem worth it most of the time and then you get that one upgrade that it is just TOO handy to have and that makes the effort worth while.

Terminal is set to unlimited but unfortunately this time I was using synaptic and the first part of the log was unreadble.
I mean when I see update process was not completed I clicked on the expander arrow of the update dialog of synaptic and the first part of log was empty.
It started only after a lot of blank lines :)

---

### Post by fjgaude on 2011-06-30
I installed yesterday's daily and back with a 11.10 VM. Did an update/upgrade and all is well, again.

---

### Post by MacUntu on 2011-07-05
Filesystem went bad today. Not yet sure what happened (dumping the partition atm). Hopefully it's not some weird ext4 bug?

---

### Post by lucazade on 2011-07-05
> **MacUntu said:**
> Filesystem went bad today. Not yet sure what happened (dumping the partition atm). Hopefully it's not some weird ext4 bug?

Hope it is not :S
never had other problem like this in the mean time

---

