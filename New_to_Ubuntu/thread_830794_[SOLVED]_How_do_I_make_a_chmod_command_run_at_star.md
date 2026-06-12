---
title: "[SOLVED] How do I make a chmod command run at startup?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by bwallum on 2008-06-16
Hi

I need to use the following command to give user access to my scanner on /dev/sg4 (it defaults to root only)

```
sudo chmod o=+rw /dev/sg4
```

Where can I put this command so that it runs automatically when Ubuntu is loaded?

---

### Post by wormser on 2008-06-16
I believe all you have to add the User Privilege for scanners.  

System> Administration> User and Groups> Unlock> select user> Properties> User Privileges tab> check Use scanners.

---

### Post by pedro_orange on 2008-06-16
I guess if that above didn't work you could add the command to the /etc/rc.local

---

### Post by bwallum on 2008-06-16
Hole in one! Thanks!

---

### Post by bwallum on 2008-06-16
Hi Pedro

I am interested in your non gui solution. My /etc/rc.local file reads:> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

The following worked ok.
> !/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo chmod o=+rw /dev/sg4
exit 0

However when I then go to check permissions for scanner through the gui approach above the check box is not ticked. So, it works but it doesn't seem to be 'integrated'. Is there another file that contains permissions?

---

### Post by wormser on 2008-06-16
What worked?  I'd like to know.  Click the star on the post that helped and mark it resolved when you are done with the thread.

---

### Post by bwallum on 2008-06-17
SOLUTION
How to give a user permission to run hardware that may by default be installed as useable by root only. e.g. a scanner. This solution ensures that permissions are automatically loaded at boot.

The GUI way by wormser:

System> Administration> User and Groups> Unlock> select user> Properties> User Privileges tab> check Use scanners.

The CLI way by pedro_orange
Open the /etc/rc.local file
```
gksudo gedit /etc/rc.local
``` the default file reads:

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
Change this file by taking out the hash on the first line and adding an appropriate chmod command before 'exit 0'. In the following a scsi scanner is at /dev/sg4.

Try this thread if you need to set up a scsi scanner
[http://ubuntuforums.org/showthread.php?t=826722]("http://ubuntuforums.org/showthread.php?t=826722")

> !/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo chmod o=+rw /dev/sg4
exit 0
However when I then go to check permissions for scanner through the gui approach above the check box is not ticked. So, it works but it doesn't seem to be fully 'joined up'.

---

### Post by anjexe on 2011-04-05
how to run this commands at start up inubuntu 10.10

sudo insmod acpi_call.ko

./test_off.sh

tnx

---

### Post by Elfy on 2011-04-05
Closed - please start your own thread.

---

