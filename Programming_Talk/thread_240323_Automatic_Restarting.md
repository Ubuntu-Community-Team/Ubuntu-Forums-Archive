---
title: "Automatic Restarting"
date: 2006-08-20
forum: Programming Talk
---

### Post by musther on 2006-08-20
Some scripting I'm working on (wont go into details now) requires the machine to be restarted and then shutdown to halt:

1 Script Runs
2 Machine restarts
3 After booting is completed, the machine automatically shuts down and halts

So I'm looking for a way to pull this off, there must be something I can do, for example make the script create a small script file in an rc directory such that the shutdown will occur.  If I place a script with the 'shutdown -h now' command in rc5, would that work?  Also, how do I get the script to do this, I know I can use touch to create the file, but how do I put content in it, and I can I get it to delete itself so that it doesn't shut the machine down every time.

Thanks for your help.

---

