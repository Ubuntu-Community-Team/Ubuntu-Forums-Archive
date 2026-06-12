---
title: "trap  command not working in ubuntu 9.04"
date: 2009-07-24
forum: Programming Talk
---

### Post by H.om on 2009-07-24
I have bash version 3.2 installed.I tried the following code.
[B]
#!/bin/bash
trap 'rm -f ~/programmming/tes' INT
 echo "creating file ~/programmming/tes"
 echo "om" > ~/programming/tes
 echo "Press ctrl + c to interrupt"

while [ -e  ~/programming/tes ]
do
echo "file exists"
done
 echo "file no longer exists"
 trap INT
 echo creating file ~/programmming/tes
 echo "om" > ~/programmming/tes
 echo &#8220;press interrupt (control-C) to interrupt ....&#8221;
 while [ -e ~/programmming/tes ]; do
    echo File exists
     sleep
 done
[/B]

When I press ctrl-c
nothing changes. First while loop continues to execute.
Any help will be greatly appreciated.............

---

### Post by dwhitney67 on 2009-07-24
Fundamentally, you had the right concepts, however your code was buggy, and even contained some weird characters before the second while-loop.

Here's the corrected code, with some extra white-space to make it more readable:
```

#!/bin/bash

FILE=~/tes
CMD="rm -f $FILE"

trap '$CMD' INT

echo "creating file $FILE"
echo "one" > $FILE

echo "Press ctrl + c to interrupt"

while [ -e $FILE ]
do
        echo "1. File Exists"
        sleep 1
done

echo "file no longer exists"

trap - INT

echo "creating file $FILE again"

echo "two" > $FILE
echo "press interrupt (control-C) to interrupt ...."

while [ -e $FILE ]
do
        echo "2. File Exists"
        sleep 1
done

```

---

### Post by dwhitney67 on 2009-07-24
I meant to add that I tested the shell script using my Ubuntu 9.04 system.

Perhaps you do not have bash installed on your system, and hence the reason why the code did not work for you.  When Ubuntu is installed from the "box", it contains a shell called **dash**, which in turn bash is linked to it, thus giving the user the illusion they have bash installed.

Dash is the mini-me of bash.  If you require the full-version of bash, go to Synaptic Package Manager to install it.

---

### Post by H.om on 2009-07-24
Hey thanks  for debugging,dwhitney67.
but I tried after debugging and is still not working.
I copied and pasted ur code and still no change except that the first while loop statement "1. File Exists" is displayed every seccond.
would u please post me a very simple script that ur version of linux can run implementing trap command

---

### Post by H.om on 2009-07-24
> **dwhitney67 said:**
> I meant to add that I tested the shell script using my Ubuntu 9.04 system.

Perhaps you do not have bash installed on your system, and hence the reason why the code did not work for you.  When Ubuntu is installed from the "box", it contains a shell called **dash**, which in turn bash is linked to it, thus giving the user the illusion they have bash installed.

Dash is the mini-me of bash.  If you require the full-version of bash, go to Synaptic Package Manager to install it.

I just checked in my Synaptic Package Manager there is Bash installed already but thanks for your reply.Any thing u want to add?

---

### Post by dwhitney67 on 2009-07-24
> **H.om said:**
> Hey thanks  for debugging,dwhitney67.
but I tried after debugging and is still not working.

I don't know what to say?

> **H.om said:**
> 
would u please post me a very simple script that ur version of linux can run implementing trap command

I tested with the (modified) script I [posted]("http://ubuntuforums.org/showpost.php?p=7669461&postcount=2") earlier.

Here's even a simpler script that does something similar:
```

#!/bin/bash

FILE=~/foo.txt
CMD="rm -f $FILE"

trap '$CMD' INT

echo "Press ctrl + c to interrupt"

touch $FILE
while [ -f $FILE ]
do
	sleep 1
	echo "I'm waiting for a ctrl-c..."
done

```

