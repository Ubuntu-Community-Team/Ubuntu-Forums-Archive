---
title: "Expect script errors out after 1,016 iterations"
date: 2015-10-20
forum: Programming Talk
---

### Post by UncleBoarder on 2015-10-20
I don't know where to go for this question... I've found lots of suggestions on Google and tried most of them but none work. So I'm coming to the Ubuntu community in hopes of finding an Expect expert.

My Expect script is designed to telnet to every address in my /16 network. Some addresses will respond, some won't, that's ok. The script runs and does what I want it to, but for some reason it stops after 1,016 connections. So I'm thinking that I'm not closing something properly but I don't know what else to do. I did a "ps -A | grep telnet" while it's running and all my telnet sessions say "<defunct>".

The error I receive is:

NotifierThreadProc: could not create trigger pipe
parent: sync byte write: broken pipe

Here's my code (shortened a bit for readability):
```

#!/usr/bin/expect
set timeout 1
set SITE 1
set HOST 1
while {$SITE < 255 } {
  while {$HOST < 255 } {
    spawn telnet 10.0.$SITE.$HOST
# this just displays the spawn ID for troubleshooting
set netip $spawn_id
send_user $netip\n
    expect {
# no need to process further if Cisco switch is detected
      timeout {send eof; send_user "TIMED OUT\n"; close}
      "Username:" {
        expect "'^]'."
        send_user "CISCO SWITCH\n"
        close
      }
# here's what I'm looking for, a login for a UPS
      "User Name :" {
        send AAA\r
        expect "Password  :"
        send P4SS\r
        expect {
# if User Name is requested twice in a row, then the password is bad
          "User Name :" {
            send eof
            send_user "BAD PASSWORD\n"
            close
          }
          "Log" {
            sleep .1
            send 3\r
              (do more menu navigation and make changes in here... all this works fine)
            expect "Log"
            sleep .1
            send 4\r
            expect "foreign host."
            close
          }
        }
      }
    }
    set HOST [expr $HOST+1]
  }   
  set HOST 1
  set SITE [expr $SITE+1]
} 
```

Ubuntu 14.04
Expect 5.45

---

### Post by howefield on 2015-10-20
Hello UncleBoarder, I have moved your thread to the "*Programming Talk*" forum. There are a few forums it could fit but Desktop environments probably isn't one of them.

---

### Post by UncleBoarder on 2015-11-16
<bump>

---

### Post by nicolas65 on 2016-06-27
I have had exactly the same problem and it was driving me crazy. After a lot of research, I managed to link it to the script indeed not closing everything properly.

To properly close a spawned process, you must use the "close" command but also the "wait" command (usually with the -nowait option), otherwise the spawned process is left in a zombie state, taking a system file descriptor, until you reach the limit set on the system, usually around 1,000.
Everywhere where you have "close" in your script follow it with the "wait -nowait" command to properly kill the spawned process. That should resolve your issues.

You can also check that indeed it is a file descriptor exhaustion by doing the following while your script runs:

Find its process ID:
[root@localhost fd]# ps -aux | grep myscript
root      49015 61.0  1.5 138672  7764 pts/0    Sl+  11:55   0:04 /usr/bin/expect -- ./myscript.exp

then go to /proc/[processnumber]/fd
cd /proc/49015/fd

This directory lists all File Descriptor currently open by the script.
While it is running, keep an eye on their total number, easily done with:
ls -la | wc -l
If the expect script is properly opening and closing down all processes then the value will remain constant (small variation up and down as process are open/closed, but stay around the same value). If you are not closing everything properly, this number will increase more and more until you reach the system default limit of around 1000, at which point you get the "NotifierThreadProc: could not create trigger pipe" error.

If the number of open FD continues to rise even after using the "wait -nowait" command then the logic of the script must be checked since it means that in some cases epects doesn't send the close and wait commands so need to check exactly what is going on, whether/when your script receives and EOF from the process, those sorts of things.

---

