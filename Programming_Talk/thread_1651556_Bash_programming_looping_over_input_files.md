---
title: "Bash programming looping over input files"
date: 2010-12-23
forum: Programming Talk
---

### Post by tejas.deshpande on 2010-12-23
Hi,
I'm an absolute noob on bash programming and I wanted to do the following.

I write a solution for a programming contest problem. I have a few test cases (10 to be precise) named 1.in , 2.in , 3.in and so on and I have the correct outputs names 1.out, 2.out....

So what I want to be able to do is run my c++ program with sequential inputs from 1.in , 2.in etc and test the output given by my program with 1.in and compare it with 1.out (I figured I would have to use the 'diff' program).

I have written the code ```
for i in 'seq 1 10'; do ./The\ Siruseri\ Sports\ Stadium < $j.in > my$j.out; done 
```

but its giving .in is not a valid file name.


Also, I would also like to see for how much time program ran.

Thanks! :)

---

### Post by thk on 2010-12-23
You probably already found the typo, but notice that you loop over i and then use j in the "do" section. Also, you must use backticks around 'seq'. It should be something like

```
for i in `seq 1 10`
do
      ./The\ Siruseri\ Sports\ Stadium < ${i}.in > my${i}.out
done
```

---

### Post by Crusty Old Fart on 2010-12-25
> **tejas.deshpande said:**
> ...Also, I would also like to see for how much time program ran.

Thanks! :)
Here it is with the execution time duration you asked for, and my personal preference of a slightly different coding style:
```

!/bin/bash
set -e

start=$(date +%s.%N)

for i in $(seq 1 3); do
  ./The\ Siruseri\ Sports\ Stadium < $i.in > my$i.out
done

end=$(date +%s.%N)
duration=$(echo "$end - $start" | bc -l)
echo -e "\nScript execution time:" $(printf "%1.9f" $duration) "seconds.\n"

exit 0

```

---

### Post by v8YKxgHe on 2010-12-26
> Also, you must use backticks around 'seq'. It should be something like

The use of backticks should only be used when you're wanting compatibility with other (or older) shells. You pretty much always want to use $() over ``. Also, no need to use 'seq' when using Bash ...

```
#!/bin/bash
for i in {1..3}; do
    ./The\ Siruseri\ Sports\ Stadium < $i.in > my$i.out
done
exit 0
```

> **Crusty Old Fart said:**
> Here it is with the execution time duration you asked for, and my personal preference of a slightly different coding style:
```

!/bin/bash
set -e

start=$(date +%s.%N)

for i in $(seq 1 3); do
  ./The\ Siruseri\ Sports\ Stadium < $i.in > my$i.out
done

end=$(date +%s.%N)
duration=$(echo "$end - $start" | bc -l)
echo -e "\nScript execution time:" $(printf "%1.9f" $duration) "seconds.\n"

exit 0

```

Why use all that when 'time' exists?

```
time ./foo
```

---

### Post by Crusty Old Fart on 2010-12-26
[I][B][COLOR=Blue]Note to tejas: I reduced the count limit in your for statement to make only three loops so my code testing would be easier. I forgot to change it back to 10 when I posted. Sorry about that.[/COLOR]

[/B][/I]> **AlexC_ said:**
> The use of backticks should only be used when you're wanting compatibility with other (or older) shells. You pretty much always want to use $() over ``... 
Yup...That and it's a helluva lot easier for old eyes to read. I was so glad when I learned that those itty-bitty backticks could be replaced with: $(), especially when backticks are adjacent to single quotation marks.

> **AlexC_ said:**
> 
Also, no need to use 'seq' when using Bash ...
```
#!/bin/bash
for i in {1..3}; do
    ./The\ Siruseri\ Sports\ Stadium < $i.in > my$i.out
done
exit 0
```
Oooh...Thank you, AlexC. I didn't know about that one. I _LIKE_ it. 

> **AlexC_ said:**
> 
Why use all that when 'time' exists?

```
time ./foo
```
Two reasons:

[LIST=1]
[*]The code I wrote is internal to the script.
[*]It not only provides more precision (all the way down to nanoseconds) but is more accurate as well. (See "man time" for accuracy issues.)
[/LIST]
I reckon "foo" could be just like you have it in your code box, and then if custom formatting for the output from the "time" command was desired, a bash wrapper (e.g.: "foobar") could look something like this:
```

#!/bin/bash
/usr/bin/time -f "Script execution time: %e seconds." ./foo
exit 0

```and then...running "bash foobar" would give output similar to this:
Script execution time: 3.07 seconds.

But all this gymnastics, kind of defeats the quest for code brevity, which seems to be your intention by suggesting the "time" command.

Ultimately, it all comes down to what the customer wants. In this case, tejas was a little short on specifics. If he reads our posts, he'll have a few more choices, eh?

Thank you again for popping in here. You gave me a few things to add to my bag of tricks.

Crusty

---

