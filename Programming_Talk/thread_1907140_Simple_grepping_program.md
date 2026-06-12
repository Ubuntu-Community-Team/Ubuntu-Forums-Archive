---
title: "Simple grepping program"
date: 2012-01-10
forum: Programming Talk
---

### Post by Eiji Takanaka on 2012-01-10
Hi guys/gals.  I'm pretty new to programming, just been playing with a few bash and perl scripts really.   I was wondering how i could go about writing a simple command line script to terminate (kill) a process.   

For example normally i would do this...  sudo ps -A | grep bladdehlah  then sudo kill -9 (process number).  How could i implement this in a simple bash script?   

The function i would need is upon grepping that process, to somehow locate the number of the process id on that line. then obviously you could simply append a && kill -9 function to the end of the script.  

So basically to cut a long story short after grepping, how would you then grab the pid from that line and pipe it into | kill -9?  Fairly simple one for you uber programmer dudes im sure, but its a simple step that i am currently unfamiliar with.  Cheers   - dan

---

### Post by sisco311 on 2012-01-10
pkill is not [POSIX]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html"), but it's installed on many Linux systems.

---

### Post by Eiji Takanaka on 2012-01-10
Hoho didn't know you could lookup process's by name =P. Thanks man.

For the record though how would you go about doing it the long roundabout way? 

I know its a bit of a moot point if pkill is available, but still might be worth knowing all the same =).

Thanks =)

---

### Post by sisco311 on 2012-01-10
If you want to use the output of **ps -A**, then check out BashFAQ 001 (link in my signature). 

If **bladdehlah** is not a regular expression, then I'd go with something like:
```
kill -9 $(pidof bladdehlah)

```

---

### Post by papibe on 2012-01-10
You can use a variable:
```
#!/bin/bash
pid=$(ps aux | grep bladdehlah | awk '{print $2}')
kill -9 "$pid"

```
Or you can put the expression right in there:
```
#!/bin/bash
kill -9 $(ps aux | grep bladdehlah | awk '{print $2}')
```
Even simpler if you use pgrep:
```
#!/bin/bash
kill -9 $(pgrep bladdehlah)
```
But there's a little caveat if there are several instances. For example:
```
$ ps aux | grep fire | awk '{print $2}'
1763
1836
6376

```
Then you would need to do something like:
```
#!/bin/bash
pids=$(ps aux | grep bladdehlah | awk '{print $2}')

for p in "$pids"
do
    kill -9 "$p"
done
```
But, the simplest way would be using the command 'killall':
```
killall bladdehlah
```
Does that helps?
Regards.

---

### Post by sisco311 on 2012-01-10
papibe, there is no need for grep or awk. You can use regular expressions in bash:
```
 ps -A | while read -r pid _ _ command; do
    if [[ $command =~ regex ]]; then 
        printf '%s\n' "$pid"
    fi
done

```


As a side note, awk can do everything(?) that grep can, so I wouldn't pipe grep into awk:
```
awk '/bladdehlah/{print $2}' < <(ps -A)
```

---

### Post by Eiji Takanaka on 2012-01-10
Thanks guys.  

Yea papibe that helps a lot thankyou, a very comprehensive answer.  

I tried the way using sudo kill -9 $(pgrep bladeblah) and it worked fine.  But i need to understand how and why that works so i have a bit of further reading ahead of me yet ;). 

It seems like the process in the brackets is a sub-routine? would that be a fair analogy?   I will look into the other methods of achieving the same results as well, as i think this is one of the first baby steps away from line by line scripting that i've currently been doing and towards "programming"  

Thanks all for your time.  - dan

P.s bloody no-script haha ;)

---

### Post by Telengard C64 on 2012-01-10
```

#! /bin/bash

if [[ -z "$1" ]]; then
    {
	echo "Program name required."
	echo "Kills all instances of the named program."
	echo "This is a really dumb implementation of \`pkill'."
	echo "Just use \`pkill' instead. srsly."
    } >&2
    exit 1
else
    kill -9 $( ps -C "$1" -o 'pid=' )
fi

```

---

### Post by sisco311 on 2012-01-10
> **Eiji Takanaka said:**
> 
It seems like the process in the brackets is a sub-routine?

That's an expansion. More precisely a command substitution. :)

If you want to learn more about bash/shell scripting, then check out the links from my signature.

---

### Post by sisco311 on 2012-01-10
> **Telengard C64 said:**
> ```

$ cat killer 
#! /bin/bash

if [[ -z "$1" ]]; then
        {
                echo "Program name required."
                echo "Kills all instances of the named program."
                echo "This is a really dumb implementation of \`pkill'."
                echo "Just use \`pkill' instead. srsly."
        } >&2
        exit 1
else
    kill -9 $( ps -C "$1" -o 'pid=' )
fi

```

fixed :)

error messages shall be redirected to stderr.

---

### Post by Eiji Takanaka on 2012-01-10
Cheers once again guys/gals just "man awk" 'ing at the mo. ;)

The only unknown part of that for me was the awk command..i see so print $2 relates to the second field....cool. 

Living and learning haha. ;)

---

### Post by Telengard C64 on 2012-01-10
> **sisco311 said:**
> fixed :)

error messages shall be redirected to stderr.

I confess I noticed that before posting, but was too lazy to fix it for such a useless script  :P

---

### Post by Eiji Takanaka on 2012-01-10
Forgive me if im wrong papibe, ive been reading the awk docu and experimenting....

 ps -A | grep Network | awk '{print $2}' returns a ? variable.

I think because the p.i.d field is on the far left that  

ps -A | grep Network | awk '{print $1}' seems to return the p.i.d number successfully. 

So i now have the process i.d number which is awesomeness.

O.k so now if i do.....sudo kill -9 $(ps -A | grep Network | awk '{print $1}')

and yesssss!

It works.

Haha well pleased with myself now ;) 

Thanks for the hints guys/gals!

---

### Post by Eiji Takanaka on 2012-01-10
Sweet!  

I just wrote this in nano and have created a very basic way of dropping both network manager and wpa_supplicant as a shell script. Which is exactly what i wanted to do ;).


#! /bin/bash

sudo kill -9 $(ps -A | grep Network | awk '{print $1}') && sleep 1

sudo kill -9 $(ps -A | grep wpa | awk '{print $1}') && sleep 1

echo "Done"

exit 0

Next step is.... if those processes are not running, how would i not execute the respective lines of code above...i'm guessing this is gonna involve an if statement? ;). Although i'm thinking it might be tricky because the commands are all chained with pipes?

---

### Post by Telengard C64 on 2012-01-11
> **Eiji Takanaka said:**
> 
#! /bin/bash

sudo kill -9 $(ps -A | grep Network | awk '{print $1}') && sleep 1

sudo kill -9 $(ps -A | grep wpa | awk '{print $1}') && sleep 1

echo "Done"

exit 0

Please use code tags. Please.

It is *never* necessary to pipe **grep** into **awk**.

```
grep Network | awk '{print $1}'
```

would be better written as

```
awk '/Network/ {print $1}'
```

---

