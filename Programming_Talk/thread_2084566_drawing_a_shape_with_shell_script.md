---
title: "drawing a shape with shell script"
date: 2012-11-15
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-15
I'm trying to draw a tree in the following form

```
    *    
   ***
  *****
 *******
*********
```

as you can see I need both spaces, and "*" stars in every line, but I can't get it quite the way I want
```
#!/bin/bash

display_tree() {
	local rows=$1
	local columns=$2

	for ((i=0; i<$rows; i++))
	do
		#spaces loop
		for ((j=0; j<$columns; j++))
		do
			echo -n " "
			#drawing tree loop
			for ((a=0; a<$(($i + 1)); a++))
			do
				echo -n "*"
			done
		done
	echo 
	done
}

if [ $# -eq 2 ]; then
	display_tree $1 $2
else
	echo "Usage: $0 rows columns"
fi



```

---

### Post by Vaphell on 2012-11-15
```
$ n=6; row="";
$ for(( i=0; i<n; i++ )); do row="$row "; done; row="${row%?}*"; for(( i=0; i<n; i++ )); do echo "$row"; row="${row#?}**"; done
     *
    ***
   *****
  *******
 *********
***********
```

---

### Post by Mia_tech on 2012-11-15
> **Vaphell said:**
> ```
$ n=6; row="";
$ for(( i=0; i<n; i++ )); do row="$row "; done; row="${row%?}*"; for(( i=0; i<n; i++ )); do echo "$row"; row="${row#?}**"; done
     *
    ***
   *****
  *******
 *********
***********
```

great job!.. would you mind explaining this two sentences

```
row="${row%?}*"
row="${row#?}**"
```
I know it is a variable declaration, but what's on the right side of "=" sign I haven't seen it yet

---

### Post by Vaphell on 2012-11-15
```
$ x="abcd"
$ echo ${x#[COLOR="Blue"]?[/COLOR]} ${x%[COLOR="Blue"]?[/COLOR]}
bcd abc
```
these parameter expansions trim chunks that match given [COLOR="Blue"]pattern[/COLOR] from the left (#) and from the right (%). ? symbol used here means 'single character'


first loop generates n spaces long string.
**${row%?}*** trims the rightmost char and adds * (last space replaced by *)
i get 1st row that way

note that (n+1)-th row has -1 space and +2 stars when compared to n-th row so in each iteration of the second loop i kill one space on the left, and add 2 *s on the right: **${row#?}****

---

### Post by Mia_tech on 2012-11-15
> **Vaphell said:**
> ```
$ x="abcd"
$ echo ${x#[COLOR="Blue"]?[/COLOR]} ${x%[COLOR="Blue"]?[/COLOR]}
bcd abc
```
these parameter expansions trim chunks that match given [COLOR="Blue"]pattern[/COLOR] from the left (#) and from the right (%). ? symbol used here means 'single character'


first loop generates n spaces long string.
**${row%?}*** trims the rightmost char and adds * (last space replaced by *)
i get 1st row that way

note that (n+1)-th row has -1 space and +2 stars when compared to n-th row so in each iteration of the second loop i kill one space on the left, and add 2 *s on the right: **${row#?}****

very efficient algorithm!..
Thanks

---

