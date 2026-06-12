---
title: "partial install of lamp through tasksel"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-06-03
I tried to install lamp through tasksel by sudo tasksel lamp-server.  The install stayed at 0 percent for awhile then I closed the terminal.  It looks like I have a partial install of a lamp server
```
david@laptopish:~$ httpd
bash: httpd: command not found
david@laptopish:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
david@laptopish:~$ 

```
by typing sudo tasksel it says that a lamp server is not installed.

Does anyone know how to completely redo the install of a lamp server and start from scratch?

---

### Post by rraj.be on 2008-06-03
to remove you can use

```
tasksel remove <task>

```

you can get help regarding any thing in terminal by just typing partial command or by typing 

man <command>

for tacksel i got

```
Usage:
tasksel install <task>
tasksel remove <task>
tasksel [options]
	-t, --test          test mode; don't really do anything
	    --new-install   automatically install some tasks
	    --list-tasks    list tasks that would be displayed and exit
	    --task-packages list available packages in a task
	    --task-desc     returns the description of a task

```

try this

---

