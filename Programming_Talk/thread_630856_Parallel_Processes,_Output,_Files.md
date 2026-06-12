---
title: "Parallel Processes, Output, Files"
date: 2007-12-03
forum: Programming Talk
---

### Post by kakemono on 2007-12-03
I am trying to:
Record the output of a mySQL stored procedure in one file.
Record average memory usage in another.
Record CPU usage in another.

I need to record the CPU and memory usage while the execution of the stored procedure.

right now... my shell script looks like this..

mysql - root capstone - "call timed_rowcreation(20)" >> /mypath/output.$$.rows.log $
pidstat 1 20 >> /mypath/output.$$.cpu.log $
pidstat -r 1 20 >> /mypath/output.$$.mem.log


All three of these commands work to the fullest when run from the shell directly (./rowcreator.sh). When I try to run it double double-clicking the rowcreator.sh files then selecting to "run in terminal", both of the pidstat commands always finish and give me the results I want. My issue is that if the timed_rowcreation(20) command takes longer than the pidstat commands, no output is written to output.$$.rows.log ... even though I know it successfully ran b/c the CPU and memory increases.

The stored procedure basics...
Create table
create rows for (in this case) 20 seconds
save the number of rows to variable => A
delete table
SELECT A

Any ideas why the pidstat commands seem to prevent the mySQL stored procedure output from being written to the file?

---

