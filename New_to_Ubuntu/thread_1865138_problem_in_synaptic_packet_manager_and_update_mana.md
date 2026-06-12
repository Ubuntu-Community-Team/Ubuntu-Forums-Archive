---
title: "problem in synaptic packet manager and update manager"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by neelk on 2011-10-19
when open it and inter the password show this 
E: Malformed line 63 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
########################################

when open update manager appear this massege 


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 63 in source list /etc/apt/sources.list (URI parse)'
any help

---

### Post by ajgreeny on 2011-10-19
Open a terminal and use the command ```
gedit /etc/apt/sources.list
```to open that file and look at line 63, and copy that line back here if you can not see the problem.

To open it with permissions to edit it use command ```
gksu gedit /etc/apt/sources.list
```but wait for a response from this forum first if you can not see a problem with that line 63.

---

### Post by neelk on 2011-10-20
[FONT=monospace]deb maverick contrib






if i made mistake please your patient beginner
[/FONT]

---

### Post by mcduck on 2011-10-20
Well, that definitely isn't a proper repository entry. You can either remove the line, or comment it out by adding a "#" to the beginning of the line.

After that save the file and run "sudo apt-get update". The problem should be fixed, but if you get any more errors please post them here.

---

### Post by neelk on 2011-11-10
fixed thank you

---

