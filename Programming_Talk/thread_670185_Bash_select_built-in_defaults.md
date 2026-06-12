---
title: "Bash select built-in defaults"
date: 2008-01-17
forum: Programming Talk
---

### Post by flightless bird on 2008-01-17
I have used the bash select built-in to generate a menu from and array,l but I would like there to be a default option in the case of the user just pressing enter other than the standard select procedure of repeating the options. Is there a way of specifying default behaviour? I have tried 

```
for opt in $options
   do
      if [ -z "$opt" ]
         then
#         the default action here
      fi
      case ... # rest of options from here
```

as well as 

```
for opt in $options
   do
      if [ "$REPLY" -lt 1 ]
         then
#         the default action here
      fi
      case ... # rest of options from here
```

but so far no luck. The rest of the menu works just fine though.Any ideas :confused:

---

### Post by naugiedoggie on 2008-01-17
> **flightless bird said:**
> I have used the bash select built-in to generate a menu from and array,l but I would like there to be a default option in the case of the user just pressing enter other than the standard select procedure of repeating the options. Is there a way of specifying default behaviour? I have tried 

```
for opt in $options
   do
      if [ -z "$opt" ]
         then
#         the default action here
      fi
      case ... # rest of options from here
```

but so far no luck. The rest of the menu works just fine though.Any ideas :confused:

Hello,

If I am reading your code correctly, you are using a case statement to pick up the appropriate option.  The standard deployment of case is like this in Bash:

```
case "$var" in
    value1)
         commands;
         ;;
    value2)
         commands;
         ;;
    *)
         commands;
         ;;
esac
```

The last item, "*", is the fall-through.  Everything that doesn't fall into the list of values is picked up there.  So, you can use that to catch your ENTER key.  

You can set a default value in a variable and then check the number of args in the command line.  If the count is zero, then you know that the user just pressed the enter key.  Process the default variable at that point.  You should be able to do that in the "*" section.

Alternatively, you could check your argument count at the top of the script and set your variable there.  This is a fairly normal method, for the case where you want to provide a help message for users who don't provide the proper command line options.

Users who don't know the application might not know what will happen when they just press the ENTER key.

Here's an example:

```
 #!/bin/bash

if [ -z "$1" ] ; then
    echo "insufficient options"
    exit 1
fi

OPTIONS="Hello Quit"

select opt in $OPTIONS; do

    if [ "$opt" = "Quit" ]; then
	    echo finished
	    exit
    elif [ "$opt" = "Hello" ]; then
	    echo Hello World
    else
	    clear
	    echo bad option
    fi
done
```

Thanks.

mp

---

### Post by flightless bird on 2008-01-17
Hi there,

thanks for the reply. I tried both your suggestions (* to catch what falls through case and else to catch what falls through if), and neither of them caught the ENTER key, instead I got the standard repeat of the options menu.

cheers

---

### Post by naugiedoggie on 2008-01-17
> **flightless bird said:**
> Hi there,

thanks for the reply. I tried both your suggestions (* to catch what falls through case and else to catch what falls through if), and neither of them caught the ENTER key, instead I got the standard repeat of the options menu.

cheers

Hello,

The code example I added at the end works, I tested it.  You just need to modify it for your particular case.

Here's a complete example:

```

 #!/bin/bash

OPTIONS="Hello Quit"

function hello {
	echo hello
}

function quit {
	if [ -z $1 ]; then
		echo quitting now
		echo because of no arguments
		echo
		exit 1
	else
		echo quitting normally
	fi
	exit 0
}

function error_quit {
	echo quitting because of an error
	exit 1
}


if [ -z "$1" ] ; then
	quit
fi

select opt in $OPTIONS; do

    if [ "$opt" = "Quit" ]; then
	    quit n
	    exit
    elif [ "$opt" = "Hello" ]; then
	    echo Hello World
    else
	    clear
	    error_quit
    fi
done

```

Output:
```

powem@ellen:~/bin$ ./select.sh
quitting now
because of no arguments

powem@ellen:~/bin$ ./select.sh h
1) Hello
2) Quit
#? 2
quitting normally
powem@ellen:~/bin$ 

```

IMO, shell scripting is a complete PITA.  So, I feel your pain.  ;-)  It's hard to get a grip on a syntax and style that haven't updated in over 30 years and have become far removed from modern styles.

Thanks.

mp

---

### Post by flightless bird on 2008-01-18
Thanks again, I'm sorry about that - I guess I must be doing something dumb somewhere. I tried the example you put at the bottom of your post and I get the same behaviour, endless repeating of the menu list. I can't get it to use the error_quit  function it should use as a default. 