To run it:
```

bash script.bash

```
or you can make it an executable:
```

chmod +x script.bash
./script.bash

```

---

### Post by stroyan on 2009-07-24
Just checking obvious assumptions-
[LIST]
[*]Does "stty -a" output include "intr = ^C;" ?
[*]Does "~/programming/tes" exist as a regular file.
[*]Does your account have permission to remove that file?
[/LIST]

---

### Post by H.om on 2009-07-25
> **dwhitney67 said:**
> I don't know what to say?



I tested with the (modified) script I [posted]("http://ubuntuforums.org/showpost.php?p=7669461&postcount=2") earlier.

Here's even a simpler script that does something similar:
```

#!/bin/bash

FILE=~/foo.txt
CMD="rm -f $FILE"

trap '$CMD' INT

echo "Press ctrl + c to interrupt"

touch $FILE
while [ -f $FILE ]
do
	sleep 1
	echo "I'm waiting for a ctrl-c..."
done

```

To run it:
```

bash script.bash

```
or you can make it an executable:
```

chmod +x script.bash
./script.bash

```
Thanks again for posting that easy script.But I have to say it still not trapped .The loop continues endlessly even after pressing ctrl +c.Now I am sure there is not problem with the code but some installation.But I am not sure what it is?

---

### Post by H.om on 2009-07-25
> **stroyan said:**
> Just checking obvious assumptions-
[LIST]
[*]Does "stty -a" output include "intr = ^C;" ?
[*]Does "~/programming/tes" exist as a regular file.
[*]Does your account have permission to remove that file?
[/LIST]
**1.** I dont know what *stty -a* does but it includes *intr=^c*.
**2.** yes,~/programming/tes exist with "om" in it.
**3.** yes I have remove permission to the file.......
**ls -l ~/programming/tes** prints
*-rw-r--r-- 1 hariom hariom 7 2009-07-24 16:35 /home/hariom/programming/tes*

---

### Post by dwhitney67 on 2009-07-25
And you are pressing the 'ctrl' key, and while holding it down, pressing the 'c' key?

I just want to make sure you are not pressing the '+' key.

---

### Post by H.om on 2009-07-25
> **dwhitney67 said:**
> And you are pressing the 'ctrl' key, and while holding it down, pressing the 'c' key?

I just want to make sure you are not pressing the '+' key.
Ofcourse i am pressing c while ctrl is holded down.

---

### Post by H.om on 2009-07-25
Ofcourse I am pressing 'c' while holding 'ctrl' key.Thanks for ur reply.I googled a lot ,but no one has this strange problem.

---

### Post by dwhitney67 on 2009-07-25
Try this experiment....

First, in one terminal, run your script.

Then, in another terminal, attempt to terminate it manually with a SIGINT signal.

For instance, if you named your script "traptest.bash", after you have started the script, execute the following command (which btw, might be best to copy/paste):
```

kill -s SIGINT `ps -ef | grep -m 1 traptest | cut -d ' ' -f3`

```
A SIGINT and a ctrl-c yield the same effect... an interrupt signal.

P.S.  Before terminating the script, ensure that the "bread crumb" file is created, and then after the signal is delivered, that the file is removed.

---

### Post by H.om on 2009-07-26
> **dwhitney67 said:**
> Try this experiment....

First, in one terminal, run your script.

Then, in another terminal, attempt to terminate it manually with a SIGINT signal.

For instance, if you named your script "traptest.bash", after you have started the script, execute the following command (which btw, might be best to copy/paste):
```

kill -s SIGINT `ps -ef | grep -m 1 traptest | cut -d ' ' -f3`

```
A SIGINT and a ctrl-c yield the same effect... an interrupt signal.

P.S.  Before terminating the script, ensure that the "bread crumb" file is created, and then after the signal is delivered, that the file is removed.
hey thanks.....
I copy pasted ur command but it gave usage error
*kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]*
But I tried 
*kill -s SIGINT 4834 *
4834 was the PID of that script process.
Script trapped the signal and it was interrupted.It worked but why it's not working with ctrl + c .
I tried the following script (corrected by u)


