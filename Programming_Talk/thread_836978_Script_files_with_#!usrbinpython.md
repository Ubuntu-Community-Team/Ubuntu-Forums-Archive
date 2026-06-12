---
title: "Script files with #!/usr/bin/python"
date: 2008-06-22
forum: Programming Talk
---

### Post by bogdanbiv on 2008-06-22
Context: Kubuntu 8.04

Q: How can I make python scripts executable like #!/bin/bash?

Besides hardcoding the path to the python executable (#!/usr/bin/python), I saw there is a way to use env instead:
#!/usr/bin/env python

(hardcoding env instead)

Trouble is that neither #!/usr/bin/python nor the env way do work.
This is just a programming exercise for me.

---

### Post by OutOfReach on 2008-06-22
Right click on the file, Properties > Permissions, Find Execute:, is the box next to that checked? If not, check it.

Theres also a terminal command that sets the file to be able to execute as a program, but I cant recall what it was sorry.

---

### Post by bogdanbiv on 2008-06-22
The command for activating the executable permission is "chmod +x file_name_here"

Sorry for not giving an example earlier:
bog@bog-desktop:/media/CORSAIR/projects/pythontest/src$ ls -lt
total 32
-rwxr-xr-x 1 bog root  20 2008-06-22 09:00 script
-rwxr-xr-x 1 bog root  42 2008-06-22 08:24 cgi.py

Contents of ./script :
#!/bin/bash
ls $HOME

Contents of cgi.py:
#!/usr/bin/env python
print "Hello cgi!"

when I type ./script I get the list of files in my home dir - so bash scripting works
when I type ./cgi.py I get "bash: cgi.py: command not found"

**UPDATE:**
It works now!
bog@bog-desktop:/media/CORSAIR/projects/pythontest/src$ ./cgi.py
Hello cgi!
bog@bog-desktop:/media/CORSAIR/projects/pythontest/src$ cgi.py
bash: cgi.py: command not found

*So all I had to do was to type ./ before the filename (./cgi.py)*

---

