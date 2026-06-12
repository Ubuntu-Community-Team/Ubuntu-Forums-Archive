---
title: "sed command matching multiple line pattern"
date: 2010-08-24
forum: Programming Talk
---

### Post by dcombest on 2010-08-24
Hello all,

Im trying to write a bash function to find and replace several lines in a very long text file.  I started to use sed, but after wasting all day trying to get this to work, I have decided to post here.  basically i'm looking for following pattern
    $1      
    {
        type            fixedValue;
        value           uniform (* * *);
    }
 and replace with the following in the same file
    $1      
    {
        type            fixedValue;
        value           uniform ($2 $3 $4);
    } 

where $1 $2 $3 $4 are arguments passed to the function.  so far the function starts like:

function changeValue {
printf "Changing $1 value to ($2 $3 $4)\n"

sed -i "/inlet \n { \n type fixedValue; \n value uniform/ s/(.*)/$1\n    {\n        type            fixedValue;\n        value           uniform ($2 $3 $4);/g" U

}  

if I have it only match the word inlet and paste in the rest of the lines, it works.  However matching multiple lines is the problem.  Also, the words uniform, fixedValue, type, and value could appear multiple times in the file.  I'm new to sed (thats the real problem) and none of the tutorials I've found can really help.  Any help is much appreciated.

---

### Post by Bachstelze on 2010-08-24
sed normally works on one line at a time.  If you want to work on several lines in the same command, you have to add them to the pattern buffer with the N command:

```
firas@aoba:~$ cat foo.txt 
foo
bar
baz
firas@aoba:~$ sed 's/foo\nbar/foobar/' foo.txt # does not work
foo
bar
baz
firas@aoba:~$ sed 'N;s/foo\nbar/foobar/' foo.txt # works
foobar
baz
firas@aoba:~$ sed 'N;s/foo\nbar/goo\nbar/' foo.txt # also works
goo
bar
baz

```

---

### Post by DaithiF on 2010-08-25
Hi, something like this may get you started:
```
sed "/${value1}/{N;N;N;N;s/${value1}\n{\ntype fixedValue;\nvalue uniform (\* \* \*)\;\n}/changedValue\n{\ntype fixedValue;\nvalue uniform(${value2} ${value3} ${value4});\n}/}" somefile

```

if there is any leading / trailing whitespace on these lines then it will require some tweaking.

---

### Post by dcombest on 2010-08-25
Thanks Bachstelze and DaithiF for the posts, both helped a lot.  I ended up doing something like

sed -i "/$1/{N; N; N; N; s/$1\n\    {\n\        type            fixedValue;\n\        value           uniform ([0-9] [0-9] [0-9]);/$1\n    {\n        type            fixedValue;\n        value           uniform ($2 $3 $4);/g}" filename

I had to put spaces after the "N;" and add in the tweeks for leading white spaces, along with matching the exact spacing between the value and uniform words (exact spacing did not show up in post here).  However, I am having difficulty in finding/implementing a wildcard for numbers in those places I had stars (or the [0-9]'s now).  The numbers could be positive or negative decimals with leading zeros and many decimal places.  How is one able to search for any numbers in the parentheses after "uniform" and replace them with $2 $3 $4 values?  Thanks again for your help.

---

### Post by dcombest on 2010-08-25
I think i might have figured it out (quick testing says yes).  

replace 
uniform ([0-9] [0-9] [0-9])

with
uniform (*.*[0-9]* *.*[0-9]* *.*[0-9]*)

and this seems to take care of positive and nagative numbers with decimal places and even numbers like -1.3434e-5

I'll do more testing and post if this doesn't work.

---

### Post by DaithiF on 2010-08-26
or:
-\?[0-9.]\+

---

