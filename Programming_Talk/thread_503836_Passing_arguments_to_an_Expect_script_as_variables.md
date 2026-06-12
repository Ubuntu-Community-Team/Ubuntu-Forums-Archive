---
title: "Passing arguments to an Expect script as variables"
date: 2007-07-18
forum: Programming Talk
---

### Post by piers on 2007-07-18
Does anyone know how I can run a script with arguments and then use those arguments as variables in an Expect script?

So i would run **$ myscript.exp thisuser thispass** and then myscript.exp will be able to use *thisuser* and *thispass* as variables.

All the docs I can find for expect are really really old, does anybody else still use it?

---

### Post by fabianp on 2008-08-16
>So i would run $ myscript.exp thisuser thispass and then >myscript.exp will be able to use thisuser and thispass as >variables.

You need to use lindex, try

set arg1 [lindex $argv 0]
set arg2 [lindex $argv 1]

send $arg1\n
send $arg2\n

I hope this helps,

--
Fabian

---

### Post by miahfost on 2009-06-18
That helps me Fabian - thanks!

---

### Post by mikeabout on 2009-11-21
[B] 	 Thank you so much!!!  Worked perfectly!
[/B]

---

### Post by SterlingCamden on 2010-07-18
Thanks, this was exactly what I was looking for!

---

### Post by sg552sg552 on 2011-06-22
Thanks a lot!  works for me!!!!
(Expect is really powerful .... it's not only a simple command.... )

---

### Post by lingeshram on 2013-04-12
From your tutorial i write a script for copy scp files between two servers by passing password as an arguments thanks a lot







first install expect

    sudo apt-get install expect



then create copyremotefiles.sh




    #!/usr/bin/expect -f
    
    set from [lindex $argv 0]
    set to [lindex $argv 1]
    set pass [lindex $argv 2]
    
    # connect via scp
    spawn scp -r $from $to
    #######################
    expect {
    -re ".*es.*o.*" {
    exp_send "yes\r"
    exp_continue
    }
    -re ".*sword.*" {
    exp_send $pass\n
    }
    }
    interact

Then change file permission 

    chmod 755 copyremotefiles.sh

now run 

    ./copyremotefiles.sh /path/myfile.txt root@45.65.89.22:/home/lingesh/ PASSWORD_OF_REMOTE_SERVER


PASSWORD_OF_REMOTE_SERVER is root password of 45.65.89.22

Enjoy.....

---

### Post by oldos2er on 2013-04-13
Old thread closed.

---

