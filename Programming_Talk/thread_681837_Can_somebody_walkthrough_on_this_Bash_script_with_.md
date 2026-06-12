---
title: "Can somebody walkthrough on this Bash script with me?"
date: 2008-01-29
forum: Programming Talk
---

### Post by jingo811 on 2008-01-29
I'm trying to learn Bash from this guide.  And I'm having trouble understanding what each line does starting from the highlighted part.
[http://www.linuxconfig.org/Bash_scripting_Tutorial#Read_file_into_bash_array](http://www.linuxconfig.org/Bash_scripting_Tutorial#Read_file_into_bash_array)

Do I always use file descriptor number 10 when reading from a file?
What does "let count=0" mean?
How do I interpret the line "while read LINE <&10; do" in human language?

I have a thousand more questions but lets start from here and see how much I can interpret on my own after understanding the above codes.

[SIZE="4"] Read file into bash array[/SIZE]
```

#!/bin/bash
#Declare array 
declare -a ARRAY
#Open file for reading to array
[B]exec 10<bash.txt
let count=0

while read LINE <&10; do

    ARRAY[$count]=$LINE
    ((count++))
done[/B]

echo Number of elements: ${#ARRAY[@]}
# echo array's content
echo ${ARRAY[@]}
# close file 
exec 10>&-
```

---

### Post by Martin Witte on 2008-01-29
> **jingo811 said:**
> ```

[B]exec 10<bash.txt
let count=0

while read LINE <&10; do

    ARRAY[$count]=$LINE
    ((count++))
done[/B]

```
the exec command links a file descriptor to a file, so we can use the descriptor in this script. you can replace this snippet with
```

[B]
let count=0

while read LINE <bash.txt; do

    ARRAY[$count]=$LINE
    ((count++))
done[/B]

```
the descriptor can be any number where you have to keep in mind that 0 is used for stdin, 1 for stdout and 2 for stderr, see eg. [http://tldp.org/LDP/abs/html/x16355.html](http://tldp.org/LDP/abs/html/x16355.html) for more information on this subject

```
let count=0
``` assign zero to variable count
```
while read LINE <bash.txt; do
``` read a line from the file, store it into variable LINE. stop reading at end of file (that is the read will fail, so the while can not continue)

---

### Post by jingo811 on 2008-01-29
Tnx I see more clearly now!  When you compared the 2 equivalent code snippets. Can you explain what advantage there is in using the more complicated descriptor code over the more direct method?

Descriptor way.
```
exec 10<bash.txt
let count=0

while read LINE <&10; do
```

Direct way.
```
let count=0

while read LINE <bash.txt; do
```

---

### Post by jingo811 on 2008-01-29
[SIZE="4"]New problem.[/SIZE]

When running this script typing in the numbers 1-4 will give you the proper output.  But when you press 5 or above or 0 and below it doesn't give you the right response.
So I thought of trying to contain the error with the second script but it doesn't work like I want to.  What am I doing wrong?

[http://www.linuxconfig.org/Bash_scripting_Tutorial#Bash_Select](http://www.linuxconfig.org/Bash_scripting_Tutorial#Bash_Select)
```
#!/bin/bash

PS3='Choose one word: ' 

# bash select
select word in "linux" "bash" "scripting" "tutorial" 
do
  echo "The word you have selected is: $word"
# Break, otherwise endless loop
  break  
done

exit 0

```


I browned out the stuff that I added and got this error.
```
bill@gates:~/bash/Lesson_01$ **./select.sh **
./select.sh: [COLOR="Red"]line 5[/COLOR]: =: No such file or directory
./select.sh:[COLOR="Red"] line 8[/COLOR]: [: one: binary operator expected
```

```

#!/bin/bash

	PS3='Choose one word: ' 

[COLOR="Sienna"]if [COLOR="Red"][ $PS3 <= 0 ][/COLOR] ; then
	echo "You must type a number between 1-4!"
	PS3='Choose one word: '
elif [COLOR="Red"][ $PS3 > 4 ][/COLOR] ; then
	echo "You must type a number between 1-4!"
	PS3='Choose one word: '
else[/COLOR]
	# bash select
	select word in "linux" "bash" "scripting" "tutorial" 
	do
		echo "The word you have selected is: $word"
		# Break, otherwise endless loop
		break  
	done
[COLOR="Sienna"]fi[/COLOR]

exit 0
```

---

### Post by mssever on 2008-01-30
> **jingo811 said:**
> Can you explain what advantage there is in using the more complicated descriptor code over the more direct method?
Personal preference, I guess. But when bash scripting gets more complicated, it's probably time to switch languages (my personal favorite is Ruby).
> ```
let count=0
```You can drop the let. You only need it if you want to do math directly. But it's much easier to do math in double parentheses-- eg ```
count=1
((count++))
```> **jingo811 said:**
> ```
[COLOR=Sienna]if [COLOR=Red][ $PS3 <= 0 ][/COLOR] ; then
[COLOR=Black] <snip>[/COLOR]
elif [COLOR=Red][ $PS3 > 4 ][/COLOR] ; then[/COLOR]
```
You can't use standard boolean options in bash when comparing numbers. Use these:[LIST]
[*]for > use -gt
[*]for < use -lt
[*]for >= use -ge
[*]for <= use -le
[*]for == use -eq
[*]for != use -ne
[*]for && use -a
[*]for || use -o[/LIST]

---

### Post by jingo811 on 2008-01-30
Ah that's right Arithmetic and String comparisons uses different syntaxes.  Matlab my first language I think was more forgiving when using comparison syntaxing.

Tnx for that and all the other heads up tips.  I'm in the tunnel now and following the bright light at the other end :)


......not anymore GOD kicked me out of the tunnel after 3 minutes.

```
./select.sh: [COLOR="Red"]line 7[/COLOR]: [: too many arguments
./select.sh: [COLOR="Red"]line 10[/COLOR]: [: too many arguments
```

```
#!/bin/bash

NUM1=0
NUM2=4
	NUM3='Choose one word: ' 

[COLOR="Red"]if [ $NUM3 -le $NUM1 ] ; then[/COLOR]
	echo "You must type a number between 1-4!"
	NUM3='Choose one word: '
[COLOR="Red"]elif [ $NUM3 -gt $NUM2 ] ; then[/COLOR]
	echo "You must type a number between 1-4!"
	NUM3='Choose one word: '
else
	# bash select
	select word in "linux" "bash" "scripting" "tutorial" 
	do
		echo "The word you have selected is: $word"
		# Break, otherwise endless loop
		break  
	done
fi

exit 0
```

```
# Is this user input prompt specific to the bash select function?
	
[COLOR="Sienna"]NUM3='Choose one word: ' [/COLOR]

# Can I replace the above code with this instead or does this only save inputs
# as strings and not arithmetic numbers?

[COLOR="Sienna"]echo -e "Choose one word: \c "
read  WORD
NUM3=$WORD
[/COLOR]
```

---

### Post by pmasiar on 2008-01-30
As msserver suggested, when you have loops or any logic, it's about time to swith to languages. To Python, naturally :-)

[php]
words = [ 'linux', 'python', 'scripting', 'tutorial']
print 'select from words:', words
print 'press Ctrl+C to quit'
while True:
    number = input('chose number 1-4:')
    if (number < 1) or (number >4):
        print "between 1-4"
        continue
    print 'you choose:', words[number-1] # arrays start from 0

[/php]

---

### Post by mssever on 2008-01-30
> **pmasiar said:**
> As msserver suggested, when you have loops or any logic, it's about time to swith to languages. To Python, naturally :-)Or to Ruby :)
```
words = %w[linux ruby scripting tutorial]
begin
  puts "Choose a word: #{words.join ', '}"
  print "Type a number between 1 and #{words.length}: "
  choice = words.fetch(gets.to_i - 1) # Array#[] returns nil if the index doesn't exist. Array#fetch raises IndexError
rescue IndexError
  puts "Invalid selection. Please try again."
  retry
end
puts "You chose #{choice}"
```

EDIT: By the way, I don't mind doing loops or if statements in bash. I draw the line based more on complexity. If I need to use files in more than a trivial way, bash is inadequate. Also, bash's support for regular expressions is pitiful (mostly involving sed, which really isn't worth learning), so for regex support I use Ruby.

---

### Post by mssever on 2008-01-30
> **jingo811 said:**
> ```
./select.sh: [COLOR=Red]line 7[/COLOR]: [: too many arguments
./select.sh: [COLOR=Red]line 10[/COLOR]: [: too many arguments
``````
#!/bin/bash

NUM1=0
NUM2=4
    NUM3='Choose one word: ' 

[COLOR=Red]if [ $NUM3 -le $NUM1 ] ; then[/COLOR]
```
Bash is really anxious to expand variables. That means that bash sees your if statement as ```
if [ Choose one word: -le 0 ]; then
```Surround any variable name that might possibly contain spaces or other special characters AT ANY TIME with double quotes every time you call it. For example: ```
if [ "$NUM3" -le "$NUM1" ]; then
``` Note that the double quotes aren't strictly necessaty around $NUM1, but they don't hurt anything, and it's a good idea to simply make a habit of using them.

EDIT: You're comparing the value of a string to 0, which will give an error even if you make the changes I suggested. If you want $NUM3 to contain user input, you should do something like ```
read NUM3
```

---

### Post by jingo811 on 2008-01-30
So what you guys are saying is that I can't do the sort of error catching in Bash like you did with your Python and Ruby codes?......................................(trying out the suggested codes right now!)

> **mssever said:**
> 
EDIT: ..........
..........
 Also, bash's support for regular expressions is pitiful (mostly involving sed, which really isn't worth learning), so for regex support I use Ruby.

And here I thought that the intended use for Bash was dealing with regular expressions.  Lucky for me you mentioned this.  However our teacher did mention sed being a relic from the past.
[http://en.wikipedia.org/wiki/Comparison_of_programming_languages#Usage](http://en.wikipedia.org/wiki/Comparison_of_programming_languages#Usage)
(Bash not mentioned in this Wiki)

> The standard shell for Linux, based on the original Unix Bourne shell. According to its man page, BASH is "ultimately intended" to be POSIX compliant.
[http://www.oreilly.com/catalog/debian/chapter/book/ch13_01.html](http://www.oreilly.com/catalog/debian/chapter/book/ch13_01.html)

I didn't really understand what the Wiki said about POSIX but could I say that the intended use for Bash is POSIX whatever that means?

---

### Post by jingo811 on 2008-01-30
This is the closest I could get with the ERROR catching.  There's not much control in displaying customized error messages.  But Bash gets the job done.
Also I win the shortest code-lines contest!  (With some major help from **mssever** of course.)

[LIST]
[*]Ruby - [COLOR="Red"]10[/COLOR] lines of codes
[*]Python - [COLOR="Red"]9[/COLOR] lines of codes
[*]Bash - [COLOR="Red"]8[/COLOR] lines of codes (empty "echos" doesn't count they're just cosmetics) :)
[/LIST]

**Bash**
```

#!/bin/bash
echo
echo '* To exit press "Ctrl+C".'
echo '* View menu just press "ENTER".'
echo
	KIRK="Choose: "
	select SPOCK in "Linux" "Bash" "Scripting" "Tutorial"
	do echo "The word you have selected is: $SPOCK" 
	done
exit 0

```

**Python**
```

words = [ 'Linux', 'Python', 'Scripting', 'Tutorial']
print 'select from words:', words
print 'press Ctrl+C to quit'
while True:
    number = input('chose number 1-4:')
    if (number < 1) or (number >4):
        print "between 1-4"
        continue
    print 'you choose:', words[number-1] # arrays start from 0

```

**Ruby**
```

words = %w[Linux Ruby Scripting Tutorial]
begin
  puts "Choose a word: #{words.join ', '}"
  print "Type a number between 1 and #{words.length}: "
  choice = words.fetch(gets.to_i - 1) # Array#[] returns nil if the index doesn't exist. Array#fetch raises IndexError
rescue IndexError
  puts "Invalid selection. Please try again."
  retry
end
puts "You chose #{choice}"

```

---

### Post by mssever on 2008-01-30
> **jingo811 said:**
> So what you guys are saying is that I can't do the sort of error catching in Bash like you did with your Python and Ruby codes?......................................(trying out the suggested codes right now!)Bash is based on (and backwards compatible with) sh, which is the original UNIX shell. So some on the ways it does things are a bit outdated. Bash doesn't have exceptions. The best you can do with bash is to examine the exit status of every command.

> And here I thought that the intended use for Bash was dealing with regular expressions.  Lucky for me you mentioned this. Bash's [[ operator has limited regex support. e.g., ```
if [[ "$somevar" =~ [a-z] ]]; then
```I don't remember if that's quite the proper syntax, but it's close. Ruby's regex support is much easier to use. Python has similar regex support to Ruby, but in my opinion, Ruby's regexes are much easier to use.
> I didn't really understand what the Wiki said about POSIX but could I say that the intended use for Bash is POSIX whatever that means?POSIX is a standard that all UNIX-like systems are supposed to comply with (such as Linux, *BSD, MacOS--from the terminal, at least--, Solaris). The POSIX shell is actually sh, but on most Linux systems, calling the shell as sh actually invokes bash, but makes bash behave like the traditional sh.
> **jingo811 said:**
> 
Also I win the shortest code-lines contest!  (With some major help from **mssever** of course.)[LIST]
[*]Ruby - [COLOR=Red]10[/COLOR] lines of codes
[*]Python - [COLOR=Red]9[/COLOR] lines of codes
[*]Bash - [COLOR=Red]8[/COLOR] lines of codes (empty "echos" doesn't count they're just cosmetics) :)[/LIST]Of course, the shortest program might not be the easiest to understand. Perl programmers love compressing a whole bunch of code into one line, but that code is a lot harder to understand and debug.

Note also that pmasiar and I followed quite different approaches that affected the number of lines. If either of us refactored our code to use the same approach as the other, the number of lines would be quite similar if you don't count Ruby's end statement which has no Python equivalent.

Before I learned Ruby, I used to do a lot of Bash scripting. But now, I've found that a number of problems that are difficult to solve in bash are trivial in Ruby. Plus, Ruby has exceptions, which make error handling much easier. I once wrote a Bash script to simplify listing processes. It simply provided a shortcut to ```
ps -ef | grep foo | grep bar
```When I upgraded to Gutsy, something changed in Bash that caused errors in my script. After trying in vain to fix my script, I rewrote it in Ruby. The rewritten version took about twice the number of lines, but the code was a lot clearer and more straightforward. So in the end it was a win.

---

### Post by ghostdog74 on 2008-01-30
> **jingo811 said:**
> [SIZE="4"]New problem.[/SIZE]

When running this script typing in the numbers 1-4 will give you the proper output.  But when you press 5 or above or 0 and below it doesn't give you the right response.
So I thought of trying to contain the error with the second script but it doesn't work like I want to.  What am I doing wrong?

[http://www.linuxconfig.org/Bash_scripting_Tutorial#Bash_Select](http://www.linuxconfig.org/Bash_scripting_Tutorial#Bash_Select)
```
#!/bin/bash

PS3='Choose one word: ' 

# bash select
select word in "linux" "bash" "scripting" "tutorial" 
do
  echo "The word you have selected is: $word"
# Break, otherwise endless loop
  break  
done

exit 0

```


I browned out the stuff that I added and got this error.
```
bill@gates:~/bash/Lesson_01$ **./select.sh **
./select.sh: [COLOR="Red"]line 5[/COLOR]: =: No such file or directory
./select.sh:[COLOR="Red"] line 8[/COLOR]: [: one: binary operator expected
```

```

#!/bin/bash

	PS3='Choose one word: ' 

[COLOR="Sienna"]if [COLOR="Red"][ $PS3 <= 0 ][/COLOR] ; then
	echo "You must type a number between 1-4!"
	PS3='Choose one word: '
elif [COLOR="Red"][ $PS3 > 4 ][/COLOR] ; then
	echo "You must type a number between 1-4!"
	PS3='Choose one word: '
else[/COLOR]
	# bash select
	select word in "linux" "bash" "scripting" "tutorial" 
	do
		echo "The word you have selected is: $word"
		# Break, otherwise endless loop
		break  
	done
[COLOR="Sienna"]fi[/COLOR]

exit 0
```

forget what others say for now. What you want to do can be done in bash.  Personally, i find case/esac construct and while loop neater.
```

cat << EOF
    1) Linux
    2) bash
    3) scripting
    4) tutorial  
    5) Quit  
EOF
while true
do
    printf "Choose one: "
    read choice
    case $choice in 
    [1-4]) echo "you chose $choice";;
    0|5) break;;  
    *) echo "Yikes ! Try again" ;;
    esac
