---
title: "getting: too many arguments error"
date: 2012-11-02
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-02
I have the following script and I'm getting: too many arguments error

```
#!/bin/bash

#creating new dir and copy files into it
create_dir() {
	if [ $# -eq 0 ]; then
		echo "Usage: $0 param1 param2"
	else
		echo "Making directory $1 and copying files..."
		mkdir $1
		for i in *
		do
			if [ -f $i ]; then
				cp $i $1/
			fi
		done
	fi
}

#count the number of files
count_files() {
	count=0
	for j in *
	do
		if [ -f $j ]; then
			count=$[ $count + 1 ]
		fi
	done
	echo "The total number of files is $count"
}

create_dir $1
count_files
```

error
```
john@xubuntu-vm:~$ ./test1.sh dir1
Making directory dir1 and copying files...
./test1.sh: line 12: [: too many arguments
./test1.sh: line 12: [: too many arguments
./test1.sh: line 12: [: too many arguments
./test1.sh: line 24: [: too many arguments
./test1.sh: line 24: [: too many arguments
./test1.sh: line 24: [: too many arguments
The total number of files is 10
```

the errors are happening at the if's statements...

---

### Post by spjackson on 2012-11-02
You will get this if you have file names with several words separated by spaces. You need to quote your variables. Instead of this:
```

			if [ -f $i ]; then

``` do this:
```

			if [ -f "$i" ]; then

``` and similarly for other uses of variables that may contain file names.

---

