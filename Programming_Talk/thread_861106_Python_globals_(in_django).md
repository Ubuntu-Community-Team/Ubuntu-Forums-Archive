---
title: "Python globals (in django)"
date: 2008-07-16
forum: Programming Talk
---

### Post by [h2o] on 2008-07-16
I have a website written with django.
The webapplication need to start jobs (as in run shell commands) on the webserver and take care of the output.
Since the jobs can take a long time (minutes to hours depending on data) it is not feasible to wait for the output before transmitting back to the server.

So what I thought was to register all new jobs in a "ExecutionManager" object which then runs the jobs, and can also be queried on the status of a job.
Writing that piece of code is no problem, but getting it to communicate with django is.

I tried putting the file in my django app dierctory "mysite/myapp/executionmanager.py" and then I do:
**mysite/myapp/__init__.py**
```
from executionmanager import ExecutionManager
executer = ExecutionManager()
```
and
**mysite/myapp/views.py**
```

from myapp import executer

# Lots of views here 
...

def my_view(request):
 job = get_job_from_request(request)
 executer.add_job(job)
 ...

```

I am sure I have used globals in that way before, but it just doesn't seem to work right now. Am I missing something fundamental about how python handles globals (then I reeeeally want to know :)) or is it django (or the way the web works) that makes it hard for me?

---

### Post by pmasiar on 2008-07-16
I am not sure how globals are related to this.

What I would do is to use Django as gui frontend to create/edit items in table queue. Then, completely separately from django, create commandline program to (1) check database table queue, (2) perform requested calculations (if any) one by one, (3) save the files, and (4) mark item as completed (and (5) each application advanced enough has to send email, of course :-) ). Then set this program as cron job starting every x minutes. Then user can later come back to your Django app, check queued tasks, see which are completed, and get the files.

How this is related to globals at all? Django will allow to request the tasks and show results when done, but calculation will run from cron job, separately from Django. 

I cannot even imagine doing it differently (given your long-running jobs), but you likely **are** doing it differently. How exactly? And how it is related to OOP mumbo-jumbo you use?

---

### Post by skeeterbug on 2008-07-16
I know .NET has this available through the HttpApplication state object.

> 
 Remarks

An ASP.NET application is the sum of all files, pages, handlers, modules, and code within the scope of a virtual directory and its subdirectories on a single Web server.

A single instance of an HttpApplicationState class is created the first time a client requests any URL resource from within a particular ASP.NET application virtual directory. A separate single instance is created for each ASP.NET application on a Web server. A reference to each instance is then exposed via the intrinsic Application object.

Application state is not shared across either a Web farm (in which an application is hosted across multiple servers) or a Web garden (in which an application is hosted across multiple processes on the same computer).


Does Django have this as well? I don't think it does. A global object does not scale if you run multiple web servers that are load balanced (unless you direct a client to the same machine every request). Like pmasiar suggested, use a queue (database table) or some other type of persisted messaging system so the entire process isn't so coupled.

---

### Post by [h2o] on 2008-07-16
> **pmasiar said:**
> I am not sure how globals are related to this.
Simple: If I could have a global instance of my ExecutionManager class then there would not be a problem. This was however not possible since mod_python runs in separate processes. Fortunately I managed to code around the need of having interprocess communication so the problem is solved.


> What I would do is to use Django as gui frontend to create/edit items in table queue. Then, completely separately from django, create commandline program to (1) check database table queue, (2) perform requested calculations (if any) one by one, (3) save the files, and (4) mark item as completed (and (5) each application advanced enough has to send email, of course :-) ). Then set this program as cron job starting every x minutes. Then user can later come back to your Django app, check queued tasks, see which are completed, and get the files.
Nah, the calculations are actually a set of calculation of which some are really quick. Having to wait a minute before execution starts is not really an option.

> I cannot even imagine doing it differently (given your long-running jobs), but you likely **are** doing it differently. How exactly? And how it is related to OOP mumbo-jumbo you use?
It works like this (somewhat simplified): Web GUI constructs a runobject containing all the neccessary data needed for the run.
The runobject is then "run" in a separate thread allowing the Django view to return immediately.
Since the "run" constructs a lot of output in form of directories and files specific to the job I can then just parse those directories and get the status needed to construct nice user feedback :)


