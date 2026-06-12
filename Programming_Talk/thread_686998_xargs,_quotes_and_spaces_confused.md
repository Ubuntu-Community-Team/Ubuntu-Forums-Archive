---
title: "xargs, quotes and spaces :confused:"
date: 2008-02-03
forum: Programming Talk
---

### Post by qazwsx on 2008-02-03
MY NEWBIE QUESTION:
For example:
arguments: arg1 arg 2 arg3 
there is space in the second argument

variable=`for arg in "$@"
do
	echo  "$arg" | grep -v 1
done | xargs -0`
echo $variable

So I would like to get out  "arg 2"  and"arg 3"on the same output line.
It prints the argument number 2 to the separate line with quotes.
Using plain xargs my output is three arguments instead of two. I also have  tried to use xargs  -I '{}'. and also  tried to insert extra quotes with sed but it didn't work like:
echo  "$arg" | grep -v 1|  sed -e 's/^/"/g'  -e 's/$/"/g'

Could someone help me with this?
Is there better to achieve this in bash shell?

Thanks

---

### Post by JamesUser on 2008-02-03
The snippet you have provided above prints "arg 2 arg3" on the same line.  At least, on my pc it does. What's the confusion?

---

### Post by qazwsx on 2008-02-04
> **JamesUser said:**
> The snippet you have provided above prints "arg 2 arg3" on the same line.  At least, on my pc it does. What's the confusion?
Looks like I did something else there :)
But
After that my arguments are: arg, 2 and arg3. Three instead of two. I need to preserve  quotes.

---

### Post by geirha on 2008-02-04
It's hard to understand what you really want to do. A few examples with some input arguments and the expected output would be helpful. Any reason why you can't just do ```
echo "$2 $3"
``` for example?

---

### Post by qazwsx on 2008-02-04
OK I am trying to filter  some of my arguments with that.
For example my files are
" one 1.ogg", "two2.mp3" and "three3.ogg"
Now I want to get rid of that mp3 file argument using different variable.

```
./script "one 1.ogg"  "two2.mp3" "three3.ogg"
```


Somewhere in the middle  I want to get my some of my variable output to be:  ```
"one 1.ogg"  "three3.ogg" .
```
As you know you can't just run program: ```
program  one 1.ogg  three3.ogg
``` It needs quotes . 

And this one cuts off the " or \.
```
variable=`for arg in "$@"
do
	echo  "$arg" | grep -v .mp3$
done | xargs -0`
echo $variable
```

I tried to double quotes with sed but it didn't work. I also tried to insert \ with sed as well.

---

### Post by erginemr on 2008-02-04
I don't know the details of it, but I know that the following code:
```
IFS=$'\n'
```
is used at the beginning of a shell script to handle the spaces correctly. 

Does it help with your case?

---

### Post by geirha on 2008-02-04
How about something like this then:
```

declare -a variable
for arg in "$@"; do
    if ! [[ "$arg" =~ '^.*\.mp3$' ]]; then
        variable=( "${variable[@]}" "$arg" )
    fi
done

echo "${variable[@]}"
for var in "${variable[@]}"; do
    echo \"$var\"
done

```

---

### Post by qazwsx on 2008-02-04
> **geirha said:**
> How about something like this then:
```

declare -a variable
for arg in "$@"; do
    if ! [[ "$arg" =~ '^.*\.mp3$' ]]; then
        variable=( "${variable[@]}" "$arg" )
    fi
done

echo "${variable[@]}"
for var in "${variable[@]}"; do
    echo \"$var\"
done

```
Thanks it seems to work.

---

