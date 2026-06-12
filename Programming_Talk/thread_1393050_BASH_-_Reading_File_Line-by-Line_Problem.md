---
title: "BASH - Reading File Line-by-Line Problem?"
date: 2010-01-28
forum: Programming Talk
---

### Post by keepthisspam on 2010-01-28
Hey guys.. I'm new to Bash programming and I'm encountering this weird problem..
I'm trying to read a text file line-by-line and store into an array..
However, by using the WHILE-LOOP to read each line from file, the variables (normal var or arrays) doesn't seem to update..
The variables were automatically cleared upon exiting the WHILE-LOOP and revert back to it's previous state.

```

#!/bin/bash

clear; echo
x=10
echo "Original X: $x"
i=0
cat "test.txt" | while read FileLine
do
   MyArray[$i]="$FileLine"
   x=$(($x + 1))
   echo "Array ($i): ${MyArray[$i]}"
   
   i=$(($i + 1))
done

echo
echo "Array (*): ${MyArray
[*]}"
echo "No.of Elements: ${#MyArray
[*]}"
echo "Is X updated?: $x"
echo

```Contents of "test.txt"
```
line1 x
line2 y
line3 z
```The output in the terminal was:
```
Original X: 10
Array (0): line1 x
Array (1): line2 y
Array (2): line3 z

Array (*): 
No.of Elements: 0
Is X updated?: 10
```You can see that variable X was not updated and reverted back to 10.

Are they ways or workarounds to get the variables updated..?

---

### Post by kaibob on 2010-01-28
The reason your script doesn't work is explained in:

[http://mywiki.wooledge.org/BashFAQ/024](http://mywiki.wooledge.org/BashFAQ/024)

The script will work as follows:

```
#!/bin/bash

clear; echo
x=10
echo "Original X: $x"
i=0
cat "test.txt" | 
{
while read FileLine
do
   MyArray[$i]="$FileLine"
   x=$(($x + 1))
   echo "Array ($i): ${MyArray[$i]}"
   
   i=$(($i + 1))
done

echo
echo "Array (*): ${MyArray[*]}"
echo "No.of Elements: ${#MyArray[*]}"
echo "Is X updated?: $x"
echo
}
```

---

### Post by denarced on 2010-01-29
I've actually had this problem :)
At the time I couldn't figure it out and thought that if in bash you can't assign values to an array with loops, why even have arrays :D

Thanks for the enlightenment

---

