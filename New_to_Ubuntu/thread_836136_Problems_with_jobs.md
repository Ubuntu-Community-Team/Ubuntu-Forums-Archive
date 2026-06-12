---
title: "Problems with jobs"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by jpka on 2008-06-21
I have almost same problem.
Before one critical moment, if I type unknown command in terminal, I get normal error message and return to prompt.
After this moment, on error input, this happens:

# sssss

[3]+  Stopped                 sssss
# _

no error messages, and terminal go to some mistic 'subterminal', with different command history, and 'exit' helps return to main terminal:

# exit
exit
There are stopped jobs.
# _

I of course do not know, what I misconfigure or mis-update at this critical moment. Maybe it happens itself.

Phease help, how I do to return my normal love error messages?
Thanks!

---

### Post by nowshining on 2008-06-21
try 

bash --login 

exit the terminal and try again.

---

### Post by jpka on 2008-06-22
> **nowshining said:**
> try 

bash --login 

exit the terminal and try again.

Thank you! It's work.

---

