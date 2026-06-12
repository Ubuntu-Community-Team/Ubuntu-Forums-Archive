---
title: "Can select be used to get multiple results?"
date: 2010-02-24
forum: Programming Talk
---

### Post by jamesisin on 2010-02-24
I am trying to write a bash script where the user is presented with a list from which they might choose from none to all of the items on that list.  I have a *select* list being generated, but I can't seem to sort out a way to accept more than one result/reply from *select*.

Basically I want to have the command line equivalent of a list of items with check boxes where the user can check some, uncheck others, then click NEXT so that the *select* list generates a user list (which may or may not be the same as the full *select* list).

I can supply my current code if that is necessary.

---

### Post by falconindy on 2010-02-24
I've never used select for, it's kinda neat. I tested the following code, which seems to work decently well.

```
#!/bin/bash

playlists=()
echo "Select playlists one at a time. Ctrl-D ends selection.
PS3="-->"
select list in rock classical jazz techno punk ska; do
    playlists+=($list)
done
```
PS3 sets your prompt, and a user can enter as many selections as they want (separated by a newline), each of which will be appended to the playlists array. As mentioned, use ctrl-D to end selection. This won't, however, check for unique input.

---

### Post by jamesisin on 2010-02-24
Hmmm...  Let me see if I understand this.

playlist() is an array.  So here select builds items into that array?

If that's the case, then the array would contain the items I needed and I could use *uniq* to get rid of duplicates.  I could count the items in the array, and perhaps I could even list them out by their *select* item number.

Am I understanding this correctly?

---

### Post by jamesisin on 2010-02-24
I wrote this to test some of this:

```
#!/bin/bash

playlists=()
echo "Select playlists one at a time. GO ends selection process."
PS3="-->"

until [ "$REPLY" == "GO" ]; do
    select list in rock classical jazz techno punk ska; do
        if [ "$REPLY" = "GO" ]; then
            echo
            echo $playlists
            break && exit 0  # is this the best place for the exit?
        elif [ -n "$list" ]; then
            playlists+=($list)
        fi 
    done #select
done #until
```

It doesn't work exactly as I expected:

```
$ ./SelectArray.sh 
Select playlists one at a time. GO ends selection process.
1) rock	      3) jazz	    5) punk
2) classical  4) techno	    6) ska
-->6
-->2
-->4
-->5
-->GO

ska

```

I was thinking the echo would list all the contents of $list.  I have to go drink some beer, but I'll take another look at this later.

---

### Post by falconindy on 2010-02-24
$playlists is only going to return the first element. You need to use proper curly brace syntax to access elements in the array. Your same code produces the following when I change '$playlists' to '${playlists[@]}':

```
Select playlists one at a time. GO ends selection process.
1) rock	      3) jazz	    5) punk
2) classical  4) techno	    6) ska
-->1
-->3
-->5
-->GO

rock jazz punk
```

> **jamesisin said:**
> I have to go drink some beer
When duty calls...

---

### Post by jamesisin on 2010-02-25
Yeah, I knew that (on some level).  I was trying to sort it out as I walked to the pub.  Anyway, that'll get me where I need to be in my script.  Baby steps.

---

### Post by jamesisin on 2010-02-25
As concerns duplicate entries, is this legitimate?

```
playlists-=($list)
```

---

### Post by jamesisin on 2010-02-25
I am trying to make a test for already added elements.  The script runs but I don't get the expected results.  I've tried several iterations and this is the latest:

```
#!/bin/bash

playlists=()
genre="rock classical jazz techno punk ska"
echo "Select playlists one at a time. GO ends selection process."
PS3="-->"

until [ "$REPLY" == "GO" ]; do
    select selected in $genre; do
        if [ "$REPLY" = "GO" ]; then

            printf "%s\n" "${playlists[@]}"
            break && exit 0  # is this the best place for the exit?
        elif [ -n "$selected" ]; then
        
            for item in "${playlists[@]}"; do
                if [[ $item == $selected ]]; then
                    test=0 # true
                    echo $test "means true"
                else test=1
                    echo $test "means false"
                fi
                
                if test=0; then
                     # playlists-=($selected)
                     echo "already selected"
                elif test=1; then
                     playlists+=($selected)
                     echo $playlists
                fi
                
            done
        fi
    done #select
done #until

```

(Note: The playlists-=($selected) construct does not appear to work.)

---

### Post by falconindy on 2010-02-25
oops, double post.

---

### Post by falconindy on 2010-02-25
Here's an example of how you can sort array elements and remove duplicates:

```
#!/bin/bash

array=(one two "also two" "also two" three three four five six six six)

saveifs=$IFS
IFS=$'\n'
newarray=($(for i in "${array[@]}"; do echo $i; done | sort -u))

for i in "${newarray[@]}"; do
    echo $i
done
```

