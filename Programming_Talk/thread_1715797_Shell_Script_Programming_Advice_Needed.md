---
title: "Shell Script Programming Advice Needed"
date: 2011-03-27
forum: Programming Talk
---

### Post by bikepaths on 2011-03-27
I am writing a shell script and need help.  Using a text file for input, for each execution I need to read through the file to output a range of characters and place a flag to mark the start of the next execution.  The range begins at the flag (or top of the file if no flag present) and ends at 500 characters, only if 500 is a period or comma. If not, I must go back to find the nearest period or comma, truncate my range, and put the flag there. Finally, I must abort when the flag reaches end of the file. This may involve awk or sed and regex, each of which I am an extreme novice.  Can anyone suggest some simple ways to do this?  Thanks.

---

### Post by deathadder on 2011-03-28
Sounds like some homework to me =P

I find the Bash Scripting Guide [1] helpful. There's also a sed / awk primer that should get you going [2].

I would suggest getting something basic together that lets you read in a file and print out the characters and build up from there. 

Post what you've got at the moment and I'll take a look to see if there are more specific pointers I can give you.

There's loads of helpful stuff from Google, so have a search around. If you're not sure what a command does you can Google it, or read the man pages. If you're not sure what some logic is doing you can always ask in the forum ;)

[1] [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[2] [http://tldp.org/LDP/abs/html/sedawk.html](http://tldp.org/LDP/abs/html/sedawk.html)

---

### Post by bikepaths on 2011-03-28
Hi and thanks.  Not homework, but have been developing this website [www.recycles.org](www.recycles.org) ... taught myself some Php and MySql to make the site work as it is.  Never had formal programming lessons, so first I spell out the task step-by-step.  First thing I need to do is to figure out how to make the flag work in an efficient manner. I think this may be a simple task, but have not been able to find useful code examples.  Still searching for examples.  Then I thought maybe I should use Php.  Don't laugh, but this is as far as I have gotten:

#!/bin/bash
#
# input text file
# find flag to begin
# if no flag, assume flag at start of file
# if flag, get string of 500 characters max past flag
# string contains no hard/soft returns or multiple spaces
# if 500th character is symbol . , ? !
# output string and place flag
# if not, go back to find nearest such symbol
# output string and place flag
# if flag at end of file, abort.

if [ $# -eq 0 ]
then
echo "Error: Command line argument missing"
echo "Usage: $0 <filename>"
echo "where <filename> is a text file to be processed."
exit 1
fi

echo "processing file: $1"

---

### Post by deathadder on 2011-03-28
Ok, it just sounds like a typical homework piece to me :)

The first thing I would suggest you do is get the various arguments from the script assigned, $1 is being used as the file to scan so doing something like this:
```
inputFile=$1
```
It'll make it easier to remember what everything is pointing too further along!

I would also assign variables for the flag, the number of characters to scan and the characters you want to check at the 500th position ".,?!". An [array]("http://www.google.co.uk/search?q=bash+array&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a&safe=images") may be the best means of doing this. 

So you may end up with something similar to this:
```

inputFile=foo
flag=bar
charPos=foobar
specialChars=ARRAY

```

Once you've got the basics of the script setup, you can start by searching the position of the first flag in the file. Google has quite a few hits for something like "[bash find position of character in file]("http://www.google.co.uk/search?source=ig&hl=en&rlz=&=&q=bash+find+position+of+character+in+string&aq=0&aqi=g1g-j2&aql=&oq=bash+find+position+#sclient=psy&hl=en&source=hp&q=bash+find+position+of+character+in+file&aq=f&aqi=&aql=&oq=&pbx=1&fp=57a6b31d03a355e6&safe=images")"

Have a go a putting those bits together, and searching for the character position then post what you've got along with an idea of what you want to do next, where you've searched for it etc. 

I know it's a pain not having me just write a script for you but honestly I don't like doing that. If you don't understand what's happening I could just throw something in that would screw your system up.:twisted: Anyway, it's always good to know what to do so you can do it again some day if you need too :)

---

### Post by bikepaths on 2011-03-28
Thanks. 
Looks like this is the [best resource]("http://tldp.org/LDP/abs/html/index.html").
I setup the variables as suggested:

```

inputFile=$1
flag=XXX-FLAG-XXX
charPos=500
specialChars=( . , ! ? )

if [ $# -eq 0 ]
then
echo "Error: Command line argument missing"
echo "Usage: $inputFile <filename>"
echo "where <filename> is a text file to be processed."
exit 1
fi

echo "processing file: $inputFile"

```

I believe that is right.  
Next read $inputFile to see if $flag exists.  
Then, three conditions:

1. If $flag no exist, then assume $flag at start of file. 
2. If $flag at end of the file, then abort.
3. If $flag exists, then ... (more complicated).

Thinking deeper, maybe I don't need $flag.  
Could extract/delete/output string from beginning of file.  

Therefore,
1. If file empty, abort.
2. read 500 characters from the first non-blank space from start of file.
3. If 500th character is equal to an element in $specialChars, then delete/extract/output.

But then what about another approach?
What if I processed the whole file at once.
Each line would be a string of 500 characters or ( 500 - x ).
(Determining the value of x is a problem for later.)

Now with the file all set up line by line,
I could use "sed" one-liners to grab and delete the first line.

```

# delete all leading blank lines at top of file
sed '/./,$!d' $inputFile
# delete leading and trailing whitespace from each line
sed 's/^[ \t]*//;s/[ \t]*$//' $inputFile
# print first line of file
sed 'q' $inputFile > $output
# delete the first line
sed '1d' $inputFile

```

What do you think of this approach?
Can suggest any tips?

I know how you feel about working the problem out for me.  I would definitely study and understand every line of code before executing.  I want to learn but it's difficult to know the best approach without the big picture.  Often I go the long way around for a simple task.  I teach elementary English in Cambodia, so I know it's best to have a guide and sounding board.  Thanks for your help to see me through this task.

---

### Post by pl@yer on 2011-03-28
I found this challenging, while not perfect here is what I came up with. 
It uses a "+" sign as the flag. So if there are "+" in your text either change the flag or take them out first. 

Use at your own risk- I wont be held responsible if this causes you to lose any data or your house to burn down :) 

```

#!/bin/bash

# input text file
filenm="test.txt"
filetxt=$(<$filenm)

# find flag to begin
#using "+" as flag to parse file
flagpos=$(echo $filetxt|grep -o "[a-zA-Z0-9\.\?\!\ \+\,\'\-]"| grep -n +|cut -d ':' -f1)

# if no flag, assume flag at start of file "character 1"
echo $flagpos|grep [0-9]>./garbout.txt
[ $? -ne 0 ]&&flagpos="1"
#echo "flagpos is $flagpos"
# if flag, get string of 500 characters max past flag
#determine 500 chars past the flag
stopper=$(echo "$flagpos + 500"|bc)
#echo $flagpos $stopper
chunk1=$(echo $filetxt|cut -b "$flagpos"-"$stopper")
# if 500th character is symbol . , ? !
# output string and place flag
echo $chunk1|grep [.,?]$
if [ $? -eq 0 ]
then
echo $chunk1
else
# if not, go back to find nearest such symbol
#looking through $chunk1
#for loop on ". , ? !"
#determine which is the last character to have symbol . , ? !
#echo string pipe to cut -b to last character
lastsymold="0"
for symb in '\.' '\,' '\?' '\!'
do
lastsym=$(echo $chunk1|grep -o "[a-zA-Z0-9\.\?\!\ \'\,\-]"|grep -n "$symb"|cut -d ':' -f1|tail -1)
echo $lastsym|grep [0-9]>./garbout.txt
if [ $? -eq 0 ]
then
if [ $lastsym -gt $lastsymold ]
then
lastsymold=$lastsym
#echo "lastsymbold is $lastsymold"
#echo "lastsymbol is $lastsym"
fi
fi
done
chunk1=$(echo $chunk1|cut -b "1"-"$lastsymold")
replacechunk=$(echo $chunk1|sed -e "s/^\+//"|sed -e "s/$/\+/")
echo $chunk1
#echo $replacechunk
echo $filetxt|sed "s/$chunk1/$replacechunk/">test.txt
fi
rm ./garbout.txt

```

---

### Post by deathadder on 2011-03-29
> **bikepaths said:**
> Thanks. 
Looks like this is the [best resource]("http://tldp.org/LDP/abs/html/index.html").
I setup the variables as suggested:

```

inputFile=$1
flag=XXX-FLAG-XXX
charPos=500
specialChars=( . , ! ? )

if [ $# -eq 0 ]
then
echo "Error: Command line argument missing"
echo "Usage: $inputFile <filename>"
echo "where <filename> is a text file to be processed."
exit 1
fi

echo "processing file: $inputFile"

```

I believe that is right.  
Next read $inputFile to see if $flag exists.  
Not quite, but very close. What I would do is drop the check to see if the number of arguments above the variable assignment, at the moment you're going to be assinging potentionally nothing to inputFile and then attemp to use that in the usage. The basename command will grab the scripts name for you, so I would use the following instead:
```

if [ $# -eq 0 ] ; then
    echo "Error: Command line argument missing"
    echo "Usage: $(basename $0) <filename>"
    echo "where <filename> is a text file to be processed."
    exit 1
fi

inputFile=$1
flag="XXX-FLAG-XXX"
charPos=500
specialChars=( . , ! ? )
```
Within a bash script $0 always refers to the actual script. One thing I would consider is, can you always guarantee that $1 will be a file? Before assigning it to inputFile it might be worth checking:
```

if [ ! -f $1 ] ; then
   echo "Fatal error: $1 is not a file."
   exit 1
fi

inputFile=$1 # Now we know $1 is a file!

```
> 
Then, three conditions:

1. If $flag no exist, then assume $flag at start of file. 
2. If $flag at end of the file, then abort.
3. If $flag exists, then ... (more complicated).

Thinking deeper, maybe I don't need $flag.  
Could extract/delete/output string from beginning of file.  

Therefore,
1. If file empty, abort.
2. read 500 characters from the first non-blank space from start of file.
3. If 500th character is equal to an element in $specialChars, then delete/extract/output.
I like your second approach so lets go with that. :) If you have a look at "[File test operations]("http://tldp.org/LDP/abs/html/fto.html")" you can see that there is this option:
> -s

    file is not zero size