Still, if I wanted to use globals in Python (assuming program runs in one and only one interpreter) is the correct way to put the globals in a module and then do "import mymodulewithglobalstuffinit" to access them?
I remember doing so in previous programs with database connections, and that seemed to work fine. Would be good to know if it is actually a correct (or atleast safe) way to do it.

---

### Post by [h2o] on 2008-07-16
> **skeeterbug said:**
> Does Django have this as well? I don't think it does. A global object does not scale if you run multiple web servers that are load balanced (unless you direct a client to the same machine every request). Like pmasiar suggested, use a queue (database table) or some other type of persisted messaging system so the entire process isn't so coupled.

True, I have not considered scaling at all since the application will never ever reach that scale. :)

---

### Post by skeeterbug on 2008-07-16
I am not sure there would be a safe way to do it though. If you deployed CGI like, you would get a completely different process.

What about using memcached as a queue or global temp store? I know Django works out of the box with that. The only problem with that is you would lose the data if the cache was restarted.

---

### Post by [h2o] on 2008-07-16
> **skeeterbug said:**
> I am not sure there would be a safe way to do it though. If you deployed CGI like, you would get a completely different process.
Yes, as I said. But I was interested to hear what the standard way of doing it is in a normal (one program, one interpreter) case.

---

### Post by pmasiar on 2008-07-16
> **'[h2o] said:**
> Nah, the calculations are actually a set of calculation of which some are really quick. Having to wait a minute before execution starts is not really an option.

Does not make sense to me. You cannot wait a minute to start, but you are willing to wait minutes/hours to finish anyway. What's the rush?

And DB solution scales, unlike your hack: it is trivial to run calculation on separate server, or multiple servers.

> The runobject is then "run" in a separate thread allowing the Django view to return immediately.

Simple attack to bring your server to knees: start couple of those long processes - you have nothing to throttle them.

> Still, if I wanted to use globals in Python

... if I wanted to use wrong tool for wrong reason... :-)

> put the globals in a module and then do "import mymodulewithglobalstuffinit" to access them?...
I remember doing so in previous programs with database connections, and that seemed to work fine. 

Each process will get own copy of the globals. Seems like you do not grasp persistence in multiprocess programming at all.

Whole point is to have database as single persistent data serving multiple processes.

Of course you can create another persistent process with shared data, but that would be very different from global (for a process) data. Why bother if database server fits the job, works, and probably would be even faster than your custom solution?

Of course do whatever you want: you have enough rope to hang yourself. Good luck!

---

### Post by [h2o] on 2008-07-17
> **pmasiar said:**
> Does not make sense to me. You cannot wait a minute to start, but you are willing to wait minutes/hours to finish anyway. What's the rush?
As I said, it is a set of calculations and you might want to take a look at the ones that have finished before all are done. Also, I think people would get really annoyed. I understand why it might sound silly, but I think I have more knowledge about this particular program and the people who will use it.

> And DB solution scales, unlike your hack: it is trivial to run calculation on separate server, or multiple servers.Yes, but as I said, it is not needed as the potential number of users is really low.

> Simple attack to bring your server to knees: start couple of those long processes - you have nothing to throttle them.It is an internal application, so if someone crashed it on purpose then I think their manager would like to have a word with them...


> ... if I wanted to use wrong tool for wrong reason... :-)Let's not get into the "Globals is wrong"-discussion. I am fully aware that one should try not to use it if possible, but there are times when it is the most convenient way to solve a problem.

> Each process will get own copy of the globals. Seems like you do not grasp persistence in multiprocess programming at all. Yes, that is what I have said in at least two posts now, thank you very much. I think it is quite obvious if you actually read my previous posts.
My question was explicitly about how I would do it in a normal (one interpreter, or process if you wish) environment.

> Whole point is to have database as single persistent data serving multiple processes.
Yes, if the data you want to share is something you can put inside a database.

> Of course you can create another persistent process with shared data, but that would be very different from global (for a process) data. Why bother if database server fits the job, works, and probably would be even faster than your custom solution?
If a global variable solves the job, why would I want to use something lika a frickin' database?
I think ```
print myglobalmodule.globalvalue
```'
is quite a lot easier (and hopefully faster in all situations) than ```
 connection = mydbmodule.connect(DB_CONNSTRING)
cursor = connection.cursor()
value = cursor.execute("SELECT globalvalue FROM globaltable").fetchone()[0]
print value

```
And then there is the previous fact that a lot of stuff is just not convenient to put in a database.

---

