---
title: "Python script with Thread + cron = Fail?"
date: 2009-04-13
forum: Programming Talk
---

### Post by KlinerDraken on 2009-04-13
I wrote this python script that starts LastFM in a new thread and slowly raises the speaker volume from ~50 to 100. It works great from the terminal and also in Gnome Schedule by pressing the 'Run Task' button. However when I schedule the task to run, the script fails to start the new thread to run LastFM in, but the rest of the script seems to run fine.

Any ideas what may be the issue?

Thanks for any suggestions.


```
#!/user/bin/env python
import commands
import time
import threading
import sys
import datetime
#---Create a thread to start LastFM---
class StartLastFM ( threading.Thread ):
	def run ( self ):
		cmd = '/usr/bin/lastfm'
		output = commands.getoutput(cmd)
#---Check to see if it is the weekend---
#---Remove this if you want it to run on the weekends--
Today = datetime.date.today()
if Today.weekday() > 4:
	sys.exit()
#---Turn volume all the way down then back up to ~50%---
cmd = 'amixer -q set Master 30- unmute'
output = commands.getoutput(cmd)
time.sleep(.25)
cmd = 'amixer -q set Master 15+ unmute'
output = commands.getoutput(cmd)
#---Start Last.FM---
StartLastFM().start()
#---Slowly raise the volume to 100% over 15 minutes---
for vloop in range(0, 16, 1):
	time.sleep(60)
	cmd = 'amixer -q set Master 1+ unmute'
	output = commands.getoutput(cmd)
#---End Script---
sys.exit()
```

---

### Post by KlinerDraken on 2009-04-13
I did some more looking into what my script is doing by adding some output to a file.

```
#!/user/bin/env python
import commands
import time
import threading
import sys
import datetime
##---
filename = '/home/ben/Documents/Python/debug.txt'
file = open(filename, 'w')
file.write('Script Started\n')
#---Create a thread to start LastFM---
class StartLastFM ( threading.Thread ):
	def run ( self ):
		##--
		file.write('Tread started\n')
		cmd = '/usr/bin/lastfm'
		##--
		file.write('Tread Mid\n')
		commands.getoutput(cmd)
		##--
		file.write('Tread end\n')
#---Check to see if it is the weekend---
#---Remove this if you want it to run on the weekends--
Today = datetime.date.today()
if Today.weekday() > 4:
	sys.exit()
#---Turn volume all the way down then back up to ~50%---
##--
file.write('Adjusting Volume\n')
cmd = 'amixer -q set Master 30- unmute'
commands.getoutput(cmd)
time.sleep(.25)
cmd = 'amixer -q set Master 15+ unmute'
commands.getoutput(cmd)
#---Start Last.FM---
StartLastFM().start()
#---Slowly raise the volume to 100% over 15 minutes---
for vloop in range(0, 16, 1):
	##--
	file.write('Looping\n')
	time.sleep(1)
	cmd = 'amixer -q set Master 1+ unmute'
	commands.getoutput(cmd)
#---End Script---
##--
file.write('Script Stopping\n')
sys.exit()

```

And it seems odd what it is doing, here is what gets output to the file when it successfully runs (from the terminal)

```
Script Started
Adjusting Volume
Tread started
Tread Mid
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Script Stopping
```

now the output from running from cron. it seems that the thread is ending?

```
Script Started
Adjusting Volume
Tread started
Tread Mid
Looping
[COLOR="Red"]Tread end[/COLOR]
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Looping
Script Stopping
```

---

### Post by slavik on 2009-04-13
what happens when there is a problem running the command?

EDIT: I am referring to this:
```

		cmd = '/usr/bin/lastfm'
		commands.getoutput(cmd)

```

---

### Post by KlinerDraken on 2009-04-13
> **slavik said:**
> what happens when there is a problem running the command?

EDIT: I am referring to this:
```

		cmd = '/usr/bin/lastfm'
		commands.getoutput(cmd)

```


I guess if that commands fails then lastfm would not start and the thread would end. Just as it seems to be doing. Why would that command have problems running? or a better question might be, how can I tell if that command is succeeding or failing and if it's failing see why?

ps. this is my first python script.

---

### Post by slavik on 2009-04-13
exceptions thrown? errors returned?

check your mail, cron tends to e-mail things that otherwise get discarded (such as stderr).

---

### Post by Reiger on 2009-04-13
Well I imagine you commands.getoutput(cmd) would return you a value which you could at least try and log to see if that is indeed the problem.

Some random thoughts:

Do you have already a lastfm instance running? Maybe it will abort launching the app if it detects it is already running?

Does the user the cron job runs under have suitable permissions to run lastfm?

---

### Post by KlinerDraken on 2009-04-13
> **slavik said:**
> exceptions thrown? errors returned?

check your mail, cron tends to e-mail things that otherwise get discarded (such as stderr).

I don't get any error messages pop up, are there an logs I can check?
I haven't received any emails, but how does it know where to send them to, it may not be set.

thanks for you help

---

### Post by KlinerDraken on 2009-04-13
> **Reiger said:**
> Well I imagine you commands.getoutput(cmd) would return you a value which you could at least try and log to see if that is indeed the problem.

Some random thoughts:

Do you have already a lastfm instance running? Maybe it will abort launching the app if it detects it is already running?

Does the user the cron job runs under have suitable permissions to run lastfm?

i'll see if i can get a return from that command, i guess i do that like this?
output = commands.getoutput(cmd)
file.write(output)


LastFM is not running at the time the script is ran. And if I run /usr/bin/lastfm from cron LastFM starts correctly.

---

### Post by KlinerDraken on 2009-04-13
here is the output from that command... thanks for the tip :p

last.fm: cannot connect to X server

any idea why it couldn't connect to X?

---

### Post by Greyed on 2009-04-14
Welcome to the deep, dark magics that is environmental variables.

Cron is getting a subset of your environment.  The variables needed to connect to the X server are not in that environment.  What needs to be there is beyond me.  However I hope that'll point you to the right places to look.  :)

Actually, after a split second and a quick edit...  first step, make sure DISPLAY is defined inside your cron environment.  After that it gets into deep mojo I never quite understood.  ;)

---

### Post by KlinerDraken on 2009-04-14
> **Greyed said:**
> Welcome to the deep, dark magics that is environmental variables.

Cron is getting a subset of your environment.  The variables needed to connect to the X server are not in that environment.  What needs to be there is beyond me.  However I hope that'll point you to the right places to look.  :)

Actually, after a split second and a quick edit...  first step, make sure DISPLAY is defined inside your cron environment.  After that it gets into deep mojo I never quite understood.  ;)

Yes, I had to run my script from cron like this 
```
export DISPLAY=:0 && python /path/to/script.py
```
instead of the way I had it 
```
python /path/to/script.py
```

Thanks everyone for your help!  ;)

---

