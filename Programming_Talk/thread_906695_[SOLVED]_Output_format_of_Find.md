---
title: "[SOLVED] Output format of Find"
date: 2008-08-31
forum: Programming Talk
---

### Post by king vash on 2008-08-31
I am writing a prefix adder script. Given a directory and a prefix it scans the directory looking for files without the prefix and add it. I am having some trouble scanning the folder. I know that eventually I will encounter a file or folder with spaces so I did not use my normal
```
	for name in $(find *)
	do
		echo $name
                code to check and add prefix
	done
```
I instead tried this.
```
	find "$1" -name "*" -type f| while read name
	do
                echo $name
                code to check and add prefix
	done
```

My code to prefix is
```
	if [ {name:0:$prefixlengh} = $2 ]
	then		
		echo "had prefix"
	else 
		echo "$name"
		echo "$prefix""$name"
		mv $name "$prefix""$name"
	fi
```
which works great if the file is formatted as "name.ext" but fails when the file is formatted as "./directory/to/file/name.ext"

What can I do about this?

---

### Post by nitro_n2o on 2008-08-31
you could try

filename = ./path/to/file.x
echo ${filename##*/} 

will give u file.x

try it out

---

### Post by weresheep on 2008-08-31
Hello,

You can use 'basename' and 'dirname' to strip the directory path / or the file name, from a given file name. It works like...

```

$ basename /foo/bar/file.txt
file.txt
$ dirname /foo/bar/file.txt
/foo/bar
$

```

so in your prefix checking code, perhaps you could do...

```

BASE="$(basename $name)"
DIR="$(dirname $name)"

if [ {BASE:0:$prefixlengh} = $2 ]
then		
    echo "had prefix"
else 
  echo "$BASE"
  echo "${prefix}${BASE}"
  mv $name "${DIR}/${prefix}${BASE}"
fi

```

I've not tested this, but hopefully you get the idea to be able to debug it 8-[

It might also be worth checking out 'rename' depending on how familiar you are with Perl regex.

-weresheep

---