Hopefully rearranging the selection doesn't pose an issue to you.

---

### Post by jamesisin on 2010-02-25
That is true; what you are suggesting will remove duplicates.  I am hoping to something a bit more robust.  I want to add things that don't exist and *remove things that do*.  So, if you have already added an item to the array and you re-select that same item, it should *remove* that item from the array.  Maybe this isn't the best path to follow, but my aim is to get a selectable list where you can pick and choose items as though they had tick boxes for each item.

---

### Post by falconindy on 2010-02-25
Given the route you've picked (select to create the menu), what you're suggesting sounds fairly painful. I can see tput being put to good use if you were to code the menu from scratch. A full blown (n)curses solution would probably be "easier" but that escapes the boundaries of Bash.

---

### Post by geirha on 2010-02-25
You can use the number typed in as an index in a (sparse) array.

```

#!/bin/bash

genres=( rock classical jazz techno punk ska )
checklist=()

select genre in "${genres[@]}"; do
  [[ $REPLY = GO ]] && break
  [[ $genre ]] || continue
  if [[ ${checklist[REPLY]} ]]; then
    unset 'checklist[REPLY]'
    echo "$genre deselected."
  else
    checklist[REPLY]=$genre
    echo "$genre selected."
  fi
done

echo "You have selected: ${checklist[@]}"
    

```

---

### Post by jamesisin on 2010-02-25
falconindy - I'm not yet familiar with tput.  I'll look into it.

geirha - That does it.  It will require a small rewrite but not too much.  I'll have a go at that now.

---

### Post by jamesisin on 2010-02-25
I have this working for now:

```
usage="\n\nPlease enter the number corresponding to the playlist you would like to synk. \n     Seperate multiple playlists with a space. \nA = synk ALL available playlists \nS = SHOW current selections \nQUIT = QUIT this script \n<ENTER> = display available playlists again \nNEXT = Proceed to the NEXT phase.\n\n"

rhythmboxlists="/home/$USER/.gnome2/rhythmbox/playlists.xml" # this changes in later versions

printf "\nI am currently set to use this Rhythmbox playlists file: \n"
printf "     $rhythmboxlists"
printf "\nI will synchronize music from this location: \n"
printf "     $library"
printf "\nwith this root folder on this particular music player: \n"
printf "     $rockbox\n\n"

read -p "Press <ENTER> to coninue. "

SAVEIF=$IFS
IFS=$'\n'
playlists=($( grep playlist\ name.*type=\"static\" $rhythmboxlists | awk -F '"' '{ print i$2 }' ))

count=0
for void in ${playlists[@]}; do
    count=$((count+1))
    done

printf "%b" "\a\nI have found $COUNT user generated playlists:\n\n" >&2

synklist=()

PS3='Select the playlist(s) for syncrhonization (or help): '

until [[ "$REPLY" == "NEXT" ]]; do
   select selected in "${playlists[@]}"; do
      if [[ "$REPLY" = "QUIT" ]]; then
           printf "\nGood-bye.\n\n"
           exit 0
      elif [[ "$REPLY" = "NEXT" ]]; then
           break
      elif [[ "$REPLY" = "A" ]]; then
           printf "\nI will synchronize all $count playlists to your device.\n\n"
              
           # create $SYNKLIST with all elements from $PLAYLISTS here
           
           
      elif [[ "$REPLY" = "S" ]]; then
           if [[ -z "$synklist" ]]; then
              printf "\nYou have not yet added any playlists for synchronization.\n"
           fi
           if [[ -n "$synklist" ]]; then
              printf "\nHere are the playlists you have added thus far: \n"
              printf "%s\n\n" "${synklist[@]}"
           fi
           printf "%b\n"
      elif [[ "$REPLY" = "help" ]]; then
           printf $usage
      else [[ $selected ]]
           if [[ ${synklist[REPLY]} ]]; then
                unset 'synklist[REPLY]'
                echo "$selected removed"
           else
                synklist[REPLY]=$selected
                echo "$selected added"
           fi
      fi
   done #select
done #until

printf "\nPreparing track synchronization list:\n\n"
printf "%s\n" "${synklist[@]}"
printf "%b\n"
exit0
```

All doesn't actually do anything yet, and I broke Show.  So far so good.

I changed the nesting around, but there may be a better way to put this together still.

---

### Post by geirha on 2010-02-25
A few comments. on that last bit.

1. Uppercase variable names are used for internal shell variables (like REPLY and IFS), and environment variables (like PATH). The convention is to use lowercase names for everything else, to avoid accidentally overwriting internal shell variables or environment variables.

