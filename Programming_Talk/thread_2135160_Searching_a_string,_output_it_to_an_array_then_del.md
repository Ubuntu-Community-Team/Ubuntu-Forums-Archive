---
title: "Searching a string, output it to an array then delete it based on user input"
date: 2013-04-13
forum: Programming Talk
---

### Post by fr0s7y on 2013-04-13
Hey,

So I'm developing a simple Address book and its going well.
It uses a singular text file to store all its information.

At the minute i can search the file for a specific string, not a problem.

I'm pretty sure i can get it to delete a string based on a users input, thats kind of easy but i thought for extra snazziness it would be 
a neat idea if I could grab the output of the search term - a multi-line output say - and store each new line into an array, each assigned a number.
From there the user could specify they would like to delete the line based on their input.

So far this is the 'delete' script:

```
ADDRESSBOOK=~/Documents/Address-Book/add_data.txt

export ADDRESSBOOK

echo "=============================== Delete a Record ==============================="
echo "==============================================================================="
echo "============ Search A Record, then delete it! Type 'exit' to exit =============

"

exit=0
search(){
while [ $exit -ne 1 ]
        do
        
        echo "Find something for me to delete"
        echo -n "-----------------------> "

        read searchTerm
    if [ "$searchTerm" = "exit" ]
    then 
        exit=1
    else

        searchOutput=$(grep $searchTerm*.$ $ADDRESSBOOK | sort)

        echo "$searchOutput"
    fi
    done

exit 0
}

search

```

The address book automatically adds each record with /n so it displays each record on a new line anyway.

Is it possible to take the $searchRecord variable and pass that to an array?

And before I go wrapping my head around arrays, is this even the best approach to take for what I'm trying to do?

---

### Post by schragge on 2013-04-13
Something like
```

while
  read -p 'Find something for me to delete> ' searchTerm
  [[ $searchTerm != 'exit' ]]
do
  ifs=$IFS; IFS=$'\n'; searchOutput=( $(grep "$searchTerm" "$ADDRESSBOOK"| sort) ); IFS=$ifs
  if ((${#searchOutput[@]}>1)); then
    PS3="Select line to delete: "
    select line in "${searchOutput[@]}"; do
      [[ -z $line ]] && break
      echo Deleting $line
    done
  else
    echo Deleting $searchOutput
  fi
done

```

---

### Post by Vaphell on 2013-04-13
arrays are very useful, so it's not like you waste your time even if they won't help here (though they should, as they eliminate the need of parsing strings by hand on every turn)

example

```
$ array=()
$ while read -r line; do   array+=( "$line" ); done < <( echo $'wut\nomg\na bc\ndef\ng h\ni' | sort )
$ printf "'%s'\n" "${array[@]}"
'a bc'
'def'
'g h'
'i'
'omg'
'wut'
$ select s in "${array[@]}"; do echo "selected: '$s'"; break; done
1) a bc
2) def
3) g h
4) i
5) omg
6) wut
#? 5
selected: 'omg'
```
example is one-linerish because it was typed directly in terminal, obviously in script this should have nice indentation
echo is an equivalent of your grep

removing element from array can be done with *unset array[n]* so you need to loop over the array, find proper index and parametrize *unset*

```
array=( "ab" "c d" "e" )
search="e"
$ for(( i=0; i<${#array[@]}; i++ )); do [ "$search" = "${array[$i]}" ] && echo $i && break; done
2
$ unset array[$i]
$ printf "'%s'\n" "${array[@]}"
'ab'
'c d'
```

---

### Post by fr0s7y on 2013-04-13
ok so, there were a few syntax bits, unexpected '(' and the like as i integrated the statement into the existing code.

Here is the code at the minute:

```
while [ $exit -ne 1 ]
        do
        
        echo "Find something for me to delete"
        echo -n "-----------------------> "

        read searchTerm
        ifs=$IFS; IFS=$'\n'; searchOutput=$(grep $searchTerm*.$ $ADDRESSBOOK | sort); IFS=$ifs
        if [[ ${#searchOutput[@]} gt 1 ]]; then
         PS3="Select line to delete: "
         select line in "${searchOutput[@]}";
           [[ -z $line ]] && break
           echo Deleting $line

        else
              echo Deleting $searchOutput
        fi
    done

exit 0
```