Just for the record, here is the actual code snippet that is causing the confusion for me: ```
	select SONG in "${tracks[@]}" 'This all looks sweet, crack on [default]' 'quit' 
		do
		if [ $REPLY -le $trackno ]; then
			  read -p "Enter new track name and press ENTER:" new_name
	        	  tracks[$(($REPLY-1))]=$new_name
			  echo -e "Cool, track $REPLY changed to \033[1m${tracks[$(($REPLY-1))]}\033[0m";
		elif [ "$SONG" = 'quit' ]; then
			  echo "Exiting."
			  exit 3 # user aborted
			  break;
		else 
			  break;
		fi
		
	done

``` As you can see, it is a menu from a little music tagging utility I have written, with this section taking the track names that have been automatically gathered and checking them with the user, allowing each track to be selected by number and renamed if necessary. The as you can see, if ENTER alone is pressed, I would have expected the selection to break and proceed with the default option, but the actual behaviour observed is that the menu is simply repeated. Selecting the number equivalent to the default option (ie. $(($trackno+1)) )works fine, as, predictably, does any number higher than $(($trackno+2)). Entering a non integer string results in the default behaviour with the following error code: ```
: line 223: [: a: integer expression expected

```.

Again, thanks for your help. This issue clearly doesn't massively effect the usability of the script - this is just a minor cosmetic point really.

---

### Post by stroyan on 2008-01-18
Select is only doing exactly what the manual says it will do.
You could get the effect you want by using echo and read instead of the select feature.
Here is a function that acts much like select (without the looping behavior).```

$ function choose() {
    local v e
    typeset -i i=1
    v=$1
    shift 2
    for e in "$@"
    do
        echo "$i) $e"
        i=i+1
    done
    read REPLY
    i="$REPLY"
    if [ $i -gt 0  -a  $i -le $# ] 
    then
        eval $v="\$$i"
    else
        eval $v=""
    fi 
}
$ choose V in a b c "something a little longer"; echo $REPLY chose $V
1) a
2) b
3) c
4) something a little longer
3
3 chose c
$ choose V in a b c "something a little longer"; echo $REPLY chose $V
1) a
2) b
3) c
4) something a little longer
4
4 chose something a little longer
$ choose V in a b c "something a little longer"; echo $REPLY chose $V
1) a
2) b
3) c
4) something a little longer

chose

```

---

### Post by naugiedoggie on 2008-01-18
> **flightless bird said:**
> 

Just for the record, here is the actual code snippet that is causing the confusion for me: ```
	select SONG in "${tracks[@]}" 'This all looks sweet, crack on [default]' 'quit' 
		do
		if [ $REPLY -le $trackno ]; then
			  read -p "Enter new track name and press ENTER:" new_name
	        	  tracks[$(($REPLY-1))]=$new_name
			  echo -e "Cool, track $REPLY changed to \033[1m${tracks[$(($REPLY-1))]}\033[0m";
		elif [ "$SONG" = 'quit' ]; then
			  echo "Exiting."
			  exit 3 # user aborted
			  break;
		else 
			  break;
		fi
		
	done

``` As you can see, it is a menu from a little music tagging utility I have written, with this section taking the track names that have been automatically gathered and checking them with the user, allowing each track to be selected by number and renamed if necessary. The as you can see, if ENTER alone is pressed, I would have expected the selection to break and proceed with the default option, but the actual behaviour observed is that the menu is simply repeated. Selecting the number equivalent to the default option (ie. $(($trackno+1)) )works fine, as, predictably, does any number higher than $(($trackno+2)). Entering a non integer string results in the default behaviour with the following error code: 

```
: line 223: [: a: integer expression expected

```.

Again, thanks for your help. This issue clearly doesn't massively effect the usability of the script - this is just a minor cosmetic point really.


Hee-hee, don't you just love the exception handling in shell scripts.  So informative, too.  I've injured some walls with my head (and my head with some desks) over those beauties.

Well, I can take a closer look in the morning.  I'm trying to get away from my desk right now.  ;-)  It could even be that select just won't do it in the manner deployed.

You might look/ask in [comp.unix.shell]("http://groups.google.com/group/comp.unix.shell/topics?hl=en&lnk=sg") -- the scripting gods live there.

Thanks.

mp

---

### Post by flightless bird on 2008-01-20
Thanks to both of you for taking the time to reply. I had read the manual on select and [http://tldp.org/LDP/abs/html/testbranch.html#EX31](http://tldp.org/LDP/abs/html/testbranch.html#EX31), and it I didn't find mention of a way to change the default looping behaviour. I was just hoping against hope that someone out there knew some clever trick ;) cheers though.

---

