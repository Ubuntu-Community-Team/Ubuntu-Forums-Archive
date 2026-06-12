---
title: "Python script to generate a list file of successes and email"
date: 2011-06-28
forum: Programming Talk
---

### Post by pafoo on 2011-06-28
I made a program that does a number of jobs/tests on 1 server. If there were any failures/errors it writes to a file, then emails it off. Afterwards it finishes and closes. This program is set up via cron to do this job on 16 different servers via sys.argv[1] being the name of the server. Each of the jobs are separated via a time frame in cron. What I am trying to do, is if the program finishes on server1 with no errors, it will add this to some type of list/file that at the completion of the day's cron's will email the number of successful servers and their name.

So I am assuming that at the end of each run I can do something like

message.write(sys.argv[1], " Completed successfully\n")
message.close
if len(message) == 16:
 sendmail blah blah
### open the file to read assign to variable etc

Any idea's would be greatly appreciated!!

---

