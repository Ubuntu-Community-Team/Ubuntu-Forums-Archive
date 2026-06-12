---
title: "CLI print file"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by wlraider70 on 2012-04-26
I have a file that I want to print from the command line.
There is already a CUPS printer setup.

Can I do that?

---

### Post by kimda on 2012-04-26
Have a look at the lp command. This allows you to print to the printer. Ex. lp filename.

---

### Post by wlraider70 on 2012-04-26
server@hyrule:~/Documents$ lp printme
lp: Error - no default destination available.


does that refer to a printer?



this is the site I found helpful
[http://www.computerhope.com/unix/ulp.htm#03](http://www.computerhope.com/unix/ulp.htm#03)

---

### Post by kimda on 2012-04-27
Yes.  You can also do lp -d printername filename For more info on this command look at the man page: man lp or the site you mentioned whcih is basically the man page of lp.

---

