---
title: "My startup script doesn't work"
date: 2007-04-07
forum: Programming Talk
---

### Post by KrazyPenguin on 2007-04-07
Can somebody please take a look at this script for me and tell me why gdesklets and skype don't start?
(Running Fiesty)


[B]#!/bin/bash
PATH=$PATH:$HOME/bin
echo *password* | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

# Delay Firestarter, since an error occurs before the wireless network is found
sleep 30s; sudo firestarter --start-hidden
sleep 10s; gdesklets &

#Delay Skype
sleep 50s; skype
[/B]

This script allows me to automatically login without having to type in the keyring password.

Firestarter starts but gdesklets and skype don't start, even if I wait a long time.

Thanks.

---

### Post by kaamos on 2007-04-07
Are you missing a & after "firestarter --start-hidden" ?

---

### Post by KrazyPenguin on 2007-04-07
> **kaamos said:**
> Are you missing a & after "firestarter --start-hidden" ?

I don't think so.

I did a logoff and logged back in and gdesklets gave me a crash error (which i reported) and skype started.

So the script does work, but not on the initial startup.

---

