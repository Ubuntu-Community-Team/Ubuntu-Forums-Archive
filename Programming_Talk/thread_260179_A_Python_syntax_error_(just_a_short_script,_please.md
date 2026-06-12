---
title: "A Python syntax error (just a short script, please help)"
date: 2006-09-18
forum: Programming Talk
---

### Post by æþeling on 2006-09-18
Now, I'm almost 100% sure there's no syntax error in here, yet there appears to be. Could someone more experienced please show me where it is?

```

#This is a simple program that reads 10 numbers and prints the highest one.
#
i=0 #This is the initial amount of numbers
m=0 #This is the initial highest number
x=0 #This one of the user-defined numbers
while i<10: #Begin loop, repeat until there's ten numbers
	x=input("Enter a number:") #Number input
	i=i+1 #i is increased by 1 each loop, so the loop is repeated 10 times
	if x>m: #If a new number is higher than the one entered before, it becomes the biggest one
		m=x
print "The highest number is", m #The result is printed

```

And I get this error:

```

thejollybloke@pub:~$ ./pythontest1.py
./pythontest1.py: line 7: syntax error near unexpected token `('
./pythontest1.py: line 7: `   x=input("Enter a number:") #Number input'
thejollybloke@pub:~$

```

---

### Post by nereid on 2006-09-18
This testing code works without a problem. Maybe there is an error with the comments

```

i=0
m=0
x=0
while i<10:
        x = input ("Enter a number: ")
        i+=1
        if x>m:
                m=x

print "The highest number is ", m

```

---

### Post by æþeling on 2006-09-18
Yeah, it works fine in an interactive shell(even with the comments), but it doesn't work if I save it as a script and make it executable with chmod, than ./ it.

---

### Post by pallaire on 2006-09-18
Works fine ... I am sure that you have a tab/space indentation problem in your file (that you wouldnt have in the console since it indent for you).

In python the indentation must always be of the same type, if you start with 4 spaces, you cant use a TAB somewhere !!!

It is the source of my errors 95% of the time.

Good luck.

---

### Post by æþeling on 2006-09-18
I've just checked the intendation, and it's all with tab.

---

### Post by pallaire on 2006-09-18
I have done a Cut and Past of you code (1st post) into a file and tested it with python 2.4.1 on windows xp (hey, that what I use at work). It works fine ... but you have to enter your 10 values, if you give it an empty value (pressing enter without number) it will crash.

---

### Post by pallaire on 2006-09-18
Try to start it this way : 

python ./test.py

instead of just :

./test.py

---

### Post by æþeling on 2006-09-18
Problem solved.
The thing was, I forgot to add
```

#! /usr/bin/python

```

As the first line.

---

### Post by altogrande on 2009-01-26
any one please help

> 
# /bin/bash

if [ $# -ne 2 ]; then

        print "Usage is: $0 list password"
        exit 1
else
        list=$1
        passwd=$2
fi

#---get the list members

list_members $list &gt; /tmp/$list.members

#---change the user passwords

for member in cat /tmp/$list.members

do
       print "==== $member"
       withlist -l -r changeuserpw $list $member $passwd

done

rm /tmp/$list.members[/qoute]



---

### Post by altogrande on 2009-01-26
and the error is:

 

command not foundy: line 2:
'in/change.userpw.py: line 19: syntax error near unexpected token `
'in/change.userpw.py: line 19: `

---

### Post by .Maleficus. on 2009-01-26
Yikes, holy thread necro.

This would be better put in its own thread, but anyways...  That isn't Python, that's Bash.  I don't do Bash so I can't help but maybe someone else here can decrypt your posts.

---

### Post by eightmillion on 2009-01-26
> **altogrande said:**
> and the error is:
command not foundy: line 2:
'in/change.userpw.py: line 19: syntax error near unexpected token `
'in/change.userpw.py: line 19: `

The reason you're getting that error is because "print" isn't a bash function. You need to use "echo" or "printf". However, even fixing that isn't going to make your script work.  What is "list_members $list &gt; /tmp/$list.members" supposed to do? Is list_members a program or a function of this script? What is "withlist"? 

> for member in cat /tmp/$list.members

This needs to be "**for member in `cat /tmp/$list.members`**" or "**for member in $(cat /tmp/$list.members)**" to even have a chance of doing anything.

I'd recommend doing some reading on bash scripting before trying to go any further.

---

### Post by altogrande on 2009-01-26
thanks, yeah you're right i should read more of bash

thanks again

---

### Post by slavik on 2009-01-26
Thread closed. Original OP can't read this anyway. Please don't reuse threads.

---

