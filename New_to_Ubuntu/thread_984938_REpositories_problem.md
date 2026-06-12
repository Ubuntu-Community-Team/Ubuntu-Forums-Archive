---
title: "REpositories problem"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by jay300zx on 2008-11-17
Just installed Ubuntu 8.10 on my Toshiba Laptop, when I goto Synaptic package manager and type in Kismet - nothing is shown - this should be a point and click affair from the repositories I thought?

Any ideas on where to start?  I did install K3B and that downloaded and installed ok.

Thanks

---

### Post by rampageoberon on 2008-11-17
Kismet package is in the universe repository. Make sure this is enabled. Check System -> Administration -> Software Sources and then try again.

Hope that helps.

---

### Post by stephanvaningen on 2008-11-17
In my distro (8.10) kismet is indeed available in the list. Do System -> Administration -> Software sources and verify if these settings look ok (not CD-ROM selected, 
Also do a update (while synaptic is not active):
 sudo apt-get update
and check after that if kismet is not yet in the list...

---

### Post by jay300zx on 2008-11-17
Cheers lads.
Universe was working but reloaded just to be sure

still not there, so I ran the sudo get-apt update from terminal then it appeared :)

Its not under the quicksearch, but when I click the search button it comes up and is now installing.

Thanks for your help

---

### Post by stephanvaningen on 2008-11-17
My pleasure,

please tag the thread as [solved] (right-top 'thread tools'...)

---