From that you can add another check, or if you think about it you can modify the file exists check to do both jobs. To do that you'd need to check the return status of the command. Some reading into it tells us that a return status of 1 means that the file either has a 0 size, or does not exist. The return status for a command is stored within the "$?" variable. We can update the check like so:
```
[[ -s $1 ]]
if [ $? -eq 1 ] ; then
   echo "File does not exist or is empty."
   exit 1
fi
inputFile=$1
```
sed does not modify the file directly, it will output the result of the command to stdout (the console). So what you should do, IMHO, is take the sed command to remove all leading whitespace and run it against the file to create a temporary file.

```

# delete leading and trailing whitespace from each line
sed 's/^[ \t]*//;s/[ \t]*$//' $inputFile > $inputFile.tmp

```
You should read the "[I/O redirection]("http://www.tldp.org/LDP/abs/html/io-redirection.html#IOREDIRREF")" of TLDP to understand what I've done there! Any questions just ask.

Now the new file will contain everything the original does, apart from leading / trailing whitespace. 

Our resulting script at the moment will look like this:
```

#!/bin/bash

if [ $# -eq 0 ] ; then
    echo "Error: Command line argument missing"
    echo "Usage: $(basename $0) <filename>"
    echo "where <filename> is a text file to be processed."
    exit 1
fi

# If it makes more sense to you to check the file exists, then replace this with the -f check!
[[ -s $1 ]]

if [ $? -eq 1 ] ; then
	echo "$1 does not exist or is empty. Not processing!"
	exit 1
fi

# Set up script variables
inputFile=$1
tempInputFile=$1.tmp
flag="XXX-FLAG-XXX"
charPos=500
specialChars=( . , ! ? )

# delete leading and trailing whitespace from each line
sed 's/^[ \t]*//;s/[ \t]*$//' $inputFile > $tempInputFile

```
I know there's a lot of stuff in here, but go through it and understand what's happening. Ask any questions you have and then we can move on :)

