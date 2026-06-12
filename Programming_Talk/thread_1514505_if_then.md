---
title: "if then"
date: 2010-06-21
forum: Programming Talk
---

### Post by Drenriza on 2010-06-21
How can you with the if then option in bash, get the script to look for a folder.

#1 if no (folder-name), create it.
#2 if (folder-name) already exist, do nothing

Thanks on advance.

---

### Post by squaregoldfish on 2010-06-21
I don't know the answer off the top of my head (I believe the -e and -d tests are what you're after), but I strongly suggest you download a copy of the Advanced Bash Scripting Guide. This is a fantastic document that contains everything you'll ever need to know about bash scripts, and it's not really that advanced :)

Steve.

---

### Post by Drenriza on 2010-06-21
is this a guide placed on the ubuntuforums.org?

---

### Post by simeon87 on 2010-06-21
It can be found [here](http://tldp.org/LDP/abs/html/).

---

### Post by Drenriza on 2010-06-21
I have a folder in a subfolder, that dosent native exist, called video2.

so if i want if then command to check this i need to do

```
if [ -e /video1/video2 ] ; then
    mkdir video2
else
    echo "video2 already exist"
fi
```

is this correct?

also i found the if then options here
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

---

### Post by Lampi on 2010-06-21
I recommend -d over -e

It will work with -e but -d is the better fit for a missing directory

---

### Post by Drenriza on 2010-06-21
Ye your correct Lampi. Thanks :)

---

### Post by Drenriza on 2010-06-21
I ask alot of questions but i also learn alot, so hope you guys will bare with me :)

i have a command as follows
```
command | awk '{print $3 " " $4 " " $5 " " $6 " " $7 }'
```

In the output, that the awk command gives me. I would like to be able to check for a specific text-string, lets say "xxx1" is the name of the text.

if xxx1 text-string already exist, do nothing.
if xxx1 text-string does not exist, ```
echo "xxx1 does not exist"
```
and then exit the script.

Is this possible? hope it make sense.

Since everything in ubuntu/linux/unix is treated as a file, i would guess that this is possible.
But the question is always how :)

---

### Post by Barrucadu on 2010-06-21
```
cmd=`command | awk '{print $3 " " $4 " " $5 " " $6 " " $7 }'`
str="whatever"

if echo $cmd | grep -q $str; then
    echo "$str found"
else
    echo "$str not found"
fi
```

---

### Post by Drenriza on 2010-06-21
so i would do

```
cmd=`command | awk '{print $3 " " $4 " " $5 " " $6 " " $7 }'`
str="xxd1"

if echo $cmd | grep -q $str; then
    echo "$xxd1 found"
else
    echo "$xxd1 not found"
fi
```

can you explane a little what the cmd, str does?

The command / commands are really good.
But if the text-string does not exist, how do i get the script to terminate but continue if it does exist.
I suspect this is done with an exit status?

---

### Post by Barrucadu on 2010-06-21
$cmd and $str are variables. And no, you'd do:

```
cmd=`command | awk '{print $3 " " $4 " " $5 " " $6 " " $7 }'`
str="xxd1"

if echo $cmd | grep -q $str; then
    echo "$str found"
else
    echo "$str not found"
fi
```

---

### Post by mainerror on 2010-06-21
To be a bit more precise. $cmd and $str are variables holding the command and the string to search for.

If you define a variable with this quote signs `` then it is treated as a command to run.

---

### Post by Drenriza on 2010-06-21
also with the

```
if [ -e /video1/video2 ] ; then
    mkdir video2
else
    echo "video2 already exist"
fi
```

With this command. if video2 does not exist and it then gets created. Can i then in the same "command set" do ln -s /video1/video2 /video2 with

so 

if 
video1/video2 exist, do nothing.
if
video1/video2 does not exist, create it.
if video1/video2 gets created do ln -s /video1/video2 /video2

can you just keep adding if then ??

---

### Post by Drenriza on 2010-06-21
> **Barrucadu said:**
> $cmd and $str are variables. And no, you'd do:

```
cmd=`command | awk '{print $3 " " $4 " " $5 " " $6 " " $7 }'`
str="xxd1"

if echo $cmd | grep -q $str; then
    echo "$str found"
else
    echo "$str not found"
fi
```

okey. What about
> **Drenriza said:**
> 
The command / commands are really good.
But if the text-string does not exist, how do i get the script to terminate but continue if it does exist.
I suspect this is done with an exit status?

---

### Post by mainerror on 2010-06-21
Sure you can do that but there is no need to.

