---
title: "Bash script job interview challenge - sorting output of /etc/passwd"
date: 2012-05-03
forum: Programming Talk
---

### Post by SuaSwe on 2012-05-03
Hi all,

I had a job interview some time back with a mighty desirable company, and fell down on an exercise that at first I thought looked simple until I tried to work through it! I didn't get any further after this but remain curious how it could have been done. 

Let's say the output of /etc/passwd looks as below:

```
 
root:x:0:0:root:/root:/bin/bash
daemon:x:0:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
luser:x:0:0:root:/root:/bin/bash
luser2:x:2:2:bin:/bin:/bin/sh
luser3:x:3:2:bin:/bin:/bin/sh

```

(E.g., users other than root have managed to assign themselves UID 0, which is bad and must be stopped!)

The idea is to obtain an output listing each used UID followed by the usernames that have them, like so:

0:root,daemon,luser
2:bin,luser2
3:luser3

For the life of me I just cannot figure out how this could be done! The furthest I've managed to get is as follows:

```

file='passwd_output'
rootusers=`cat $file | grep ":0:[0-9]" | cut -d ':' -f1 | sed 's_$_,_'`
echo "0:"$rootusers

```

.. which could be used to compile the list but only if setting a separate variable for each UID, e.g. assuming they are known beforehand, which is cheating a bit.

Has anyone got any ideas/pointers? It must be done in bash but otherwise anything goes. :)

---

### Post by r-senior on 2012-05-03
I'm not very practiced with bash, so I won't attempt the code, but from a general perspective, it looks like a job for associative arrays (aka dictionaries, maps).

From v4, bash has associative arrays:

[http://www.linuxjournal.com/content/bash-associative-arrays](http://www.linuxjournal.com/content/bash-associative-arrays)

So my idea would be to chug through the file and make an associative array with the key being the UID. If the key is missing from the array when you encounter it in the file, create a new entry with the username as the value, otherwise append a comma and the username to the existing entry.

Then iterate over the associative array, printing the key and value.

---

### Post by emiller12345 on 2012-05-03
This is a oneliner:
```
$ ETC_PASSD=/etc/passwd; UID_LIST="$(cat $ETC_PASSD | awk -F: '{print $3}' | sort | uniq)"; for uid in $UID_LIST; do echo -ne $uid":"; for name in $(cat $ETC_PASSD); do if [ $uid = "$(echo $name | awk -F: '{print $3}' )" ]; then NAMELIST="$NAMELIST $(echo $name | awk -F: '{print $1}')"; fi; done; NAMELIST="$(echo $NAMELIST | tr ' ' ',')"; echo $NAMELIST; NAMELIST=""; done
```

---

### Post by codemaniac on 2012-05-03
Here is my awk one liner to serve your purpose . ;)
Associative arrays are cool and saves a lot of coding .
```
awk -F":" '{arr[$3]=arr[$3]" "$1}END{for (i in arr)print i,arr[i];}' /etc/passwd
```

---

### Post by r-senior on 2012-05-03
Awk is cheating! :)

Right tool for the job though.

---

### Post by diesch on 2012-05-03
Quick and dirty "only sh and coreutils" solution:

```
#!/bin/sh

old_uit=''

sort -t: -k3 -n passwd | (IFS=:; while read name x uid _; do
 if [ "$uid" != "$old_uid" -a "$old_uid" != '' ]; then
   echo "$old_uid: $users"
   users="$name"
 else
   if [ -z "$users" ];  then
     users="$name"
   else
     users="$users,$name"
   fi
 fi
 old_uid="$uid"
done; echo "$old_uid: $users")
```

---

### Post by SuaSwe on 2012-05-04
Nah, awk is allowed, was never told otherwise! 

And cheers guys, I knew I could rely on this forum to come up with some clever answers. :D Suspected there would be arrays involved in the solution, so much as they frighten me (even the name sends bolts of terror down my spine) I reckon I'm gonna have to do some reading-up!

---

