---
title: "Shell Error"
date: 2010-06-20
forum: Programming Talk
---

### Post by huangyingw on 2010-06-20
Hello all,
	I am encountering with this problem.
	Bellowing is my content of fake.sh
	```

	#! /bin/bash
function check_disk
{
	result=1
	for file in `cat lv_list.txt`
	do
		if ! (lvdisplay|grep -q ${file})
		then   
    	echo ${file}
	 	fi
	done
	echo $result
}

check_bool=`check_disk`

if [ $check_bool -eq 1 ];   
then
	echo the disks ready!!!
else
 	echo the disks not ready!!!
fi
	
```
	The output of this shell is 
	```

	./fake.sh: line 17: [: too many arguments
the disks not ready!!!
	
```
	Line 17 is 
	```

	if [ $check_bool -eq 1 ];   
	
```

---

### Post by simeon87 on 2010-06-20
I just copied that script plus I created a file called lv_list.txt but I'm not getting that error. My lv_list.txt is empty however.. perhaps it has to do with the contents? Perhaps you're now reading the contents and supplying too many arguments to whatever you're doing in your function? I'm just using general programming knowledge here as I'm not that familiar with all this.

---

### Post by huangyingw on 2010-06-20
> **simeon87 said:**
> I just copied that script plus I created a file called lv_list.txt but I'm not getting that error. My lv_list.txt is empty however.. perhaps it has to do with the contents? Perhaps you're now reading the contents and supplying too many arguments to whatever you're doing in your function? I'm just using general programming knowledge here as I'm not that familiar with all this.
Thank you for doing so..My update my lv_list.txt 
is as bellow:
```

/dev/ubuntu/volgrp
/dev/ubuntu/back1
/dev/ubuntu/back2
/dev/ubuntu/archive1
/dev/ubuntu/archive2
/dev/ubuntu/archive3

```
And I find that if I delete the for loop:
```

for file in `cat lv_list.txt`
	do
		echo some
	done

```
This one would not reproduce that annoying error:
```

#! /bin/bash
function check_disk
{
	result=1
	
	echo $result
}

check_bool=`check_disk`

if [ $check_bool -eq 1 ];   
then
	echo the disks ready!!!
else
 	echo the disks not ready!!!
fi

```

---

### Post by Martin Witte on 2010-06-20
The use of the lvdisplay command seems wrong to me. The [man page]("http://linux.die.net/man/8/lvdisplay") learns you have to give a logical volume path as argument, the you can search the output for certain strings with grep. I don't have lvm running on my 
machines, so I can not provide an example

---

### Post by geirha on 2010-06-20
I think what you're trying to do is:
```

#! /bin/bash
check_disk()
{
    local return=0 lvoutput=$(lvdisplay) file
    while read -r file; do
        if [[ "$lvoutput" != *"$file"* ]]; then
    	    echo "$file"
            return=1
        fi
    done < lv_list.txt
    return "$return"
}

if files=$(check_disk); then
   echo "the disks are ready"
else
   printf "%s\n" "the following are not ready:" "$files"
fi

```

The reason for the error you got is because you gave [ too many arguments. E.g. if two of the files were output by your check_disk function, then check_bool would contain something like: $'/dev/ubuntu/back1\n/dev/ubuntu/back2\n1'

And so ```
[ $check_bool -eq 1 ]
``` would expand to ```
[ /dev/ubuntu/back1 /dev/ubuntu/back2 1 -eq 1 ]
```. If you try that you'll see you get the same error, and that's because you didn't quote the parameter expansion. "$check_bool", not $check_bool. After quoting it though, you'd have another problem because -eq requires a number on each side ... you're giving it a string.

I recommend you read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide), you have alot to learn.

---

### Post by huangyingw on 2010-06-21
> **geirha said:**
> I think what you're trying to do is:
```

#! /bin/bash
check_disk()
{
    local return=0 lvoutput=$(lvdisplay) file
    while read -r file; do
        if [[ "$lvoutput" != *"$file"* ]]; then
    	    echo "$file"
            return=1
        fi
    done < lv_list.txt
    return "$return"
}

if files=$(check_disk); then
   echo "the disks are ready"
else
   printf "%s\n" "the following are not ready:" "$files"
fi

```

The reason for the error you got is because you gave [ too many arguments. E.g. if two of the files were output by your check_disk function, then check_bool would contain something like: $'/dev/ubuntu/back1\n/dev/ubuntu/back2\n1'

And so ```
[ $check_bool -eq 1 ]
``` would expand to ```
[ /dev/ubuntu/back1 /dev/ubuntu/back2 1 -eq 1 ]
```. If you try that you'll see you get the same error, and that's because you didn't quote the parameter expansion. "$check_bool", not $check_bool. After quoting it though, you'd have another problem because -eq requires a number on each side ... you're giving it a string.

I recommend you read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide), you have a lot to learn.
Thank you for pointing out the root cause. I have a previously lucky success example of check_disk in back.sh as bellow. And the back.sh works well.
```

function check_disk
{
	check_file=/root/disk_list.txt
	result=1
	for file in `cat $check_file`
	do
		if ! (df -Th|grep -q ${file})
		then   
    	result=0
    	echo ${file}>> check_disk.log
	 	fi
	done
	echo ${result}
}
check_bool=`check_disk`

if [ ${check_bool} -eq 1 ];   
then

```
And I want to extend its function, so, in order to do a conservative experiment, I wrote fake.sh, aimed to create a fake environment in virtual machine. 
Well, however I learn a lot from this trouble.

---

