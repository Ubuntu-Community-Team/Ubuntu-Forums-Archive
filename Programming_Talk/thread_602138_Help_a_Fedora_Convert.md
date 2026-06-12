---
title: "Help a Fedora Convert"
date: 2007-11-03
forum: Programming Talk
---

### Post by ubuntology on 2007-11-03
In fedora, if I wanted to restart ssh or httpd, the command was: service httpd restart

I'm trying to recreate that functionality in Ubuntu with a simple bash script.
I have it working if I call it after sudo, but I want it to ask for the password if I forget, and return an error if the service name doesn't exist. Can anyone help?
Here's what I have so far.

```
#!/bin/bash
# Make sure we're run as root.
if [ ! $( id -u ) -eq 0 ]; then
        echo "Please enter password."
        sudo "${0} ${1} ${2}"
        exit ${?}
fi

# Make sure the service is found in /etc/init.d/
if [ ! -e /etc/init.d/$1 ]; then
        echo 'Service not found in /etc/init.d'
        exit ${?}
fi

/etc/init.d/$1 $2
exit

```

---

### Post by xtacocorex on 2007-11-04
I had a script just like this on my Dell running Edgy, but the machine won't start.  

sudo keeps the password for 15 minutes I think and will then destroy it; the next time you use it after that period, it asks for the password.

You could do the following with the code, since it will need sudo to run anyway:
```

#!/bin/bash

# Make sure the service is found in /etc/init.d/
if [ ! -e /etc/init.d/$1 ]; then
        echo 'Service not found in /etc/init.d'
        exit ${?}
fi

sudo /etc/init.d/$1 $2

```

---

### Post by slavik on 2007-11-04
why not just use sudo directly to restart it?

---

### Post by ubuntology on 2007-11-04
> **slavik said:**
> why not just use sudo directly to restart it?

If you mean to use something like: sudo /etc/init.d/ssh restart
Well, I'm afraid I just don't want to. Sorry, I don't have a better answer than that, but I've been a Red Hat/Fedora user for around 10 years, and I like the service command.

---

### Post by xtacocorex on 2007-11-04
> **ubuntology said:**
> If you mean to use something like: sudo /etc/init.d/ssh restart
That's what your and my code does.  It's still callable by "service" and will prompt for password when needed.

FYI, somewhere floating around the forum is a post that has a script that sort of mimics chkconfig; it's not the real deal, but does work.

---

### Post by ubuntology on 2007-11-04
> **xtacocorex said:**
> That's what your and my code does.  It's still callable by "service" and will prompt for password when needed.

FYI, somewhere floating around the forum is a post that has a script that sort of mimics chkconfig; it's not the real deal, but does work.

Awesome. Thanks man.

---

