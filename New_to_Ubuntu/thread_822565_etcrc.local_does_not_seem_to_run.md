---
title: "/etc/rc.local does not seem to run?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Twizzle on 2008-06-08
I am running 8.04 server edition on a headless machine.

I have set my /etc/rc.local script to include:

```
sudo -u john screen -dmS hellanzb hellanzb
```

The rest of it is as it was on install, ie nothing really.

It will run if I just run in from a command prompt, but on reboot does not seem to do anything. I have chmod 777 /etc/rc.local but still nothing.

All I want to do is have my server running hellanzb at boot without having to login and start it.

I have read a number of posts about this and as far as I can understand, the above *should* work!

---

### Post by quelx on 2008-06-08
If it's in rc.local (which is run with root priveledges anyway) I think the line should be
```
su - john -c screen -dmS hellanzb hellanzb
```

---

### Post by Twizzle on 2008-06-08
No that did not work either.

I thought that I needed the -u switch to change the user?

I have also triedsaving the contents of my 'rc.local' as 'myscript' into 
/etc/init.d/ , chmod 755 it and then running:

```
update-rc.d myscript defaults
```

but that did not work either.

---

### Post by quelx on 2008-06-08
For BSD but should apply here too
[http://groups.google.com/group/lucky.freebsd.questions/browse_thread/thread/00b6a2a0b2e7f764](http://groups.google.com/group/lucky.freebsd.questions/browse_thread/thread/00b6a2a0b2e7f764)

---

