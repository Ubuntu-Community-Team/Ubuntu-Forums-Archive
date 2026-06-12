---
title: "Apache2, CGI and client disconnection : program terminates unexpectedly"
date: 2007-07-09
forum: Programming Talk
---

### Post by aks44 on 2007-07-09
I'm currently writing a C++ CGI that runs under Apache2.

My problem at the moment is that when the client disconnects (eg. by clicking the "Stop" button of his browser), the CGI terminates without any apparent way to continue it's job.

The termination only happens when I flush std::cout / stdout, if I don't flush then the CGI continues running.
The behaviour is the same whether I use
```
std::cout << "whatever" << std::endl;
```or```
fwrite("whatever", 1, 8, stdout); fflush(stdout);
```

I've got no error neither in my CGI's own debug log (ie. no C++ exception has been thrown), nor in Apache log.

According to several sources on the net concerning FastCGI (which I don't use, but anyway it was worth the try), signals seem to be the cause of my problem. So I tried ignoring all the signals that seemed even remotely relevant (SIGHUP, SIGINT, SIGQUIT, SIGUSR1, SIGUSR2, SIGPIPE, SIGTERM, SIGTSTP) but to no avail. :(

Now I'm stuck, I've got no idea where to look for as I'm kinda new to Linux programming.


Anyone got an idea? Am I missing something concerning this signals thing, or is it something totally different?


Thanks for your attention.


EDIT: I know it's possible... PHP allows this thanks to ignore_user_abort(true)... maybe I'm gonna dig in PHP source code if I can't find any other way :(
EDIT: Oh my, PHP source is even worse that what I expected... maybe another day...

---

### Post by aks44 on 2007-07-10
After some digging, I finally found the core of the problem...

Whenever I flush stdout, Apache tries to send the data to the disconnected client. As the pipe between Apache and the client is broken, Apache gets a SIGPIPE, and in turn sends my CGI a SIGTERM.

If I ignore SIGTERM, Apache waits 3 seconds then sends a SIGKILL. :(

Looks like I'm doomed, I'd better avoid writing to stdout altogether during sensitive operations (a flush could happen without me knowing, if I manage to fill up the buffer).

And also force a flush at adequate moments (before a sensitive operation) to manually check for a disconnection :
=> flush
=> SIGTERM handler which sets a global variable
=> throw an exception if that variable is set
=> hopefully the stack will unwind all the way up to main() before SIGKILL is sent and I'll exit properly

Any suggestions to make the process a bit more smooth?

---

