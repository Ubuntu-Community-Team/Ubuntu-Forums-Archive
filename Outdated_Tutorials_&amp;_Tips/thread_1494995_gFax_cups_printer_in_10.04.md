---
title: "gFax cups printer in 10.04"
date: 2010-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by cheesyking on 2010-05-27
so gfax 0.7.7 (in 10.04) can finally be printed to directly from any application... but it isn't setup automatically for some reason (maybe I should report a bug?)

If you install from source there's a "postinstall.sh" script that you're supposed to run but this doesn't seem to happen when you install through the repos. This script creates a spool dir for gfax and adds the printer to cups so without it gfax won't even start (since it can't find the spool dir) and explains why cups printing doesn't work

Anyhow here's how to make the changes manually:

```

sudo mkdir -m 777 /var/spool/gfax
sudo cp -f /usr/lib/gfax/cups-gfax /usr/lib/cups/backend/
sudo chmod 755 /usr/lib/cups/backend/cups-gfax
sudo ln -sf /usr/lib/cups/backend/cups-gfax /usr/lib/cups/backend-available/cups-gfax
sudo lpadmin -p Gfax_Facsimile_Printer -v cups-gfax:/ -m lsb/usr/cups-included/postscript.ppd -E
```

You also need to make sure gfax is running before you try to print to it! I suggest creating an entry in System->Preferences->Startup Applications with the command "gfax" and making sure you don't accidentally close it.

NB I also had to restart before it would work, even though I restarted cups (well I think I did anyway :wink: )


Here's the original script:
```
#!/bin/bash
if [ ! -d /var/spool/gfax ]; then
   mkdir -m 777 /var/spool/gfax
   chown root:root /var/spool/gfax
fi
cp -f /usr/lib/gfax/cups-gfax /usr/lib/cups/backend/
chmod 755 /usr/lib/cups/backend/cups-gfax
ln -sf /usr/lib/cups/backend/cups-gfax /usr/lib/cups/backend-available/cups-gfax
lpadmin -p Gfax_Facsimile_Printer -v cups-gfax:/ -m lsb/usr/cups-included/postscript.ppd -E
gconf-schemas --register /etc/gconf/schemas/gfax.schemas
```

I suppose you could just remove that last line about gconf and sudo that script anyway.

---

### Post by maxter on 2010-07-23
many many thanks cheesyking
it works like a charm :)

---

### Post by nicholse on 2010-11-05
sudo mkdir -m 770 /var/spool/gfax
sudo chgrp dialout /var/spool/gfax

Those first two lines would be more secure like this.

---

### Post by ylavi on 2011-03-29
I was struggling with printing to the GFax printer for a long time.
After all the setup above which let me get the GFax program started, I still couldn't print and have the program pop up.

If you encounter this problem, where CUPS reports errors involving cpdftocps try changing the permissions of /usr/lib/cups/backend/cups-gfax to 744. Apparently as 755 the backend runs as some user (group?) which doesn't have permission for /var/spool/gfax but with 744 it's forced to run as root and then all works well.

---

