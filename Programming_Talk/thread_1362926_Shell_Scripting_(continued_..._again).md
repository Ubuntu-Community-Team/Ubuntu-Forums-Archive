---
title: "Shell Scripting (continued ... again)"
date: 2009-12-23
forum: Programming Talk
---

### Post by J05HYYY on 2009-12-23
This is a continuation of [this thread]("http://ubuntuforums.org/showthread.php?t=757995"), and [this thread]("http://ubuntuforums.org/showthread.php?t=1280257")... In which I attempted to solve a few vividly related tasks using bourne shell scripts:

In the first: I was looking to get a position of a pattern within a string.
In the second: I was looking at different ways to search for the same pattern both backwards and forwards.
**In this: I want to look at two things given below.**

1) As from the first thread - the expr command can be used to do an "anchored pattern match".

For instance, if given the string "xxxabxxx", searching for the pattern "ab", the result is going to be 3; when using the following command:

```
echo `expr "xxxabxxx" : '.*ab' - $(expr "ab" : '.*')`
```

This is all well and good ... but *what if I were to have a string like "xabxabxab", and I wanted to get the position of the second occourance?*

2) *Is there a way to count how many times "ab" exists in the string?*

_I would like to continue using the expr command, any suggestions, much appreciated._
________________________________________________________________________
[COLOR="RoyalBlue"]So far; I can see two ways of searching. If I had "aaaaaa" as a string instead and I wanted to count how many times "aa" existed: I could count either 3 times or 5 times because the pattern "aa" occurs at the positions 0,2 & 4 (and also 1 & 3). Please let me know - whatever the whether.[/COLOR]

---

### Post by J05HYYY on 2009-12-23
well I came up with this beast:

```

#!/bin/sh
#it's pretty dirty & finds each instance backwards instead of forwards.
string="aaaaaa"
count=0
end="FALSE"
while [ end="FALSE" ]; do
	position=`expr "$string" : '.*aa' - 1` #add "- $(expr "ab" : '.*')" instead of "-1" to exclude patterns within patterns.
		if [ $position -gt -1 ]; then
			echo "Found at position: $position"
			count=$((count+1))
				if [ $position -gt 0 ]; then
					string=`echo $string | cut -c 1-$position`
				else
					end="TRUE"
					break
				fi
		else
			end="TRUE"
			break
		fi	
done
echo "Overall, the string was found $count times."
```

I'm trying to avoid grep because of it's portability issues with solaris. If anyone else can find a better method with expr, do let me know. Cheers

---

### Post by ghostdog74 on 2009-12-24
you can easily do this with awk. Use nawk for Solaris. No need to worry about different shells.
```


nawk 'BEGIN{
    string="abxabxabxabblah"
    pat="ab"
    o=string
    m=gsub(pat,"",string)
    print pat" appears "m" times"
    while(1){
        match(o,pat)
        if (RSTART>0){
            print "found "pat" at: "t+RSTART
            t=t+RSTART+1
            o=substr(o,RSTART+length(pat))
        }else{break}

    }
}
'


```
output
```

# ./shell.sh
ab appears 4 times
found ab at: 1
found ab at: 4
found ab at: 7
found ab at: 10


```

---

### Post by geirha on 2009-12-24
```

while [ end="FALSE" ]; do

```
That will always be true. When you only provide one argument to the [ command, it is equivalen to [ -n "string" ], which returns true if string is not empty.

What you want is:
```
while [ FALSE = "$end" ]; do
```

Also, your script is NOT a bourne shell script, because bourne does not accept $(( )); POSIX sh does however, so your script is actually a POSIX sh script. And since POSIX sh can do arithmetics and parameter expansion, you should use that rather than using external commands like expr whenever possible. 

```

#!/bin/sh
string=aaaaaa
count=0
while true; do
  tmp=${string#*aa}  # Strip away everything up to and including the first aa
  [ "$tmp" = "$string" ] && break # If nothing was stripped away, we're done
  string=$tmp
  : $((count+=1))
done
echo "$count"

```

---

### Post by J05HYYY on 2009-12-24
Some good comments. Thank you!

(ghostdog74) I have had a look at awk & nawk but as far as I'm aware, only a select number of systems ship with nawk. Apparently awk does not support gsub, so I assume it would be different with the original awk?

(geirha) The do while was a silly mistake on my part - which I gave up on and just used break, cheers for the correction X). It's interesting to hear about some of the differences between the POSIX and Bourne shell. Could you possibly send me any further reading material on the subject? To me, it would seem logical to use the external command expr instead; as it looks to be older (single un*x specification) and would hence support more systems?
I don't see how it would be otherwise preferable?

Again, thank you for your help, it's very much appreciated. :KS

---

### Post by geirha on 2009-12-24
Would be nice to have a list of features available in the different shells, though I don't know of such list. The best way to see the difference between bourne, posix sh and bash, is to actually compare them; run you scripts in all of them and see what differences there are. You can get the bourne shell from the heirloom project. See [http://mywiki.wooledge.org/BourneShell](http://mywiki.wooledge.org/BourneShell)

---

### Post by ghostdog74 on 2009-12-24
> **J05HYYY said:**
> Some good comments. Thank you!

(ghostdog74) I have had a look at awk & nawk but as far as I'm aware, only a select number of systems ship with nawk. Apparently awk does not support gsub, so I assume it would be differen
which system doesn't ship with awk? awk is part of single unix specs. On solaris use nawk and it supports gsub. don't use the crippled awk that comes with Solaris.

---

### Post by Rany Albeg on 2009-12-25
Hi , this is a quick reply.

If you just want to calculate how many times str1 exists in str2 i would do something like this

```
rany@rany-laptop:~$ var=xabababx
rany@rany-laptop:~$ vs="${#var}"
rany@rany-laptop:~$ p=ab
rany@rany-laptop:~$ ps="${#p}"
rany@rany-laptop:~$ var=$(echo $var|sed 's/'$p'//g')
rany@rany-laptop:~$ cursize="${#var}"
rany@rany-laptop:~$ echo $(((vs-cursize)/ps))
3
rany@rany-laptop:~$
```

---

### Post by ghostdog74 on 2009-12-25
> **Rany Albeg said:**
> Hi , this is a quick reply.

If you just want to calculate how many times str1 exists in str2 i would do something like this

```
rany@rany-laptop:~$ var=xabababx
rany@rany-laptop:~$ vs="${#var}"
rany@rany-laptop:~$ p=ab
rany@rany-laptop:~$ var=$(echo $var|sed 's/'$p'//g')
rany@rany-laptop:~$ cursize="${#var}"
rany@rany-laptop:~$ echo $(((vs-cursize)/ps))
3
rany@rany-laptop:~$
```

well, don't even have to use sed. 
```

var=${var//$p}

```

and how did you get "ps" ??

---

### Post by Rany Albeg on 2009-12-25
Thanks you , i missed  the ps part.
And yes , you don't have to use sed to accomplish that.

Have a nice day.

---

