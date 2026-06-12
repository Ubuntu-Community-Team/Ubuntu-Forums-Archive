---
title: "if statement driving me mad!"
date: 2008-03-18
forum: Programming Talk
---

### Post by jobsonandrew on 2008-03-18
ok.. whats wrong with this:
```
#! /bin/bash
IFS=$'\n' #internal field seperator: the char used by array etc to seperate values.. must be set to newline to allow for filenames with spaces

array=(`find -name "*~"`) #find all files ending with a ~
len=${#array[*]}
echo $len
if ($len != 0)then
	i=0
	while [ $i -lt $len ]; do
		echo "Deleting: ${array[$i]}"
		rm "${array[$i]}"
		let i++
	done
else
	echo "Nothing found, no action taken"
fi
```

the output i get is:
```
andy@laptop:~$ ./delbak.sh
1
./delbak.sh: line 7: 1: command not found
Deleting: ./delbak.sh~
andy@laptop:~$ 

```

Its probably something stupid...

PS i know theres stuff like this out there but i like to make things myself so i can learn from them :)

---

### Post by LaRoza on 2008-03-18
Aren't you supposed to use brackets []?

```

#! /bin/bash
IFS=$'\n' #internal field seperator: the char used by array etc to seperate values.. must be set to newline to allow for filenames with spaces

array=(`find -name "*~"`) #find all files ending with a ~
len=${#array[*]}
echo $len
if [ $len != 0 ]
    then
	i=0
	while [ $i -lt $len ]; do
		echo "Deleting: ${array[$i]}"
		rm "${array[$i]}"
		let i++
	done
else
	echo "Nothing found, no action taken"
fi

```

---

### Post by jobsonandrew on 2008-03-18
hmm nope... just get a plain old syntax error then :S

thanks though!

---

### Post by WW on 2008-03-18
I'm curious... where have you ever seen an **if** statement like the one you tried to use (i.e with parentheses)?

Guides to using if/then in BASH include:
    [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-6.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-6.html)
    [http://tldp.org/LDP/abs/html/testconstructs.html](http://tldp.org/LDP/abs/html/testconstructs.html)

---

### Post by jobsonandrew on 2008-03-18
Java, C++, other BASH scripts, PERL, VBS, VB, Excel, Access... the list goes on..

as for BASH, ive seen either being used.. but i thought that these days with bash v3 it was ()

I tried changing it to:
```
if ["$len"!="0"]; then
```

but i get:
```

andy@laptop:~$ ./delbak.sh
1
./delbak.sh: line 13: syntax error near unexpected token `else'
./delbak.sh: line 13: `else'

```

And the same happens if I leave out the double quotes

---

### Post by LaRoza on 2008-03-18
> **jobsonandrew said:**
> Java, C++, other BASH scripts, PERL, VBS, VB, Excel, Access... the list goes on..

as for BASH, ive seen either being used.. but i thought that these days with bash v3 it was ()

I tried changing it to:
```
if ["$len"!="0"]; then
```

but i get:
```

andy@laptop:~$ ./delbak.sh
1
./delbak.sh: line 13: syntax error near unexpected token `else'
./delbak.sh: line 13: `else'

```

And the same happens if I leave out the double quotes
You have an extra ;

```

if [ condition ] 
then
   #do this
else
    #else
fi

```

---

### Post by jobsonandrew on 2008-03-18
I know, Ive tried with and without... according to some guides the semicolon needs to be there..
another script ive written has this:
```

if !(zenity --question --title "remove all gif" --text "Remove all gifs?")then
    exit 0
else
    #other stuff
fi

```

Which works like a charm :( so confused!

---

### Post by jobsonandrew on 2008-03-18
SOLVED
I wasnt using my common sense, I looked at the while loop i had and copied its format:
```

if [ $len -gt 0 ]; then

```
(the space between [ and $len HAS to be there) which seems pretty bleeding stupid to me(-gt ??? just use >)

nevermind eh... now i know

---

### Post by LaRoza on 2008-03-18
> **jobsonandrew said:**
> I know, Ive tried with and without... according to some guides the semicolon needs to be there..
another script ive written has this:
```

if !(zenity --question --title "remove all gif" --text "Remove all gifs?")then
    exit 0
else
    #other stuff
fi

```


The () are doing something else there...

---

