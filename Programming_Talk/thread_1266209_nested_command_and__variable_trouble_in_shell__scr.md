---
title: "nested command and  variable trouble in shell  script"
date: 2009-09-14
forum: Programming Talk
---

### Post by Shpongle on 2009-09-14
Hey , Iv only started scripting and im having a bit of trouble with variables and using nested command in scripts ,  my code and the output is below , Id be grateful if someone could point me in the right direction as to what im doing wrong, thanks


```

#
# Script to test my knowledge about variables

number=10
echo $number

name=Dill
echo $name

echo "sum of 6 + 3 = '$expr 6 + 3'"

x=20
y=5
echo "x / y =  '$expr x / y'"

z='$expr x / y'

echo "z is $z"
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~   
```

im not getting the desired output


im getting this instead


10
Dill
sum of 6 + 3 = ' 6 + 3'
x / y =  ' x / y'
z is $expr x / y

---

### Post by geirha on 2009-09-14
The shell can do integer arithmetics by itself, no need to use the external expr-command.

```

a=6 b=3
echo "Sum of $a + $b = $((a+b))"
```

I recommend this guide on bash scripting: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by Shpongle on 2009-09-14
hey thanks man , that helped a lot , also that guide looks a lot better than the one i was using [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

---

### Post by Keith Hedger on 2009-09-14
I think you are getting the single quote "'" mixed up with the back quote "`" single quotes just protect whats between them back quotes are used to run a command ie:```
x='ls'
echo $x
``` gives the output "ls"
whereas ```
x=`ls`
echo $x
``` gives a listing of the current dir, to avoid confusion and if you are scripting for bash try using ```
x=$(ls)
echo $x
``` its less prone to mistakes

---

### Post by DaithiF on 2009-09-14
also, although no need to call the expr command for arithmetic, as previous poster said, just to say that the way you are trying to call an external command is incorrect, since it may help you in your next steps.

To run a command from a bash script, there are 2 ways that you can choose from.  (The 2nd form is slightly preferable since it allows commands to be nested.)
1. enclose the command in backticks, ie. the ` character, so: `command`
```
echo `expr 6 + 3`

```In your post you were using normal single quotes, these are not the same as backticks (key to the left of '1' on a uk/irish keyboard)

2. use $(command)
```
echo $(expr 6 + 3)

```

your version:
'$expr 6 + 3' looks like an amalgamation of those methods, which won't work of course :)

---

### Post by Keith Hedger on 2009-09-14
P.S.
Try the abs-guide (advanced bash scripting guide) its in the repos its excellent.

---

### Post by Shpongle on 2009-09-14
> **Keith Hedger said:**
> I think you are getting the single quote "'" mixed up with the back quote "`" single quotes just protect whats between them back quotes are used to run a command ie:```
x='ls'
echo $x
``` gives the output "ls"
whereas ```
x=`ls`
echo $x
``` gives a listing of the current dir, to avoid confusion and if you are scripting for bash try using ```
x=$(ls)
echo $x
``` its less prone to mistakes

thanks all for the help and advice i really appreciate it , yea you were right i was mixing them up  , yea il get into a habit of using the brackets!

---

