---
title: "Reading from constantly updating file - efficient?"
date: 2008-06-26
forum: Programming Talk
---

### Post by escapee on 2008-06-26
I have a client program I'm trying to write that is meant to read a constantly updating log file (could access system.log if desired).  It is meant to behave somewhat similarly to Mac's Console app if you've happened to use it before.  I want it to update fairly close to real time, but minor delays are not terrible at this point.  It is meant so that it stores my log info while also displaying it as it updates.

Here is the very basic rundown of my current algorithm to read in information from the log

```

Open file for input
While(1)
    While (input stream not bad)
        Get line from input stream
        If (input isn't null)
            Print data retrieved from input to screen
        End If
    End While
    Clear input stream if it reaches EOF
    Sleep for 2 seconds
End While
Close Input

```


I know it's not well designed or anything, it's just meant to give an overview of it
I haven't run this through a debugger or any analysis software, just ran off my CPU gauges.

Is this an acceptable method of doing it or is there a better way to go about it?  I can't read it in any smaller increments without it taking up a lot more CPU time so I thought there may be a more efficient way.  

Any suggestions are welcome.

Thanks in advance for your time.


As a side note - I'm likely using C, C++, or Python for this.

---

### Post by geirha on 2008-06-26
Sounds like "tail -f" to me ... ```
man tail
```

---

### Post by escapee on 2008-06-26
It really is in a very watered down sense.  I'd just use tail, but I want to build a GUI that can open and close logs whenever.  Could probably just call tail from the app, but I'm doing this as both to build a useful app for myself and just as a personal programming exercise since it's been over a month or so since I've coded something other than CSS.

I don't mind reinventing the wheel in this case. :)

Thanks for the quick reply and advice!  Had completely forgotten about tail.


Edit: I looked into it for a bit, if tail -f is called from the program it won't be able to return so I wouldn't be able to destroy that object or the program appropriately.

---

### Post by slavik on 2008-06-26
most used I/O calls are blocking by nature unless you tell them otherwise, hence you do not need to check for null input.

---

### Post by Can+~ on 2008-06-26
I don't quite get what you want to do, so I'll shoot a general answer. Updating files in the hard disk is wrong; evaluating the expressions usually takes nano-seconds, while hard disks take microseconds (depending on the size) to store them. So, use a buffer in the memory, then write into the hard disk every time a condition is met (usually space, time).

---edited----
I don't know why, I read "Writing ... constantly ... file". I think I misread.

---

### Post by escapee on 2008-06-26
> **Can+~ said:**
> I don't quite get what you want to do, so I'll shoot a general answer. Updating files in the hard disk is wrong; evaluating the expressions usually takes nano-seconds, while hard disks take microseconds (depending on the size) to store them. So, use a buffer in the memory, then write into the hard disk every time a condition is met (usually space, time).

Sorry about the confusion.  I'll try to elaborate a bit more.

I'm attempting to write an app that reads from log files that may be updated often.  It is disconnected from any other program.  It sits independent of any writing and just reads files, such as system.log, and prints any updates to screen - much in the same way that 'tail -f' would as geirha stated earlier.

---

### Post by slavik on 2008-06-27
> **escapee said:**
> Sorry about the confusion.  I'll try to elaborate a bit more.

I'm attempting to write an app that reads from log files that may be updated often.  It is disconnected from any other program.  It sits independent of any writing and just reads files, such as system.log, and prints any updates to screen - much in the same way that 'tail -f' would as geirha stated earlier.
here's a Perl script to do what you need.

```

use strict;
use warnings;

my $file = shift;
open FILE, $file or die $!;

while (<FILE>) {
  #process $_
}

close FILE;

```

---

### Post by escapee on 2008-06-27
> **slavik said:**
> here's a Perl script to do what you need.

```

use strict;
use warnings;

my $file = shift;
open FILE, $file or die $!;

while (<FILE>) {
  #process $_
}

close FILE;

```

Thanks Slavik.

I already had the code written and working in C++ before I posted, but I wanted to if the method was practical or if there were better ways to go about it.  I read through tail's source a bit ago and it does sooomewhat of the same thing, but much better.  Hopefully I'm on the right track?

---

### Post by kknd on 2008-06-27
" tailf 
       will print out the last 10 lines of a file and then wait for the
       file to grow.  It is similar to tail -f but does not  access  the  file
       when  it  is not growing.  This has the side effect of not updating the
       access time for the file, so a filesystem flush does not occur periodi&#8208;
       cally when no log activity is happening.
"

---

### Post by escapee on 2008-06-27
> **kknd said:**
> " tailf 
       will print out the last 10 lines of a file and then wait for the
       file to grow.  It is similar to tail -f but does not  access  the  file
       when  it  is not growing.  This has the side effect of not updating the
       access time for the file, so a filesystem flush does not occur periodi&#8208;
       cally when no log activity is happening.
"

I definitely hadn't thought of that.  Thanks kknd!

---

### Post by tldncdq on 2008-08-19
So, i recently made a search in google looking for a way to solve the same problem you had. After reading your solution i thought of another one, i expect to be more eficient. So i'm using a timer that for periods of time checks if the file was written, if it was, then i open the file and with fseek i read the latest changes, and check if some error ocurred.

```
 timer expires
 if  file.size(timeperiod.now) > file.size(timeperiod.lastupdate)
      fseek(file.size(timeperiod.lastupdate))
      file.read
      check errors

```

btw, i'm using C# and .NET 2.0, in there exists a library FileSystemWatcher that automatically warns me of changes in files or directories. Then i can read that changes with the same strategy.

So this is a solution i think it's more efficient. you are trading the "active waiting" in the while loop, where you are burning some CPU cycles for nothing, for the ability to know immediately that the file was updated. 

i think that in this case, the best thing to do, is check first if the file was written or not.

---

### Post by escapee on 2008-08-19
> **tldncdq said:**
> 

So this is a solution i think it's more efficient. you are trading the "active waiting" in the while loop, where you are burning some CPU cycles for nothing, for the ability to know immediately that the file was updated. 

i think that in this case, the best thing to do, is check first if the file was written or not.


tldncdq,
Ya I think that's what kknd suggested with tailf.  Seems like a good idea.  Right now I have a class to open and read from a log, but it will allow the client to select time intervals to check the logs for updates so as to avoid blocking and other issues tailf would disrupt the way I'm handling my app (I know I can easily avoid it, but I'm just using this way for now).  Right now I'm preoccupied porting it over to Objective-C and Cocoa from C++ and creating a GUI for it, so I'll work on updating features after that.

---