[EDIT...]
Reading into this a little more, the -s check will let you know if the file exists or has a non-zero size, what it doesn't do however (unlike -f) is check to see if the file is a regular file and not a [device file]("http://tldp.org/LDP/abs/html/devref1.html#DEVFILEREF"). What you can do is using a logical operator is tie it together, so that if the file does not exist, or it has a 0 size, or it is not a regular file then exit. 
```

[[ -s $1 ]]

if [ $? -eq 1 ] || [ ! -f $1 ] ; then
    echo "Fatal Error: File does not exists, has a zero size or is not a regular file."
    exit 1
fi

```

Now if you can get together something to attempt to [read character by character]("http://www.google.co.uk/#sclient=psy&hl=en&q=bash+read+character+by+character&aq=1&aqi=g2g-b2&aql=&oq=bash+read+char&pbx=1&fp=ebd605fcb5a6383a"), we can have a look at it. You may also want to have a look at "grep" to see if you can find the flag at all within the file. :)

---

### Post by bikepaths on 2011-03-29
Thanks to you both deathadder and pl@yer for the pointers.  With my other work it will take a while to study all of this to figure out exactly what is happening, but it is a great way to learn ... it may take a few days, but I will write back with a progress report ... thanks again for your help.

---

### Post by pl@yer on 2011-03-29
I'd like to hear your progress. 