which is giving me:

```
Find something for me to delete
-----------------------> a
grep: /home/fr0s7y/Docume: No such file or directory
grep: ts/Address-Book/add_data.txt: No such file or directory
./delete.sh: 30: ./delete.sh: [[: not found
Deleting

```

strange how grep is cutting off the last couple of digits from documents, also I dont understand where the file path for 'ts/' is being declared :/

---

### Post by schragge on 2013-04-13
I've updated my post, it now includes the full while loop. BTW are you using bash? Looks like you're trying to execute it with */bin/sh*

---

### Post by fr0s7y on 2013-04-13
is the first line array=() intended to be an empty array? all examples like to populate it with array=(num1, num2, num3) etc.

bash is telling me that '(' is unexpected on that line

---

### Post by fr0s7y on 2013-04-13
> **schragge said:**
> I've updated my post, it's now includes the full while loop. BTW are you using bash? Looks like you're trying to execute it with */bin/sh*

sorry yeah, its a .sh script, would that be why theres an error in the file path?

---

### Post by Vaphell on 2013-04-13
yes, it's empty because i want to populate it with += operator (add elem(s)) inside while read loop for each line. I updated my previous post with how to remove elements from array

```
$ array=()
$ printf "%s\n" "${array[@]}"

$ array+=( 'a' )
$ printf "%s\n" "${array[@]}"
a
$ array+=( 'b' 'c' 'd' )
$ printf "%s\n" "${array[@]}"
a
b
c
d
```


array is a bash feature so you either need to run the script with *bash script* or explicitly declare bash in the very first line of the script: **#!/bin/bash** and run with *./script*

---

### Post by schragge on 2013-04-13
No matter what the extension is, it depends on the shebang line:
```
!#/bin/bash
```

---

### Post by fr0s7y on 2013-04-13
yeah the shebang is included at the top of the file like so :
```

#!/bin/bash -       
#title           :delete.sh
#description :This script will delete an entry in  the Address Book
#date          :April 2013
#version      :1.0
#==============================================================================
```

the script is part of a larger program as in i have a run.sh that handles the main menu etc. with different .sh files for different parts of the application, add, search, print etc.

all .sh files are in the same directory, the address book is stored in the users documents.

---

### Post by fr0s7y on 2013-04-13
> **Vaphell said:**
> yes, it's empty because i want to populate it with += operator (add elem(s)) inside while read loop for each line. I updated my previous post with how to remove elements from array

```
$ array=()
$ printf "%s\n" "${array[@]}"

$ array+=( 'a' )
$ printf "%s\n" "${array[@]}"
a
$ array+=( 'b' 'c' 'd' )
$ printf "%s\n" "${array[@]}"
a
b
c
d
```


array is a bash feature so you either need to run the script with *bash script* or explicitly declare bash in the very first line of the script: **#!/bin/bash** and run with *./script*

how to pull the output of grep into the array though? ```
array=($searchOutput) 
``` something like that?

---

### Post by schragge on 2013-04-13
First, check that you are not invoking delete.sh with *sh delete.sh* anywhere nor sourcing it from a */bin/sh* script.
Next, add *set -x* to the beginning of the script and watch out where it terminates.

---

### Post by schragge on 2013-04-13
> **fr0s7y said:**
> how to pull the output of grep into the array though? ```
array=($searchOutput) 
``` something like that?Look again at [post=12601487]my example above[/post].

---

