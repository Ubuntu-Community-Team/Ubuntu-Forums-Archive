---
title: "invoke root inside script"
date: 2007-10-19
forum: Programming Talk
---

### Post by svalding on 2007-10-19
does anyone know of a way to envoke root from inside of a shell script? I have a need to use a script to automatically update some software on a weekly basis, and can't seem to think of the best way to do it. I know becoming root in a script isn't entirely the smartest way to go about to though too. Is there a way I could set the script maybe as a cron job and execute it as root that way? any advice would be wonderful!

---

### Post by tkharris on 2007-10-19
Do not become root inside of a script, it's very bad.  Root should only be used as a last resort.

Instead write your script ( if it's connecting to untrusted _anything_ don't run it as root ) toss it into /root/bin/ ( or even /sbin/ ) and then run it from root's crontab or make an entry for it in /etc/cron.d/

---

