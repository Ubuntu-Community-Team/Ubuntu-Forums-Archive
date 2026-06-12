---
title: "Expect Function Help Using Bash"
date: 2011-10-04
forum: Programming Talk
---

### Post by metallica1973 on 2011-10-04
By no means am I scripting master nor a "expect" guru so afters days of frustration I have given up. I am trying to add a couple of functions using "expect" to automate an mysqldump over ssh and then have it scp the mysqldump back to the base to add it to our backup archives but have ran into a brick wall. 

```

################################################################# Functions using Expect########################################

ssh_mysql_bak ()
{
expect
spawn ssh -p 3202 testuser@10.7.0.105 {mysqldump --opt -u root -pmysqlpass mysql > mysql.bak.dump}
expect {
                "testuser@10.7.0.105's password:"{
                                                send "password\r"
                } timeout {
                           exit
                }
  }
}

scp_mysql_bak ()
{
expect
spawn scp -P 3202 testuser@10.7.0.105:/home/testuser/mysql.bak.dump $home
expect {
         "testuser@10.7.0.105's password:"{
                                           send -- "password\r"
         } timeout {
                   exit
        }
   }
}

```

When I run my script, it keeps erroring with:

```

bash -x saint.ksh
saint.ksh: line 18: syntax error near unexpected token `"timeout"'
saint.ksh: line 18: `		} "timeout" { 

```

I originally used autoexpect to create my initial .exp scripts and just pulled my expect stuff from there with a couple of tweaks:

SSH.exp

```

#!/usr/bin/expect -f


set timeout -1
spawn ssh -p 3202 testuser@10.7.0.105 {mysqldump --opt -u root -pmysqlpass mysql > mysql.bak.dump}
match_max 100000
expect -exact "\r
\r
############################ Welcome ######################################\r
testuser@10.7.0.105's password: "
send -- "password\r"
expect eof

```

and respectively

```

#!/usr/bin/expect -f
set timeout -1
spawn scp -P 3202 testuser@10.7.0.105:/home/testadmin/mysql.bak.dump .
match_max 100000
expect -exact "\r
\r
############################ Welcome ######################################\r
testadmin@10.7.0.105's password: "
send -- "password\r"
expect eof

```

Let me have it!!!

---

### Post by metallica1973 on 2011-10-08
I had a old friend on mine several years ago do this and it worked fine so that is why am attempting to replicate what he did. Here is what he did but I cannot get my script to due the same. It has something to due I think with my brackets {{{}}}}

He used korn shell

```

expect_session()
{
echo " "  >> $logdata
echo " " > $logOK # Do not append to this logfile...
# Open a telnet session to a remote server, and wait for a username prompt.
expect << DONE >>$logdata 
spawn telnet -e~ -l$userid $ip_address
expect {
       Password: {
                 send "~"
                 sleep 1
                 log_file -a $logOK
                 send_log "$ip_address Yes\n" 
                 log_file
                 exp_continue
       } timeout {
                 log_file -a $logOK
                 send_log "$ip_address No\n"
                 log_file  
                 exit
       } "closed by foreign host" {
                 log_file -a $logOK
                 send_log "$ip_address No\n"
                 log_file
                 exit
       } "Connection refused" {
                 log_file -a $logOK
                 send_log "$ip_address No\n"
                 log_file
                 exit
       } -exact telnet>  {
                 send "quit\n"
                 sleep 1
                 exit
       } 
DONE

```

I made progress. I was reading some additional information from another post and came up with this:

```

ssh_mysql_bak()
{
expect <<EOD
spawn ssh -p 3202 testuser@10.7.0.105 "mysqldump --opt -u root -pmysqlpass mysql > mysql.bak.dump"
expect "testuser@10.7.0.105's password:""
send "MyPassword\r"
EOD
}

```

My korn scripts runs and call this function fine and I can see if passes the command but then ends prematurely. When I check on the remote server, I dont not see "mysql.bak.dump". If I test via the expect> interface, every operates as expected no problems at all, so I know the command are correct. There must be some inside the function that I am doing wrong. I replaced the "" for {}:

```

spawn ssh -p 3202 testuser@10.7.0.105 {mysqldump --opt -u root -pmysqlpass mysql > mysql.bak.dump}

```

and it doesnt make any difference. Any ideas?

---

