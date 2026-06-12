---
title: "Expect Telnet script sending password twice"
date: 2011-10-13
forum: Programming Talk
---

### Post by SuaSwe on 2011-10-13
Hi all,

I'm trying to massage an Expect script into a working state however can't get past the hurdle that it keeps sending my password twice - once to log in to the Cisco devices (which works fine) and then again on the Cisco devices' command line, causing the script to interrupt. 

Script below:
```

#!/opt/csw/bin/expect -f
# Usage: ./cisco_config.exp <input_file>

if 0==$argc {
        send_user "Usage: $0 <devices>\n"
        send_user "\n<devices> is the list of Cisco devices requiring configuration\n"
        exit 1
}

set timeout 10

# Open file and split into an array
set load_devices [open "$argv" r]
set device_list [split [read $load_devices] "\n"]
close $load_devices

send_tty "Enter your username: "
expect_user -re "(.*)\n"
set username $expect_out(1,string)
stty -echo
send_tty "Enter your password: "
expect_user -re "(.*)\n"
set password $expect_out(1,string)
stty echo

# Loop through array and perform commands
send_tty "\n"
foreach device $device_list {
        if {$device != ""} {
                send_tty "Connecting to: $device...\n"
                log_user 1

                spawn /usr/bin/telnet $device

                expect {
                        eof {
                                send_tty "\n"
                                send_tty "Connection to host failed: $expect_out(buffer)"
                                continue
                        } -re sername {
                                send "$username\r"
                        }
                }
                expect {
                        -re assword {
                                send "$password\r"
                                exp_continue
                        } failed {
                                send_tty "\n"
                                send_tty "Invalid username or password\n"
                                exit
                        } timeout {
                                send_tty "Connection to $device timed out\n"
                                continue
                        }
                }
                expect {
                           -re "#" {
                                send "show ver | i up\r"
                        }
                 }
                 expect {
                           -re "#" {
                                send "exit\r"
                        }
                }
                expect eof
                wait
        }
}
```

Result of running this, pretending my password is "hello123":

```

[me@server]$ ./cisco_login.exp devices
Enter your username: user
Enter your password:
Connecting to: router1...
spawn /usr/bin/telnet router1
Trying 10.1.1.5...
Connected to router1

Username: user
Password:

router#hello123
Translating "hello123"
% Unknown command or computer name, or unable to find computer address
router#

```

I have scoured the script and can't see any reason why the password is sent a second time. If anyone could nudge me in the right direction that would be most appreciated!

---

### Post by SuaSwe on 2011-10-15
Any ideas, guys?

---

### Post by SuaSwe on 2011-10-22
Anyone?

---

### Post by GreenFire on 2013-03-05
Pretty old post but I'll reply anyway.

The "-re" is used for regular expression parsing. You don't really need it while expecting the "password" prompt string.
Hence, replace the "-re assword" with a simple "assword".

---

