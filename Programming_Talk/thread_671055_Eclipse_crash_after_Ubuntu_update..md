---
title: "Eclipse crash after Ubuntu update."
date: 2008-01-18
forum: Programming Talk
---

### Post by ksmster on 2008-01-18
Hi.
After today Ubuntu 7.10, Gutsy Gibbon  update my Eclipse(3.3) will crash with: 


The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 805 error_code 11 request_code 145 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I try to reinstall Eclipse but the result is same.


Can you help me?

---

### Post by fishyf on 2008-01-19
I also had a problem with Eclipse on the last update. However, in my case, it was that the JVM exited.
Also it has something to do with my workspace, because if I login as a new user, it starts perfectly.
It may be something to do with phpeclipse because the phpeclipse options don't appear for the new user.

Edit: when run from the command line, I get the same error message that you do.

---

