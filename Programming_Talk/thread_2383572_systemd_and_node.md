---
title: "systemd and node"
date: 2018-01-26
forum: Programming Talk
---

### Post by Notre on 2018-01-26
Hi,

I'm trying to automatically start my node application when Ubuntu starts up.  I ran across this page, which suggests using systemd:

[http://nodesource.com/blog/running-your-node-js-app-with-systemd-part-1/](http://nodesource.com/blog/running-your-node-js-app-with-systemd-part-1/)

I tried following the steps, except with my own node application.  When I try to start the service with:

sudo systemctl start automation-server

and then query the status:

sudo systemctl status automation-server

for a brief moment it looks like it worked.  But checking status shortly afterwards reveals it has failed:

```
&#9679; automation-server.service - server.js - home automation server
   Loaded: loaded (/lib/systemd/system/automation-server.service; disabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Fri 2018-01-26 19:39:30 PST; 36ms ago
  Process: 29218 ExecStart=/usr/bin/node /home/trevor/automation-server/server.js (code=exited, status=1/FAILURE)
 Main PID: 29218 (code=exited, status=1/FAILURE)


Jan 26 19:39:30 trevor-ubuntu systemd[1]: automation-server.service: Main process exited, code=exited, status=1/FAILURE
Jan 26 19:39:30 trevor-ubuntu systemd[1]: automation-server.service: Unit entered failed state.
Jan 26 19:39:30 trevor-ubuntu systemd[1]: automation-server.service: Failed with result 'exit-code'.



```

I'm not sure how I should go about troubleshooting why it's failing. When I run the application interactive, in the console it works okay. Any suggestions?

If this is the wrong forum, please feel free to point me to another one.  Thank you!

---

### Post by Notre on 2018-01-26
I found the problem. I needed to add:
WorkingDirectory=/home/trevor/automation-server

to the service section, since I was doing some IO in that folder.  Thanks!

---

