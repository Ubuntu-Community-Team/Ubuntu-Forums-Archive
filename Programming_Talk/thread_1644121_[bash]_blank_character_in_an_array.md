---
title: "[bash] blank character in an array?"
date: 2010-12-12
forum: Programming Talk
---

### Post by tacticalbread on 2010-12-12
to keep it short, I'm writing a roguelike-like (it's like a roguelike :p) purely in bash (to prove it can be done), and one thing that's been bothering me is the inability (as far as I know) to output a blank character in an array. So far, I've been using '&#9608;' to signify nothingness; spaces seem to be ignored when outputting the 'room'.

```

# # # # # # &#9608; &#9608; &#9608; &#9608; &#9608; # # # # # # # &#9608; &#9608; &#9608; &#9608; &#9608; &#9608;
# . . . . # # # # # # # . . . . . # &#9608; &#9608; &#9608; &#9608; &#9608; &#9608;
# . . . . + . . . . . + . . . . . # &#9608; &#9608; &#9608; &#9608; &#9608; &#9608;
# . < . . # # # # # # # . . . @ . # # # # # # #
# . . . . # &#9608; &#9608; &#9608; &#9608; &#9608; # . . . . . . . . . . > #
# . . . . # &#9608; &#9608; &#9608; &#9608; &#9608; # . . . . . # # # # # # #
# # # # # # &#9608; &#9608; &#9608; &#9608; &#9608; # # # # # # # &#9608; &#9608; &#9608; &#9608; &#9608; &#9608;

```

I've also thought of just making a character black, but then that would be visible if anyone doesn't have the background color of the shell black.

I also tried \040, and that is also ignored; and '\007\040\' sort of worked, but the blank space was about half as wide as one character; and '\007\040\\007\040\' did not double the width.

So is there a way of outputting a character with the same width as everything else?

---

### Post by Arndt on 2010-12-12
> **tacticalbread said:**
> to keep it short, I'm writing a roguelike-like (it's like a roguelike :p) purely in bash (to prove it can be done), and one thing that's been bothering me is the inability (as far as I know) to output a blank character in an array. So far, I've been using '&#9608;' to signify nothingness; spaces seem to be ignored when outputting the 'room'.

```

# # # # # # &#9608; &#9608; &#9608; &#9608; &#9608; # # # # # # # &#9608; &#9608; &#9608; &#9608; &#9608; &#9608;
# . . . . # # # # # # # . . . . . # &#9608; &#9608; &#9608; &#9608; &#9608; &#9608;
# . . . . + . . . . . + . . . . . # &#9608; &#9608; &#9608; &#9608; &#9608; &#9608;
# . < . . # # # # # # # . . . @ . # # # # # # #
# . . . . # &#9608; &#9608; &#9608; &#9608; &#9608; # . . . . . . . . . . > #
# . . . . # &#9608; &#9608; &#9608; &#9608; &#9608; # . . . . . # # # # # # #
# # # # # # &#9608; &#9608; &#9608; &#9608; &#9608; # # # # # # # &#9608; &#9608; &#9608; &#9608; &#9608; &#9608;

```

I've also thought of just making a character black, but then that would be visible if anyone doesn't have the background color of the shell black.

I also tried \040, and that is also ignored; and '\007\040\' sort of worked, but the blank space was about half as wide as one character; and '\007\040\\007\040\' did not double the width.

So is there a way of outputting a character with the same width as everything else?

What does the code look like that ought to output blanks but doesn't?

---

### Post by tacticalbread on 2010-12-12
not in complete context, but these are a few things I've tried:
```

room1=(\
"#" "#" "#" "#" "#" "#" " " " " " " " " " " "#" "#" "#" "#" "#" "#" "#" " " " " " " " " " " " " \
"#" "." "." "." "." "#" "#" "#" "#" "#" "#" "#" "." "." "." "." "." "#" " " " " " " " " " " " " \
"#" "." "." "." "." "+" "." "." "." "." "." "+" "." "." "." "." "." "#" " " " " " " " " " " " " \
"#" "." "<" "." "." "#" "#" "#" "#" "#" "#" "#" "." "." "." "." "." "#" "#" "#" "#" "#" "#" "#" \
"#" "." "." "." "." "#" " " " " " " " " " " "#" "." "." "." "." "." "." "." "." "." "." ">" "#" \
"#" "." "." "." "." "#" " " " " " " " " " " "#" "." "." "." "." "." "#" "#" "#" "#" "#" "#" "#" \
"#" "#" "#" "#" "#" "#" " " " " " " " " " " "#" "#" "#" "#" "#" "#" "#" " " " " " " " " " " " " )

```

but it just ignored the spaces.

also, different varities of:
```

s="\040"
OR
s="\007\040"
OR
s="\007\040\007\040"

```


with
```

room1=(\
"#" "#" "#" "#" "#" "#" "$s" "$s" "$s" "$s" "$s" "#" "#" "#" "#" "#" "#" "#" "$s" "$s" "$s" "$s" "$s" "$s" \
"#" "." "." "." "." "#" "#" "#" "#" "#" "#" "#" "." "." "." "." "." "#" "$s" "$s" "$s" "$s" "$s" "$s" \
"#" "." "." "." "." "+" "." "." "." "." "." "+" "." "." "." "." "." "#" "$s" "$s" "$s" "$s" "$s" "$s" \
"#" "." "<" "." "." "#" "#" "#" "#" "#" "#" "#" "." "." "." "." "." "#" "#" "#" "#" "#" "#" "#" \
"#" "." "." "." "." "#" "$s" "$s" "$s" "$s" "$s" "#" "." "." "." "." "." "." "." "." "." "." ">" "#" \
"#" "." "." "." "." "#" "$s" "$s" "$s" "$s" "$s" "#" "." "." "." "." "." "#" "#" "#" "#" "#" "#" "#" \
"#" "#" "#" "#" "#" "#" "$s" "$s" "$s" "$s" "$s" "#" "#" "#" "#" "#" "#" "#" "$s" "$s" "$s" "$s" "$s" "$s" )

```

