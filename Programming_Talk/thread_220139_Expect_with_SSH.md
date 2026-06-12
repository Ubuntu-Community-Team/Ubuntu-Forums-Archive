---
title: "Expect with SSH"
date: 2006-07-21
forum: Programming Talk
---

### Post by cybermatthieu on 2006-07-21
Hi,
I have several machines that I whould like to shutdown by running a script from one other machine. So I did some research and I found expect. This program should be able to do the task but I can't do anything with it. Here's my script :
```
#!/usr/bin/expect -f
set timeout 60
set env(TERM)

spawn ssh 192.168.0.183
expect "Password: "
send "<the_password>\r"
send "eject /dev/cdrom\r"

```

All it does is wait after the password. What I'm I missing here!???

Thanks,

---

### Post by mogelhead on 2006-07-21
With ssh you can supply a command that should be executed on the remote computer. ```
man ssh
``` reveals this information (and much more): ssh [user@]hostname [command]

I used it to display the contents of my home directory on a remote computer with this command: ```
ssh user@hostname ls
```

I can't test this at the moment, but I think it should be possible to use:
```
ssh user@hostname shutdown -h now
```
or maybe with sudo:
```
ssh user@hostname sudo shutdown -h now
```

---

### Post by yaaarrrgg on 2006-07-21
If you don't need to do a sudo, or any interactive program, then it might be possible to do is all with ssh.  Otherwise, you'll probably need to use expect, since sudo is an interactive program itself.

A couple things in your expect script look odd to me (at first glance).

is Password always all caps?  I would wait for "assword" instead

why passing \r and not \n?  I guess this doesn't matter.

you should have an "expect" statement after everything you send.

for example, here's a rough example of connecting with ssh to remote server and running a ls command....

```

#!/usr/bin/expect -f
set timeout 30

#example of getting arguments passed from command line..
#not necessarily the best practice for passwords though...
set server [lindex $argv 0]
set user [lindex $argv 1]
set pass [lindex $argv 2]

# connect to server via ssh, login, and su to root
send_user "connecting to $server\n"
spawn ssh $user@$server

#login handles cases:
#   login with keys (no user/pass)
#   user/pass
#   login with keys (first time verification)
expect {
  "> " { }
  "$ " { }
  "assword: " { 
        send "$pass\n" 
        expect {
          "> " { }
          "$ " { }
        }
  }
  "(yes/no)? " { 
        send "yes\n"
        expect {
          "> " { }
          "$ " { }
        }
  }
  default {
        send_user "Login failed\n"
        exit
  }
}

#example command
send "ls\n"

expect {
    "> " {}
    default {}
}

#login out
send "exit\n"

expect {
    "> " {}
    default {}
}

send_user "finished\n"

```

---

### Post by cybermatthieu on 2006-07-24
Thanks for all the reply!

I got the script working after all.

Thanks again,

Matt

---

### Post by mogelhead on 2006-07-25
Nice!

How did you solve it?

Do you mind sharing the script, so others can benefit?

---

### Post by huzefa_from_kuwait on 2011-08-20
Hello people,

The script works perfect as posted by yaaarrrgg.

However I cannot interact with the session established.

Is there a way to accomplish that ? 

I mean I do ssh to my rtorrent server giving "screen -r". However I cannot pass any command to rtorrent like start, stop or load torrent.

Thanks.

---

### Post by saipraneeth on 2012-09-05
> **huzefa_from_kuwait said:**
> Hello people,

The script works perfect as posted by yaaarrrgg.

However I cannot interact with the session established.

Is there a way to accomplish that ? 

I mean I do ssh to my rtorrent server giving "screen -r". However I cannot pass any command to rtorrent like start, stop or load torrent.

Thanks.
place **interact** After **send "ls\n"**

---

