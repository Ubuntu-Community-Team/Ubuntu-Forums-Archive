---
title: "Extraction failed with code: 2"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by obromios on 2012-02-08
I am trying to install Ubuntu on my windows 7 PC but after about 30 minutes, I get an error message:

"Extraction failed with code: 2", with a pointer to the log file.
Please find below the relevant extract from **wubi-11.10-rev245.log.**

thank you

Chris
02-08 21:11 DEBUG  TaskList: ### Finished download
02-08 21:11 DEBUG  TaskList: ## Finished get_diskimage
02-08 21:11 DEBUG  TaskList: ## Running extract_diskimage...
02-08 21:12 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 448, in extract_diskimage
Exception: Extraction failed with code: 2
02-08 21:12 DEBUG  TaskList: # Cancelling tasklist
02-08 21:12 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 448, in extract_diskimage
Exception: Extraction failed with code: 2
02-08 21:12 DEBUG  TaskList: # Finished tasklist

---

### Post by Ms. Daisy on 2012-02-12
Full disclosure: I have never used Wubi.  But seeing that no one has answered you in 4 days I googled the error you got and found this, might be worth a try:

[https://answers.launchpad.net/wubi/+question/181794](https://answers.launchpad.net/wubi/+question/181794)

---

### Post by Rubi1200 on 2012-02-12
Hi and welcome to the forums obromios :)

If the solution suggested by Ms. Daisy doesn't help, then post as much relevant information as you can such as computer specifications etc. so we can try and help you resolve this.

Also worth trying is placing the wubi.exe and relevant Desktop ISO in the same folder before running the executable.

---

