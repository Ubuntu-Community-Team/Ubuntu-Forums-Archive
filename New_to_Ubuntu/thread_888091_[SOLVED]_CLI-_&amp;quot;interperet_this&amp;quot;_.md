---
title: "[SOLVED] CLI- &amp;quot;interperet this&amp;quot; challenge"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-12
hi essentially I'm trying to run this application.  It has worked before.  the only thing new is this fail-report.  



adamogardner@CRONUS:~/Apps/framework-3.1$ ./msfconsole
./lib/rex/logging/sinks/flatfile.rb:20:in `initialize': Permission denied - /home/adamogardner/.msf3/logs/framework.log (Errno::EACCES)
	from ./lib/rex/logging/sinks/flatfile.rb:20:in `new'
	from ./lib/rex/logging/sinks/flatfile.rb:20:in `initialize'
	from ./lib/msf/base/logging.rb:20:in `new'
	from ./lib/msf/base/logging.rb:20:in `init'
	from ./lib/msf/base/simple/framework.rb:95:in `simplify'
	from ./lib/msf/base/simple/framework.rb:71:in `create'
	from ./lib/msf/ui/console/driver.rb:67:in `initialize'
	from ./msfconsole:77:in `new'
	from ./msfconsole:77
adamogardner@CRONUS:~/Apps/framework-3.1$

---

### Post by nicedude on 2008-08-12
./lib/rex/logging/sinks/flatfile.rb:20:in `initialize': Permission denied - /home/adamogardner/.msf3/logs/framework.log (Errno::EACCES -> looks like it doesn't have permissions that it needs here.

so try adding sudo to the command to give it full permission 

sudo ./msfconsole

OR 

change the permissions on the log file it denied you to allow the user account you use to have write permissions

/home/adamogardner/.msf3/logs/framework.log  <---- framework.log would be the file I believe in this case

---

### Post by Joeb454 on 2008-08-12
That looks like it might work.

Naturally if you have no idea what it does, then just leave it :)

---

### Post by adamogardner on 2008-08-12
boy do I feel like an idiot.  Why doesn't it just say, "use sudo, otherwise you can't have permission"   ?  of course all they other times I remembered to do that.

---

### Post by nicedude on 2008-08-12
Glad that did the trick

---

### Post by Joeb454 on 2008-08-12
Well hey, I do it all the time ;)

---

