---
title: "ipython not workinkg"
date: 2012-09-25
forum: Programming Talk
---

### Post by RENOO on 2012-09-25
Hi everyone,

I cannot start ipython. Here is my error message :

```
ipython
ERROR! History file wasn't a valid SQLite database. It was moved to /home/openocean/.config/ipython/profile_default/history-corrupt.sqlite and a new file created.
Traceback (most recent call last):
  File "/usr/bin/ipython", line 8, in <module>
    launch_new_instance()
  File "/usr/lib/python2.7/dist-packages/IPython/frontend/terminal/ipapp.py", line 402, in launch_new_instance
    app.initialize()
  File "<string>", line 2, in initialize
  File "/usr/lib/python2.7/dist-packages/IPython/config/application.py", line 84, in catch_config_error
    return method(app, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/IPython/frontend/terminal/ipapp.py", line 312, in initialize
    self.init_shell()
  File "/usr/lib/python2.7/dist-packages/IPython/frontend/terminal/ipapp.py", line 332, in init_shell
    ipython_dir=self.ipython_dir)
  File "/usr/lib/python2.7/dist-packages/IPython/config/configurable.py", line 318, in instance
    inst = cls(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/IPython/frontend/terminal/interactiveshell.py", line 183, in __init__
    user_module=user_module, custom_exceptions=custom_exceptions
  File "/usr/lib/python2.7/dist-packages/IPython/core/interactiveshell.py", line 431, in __init__
    self.init_history()
  File "/usr/lib/python2.7/dist-packages/IPython/core/interactiveshell.py", line 1439, in init_history
    self.history_manager = HistoryManager(shell=self, config=self.config)
  File "/usr/lib/python2.7/dist-packages/IPython/core/history.py", line 402, in __init__
    **traits)
  File "/usr/lib/python2.7/dist-packages/IPython/core/history.py", line 134, in __init__
    self.init_db()
  File "/usr/lib/python2.7/dist-packages/IPython/core/history.py", line 158, in init_db
    end timestamp, num_cmds integer, remark text)""")
OperationalError: database is locked

If you suspect this is an IPython bug, please report it at:
    https://github.com/ipython/ipython/issues
or send an email to the mailing list at ipython-dev@scipy.org

You can print a more detailed traceback right now with "%tb", or use "%debug"
to interactively debug it.

Extra-detailed tracebacks for bug-reporting purposes can be enabled via:
    c.Application.verbose_crash=True

```
I am not sure about this Sqlite problem mentioned. 
How ever I can import the module IPython from a python console

 ```
python
Python 2.7.3 (default, Aug  1 2012, 05:14:39) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import IPython
>>> print IPython.__version__
0.12.1
>>> print IPython.__file__
/usr/lib/python2.7/dist-packages/IPython/__init__.pyc
```

Thank you very much for your help

---

### Post by spjackson on 2012-09-25
Was this working before or have you only just installed ipython? What is the filesystem type that your home directory is on?

---

### Post by RENOO on 2012-09-25
Thank for your interest.

I think you are on the right track.

I have several servers on which ipython is working well. I don't remember if it was working before on this one or not.
However, the /home directory is mounted automaticaly from an NFS server using autofs
with the following line in my /etc/auto.home :

```
*       192.168.1.2:/mnt/main/homes/Data/& 
```

Why this could be a problem ?

---

### Post by spjackson on 2012-09-25
I haven't actually used a sqlite database over NFS, but there are reported to be problems with this.

[URL="http://www.sqlite.org/faq.html"]http://www.sqlite.org/faq.html
[/URL]
[http://www.sqlite.org/howtocorrupt.html]("http://www.sqlite.org/howtocorrupt.html")

So I think there's a good chance that's your problem.

---

### Post by RENOO on 2012-09-26
Bad news,

But do I have to use an SQlite database in order to use ipython ?

---

### Post by RENOO on 2012-09-26
I found this post confirming this problem.
I did not understand if there is a way to set the history directory in a config file
[https://github.com/ipython/ipython/issues/882]("https://github.com/ipython/ipython/issues/882")

---

### Post by spjackson on 2012-09-26
> **RENOO said:**
> Bad news,

But do I have to use an SQlite database in order to use ipython ?

I use python but not ipython, so I don't know much about the latter. The error message you got suggests that ipython uses sqlite for its history.

> 
I found this post confirming this problem.
I did not understand if there is a way to set the history directory in a config file
[https://github.com/ipython/ipython/issues/882](https://github.com/ipython/ipython/issues/882)

Again, I don't know much about ipython, but from [the manual]("http://ipython.org/ipython-doc/stable/config/overview.html#command-line-arguments") I expect you can do something like
```

mkdir -p /tmp/username/ipython
ipython --ipython-dir=/tmp/username/ipython

```
I don't suggest you put it in /tmp, but some local Linux filesytem that you can write to.

---

### Post by RENOO on 2012-09-26
Working great Thanks

---

### Post by MadCow108 on 2012-09-26
you can also use an environment variable to relocate the folder to a fully functional mount, e.g. bash:
```
export IPYTHONDIR=/some/folder
```

---

