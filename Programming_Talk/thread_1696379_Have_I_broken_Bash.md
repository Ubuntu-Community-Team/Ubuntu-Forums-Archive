---
title: "Have I broken Bash?"
date: 2011-02-27
forum: Programming Talk
---

### Post by dartdog on 2011-02-27
Ubuntu 10.10
I created a bash file called run and attempt to invoke it as ./run
The file contents are
#!/bin/bash python2.5 ${HOME}/Projects/gae/google_appengine/dev_appserver.py ./ 
I previously used ~ instead of ${HOME} with no difference.
I just get
>>>I get file not found::
/bin/bash: python2.5 ~/Projects/gae/google_appengine/dev_appserver.py ./: No such file or directory

the  Command :"bash -x ./run"  just returns to the prompt>> 

I'm wondering if I have somehow messed up the terminal, or Bash control file (not intentionally! I've made no direct edits..) how or should I reset it?

When I enter the command "python2.5 ~/Projects/gae/google_appengine/dev_appserver.py ./" in the shell vs using the bash file..it works fine

---

### Post by gmargo on 2011-02-27
> **dartdog said:**
> Ubuntu 10.10
I created a bash file called run and attempt to invoke it as ./run
The file contents are
#!/bin/bash python2.5 ${HOME}/Projects/gae/google_appengine/dev_appserver.py ./ 


Is that all on one line?  You have to put commands after the shebang line:
```

#!/bin/bash 
python2.5 ${HOME}/Projects/gae/google_appengine/dev_appserver.py ./ 

```(You don't need bash in this case, could use #!/bin/sh)

---

### Post by dartdog on 2011-02-27
Well dang!! It is always those simple things, the ones that most docs don't mention or mention in some way that newbs like me miss!

Thank you
Worked like a charm..:KS

---