You can simply create the link after the directory got created in the same if branch.

Alternatively you could set a variable to one or any other desired value after the directory got created and then check the variable if is has the desired value and do something upon that but this is not really needed as it would just add unnecessary complexity to the whole script.

---

### Post by Drenriza on 2010-06-21
> **mainerror said:**
> To be a bit more precise. $cmd and $str are variables holding the command and the string to search for.

If you define a variable with this quote signs `` then it is treated as a command to run.

im not sure i understand.
Maybe it will make sence after lunch and a break :p

---

### Post by Drenriza on 2010-06-21
> **mainerror said:**
> Sure you can do that but there is no need to.

You can simply create the link after the directory got created in the same if branch.

Alternatively you could set a variable to one or any other desired value after the directory got created and then check the variable if is has the desired value and do something upon that but this is not really needed as it would just add unnecessary complexity to the whole script.

but if you wanted to do it with
> **Drenriza said:**
> 
if 
video1/video2 exist, do nothing.
if
video1/video2 does not exist, create it.
if video1/video2 gets created do ln -s /video1/video2 /video2


what would it then look like?

---

### Post by mainerror on 2010-06-21
This would be option one.

```

dir="video1/video2"

if [ -d "$dir" ]; then
    #DO NOTHING
else
    echo "Directory not found."
    mkdir video2
    ln -s /video1/video2 /video2
fi
```

Option two would be this.

```

dir="video1/video2"
state=0

if [ -d "$dir" ]; then
    #DO NOTHING
else
    echo "Directory not found."
    mkdir video2
    state=1
fi

if [ $state -eq 1 ]
    echo "Creating link"
    ln -s /video1/video2 /video2
fi
```

But I'd rather go with option one.

---

### Post by Drenriza on 2010-06-21
mainerror, just a thought.

But cant you also do
```
if [ -d /video1/video2 ] ; then
    mkdir video2
    ln -s /video1/video2 /video2
else
    echo "video2 already exist"
fi
```

?

---

### Post by mainerror on 2010-06-21
Of course you can. Using variables is better than just hardcode stuff in your scripts thats why I used a variable for the directory.

---

### Post by Drenriza on 2010-06-21
Isee.

Anyone who can answer #14 or point me in the right direction?

So far thanks for all guys, its super really help full.

---

### Post by mainerror on 2010-06-21
Could you reformulate your question in #14 a bit? I do not really understand what exactly you want to check for.

---

### Post by Lampi on 2010-06-21
> **Drenriza said:**
> Isee.
Anyone who can answer #14 or point me in the right direction?

put 'exit 1' **below** the line with false condidion (echo "$str not found")

exit 0 = exit status is 0 = normal termination of bash with a true condition
exit 1 = exit status is 1 = error termination of bash with a false condition

You can then check the exit status with 'echo $?' this will only offer exit status of the last command that has been run before you forced exit

---

### Post by Drenriza on 2010-06-21
```
cmd=`command | awk '{print $3 " " $4 " " $5 " " $6 " " $7 }'`
str="xxd1"

if echo $cmd | grep -q $str; then
    echo "$str found"
else
    echo "$str not found"
fi
```

Here in the code i look for the text-string xxd1.

If i find xxd1 i want the script to continue as normal. Executing the remaining commands. If the xxd1 text-string does not exist. I would like the script to stop. And giving an ```
echo "the script stopped because xxd1 does not exist"
``` or something like that.

hope this makes sence

---

### Post by Drenriza on 2010-06-21
So should it look like this lampi

```
cmd=`command | awk '{print $3 " " $4 " " $5 " " $6 " " $7 }'`
str="xxd1"

if echo $cmd | grep -q $str; then
    echo "$str xxd1 found"
else
    echo "$str xxd1 not found"
    echo "bash will close because ..........."
    exit 1
fi
```

??

---

### Post by Lampi on 2010-06-21
> **Drenriza said:**
> So should it look like this lampi
I don't know what str="xxd1" does, so no, I can't tell you this will work, but I can confirm it will exit with 1 in the else condition ;)

Edit: ah now I got it - you grep this through the $cmd output ...

so yeah, you might have a chance it will work, grep -q will exit as well with status 0 in the if condition, you get status 1 in the else condition

so yeah, this looks good at second thought :)

---

### Post by Drenriza on 2010-06-21
xxd1 is not a command. It is simply clear text.

---

### Post by Drenriza on 2010-06-21
anyways thanks for all guys.

It has been a huge help.

---

