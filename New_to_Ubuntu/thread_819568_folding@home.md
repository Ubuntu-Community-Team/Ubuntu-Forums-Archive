---
title: "folding@home"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by shifty_powers on 2008-06-05
hi guys ;)

just had a kernel update. everything is fine apart from folding@home.

the client doesn't start on boot up any more, and if i

```
sudo /etc/init.d/foldingathome start
```

then it states that it is starting the service, but my process monitor clearly shows it is not.

any ideas?

---

### Post by Flying caveman on 2008-06-05
whats your cpu usage? if you installed folding to the system it won't show as a process, but you should still see your cpu usage increase. 

try ```
top
```
to see if its running.

---

### Post by shifty_powers on 2008-06-05
i've got a gesklet runnin that monitors my cpu usage, and it shows up the folding@home usage. the process is definitely not running i'm afraid ;)

---

### Post by Flying caveman on 2008-06-05
maybe try ```
sudo /opt/foldingathome/reconfigure.sh
```:confused:

then try to start it again.  Is there anything weird in your FAHlog.txt? like it can't connect to a server or something?

---

### Post by shifty_powers on 2008-06-06
well when i do that, this ii the result...

```
shifty@shifty-desktop:~$ sudo /opt/foldingathome/reconfigure.sh
[sudo] password for shifty: 

Note: Please read the license agreement (FAH504-Linux.exe -license). Further 
use of this software requires that you have read and accepted this agreement.

Folding@Home User Configuration



--- Opening Log file [June 6 18:59:55] 


# Linux Console Edition #######################################################
###############################################################################

                       Folding@Home Client Version 5.04beta

                          http://folding.stanford.edu

###############################################################################
###############################################################################

Launch directory: /opt/foldingathome/config
Executable: ./FAH504-Linux.exe
Arguments: -configonly 

[18:59:55] - Ask before connecting: No
[18:59:55] - User name: shifty_powers (Team 46590)
[18:59:55] - User ID: 1B197884511AC6BC
[18:59:55] - Machine ID: 1
[18:59:55] 
[18:59:55] Configuring Folding@Home...

User name [shifty_powers]? 
Team Number [46590]? 
Ask before fetching/sending work (no/yes) [no]? no
Use proxy (yes/no) [no]? 
Allow receipt of work assignments and return of work results greater than
 5MB in size (such work units may have large memory demands) (no/yes) [yes]? 
Change advanced options (yes/no) [no]? 

[19:00:08] - Ask before connecting: No
[19:00:08] - User name: shifty_powers (Team 46590)
[19:00:08] - User ID: 1B197884511AC6BC
[19:00:08] - Machine ID: 1
[19:00:08] 
[19:00:08] -configonly flag given, so exiting.
/opt/foldingathome/reconfigure.sh: line 23:  7362 Terminated              ./$executable -configonly
cp: cannot stat `/opt/foldingathome/config/mpiexec': No such file or directory

```

---

### Post by Princey on 2008-06-07
Reinstall the client.

---

