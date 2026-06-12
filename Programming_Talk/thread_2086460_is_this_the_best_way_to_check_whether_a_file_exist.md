---
title: "is this the best way to check whether a file exist or not"
date: 2012-11-21
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-21
is this a good way to check whether a file exist or not? and then delete it

```

echo -n "Enter file name: "
	read fileName
	for i in * 
	do
		if [ -f $i ] && [ $i == $fileName ]; then
			rm $fileName
		else
			echo "Error $fileName doesn't exist"
		fi
	done
```
when the file doesn't exist, I'm getting a bunch of errors b/c is in a loop, how could I make this more efficient?

Thanks

---

### Post by Vaphell on 2012-11-21
is that for loop supposed to do something else? because when you have a name, comparing it to every file in directory doesn't make much sense. Just attack the name directly.
```
read -p "enter file name: " fn
if [ -f "$fn" ]
then
  rm "$fn"
else
  echo "$fn doesn't exist"
fi
```

or even try to rm whatever is provided but silence stderr
```
rm "$fn" 2>/dev/null || echo "rm fail"
```

---

### Post by dwhitney67 on 2012-11-21
The -f option checks to ensure that the given name is a file or not.  However, it does not ensure that the user actually has privileges to do anything with the file.

You may want to employ the use of 'stat' to ensure that the current user also has permissions (ie ownership) of the file before attempting to remove it.

When the -f option reports "false", your script prints that the file does not exist.  You may want to consider reporting to the user that perhaps the name given represents a directory or other type of file (e.g. character special file).  If none of the above, then and only then, do you report that the file does not exist.

---

