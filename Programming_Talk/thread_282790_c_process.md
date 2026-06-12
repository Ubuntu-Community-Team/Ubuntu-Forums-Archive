---
title: "c process"
date: 2006-10-23
forum: Programming Talk
---

### Post by vijraj on 2006-10-23
I have a problem to solve in C language but I don't know how.Here it is.

A main process creates 4 new processes A,B,C,D.
when the original process creates the new processes, it passes the same pipe that they can use to send data to the original process, which will serve as a logginng process, displaying each line it receives along withe time stamp.a pipeline is to exist between A and B, another between B and C and another between B and D . There will be four pipes in all.
Process A generates 10 records consisting of the letter C or D(picked randomly
for each record),along with the record number(2 bytes ascii).
and sends it to process b.Process A also sends a log message like 'A sent process B 'do1' to the logging process.
Process B reads from the pipe connecting it to A.For each record it reads , it will send it to the process indicated by the first character, along with sending an appropriate log message to the logging process.It then waits for one second.
Process c reads its pipe and for each message received sends logging process ab appropriate message.
Process D is like c except itwaits 5 seconds every time after it receives a message.
This should be done using lowlevel piping like using the
int pfds[2];
pipe (pfds);
etc.
rand() for sleeping and also for generating C or D.
can anyone post a solution for this.I appreciate any kind of help.
Thank you.

---

