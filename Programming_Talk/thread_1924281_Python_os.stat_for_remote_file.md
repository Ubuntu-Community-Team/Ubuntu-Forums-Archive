---
title: "Python os.stat for remote file"
date: 2012-02-12
forum: Programming Talk
---

### Post by MickSulley on 2012-02-12
Hi

I can use os.stat(SomeFile).st_atime to see when a file was updated.

Question - how can I do this when the file is on a different server?  I have tried 
os.stat(user@server:/SomeFile).st_atime
but that gives me an error 'No such file or directory'

Alternatively is there some other way to achieve this?

Thanks
Mick

---

### Post by ofnuts on 2012-02-12
> **MickSulley said:**
> Hi

I can use os.stat(SomeFile).st_atime to see when a file was updated.

Question - how can I do this when the file is on a different server?  I have tried 
os.stat(user@server:/SomeFile).st_atime
but that gives me an error 'No such file or directory'

Alternatively is there some other way to achieve this?

Thanks
MickYou can use various remote file access commands such as FTP/SFTP/RSH... unless there is a specific python module for this (usually you'll want to access the file contents anyway).

Another possibility is to have the remote filesystem mounted locally (NFS or else). Then you can use os.stat().

---

### Post by MickSulley on 2012-02-12
Sorry I haven't explained this very well.  
I have a control system that runs on either one of my two servers.  The control system updates the timestamp on a heartbeat file every 20-30 seconds and I then have another program that monitors the timestamp on the heartbeat and sends me an email if it is more that 5 minutes old.
What I want to do is to run the monitor program on both servers, so if everything is healthy each monitor should see either its own or the other servers heartbeat is < 5 mins old.  The monitor currently looks at its own heartbeat, that's fine, but I can't figure out how to see the timestamp on the heartbeat on the other server.  I'm not interested in what is in the file, just when it was last updated.
Thanks
Mick

---

### Post by MadCow108 on 2012-02-12
*os.stat* won't work for that purpose (without a network filesystem)
*os.stat* works only on mounted file systems, it just uses the *stat* system call

why not just let the clients sends heartbeats directly to some server socket?

---

### Post by MickSulley on 2012-02-12
> why not just let the clients sends heartbeats directly to some server socket?

OK, but I'm afraid the next question is how do I do that?

---

### Post by MadCow108 on 2012-02-12
so you have no infrastructure for that already available?
in that case it may be overkill (though it is quite simple to build a minimal heartbeater with pyzmq, see e.g. [https://github.com/zeromq/pyzmq/tree/master/examples/heartbeat](https://github.com/zeromq/pyzmq/tree/master/examples/heartbeat))

you could try if this works:
```
import urllib
print urllib.urlopen(file, timeout=30).info().getdate('last-modified')
```

urllib can handle local and remote files, though if you get last-modified information depends on the server sending the file.

or ssh remote-server "check-last-mod-time.sh $NOW" could also be done

---

### Post by MickSulley on 2012-02-12
Thanks for the reply, I tried that, it didn't seem to like the timeout, so I took that out.  My code is now
```
print urllib.urlopen('control@solar:/home/control/solar/ctrl_hrt_bt').info().getdate('last-modified')
```
but that generates an error
[HTML]The debugged program raised the exception unhandled IOError
"[Errno url error] unknown url type: 'control@solar'"
File: /usr/lib/python2.7/urllib.py, Line: 214
[/HTML]
If I use a local file name it works fine.
Any idea what I have done wrong?

---