2. select is a loop. The until-loop you have around it is pointless.

3. «break && exit 0»  break exits a loop, so it will never reach that exit.

4. You are using both [[ and [ in the same script. Stick with one of them. Since this is bash, you should use [[ for file and string comparison, and (( for arithmetic comparison. As an added bonus, «[ "$REPLY" = "S" ]» can be changed to «[[ $REPLY = [Ss] ]]» to match both 's' and 'S', since [[ allows the RHS of = to be a [glob](http://mywiki.wooledge.org/glob).

5.
```

IFS=$'\n'
PLAYLISTS=($( grep playlist\ name.*type=\"static\" $RHYTHMBOXLISTS | awk -F '"' '{ print i$2 }' ))

```
This is an unsafe way of parsing data. The output of that grep|awk will be subjected to pathname expansion. The safe way is to use read. See [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001) for a more elaborate explanation.

```
playlists=()
while IFS='"' read -r _ playlist _; do 
  playlists+=( "$playlist" )
done < <(grep '<playlist name=.*type="static"' "$playlistfile")

```

6.
```

      else #solo?
           [[ $SELECTED ]] || continue
                if [[ ${SYNKLIST[REPLY]} ]]; then
                     unset 'SYNKLIST[REPLY]'
                     ...

```
That bit would look better like this:
```

      elif [[ $SELECTED ]]; then
          if [[ ${SYNKLIST[REPLY]} ]]; then
              unset 'SYNKLIST[REPLY]'
              ...

```
(and of course even better if you used lowercase variable names.)

---

### Post by jamesisin on 2010-02-25
Thanks for the suggestions.  I really appreciate it.  I have fixed everything but point 5 which will require some more reading on my part, so you can expect that sooner or later.

1. I guess I am used to seeing the system and built-in variables.  Fixed.
2. Altered the until loop to be useful.
3. Removed break to access exit.
4. Conformed all [ to [[ except where I thought they needed to be [ (synklist[REPLY]=$selected).  Let me know if I need to change others.
5. Skipped for now.
6. Your code was slightly wrong but I figured it out from your suggestion (else is necessary).

```
usage="\n\nPlease enter the number corresponding to the playlist you would like to synk. \n     Seperate multiple playlists with a space. \nA = synk ALL available playlists \nS = SHOW current selections \nQUIT = QUIT this script \n<ENTER> = display available playlists again \n\n"

rhythmboxlists="/home/$USER/.gnome2/rhythmbox/playlists.xml" # this changes in later versions

printf "\nI am currently set to use this Rhythmbox playlists file: \n"
printf "     $rhythmboxlists"
printf "\nI will synchronize music from this location: \n"
printf "     $library"
printf "\nwith this root folder on this particular music player: \n"
printf "     $rockbox\n\n"

read -p "Press <ENTER> to coninue. "

## obtain a list of playlists available
# IFS will alter the Internal Field Separator to the line break
# then grep parses out the playlist name lines
SAVEIF=$IFS
IFS=$'\n'
playlists=($( grep playlist\ name.*type=\"static\" $rhythmboxlists | awk -F '"' '{ print i$2 }' ))


## allow user to select playlists--include simple ALL and QUIT options
# count user generated playlists
count=0
for void in ${playlists[@]}; do
    count=$((count+1))
    done
    
# display a playlist count for the user
printf "%b" "\a\nI have found $COUNT user generated playlists:\n\n" >&2

# define array for collecting selected playlists
synklist=()

# Set a useful select prompt
PS3='Select the playlist(s) for syncrhonization (or help): '

# User types a number which is stored in $REPLY
# but $SELECTED returns the value (name of the playlist)

until [[ "$REPLY" == "NEXT" ]]; do
   select selected in "${playlists[@]}"; do
      if [[ "$REPLY" = "QUIT" ]]; then
           printf "\nGood-bye.\n\n"
           exit 0
      elif [[ "$REPLY" = "help" ]]; then
           printf $usage
      elif [[ "$REPLY" = [Aa] ]]; then
           if [[ ${#synklist[*]} != 0 ]]; then
                unset 'synklist[*]'
                printf "%b     Your synk list is now empty.\n"
           else [[ ${#synklist[*]} = 0 ]]
                synklist=("${playlists[@]}")
                printf "\nI will synchronize all $count playlists to your device.\n\n"
           fi
      elif [[ "$REPLY" = [Ss] ]]; then
           if [[ ${#synklist[*]} != 0 ]]; then
              printf "\nHere is what you have added thus far: \n"
              printf "%s\n" "${synklist[@]}"
	   else [[ ${#synklist[*]} = 0 ]]
              printf "\nYou have not yet added any playlists for synchronization.\n"
           fi
           printf "%b\n"
      elif [[ "$REPLY" = "NEXT" ]]; then
           break
      elif [[ $selected ]]; then
           if [[ ${synklist[REPLY]} ]]; then
                unset 'synklist[REPLY]'
                printf "%b     Now REMOVED from your synk list:     $selected\n"
           else synklist[REPLY]=$selected
                printf "%b     Now ADDED to your synk list:     $selected\n"
           fi
      else printf "\nI\'m sorry but \'$REPLY\' is not a valid entry."
           printf "$usage"
      fi
   done #select
done #until

printf "\nPreparing track synchronization list:\n\n"
printf "%s\n" "${synklist[@]}"
printf "%b\n"
exit 0
```

---

### Post by jamesisin on 2010-02-25
Ok, this phase looks like it's coming to completion.

I have fixed the case for A and S (I have left it caps for NEXT and QUIT).

I have added a response for bad entries (like w or an out of range number).

All will either empty for fill the synk list depending if it is currently empty or not.

Yeah, pretty much looks good.

Of course if I am making any bad coding decisions I'd love to hear about it.  Still a long way to go to finish the whole script.

Thanks for all your help those who stopped in and did so.

I have updated the previous code box to include the latest version of the code.

---

### Post by jamesisin on 2010-02-26
I have tested this replacement (as suggested by geirha) and it works:

```
# what I had come up with

#SAVEIF=$IFS
#IFS=$'\n'
#playlists=($( grep playlist\ name.*type=\"static\" $rhythmboxlists | awk -F '"' '{ print i$2 }' ))

# what geirha suggested

playlists=()
while IFS='"' read -r _ playlist _; do 
  playlists+=( "$playlist" )
done < <(grep '<playlist name=.*type="static"' "$rhythmboxlists")
```

I want to understand what it does though.

I see the field separator is now the double-quotes.  The output of grep is being used as the input for the array analysis.  Each playlist is put into the array as a unique element as it passed through the while loop.

I looked for information about read but there is no man page nor anything in info.  What does the -r do?  What do the underscores do?

---

### Post by falconindy on 2010-02-26
Underscores are valid variable names. They're "absorbing" assumed unneeded data. The '-r' flag prevents \ from acting as an escape char.

Note to self: I need to read that Bash wiki more often.

*me goes back to updating ~/bin*

---

### Post by jamesisin on 2010-02-26
I see, so without them I get results such as this:

```
32)   <playlist name="Return of Heavy Metal Man, the [16]" type="static">
```

With the underscores one absorbs [NOPARSE]'   <playlist name='[/NOPARSE] and the other absorbs [NOPARSE]' type="static">'[/NOPARSE] so that with them I get:

```
32) Return of Heavy Metal Man, the [16]
```

There must be something I'm still not getting because I would think the first result would have ended with the double-quote after type= (as I thought the double-quote was the new field separator).

It looks like using -r is a best practice and not so specific to my script:

> The -r option to read prevents backslash interpretation (usually used as a backslash newline pair, to continue over multiple lines). Without this option, any backslashes in the input will be discarded. You should always use the -r option with read.

---

### Post by geirha on 2010-02-26
> **jamesisin said:**
> 
```
32)   <playlist name="Return of Heavy Metal Man, the [16]" type="static">
```
There must be something I'm still not getting because I would think the first result would have ended with the double-quote after type= (as I thought the double-quote was the new field separator).


It reads from left to right, stopping at the first " (IFS-char), and putting everything up to that point into the variable given by the first name argument. Then it reads from the next char upto the next IFS-char, and puts that in the variable given by the second name argument. For the last one, it will just put the rest of the line.

```
$ read -r var1 var2 var3 <<< "one two three four"
$ printf "[%s]\n" "$var1" "$var2" "$var3"
[one]
[two]
[three four]

$ read -r var1 var2 <<< "one two three four"
$ $ printf "[%s]\n" "$var1" "$var2"
[one]
[two three four]

```

Oh, btw, read is a builtin, which means you shouldn't look for a separate man-page. It will be documented in the shell's man-page, and bash also has a help command which will show you information on a builtin or keyword.
```
$ type read
read is a shell builtin
$ help read
read: read [-ers] [-a array] [-d delim] [-i text] [-n nchars] [-p prompt] [-t timeout] [-u fd] [name ...]
    Read a line from the standard input and split it into fields.
[...]

```

---

### Post by jamesisin on 2010-02-26
Oops:

> For the last one, it will just put the rest of the line.

Standard behavior.  Wasn't thinking.

> It will be documented in the shell's man-page, and bash also has a help command which will show you information on a builtin or keyword.

Good enough.  Thanks for that.

---

