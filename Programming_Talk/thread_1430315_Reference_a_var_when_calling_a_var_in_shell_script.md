---
title: "Reference a var when calling a var in shell script"
date: 2010-03-15
forum: Programming Talk
---

### Post by Cheeselogs on 2010-03-15
The best way I can illustrate what I'm trying to do is with an example:


```
#!/bin/sh
opttest='Hello World'
i='test'

echo $opt$i
```Actual Output: test

Wanted output: Hello World

---

### Post by sisco311 on 2010-03-15
use an array:
```

opt[1]="whatever"
i=1
echo ${opt[$i]}

```[http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)

---

### Post by kaibob on 2010-03-15
I agree with sisco311 that an array is a good solution. If you are running Bash 4, which is included in Karmic, you can use an associative array:

[http://www.bash-hackers.org/wiki/doku.php/bash4](http://www.bash-hackers.org/wiki/doku.php/bash4)

BTW, to the best of my knowledge, the Dash shell does not support arrays, so you will have to change your shell script to Bash (#!/bin/bash).

---

### Post by slakkie on 2010-03-15
```

opttest='Hello World'
i='test'

eval echo '$opt'$i

```

There you go.

---

### Post by Cheeselogs on 2010-03-15
> **slakkie said:**
> ```

opttest='Hello World'
i='test'

eval echo '$opt'$i

```There you go.

Perfect! Thanks so much. 

To the other posters, I know that an array would work in this case, which is why I was careful to set i to a word rather than a number. In the actual context of the script I am writing, an array does not work, and I am actually using this in lieu of a hash table, which isn't supported with shell scripts.

---

### Post by soltanis on 2010-03-15
Yes, but there's no reason why that wouldn't work with a shell supporting associative arrays -- which bash does. You could use an outer eval thing but using an associative array works just as well.

---

### Post by Cheeselogs on 2010-03-16
Hit another slight wall, so I'll explain exactly what I'm trying to do in a lot more detail. 

* I created a menu
* The main menu stores the values of the submenus in an array. 
* The submenus are arrays of options
* I am trying to print the menu, and submenus in a generic header function to reduce code lines
* This is why using an array wouldn't solve my problem

Using eval, and the code above I was able to figure out that *eval echo $\{$somevar[@]\}* would work to print an array with a dynamic name. However, I can figure out how to get the array to print with tailing newlines. Traditionally I'd use a for loop to iterate through the items, but this wont work with the eval command.

The simplist form of what I am trying to achieve is below:

```
#!/bin/sh

menu1[1]='item 1'
menu1[2]='item 2'

a='test'

eval echo $\{$a[@]\} 

Output: 
'item 1 item 2'

Wanted output:
'item 1
item 2'
```Sorry I was so vague before.

---

### Post by Cheeselogs on 2010-03-17
Figured it out.

```
#!/bin/sh

test[1]="hello world\n"
test[2]='hi world\n'
bye[1]='goodbye world\n'
bye[2]='bye world\n'


a='test'

eval echo -e $\{$a[@]\}
```

---

### Post by geirha on 2010-03-17
Here's one without eval.

```

#!/bin/bash
test=( 
  [1]="Hello, World!"
  [2]="Hi, World."
)
a="test[@]"
printf "%s\n" "${!a}"

```

BTW, your hash-bang is wrong. POSIX sh does not define arrays, so you need to set it to bash instead of sh.

[http://mywiki.wooledge.org/BashFAQ/006](http://mywiki.wooledge.org/BashFAQ/006)

---

### Post by Rany Albeg on 2010-03-17
Maybe i didn't understand the question , but you echo $opt instead of $optest

You can also do 

```
optest='hello'
i='test'
var=$optest$i
echo "${var%$i}"
```

I hope i understand you correctly.

have a nice day.

---

