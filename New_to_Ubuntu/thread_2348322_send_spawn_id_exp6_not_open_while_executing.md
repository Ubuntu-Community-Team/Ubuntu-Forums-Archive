---
title: "send: spawn id exp6 not open while executing"
date: 2017-01-02
forum: New to Ubuntu
---

### Post by alapati968 on 2017-01-02
#!/usr/bin/expect


# .....- configuration .....- #
set device [lrange $argv 0 0]
set user [lrange $argv 1 1]
set pass [lrange $argv 2 2]
set enpass [lrange $argv 3 3]
set timeout 60
set now [clock seconds]
set date [clock format $now -format {%b-%d-%Y}]


# ..... do not edit below ..... #
spawn ssh -o StrictHostKeyChecking=no $user@$device
expect "password:"
send "$pass\n"
send "\n"
expect ">"
send "en\n"
expect "Password:"
send "$enpass\n"
expect "#"
#log_file $device/$device.txt
log_file /var/lib/tftpboot/$device/$device-$date.txt
send "term len 0\n"
send "show running-config\n"
expect "end\r"
send "\n"
send "exit\n"
log_file


Error is below mentioned 

send: spawn id exp6 not open
    while executing
"send "term len 0\n""
    (file "/usr/local/sbin/qbackup1" line 24)

---

