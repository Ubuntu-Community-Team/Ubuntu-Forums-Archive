---
title: "Using inittab to respawn a process if it dies"
date: 2007-10-03
forum: Programming Talk
---

### Post by saracen on 2007-10-03
I have a bash script that sets up some environment variables and on the last line starts up a server that runs in the background (using the 'nohup' command).  The script is named 'setup' and the server command is called 'server'.  When i run the script the process that stays running in the background is the 'server' process.  The script itself terminates.

How can I tell inittab to watch the server process, and then if it terminates to run the startup script?  I noticed that for inittab you can only specify one command to watch and it will respawn that same command.... :confused:

---

### Post by mssever on 2007-10-03
You need [Upstart]("http://upstart.ubuntu.com/").

---

### Post by jluce on 2010-01-29
Upstart looks good, but without documentation anything other than trivial init files are downright impossible!

---

### Post by falconindy on 2010-01-29
You certainly don't need upstart. 'man inittab' is probably going to be useful for you. I think you need to restructure your 2 scripts into a single one.

---

