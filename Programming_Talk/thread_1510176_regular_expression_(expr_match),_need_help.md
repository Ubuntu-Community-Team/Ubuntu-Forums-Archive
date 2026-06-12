---
title: "regular expression (expr match), need help"
date: 2010-06-15
forum: Programming Talk
---

### Post by apeganz on 2010-06-15
hello everyone,

I am trying to improve my mdadm raid tuning script and I'm stuck. What I need is a regular expression that returns the "drive letters" of all partitions that are part of an md array and one that only returns the letters of those that are not spares.
so far I have```
expr match "`grep \"md51 : \" /proc/mdstat`" '.*\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \?\)\+'
```the `grep \"md51 : \" /proc/mdstat` part gives me```
md51 : active raid5 sdd1[3] sdc1[0] sdg1[1] sdh1[4] sdf1[5](S) sde1[2]
```the whole command only gives me the last part of that (sde1[2]) where I want all the drives. That string will then be cut down to just dcghfe, but I can't work on that until I figure out how to get all the drives. If I end the regexp with \{6\} instead of \+ I still get the same result (just the last drive).

And I have not yet worked on getting just the active drives (everything without an appendent (S)), so I can cut that down to dcghe.

can someone help me out with some regex-magic? :D
thx4help,
alex

---

### Post by geirha on 2010-06-15
Here's a way to do it without regex. It will at least work for the input line you specified. I don't know in what way that line may change though.
```
#!/bin/bash
# read each word into an array
read -r -a words < <(grep -F 'md51 : ' /proc/mdstat)

# For each word, starting from the fifth
for word in "${words[@]:4}"; do 
  # output the third letter of the word
  echo "${word:2:1}" 
done

```

---

### Post by apeganz on 2010-06-15
thx 4 your reply!

I already experimented a little with awk to do sth similar, but I don't know either in what way the file changes :(
I guess everything after raid5 is always the same, but I'm quite certain that active can change to sth different.
If it can't be done with a single regex I think I will go with your solution but read all the words and check them against a regex individually.

alex

---

### Post by geirha on 2010-06-15
Maybe
```

#...
for word in "${words[@]:2}"; do
  # skip words that doesn't start with sd<lowercase letter><digit>
  # Note, that is a glob, not a regex.
  [[ $word = sd[[:lower:]][[:digit:]]* ]] || continue 
  echo "${word:2:1}"
done

```

---

### Post by apeganz on 2010-06-15
here is what I'm using now. I think it covers pretty much every possibility, but of course they are endless ;)```
#!/bin/bash
MDDEV=md51

# get all devices
DEVSTR="`grep \"^$MDDEV : \" /proc/mdstat` eol"
DEVSTR='md51 : active raid5 sdd1[3] sdc1[0] sdg1[1] sdh1[4] sdf1[5](S) sde1[2] eol' #debug
while \
 [ -z "`expr match \"$DEVSTR\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \)'`" ]
do
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

# get active devices list and spares list
DEVS=""
SPAREDEVS=""
while [ "$DEVSTR" != "eol" ]
do
  CURDEV="`echo $DEVSTR|cut -f -1 -d \ `"
  if [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\)'`" ]
  then
    SPAREDEVS="$SPAREDEVS${CURDEV:2:1}"
  elif [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\)'`" ]
  then
    DEVS="$DEVS${CURDEV:2:1}"
    SPAREDEVS="$SPAREDEVS${CURDEV:2:1}"
  fi
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done
echo $DEVS #debug
echo $SPAREDEVS #debug
```thx 4 your help and ideas!

regards,
alex


edit: I included the changes in my raid tuning script, if you are interested you can find it at [http://ubuntuforums.org/showthread.php?t=1494846](http://ubuntuforums.org/showthread.php?t=1494846)

---

### Post by geirha on 2010-06-15
I'd strongly recommend you not use expr and `` in a bash script. You should only use those if you have to write a script that needs to be portable with the bourne shell. If you absolutely insist on using regular expressions, I suggest you use bash's [[ keyword rather than `expr`.

```

devstr='md51 : active raid5 sdd1[3] sdc1[0] sdg1[1] sdh1[4] sdf1[5](S) sde1[2]'
read -r -a array <<< "$devstr"
re='^sd([a-z])1\[[12]?[0-9]\]'
res=
for word in "${array[@]}"; do
  if [[ $word =~ $re ]]; then
    res+=${BASH_REMATCH[1]}
  fi
done
echo "$res"

```

You should really read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) and learn good shell scripting practice. 

[quote="Jamie Zawinski"]Some people, when confronted with a problem, think “I know, I'll use regular expressions.”   Now they have two problems.[/quote]

---

