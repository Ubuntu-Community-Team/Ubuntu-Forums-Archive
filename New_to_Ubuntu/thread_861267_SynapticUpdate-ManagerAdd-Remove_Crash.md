---
title: "Synaptic/Update-Manager/Add-Remove Crash"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by MothHunter on 2008-07-16
I am running 8.04 Ubuntu hardy heron.

Update-manager, Synaptic and Add/Remove Program applications all crash immediately after loading... everything else is a-ok...

I don't know how to problem solve in Ubuntu - everything in the system monitor looks fine. Restarting didn't help.

Any ideas?  Thanks.

---

### Post by benfindlay on 2008-07-16
Do any error messages come up? If so can you post them?

Alternatively, once you have booted up try ```
sudo apt-get update
```followed by ```
sudo apt-get upgrade
``` and see if there are any error messages following either of those commands

Cheers
Ben

---

### Post by MothHunter on 2008-07-16
Ahh! Thankyou so much!  No error messages came up, but running Update through the terminal sovled the issue - all three programs now run :)

...I have written the code down for future use... ^^;

---

### Post by benfindlay on 2008-07-16
No problems, in fact you can combine them into one command, which is ```
sudo apt-get update && sudo apt-get upgrade
```
This does the same as the update manager GUI, just without the front end.

---

