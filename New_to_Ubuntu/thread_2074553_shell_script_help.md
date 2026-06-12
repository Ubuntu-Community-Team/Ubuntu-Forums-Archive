---
title: "shell script help"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by hookitup on 2012-10-21
hello folks, i have this shell script, just messing around with shell scripts for fun. how would i edit this file so that if the username is wrong it will display the proper message "sorry wrong username exiting in 5 seconds" and then wait 5 seconds and apply the exit command? Im just not sure how to add it properly into the else field. keep in mind i do not want it to initiate the command to wait 5 seconds and exit if it is a successful login.


```
#!/bin/bash
echo "enter your username"
read username

If [ "$username" = "jake" ]
then
        echo 'success you are logged in now'
else
        echo 'sorry wrong username exiting in 5 seconds'
fi
```

---

### Post by spillin_dylan on 2012-10-21
```
#!/bin/bash
echo "enter your username"
read username

If [ "$username" = "jake" ]
then
        echo 'success you are logged in now'
else
        echo 'sorry wrong username exiting in 5 seconds'
        string="exiting"
        echo $string
fi
```

You could maybe try some other commands inside your **if** block.  Some examples might be the **sleep** command and **exit** command.  

Also, there is an excellent guide on bash scripting at [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

---

### Post by hookitup on 2012-10-21
spillin- this does not exit the session tho. it only says exiting, i would like it to actually exit the actual ssh session as if you where to type in the command exit and kills the ssh session. .
working via putty ssh FYI

so if im working via ssh and i type in
```
exit
```

it kills my ssh session i have open

same as if you type exit locally it will log you out or close the terminal depending on which init your in.

do you know how to achieve this ?

i know its something simple i just cant figure it out.

---

### Post by spillin_dylan on 2012-10-21
Yeah, I know.  My changes were just to show you an example that you can put code inside the if/then/else block.  You're on the right track, and I'm doing my best to help you learn the answer without just outright giving it to you.  

So you basically know what happens if you type 
```
$ echo "This is a string"
$ sleep 5
$ exit

```
at a bash command prompt.  What would you expect those same commands to do in a bash script?  HINT: All are bash commands in a bash environment.

---

### Post by hookitup on 2012-10-22
so in a terminal typing this would 

this is a string
waiting 5 seconds
exiting terminal



in a script when ran i see it do

this is a string
waiting 5 seconds (doesnt actually say anything just waits)
exit shell script. but not terminal.


so a little confused.

---

### Post by papibe on 2012-10-22
Hi hookitup.

When you call a script from the terminal, a new bash process is created. Any 'exit' instruction will affect only the new bash instance, not the current interactive one (this also applies when exporting variables).

In order for the commands to apply 'as they were run con the command line', you need to call the script with a special syntax.

Take a look at the 'source' or '.' in the bash's man page.

Hope that helps. Let us know how it goes.
Regards.

---

### Post by hookitup on 2012-10-22
thats what i am unsure about . i am asking how i would put that into the script.

---

### Post by hookitup on 2012-10-23
bump 




ANYBODY? :(

---

### Post by Vaphell on 2012-10-23
>  i am asking how i would put that into the script
verbatim

```
if ...
... 
else
        echo 'sorry wrong username exiting in 5 seconds'
        # wait 5s
        sleep 5
        # exit script
        exit
fi
```

---

### Post by hookitup on 2012-10-23
vaphell..

thanks for the reply but that is not what im looking for , this will only exit the script, as mentioned above- i want it to exit the session that is open, 

like close the terminal 
same effect if you type the command exit

i feel like i am being misunderstood.

---

### Post by pqwoerituytrueiwoq on 2012-10-23
you would probably need to use [wmctrl]("apt:wmctrl") for that
exit exits the script

---

### Post by hookitup on 2012-11-05
anyboy have a clue?

---

### Post by hookitup on 2012-11-05
I figured it out with this link
[http://www.cyberciti.biz/faq/linux-logout-user-howto/](http://www.cyberciti.biz/faq/linux-logout-user-howto/)
 
i just incoperated the command 
```
pkill -KILL -u username
```
into the else field and works great

---

