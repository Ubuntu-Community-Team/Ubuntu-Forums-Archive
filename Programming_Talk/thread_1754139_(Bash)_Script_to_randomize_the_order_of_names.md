---
title: "(Bash) Script to randomize the order of names"
date: 2011-05-09
forum: Programming Talk
---

### Post by jakupl on 2011-05-09
As a part of a larger bash script, I want a script to ask for input "names", one at a time.
The number of names varies, so it needs to stop asking after the last input.

 It has to input commas after each name until the second to last name, where it inserts "and", like this:

```
name1, name2, name2, ...etc... name8, and name9
```

Aaand the order of the names has to be random.

Does anyone know of a nice way to do this in bash?

Any help is greatly appreciated

---

### Post by lloyd_b on 2011-05-09
This looks suspiciously like a homework problem, which we generally won't just provide code for.  If you have something that sorta works, you can post that, and we'll be happy to point out any problems and offer suggestions.

One hint for you - look at the options of the 'sort' command ("man sort" in a terminal window).  'sort' can easily handle one part of your problem.

Lloyd B.

---

### Post by jakupl on 2011-05-10
> **lloyd_b said:**
> This looks suspiciously like a homework problem, which we generally won't just provide code for.  If you have something that sorta works, you can post that, and we'll be happy to point out any problems and offer suggestions.

One hint for you - look at the options of the 'sort' command ("man sort" in a terminal window).  'sort' can easily handle one part of your problem.

Lloyd B.

Thankyou. I will look further into it when I get home.
This however is certantly not homework. I am a musician, not a programmer. Otherwise I would be better at it than this.
I need this for automation of some common tasks that I do.

I tried something that almost worked, but had an impossible problem. It was a completely wrong approach, that's why I didn't post it.

Thanks for your time.

---

### Post by jakupl on 2011-05-10
I suppose I could do something like this:
```
echo "write the names"
read name1
read name2
read name3
read name4
read name5
read name6
read name7
read name8
```
"Assuming the max number of names would be 8"

then use cat to put all names into a file and use sed to delete empty lines.

Then I could use this to shuffle the lines randomly

