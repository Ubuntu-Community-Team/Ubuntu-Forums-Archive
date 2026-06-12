---
title: "error running autoexec script"
date: 2007-08-24
forum: Programming Talk
---

### Post by trakzcorp on 2007-08-24
Hi all, I get this error when I try to run the autoexec script posted on the Ubuntu website


tab@marklinux:~/scripts$ . autoexpect
bash: proc: command not found
bash: autoexpect: line 26: syntax error near unexpected token `}'
bash: autoexpect: line 26: `}'
tab@marklinux:~/scripts$ 


I have a very basic understanding of shell scripts, I cannot figure out what is wrong with line 26 in this script

the line 26 of the script is below


line 18 set promptmode 0
line 19 set option_keys ""
line 20
line 21 proc check_for_following {type} {
line 22 if {![llength [uplevel set argv]]} {
line 23 puts "autoexpect: [uplevel set flag] requires following $type"
line 24 exit 1
line 25 }
line 26 }
line 27 }
line 28
line 29 while {[llength $argv]>0} {

---

### Post by slavik on 2007-08-24
unless there is an opening brace in the code you didn't paste, there are 3 closing braces that don't match up.

---

