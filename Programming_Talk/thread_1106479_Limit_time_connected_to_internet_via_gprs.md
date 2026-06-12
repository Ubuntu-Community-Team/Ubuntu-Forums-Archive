---
title: "Limit time connected to internet via gprs"
date: 2009-03-25
forum: Programming Talk
---

### Post by UbuKunubi on 2009-03-25
Hello Folks,
Using Ubuntu Hardy and Python 2.4 I have configured a PC that will use pppd to happily connect to the internet. 
Im trying to achieve the following (basically automate the internet connection) :

1) Connect to the internet (send the 'pppd call gprs' command to terminal).
2) perform an internet task (this I've sorted)
3) Disconnect from the internet (send Ctrl 'c' to the abort the gprs connection).

Can anyone please help?
I've gone google blind with trying to solve this for the last month.
The main problem im encountering is conflicting information between the different versions of python, and the different ways of performing commands!

Many thanks in anticipation,
Ubu.

---

### Post by UbuKunubi on 2009-03-26
Bump.

I've been searching further for an answer to this and the more i look, the confused i've become.

dbus, pipes, and ncurses are just some of the topics i've seen. But if anyone can give me nudge in the right direction i'd be grateful.

It seems inordinately difficult to what I thought was an easy task.

Thanks in advance,
Ubu.

---

### Post by UbuKunubi on 2009-03-29
48 hours since Bump.

Is this impossible? Is there no way to use python to send the 'pppd call gprs' command to terminal, and then send the Ctrl+c to the same terminal after 5 minutes?

---

### Post by wmcbrine on 2009-03-30
Back in my dialup days, I used to use something called "diald" for this purpose. It would connect automatically on network activity, and disconnect after a few minutes of inactivity. I just did a brief search, and it looks like it hasn't been updated in ten years, and may or may not still be available. But surely there are modern substitutes. Maybe pppd would even handle it by itself.

As far as getting Python to start and stop pppd, it will be easier if you forget about the terminal. Just use the subprocess module:

```

import os
import signal
import subprocess
import time

pppd = subprocess.Popen(['/usr/bin/pppd', 'call', 'gprs']) # Start pppd
time.sleep(300) # Your five minutes online
os.kill(pppd.pid, signal.SIGINT) # ^C to pppd

```

---

### Post by UbuKunubi on 2009-11-15
> **wmcbrine said:**
> Back in my dialup days, I used to use something called "diald" for this purpose. It would connect automatically on network activity, and disconnect after a few minutes of inactivity. I just did a brief search, and it looks like it hasn't been updated in ten years, and may or may not still be available. But surely there are modern substitutes. Maybe pppd would even handle it by itself.

As far as getting Python to start and stop pppd, it will be easier if you forget about the terminal. Just use the subprocess module:

```

import os
import signal
import subprocess
import time

pppd = subprocess.Popen(['/usr/bin/pppd', 'call', 'gprs']) # Start pppd
time.sleep(300) # Your five minutes online
os.kill(pppd.pid, signal.SIGINT) # ^C to pppd

```

Thanks for your time with that code sample.
I recently had an ISP failure, so was looking for this so I could use my phone as a modem.

This is just the kind of code sample I wanted.
Many thanks,
Ubu.

---

