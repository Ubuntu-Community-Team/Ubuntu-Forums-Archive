---
title: "TCL/EXPECT script &amp; telnet"
date: 2009-02-04
forum: Programming Talk
---

### Post by qmqmqm on 2009-02-04
Hi

I have the following TCL/EXPECT script:

```
spawn /usr/bin/bash

#
# telnet into the remote machine
#
spawn telnet $myServer
expect "login:" { send "user\r" }
expect "Password:" { send "user\r" }

#
# log into oracle
#
expect "#" { send "su - oracle\r" }

expect "$" { send "cd /oracle_db\r" }

#
# look for pattern
#
set myCount [exec grep -c "pattern" status.txt]
```

I have another tcl script that invokes this script. Everything runs fine, except when it comes to the last line, I got an error "grep: can't open status.txt".

Through debugging I found that this is because TCL is looking for status.txt in the local directory, instead of the remote directory that I just logged into.

Does anyone know how to point grep to the remote machine's "oracle_db" directory?

Thanks in advance!

Tom

---

### Post by qmqmqm on 2009-02-04
Or to put the question another way,

I have a TCL script on one machine. Within this script, is there a way to "grep" a file on a remote machine?

Within the TCL script, I telneted into the remote machine, then used
```
set myCount [exec grep -c "pattern" status.txt]
```
, but it keeps giving me the following error:

" couldn't open "status.txt": no such file or directory "

because the script is looking for this file in the local directory instead of the remote directory.

Is there a way to solve this problem?

Thanks,

Tom

---

### Post by qmqmqm on 2009-02-07
After some research, I don't think telnet allows data to be passed between 2 computers. Therefore I don't think there is a way for the calling computer to know the returned message of a command on the remote machine. Unless there is a way to parse what is displayed in the terminal of the telnet session.

---

### Post by claird on 2009-02-07
> **qmqmqm said:**
> After some research, I don't think telnet allows data to be passed between 2 computers. Therefore I don't think there is a way for the calling computer to know the returned message of a command on the remote machine. Unless there is a way to parse what is displayed in the terminal of the telnet session.

Whoa!

This thread opens several questions.  The brief answer to all of them is, "Expect can do that".

I'm unfamiliar with the culture of Ubuntu Forums.  I'll outline the highlights that seem to apply in your case, and you let me know if you need more detail, or you feel one of your questions remains unaddressed:

You'll want to know about <URL: [http://wiki.tcl.tk/2958](http://wiki.tcl.tk/2958) >.

At one level, you need to replace "exec grep ..." with "send grep ..."  Do you see why?  [Exec] launches a process on the local host; [send] transmits a command to, in this case, the remote process.

I want to emphasize that telnet absolutely "allows data to be passed ..."  ftp-inband <URL: [http://expect.nist.gov/example/ftp-inband](http://expect.nist.gov/example/ftp-inband) >, for example, might already be on your host, and it certainly has a long history of passing data through a telnet connection.  You might like the commentary on ftp-inband which appears in <URL: [http://www.linux.com/feature/53606](http://www.linux.com/feature/53606) >.

---

### Post by stevescripts on 2009-02-09
As I asked claird to respond to this thread, I feel that perhaps a brief introduction is warranted.

Cameron Laird is a well-respected author, and long time friend, mentor, and ... occasional co-conspirator ... ;)

Cameron is the first person I would direct questions regarding Expect toward.

Hope the OP finds this helpful.

Steve

---

### Post by qmqmqm on 2009-02-11
Hi Cameron and Steve

Thanks so much for your information!

The links are very helpful. I am experimenting with ftp-inband of Expect.

Have a great day :)

Tom

---

