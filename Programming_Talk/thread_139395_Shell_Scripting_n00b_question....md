---
title: "Shell Scripting n00b question..."
date: 2006-03-04
forum: Programming Talk
---

### Post by Itami on 2006-03-04
Ok this maybe easy for someone to answer.  My book and googling has not helped in the slightest.  All they explain about normal variables is like set Var=1. not useful.  I'm taking a Unix class right now but I've been kinda sick so I haven't had a chance to go to the labs and bug the tutors there, so I figured this was my next best bet.

So what I'm trying to do is take in user input in the form of a word, then extract the vowels from the word to then search a wordlist with them. 

What I'm trying to figure out is how do I seperate the individual characters i want and then how to put them into variables to use in my search?

---

### Post by stuporglue on 2006-03-04
Does this have to be done in shell (ie. bash/sh/etc) scripting? Can it be perl scripting or something, or does it have to be bash? If I were you, and it were allowed, I'd do it in perl, ruby, or python.  

If you pick a language that is not also the name of the shell, your google results will be more helpfull.

---

### Post by IYY on 2006-03-04
It's been a while since I used shell, so I don't remember how to do this in the most elegant and efficient way (and there are some pretty damn hot ways to do this).

I know that one option would be to just use a loop, and the cut command. For example 

echo ubuntu | cut -c2 

will print out the letter b.

---

### Post by Itami on 2006-03-04
You know, come to think of it I don't think it specifically has to be done in shell.  Though I'm even less familar with perl/python/etc.  The only thing I've worked in before this was Java, and unix/linux is a very alien thing.

