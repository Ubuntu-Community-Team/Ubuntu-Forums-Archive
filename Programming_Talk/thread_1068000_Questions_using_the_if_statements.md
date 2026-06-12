---
title: "Questions using the if statements"
date: 2009-02-12
forum: Programming Talk
---

### Post by Simplemind169 on 2009-02-12
i'm trying to write a program that allows the user to select a time frame and then displays all files modified in that range.
so far i have come up with
```
#!/bin/sh

#declare variable
var=0 
x=5

#user selects time frame
echo 'How far back would you like to go?'
select var in "Less than one day" "One day" "One Week" "One Month" ; do
	break
done

#set numerical equilivents
if [ var=='Less than one day' ] 
then
	x=0

elif [ var=='One day' ] 
then
	x=1

elif [ var=='One Week' ] 
then
	x=7

else [ var=='One Month' ] 
	x=30

fi

#display variable value
echo $x

#find and display the files within time frame
find $HOME -mtime -$x -print
```
no matter which selection i use it only does the first if statement and wont skip if not correct. i am using ubuntu 8.10 and under the bash shell as a reference

---

### Post by geirha on 2009-02-12
you are missing some spaces and the $ in the comparison.
```

if [ var=='Less than one day' ] 
# should be
if [ "$var" = "Less than one day" ]

```
And of course the same for the other [ commands

```
man [
```

---

### Post by Tek-E on 2009-02-12
Im not sure if this means anything or even pertains to your issue. but I though the correct use of an if statement was like this
```

if [ "$var" = "less then one day" ] ; then
     blah de blah de blah
     do this and that and the other thing
elif
and so on......

```
Im not trying to correct you or anything.  I am more asking as to wether it is more proper to use 
```

if [ blah = blah ] ; then

```
rather than the other way?

---

### Post by geirha on 2009-02-12
> **Tek-E said:**
> rather than the other way?

I don't quite follow. Could you give an example of the other way?

---

### Post by Tek-E on 2009-02-12
> **geirha said:**
> I don't quite follow. Could you give an example of the other way?
```

if [ blah = blah ]
then
    blah blah blah blah blah
fi

```

---

### Post by geirha on 2009-02-12
Ah. To bash, a semicolon is equivalent to a newline, so it's just a matter of style. Similar to that of C-programming; whether you prefer to do
```

if (!something) {
   do_something_else();
}

```
or
```
if (!something)
{
   do_something_else();
}
```

---

### Post by Tek-E on 2009-02-12
Ahhh I see. Thank you!

---

