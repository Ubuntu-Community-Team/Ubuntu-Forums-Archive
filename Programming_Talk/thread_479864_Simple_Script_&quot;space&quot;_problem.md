---
title: "Simple Script &quot;space&quot; problem"
date: 2007-06-20
forum: Programming Talk
---

### Post by KrazyPenguin on 2007-06-20
Here is a simple menu script but how do I get rid of the space
between Start and Backup?
Obviously I am getting three options listed instead of two:
Start
Backup
Quit

OPTIONS="Start Backup Quit"
           select opt in $OPTIONS; do
               if [ "$opt" = "Start Backup" ]; then
                echo "start backup"
                exit
               elif [ "$opt" = "Quit" ]; then
                echo done
               else
                clear
                echo bad option
               fi
           done

But I want Start Backup to be one option.
I am new to this and learning a little here and a little there.
I search google but couldn't find the answer.
Thanks.

---

### Post by linfidel on 2007-06-20
Did you try a backslash before the space?  That's one common way to enter spaces - the backslash "escapes" the space.

Just one blind man trying to lead another here. :)

---

### Post by HackingYodel on 2007-06-20
The easy way would be to change the space to either - or _

```
OPTIONS="Start-Backup Quit"

select opt in $OPTIONS; do
	if [ "$opt" = "Start-Backup" ]; then
		echo "start backup"
		exit
	elif [ "$opt" = "Quit" ]; then
		echo done
		exit
	else
		clear
		echo bad option
	fi
done
```

---

### Post by HackingYodel on 2007-06-20
The harder way:

If you don't feed the* in list* option to **select**, it takes its options from the command line arguments.
It just so happens that **set -- "Start Backup" Quit** will set $1 to *Start Backup* and $2 to *Quit*

Therefore:
```
set -- "Start Backup" Quit
 
select opt; do
	if [ "$opt" = "Start Backup" ]; then
		echo "start backup"
		exit
	elif [ "$opt" = "Quit" ]; then
		echo done
		exit
	fi
done
```
will get you an option with a space in it.  Also remember that if you set **PS3=** a string, the string will follow your menu as a prompt.
```
PS3="Begin backup now: "
set -- "Start Backup" "No, Quit"
select opt; do
	if [ "$opt" = "Start Backup" ]; then
		echo "Starting backup"
		exit
	elif [ "$opt" = "No, Quit" ]; then
		echo done
		exit
	fi
done
```

gets me:

```
1) Start Backup
2) No, Quit
Begin backup now: 1
Starting backup
```

Hope this helps!

---

