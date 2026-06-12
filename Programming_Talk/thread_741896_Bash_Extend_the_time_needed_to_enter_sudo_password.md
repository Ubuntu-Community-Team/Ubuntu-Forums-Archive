---
title: "Bash: Extend the time needed to enter sudo password"
date: 2008-04-01
forum: Programming Talk
---

### Post by rockstar82 on 2008-04-01
I am writing a backup-script using tar, with an option to automaticly shutdown computer when finished.

The problem is that the backup takes different amount of time to complete, which forces me to enter the sudo password again to shutdown. The script is meant to be unattended.

The script is made for use on both server/desktop-systems, so running the script as root is not an option.

Is there a way to temporarily extend the time to enter the sudo password?

---

### Post by shawnhcorey on 2008-04-01
You shouldn't use sudo inside a script.  Remove it from your script and run it with sudo on the command line:
```
sudo my_backup_script
```

---

### Post by stroyan on 2008-04-01
As 'man sudo' notes, you can run 'sudo -v' to extend the sudo timeout.
You could have your script run a little background loop that would sleep for
a while and invoke 'sudo -v' occasionally.

I don't know if that is really a good idea.  It does reduce security as
it extends the time that other shells of that user have to sudo without
any password.

It is also possible to change the sudo timeout in /etc/sudoers .
That would make security even more lax.

---

### Post by shawnhcorey on 2008-04-01
If you put sudo inside a script, you have already compromised security, so it's not a big problem to extend its timeout.

As I said, run the script from the command line using sudo is the best way.

And backups should be done by hand.  The first time you try to retrieve a file from backup and discover that the automatic backup hasn't worked in 6 months, you'll understand why.  (Of course, this has never happen to me, it happen to a...er...friend of a friend, yeah, that's it ;)

---

### Post by rockstar82 on 2008-04-01
> **stroyan said:**
> As 'man sudo' notes, you can run 'sudo -v' to extend the sudo timeout.
You could have your script run a little background loop that would sleep for
a while and invoke 'sudo -v' occasionally.

That was exactly what i was looking for. Thanks!

In future scripts I will force the user to run it from sudo instead.

---

