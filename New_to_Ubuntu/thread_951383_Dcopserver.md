---
title: "Dcopserver ?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by anthology on 2008-10-18
dcopserver ?
I have installed k9copy.
When I run the programme I get an error saying
please check decopserver is running.
Could someone please explain what decopserver is PLEASE.
Does it have anything to do with DHCP?

---

### Post by ajmorris on 2008-10-18
hi there,

DCOP stands for ***D**esktop **CO**mmunication **P**rotocol*. It's a light-weight interprocess and  software componentry communication system. The main point of this system is to allow applications to interoperate, and to share complex tasks. Essentially, DCOP is a &#8216;remote control&#8217; system, which allows an application or a script to enlist the help of other applications. Unfortunately, DCOP is associated with the *K Desktop Evironment. *To run a KDE application in Gnome, that requires the DCOP server, you will need to install the kde libraries. You can do this via this command from a terminal (or via a gui alternative method, in add/remove or the synaptic package manager):

```
sudo apt-get install kdelibs
```AJ

---

### Post by JibberFisch on 2008-10-23
Now I'm getting an issue:

```
will@fischtablet:~$ dcopserver
Only one line in dcopserver file !: 
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
Only one line in dcopserver file !: 
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
DCOPServer self-test failed.

```

Did my:
```
sudo apt-get install kdelibs
```
but to no avail.  Any thoughts?

Is there any chance that it had anything to do with my Firefox suddenly losing its ability to use the forward and back buttons, and the bookmarks on my toolbar disappearing?  Help!
Thanks,
Will

---

### Post by Keen101 on 2008-10-23
[http://ubuntuforums.org/showthread.php?t=511300&highlight=DCOP](http://ubuntuforums.org/showthread.php?t=511300&highlight=DCOP)

this might help.

---

### Post by oldos2er on 2008-10-23
I used the command "sudo chown -R ann:ann /home/ann/.kde" which worked for me. Replace "ann" with your user name.

---

