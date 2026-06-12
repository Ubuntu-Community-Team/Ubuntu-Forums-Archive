---
title: "TCL/Expect Loop for CISCO IOS Upgrades"
date: 2013-06-19
forum: Programming Talk
---

### Post by bjforesthowell on 2013-06-19
I'm trying to write an expect script (I'm completely new to it by the way) that allows me to ssh into a switch, look for a certain set of software in flash, then delete it. I would like to say that if you see result "A" do action "B", and if you see result "C" do action "B". All of these results are displayed when I run one command.

I was able to get some help from a Glen Jackman on [www.stackflow.com](www.stackflow.com) ([http://stackoverflow.com/questions/17108715/am-i-missing-the-target-with-exp-continue](http://stackoverflow.com/questions/17108715/am-i-missing-the-target-with-exp-continue)) I'd just like to put out some more feelers. He showed me how to write a loop that would allow me to do one command, save the results of that command in a variable, then use that variable to determine whether or not I need to run a command given that a numbered flash directory is available.

What's happening is the section labeled "checks to see if there are other members in the stack, and if there are it will delete the old IOS off of each member." is running the command "dir ?" but for some reason isn't finding a match for the regular expression. The same thing is happening under the section labeled "checks to see if there are other members in the stack, and if there are it will copy the .bin file from flash1 to the other devices." The regular expression is working, because I can see that format working earlier on in the script in the section labeled "Checks to see if it has the new code. If it does, it schedules a reboot and sets the boot statement." When I pipe the output from the expect script into a text file I can see that for some reason it isn't matching anything. What could be pausing the regex from showing results when the expression is working earlier on in the script?

Here is a copy of the command that I would run in expect that would give me the strings that are stored in the variable.

```

B3898_RM23_SW1#dir ?
  /all             List all files
  /recursive       List files recursively
  all-filesystems  List files on all filesystems
  bs:              Directory or file name
  cns:             Directory or file name
  flash1:          Directory or file name
  flash2:          Directory or file name
  flash:           Directory or file name
  null:            Directory or file name
  nvram:           Directory or file name
  system:          Directory or file name
  tar:             Directory or file name
  tmpsys:          Directory or file name
  vb:              Directory or file name
  xmodem:          Directory or file name
  ymodem:          Directory or file name
  <cr>

  B3898_RM23_SW1#
```

Here's a copy of the script that I've written.

```
#!/usr/bin/expect -f
# Bj Howell
# June 3, 2013
# Upgrades the IOS on a list of systems.
set timeout 700
exp_internal -f ERROR 0
set host [lindex $argv 0]
set user [lindex $argv 1]
set pass [lindex $argv 2]
spawn ssh -o StrictHostKeyChecking=no $user@$host
expect "assword:"
send "$pass\r"
expect "*#"

#Checks to see if it has the new code. If it does, it schedules a reboot and sets the boot statement.

send "term length 0\r"
expect "*#"
send "wr mem\r"
expect "*#"
send "dir flash:\r"
expect {
    -re {\mc3750-ipservicesk9-mz\.122-55\.SE7\.bin\M} {
        send "conf t\r"
        expect "*(config)#"
        send "boot system switch all flash:c3750-ipservicesk9-mz.122-55.SE7.bin\r"
        expect "*(config)#"
        send "exit\r"
        expect "*#"
        send "reload at 02:00 15 June\r"
        expect "System configuration has been modified. Save?"
        send "yes\r"
        expect "Proceed with reload?"
        send "\r"
        expect "*#"
        send "wr\r"
        expect "*#"
        send "exit\r
        expect eof
        }
    -re {\mc3750-ipservicesk9-mz\.122-55\.SE5(?:\.bin)?\M}
}

# checks to see if there are other members in the stack, and if there are it will delete the IOS off of each member.

set flash_dirs {}
send "dir ?\r"
expect {
    -re {\m(flash[1-9])\M} {
        lappend flash_dirs $expect_out(1,string)
        exp_continue
    }
    "*#"
}
foreach dir $flash_dirs {
    send "delete /force /recursive $dir:c3750-ipservicesk9-mz.122-55.SE5\r"
    expect "*#"
    send "delete /force /recursive $dir:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
    expect "*#"
}

#This deletes the IOS from a single device, then tftps the IOS to flash. If the TFTP fails it tries one more time.

send "copy tftp: flash:\r"
expect "Address or name of remote host []?"
send "204.208.204.209\r"
expect "Source filename []?"
send "c3750-ipservicesk9-mz.122-55.SE7.bin\r"
expect "Destination filename"
send "\r"
expect {
    -re {\mtimed out\M} {
        send "copy tftp: flash1:\r"
        expect "Address or name of remote host []?"
        send "204.208.204.209\r"
        expect "Source filename []?"
        send "c3750-ipservicesk9-mz.122-55.SE7.bin\r"
        expect "Destination filename [c3750-ipservicesk9-mz.122-55.SE7.bin]?"
        send "\r"
        expect "*#"
        }
    -re {\mOK - 13010154 bytes\M}
}


# checks to see if there are other members in the stack, and if there are it will copy the ios from flash1 to the other devices.

set flash_dirs {}
send "dir ?\r"
expect {
    -re {\m(flash[1-9])\M} {
        lappend flash_dirs $expect_out(1,string)
        exp_continue
    }
    "*#"
}
foreach dir $flash_dirs {
    if {$dir eq "flash1"} continue
    send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin $dir:\r"
    expect "Destination filename"
    send "\r"
    expect "*#"
}

# Sets the boot statement for the stack

send "conf t\r"
expect "*(config)#"
send "boot system switch all flash:c3750-ipservicesk9-mz.122-55.SE7.bin\r"
expect "*(config)#"
send "exit\r"
expect "*#"

#sets the reload time, changes the term length, writes everything to memory, then exits.

send "reload at 02:00 22 June\r"
expect "System configuration has been modified. Save?"
send "yes\r"
expect "Proceed with reload?"
send "\r"
expect "*#"
send "term length 50\r"
expect "*#"
send "wr mem\r"
expect "*#"
send "exit\r"



expect eof
```

This is the output of the script sent to a text document.

```
send: sending "dir ?\r" to { exp7 }
Gate keeper glob pattern for '\m(flash[1-9])\M' is 'flash?'. Activating booster.

expect: does "\r\n    6  -rwx       28612  Apr 23 2012 02:35:18 +02:00  config.text.backup\r\n    5  -rwx        1276   Mar 1 1993 01:04:41 +01:00  vlan.dat\r\n    4  -rwx        2404  Jun 17 2013 14:01:30 +02:00  private-config.text\r\n   88  -rwx        2404  Apr 23 2012 02:35:18 +02:00  private-config.text.backup\r\n    8  -rwx       43535  Jun 17 2013 14:01:29 +02:00  config.text\r\n\r\n32514048 bytes total (19417088 bytes free)\r\nB3762_6D205C_SW1&2#" (spawn_id exp7) match regular expression "\m(flash[1-9])\M"? Gate "flash?"? gate=no
"*#"? yes
expect: set expect_out(0,string) "\r\n    6  -rwx       28612  Apr 23 2012 02:35:18 +02:00  config.text.backup\r\n    5  -rwx        1276   Mar 1 1993 01:04:41 +01:00  vlan.dat\r\n    4  -rwx        2404  Jun 17 2013 14:01:30 +02:00  private-config.text\r\n   88  -rwx        2404  Apr 23 2012 02:35:18 +02:00  private-config.text.backup\r\n    8  -rwx       43535  Jun 17 2013 14:01:29 +02:00  config.text\r\n\r\n32514048 bytes total (19417088 bytes free)\r\nB3762_6D205C_SW1&2#"
expect: set expect_out(spawn_id) "exp7"
expect: set expect_out(buffer) "\r\n    6  -rwx       28612  Apr 23 2012 02:35:18 +02:00  config.text.backup\r\n    5  -rwx        1276   Mar 1 1993 01:04:41 +01:00  vlan.dat\r\n    4  -rwx        2404  Jun 17 2013 14:01:30 +02:00  private-config.text\r\n   88  -rwx        2404  Apr 23 2012 02:35:18 +02:00  private-config.text.backup\r\n    8  -rwx       43535  Jun 17 2013 14:01:29 +02:00  config.text\r\n\r\n32514048 bytes total (19417088 bytes free)\r\nB3762_6D205C_SW1&2#"
send: sending "copy tftp: flash:\r" to { exp7 }

expect: does "" (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no
d
expect: does "d" (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no
i
expect: does "di" (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no
r
expect: does "dir" (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no

expect: does "dir " (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no
?
expect: does "dir ?" (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no

  /all             List all files
  /recursive       List files recursively
  all-filesystems  List files on all filesystems
  bs:              Directory or file name
  cns:             Directory or file name
  flash1:          Directory or file name
  flash2:          Directory or file name
  flash:           Directory or file name
  null:            Directory or file name
  nvram:           Directory or file name
  system:          Directory or file name
  tar:             Directory or file name
  tmpsys:          Directory or file name
  vb:              Directory or file name
  xmodem:          Directory or file name
  ymodem:          Directory or file name
  <cr>

B3762_6D205C_SW1&2#dir 
expect: does "dir ?\r\n  /all             List all files\r\n  /recursive       List files recursively\r\n  all-filesystems  List files on all filesystems\r\n  bs:              Directory or file name\r\n  cns:             Directory or file name\r\n  flash1:          Directory or file name\r\n  flash2:          Directory or file name\r\n  flash:           Directory or file name\r\n  null:            Directory or file name\r\n  nvram:           Directory or file name\r\n  system:          Directory or file name\r\n  tar:             Directory or file name\r\n  tmpsys:          Directory or file name\r\n  vb:              Directory or file name\r\n  xmodem:          Directory or file name\r\n  ymodem:          Directory or file name\r\n  <cr>\r\n\r\nB3762_6D205C_SW1&2#dir " (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no


expect: does "dir ?\r\n  /all             List all files\r\n  /recursive       List files recursively\r\n  all-filesystems  List files on all filesystems\r\n  bs:              Directory or file name\r\n  cns:             Directory or file name\r\n  flash1:          Directory or file name\r\n  flash2:          Directory or file name\r\n  flash:           Directory or file name\r\n  null:            Directory or file name\r\n  nvram:           Directory or file name\r\n  system:          Directory or file name\r\n  tar:             Directory or file name\r\n  tmpsys:          Directory or file name\r\n  vb:              Directory or file name\r\n  xmodem:          Directory or file name\r\n  ymodem:          Directory or file name\r\n  <cr>\r\n\r\nB3762_6D205C_SW1&2#dir \r\n" (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no
Directory of flash:/

    2  -rwx        9240  Jun 17 2013 14:01:30 +02:00  multiple-fs
    3  -rwx    13006601  Apr 24 2012 19:24:08 +02:00  c3750-ipservicesk9-mz.122-55.SE5.bin
    6  -rwx       28612  Apr 23 2012 02:35:18 +02:00  config.text.backup
    5  -rwx        1276   Mar 1 1993 01:04:41 +01:00  vlan.dat
    4  -rwx        2404  Jun 17 2013 14:01:30 +02:00  private-config.text
   88  -rwx        2404  Apr 23 2012 02:35:18 +02:00  private-config.text.backup
    8  -rwx       43535  Jun 17 2013 14:01:29 +02:00  config.text

32514048 bytes total (19417088 bytes free)
B3762_6D205C_SW1&2#
expect: does "dir ?\r\n  /all             List all files\r\n  /recursive       List files recursively\r\n  all-filesystems  List files on all filesystems\r\n  bs:              Directory or file name\r\n  cns:             Directory or file name\r\n  flash1:          Directory or file name\r\n  flash2:          Directory or file name\r\n  flash:           Directory or file name\r\n  null:            Directory or file name\r\n  nvram:           Directory or file name\r\n  system:          Directory or file name\r\n  tar:             Directory or file name\r\n  tmpsys:          Directory or file name\r\n  vb:              Directory or file name\r\n  xmodem:          Directory or file name\r\n  ymodem:          Directory or file name\r\n  <cr>\r\n\r\nB3762_6D205C_SW1&2#dir \r\nDirectory of flash:/\r\n\r\n    2  -rwx        9240  Jun 17 2013 14:01:30 +02:00  multiple-fs\r\n    3  -rwx    13006601  Apr 24 2012 19:24:08 +02:00  c3750-ipservicesk9-mz.122-55.SE5.bin\r\n    6  -rwx       28612  Apr 23 2012 02:35:18 +02:00  config.text.backup\r\n    5  -rwx        1276   Mar 1 1993 01:04:41 +01:00  vlan.dat\r\n    4  -rwx        2404  Jun 17 2013 14:01:30 +02:00  private-config.text\r\n   88  -rwx        2404  Apr 23 2012 02:35:18 +02:00  private-config.text.backup\r\n    8  -rwx       43535  Jun 17 2013 14:01:29 +02:00  config.text\r\n\r\n32514048 bytes total (19417088 bytes free)\r\nB3762_6D205C_SW1&2#" (spawn_id exp7) match glob pattern "Address or name of remote host ?"? no
c
```

---

