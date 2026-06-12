---
title: "expect program executing next command before existing one finishes"
date: 2014-02-26
forum: Programming Talk
---

### Post by Bonnie_Mtengwa on 2014-02-26
Hie guys, im new to scripts so i just thought of automating some ssh functions using "expect" and "cron". some people dump files into their server daily so i have to collect them daily and delete the files when i finish copying them. my problem is that expect is sending the next command before the running command  finishes excecuting. for example, 

my script follow the secquence

1) ssh into remote host  ---> 
2) change directory into folder with file  -->
3) compress all csv files into tar.gz file  -->
4) copy tar.gz file to remote host i.e (to my server)  -->
5) delete csv and tar.gz file when done downloading the file to my server.

so before the comptression of files is complete, im seeing on the terminal the copy command being sent, followed by the delete command, to the extent that when the compression finishes, there is no other command to execute.
[HTML]
spawn ssh ftp@192.168.1.1
#######################

expect "*sword.*"
exp_send "password\r"
expect "$ "
exp_send "cd /srv/network_stats/stats\r"
expect "$ "
exp_send "tar -czvf compressed_files.tar.gz *.csv\r"
expect "$ "
exp_send "rm -rf *.csv\r"
expect "$ "
exp_send "scp *.tar.gz  ftpuser@191.168.2.1:/ftp/stats/company1/2014/stats/\r"
expect "*sword.*"
exp_send "mypassword\r"
expect "$ "
exp_send "exit\r"

[/HTML]


what am i doing wrong?

---

### Post by Vaphell on 2014-02-26
why don't you split compression and download into 2 different cron jobs with a delay between them? 23:30 compression, 23:45 download.

Your expect approach looks incredibly fragile because it tries to mimick human interaction when none is really needed. I'd set up a script on the other side to do things in order to eliminate the need for doing everything in expect (open ssh connection, run script, done). The script could also be cronned so you would be able to copy stuff with scp right off the bat.

my idea
ftp machine: cron job at 23:30 compress_stuff.sh
local machine: cron job at 23:45 copy_compressed_stuff.sh (or directly scp ....)

---

