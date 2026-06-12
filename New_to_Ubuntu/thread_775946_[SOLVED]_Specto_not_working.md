---
title: "[SOLVED] Specto not working?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-04-30
Hi, i recently installed specto on ubuntu hardy heron and it worked fine for about a week but now when i click the icon on the menu the cursor just changes to loading and then nothing happens? can anyone help me sort this out...

thanks in advance:lolflag:

---

### Post by kamitsukai on 2008-04-30
so know one has any ideas? (this may infact look like a bump but its in fact a question LMAO :P)

---

### Post by dangerpl on 2008-04-30
run it from the Terminal and see what kind of errors you get.

---

### Post by kamitsukai on 2008-04-30
> **dangerpl said:**
> run it from the Terminal and see what kind of errors you get.

thanks this is what i get...looks worrying

```
dreamsofubuntu@dreamsofubuntu-desktop:~$ specto
Traceback (most recent call last):
  File "/usr/bin/specto", line 38, in <module>
    specto = Specto()
  File "/usr/lib/python2.5/site-packages/spectlib/main.py", line 100, in __init__
    self.watch_io = Watch_io()
  File "/usr/lib/python2.5/site-packages/spectlib/watch.py", line 174, in __init__
    self.cfg = ini_namespace(file(self.file_name))
  File "/usr/lib/python2.5/site-packages/spectlib/iniparser.py", line 621, in __init__
    self.readfp(fp)
  File "/usr/lib/python2.5/site-packages/spectlib/iniparser.py", line 762, in readfp
    raise exc
ConfigParser.ParsingError: File contains parsing errors: /home/dreamsofubuntu/.specto/watches.list
	[line  9]: [[Nifty] Running away]

Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_specto.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/specto", line 38, in <module>
    specto = Specto()
  File "/usr/lib/python2.5/site-packages/spectlib/main.py", line 100, in __init__
    self.watch_io = Watch_io()
  File "/usr/lib/python2.5/site-packages/spectlib/watch.py", line 174, in __init__
    self.cfg = ini_namespace(file(self.file_name))
  File "/usr/lib/python2.5/site-packages/spectlib/iniparser.py", line 621, in __init__
    self.readfp(fp)
  File "/usr/lib/python2.5/site-packages/spectlib/iniparser.py", line 762, in readfp
    raise exc
ConfigParser.ParsingError: File contains parsing errors: /home/dreamsofubuntu/.specto/watches.list
	[line  9]: [[Nifty] Running away]

```

---

### Post by it.henrik on 2008-04-30
It seems like this file has been corupted or specto has been updated and cant understand its own file anymore 

/home/dreamsofubuntu/.specto/watches.list

I dont know how specto works but if you make a backup and add new watches to specto it should work.

try this 
mv /home/dreamsofubuntu/.specto/watches.list /home/dreamsofubuntu/.specto/watches.list.backup

and if it fails and nothing works anymore you can put everything back like this

mv /home/dreamsofubuntu/.specto/watches.list.backup /home/dreamsofubuntu/.specto/watches.list

---

### Post by kamitsukai on 2008-04-30
Wow thanks it.henrik it worked great :) i wonder what caused this though? as ive only updated once and that was only for awn....strange

---

### Post by G|N| on 2008-05-05
Your problem was that u use brackets in your watch name.
This is not supported in version 0.2.2 (but it will be in 0.3)

---