done    

```
After you get tired of bash, you can explore the rest

---

### Post by Martin Witte on 2008-01-31
> **ghostdog74 said:**
> forget what others say for now. What you want to do can be done in bash.  Personally, i find case/esac construct and while loop neater. After you get tired of bash, you can explore the rest

I fully agree with this. Besides this some organizations do not give access to python, ruby or other 'higher' languages, so good knowledge of scripting can be valuable if you end up working in one of these.

---

### Post by mssever on 2008-01-31
> **Martin Witte said:**
> I fully agree with this. Besides this some organizations do not give access to python, ruby or other 'higher' languages, so good knowledge of scripting can be valuable if you end up working in one of these.

Yes, a good knowledge of Bash has its value. But not for the reasons you mention. Practically every *nix system at least has Perl <shudder>, which was designed to help system administrators with more complex tasks. Nearly every modern system has Python, and possibly Ruby. So you don't have to learn Bash for system compatibility. (By the way, POSIX specifies sh, not bash, so not every bash trick would necessarily be portable, anyway.)

An example where some knowledge of Bash is important: creating .deb packages. .deb packages often contain maintainer scripts, which are supposed to be written in bash.

In short, I think that it's valuable to know many different languages, including bash. But I also know that a lot of people who know bash--myself included, at one time--waste a lot of time trying to make something work in bash, when that particular problem would be a lot simpler in another language. Remember, the right tool for the job. But you won't choose a tool if you don't know it.

---

### Post by jingo811 on 2008-02-01
> **ghostdog74 said:**
> forget what others say for now. What you want to do can be done in bash.  Personally, i find case/esac construct and while loop neater.
```