Though is this sort thing even possible with a shell? (If it is I bet it's ugly).   Or does it require at least in part some scripting in like Python?

Guess I'll be reading up on python this weekend.

---

### Post by IYY on 2006-03-04
Certainly possible. Here's an example of how you may do this (in pseudocode, because as I said, I am rusty with the syntax):

loop for i = 0 to length of the word
> grep `cut -ci` wordlist.txt

---

### Post by Itami on 2006-03-04
[QUOTE=IYY]Certainly possible. Here's an example of how you may do this (in pseudocode, because as I said, I am rusty with the syntax):

loop for i = 0 to length of the word
> grep `cut -ci` wordlist.txt[/QUOTE]
Ohh dur, loop through the vowels, genius why didn't I think of that. I'll give it a shot.

---

### Post by nrwilk on 2006-03-05
[QUOTE=Itami]Though is this sort thing even possible with a shell? (If it is I bet it's ugly).[/QUOTE]
Actually, it's easier in a shell script than it would be if you did it in another language.

The tools you need to do it have already been mentioned, too.  Use grep and cut.

You may need some other commands in addition, but I assure you that it will be easier to do this in the shell than with perl or python.

Just take a gander at this quote from [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) :
[quote=http://linuxcommand.org/learning_the_shell.php]
Not long ago we had a problem where I work. There was a shared drive on one of our file servers that kept getting full. I won't mention that this legacy operating system did not support user quotas; that's another story. But the server kept getting full and stopping people from working. One of the software engineers in our company spent the day writing a C++ program that would look through the directories of all the users and add up the space they were using and make a listing of the results. Since I am forced to use the legacy OS while I am on the job, I installed a version of the bash shell that works on it. When I heard about the problem, I realized I could do all the work this engineer had done with this single line:

du -s * | sort -nr > $HOME/space_report.txt
[/QUOTE]

---

### Post by jerome bettis on 2006-03-05
i can't sleep so i did this, let me know if you want me to post it.

i used bash and awk's split() function to count the letters.

---

### Post by nrwilk on 2006-03-05
[QUOTE=jerome bettis]i can't sleep so i did this, let me know if you want me to post it.

i used bash and awk's split() function to count the letters.[/QUOTE]

That's cool.  I was going to suggest awk, but I thought it wasn't neccessary.

I like to do random scripting/coding when I can't sleep too.

---

### Post by Itami on 2006-03-05
[QUOTE=jerome bettis]i can't sleep so i did this, let me know if you want me to post it.

i used bash and awk's split() function to count the letters.[/QUOTE]
Oh I'd like to see.  Examples are the best way to learn.  That and I can't seem to get AWK to do anything for me.  It hates me.

---

### Post by jerome bettis on 2006-03-05
```
#!/bin/bash
# asks the user for a string and prints the number of vowels in it

# prints the count of a given letter in a given word
letter_count()  { # $1 = word, $2 = letter to count
    echo ${1} | awk -v letter=${2} ' {
                    printf("%d\n", (split($0, tmp, letter) - 1));
                } '
}

# prints the number of vowels in a given word
vowel_count()  { # $1 = word
    vowels="A E I O U a e i o u"
    num_vowels=0
    for i in ${vowels} ; do
        let "num_vowels += `letter_count ${1} ${i}`"
    done
    echo ${num_vowels}
}

main()  {
    echo -e "Enter a string:"
    str=`line`
    str2=""
    for i in ${str} ; do    # if they enter "abcde abc abcd"
        str2=${str2}${i}    # change it to "abcdeabcabcd"
    done                    # you could delete this to just count one word
    echo -e "\nThe string \"${str}\" has `vowel_count ${str2}` vowels in it."
}

main
```

---

### Post by Itami on 2006-03-05
[QUOTE=jerome bettis]```
#!/bin/bash
# asks the user for a string and prints the number of vowels in it

# prints the count of a given letter in a given word
letter_count()  { # $1 = word, $2 = letter to count
    echo ${1} | awk -v letter=${2} ' {
                    printf("%d\n", (split($0, tmp, letter) - 1));
                } '
}

# prints the number of vowels in a given word
vowel_count()  { # $1 = word
    vowels="A E I O U a e i o u"
    num_vowels=0
    for i in ${vowels} ; do
        let "num_vowels += `letter_count ${1} ${i}`"
    done
    echo ${num_vowels}
}

main()  {
    echo -e "Enter a string:"
    str=`line`
    str2=""
    for i in ${str} ; do    # if they enter "abcde abc abcd"
        str2=${str2}${i}    # change it to "abcdeabcabcd"
    done                    # you could delete this to just count one word
    echo -e "\nThe string \"${str}\" has `vowel_count ${str2}` vowels in it."
}

main
```[/QUOTE]
This is nice and all, and is really helping me get a better grasp on how to use AWK and variables but it still doesn't really help answer my question which is:

How do I seperate out the vowels (like into their own variables maybe) so I can use them to search a wordlist, in the same order as they were in the word?

---

### Post by jerome bettis on 2006-03-05
[quote=Itami]How do I seperate out the vowels (like into their own variables maybe) so I can use them to search a wordlist, in the same order as they were in the word?[/quote]

can you give an example of what you want to do?  that isn't very clear

---

### Post by hod139 on 2006-03-05
Not exactly sure what you want, but here is a pure bash solution using the 
cut command that IYY suggested.

```

#!/bin/bash
# asks the user for a string and prints the number of vowels in it
# and prints the order of the vowels

echo "Type a word, followed by [ENTER]:"
read word

vowels="AEIOUaeiou" 
vowelList=""  # variable to store the vowels in the order read

i=1  # cut starts at index 1, not 0
while [ $i -le ${#word} ]
do
    if [ `echo $word | cut -c$i | grep \[$vowels\]` ]; then
        vowelList=$vowelList`echo $word | cut -c$i`
    fi
    i=$((i+1))
done

echo "There are ${#vowelList} vowels."
echo "In order, they are: $vowelList"

```

---

### Post by Itami on 2006-03-05
[QUOTE=jerome bettis]can you give an example of what you want to do?  that isn't very clear[/QUOTE]
Not really, because if i could give an example I wouldn't need to ask for help now would i?

---

### Post by jerome bettis on 2006-03-05
[quote=Itami]Not really, because if i could give an example I wouldn't need to ask for help now would i?[/quote]

sigh  ... i mean an example of the problem you're trying to solve

like i have this word "afdsadasf" and i want to do this this and this so i have this for output.

that cut thing is pretty neat i'm gonna look at it.

---

### Post by Itami on 2006-03-05
[QUOTE=jerome bettis]sigh  ... i mean an example of the problem you're trying to solve

like i have this word "afdsadasf" and i want to do this this and this so i have this for output.

that cut thing is pretty neat i'm gonna look at it.[/QUOTE]
Alright lets see if I can think of something better to explain the problem.

Ok I need to take in an inputed word from a user.    Then take out the vowels from the word in order and use those vowels to search a wordlist.

The problem I'm having is extracting the vowels since i don't really know how to use variables and such.

Though that little vowel code script from hod139 is really close to what I need i think.

Nothing quite like learning a new programming language to make you feel really stupid.

---

### Post by jpkotta on 2006-03-05
To get only vowels:
```
cat file | sed -e 's/[^aeiouAEIOU ]//g'
```

To separate out letters:
```
cat file | sed -re 's/(.)/\1 /g'
```

Learn regexs.  You will love them.

---

### Post by colo on 2006-03-06
As of yet, each and every approach to filter out vowels seems overcomplicated to me.

```
read word && echo "${word}" | grep -io "[aeiou]"
```
To get rid of \n after each char, use tr.

Just in case the question on how to get the filtered chars into a variable:
```
read word && vowels="`echo ${word} | grep -io [aeiou]`"
```
To get rid of the whitespaces in between of the chars, again, use tr.

Hth.

---

### Post by hod139 on 2006-03-06
The -o option on grep is new to me, thanks for that trick.  Removes the loop in my code.

The ignore case option "-i" wasn't working for me though when used with the -o option.
```

$ echo "wOrd" | grep -i "[aeiou]"
wOrd
$

``` 
```

$ echo "wOrd" | grep -io "[aeiou]"
$
 
``` I'm not sure why it doesn't work.  Does anyone know why?

Itami, to use the "tr" command to strip the newlines and the spaces, the code would look like
```

#!/bin/bash
# asks the user for a string and prints the number of vowels in it
# and prints the order of the vowels

vowels="aeiouAEIOU" 
vowelList=""  # variable to store the vowels in the order read

echo "Type a word, followed by [ENTER]:"
read word && vowelList="`echo ${word} | grep -o [${vowels}]`"
vowelList=`echo ${vowelList} | tr -d '\n '` # delete spaces and newlines

## Or in one line if that's your thing
# read word && vowelList="`echo ${word} | grep -o [${vowels}]`" && vowelList=`echo ${vowelList} | tr -d '\n '`

echo "There are ${#vowelList} vowels."
echo "In order, they are: ${vowelList}"

```

---

### Post by Itami on 2006-03-06
Actually a friend helped me and I showed him your previous nugget of code hod139 and we cobbled together this:
```
echo "Please enter a word:"
read word
list=/usr/share/dict/WORD.LST
vowels="AEIOUaeiou"  #yay for vowels
vowelList=""  # variable to store the vowels in the order read

i=1  # cut starts at index 1, not 0
while [ $i -le ${#word} ]
do
        if [ `echo $word | cut -c$i | grep \[$vowels\]` ]; then
                vowelList=$vowelList`echo $word | cut -c$i`
                vowelList=$vowelList

        fi
        i=$((i+1))
done


echo "The vowels are: $vowelList"
echo "Searching... this may take a while, go get some crackers or something"
grep -i "[$vowelList]" $list > output.txt
echo "And the longest matching word is:"
echo | ./lensort output.txt | tail -1
echo "Full results printed in output.txt, feel free to delete it.
```
Which, while slow, does exactly what I needed. So yay!

Edit oh yeah this is lensort:
```
#! /bin/sh
awk 'BEGIN { FS=RS }
{ print length, $0}' $* |
#sort lines numerically
sort +0n -1 |
#remove length and paces and print lines
sed 's/^[0-9][0-9]* //'
```
which I stole from my unix book.

---

### Post by hod139 on 2006-03-06
Itami, I have a feeling you are still doing something wrong. That search you are performing doesn't care about the order of the vowels. In your code, if the vowels are "eo", grep would return "open" since 
```

$ echo open | grep "[eo]"
$ open

``` is correct. You need to make sure the regular expression you pass to grep does exactly what you want. I'm guessing you wanted:
```

 $ echo open | grep .*[e].*[o].*
$
 
``` where now open isn't found.  I have modified your posted script, and  made the lensort function internal.

```

#!/bin/bash

vowels="aeiouAEIOU" 
vowelList=""  # variable to store the vowels in the order read
#list=list=/usr/share/dict/WORD.LST  ## Didn't exist on my machine
list=/usr/share/dict/american-english #American English dictionary

lensort() { 
awk 'BEGIN { FS=RS }
{ print length, $0}' $* |
#sort lines numerically
sort +0n -1 |
#remove length and paces and print lines
sed 's/^[0-9][0-9]* //'
}

echo "Type a word, followed by [ENTER]:"
read word 

i=1  # cut starts at index 1, not 0
while [ $i -le ${#word} ]
do
    if [ `echo $word | cut -c$i | grep \[$vowels\]` ]; then
        vowelList=$vowelList".*["`echo $word | cut -c$i`"]"
    fi
    i=$((i+1))
done
vowelList=$vowelList".*"

echo "The vowels are: `echo $vowelList | tr -d '.*[]'`"
echo "The search string for grep is: $vowelList"
echo "Searching... this may take a while, go get some crackers or something"
grep -i ${vowelList} $list > output.txt
echo "And the longest matching word is: `lensort output.txt | tail -1`"
echo "Full results printed in output.txt, feel free to delete it."

``` 
and what is kinda fun
```

$ sh script.sh
Type a word, followed by [ENTER]:
aeiou
The vowels are: aeiou
The search string for grep is: .*[a].*[e].*[i].*[o].*[u].*
Searching... this may take a while, go get some crackers or something
And the longest matching word is: facetiousness's
Full results printed in output.txt, feel free to delete it.
$

``` 
and in case you wonder the other words found were: 
abstemious
adventitious
facetious
facetiously
facetiousness
facetiousness's
sacrilegious

**Edit:** For fun, I also tried "uoiea" and got the following words:
uncomplimentary
unnoticeable

---

