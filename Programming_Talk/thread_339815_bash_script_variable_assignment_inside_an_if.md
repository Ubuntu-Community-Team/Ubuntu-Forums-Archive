---
title: "bash script: variable assignment inside an if"
date: 2007-01-16
forum: Programming Talk
---

### Post by jordilin on 2007-01-16
I have the following:
```
if [ -f $NAME=$dir"/"$NEWNAME\_$j".jpg" ]
	then
		echo "file already exists"
		exit 0
	else
		echo $NAME
		mv $i $NAME
	fi
	let "j+=1"

```
but, I think that the NAME variable is not correct inside the if. Is there a way to do an assignment inside an if? Thanks

---

### Post by hal10000 on 2007-01-16
You may have to quote the $NAME 
```

if [ -f "$NAME"=$dir"/"$NEWNAME\_$j".jpg" ]

```

EDIT: I'm not too sure, but maybe you have to quote the $dir, $NEWNAME and $j variables too:

```

if [ -f "$NAME"="$dir""/""$NEWNAME"\_"$j"".jpg" ]

```
or a shorter version:
```

if [ -f "$NAME"="$dir\/$NEWNAME\_$j.jpg" ]

```

---

### Post by jordilin on 2007-01-16
thanks

---