cat << EOF
    1) Linux
    2) bash
    3) scripting
    4) tutorial  
    5) Quit  
EOF
while true
do
    printf "Choose one: "
    read choice
    case $choice in 
    [1-4]) echo "you chose $choice";;
    0|5) break;;  
    *) echo "Yikes ! Try again" ;;
    esac
done    

```
After you get tired of bash, you can explore the rest

Tnx that's some nice coding.

---

### Post by jingo811 on 2008-02-05
[SIZE="4"]New problem, number 2[/SIZE]

I'm having a looping problem this time the 2 codes below was initially run in the opposite order.  But that made the program jump out before doing it's entire job.
So I'm trying to solve it by making this line into a NOT thingy if the $directory doesn't exist yet.
```
if [ -d $directory ]; then 
```
So that it creates the proper direcotry the first time then the next time the script checks it should jump to the ELSE part and do its job and then finish.



[PHP]#!/bin/bash


directory="/home/`whoami`/bash/temp99"
if [ -d $directory ]; then       # -----> How do I make this into a NOT thingy?



        # If directory does not exists it will be created.
        #
        echo "Directory does not exists. '/home/`whoami`/bash/temp99'"
        echo "It will be created automatically."
        mkdir /home/`whoami`/bash/temp99



else
# Check if directory exists.  If it does then copy the selected file types to
# predetermined location.
#
        echo "Directory exists. '/home/`whoami`/bash/temp99'"
        echo -e "Type in file type to search: \c "
        read word
        LIST=`find / -name \*.$word`
        cp $LIST /home/`whoami`/bash/temp99
        break
fi

                done[/PHP]


Manpages says this but I can't find the opposite expression?
```

       -d file
              True if file exists and is a directory.
```

And I don't see how I can use this one for my script?
```
       string1 != string2
              True if the strings are not equal.
```

---

### Post by mssever on 2008-02-05
> **jingo811 said:**
> [php]directory="/home/`whoami`/bash/temp99"[/php]
Or, ```
directory="$HOME/bash/temp99"
```
> [php]if [ -d $directory ]; then       # -----> How do I make this into a NOT thingy?[/php]
```
if [ ! -d "$directory" ]; then
```

(By the way, you'll save yourself headaches if you always quote variables and strings that might ever contain spaces.)

> And I don't see how I can use this one for my script?
```
       string1 != string2
              True if the strings are not equal.
```

I don't see where you would need this in your script.

---

### Post by jingo811 on 2008-02-06
Tnx mssever the script works like I want it to now. :)

---

