---
title: "Using Expect and if"
date: 2009-02-16
forum: Programming Talk
---

### Post by cogitate228 on 2009-02-16
Hi there,

I'm very green when it comes to scripting but I'm trying to get an expect script to recognize a specific shell prompt and then execute some simple commands when it detects that particular prompt.

So say I log in to a box, and the shell prompt is

abc#

it executes commands

and if my script logs in to another box, it would be a different shell prompt like:

def#

How do i get my expect script to recognize that? Reason being is because i need to login as root to execute these commands and the prompts are different from server to server. I've tried to set a variable but it doesn't seem to work either. Here is my code below, with the variable commented out:


```
#!/usr/local/bin/expect -f
log_user 0

spawn ssh [lindex $argv 0]
        send "su -\r"
expect "Password:"
        send "password\r"
expect "#"
        send "\r"
        send "su - root\r"
        send "\r"

log_user 1

#set PROMPTNAME [send "echo \$LOGNAME\r"]

        send "echo \$LOGNAME\r"


        if { $PROMPTNAME == "root" } {
                        send "command\r"
                        send "command\r"
                        send "exit/r"
                        exit
                
        } else {
                        send "command\r"
                        send "command\r"
                        send "exit/r"
                        exit
                }
expect eof
```

Any help would be greatly appreciated as I've been looking on other forums to no avail :( Am I totally goofing it up? Or is there a better way? Am I close? Thanks...

---

### Post by Silver Bullet on 2009-02-16
I was just reading/testing expect today as well. :D

From what i understand, you don't have to match the full prompt name. For your example, abc# and def# would work with matching just #

so you could do this and it should work for both abc# and def#

expect #
send command\r

---

### Post by cogitate228 on 2009-02-16
> **Silver Bullet said:**
> I was just reading/testing expect today as well. :D

From what i understand, you don't have to match the full prompt name. For your example, abc# and def# would work with matching just #

so you could do this and it should work for both abc# and def#

expect #
send command\r

Thanks for the quick reply, but the problem with my situation is that we have old and new servers with different root environments. So the commands I need to run will differ from box to box. I need expect to recognize either the prompt or an environment variable.

---

### Post by lonchus on 2009-03-11
You could use something like this:

expect {
"abc#" { send "something\r"}
"def#" { send "another_thing\r"}
}

I think this is called "Pattern/Action", also you could make use of regular expressions. Take a look a this url: [http://expect.nist.gov/](http://expect.nist.gov/) or at this one 
Hope this works for you.

---