I wanted to let you know some issues with the script I posted, 


I don't have all possible characters in the first grep. For example double quotes are missing. So for every double quote in the string the script 
will be out 1 character. 
```

grep -o "[a-zA-Z0-9\.\?\!\ \+\,\'\-]"

```

Then there will be leading characters in front of the "+" in the string. This will cause the below sed command to **not** get rid of the "+". Leading to a failure.
```

replacechunk=$(echo $chunk1|sed -e "s/^\+//"|sed -e "s/$/\+/")

```

The code below attempts to check if the last character of the string is punctuation. I don't have an "!" in there so if the current string ends with that it will end up going back to previous punctuation.
```

echo $chunk1|grep [.,?]$

```

I'm sure there are lots of room for fixing and tweaking.

---

### Post by bikepaths on 2011-03-30
I have time to look at this between students. From the discussion, I combined the initial checking routine and it seems to do the job nicely :  

```

[[ -s $1 ]]
if [ $? -eq 1 ] || [ ! -f $1 ] || [ $# -eq 0 ]; then
    echo "Filename is missing, does not exist, has a zero size, or is not a regular file."
    echo "Error: Command line argument missing"
    echo "Usage: $(basename $0) <filename>"
    echo "where <filename> is a text file to be processed."
    exit 1
fi

```

After that, things become a bit more tangled.  Pl@yer I see your code involves some simple commands with switches and regex piped and redirected.  It's difficult for me to understand because of all the pipes and regex, but I understand the individual concepts and can study the bigger picture further.  The sum of the parts equals the whole.  What is it but : echo, bc, if/then/else/fi, do/done, grep, cut, sed, rm ?

Well even with my limited understanding, it didn't seem dangerous to do a test run, but I hit an error.  It seems bash error reporting does not tell me which line the cut problem is occurring.  Here is my output from prompt to prompt : 

```

user0@aspire ~/docs/program-test/> ./script-test.sh testfile
cut: invalid decreasing range
Try `cut --help' for more information.

sed: -e expression #1, char 0: no previous regular expression
user0@aspire ~/docs/program-test/>

```

Okay, no problem really, I can rtfm and tweak to see what becomes of things.  Certainly I will learn, but what about the idea of not using a flag?  Also I need to really define the variables at the start just so I can understand and read through it more easily.  I think your code is what they call cryptic, and I really can appreciate being able to do 5 tasks on one line of code, but it really takes some study to figure it out.  That's where I am at with this project today ... will continue. Thanks again for the tips ...

---

### Post by pl@yer on 2011-03-31
This is how I would troubleshoot.

Edit- Looking at the script keeping the error in mind. The error is saying that we are using a decreasing range. 

For example:
this works
```

$ echo testing|cut -b 1-3
tes

```

This does not
```

echo testing|cut -b 3-1
cut: invalid decreasing range
Try `cut --help' for more information.

```

So what I think is happening is that the variable for cut is not getting populated properly. 

So the command causing the problem is a cut command that has the -b option in it. Which means it is either of these 2 lines.

```

chunk1=$(echo $filetxt|cut -b "$flagpos"-"$stopper")
chunk1=$(echo $chunk1|cut -b "1"-"$lastsymold")

```


In order to troubleshoot this further I would add a couple of lines to validate the variables for cut -b.

To validate the first instance of cut -b
I would change this line 
```

chunk1=$(echo $filetxt|cut -b "$flagpos"-"$stopper")

```
to
```

echo "$flagpos is \$flagpos $stopper is \$stopper"
chunk1=$(echo $filetxt|cut -b "$flagpos"-"$stopper")

```

---

