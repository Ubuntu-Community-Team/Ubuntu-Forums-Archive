---
title: "Some help with an app"
date: 2007-05-24
forum: Programming Talk
---

### Post by energiya on 2007-05-24
Hi,

I tried to make a small script that will be executed by irexec when I press a remote key. I wanted to make it execute something else when I press it more than 2 seconds. I came to this (not finished):
```

#!/bin/sh

file="/home/energiya/.remote"
time=2
times=8

vs=`date +%s`

function write_data
{
	echo $vnr > $file
	echo $vs >> $file
}

function check_number
{
	exec 3< $file
	read <&3 vnr
	read <&3 s
	sub=$(($vs - $s))
	if [ $sub -gt 10 ]; then
	  write_data
	else
	  if [ $sub -lt $time ]; then
	    vnr=$(expr $vnr + 1)
	    echo $vnr > $file
  	    echo $s >> $file
	  else
  	  {
	    if [ $vnr -gt $times ]; then
	      sub=$(($vs - $s))
	      echo $vnr $sub
	      echo "**********************************"
	    fi
	    vnr=0
	    write_data
	  }
	  fi
	  echo $vnr
	fi
}

if [ -e $file ]; then
  check_number
else
  write_data
fi

```

The thing is that it writes to the hdd every time I press a remote key and it writes a lot when I keep it pressed, so I'm now thinking a daemon will be better. But how do I build a daemon that can recive input from irexec? I don't care in what programming/scriping language it's made... I can handle it. I want it to be able to modify the values in memory and not write it to the hdd.

Could someone please help?
Thanks in advance!

---

### Post by energiya on 2007-05-25
Made myself the daemon in C, so problem solved :)

---

