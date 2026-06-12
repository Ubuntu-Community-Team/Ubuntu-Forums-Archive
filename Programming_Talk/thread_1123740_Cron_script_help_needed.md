---
title: "Cron script help needed"
date: 2009-04-12
forum: Programming Talk
---

### Post by autocrosser on 2009-04-12
I've made a script to restart Gkrellm when it is not running--It "mostly" works, but when cron uses it a terminal window opens--I'm stuck & could use a bit of help---

```
#
!/bin/bash
#restart-process.sh

NOPROCESS=2

process=gkrellm  

t=`pidof $process`       # Find pid (process id) of $process.
# The pid is needed.

if [ -z "$t" ]           # If process not present, 'pidof' returns null.
then
  gkrellm & exit 0
fi  

  echo "Process $process was running."
  exit $NOPROCESS

exit 0

```

Could someone point out where I've gone wrong?

---

