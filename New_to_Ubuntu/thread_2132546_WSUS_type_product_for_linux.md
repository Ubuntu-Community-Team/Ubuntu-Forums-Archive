---
title: "WSUS type product for linux"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by wtsn on 2013-04-05
Hi

I am looking for a way to centrally manage updates for our 30 odd Ubuntu servers similar to the WSUS system on Windows.  Ideally it should be run from a central server and have a client installed on remote servers which interacts with apt and allows me to approve an update from some of GUI, ideally a web page. 

I've tried cron-apt but receiving an email from every server which I then have to collate isnt ideal.   I've also tried webmin, which comes close the functionality I want, but has to be installed on each server which also isnt ideal.

I've also looked at using Nagios, but whilst this seems to alert that updates are needed, it doesnt seem possible to approve / install updates.

Landscape also seems to do what we want, but is expensive.

Any suggestions 

Thanks

---

### Post by HermanAB on 2013-04-05
Parallel SSH.

---