\040 was ignored, and \007\040 just output a half width character.

and then I'm outputting the whole thing with:
```
printf "${room1[*]}" | xargs -n $width
```
width being how many characters wide the room is, 24 in this case.

---

### Post by highspider on 2010-12-12
Can you dump the ascII key list with for loop and find a NULL or null looking one?
  Note: i modified some one else's code but cant remember where I got the original from 
  didn't mean to be a script kiddy but... 
 
!#/bin/bash 
START=0  
END=255  
echo " Decimal   Hex     Character"   # Header.
echo " -------   ---     ---------"
for ((i=START; i<=END; i++))
do
  echo $i | awk '{printf("  %3d       %2x         %c\n", $1, $1, $1)}'
done
exit 0

---

### Post by ender4 on 2010-12-12
Have you tried using ```
s=" "
```, I think the whitespace is being eaten by xargs, so you need to wrap it in an extra set of quotations to escape it.

---

### Post by tacticalbread on 2010-12-12
> **highspider said:**
> Can you dump the ascII key list with for loop and find a NULL or null looking one?
  Note: i modified some one else's code but cant remember where I got the original from 
  didn't mean to be a script kiddy but... 
 
!#/bin/bash 
START=0  
END=255  
echo " Decimal   Hex     Character"   # Header.
echo " -------   ---     ---------"
for ((i=START; i<=END; i++))
do
  echo $i | awk '{printf("  %3d       %2x         %c\n", $1, $1, $1)}'
done
exit 0



Thanks for that idea, that made me think to try this:

```

#!/bin/bash

clear

for ((i=0; i<=255; i++)); do
	if [ "$i" -lt "100" ]; then
		s="\0$i"
	else
		s="\\$i"
	fi
	
	room0=(\
	"#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "." "." "." "." "." "." "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "#" "#" "#" "#" "#" "." "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "#" "$s" "$s" "$s" "#" "#" "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "#" "$s" "$s" "$s" "$s" "$s" "$s" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "+" "." "#" "$s" "$s" "$s" "#" "#" "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "#" "#" "#" "#" "#" "<" "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "." "." "." "." "." "." "#" \
	"#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" )
	
	printf "${room0[*]}" | xargs -n 24
	
	printf "$i: $s"
	sleep 0.5
	clear
done

```

Although, that didn't give me a character that worked. :(

Ah well, I suppose I'll live without a blank character. :p


> **ender4 said:**
> Have you tried using ```
s=" "
```, I think the whitespace is being eaten by xargs, so you need to wrap it in an extra set of quotations to escape it.

nope, same thing. :(

EDIT:

```

room0=(\
	"#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "." "." "." "." "." "." "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "#" "#" "#" "#" "#" "." "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "#" "\" \"" "\" \"" "\" \"" "#" "#" "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "#" "\" \"" "\" \"" "\" \"" "\" \"" "\" \"" "\" \"" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "+" "." "#" "\" \"" "\" \"" "\" \"" "#" "#" "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "#" "#" "#" "#" "#" "<" "#" \
	"#" "." "." "." "." "." "." "." "." "." "." "." "." "." "." "#" "." "." "." "." "." "." "." "#" \
	"#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" "#" )

```

ha! That worked! Thanks much, good sir!

Edit: well, it *visually* worked. That somehome screwed up the indexes; I'm guessing it registers each "\" \"" as more than one character. The spot that is normally index 97, is now index 100.

Although using something like "\"~\"" works perfectly normal.

Blargh.

edit again:
"\"\040\"" works visually, and *doesn't* screw up the indexes. Wooooo! <3

---

### Post by highspider on 2010-12-13
i found something cool try this 

cut paste and cat the file
 warning its pretty lame but still cool LOL

--------------------------cut--------------------------------

[0;1;35;95m&#9612;[0m   [0;1;33;93m&#9630;&#9600;[0;1;32;92m&#9622;[0m [0;1;36;96m&#9625;&#9623;[0;1;34;94m&#9612;[0m [0;1;35;95m&#9627;&#9600;[0;1;31;91m&#9624;[0m
[0;1;31;91m&#9612;[0m   [0;1;32;92m&#9625;&#9604;[0;1;36;96m&#9612;[0m [0;1;34;94m&#9612;&#9624;[0;1;35;95m&#9612;[0m [0;1;31;91m&#9625;&#9604;[0m 
[0;1;33;93m&#9612;[0m   [0;1;36;96m&#9612;[0m [0;1;34;94m&#9612;[0m [0;1;35;95m&#9612;[0m [0;1;31;91m&#9612;[0m [0;1;33;93m&#9612;[0m  
[0;1;32;92m&#9600;&#9600;[0;1;36;96m&#9624;[0m [0;1;34;94m&#9624;[0m [0;1;35;95m&#9624;[0m [0;1;31;91m&#9624;[0m [0;1;33;93m&#9624;[0m [0;1;32;92m&#9600;&#9600;[0;1;36;96m&#9624;[0m

------------------------end cut----------------------------------

---

