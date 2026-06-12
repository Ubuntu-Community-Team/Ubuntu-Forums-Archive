---
title: "does Expect/TCL script know to skip a line if it does not see anything that matches?"
date: 2009-04-30
forum: Programming Talk
---

### Post by qmqmqm on 2009-04-30
Hi

I have searched around on [http://wiki.tcl.tk](http://wiki.tcl.tk) and other places online, but I did not seem to have found the answer...
My questions is: does Expect script know to skip a line if it does not see anything that matches it, but sees something that matches the next line?
For example:
Suppose I have the following Expect script:

expect "Hi1" {send_user "received 1"}
expect "Hi2" {send_user "received 2"}

If the input received is "Hi2" without having "Hi1" before it, does the script know to skip the first line of code?

If not, is there a way to make the script smart enought to do this?

Thanks a lot.

Tom

---

### Post by qmqmqm on 2009-04-30
I think I can achieve this by using a structure like this... ...

expect {
            "1" {
                return         ;# return from foo
            }
            "2" {
                break          ;# break out of while
            }
            "3" {
                if {0==[func]} {
                    exit       ;# exit program
                } else {
                    continue   ;# restart while
                }
            }
        }

But just out of curiosity, is Expect smart enough to skip a line if the input matches the next line?

Thanks,

Tom

---

