---
title: "Unable to accept input during a script (bash &quot;read&quot;)"
date: 2007-11-01
forum: Programming Talk
---

### Post by ciper on 2007-11-01
I am having trouble with the read command. For some reason it is not accepting any input.

For example if I run it directly from the bash prompt as follows
read test
and type
123
then run the set command I can see that an environment variable named test has been created but it is blank.

Once the read command has exited the string I typed (123 in this example) is then output to the bash prompt resulting in a command not found error.

The same thing happens in a script. For example
echo "enter password"
read password
echo $password

Will echo nothing and then whatever I typed during the script will then be entered at the next prompt with a "command not found" error.

Any ideas? Its pretty hard to google for something like this since the word "read" is so common.

---

### Post by ciper on 2007-11-04
If it helps any here is the output to verify my shell

/var/tmp# echo $0
/bin/bash
/var/tmp# echo $SHELL
/bin/sh

---

### Post by jinx099 on 2007-11-04
This is the wrong section, BTW.

What you want is an expect script.  I don't believe that you can input a password with bash, but you can with expect, if fact, that is why expect was made.

---

### Post by ciper on 2007-11-04
Heh, I used to live on Impala drive right down the street from Poudre .

Which section should I ask the question in? This issue is not on Ubuntu so that is why I chose the "Other OS Talk" forum.

The string above about passwords was only an example of a way to use "read" . I am not trying to provide input for another application. My goal is to set a variable with user input, similar to the "select" command.

---

### Post by ciper on 2007-11-05
I feel a little stupid. After all I found out the issue had nothing to do with the system at all. It was in fact my Telnet client sending CRLF when I press enter and bash seeing this as two events causing the above mentioned problem.
In windows hyperterminal doesnt have this issue. 
 For windows Telnet.exe
unset crlf
Line feed mode - Causes return key to send CR (normally CRLF)

Thanks for the help. I hope someone reads this thread some day and it fixes their issue.

---

