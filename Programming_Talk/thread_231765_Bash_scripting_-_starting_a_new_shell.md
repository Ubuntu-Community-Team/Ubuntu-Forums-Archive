---
title: "Bash scripting - starting a new shell"
date: 2006-08-07
forum: Programming Talk
---

### Post by endfx on 2006-08-07
Is there a way to start a script/program in a new shell from a bash script.

I'm writing a script and I start a never ending program, and 5 seconds after this never ending program starts, I want to start another program.

---

### Post by KaeseEs on 2006-08-08
To call a new shell to execute something, use 
```
/bin/bash -c "/path/to/prog"
```

However, for your purposes, you may be better off investigating the sleep command, which waits for a specific amount of time before running the next command ( try 'man sleep' ).

---

### Post by bzhao on 2008-05-06
> **endfx said:**
> Is there a way to start a script/program in a new shell from a bash script.

I'm writing a script and I start a never ending program, and 5 seconds after this never ending program starts, I want to start another program.


Maybe you don't need a new shell.
& will make your program go to backdesk.

Like:
  
....
your_neverend_program &
sleep 5
your another program
....

---

### Post by ldevil on 2008-11-24
I currently try to get some (endless) scripts to startup automatically. I did get yet that I can use a sym. link in /etc/rc2.d/ to start the scripts but then the startup will block, so I thought I can just start them in a new console or backdesk.
As I could not get a new console with "/bin/bash -c" i tried following:

symlink in /etc/rc2.d/ to following script (in /etc/init.d/):

```
#!/bin/bash
/home/aslca/scripts/getnewreq.sh $
/home/aslca/scripts/getnewrevoke.sh $
/home/aslca/scripts/getnewrevokeall.sh $
/home/aslca/scripts/backup.sh $
/home/aslca/scripts/updatestats.sh $
```

All scripts need to be run as root and are endless, they will login to another virtual machine and pull/post some files. But they dont seem to be running when I log in.

All the scripts work when I start them as root, but not with 'sudo'.

Any ideas how I can get those scripts to be executed at startup/login so they will do their work?

Oh and is there a way to get the ourput of the scripts redirected to a log file?
edit: found how to redirect output:
```
exec >> some.log 2>&1
```

edit2: Hm, now with the log working I see that the problem is a different one... the script does not seem to be executed as root :(

---

### Post by geirha on 2008-11-25
You want to end the lines with &, not $ ...

---

