---
title: "Expect Question - Basics"
date: 2009-01-26
forum: Programming Talk
---

### Post by alyssariffic on 2009-01-26
I have a question regarding expect that I was hoping someone could help me with.  Basically, I've written a script to automate creation of ssh keys and adding those keys to the authorized keys list, and that works fine without expect.  Now, I'm trying to add Expect to make it work without having to worry about a lot of user input.  However, I keep having trouble with "Invalid spawn id" errors.  From my understanding, these occur when the process that expect is running with has ended but there are Expect statements that were never executed.


The code I have is below.  The error I get is 
"expect: invalid spawn id (4) 
while executing "expect -nobrace "*@master password:" send "$password\r".

I believe this is due to the fact that the user is never prompted for the password if the ssh keys already exist. But, I want my script to work whether or not the keys exist or not.  Is there some way I can make it just ignore these expect statements if the request for a password never comes up? Or is there something else I'm missing.

Note: the script uses commands that request the password 3 times, so that's why it's in there 3 times. The line it refers to in the error though is the one that the first password request is at.

Thanks in advance for any help.

```

#!usr/local/bin/expect -f
# Requires 2 arguments
#   username - user's username
#   password - passsword of user
#-----------------------------------

set username [lrange $argv 0 0]
set password [lrange $argv 1 1]
spawn ./ssh-keys.sh $username@master
expect { 
	"Enter passphrase (empty for no passphrase):"
	send "\r"
}
expect { 
	"Enter same passphrase again:"
	send "\r"
}
expect {
	"Are you sure you want to continue connecting (yes/no)?"
	send "yes\r"
}
expect { 
	"*@master's password:"
	send "$password\r"
}
expect { 
	"*@master's password:"
	send "$password\r"
}
expect { 
	"*@master's password:"
	send "$password\r"
}
```

---

### Post by clustermonkey on 2009-01-31
Expect allows conditional checks for contol, basically a 
case statement.  The code snippet below checks for the 
"Are you sure..." or an eof (the driven script/program ended).
If it gets the question, it sends the password.  If not it
just falls through. 

```
expect {
       "Are you sure you want to continue connecting (yes/no)?" {
                send "yes\r"
                expect { "*@master's password:"
                        send "$password\r"
                }
                expect { "*@master's password:"
                        send "$password\r"
                }
                expect { "*@master's password:"
                        send "$password\r"
                }
        }
        eof { }
}
```

Hope this helps...

---

