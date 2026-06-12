---
title: "Suspend and Hibernate"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Canis familiaris on 2008-06-30
I dont get it. Whenever I supend or hibernate my desktop, it does so successfully(mostly), but an error comes "Your hardware could not be suspended".
Also hibernate does not work when I try to hibernate Ubuntu with Virtualbox running Windows XP. What exactly is the problem?
Also should I try TuxOnIce or Suspend2Kernel as per [this documentation]("https://help.ubuntu.com/community/Suspend2Kernel").

---

### Post by sdennie on 2008-06-30
I think it's fairly common to get that message even if the suspend was successful.  There should be a button that says, "Don't show me this again" that you can press to get rid of the popup.  You can also look in /var/log/acpid and /var/log/syslog and see if you can figure out why it thinks the suspend wasn't successful.

As for the hibernate problem, are you sure you have enough swap space to cover the hibernate when the VM is running?  That may not be the issue because I've noticed this problem as well but, didn't try to track it down as I only use suspend.

---

### Post by Canis familiaris on 2008-07-01
No I have enough SWAP.

---

### Post by sdennie on 2008-07-01
One thing you could try would be to make a script that gets run on hibernation that saves/restores your VMs for hibernation.  I tried this (without the pm-utils specific stuff) in a "sudo -i" shell and it worked as expected (Using VirtualBox 1.6.0):

```

#!/bin/bash

# Replace this with the user that runs the VMs
VBUSER=your_username

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate)
        rm -f /home/${VBUSER}/.savedvms

        for vm in `su $VBUSER -c "VBoxManage list runningvms | tail -n+4"`; do
            echo $vm >> /home/${VBUSER}/.savedvms
            su $VBUSER -c "VBoxManage controlvm $vm savestate"
        done
    ;;
    thaw)
        for vm in `cat /home/${VBUSER}/.savedvms` ; do
            DISPLAY=:0.0 su $VBUSER -c "VBoxManage startvm $vm"
        done
        
        rm -f /home/${VBUSER}/.savedvms
    ;;
esac

exit 

```

Change your_username to your username, name it 01savevms and install with:

```

sudo install 01savevms /etc/pm/sleep.d

```

That may not be perfect, but, it's the general idea.  Hope that helps.

---

### Post by jnewm on 2009-02-13
Thank you so much sdennie!  Those instructions worked for me.  It's great to be able to hibernate because my Virtualbox is still up and running (and I don't have to wait for a very long virtual boot) when I return from hibernate.

---

