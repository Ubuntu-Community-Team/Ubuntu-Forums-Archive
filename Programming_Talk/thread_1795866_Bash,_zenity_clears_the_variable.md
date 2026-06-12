---
title: "Bash, zenity clears the variable"
date: 2011-07-03
forum: Programming Talk
---

### Post by 5ive on 2011-07-03
I want to have the result in variable.
```
apt=`sudo apt-get update`
echo "$apt"
```
Echo something always returns.
```
apt=`sudo apt-get update | zenity --progress --auto-close`
echo "$apt"
```
Echo empty always returns. Why doesn't anything display? How to do well?

---

### Post by mikejonesey on 2011-07-03
man tee

tee stdout to zenity and cat the stdoutput from file on finish :)

eg

```
sudo apt-get update | tee mylog.log | zenity --progress --auto-close
cat mylog.log
```:)

---

### Post by ziekfiguur on 2011-07-03
> **5ive said:**
> ```
apt=`sudo apt-get update | zenity --progress --auto-close`
echo "$apt"
```
Echo empty always returns. Why doesn't anything display? How to do well?

The reason is that `command` takes the output of command, if you use a pipe to redirect the output from apt-get to zenity and zenity does not output anything there will be no output.

---

### Post by 5ive on 2011-07-07
Thank you.

---

### Post by dwhitney67 on 2011-07-07
> **5ive said:**
> Thank you.

Mark this (your) thread as solved.

---

### Post by 5ive on 2011-07-20
```
var="$(sleep 5 && echo "Ubuntu 11.04 is...")" &
sleep 5
echo $var
```
Echo empty always returns. Is there a solution? Is there a solution? I want to necessarily result in a variable.

---

### Post by dethorpe on 2011-07-21
(should probably have started new thread for this as its a new question )
 
However, the reason is the 1st line puts the command into the background in a subshell, so $var is then set in the sub-shell not the parent shell and remains undefiend in the parent.
 
If you want to capture the output of a background command investigate using the bash coprocess (a few google searchs should bring up all the info you need), that allows you to connect to and capture the background processes stdout.

---

### Post by mikejonesey on 2011-07-21
strange way of doing things... but...
```
var="$(sleep 1; (echo "Ubuntu 11.04 is..."))"; sleep 2; echo $var
```

---

