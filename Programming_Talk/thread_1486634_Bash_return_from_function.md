---
title: "Bash return from function"
date: 2010-05-18
forum: Programming Talk
---

### Post by dragos2 on 2010-05-18
I have a function that returns a value
```

function afunc {
 found=0
 # code
 if some-stuff
  found=`expr $found + 1`
 return $found
}

```

Then in the main code
```

    afunc
    ret=$?
    if [[ "$ret" -gt "0" ]]; then
     echo "Sending email.."
     mailFile "mail.txt"
    fi

```

Surprise or not when debugging with bash -x the output is:
```

++ expr 0 + 1
+ found=1
+ return 0
+ ret=0
+ [[ 0 -gt 0 ]]

```

Why ?

---

### Post by BoneKracker on 2010-05-18
Interesting.

It looks like it's returning the value but still assigning "success" to the function's exit status.  I can't explain that.  It looks to me like it ought to work.

I personally would try one of these next just to see if it produces a different result.:

```
    ret=$(afunc)
    if [[ "$ret" -gt "0" ]]; then
     echo "Sending email.."
     mailFile "mail.txt"
    fi

```
```

    if [[ "$(afunc)" -gt "0" ]]; then
     echo "Sending email.."
     mailFile "mail.txt"
    fi
```

---

### Post by frostschutz on 2010-05-18
bash functions can only return exit / success status or, in other words, integer values of a certain range, read man bash for details

if you need to return arbitrary values, use variables instead

you can still return success or not so && || etc will work properly

```

function foo() {
    do something great
    HEUREKA=xyz
    return 0
}

foo && echo Aaand the winner is $HEUREKA || echo Oh noes, we fail

```

EDIT:
Just tried your snippet, works for me actually (for found=0 / 1)... do you actually use these values or other?

Also, dunno if this is BASH only, but instead of `expr ` I usually just write $[$found+1]

---

### Post by dragos2 on 2010-05-18
It is incredible, I did not returned from function, instead defined found=0 at the beginning
of script then in main routine I am doing the comparision like this:

