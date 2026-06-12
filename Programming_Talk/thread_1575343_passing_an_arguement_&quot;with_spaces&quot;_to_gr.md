---
title: "passing an arguement &quot;with spaces&quot; to grep?"
date: 2010-09-15
forum: Programming Talk
---

### Post by haqthat on 2010-09-15
Here is what I'm attempting to do.

I created a shell script test.sh that I would like to pass variable to and grep out what I've passed.

It works, sort of.

Here is what the code looks like:
```

#!/bin/bash

[[ -n "$1" ]] || {
echo "";
echo "###################################################################################"
echo "";
echo "Loading ALL Activity.   Try test 'somestring' to narrow results.";
echo "";
echo "###################################################################################"
echo "";
tail -f /var/log/areallylonglog.log | grep --color=auto -i -e 'send'
 }

echo "###################################################################################"
echo "";
echo Loading Activity for "$@".   Try 'test' by itself to show ALL Activity.;
echo "";
echo "###################################################################################"
echo "";

tail -f /var/log/areallylonglog.log | grep -i -e 'send' | grep --color=auto -i -e "$@"

```I know the issue has something to do with grep not wrapping "$@" in quotes.

It works find if I do:
./test.sh  -- it will tail/grep for the word send and output to screen

if I do:
./test.sh happy  -- it works, it will grep each line for the word 'send', then pass it to grep again for the word 'happy'  and only show me the lines that contain both (in that order).

BUT 
if I add a argument with spaces:
./test.sh happy people  -- I will get
```
grep: people: No such file or directory
```I understand already that it would work if I could get grep to wrapp happy people in quotes ; "happy people" or even single quotes 'happy people'

But no matter what I try inside the script, I can't get it to work.

I've tried:
"$@"
""$@""
'"$@"'
\""$@"\"

I'm stumped.

Any help would be much appreciated!

---

### Post by DaithiF on 2010-09-15
Hi,
use "$*"

an alternative would be to quote the words you pass in, so that you only pass in a single parameter, ie.
```
./test.sh "happy people"

```
in which case then "$@" and "$*" or indeed "$1" would all resolve to the sam thing.

---

### Post by haqthat on 2010-09-16
DaithiF......

THANK YOU.

Using "$*" instead of "$@" works perfectly!
I searched all over the forums, and google for at least a couple hours (over the course of two days) trying to figure this out.

I'm not a noob, but writing shell scripts isn't my day job either, I mostly come up with them on the fly to help make my day easier.

Passing the argument in quotes worked as well, but I'd rather not have to, (as other people will be using this script as well), and it's just easier to not have to worry about syntax if you don't have to.

I appreciate your help, and I am very grateful.

Thanks!

---

