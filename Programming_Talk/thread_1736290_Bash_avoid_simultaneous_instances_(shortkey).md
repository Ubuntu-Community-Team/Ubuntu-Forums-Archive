---
title: "Bash avoid simultaneous instances (shortkey)"
date: 2011-04-22
forum: Programming Talk
---

### Post by Humphreybas on 2011-04-22
The solution to avoid simultaneous running bash script instances from the following page works when I call the script instances from command line:
[http://perplexed.co.uk/498_bash_pid_detection.htm](http://perplexed.co.uk/498_bash_pid_detection.htm)

However when I create a shortkey to activate the script it says: "permission denied for LCK_FILE.lck" or something. And it does not work (I can start multiple instances of the script they don't queue).
I tried to change the rights for the lock file but still no success, anyone some suggestions?

---

