---
title: "Reading Cronjob Output"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by Fidividi on 2014-10-23
I have a task setup to run on my cronjob where I need to read the output. What I need from the output is the starting character (let's say 'A') and the ending character (let's say 'Z'). A helps me understand my script started from the right place, and Z helps me understand my script finished at the right place.

So, it is important for me to run that cronjob, and see that my output is having proper A and Z.

I know that not sending the script to '> /dev/null' will try to mail using the MTA, which is not something I want to do. I also don't want to send it to /dev/null because I need to read the output.

When I run my script normally from the console (tty), I am able to see the start character (A) and end character (Z), but when I let the cronjob run, my script fails to read the start character and complains about 'no start characters'.

What can be the problem?
Thank you.

---

### Post by papibe on 2014-10-23
Hi Fidividi. Welcome to the forum ):P

You can redirect all the output of your script to a file. For instance:
```
00 15 * * * /path/to/script.sh > /path/to/output.log 2>&1
```
After 'script.sh' runs, all of its output, including error messages, will be on the file 'output.log'.

Hope it helps. Let us know how it goes.

Come here often and have fun.
Regards.

---