[I]

#!/bin/bash

FILE=~/tes
CMD="rm -f $FILE"

trap '$CMD' INT

echo "creating file $FILE"
echo "one" > $FILE

echo "Press ctrl + c to interrupt"

while [ -e $FILE ]
do
        echo "1. File Exists"
        sleep 1
done

echo "file no longer exists"

trap - INT

echo "creating file $FILE again"

echo "two" > $FILE
echo "press interrupt (control-C) to interrupt ...."

while [ -e $FILE ]
do
        echo "2. File Exists"
        sleep 1
done




[/I]
I checked that the file tes initially existed containing 'one' and after interruption it is overwritten by 'two'.Everything worked just fine printing 
*2. File Exists *         in while  loop

But second time when I issued the command it was not trapped because the loop continues to execute.and file 'tes' still exists.Now whats this?

---

### Post by dwhitney67 on 2009-07-26
Per your final question, I thought that this is what you wanted?

I disabled the monitoring of the (trap) interrupt with this statement:
```

trap - INT

```
If after this statement is issued, and you once again repeat the "kill -s SIGINT", the script will abort most ungracefully.  The test file that is created in your home directory and contains the text "two" will still remain behind.

If your intent is to continue monitoring for the interrupt, then remove that statement shown above.

---

### Post by H.om on 2009-07-26
> **dwhitney67 said:**
> Per your final question, I thought that this is what you wanted?

I disabled the monitoring of the (trap) interrupt with this statement:
```

trap - INT

```
If after this statement is issued, and you once again repeat the "kill -s SIGINT", the script will abort most ungracefully.  The test file that is created in your home directory and contains the text "two" will still remain behind.

If your intent is to continue monitoring for the interrupt, then remove that statement shown above.
Hey I am very very thankful to u. 
I got you.But I still dont understand why ctrl+c is not working if it does the same as sending SIGINT signal.

---

### Post by lswb on 2009-07-26
> **dwhitney67 said:**
> I meant to add that I tested the shell script using my Ubuntu 9.04 system.

Perhaps you do not have bash installed on your system, and hence the reason why the code did not work for you.  When Ubuntu is installed from the "box", it contains a shell called **dash**, which in turn bash is linked to it, thus giving the user the illusion they have bash installed.

Dash is the mini-me of bash.  If you require the full-version of bash, go to Synaptic Package Manager to install it.

This is not quite correct information. default ubuntu (I believe since 6.10 or 7.04) has both dash and bash installed. /bin/sh is linked to dash so that scripts using #!/bin/sh will use dash and hopefully execute faster and more efficiently. An interactive shell (like a terminal window or console) will always use bash, not dash. There are some things bash will do that dash will not, so if your script requires bash-specific features, use "#!/bin/bash" at the start of the script instead of "#!/bin/sh"

---

### Post by dwhitney67 on 2009-07-26
> **lswb said:**
> This is not quite correct information. default ubuntu (I believe since 6.10 or 7.04) has both dash and bash installed. /bin/sh is linked to dash so that scripts using #!/bin/sh will use dash and hopefully execute faster and more efficiently. An interactive shell (like a terminal window or console) will always use bash, not dash. There are some things bash will do that dash will not, so if your script requires bash-specific features, use "#!/bin/bash" at the start of the script instead of "#!/bin/sh"

How come when Ubuntu is installed out of the "box", that a command similar to the following does not work from the command line?
```

cp somefile{,.bak}

```
I started using Ubuntu a couple of years ago; maybe with the new releases it works.

---

### Post by lswb on 2009-07-26
> **dwhitney67 said:**
> How come when Ubuntu is installed out of the "box", that a command similar to the following does not work from the command line?
```

cp somefile{,.bak}

```
I started using Ubuntu a couple of years ago; maybe with the new releases it works.

That command works as expected for me. Maybe check your /etc/passwd and make sure your shell is set to bash?

---

