---
title: "simple bash script to write to a file"
date: 2008-04-22
forum: Programming Talk
---

### Post by newsman on 2008-04-22
ha i need help.  I have tried lots of different ways but the most successful (and yet not a success) is as follows

```

#!/bin/bash
#A script that takes two arguments, a line of text and a filename
#and adds to the file of filename with the line of text at the bigenning.

if [$# -eq 2]
then if [ -f $2 ] 
	then vi +I%s'$1'+'wq' $2;
	fi
else
	echo "usage script text filname";
fi
exit 0

```

The following is output:


newsman@newsman-laptop:~$sh firstline3 "hello my name is newsman" textlines
firstline3: 11: [2: not found
usage script text filname
newsman@newsman-laptop:~$ sh firstline3
firstline3: 11: [0: not found
usage script text filname

---

### Post by Tuna-Fish on 2008-04-22
The basics are:
echo $2 | cat - $1 > temp
mv temp $1

although you need really robust naming for temp, like:

TEMPNAME="/tmp/`whoami``date +%s%N`myshellscript"
echo $2 | cat - $1 > $TEMPNAME
mv $TEMPNAME $1

Is it ugly? oh yes. But it works. Also, wrap in proper tests for the existence of file etc.

---

### Post by ghostdog74 on 2008-04-22
> **newsman said:**
> ha i need help.  I have tried lots of different ways but the most successful (and yet not a success) is as follows

```

#!/bin/bash
#A script that takes two arguments, a line of text and a filename
#and adds to the file of filename with the line of text at the bigenning.

if [$# -eq 2]
then if [ -f $2 ] 
	then vi +I%s'$1'+'wq' $2;
	fi
else
	echo "usage script text filname";
fi
exit 0

```


```

....
then
    sed -i "1i $1" file
....

```

---

### Post by newsman on 2008-04-23
cannot use sed or temporary files (> operator). not fair la

on second check, i am allowed to use > operator and temporary files

---

### Post by newsman on 2008-04-23
I completed this exercise, next one is to insert line at the middle.  I know i can use wc -l command to find out the lines, but it also displays the filename.  Is there a better way without using sed or awk? Thanks.  Following that is an exercise to append a file without using temporary files (the only time when I am not allowed using temporary files), display user permissions of certain file and display processes.  I think apart from the not using temp file clause the rest should be straight forward.

---

### Post by newsman on 2008-04-23
I completed the first exercise, ( i managed to complete it using call to vim). 

The second ex is to insert line at the middle of the file is proving too difficult.

The third one i managed to complete somehow (i can't believe i did that without any help! yippeee but i used a call to vim with script again.) (the exercise was to gather env variable and grep them with username and format them so that instead of line number: ..... you get line number)


the fourth i have attempted a thousand million times,  I am now confused with BASH and variable assingment.  Particularly assigning strings .  The point is to check file ownership and instead of printing  rw..... string format into columns Read Write Execute followed by three rows for Owner, Group and Everyone respectively and have yes or no for each.

Please let me know of any good tutorial or point to me what is going on in this code which makes it not work.  Thanks

```
#!/bin/bash
STR="Hello World"
touch output01;
ls -l temp01 > output01;
cat output01 > $STR;
echo $STR;
```

I have tried to use pipe operator instead of > and i get error.

Even if i get read of dollar sign, in cat > $STR statement, still no assignment occurs.


The fifth is similar to this i guess i have to collect process and produce a similar formatted output.

These exercises really hit home the power of awk and sed right.  Too bad I can't use them for these exercises.  Another thing is on formatting output.  Any pointer would be appreciated.

---

### Post by RIchard James13 on 2008-04-23
> **newsman said:**
> Please let me know of any good tutorial or point to me what is going on in this code which makes it not work.  Thanks

At the [Linux Documentation Project]("http://tldp.org/") is the [Advanced BASH Scripting Guide]("http://tldp.org/LDP/abs/html/index.html")

Although not a tutorial it is a good reference especially if you look at the examples.

```
cat output01 > $STR;
```
This line won't work because you can't redirect straight to a variable.
[look on the bottom of this page]("http://tldp.org/LDP/abs/html/varassignment.html") for some ways to do it.

---

### Post by newsman on 2008-04-24
howcome this does not work in the script but works in the prompt?

$ EXCLAIM=cowabunga
$ echo ${EXCLAIM:0:3}
cow
$ echo ${EXCLAIM:3:7}
abunga

If I were to have these echo lines in script i would get:
Syntax error: Bad substitution

---

### Post by newsman on 2008-04-28
Is there another way to look at cells in a row of text (delimited by tab or : or something)?

---

### Post by newsman on 2008-04-28
oh man just solved another piece of the puzzle..i will try to get a webpage to document all my coding.. but not before the work is done... but now i have a variable $STR with following user1 user2 user3 user4 user5  (space delimited list)..how can i turn this into a an array in bash

---

### Post by newsman on 2008-04-28
I have file

with random names seperated by space, duplicate names are side by side (sorted out). i want to pass them to "ps -u" function one by one..

so far i have 
```
#!/bin/bash
#STR=$(users) 
#VAR=$(finger | wc -l)


#STR2=${STR#*" "}
VAR2=$(cat users);

#echo output of users $STR
#VAR=$(($VAR-1))
echo $VAR
#echo $STR2
echo $VAR2
NUM=10;

VARl3=${VAR2##*" "} #get the last name

while [$NUM -gt 0]
do
  echo $VARl3 # perform ps

  while [$VARn -ne $VARc] #continue shortening the string until unique name found
  do
  VARn=${VAR2%" "*} #new string
  Number=$(($UM-1))
  #echo $VAR4
  VARc=${VARm##*" "} #get second last name
  done
  VARl3=$VARc
done

```
and output



```

john.smith john.smith william.shakespear william.shakespear whocares.whoevever
userprocesses: 30: [10: not found

```

---

### Post by mssever on 2008-04-28
> **newsman said:**
> ```
while [$NUM -gt 0]
```

You need spaces around [ and ]. Also, if you use [[ ]] instead of [ ], you'll find that it supports a few more options and is less likely to break in weird ways.

---

### Post by newsman on 2008-04-30
I am getting errors when i try to use functions in bash

```
#!/bin/bash

VAR=$(cat users)
NUM=10

function getname(){
LAST=${VAR##*" "}
VAR=${VAR%" "*} #new string
NUM=$(($NUM-1)) 
}

function printout(){
echo $LAST
echo $NUM
echo new string $VAR

}

while [ $NUM -gt 0 ]
do
$(getname())
$(printout())


done
```
output
```
userprocesses4: 6: Syntax error: "(" unexpected

```

even if i had empty functions i am getting this error in BASH?

I am also having trouble testing for string equality
```

if [ test $LAST=$LASTl ]
then
{
VAR=${VAR%" "*} #new string
NUM=$(($NUM-1))
LAST=${VAR##*" "}
}
else
{
echo $LAST
VAR=${VAR%" "*} #new string
echo new string $VAR
NUM=$(($NUM-1)) #decrement number of users
LASTl=$LAST
LAST=${VAR##*" "}
echo $NUM
}
fi

```
results in 

```
[: 33: adul.latif1=abdul.latif1: unexpected operator

```

---

### Post by howlingmadhowie on 2008-04-30
here a simple function to get you started:

```

#!/bin/bash

function myfunc {
  echo "hello world!"
  echo $1
}

myfunc 3

```

---

### Post by mssever on 2008-04-30
> **newsman said:**
> I am getting errors when i try to use functions in bash
Either of the following will work, but they can't be combined: ```
function foo {
  #do stuff
}

bar() {
  #do more stuff
}
```I prefer the first form because it doesn't imply that you can place arguments inside the parentheses (since you can't).

EDIT:
> ```
if [ test $LAST=$LASTl ]
```Try ```
if [[ "$LAST" = "$LASTl" ]]
```[ and test mean the same thing; don't use both. [[ is safer than [. Make it a habit to always enclose your variables in double quotes. It will save a lot of headaches later.

---

### Post by newsman on 2008-04-30
I get an error on that as well
```

myfunc1: 3: function: not found
hello world!

myfunc1: 6: Syntax error: "}" unexpected

```

---

### Post by newsman on 2008-04-30
I will do half an hour more brain squeezing before i get back....

---

### Post by howlingmadhowie on 2008-04-30
> **newsman said:**
> I get an error on that as well
```

myfunc1: 3: function: not found
hello world!

myfunc1: 6: Syntax error: "}" unexpected

```

are you sure you entered my example correctly? it looks okay to me.

---

### Post by newsman on 2008-04-30
my idea was to use recursive functioning to test for uniqueness (until unique name found call the function to shorten string of names and get new names and check)

but i managed to complete without functions (i am a big fan of the KISS principle although I think i better practice this before progressing in my application)


```

#!/bin/bash

VAR=$(cat users)
echo $VAR
NUM=11

LAST=${VAR##*" "}
NUM=$(($NUM-1))
#VAR=${VAR%" "*} #new string


echo $NUM
LASTl="anything"

while [ $NUM -gt 0 ]
do
if [ "$LAST" = "$LASTl" ]
then
{
VAR=${VAR%" "*} #new string
NUM=$(($NUM-1))
echo $NUM
LAST=${VAR##*" "}
}
else
{
echo $LAST
VAR=${VAR%" "*} #new string
echo new string $VAR
NUM=$(($NUM-1)) #decrement number of users
LASTl=$LAST
LAST=${VAR##*" "}
echo $NUM
}
fi

done

```

thanks a bunch guys

Also when i place [[ instead of [ in if [ "$LAST" = $LASTl" ] i get an error 
```
userprocesses5: 37: [[: not found
```

now i have to submit in little under three hours and hopefully the evaluators wll accept my work, so happy, if you were in bradford i could treat you.

my function i typed
```
#!/bin/bash

function myfunc {
echo "hello world!"
echo $1
}

myfunc 3

``` I just copied and pasted just now to make sure..got the same error

---

### Post by mssever on 2008-04-30
Dunno if it's too late, but here are a couple more tips:

[LIST=1]
[*]For recursive functions, be absolutely sure to declare all variables as local. Otherwise, Bad Things will happen. E.g.: ```
function adder {
  local current="$1"
  local max="$2"
  [[ "$current" -ge "$max" ]] && return current
  (($current++))
  adder "$current" "$max"
}
echo "$(adder 0 10)"
```
[*][[ is a Bash extension. If you're not calling bash (or if you're calling Bash, but as sh), then it might not work. In particular, /bin/sh actually calls dash, not bash on Ubuntu. [[ doesn't work in dash.
[*]If you must use [, consider that an empty string will cause errors, even with quotes. Compare strings with something added, e.g., ```
[ "x$foo" = "x$bar" ] && echo "Success"
```
[/LIST]

---

### Post by newsman on 2008-04-30
actually i do have time but, i have few loose ends to tie up.. i have to answers questions on use of vi...use date function to append to file and submit that file and this particular example... i have to get VAR initially to read from output of users command  and num to read from finger | wc -l (and decrement initial value by one since finger results in one extra header line) to find uers and instead of echoing names, i have to run ps -u $LAST command on them...i will probably spend an hour more on this and then try to tie up other loose ends

---

### Post by howlingmadhowie on 2008-04-30
> **newsman said:**
> 
my function i typed
```
#!/bin/bash

function myfunc {
echo "hello world!"
echo $1
}

myfunc 3

``` I just copied and pasted just now to make sure..got the same error

that's weird. it works fine for me. let me think...

---

### Post by mssever on 2008-04-30
> **howlingmadhowie said:**
> that's weird. it works fine for me. let me think...

function foo is a Bashism. The portable way is foo(). This and the OP's trouble with [[ (another Bashism) suggests to me that he/she isn't actually using Bash.

---

### Post by newsman on 2008-04-30
is there any way to confirm but it looks like the case..

i did a search on yahoo "bash or dash" and found this in [http://ubuntuforums.org/archive/index.php/t-221769.html](http://ubuntuforums.org/archive/index.php/t-221769.html)

i thought this means both bash and dash are available in and i need to have the shebang line correct to call correct shell but it appears to not be the case??

---

### Post by mssever on 2008-04-30
> **newsman said:**
> is there any way to confirm but it looks like the case..

i did a search on yahoo "bash or dash" and found this in [http://ubuntuforums.org/archive/index.php/t-221769.html](http://ubuntuforums.org/archive/index.php/t-221769.html)

i thought this means both bash and dash are available in and i need to have the shebang line correct to call correct shell but it appears to not be the case??

If your shebang line calls bash, then I can't imagine what your problem is. Perhaps you could post the current version of your code so I can try it here.

---

### Post by newsman on 2008-05-01
I think bash shebang might be a symbolic link to dash...lol... I don't want to investigate it just now (let the weekend start in UK first)

I submitted the required code.  They also said its not working on their servers... They have given me another deadline (three working days).  I want to try it myself (cos maybe it is just stupid me) first and that is most productive and beneficial for myself.. I might just focus on this for Friday at least.

Besides.  I have another interview and I have been told that they will take a test on Bash and SQL so I will use this weekend to learn more about them. And my C is also much to be desired.

---

### Post by newsman on 2008-05-01
eek I had not completed one requirement...

how can we get real name from login name

id -r login.name is giving me: error:
id: cannnot only print names or real IDs in default format

is there a way to select the second column 1st row output of finger login.name
Because this gives:
Login:login.name               Name: Login Name
Directory:don't care           Shell: don't care
Rest info: don't care

without using sed or awk

---

### Post by newsman on 2008-05-01
Some how i want this work ...

I got the first part to work, but i want to input into last part to get rid of everything before the last space ( i can check the exact regular expression to use later) but how do i get this to syntactically work....

Another way to do it is input finger -l -p -m $USER | grep Name  into a variable.. but i get scriptname: 5: =Login:: not found


~$ finger -l -p -m $USER | grep Name | ${%%" "*}
bash: ${%%" "*}: bad substitution
~$ finger -l -p -m $USER | grep Name | ${$1%%*" "}
bash: ${$1%%*" "}: bad substitution
~$ finger -l -p -m $USER | grep Name | ${$%%*" "}
bash: 15905: command not found
~$

Another idea i had was to use this
finger -l -p -m $USER | grep -o Name:\W
but results in nothing.

if i do finger -l -p -m $USER | grep -o Name:
at least the result is

Name:

---

### Post by newsman on 2008-05-02
After several brainwacking minutes (almost half hour from my edit..oh gosh my concentration) I get:

for:

finger -l -p -m $USER | grep -o Name:" ".*

result:
Name: Login Name

But i would rather get rid of name part but i will submit it early and get some feedback before the deadline...then i can concentrate a bit on sql and bash dash mystery on the weekend

---

### Post by newsman on 2008-05-05
all the work got accepted except one

The following takes a file, finds all occurances of $USER and appends it with that line and line number as follows but

12:user occurance line

But the requirement is that the format should be

12)user occurance line

I accomplished this via vim as use of sed and awk is not allowed.

They have got back to me and said, using vim is just like using sed or awk so we will not accept this.  What other direction is there?

```

#!/bin/bash


if [ $# -eq 0 ]

then echo "please pass a filename as an argument" ;

else
{
if [ -f  $1 ] 
then 
{
  grep -n $USER $1 >> $1;
  vim +%s/:/\)/g +wq $1;

}
fi;
}
fi;

```

---

### Post by mssever on 2008-05-05
You could do it in Ruby:

```
 echo "$somevar" | ruby -e 'print gets.gsub(/:/,")")'
```

---

### Post by newsman on 2008-05-05
yep they have made it difficult.

i think they might say,,, well using ruby is same as using sed or awk or vim hahaha (orginally they never said you cannot use vim but after submission they came back and said, well using vim is same as using sed or awk).

i did

```
grep -n $USER $1 | ruby -e 'print gets.gsub(/:/,")")' | cat 
```

and only get the first occurance rather than all occurances.

---

### Post by mssever on 2008-05-05
Well, you could run it in a loop. But if you're required to stick to pure bash, read up on parameter expansion, and check out the [Advanced Bash Scripting Guide]("http://tldp.org/LDP/abs/html/"). I don't have any personal experience solving such a problem in pure bash, as I don't see much point in it.

---

### Post by newsman on 2008-05-05
I have edited the file so it comes to variable now, (which works haha)  now to edit the variable.

$VAR | grep -n $USER $1 ; echo -n "$VAR";

which gives the output 
6:line
10:line
34:line

etc..

is there way to run through a loop sub : with )

how about using this properly?

nl [?bp")"?] $VAR



i got this from someone else but i don't know how to use it for my purpose with creating a temp file.

while read filename
do
grep ?$user? > temp
newform ?p[)] temp
nl [?bp?$user?] [temp]
cat temp
done

Thhe problem is only need 
newform ?p[)] temp
nl [?bp?$user?] [temp]

to act on a variable as temp file creation is not allowed for this exercise.

and i am getting  Syntax error: ")" unexpected (expecting "done") error on using the two commands and if do put ) in quotes in the first line 

So my main code looks like:

```

#!/bin/bash
if [ $# -eq 0 ]
then echo "please pass a filename as an argument" ;
else
{
if [ -f  $1 ] 
else
then 
{
  $VAR | grep $USER $1 ; echo -n "$VAR";
#  vim +%s/:/\)/g +wq $1;

 while read $VAR
 do
 newform ?p[")"] $VAR
 nl [?bp?] $VAR
 done
 echo "$VAR"

}
fi
}
fi

```


the output does not change and i get an additional error as follows:




line
line
line
line
line
read: 27: arg count

---

### Post by newsman on 2008-05-06
Why doesn't this work?

```
#!/bin/bash


if [ $# -eq 0 ]

then echo "please pass a filename as an argument" ;

else
{
if [ -f  $1 ] 
then 
{
  $VAR | grep -n $USER $1 ; echo -n $VAR;

  $newVAR=${VAR//\:/\)}
  echo $newVAR
}
fi
}
fi

```
it results in bad substitution error.


taken from your link above Bash advanced scripting guide:

${string//substring/replacement}	Replace all matches of $substring with $replacement

---

### Post by mssever on 2008-05-06
Try different escaping. Maybe \) is special. Maybe you need to escape the backslashes. I have no experience in this, so I really can't tell you much. Maybe you could poke ghostdog74 on this.

---

### Post by ghostdog74 on 2008-05-06
> **newsman said:**
> Why doesn't this work?

```
#!/bin/bash


if [ $# -eq 0 ]

then echo "please pass a filename as an argument" ;

else
{
if [ -f  $1 ] 
then 
{
  $VAR | grep -n $USER $1 ; echo -n $VAR;

  $newVAR=${VAR//\:/\)}
  echo $newVAR
}
fi
}
fi

```
it results in bad substitution error.


taken from your link above Bash advanced scripting guide:

${string//substring/replacement}	Replace all matches of $substring with $replacement

1) ask your teacher , can grep be used? 
2) What is $VAR, and where have you defined it?
3) What exactly is it you want to do, substitute ":" with ")" ?
Bash
```

# s="d:e"
# echo $s
d:e
# echo ${s/:/)}
d)e

```
of course, you should be using a bash shell to do this.

---