### Post by Vaphell on 2013-04-13
no, by while reading it line by line (i dislike IFS hack and it can't be made to work with \0-delimited lists). In the example from my first post i said echo is your grep

```
array=()
while read -r line
do
  array+=( "$line" )
done < <( grep "$search" file | sort )
```

if you really want to do this via IFS
```
IFS=$'\n' array=( $output )
```
IFS is changed locally only for the creation of array, so you don't have to save it and then restore it

---

### Post by fr0s7y on 2013-04-13
bash still isn't liking the empty array,
```

./delete.sh: 21: ./delete.sh: Syntax error: "(" unexpected
```

the file is sourced in my run.sh as follows:

 ```
  sh ./delete.sh
```

is this an error exclusive to the array command? I havent ran into any problems using this method so far :/

---

### Post by Vaphell on 2013-04-13
you explicitly call **sh** which is a very barebone shell. It doesn't know arrays so it takes them as syntax errors. Drop sh and let system figure proper shell according to the hashbang line (=bash).

---

### Post by fr0s7y on 2013-04-13
> **schragge said:**
> Look again at [post=12601487]my example above[/post].

there is a problem with the second 'do' , i tried nesting the while functions however it kept kicking me out of the script.

---

### Post by fr0s7y on 2013-04-13
> **Vaphell said:**
> you explicitly call **sh** which is a very barebone shell. It doesn't know arrays so it takes them as syntax errors. Drop sh and let system figure proper shell according to the hashbang line (=bash).
  this fixed it!!! thank you so much guys, the code now looks like:

```
#!/bin/bash -       
#title           :delete.sh
#description     :This script will delete an entry to the Address Book
#date            :April 2013
#version         :1.0
#==============================================================================


ADDRESSBOOK=~/Documents/Address-Book/add_data.txt

export ADDRESSBOOK

echo "=============================== Delete a Record ==============================="
echo "==============================================================================="
echo "============ Search A Record, then delete it! Type 'exit' to exit =============

"

exit=0
while
  read -p 'Find something for me to delete> ' searchTerm
  [[ $searchTerm != 'exit' ]]
do
  ifs=$IFS; IFS=$'\n'; searchOutput=( $(grep "$searchTerm" "$ADDRESSBOOK"| sort) ); IFS=$ifs
  if ((${#searchOutput[@]}>1)); then
    PS3="Select line to delete: "
    select line in "${searchOutput[@]}"; do
      [[ -z $line ]] && break
      echo Deleting $line
    done
  else
    echo Deleting $searchOutput
  fi
done
exit 0


```

I am tempted to give the array option a shot though, as always though if ain't broke don't fix it so I'll maybe hang on until I'm done and going over optimising bits here and there!

---

### Post by schragge on 2013-04-13
> **fr0s7y said:**
> I am tempted to give the array option a shot thoughWell, your code already uses an array :)

---

### Post by Vaphell on 2013-04-13
check if 
```
ifs=$IFS; IFS=$'\n'; searchOutput=( $(grep "$searchTerm" "$ADDRESSBOOK"| sort) ); IFS=$ifs
```
(IFS is changed globally and then restored which can cause trouble should you ever forget to restore - in other words not rock solid and idiotproof)
can be replaced with 
```
IFS=$'\n' searchOutput=( $(grep "$searchTerm" "$ADDRESSBOOK"| sort) )
```
(IFS is changed only in the scope of this line)

searchOutput is an array, as schragge said
its elements with indices:
```
for (( i=0; i<${**#**searchOutput[@]}; i++ )); do echo "searchOutput[$i] = '${searchOutput[$i]}'"; done
```

