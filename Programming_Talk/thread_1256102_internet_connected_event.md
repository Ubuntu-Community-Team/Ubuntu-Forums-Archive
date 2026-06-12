---
title: "internet connected event"
date: 2009-09-02
forum: Programming Talk
---

### Post by itsalmostreal on 2009-09-02
i have database app that is running on a lamp stack that i want some of my users to be able to take with them and use when not connected to the internet. however, when they do connect to the internet, id like to be able to pass their updates to the 'mother' server. i have all the scripting written, i just dont know how to trigger script to sync the updates.

is there somewhere i can place a command to run when an internet connection become available?

---

### Post by mcla0203 on 2009-09-02
You could make an event if you have a "ping" command... and you know the server, you could ping the server.  You could make some value isInternetOn a boolean assigned to true for Case 2, and regularly check it.

Case 1:  ping times out, not connected to internet or the server is down.
Case 2:  ping responds with success

example.  "ping google.com"

---

### Post by itsalmostreal on 2009-09-02
i guess in theory that could work. i could just run my script via cron every 5 minutes or so, and whenever it does connect it could send the updates.

was just wondering if there was a daemon in linux that run scripts when an internet/network connection is detected.

thanks for your input.

---

### Post by unutbu on 2009-09-02
Perhaps you could use the "dig" command to test if you have a connection:

[php]
#!/bin/sh
dig +time=1 +retry=0 google.com 2>/dev/null 1>&2
if [ "$?" -eq 0 ]; then
    echo "Internet connected"
else
    echo "No internet connection"
fi
[/php]

---

### Post by johnl on 2009-09-02
Hi,

At least under Ubuntu, there should be a NetworkManager DBUS event for the network connection being available.  If you want your program to work correctly on systems without dbus/NetworkmManager, you would need to use a different tactic.

---

### Post by soltanis on 2009-09-02
As I run Fedora, I do not know the exact directory/script for Ubuntu, but I do know that when your internet connection is started, then normally clients run the dhclient program to obtain an IP address. The exception to this rule is clients with static IP addresses, which in my experience is very rare.

Anyway, on F11, adding a script to /etc/dhcp/dhclient.d/ following these rules:
[http://cvs.fedora.redhat.com/viewvc/devel/dhcp/README.dhclient.d?view=co](http://cvs.fedora.redhat.com/viewvc/devel/dhcp/README.dhclient.d?view=co)

Would cause that to be triggered whenever the DHCP client runs (i.e. whenever configuring a network connection). This could be used to notify your script that a network connection is available.

Again, I don't know if Ubuntu has the same directory or the same way of doing things, so you should poke around your own system, but I suspect they are very similar since they use the same dhclient program.

---

### Post by Reiger on 2009-09-03
Can't you simply attempt to sync with the DB every time the app is run (presumably users must pull updates as well?). If that fails (or user configures it that way) continue in offline modus, if it succeeds continue in online modus...

---

