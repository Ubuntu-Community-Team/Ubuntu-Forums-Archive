---
title: "Shell Scripting Question"
date: 2008-10-23
forum: Programming Talk
---

### Post by 420shaggy on 2008-10-23
Hello all,
  I am trying to make a simple shell script to read the input from netstat as it comes, and when it identifies foreign ip address' to then fork and run a nmap on the "intruder(s)."  I can't seem to get a continuous read from netstat to work however.  Maybe someone is a bit more experienced and could show me where I went wrong?

```

while netstat -t | read -e x > temp 
do  
	grep -o "[0-9][0-9][0-9]*\-[0-9]*\-[0-9]*\-[0-9]" temp > ttemp 
	for i in {0..2}
	do
		cut -f $i -sd\- ttemp >> Ttemp			 
		echo "." >> Ttemp
	done 
	cut -f 1-4 -sd\. Ttemp | nmap
done

#( I know it is silly to use 3 temp files but I am tired and it is easy )

``` 

That is where I am currently stuck

---

### Post by ghostdog74 on 2008-10-23
```

netstat -tn|awk 'NR>2{  
    sub(/:.*/,"",$5)
    cmd="nmap -sS "$5
    while ( cmd |getline line){
        print line
    }
    close(cmd)
}'


```

---

### Post by 420shaggy on 2008-10-23
Thx for the reply, it worked perfectly.  I am new to awk completely though.  Any suggestions as to a good place to start reading for information about awk programming?

---

### Post by 420shaggy on 2008-10-23
nvm I just noticed the link in your signature hehe :lolflag:

---

### Post by geirha on 2008-10-23
For the sh approach, you could do something like this:
```

#!/bin/sh
tmp=`tempfile`   # Create a temporary file (in /tmp)

# tail -n +3 starts reading on line three, i.e. skips the first two lines
# tr -s ' ' squeezes all space into just one space, to make it easier for cut
# cut -d ' ' -f5 cuts out the fifth field seperated by spaces
# cut -d ':' -f1 cuts away the port number
netstat -tn | tail -n +3 | tr -s ' ' | cut -d ' ' -f5 | cut -d ':' -f1 >"$tmp"

while read ip; do
  nmap -sS $ip
done < "$tmp"

rm "$tmp"   # Clean up

```

Not nearly as short and sweet as ghostdog's awk. Using bash arrays would make it a bit shorter though.

---

### Post by ghostdog74 on 2008-10-23
the shell method can be done without much external tools
```

netstat -tn | while read line
do
  case $line in
    tcp*) 
        set -- $line
        nmap -sS ${5%:*}
        ;;
  esac
done

```

---

### Post by geirha on 2008-10-23
As usual, ghostdog stops by and ruins my nice shell scripts by making them shorter and better :) 

I know you can change the shell's arguments with set, but it just didn't enter my mind. Thanks for reminding me :)

---

### Post by ghostdog74 on 2008-10-23
just different ways of doing things that's all :)
anyway, there's no need for set as well. since we can do
```

netstat -tn | while read a b c d e f
..
...

```

---

### Post by 420shaggy on 2008-10-23
Thanks for the replies, they are really helping me get a better understanding of the versatility of the shell.

As for ghostdog's reply to geirha, I am still puzzled:

```
 nmap -sS ${5%:*} 
```

So it will nmap the value of the 5th argument with 0 or more colons afterwards?  

Also in the set command, what is the "--"?  I assume that it points to the shells arguments as the variable to set?

---

### Post by geirha on 2008-10-23
> **420shaggy said:**
> Thanks for the replies, they are really helping me get a better understanding of the versatility of the shell.

As for ghostdog's reply to geirha, I am still puzzled:

```
 nmap -sS ${5%:*} 
```

So it will nmap the value of the 5th argument with 0 or more colons afterwards?  

It's not a reg ex, it's a pattern. the % means cut away pattern (:*) from the end of the var. So it removes the port number. It's described under the "Parameter Expansion" section in bash's man-page.

> **420shaggy said:**
> 
Also in the set command, what is the "--"?  I assume that it points to the shells arguments as the variable to set?

-- is a special argument commonly accepted by GNU applications. It means that everything behind this should not be parsed as options, but treated as arguments. For example, if you have a file named "-foo", and you want to list its content with cat:
```
$ echo hello > -foo
$ cat -foo
cat: invalid option -- f
Try `cat --help' for more information.
$ cat -- -foo
hello

```

---

### Post by 420shaggy on 2008-10-23
Thank you geirha for the response, it was most helpful \\:D/

---

