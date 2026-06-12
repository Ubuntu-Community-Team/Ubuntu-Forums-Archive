---
title: "How to kill a python"
date: 2009-10-23
forum: Programming Talk
---

### Post by Sandsound on 2009-10-23
I would like to kill a python script that is run from within another python script, while keeping the original script running.

example:

programX has a virtual terminal where I launch programY.
If I just do a "killall python" - both windows will be killed.
If I do a "Killall programY" - no process is found.

If I do a "ps -e" - I don't get programX and programY as I expected, I just get two processes called python.

What am I doing wrong, and is this at all possible ?

btw. the program can be found here : [reload-0.0.2.tar.gz]("http://www.sandgreen.dk/xt2/files/reload-0.0.2.tar.gz")
If you look at this code it might be painfully obvious that I don't know much about Python, but that doesn't keep me from trying :-)

EDIT: look at #13 for the answer

---

### Post by sisco311 on 2009-10-23
```
ps -ef
```
```
kill -9 <pid>
```

---

### Post by diesch on 2009-10-23
```
ps -ax -opid,cmd
```

---

### Post by Sandsound on 2009-10-23
> **sisco311 said:**
> ```
ps -ef
```

If I do :
```
ps -ef | grep python programX
```
I get :
```
grep: programX: No such file or directory
```

I still don't know how to get the pid  of a process called
"python ./programX"

EDIT : doh... I should of course be using :
```
ps -ef | grep "python ./programX"
```
(added quotation-marks)

But this also gives me a :
```
grep --color=auto python ./reload.py
```
So now I at least only have two possible options :-)

---

### Post by sisco311 on 2009-10-23
```
ps -ef | grep python\ programX  #or
ps -ef | grep "python programX"

```
or
```
ps -ef | grep python | grep programX
```

---

### Post by diesch on 2009-10-23
To avoid the grep itself showing up use

```
ps -ef | grep "[p]ython ./programX"
```

---

### Post by sisco311 on 2009-10-23
how abaout:
```
pidof -x scriptname
```

---

### Post by Can+~ on 2009-10-23
You must grab it by the head, pressing on the sides of the mouth, so it keeps its mouth open, and keep your hands far from the fang... oh.

Sorry, totally misunderstood the thread.

---

### Post by dwhitney67 on 2009-10-23
```

fuser -k <script name>

```

---

### Post by Sandsound on 2009-10-23
> **diesch said:**
> To avoid the grep itself showing up use

```
ps -ef | grep "[p]ython ./programX"
```

Thanks, this looks promising.

Can't understand why this doesn't work thou :
```
self.command_entry.set_text('programX')
process_name = ('[p]ython '+'"'+ self.command_entry.get_text() +'"')
process_id = os.system('ps -ef | grep '+'"'+ process_name +'"')
print (process_id)

```
All it do is print a "0" ?


If I run ```
ps -ef | grep "[p]ython programX"
```in a terminal, I get the whole line with the PID.


it's almost 4 o'clock in the morning here in Denmark.. maybe some sleep will help :-)

---

### Post by dwhitney67 on 2009-10-23
> **Sandsound said:**
> ...


it's almost 4 o'clock in the morning here in Denmark.. maybe some sleep will help :-)

No, just look at my post... well, ok... goto sleep.  But use fuser.

---

### Post by Sandsound on 2009-10-24
Thank you all for helping.

I still haven't been able to figure out why ps return the correct line in a terminal and a "0" in the script ?


> **dwhitney67 said:**
> No, just look at my post... well, ok... goto sleep.  But use fuser.

Looks nice and simple, but it doesn't seam to be able to do what I want.
fuser -k programX = No such file or directory
fuser -k /full_path_to_script/programX = Nothing happens
fuser -k "python /full_path_to_script/programX" = Nothing happens

Am I doing it wrong ?

---

### Post by Sandsound on 2009-10-24
Got it :-)

```
def kill_callback(self, kill_button):
	entry_box = self.command_entry.get_text()
	for line in os.popen("ps -ef"):
		if entry_box in line:
			fields  = line.split()
			pid     = fields[1]
			process = fields[8]
			os.kill(int(pid), signal.SIGHUP)
```

Thanks to everyone for guiding me through this

---

