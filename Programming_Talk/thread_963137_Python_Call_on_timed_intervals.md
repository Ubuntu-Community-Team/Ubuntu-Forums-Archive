---
title: "Python: Call on timed intervals"
date: 2008-10-29
forum: Programming Talk
---

### Post by abeisgreat on 2008-10-29
I need my script to do something every minute, and as it is now i have it set up so

```
		while 1:
		    global nTime
		    global update
	            oTime = int(time.time())
	            #print oTime
	            #print nTime
	            if oTime > nTime:
		   	print'TIME'
			self.find_updates('w')
			nTime = time.time() + int(update*60)
		    while gtk.events_pending():
                        gtk.main_iteration()
```

but the issue is it takes %50 of my 1.6 atom processor, is there a better way of doing this?

I THINK this is whats causing the processor jumps but im not sure

---

### Post by WW on 2008-10-30
It looks like you are using PyGTK.  You could use a "timeout":
[http://www.pygtk.org/pygtk2tutorial/ch-TimeoutsIOAndIdleFunctions.html](http://www.pygtk.org/pygtk2tutorial/ch-TimeoutsIOAndIdleFunctions.html)
[http://mail.python.org/pipermail/python-list/2003-September/226306.html](http://mail.python.org/pipermail/python-list/2003-September/226306.html)

---

### Post by abeisgreat on 2008-10-30
> **WW said:**
> It looks like you are using PyGTK.  You could use a "timeout":
[http://www.pygtk.org/pygtk2tutorial/ch-TimeoutsIOAndIdleFunctions.html](http://www.pygtk.org/pygtk2tutorial/ch-TimeoutsIOAndIdleFunctions.html)
[http://mail.python.org/pipermail/python-list/2003-September/226306.html](http://mail.python.org/pipermail/python-list/2003-September/226306.html)

That worked, thanks

---

### Post by Guille Damke on 2008-10-30
Hi,

Also you can modify your script TO BE EXECUTED once a minute by using crontab (cron), which is a system daemon for running scripts periodically where basically you choose the time interval (once a minute, hour, week, etc, or at a fixed time each day, week, month, etc).

[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

Good luck,
Guillermo

---

### Post by abeisgreat on 2008-10-30
thanks although I need the script to be running and do it on intervals

thanks though

---