[http://mywiki.wooledge.org/BashFAQ/026](http://mywiki.wooledge.org/BashFAQ/026)

that would result in a file that looks like this:


```
Donald Duck
Daisy Duck
Magica De Spell
Gyro Gearloose
Scrooge McDuck
```
I think I know how to do this.
-----------------------------------------------------------------------------
The problem is now:
The number of names varies.

How do I get the names in a variable like this:

```
Donald Duck, Daisy Duck, Magica De Spell, Gyro Gearloose and Scrooge McDuck
```

---

### Post by DaithiF on 2011-05-10
store the names in an array as you read them, the iterate over the array adding whatever seperator is appropriate depending on the position.  the complicated part is the random sorting of the array, but borrowing the shuffle function from [http://mywiki.wooledge.org/BashFAQ/026](http://mywiki.wooledge.org/BashFAQ/026)
gives something like:

```
shuffle() {
   local i tmp size max rand

   # $RANDOM % (i+1) is biased because of the limited range of $RANDOM
   # Compensate by using a range which is a multiple of the array size.
   size=${#array
[*]}
   max=$(( 32768 / size * size ))

   for ((i=size-1; i>0; i--)); do
      while (( (rand=$RANDOM) >= max )); do :; done
      rand=$(( rand % (i+1) ))
      tmp=${array[i]} array[i]=${array[rand]} array[rand]=$tmp
   done
}

while true
do
    read -p "enter a name or quit to exit: " name
    [[ $name == quit ]] && break
    array=("${array[@]}" "$name")
done

shuffle

i=0
for name in "${array[@]}"
do
    ((i++))
    (( i > 1 )) && sep=", " || sep=""
    (( i == ${#array[@]} )) && sep=" and "
    printf "${sep}${name}"
done

```

```
$ ./1
enter a name or quit to exit: Donald Duck
enter a name or quit to exit: Daisy Duck
enter a name or quit to exit: Magica De Spell
enter a name or quit to exit: etc
enter a name or quit to exit: quit
Donald Duck, Magica De Spell, Daisy Duck and etc

```

---

### Post by jakupl on 2011-05-10
> **DaithiF said:**
> store the names in an array as you read them, the iterate over the array adding whatever seperator is appropriate depending on the position.  the complicated part is the random sorting of the array, but borrowing the shuffle function from [http://mywiki.wooledge.org/BashFAQ/026](http://mywiki.wooledge.org/BashFAQ/026)
gives something like:

```
shuffle() {
   local i tmp size max rand

   # $RANDOM % (i+1) is biased because of the limited range of $RANDOM
   # Compensate by using a range which is a multiple of the array size.
   size=${#array
[*]}
   max=$(( 32768 / size * size ))

   for ((i=size-1; i>0; i--)); do
      while (( (rand=$RANDOM) >= max )); do :; done
      rand=$(( rand % (i+1) ))
      tmp=${array[i]} array[i]=${array[rand]} array[rand]=$tmp
   done
}

while true
do
    read -p "enter a name or quit to exit: " name
    [[ $name == quit ]] && break
    array=("${array[@]}" "$name")
done

shuffle

i=0
for name in "${array[@]}"
do
    ((i++))
    (( i > 1 )) && sep=", " || sep=""
    (( i == ${#array[@]} )) && sep=" and "
    printf "${sep}${name}"
done

```

```
$ ./1
enter a name or quit to exit: Donald Duck
enter a name or quit to exit: Daisy Duck
enter a name or quit to exit: Magica De Spell
enter a name or quit to exit: etc
enter a name or quit to exit: quit
Donald Duck, Magica De Spell, Daisy Duck and etc

```

Wow awesome! You solved it. Thanks very much.

---

### Post by jakupl on 2011-05-10
So this is the final product of this piece of the script, if anyone needs something similar.

```
#!/bin/bash
shuffle() {
	local i tmp size max rand

	size=${#array[*]}
	max=$(( 32768 / size * size ))

	for ((i=size-1; i>0; i--)); do
		while (( (rand=$RANDOM) >= max )); do :; done
		rand=$(( rand % (i+1) ))
		tmp=${array[i]} array[i]=${array[rand]} array[rand]=$tmp
	done
}


while [ "$var1" != "yes" ]
do
	echo "Write one name at the time"
	unset array


	while true
	do
		read -p "quit to exit: " name
		[[ $name == quit ]] && break
		array=("${array[@]}" "$name")
	done
	
	shuffle
	
	i=0
	for name in "${array[@]}"
	do
		((i++))
		(( i > 1 )) && sep=", " || sep=""
		(( i == ${#array[@]} )) && sep=" and "
		printf "${sep}${name}" > fil1
		cat fil2 fil1 > fil3
		rm fil2 fil1
		mv fil3 fil2
	done
	people=`cat fil2`
	rm fil2
	echo
	echo
	echo
	echo "$people"
	echo
	
	
	echo "Is this okay? write yes to continue, press enter to write names again."
	read var1
	echo
done
echo "$people"
```

The only problem with it is, that if there only is one name, then the output will still include " and" with a leading space
```
 and Donald Duck
```
But that will never happen for me, so this is fine.

---

### Post by DaithiF on 2011-05-10
> **jakupl said:**
> The only problem with it is, that if there only is one name, then the output will still include " and" with a leading space

thats easily fixed:
(( i == ${#array[@]}** && i > 1 **)) && sep=" and "

---

### Post by kaibob on 2011-05-10
The OP has marked this thread as solved, but I wanted to use it as a learning aid to work on certain bash skills and thought I would post my final shell script. 

```

#!/bin/bash

while true ; do
  read -p "Enter a name or (m)ake string or (e)xit: " keypress
  case "$keypress" in
    ""  ) continue ;;
    "m" ) [[ "${names[*]}" ]] && break || exit 1 ;;
    "e" ) exit 0 ;;
     *  ) names+=("$keypress") ; continue ;;
  esac
done

num="${#names[*]}" ; y=$((num-2)) ; z=$((num-1))

mapfile -t output < <( printf "%s\n" "${names[@]}" | sort -R)

if [[ "${num}" -eq 1 ]] ; then
  printf "%s\n" "${output[0]}"
elif [[ "${num}" -eq 2 ]] ; then
  printf "%s and %s\n" "${output[0]}" "${output[1]}"
else
  printf "%s, " "${output[@]:0:${y}}" ; printf  "%s and %s\n" "${output[y]}" "${output[z]}"
fi

```

---

