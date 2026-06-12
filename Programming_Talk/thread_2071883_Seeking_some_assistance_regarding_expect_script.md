---
title: "Seeking some assistance regarding expect script"
date: 2012-10-16
forum: Programming Talk
---

### Post by bageltheGURU on 2012-10-16
Hello, I'm a ubuntu user ( about 3 years). I just started administration / scripting at my job, and am a rookie with bash / perl / etc. I've been fine making my own so far with perl, but having some trouble with an expect script regex. This is my syntax; sorry for the messiness, but you get the idea. The "cat file" on the remote system is all I want, but I'm not too familiar with regex / expect command syntax. Any help in the right direction is amazingly appreciated, as I'm an avid user trying to learn very quickly.

[IMG]http://imgur.com/uVW2p[/IMG]


[http://imgur.com/uVW2p](http://imgur.com/uVW2p)

---

### Post by bageltheGURU on 2012-10-16
I also apologize if this is in the wrong place in the forums, was not quite sure. Mucho thanks.

---

### Post by bageltheGURU on 2012-10-16
oops....

#!/bin/bash
HOST="hostname"
USER="user" 
PASS="pass"

VAR=$(expect -c "
spawn ssh $USER@$HOST
expect \"password::\"
send \"$PASS\r\"
expect \"\\\\$\"
send \"cat output.txt\r\"
expect -re \"$USER.*\"
send \"logout\"
")

echo "==============="
echo "$VAR" > /home/folder/output.txt

---

### Post by kevinharper on 2012-10-16
Are you getting any errors?

Also, code is easier to read if enclosed in code tags like this:

```
This is code
```

I haven't done PERL in a long time, but I'm pretty sure you need ; after your var declarations, the last ) of your VAR, and echos.

---

