---
title: "[SOLVED] [Bash] Don't understand error in script!"
date: 2008-06-13
forum: Programming Talk
---

### Post by JupiterV2 on 2008-06-13
I get the following error with the code below:

**Error:**
```
./cd_app.sh: 1: Bad substitution
cut: you must specify a list of bytes, characters, or fields
Try `cut --help' for more information.

```

**Error with debug flags:**
```
+ [ 3 /tmp/cdb.7505 = 0 ]
+ echo
+ echo metallica :&#8722;
+ echo
+ cut &#8722;f 2&#8722; &#8722;d , /tmp/cdb.7505
./cd_app.sh: 1: Bad substitution
cut: you must specify a list of bytes, characters, or fields
Try `cut --help' for more information.
+ echo
+ set +vxu

```

**Full function:**

[PHP]list_tracks() {
	if [ "$cdcatnum" = "" ]; then
		echo "no CD selected yet"
		return
	else
		grep "^${cdcatnum}," $tracks_file > $temp_file
		num_tracks=$(wc -l $temp_file)
		set -vxu
		if [ "$num_tracks" = "0" ]; then
			echo "no tracks found for $cdtitle"
		else {
			echo
			echo "$cdtitle :&#8722;"
			echo
			cut -f 2- -d , $temp_file
			echo
		} | ${PAGER:&#8722;more}
		set +vxu
		fi
	fi
	get_return
	return
}[/PHP]

What I don't understand is why the code "cut -f 2- -d , $temp_file" works on the command line as intended but not from within the script! What am I doing wrong?

---

### Post by KingTermite on 2008-06-13
do you need quotes around the command?

---

### Post by ghostdog74 on 2008-06-13
use  awk
```

awk -F"," '{print $2}' /tmp/dfdfs

```

---

### Post by geirha on 2008-06-14
> **JupiterV2 said:**
> 
[PHP]
		} | ${PAGER:&#8722;more}
[/PHP]


It took me a while to figure out what this was doing. ${var:&# was unfamiliar to me. But then I realized it was an html-entity, and it was supposed to be ${PAGER:-more}. I doubt bash will understand the '&#8722;' symbol you are using, so change it to a regular '-'. It would be odd if that produced the error message you got though.

---

### Post by Martin Witte on 2008-06-14
```
martin@toshibap200:~$ echo 1,2,3| cut -d, -f2
2
martin@toshibap200:~$ echo 1,2,3|cut -f 2- -d ,
2,3
martin@toshibap200:~$ 

```

---

### Post by JupiterV2 on 2008-06-16
So weird...I guess something wacky went on when I was putting in the 'dashes' as geirha suggested. I retyped them and it works perfectly! Thanks!

---

