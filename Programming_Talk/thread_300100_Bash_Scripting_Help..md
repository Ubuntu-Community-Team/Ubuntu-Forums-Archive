---
title: "Bash Scripting Help."
date: 2006-11-15
forum: Programming Talk
---

### Post by fishcake007 on 2006-11-15
Some quick ones that I can't seem to place my finger on.

1)How do I execute an entire directory of scripts?

I've tried /.*sh but it doesn't do the trick.

2)How do I execute a script from within another script?


Thanks for your help in advance.

---

### Post by shining on 2006-11-15
1) I'm not sure if there are better ways, but I believe that is one:

```

for i in *.sh; do sh $i; done

```

---

### Post by lkagan on 2006-11-15
run-parts runs all scripts or binaries in a directory.  It's what cron uses to run all jobs in the /etc/cron.daily /etc/cron.hourly, etc... directories.

To run a script from within another script, you can either simply type the full path of the script if it has the shebang, or type the path to the shell that you want to run the script followed by the file name of the script.

HTH

Larry Kagan

---

### Post by fishcake007 on 2006-11-15
Thanks for all your help. Works a treat.

---

