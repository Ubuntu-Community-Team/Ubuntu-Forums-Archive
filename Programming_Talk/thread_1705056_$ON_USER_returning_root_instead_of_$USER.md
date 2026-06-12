---
title: "$ON_USER returning root instead of $USER"
date: 2011-03-11
forum: Programming Talk
---

### Post by Cypher2 on 2011-03-11
Hello everybody!

With Natty coming out soon, I've been at work updating my deployment and self-config script to make my desktop on 11.04 run and look the way I want it to.

One bummer is that dbus seems to have changed and does not permit, in the same manner Lucid and Maverick did, the authentication of the current user by terminal call using grep and cat.

Ideally, to run the script, I would sudo -s and then launch it as

/# chmod +x install && ./install

Instead of returning my user name.. it now returns root and applies changes to the root profile and aborts whenever paths do not correspond.

Here is my script header:

----------------------

#!/bin/bash

ON_USER=$(echo ~ | awk -F'/' '{ print $1 $2 $3 }' | sed 's/home//g')

export $(grep -v "^#" ~/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)

if sudo -u $ON_USER test -z "$DBUS_SESSION_BUS_ADDRESS" ;
then eval `sudo -u $ON_USER dbus-launch --sh-syntax --exit-with-session`
fi

RELEASE=$(lsb_release -cs)

----------------------

How could I make it return the actual user now that natty is coming?

Thanks for the help

---

