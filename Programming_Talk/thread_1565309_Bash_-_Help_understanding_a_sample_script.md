---
title: "Bash - Help understanding a sample script"
date: 2010-08-31
forum: Programming Talk
---

### Post by mendhak on 2010-08-31
Just beginning with bash, but having trouble understanding a specific example from [this page]("http://www.linuxconfig.org/Bash_scripting_Tutorial"). (Look at #8.2)

So this is the script:

```
#!/bin/bash
#Declare array
 declare -a ARRAY
#Open file for reading to array
exec 10
let count=0

while read LINE <&10; do

    ARRAY[$count]=$LINE
    ((count++))
done

echo Number of elements: ${#ARRAY[@]}
# echo array's content
echo ${ARRAY[@]}
# close file 
exec 10>&- 

```

The execution example given is:
[img]http://www.linuxconfig.org/images/Read-file-into-bash-array.gif[/img]

So the first problem is, the script doesn't run.  I've even created a bash.txt with 4 lines in it. 

> 
mendhak@ashenvale:~/Desktop$ cat bash.txt
a
b
c
d
mendhak@ashenvale:~/Desktop$ ./script.sh
./script.sh: line 5: exec: 10: not found


So...

1) What am I missing?  I'm not sure where in that script above it's opening the file.  I've also tried ./script.sh bash.txt
2) What is exec 10?
3) What is exec <&10 - I see it's in a loop, did the author mean < 10?
4) What is 10>&- ?


And finally

5) Do you think there's a better bash script tutorial to be following? 

Thanks for your time!

---

### Post by spjackson on 2010-08-31
> **mendhak said:**
> 
1) What am I missing?  I'm not sure where in that script above it's opening the file.  I've also tried ./script.sh bash.txt
2) What is exec 10?

That's a mistake in the example; it should be 
```
exec 10< bash.txt
```This opens the file and assigns it the file descriptor 10, which is then used to read file the file and then to close it.
> 
3) What is exec <&10 - I see it's in a loop, did the author mean < 10?
It isn't exec <&10, it's ```
while read LINE <&10; do
```and what it does is read from file descriptor 10, i.e. bash.txt.
> 
4) What is 10>&- ?
It closes the file, as per the comment on the line above.

---

### Post by mendhak on 2010-09-01
Thanks for that, makes sense now.  

I did a bit more searching and found (to my understanding) that the 10 is something akin to a file descriptor or a file handle.  It could be any other number (but not 1 and 2).  

The 

10 < bash.txt

indicates that the input for '10' should come from bash.txt rather than the keyboard.

---

