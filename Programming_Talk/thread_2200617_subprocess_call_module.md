---
title: "subprocess call module"
date: 2014-01-20
forum: Programming Talk
---

### Post by wingnut2626 on 2014-01-20
here is the code:
```

subprocess.getoutput(['php','package.php',directory+'/kaltura-installer', 'false', 'CE v6.0.0 dev'])
```

The subprocess call ends after the directory+'/kaltura-installer', and is ignoring anything after that.  Any ideas of how to make subprocess call the entire string?

PS.  directory is defined as /home/user

---

### Post by wingnut2626 on 2014-01-20
its subprocess call by the way.  sorry just noticed that

---

### Post by Bachstelze on 2014-01-20
[It seems]("http://docs.python.org/3.2/library/subprocess.html#subprocess.getoutput") that [font=monospace]subprocess.getoutput()[/font] takes a string as argument...

---