```

#!/bin/bash -x

found=0

function afunc {
 # code here
}

#main routine
if [ "$found" -gt "0" ]; then
     echo "Sending email.."
     mailFile "mail.txt"
fi

```and the trace:
```

+ echo 'Incrementing found..'
Incrementing found..
++ expr 0 + 1
+ found=1
+ read line
+ '[' 0 -gt 0 ']'

```Why is this happening? :(

---

### Post by BoneKracker on 2010-05-18
Hard to tell without seeing the code.  For example, I don't see any read statements anywhere, and there's a read occurring now between your variable assignment and the comparison operation.

Also, I stay away from using $? because it's easy to misinterpret what it's referring to (it's the exit status of the last operation).  That's why my suggestions centered on avoiding the use of $? and instead directly assigning the value returned by the function to a variable.

Additionally, I second frostschultz' suggestion that the function do what you actually need it to do: return true or false.  You need to know whether or not to send mail, so the function should return true or false, not some count of messages or something.

---

### Post by dragos2 on 2010-05-18
> **BoneKracker said:**
> Hard to tell without seeing the code.  For example, I don't see any read statements anywhere, and there's a read occurring now between your variable assignment and the comparison operation.

Also, I stay away from using $? because it's easy to misinterpret what it's referring to (it's the exit status of the last operation).  That's why my suggestions centered on avoiding the use of $? and instead directly assigning the value returned by the function to a variable.

Additionally, I second frostschultz' suggestion that the function do what you actually need it to do: return true or false.  You need to know whether or not to send mail, so the function should return true or false, not some count of messages or something.

The function now does not return anything, it just increments found variable, which can be seen globally. Then in main routine I am calling the afunc function, then back in main routine where I compare if found is -gt 0. 

It seems that somehow it loosens its value outside of the function..

---

### Post by BoneKracker on 2010-05-18
If you've declared the variable in the main script it should have global scope, and you should be able to make an assignment to it within the function and have it reflected outside the function (unless within the function you have also declared the variable with local scope, effectively overloading it).  So based on what you're _saying_, it should be working.

It's starting to sound like you have some weird shell options set or something.

See what happens if you avoid using the return value.  Have the function 'echo' the value to stdout, and then capture the value by using command substitution (like I showed above, but with 'echo' instead of 'return').

```
afunc() {

  blah blah

  echo $found

}

```
And then use command substution instead of the return value; something like one of these:
 ```
   ret=$(afunc)
    if [[ "$ret" -gt "0" ]]; then
     echo "Sending email.."
     mailFile "mail.txt"
    fi
``````
    if [[ "$(afunc)" -gt "0" ]]; then
     echo "Sending email.."
     mailFile "mail.txt"
    fi
```

---

### Post by hannaman on 2010-05-18
It seems to work for me.
```
#!/bin/bash -x

found=0

function afunc {
        found=`expr $found + 1`
}

afunc
if [ "$found" -gt "0" ]; then
        echo "Sending email..."
else
        echo "No email..."
fi

```
```
+ found=0
+ afunc
++ expr 0 + 1
+ found=1
+ '[' 1 -gt 0 ']'
+ echo 'Sending email...'
Sending email...

```
Are you sure you don't have a typo somewhere?

---

### Post by BoneKracker on 2010-05-18
That test script works for me, as does your original code:```
#!/bin/bash -x

afunc() {
 found=`expr $found + 1`
 return $found
}

afunc

ret=$?
if [[ "$ret" -gt "0" ]]; then
   echo "Sending email.."
fi

``````
~ $ ./test.sh 
+ afunc
++ expr + 1
+ found=1
+ return 1
+ ret=1
+ [[ 1 -gt 0 ]]
+ echo 'Sending email..'
Sending email..
```


Verify that those two scriptlets, as posted, do not run properly.

If they don't, then you must have some kind of weird shell option set or something.

---

### Post by dragos2 on 2010-05-19
The short version works fine, it seems that there is a type somewhere.

Thanks all for helping.

---

### Post by BoneKracker on 2010-05-19
Please put "[SOLVED]" in the subject line of the original post.

Or maybe "[Doh!  My bad.]" would be more apropos.

---

### Post by dragos2 on 2010-05-19
> **BoneKracker said:**
> Please put "[SOLVED]" in the subject line of the original post.

Or maybe "[Doh!  My bad.]" would be more apropos.

:) I will update when I find my error.

---

### Post by dragos2 on 2010-05-20
I am releasing a functional code:
In my bash shell from 8.04 found is never returned as true!!

How is in yours ?

```

#!/bin/bash -x

SMB=/home/dragos
pj=$SMB/a
mc=$SMB/b

totalLines=0
changesperuser=1
found=false

function mailFile {
 content=$(cat "$1")
 echo "Changed files: $content" | mailx -s "Files" someemail@address.com
}

function analyze {
 a=$(cat diff.txt | grep -E "<|>" | awk '{print $2}')
 if [ -z "$a" ]
 then
  return 0
 fi

 if [[ -f temp.txt ]]; then
  rm -f temp.txt
 fi
 touch temp.txt

 if [[ -f mail.txt ]]; then
  rm -f mail.txt
 fi
 touch mail.txt

 if [[ -f temp2.txt ]]; then
  rm -f temp2.txt
 fi
 touch temp2.txt

 echo "$a" | while read line;
 do
  echo $(ls -l "$line") >> temp.txt
 done

 cat temp.txt | awk '{print $3}' | grep -v '^$' | uniq > temp2.txt
 
 cat temp2.txt | while read line;
 do
  content=$(grep $line temp.txt)
  size=$(grep $line temp.txt | wc | awk '{print $1}')
  if [ $size -gt $changesperuser ]; 
  then
   found=true
   echo "User $line has $size changed files :" >> mail.txt
   echo "$content" >> mail.txt
  fi
 done
}

function updatef1 {
 touch "f1.txt"
 echo "updating f1.."
 find $pj/ $mc/ 2>/dev/null > f1.txt
 changed=$(diff f1.txt f2.txt)
 echo "$changed" > diff.txt
}

function updatef2 {
 touch "f2.txt"
 echo "updating f2.."
 find $pj/ $mc/ 2>/dev/null > f2.txt
 changed=$(diff f2.txt f1.txt)
 echo "$changed" > diff.txt
}

if test "f1.txt" -nt "f2.txt";
then
 updatef2
 analyze
 if $found; 
 then
  echo "Sending email.."
  mailFile "mail.txt"
 fi
else
 updatef1
 analyze
 if $found;
 then
  echo "Sending email.."
  mailFile "mail.txt"
 fi
fi

```

---

### Post by dragos2 on 2010-05-21
Sorry for bumping but please have a look at the upper code, it is very weird why the $found variable can't keep its state.

Thank you

---