${#searchOutput[@]} returns number of elements, so the loop is "for index in (0..NUMBER_OF_ELEMS-1) get array[index]" (arrays are indexed from 0)

---

### Post by schragge on 2013-04-13
[size=-1]*Misleading post deleted.*[/size]

---

### Post by fr0s7y on 2013-04-13
wow arrays can get pretty complex huh!!

erm, unfortunately the problem isn't solved :'( 

although the code does run through and states it is deleting, it never actually deletes the line, I have been trying to integrate sed into the function
and nothiing so far has reaped success.
```

while
  read -p 'Find something for me to delete> ' searchTerm
  [[ $searchTerm != 'exit' ]]
do
  ifs=$IFS; IFS=$'\n'; searchOutput=( $(grep "$searchTerm" "$ADDRESSBOOK"| sort) ); IFS=$ifs
  if ((${#searchOutput[@]}>1)); then
    PS3="Select line to delete: "
    select line in "${searchOutput[@]}"; do
      [[ -z $line ]] && break
    sed "/$line/d" $ADDRESSBOOK 
      echo "Deleting line" $line
    done
  else
    echo "Deleting" $searchOutput
  fi
done
```

like i said it works fine apart from the actual deleting of the line, apparently this can be achieved through a mv command also, I am again confused!
Am I passing the right variable with $line?
I was under the assumption that $line was equal to the string so in essence i am telling sed to delete the line (name, name, address etc.) from the file $ADDRESSBOOK, makes sense?
apparently not as everytime I reload the file the record is still present, apparently I need to 'commit' the changes also?

Also, what is the 'PS3' variable doing? why not use read?

---

### Post by schragge on 2013-04-13
All you need is to add the **-i** option to sed: ```
sed -i "/^${line//\\/\\\\}\$/d" "$ADDRESSBOOK"
``` Also pay attention to proper quoting. This is still very unsafe as sed searches for a regular expression. Better find out the line number with fgrep and delete the line by number:
```

line=$(fgrep -nx "$line" "$ADDRESSBOOK")
sed -i ${line%%:*}d "$ADDRESSBOOK"

```

---

### Post by fr0s7y on 2013-04-13
> **schragge said:**
> All you need is to add the **-i** option to sed: ```
sed -i /"$line"/d "$ADDRESSBOOK"
``` Also pay attention to proper quoting.

worked perfect, i started panicking and throwing quotes around all sorts, oops. I havent used sed before.

Thanks again!! Is there a 'thanks' system on this forum?

---

### Post by schragge on 2013-04-13
I've edited my post. Please have a look at it again. Using sed like this is not safe.

---

### Post by schragge on 2013-04-13
> **fr0s7y said:**
> Also, what is the 'PS3' variable doing? why not use read?$PS3 stores prompt for the select statement. Why use *read* if you can use *select*?

---

### Post by fr0s7y on 2013-04-13
I've updated my code, what's the danger?

Also, if it wouldn't be too much trouble, could you give me a brief overview of how exactly the if statement acquires the variable, i'm ok with most concepts, its
the regular expressions like -z that confuse, ill quickly go over how much of it i understand




```

#im still unclear on how IFS, I've seen it used before while i was searching for a solution and apparently it ?splits? a FOR-Loop i am quite unclear on this

ifs=$IFS; IFS=$'\n'; searchOutput=( $(grep "$searchTerm" "$ADDRESSBOOK"| sort) ); IFS=$ifs 
# ok so If the searchOutput array position is ? less than 1 ? display the  contents of the array?
  if ((${#searchOutput[@]}>1)); then #  PS3 sets a custom select statement yes?, just read up on this, seems very appropriate for the use of this application
    PS3="Select line to delete: " 
#takes user input and selects line based on their choice
    select line in "${searchOutput[@]}"; do

#really dont know what -z does as a regular expression tried searching for it, totally in the dark :(       [[ -z $line ]] && break
    sed "/$line/d" $ADDRESSBOOK        echo "Deleting line" $line     done   else
```


i've added my thoughts as comments within the code, if you could spare a moment and let me know how close, far from the mark i am?

edit: yeah sorry the PS3 stores the prompt for the select statement, when should read be used then?

---

### Post by Vaphell on 2013-04-13
seriously  simplify this IFS thing out, because what you have currently is bug prone. If it's possible to localize such a change, do it. IFS is too important to mess it up by accident.
```
IFS=$'\n' searchOutput=( ... )
```


if ((${#searchOutput[@]}>1)) then ....
if length of searchOutput (number of elems) is > 1 then show menu (obviously there is no point in choosing when there is only 1 elem)
${array[@]} = all elems
${#array[@]} = number of elems
${!array[@]} = all indices of elems
${array[n]} = n-th element counted from 0


[ -z *string* ] check if zero-length
[http://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html](http://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html)

---

### Post by schragge on 2013-04-13
> **fr0s7y said:**
> I've updated my code, what's the danger?Lines from the address book may contain characters that are special to regular expressions (metacharacters). E.g. dot means "any character", so the command
```
sed /jane.dow/d
``` will delete both *jane.dow* and *janetdow*
> **fr0s7y said:**
> could you give me a brief overview of how exactly the if statement acquires the variable To begin with, what acquires the variable is not an if statement. Try to rewrite it like **Vaphell** suggested then probably it will be clearer:
```
IFS=$'\n' searchOutput=( $(grep "$searchTerm" "$ADDRESSBOOK"| sort) )
```
IFS is a special shell variable (input field separator). It contains a list of characters that separate fields. In this case array elements get separated by newline.
> ok so If the searchOutput array position is ? less than 1 ? display the  contents of the array?
${#searchOutput[@]} is number of elements in array. If there are more than one element we ask user to select one.
> PS3 sets a custom select statement yes?Yes, it sets a custom prompt for select statement.
> really dont know what -z does as a regular expressionIt is not a regular expression, it's an option to the test builtin. It means "true if the tested string is empty".
> yeah sorry the PS3 stores the prompt for the select statement, when should read be used then? The select statement does it for us, we do not need read in this case.

---

### Post by schragge on 2013-04-13
I guess a better solution would be using [mapfile]("http://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html#index-mapfile") aka *readarray*:
```

readarray -t searchOutput < <(grep "$searchTerm" "$ADDRESSBOOK" | sort)

```

---

### Post by fr0s7y on 2013-04-13
> **schragge said:**
> I guess a better solution would be using [mapfile]("http://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html#index-mapfile") aka *readarray*:
```

readarray -t searchOutput < <(grep "$searchTerm" "$ADDRESSBOOK" | sort)

```

This also works perfectly, and also thank you for the above comments, its a lot to take in when learning new commands. The code is much clearer now.

---

### Post by Vaphell on 2013-04-13
cool, i didn't know about readarray, i knew only about somewhat similar *read -a array*. I think i have to read about all builtins bash has.

```
IFS=$'\n' read -d'' -a arr < <( ... )
```

unfortunately in case of null-delimited inputs which are sometimes useful/necessary i think the only way is to fall back on *while read* and *array+=( elem )*

---

### Post by schragge on 2013-04-13
> **Vaphell said:**
> ```
IFS=$'\n' array=( $output )
```
IFS is changed locally only for the creation of array, so you don't have to save it and then restore it Only after you posted the example with *read -a*, it occured to me that the sentence above is wrong.

First, in this case two variables just get assigned, but there's no command word. IFS keeps the new value afterwards. Contrast it with
```
IFS=$'\n' read ...
``` where *read* is the command word (regular builtin, this  won't work with special builtins either), and the scope of IFS is restricted.

[s]And secondly, setting IFS won't affect the array assignment since all variables on the line get assigned first, and only then the new IFS value takes effect.[/s][highlight]Edit[/highlight] That is incorrect, see the next post by **Vaphell**.

See [POSIX]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_09_01") for reference.

---

### Post by Vaphell on 2013-04-13
yup, i failed hard :) quite ironic considering i warned against it :D this only shows how playing with IFS can backfire.
I didn't know one can do multiple assignments with only whitespace separating expressions... though when i think about it it makes sense, after all you can do IFS= LANG= SOMETHING_ELSE= some_command

array itself seems to work fine, despite that IFS blunder
```
$ x=$'a a\nb b\nc c'
$ unset IFS
$ array=( $x )
$ printf "%s\n" "${array[@]}"
a
a
b
b
c
c
$ IFS=$'\n' array=( $x )
$ printf "%s\n" "${array[@]}"
a a
b b
c c
```

---

### Post by sisco311 on 2013-04-14
@OP

You might want to check out BashFAQ 005 (link in my signature). It explains the differences between the different methods posted in this thread. ;)

---

### Post by fr0s7y on 2013-04-15
that is a mighty FAQ, bookmarked! I honestly didn't foresee so many ways to solve this, though as I am fairly new to performing these kinds of functions I'm just happy to get a result.

I did read that it's imperative to UNSET IFS after use and I'm still unclear as to how it can backfire? how bad is bad in this case? As mentioned above the preferred route is to use readArray, keeps the code looking clean too!!

---

