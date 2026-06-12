---
title: "trouble piping grep into select--best solution?"
date: 2010-02-22
forum: Programming Talk
---

### Post by jamesisin on 2010-02-22
I am writing a script to sync playlists onto a music device.

I have some code which will give me a list of user-generated playlists:

```
PLAYLISTS=$( grep playlist\ name.*type=\"static\" $RHYTHMBOXLISTS | awk -F '"' '{ print i$2 }' )
```

The variable $RHYTHMBOXLISTS is the location of the playlists file:

```
RHYTHMBOXLISTS="/home/$USER/.gnome2/rhythmbox/playlists.xml"
```

Running the code under PLAYLISTS (ie, that which resides in the parentheses) returns a list of the names of the playlists which the user has created using Rhythmbox.

```
grep playlist\ name.*type=\"static\" /home/username/.gnome2/rhythmbox/playlists.xml | awk -F '"' '{ print i$2 }'
_0_0_Burn_0_0_
_0_0_RockBox1
_0_0_RockBox2
**_0_j2 [16]**
_1_2_BeattlesCovers
...
```

I would like to put selectable numbers before each playlist.  I tried using select:

```
select SYNKLIST in "$PLAYLISTS"; do
        
             echo "You chose "$SYNKLIST", processing..."
             
    done
```

The problem is that the list gets transformed somewhere.  As written above I get a one item list which gives the entire list (with line breaks, but all one item).  If I remove the quotes around $PLAYLISTS I get a list of each space separated word (no longer broken at the line breaks in the grep list):

```
./RockBoxSynk.sh 
...
**1)** _0_0_Burn_0_0_
_0_0_RockBox1
_0_0_RockBox2
_0_j2 [16]
_1_2_BeattlesCovers

or

./RockBoxSynk.sh 
...
 1) _0_0_Burn_0_0_	    51) **Slow**
 2) _0_0_RockBox1	    52) **Fire**
 3) _0_0_RockBox2	    53) **[16]**
 4) **_0_j2**		    54) **Digital**
 5) **[16]**		    55) **Dawn**
 6) _1_2_BeattlesCovers	    56) **[13]**

```

Am I going about this all wrong?  What is the best solution?

I would like the user to be able to select one or more playlist from the list (with options to QUIT and select ALL).

---

### Post by falconindy on 2010-02-22
You probably want to wrap the results into an array. You'll need some tricky to avoid having issues with spaces:

```
SAVEIF=$IFS
IFS=$'\n'
PLAYLISTS=($( grep playlist\ name.*type=\"static\" $RHYTHMBOXLISTS | awk -F '"' '{ print i$2 }' ))

for list in "${PLAYLISTS[@]}"; do
   # good stuff goes here
done
```

---

### Post by jamesisin on 2010-02-23
Thanks for stopping by to help out.

Perhaps I'm still a little confused.  I built this to test your suggestion:

```
RHYTHMBOXLISTS="/home/$USER/.gnome2/rhythmbox/playlists.xml"

SAVEIF=$IFS
IFS=$'\n'
PLAYLISTS=($( grep playlist\ name.*type=\"static\" $RHYTHMBOXLISTS | awk -F '"' '{ print i$2 }' ))

for list in "${PLAYLISTS[@]}"; do
   # good stuff goes here

read -p "Please select PlayLists to synk: "

done
```

No list appears.

Does it matter that the parsing of the IFS comes before the grep pipeline?

What does the second parenthetical pair in PLAYLISTS do?

What does the enclosed snail [@] in the for loop do?

---

### Post by falconindy on 2010-02-23
Ah. Got it. Assumed you were a little more familiar with Bash. Consider the following:

```
var=zero one "two alsotwo" three four
```
On it's own, you have no way to separate out these elements except to iterate over them with a construct like a for loop. You'll also run into issues with the 3rd element because the quotes won't be preserved in a meaningful way.

Fear not, Bash gives you arrays!
```
var=(zero one "two alsatwo" three four)
```
Now we can access each element directly by its index. Better yet, quoted elements are preserved.
```
$ echo ${var[0]}
zero
$ echo ${var[2]}
two alsotwo

```

If you want to iterate over the contents, you have two options:
```
$ echo "${var[*]}"
zero one two alsotwo three four
$ echo "${var[@]}"
zero one two alsotwo three four
```
They look exactly the same, but in practice, will behave slightly differently. Whereas using the * operator with the array name quoted will return the entire content of the array as a single quoted variable, the @ operator with the array name quoted will return each element quoted for you.

```
$ for ele in "${var[*]}"; do
>  echo $ele
>done
one two also two three four

$ for ele in "${var[@]}"; do
>  echo $ele
>done
one
two also two
three
four

```
9 times out of 10, you'll want to use the quoted @ syntax.

---

### Post by jamesisin on 2010-02-23
My system is behaving a little differently:

```
$ var=(zero one "two alsatwo" three four)
$ for ele in "${var[@]}"; do echo ele; done
ele
ele
ele
ele
ele
$ echo ${var[0]}
zero

```

Huh?  It's parsing the correct *number* of elements, but then it lists the variable name when called out with the snail.

(If I substitute that syntax into my select loop from the opening it does parse the elements as expected, so I think I can beat my selection section into submission.  Thanks for the education.  I'm just a BASH novice with good books.)

---

### Post by falconindy on 2010-02-23
> **jamesisin said:**
> My system is behaving a little differently:

```
$ var=(zero one "two alsatwo" three four)
$ for ele in "${var[@]}"; do echo **$**ele; done
ele
ele
ele
ele
ele
$ echo ${var[0]}
zero

```

Huh?  It's parsing the correct *number* of elements, but then it lists the variable name when called out with the snail.

(If I substitute that syntax into my select loop from the opening it does parse the elements as expected, so I think I can beat my selection section into submission.  Thanks for the education.  I'm just a BASH novice with good books.)
Working as intended. You missed a $ sign that I've inserted into your code in bold.

edit: oh, looks like i did too.

---

### Post by jamesisin on 2010-02-23
Yeah, little missing characters are so easily overlooked.  Funny that I got it correct in my script but not in my test.

Ok, I'm going back to digging.  Now that I have my list of playlists I need to get user input to pick which of the playlists are to be included in the synk.  I hope to find a way to allow select to accept multiple numeric input (like 1 2 4 13).

I know how to get it to accept my two extra entries (ALL and QUIT) but I also should limit its numeric input to numbers within the range of the list grep/awk/sed generates.

Thanks again for your assistance.

---

