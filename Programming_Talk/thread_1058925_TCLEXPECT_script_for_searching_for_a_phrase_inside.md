---
title: "TCL/EXPECT script for searching for a phrase inside of a file"
date: 2009-02-03
forum: Programming Talk
---

### Post by qmqmqm on 2009-02-03
Hi

I am new to shell proframming. Does anyone know how to write a tcl/expect script for searching for a phrase inside of a file?

Thanks.

Tom

---

### Post by stevescripts on 2009-02-03
While I am a great fan and advocate of tcl - I urge you not to re-invent the wheel ...
(unless you just want to, as a learning process)

Do you want something that can't be readily done with tools like grep?

Also, a good example if you want to script your own:
[http://wiki.tcl.tk/8405](http://wiki.tcl.tk/8405)

If you are learning/using tcl - the wiki is you friend.

Steve

---

### Post by qmqmqm on 2009-02-03
Thank you Steve!

Here is another way that I just found to do this:

```

set pattern myPattern

set isMatch [string match *$pattern* "SOME_STRING"]

if { $isMatch != 0 } {
	puts "match!"
} else {
	puts "no match!"
}
```

( [http://tmml.sourceforge.net/doc/tcl/string.html](http://tmml.sourceforge.net/doc/tcl/string.html) )


As a follow up question, I know that grep does the job, but how do you use grep inside of a piece of tcl script to accomplish the same?

Thanks,

Tom

---

### Post by stevescripts on 2009-02-03
> **qmqmqm said:**
> Thank you Steve!
...
As a follow up question, I know that grep does the job, but how do you use grep inside of a piece of tcl script to accomplish the same?


Using grep rather than tcl - saves you scripting the part to open the file, read it into a var, and then check for matches. (also, faster)

As far as using grep in a tcl file - some simple examples:

```

steveo@delldesktop:~/Desktop$ tclsh
% exec grep proc swatch.tcl -c &
3
5875
% set result [exec grep proc swatch.tcl -c]
3
% puts $result
3
% set otherres [exec grep proc swatch.tcl]
proc chgvar { } {
proc run {  } {
proc reset { } {
% puts $otherres
proc chgvar { } {
proc run {  } {
proc reset { } {

```

(swatch.tcl is a little tcl/tk stopwatch script that was handy)

Note that running grep in the background returns not only the count, but also the PID.

Steve

---

### Post by qmqmqm on 2009-02-03
Hi Steve

Thank you very much!

Although my unix box (Solaris) only understood "grep" with a different parameter order:
```
grep -c pattern filename
```

But I was able to get it working.

Thanks!

Tom

---

