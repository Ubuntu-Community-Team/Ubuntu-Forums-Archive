---
title: "os.system(command) inheriting open socket"
date: 2010-05-27
forum: Programming Talk
---

### Post by The Cog on 2010-05-27
How can I stop processes launched with os.system("someCommand") from inheriting open sockets from the parent process?

I have a long-running daemon (listen.py) that sits listening on a socket and collecting data. Occasionally, it writes to a file and then launches a second process ("nohup nice digest.py &")) to deal with that file-load of data. This second process can be quite a long one. 

I have noticed that if the listening process dies for any reason then it cannot restart (address in use) until the secondary process has exited. In my case, this means I may be unable to restart the listening process for several hours. Using **lsof -i** I can see that when the second process is launched, it seems to be given a reference to the open socket - the socket is opened by both processes.

I don't want to have to wait for hours to restart the listening process and neither do I want to have to close the socket before launching the digest process.

So the question is, how can I launch this second process without it holding a second handle to the listening socket?

---

### Post by The Cog on 2010-05-27
Answering my own question. 
Should have googled for longer before asking.
This does it:
> subprocess.Popen("nohup nice ./digest.py >> digest.log &".split(), close_fds=True)

---

