---
title: "Can I change my username?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-08-01
I'd like to change my username on Ubuntu (the one I registered when I first installed).  Is this possible?  Will it affect files that are currently referencing /home/currentusername ?

---

### Post by dca on 2008-08-01
Go to 'System -> Administration -> Users & Groups' from main menu bar and then click 'Unlock' button and see if it lets you there.

---

### Post by dca on 2008-08-01
You may have to log out and log back in again.

---

### Post by prshah on 2008-08-01
> **TMcKSmith said:**
> I'd like to change my username on Ubuntu (the one I registered when I first installed).  Is this possible?  Will it affect files that are currently referencing /home/currentusername ?

You can change your username by booting into the recovery console, then giving the command ```

usermod -l newname -m -d /home/newname oldname
```this will change your username from oldname to newname, create an appropriate home folder, and copy your files into the new home folder, and set permissions and ownerships accordingly.

You need to do this in the recovery console because usermod will not allow changes to the name of a logged-in user.

Note that this may still cause problems; eg. any cron jobs etc setup in the old username will not be migrated automatically.

In short, unless you have a compelling reason to change the name, don't do it.

---

### Post by sub2007 on 2008-08-01
Thanks a lot, I've been looking for this for ages.

Only thing is that the code won't work unless it reads like this:

```
usermod -l newname -d /home/newname -m oldname
```

You may have to reset up your sudoers file as well if you do this on your root account. If your new username breaks your sudo you can't fix it easily (as ironically you would need root access for that) so it would be a good idea to either add your new username to the sudo file using visudo or create a new account with sudo privileges that you can log in as just in case you break it.

---

### Post by bver on 2011-07-26
worked perfectly.

The only issue i had was it still said my old username at the login screen. A quick edit of /etc/passwd solved that though.

---

### Post by Cr0mC0rrag on 2012-09-08
So... we have:

Log onto recovery console, then:

usermod -1 newname -m -d /home/newname oldname

OR

usermod -1 newname -d /home/newname -m oldname

OR

sudo usermod -1 oldname newname

SO which one is the right one? AND what is the -1? Is that a ONE, an L? Lower case l? An I?

Thx

---

### Post by oldos2er on 2012-09-08
Please start a new thread, this one's quite old.

---

