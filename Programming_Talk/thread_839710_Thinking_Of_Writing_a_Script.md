---
title: "Thinking Of Writing a Script"
date: 2008-06-24
forum: Programming Talk
---

### Post by Nullack on 2008-06-24
Im a beginner programmer and Im thinking of writing a script to overcome a problem Im having with Ushare (upnp media server).

Ushare requires root permissions but wont run as a deamon. If I put an exception in sudoers and add a session for it to execute, this breaks when the user loggs out and reloggs back in because then two sessions are running. Ushare doesnt quit when the user loggs.

So I was thinking of something like:

1. Get list of processes
2. Idenytify if ushare is in the list
3. If exists dont run another
4. Else execute ushare

Or is this really a clumsy hack and theres a superior way for me to go here?

---

### Post by geirha on 2008-06-24
Change /usr/bin/ushare with the full path of the executable if my guessed one is incorrect.
[php]
usharepid=`pidof /usr/bin/ushare`
if [ -n "$usharepid" ]; then
  echo "ushare is running with pid $usharepid"
else
  echo "ushare is not running"
fi
[/php]

EDIT: And reading your post more closely; do you want ushare to be running all the time? if so, just add it to the /etc/rc.local script. It is run (as root) during boot, just before the login-screen appears.

---

