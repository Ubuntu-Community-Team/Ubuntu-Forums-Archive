---
title: "Writing a Linux Daemon"
date: 2007-09-03
forum: Programming Talk
---

### Post by what4893 on 2007-09-03
Hi,

I am writing a web application and this web app is going to queue up jobs for a PHP script. I need this PHP script to run whenever something is queued up for it. I asked a friend and he said a daemon would be the best way to go about this. I have done a small amount of C/C++ coding and when I searched around for info regarding writing your own daemons I found very little. I wanted to see if anyone here had any info in the form of sites or book titles that might help me learn more about writing my own Ubuntu server daemon. Any help would be greatly appreciated.

what4893

---

### Post by fct on 2007-09-03
A daemon is just a program that runs in the background and is not interactive. Not much to learn, but there are some tutorials around.

Look at the links at the bottom:

[http://en.wikipedia.org/wiki/Daemon_(computer_software](http://en.wikipedia.org/wiki/Daemon_(computer_software))

---

### Post by what4893 on 2007-09-03
fct,

Thanks so much. Normally I check out Wikipedia but didn't think they'd have any info directly related to what I was looking for. The article pertaining the the bash http daemon was exactly the basis of what i was looking for. Thanks for your prompt reply.

what4893

---

### Post by zakili on 2007-09-06
.

---

### Post by carstenson on 2007-09-13
I hack a little bit with *nix C. I highly recommend a book, "Advanced Programming in the UNIX Environment" by W. Richard Stevens. It obviously is old, but still quite relevant to Linux. Costs a little bit.

Here is some code of mine (don't judge):

```
daemon_init()
{
        pid_t pid;
        char outfile[]="/source/rfs-.out";
        char logfile[]="/source/rfs-.log";
        FILE *fdout;
        if ( (pid = fork()) < 0) {
                perror("fork");
                exit(errno);
                }
        else if (pid != 0)
                exit(0);
        setsid();
        umask(0);
        outfile[11] = *svrid;
        logfile[11] = *svrid;
        freopen("/dev/null", "a", stdin);
        fdout = freopen(outfile, "w", stdout);
        fdlog = freopen(logfile, "a", stderr);
        setvbuf(fdout, (char *)NULL, _IONBF, (size_t)BUFSIZ);
        setvbuf(fdlog, (char *)NULL, _IOLBF, (size_t)BUFSIZ);
}

```

---

### Post by dwhitney67 on 2007-09-13
A daemon is nothing more than a "server" application that does something in the background.  It can perform any task you design it to do, and hopefully it will run indefinitely unless told to stop or restart.

There are various ways to communicate with a daemon/server, but generally it is via a TCP port.  Applications that comes to mind are the HTTPD, SSHD, and SNMPD (or Agent, as some like to call it).

If you are really adventurous, you can implement a server that uses ORB (object request brokering).  Another implementation idea is to design a multi-threaded application where threads are started as needed and then terminated when no longer required.  If you do not expect much data traffic or interaction with the server, then a simpler design should be implemented.

---

### Post by slavik on 2007-09-13
php should have a daemonization library. :)

question, your php script is going to be running on the system? (not a web page/app)

---

### Post by gnusci on 2007-09-13
Here you have a simple bash daemon:

[PHP]
# mydaemon.sh
# This is a simple daemon shell script.
#
# Traps:
# signal HUP (1) read config file again
# signal QUIT (3) delete temp files
# signal TERM (15) delete temp files

PSLOG=/home/$USER/psaux.log

# set traps
trap 'source $conf' 1
trap 'rm -f $tempfile; exit' 0
trap 'rm -f $tempfile; exit' 3
trap 'rm -f $tempfile; exit' 15

# loop forever
while :
do
    echo "hello"
    ps aux > $PSLOG
    sleep 10s
done
[/PHP]

Save in a **daemon.sh** file then make it executable:

**> chmod u+x mydaemon.sh**

and then run it:

**>./mydaemon.sh**

if you want a background daemon just run it with the condition **&**:

**>./mydaemon.sh &**

As you will see this small daemon will save a copy of the output of **ps aux** every 10s in you user directory.

when you get bored to receive the **ps aux** log in your directory. Just look for this job with:

**> ps aux | grep mydaemon**

and then you can send a kill -9 to its PID.

---

### Post by what4893 on 2007-09-13
Wow, thanks for all the feedback.

In response to one question that was posted: I know it seems contradictory to execute a PHP script locally when I'm calling the daemon from a PHP app. The reason I am doing this as opposed to just running the script online is the PHP script will be making dynamic PDF documents that have been queued up sometimes a few hundred at a time. Now personally I don't want to go in to a computer every once in a while and refresh the web page to force the script to start running, plus then I have to worry about timeouts. That's my reasoning behind this.

Once again thank you for the feedback so far and I will look into each response and see if I can piece together some more of the daemon puzzle.

what4893

---

### Post by what4893 on 2007-09-13
carstenson,

I checked out the book on Amazon and it looks perfect with several chapters on Unix processes and system calls. Thanks for recommending this book. I think I'll grab a copy today.

what4893

---

### Post by zazuge on 2008-01-28
A daemon is just program that is the direct child of init process and it have his ouput and input not directed to a stdin (he can read from a file or a fifo ) & stdout (perhaps to a log file or the null device)

to have a programe to be the child of init process he must be orphaned so the init process will adopt him (Oh, poor little programe :3 )

the daemon have to handle signals correctly so he can be stoped & started cleanly

those are the basic rules of a daemon programme, apart from these basic rules other things are just black magic. :-p

---

### Post by Acglaphotis on 2008-01-28
Dude, this thread is from like september 2007.

---

### Post by zazuge on 2008-01-29
> **Acglaphotis said:**
> Dude, this thread is from like september 2007.
Oh yeah I know but then you have to mark it as solved
If you don't want people to bother answer your unaswered question -_-'

---

