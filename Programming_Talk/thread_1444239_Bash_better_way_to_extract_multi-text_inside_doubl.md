---
title: "Bash: better way to extract multi-text inside double quotes"
date: 2010-04-01
forum: Programming Talk
---

### Post by iMisspell on 2010-04-01
Im trying to extract the name(s) in side the double quotes here, then pass that info to another function:

```
Sun VirtualBox Command Line Management Interface Version 3.1.6
(C) 2005-2010 Sun Microsystems, Inc.
All rights reserved.

"WinXP" {c01deb7e-c899-4edd-96b4-f033d2c62bbc}
"Lucid Lynx" {519fc43f-e6d7-4b23-8e31-63aa1fc620e6}
```

The "return" string needs to be something like:
**WinXP**|**Lucid Lynx**
or
**WinXP**delimiter-for-second-function**Lucid Lynx**

With the following sed i can get the second (Lucid Lynx), but not both.```
sed 's/.*"\(.*\)".*/\1/g'
```

Below is a (quite sloppy :( ) peice of the script im writing, if you have Vbox installed  you can test it out, if you want.
Right now i have a bunch of crap in the **askWhatVM_thenDisplayInfo()** function, which is working, but i would really like to know a more cleaner way of doing this.
[PHP]

#!/bin/bash

function displayOptions(){
# $1 = options
# $2 = question
# $3 = delimitor

displayOptions_res=null;

# check and set new delimitor
if [ $3 ] ; then
OIFS=$IFS
IFS="$3"
fi
 
declare -a Array=($1);
count=${#Array[@]};

echo "------------------------------------------------------------------------"
PS3="$2 (1-$count) ";

select displayOptions_res in $1
do
	break
done

if [ $3 ] ; then
IFS=$OIFS
fi

if [ "$displayOptions_res" = '' ]; then
	echo "****************************
      Error in entry."
	displayOptions "$1" "$2" "$3";
	return;
fi

echo -n "You choose ' $displayOptions_res ' (y/n)? ";
read;
[[ $REPLY = [yY] ]] || displayOptions "$1" "$2" "$3"; return;

}


function askWhatVM_thenDisplayInfo(){

questionIs="$1";

vms=`VBoxManage list vms`;

#vms=`echo $vms | sed 's/.*"\(.*\)".*/\1/g'`
#vms=`echo $vms | awk '{x[++c]=$4}END{for(i=1;i<=c;i++)print x[i]"|"}' FS="\""`

vms=`echo $vms | awk 'BEGIN{FS="\""}
{
for (i=1;i<=NF;i++)
print $i"|"
}'`

vms=`echo $vms | sed 's/\n//g'`

OIFS=$IFS
IFS="|"
c=0;

for n in $vms ; do

c=$(( c+ 1 ));
if [ $(( c % 2 )) == 0 ]; then
out=$out$n"|";
fi
   
done
IFS=$OIFS

out=`echo $out | sed 's/\s|/|/g'`
out=`echo $out | sed 's/|\s/|/g'`

displayOptions "$out" "$questionIs" "|"
vmGuestName="$displayOptions_res";

showvminfo=`VBoxManage showvminfo "$vmGuestName"`
echo "========================================
$showvminfo
=======================================
"
	
}
askWhatVM_thenDisplayInfo "Test Question For Select";

exit 0;

[/PHP]


----------------------------------------------
What im trying to do, if you care...
Create a "utility" script to work with Virtualbox from the command line on on my server.

The above function will be called at different points in the script (depending what i want/need to do) to get the names of the vbox guests installed to make editing there config easyer.

Any guidance would be great.

_

---

### Post by myrtle1908 on 2010-04-01
In Perl you can do it this way (i'm sure a sed/bash person can give you suitable equivalent) ...

```
use strict;
use warnings;

my $s = 'Sun VirtualBox Command Line Management Interface Version 3.1.6
(C) 2005-2010 Sun Microsystems, Inc.
All rights reserved.

"WinXP" {c01deb7e-c899-4edd-96b4-f033d2c62bbc}
"Lucid Lynx" {519fc43f-e6d7-4b23-8e31-63aa1fc620e6}';

my @q = ($s =~ m/"(.*?)"/g);

print join '|', @q;
```

Yields:-

```
WinXP|Lucid Lynx
```

---

### Post by iMisspell on 2010-04-01
Thanks for the perl tip, myrtle1908.

Just played around little more, by using this:
```
vms=`echo $vms | awk 'BEGIN { RS="\"" } { print $0 "|"}'`
```

In place of this:
```
vms=`echo $vms | awk 'BEGIN{FS="\""}
{
for (i=1;i<=NF;i++)
print $i"|"
}'`
```

It cleans things up a little, but there has to be a better way.

Gonna try to piping that to something, some how and see what happens :)

**[EDIT]**
After more fiddling the following is working...

```
vms=`echo $vms | awk 'BEGIN { RS="\"" } { if(NR % 2 == 0) print $0 "|"}'`
vms=`echo $vms | sed 's/\n//g'`
vms=`echo $vms | sed 's/\s|/|/g'`
vms=`echo $vms | sed 's/|\s/|/g'`

```

Testing....
[PHP]
#!/bin/bash

vms='Sun VirtualBox Command Line Management Interface Version 3.1.6
(C) 2005-2010 Sun Microsystems, Inc.
All rights reserved.

"WinXP" {c01deb7e-c899-4edd-96b4-f033d2c62bbc}
"Lucid Lynx" {519fc43f-e6d7-4b23-8e31-63aa1fc620e6}
';

vms=`echo $vms | awk 'BEGIN { RS="\"" } { if(NR % 2 == 0) print $0 "|"}'`
vms=`echo $vms | sed 's/\n//g'`
vms=`echo $vms | sed 's/\s|/|/g'`
vms=`echo $vms | sed 's/|\s/|/g'`

echo "$vms";

[/PHP]

**[EDIT Again]**
Ended up with the following (using the awk in last edit).
Would still like to hear what others have o say, but im happy with how it is now, much easyer to read in my opinion.
[php]
#!/bin/bash

function displayOptions(){
# $1 = options
# $2 = question
# $3 = delimitor

displayOptions_res=null;

# check and set new delimitor
if [ $3 ] ; then
OIFS=$IFS
IFS="$3"
fi
 
declare -a Array=($1);
count=${#Array[@]};

echo "------------------------------------------------------------------------"
PS3="$2 (1-$count) ";

select displayOptions_res in $1
do
	break
done

if [ $3 ] ; then
IFS=$OIFS
fi

if [ "$displayOptions_res" = '' ]; then
	echo "****************************
      Error in entry."
	displayOptions "$1" "$2" "$3";
	return;
fi

echo -n "You choose ' $displayOptions_res ' (y/n)? ";
read;
[[ $REPLY = [yY] ]] || displayOptions "$1" "$2" "$3"; return;

}


function askWhatVM_thenDisplayInfo(){

questionIs="$1";

vms=`VBoxManage list vms`;

# Split/replace string at double quotes with pipe(s), print out the 'even' chunks (the names)
vms=`echo $vms | awk 'BEGIN { RS="\"" } { if(NR % 2 == 0) print $0 "|"}'`
vms=`echo $vms | sed 's/\n//g'` # Remove line breaks
vms=`echo $vms | sed 's/\s|\||\s/|/g'` # Remove single space on eather sides os pipe

displayOptions "$vms" "$questionIs" "|"
vmGuestName="$displayOptions_res";

showvminfo=`VBoxManage showvminfo "$vmGuestName"`
echo "========================================
$showvminfo
=======================================
";
}
askWhatVM_thenDisplayInfo "Test Question For Select";

exit 0;
[/php]
_

---

### Post by falconindy on 2010-04-01
```
vms=($VBoxManage list vms | sed -n 's|"\(.*\)".*|\1|p'))
```

Single line of sed assigned to a bash array gives you a nicely accessible list.

---

### Post by geirha on 2010-04-01
I've shortened the script down a bit, and instead of generating a string of names delimited by |, I changed it to pass each name as a separate argument.

```
#!/bin/bash 

# displayOptions QUESTION DISPLAYOPTIONS...
displayOptions() { 
    local question=$1 old_ps3=$PS3 name
    shift

    printf "%$(tput cols)s\n" "" | tr ' ' '-' >&2
    PS3="$question (1-$#) " 
    select name; do 
        [[ $name ]] && break 
    done 
    PS3=$old_ps3

    printf "%s" "$name"
} 

# askWhatVM_thenDisplayInfo QUESTION
askWhatVM_thenDisplayInfo() { 
    local question=$1 names name vmGuestName

    names=()
    while IFS=\" read _ name _; do 
        [[ $name ]] || continue
        names+=("$name")
    done < <(VBoxManage list vms)

    vmGuestName=$(displayOptions "$question" "${names[@]}")

    echo ======================================= 
    VBoxManage showvminfo "$vmGuestName"
    echo ======================================= 
} 

askWhatVM_thenDisplayInfo "Test Question For Select"; 

```

---

### Post by iMisspell on 2010-04-01
Thanks so much everyone, been a great help.
Off to work now so no time to play, will post back later.


**[EDIT]**
What do the _ underscores do here...
```
while IFS=\" read _ name _; do 
```

_

---

### Post by geirha on 2010-04-01
> **iMisspell said:**
> 
**[EDIT]**
What do the _ underscores do here...
```
while IFS=\" read _ name _; do 
```

_

They are placeholders. _ is a special var which will contain the last argument of the last executed command, so anything you assign to it, will quickly be "lost".

```
$ IFS=\" read before middle after <<< 'blabla "something inside quotes" something else'
$ echo -e "before:$before\nmiddle:$middle\nafter:$after"
before:blabla 
middle:something inside quotes
after: something else

```
Since we're only interested in the part inside quotes, we assign everything else to _. Kind of like a /dev/null var.

---

### Post by iMisspell on 2010-04-02
OK, a few more questions.

First: I would really like to have the *"You Choose 'this' (y/n)"* (i think its a nice option and once this script is done i plan on posting it online for others to use if they want, so i think its a good "fail safe")
So instead of calling the function with **var=$(function string arr)** i now call it with **function string arr** and changed the function to "return nothing", and have the selection var a global var and then just read that global var. 
* Is there a way around this ?
I like the "return string" and not having to use a global (now that i know how, before this i could only return integers).
When trying to call with **var=$(function string arr)** i was not able to use echo's 'read' correctly. The echo string would be blank when its called *with-in* the function, but **after** answering the y/n question, it would then print the full string if 'y' was selected, or it would recall the function

And why does it not matter if the following is comment-out or not ?
**printf "%$(tput cols)s\n" "" | tr ' ' '-' >&2**

**"Working"**
[php]
displayOptions() {
		local question=$1 old_ps3=$PS3
		shift
		
		displayOptions_res=null;
		
		#printf "%$(tput cols)s\n" "" | tr ' ' '-' >&2
		PS3="$question (1-$#) " 
		select displayOptions_res; do 
			[[ $displayOptions_res ]] && break
		done 
		PS3=$old_ps3	
		
		echo -n "You choose '$displayOptions_res' (y/n)? "
		read
		[[ $REPLY = [yY] ]] || displayOptions "$question" "$@"; return;
}

# askWhatVM_thenDisplayInfo QUESTION
askWhatVM_thenDisplayInfo() { 
    local question=$1 names name vmGuestName

    names=()
    while IFS=\" read _ name _; do 
        [[ $name ]] || continue
        names+=("$name")
    done < <(VBoxManage list vms)

    #vmGuestName=$(displayOptions "$question" "${names[@]}")
	displayOptions "$question" "${names[@]}"
	vmGuestName="$displayOptions_res"
	
    echo ================================================== 
    VBoxManage showvminfo "$vmGuestName"
    echo ================================================== 
} 
askWhatVM_thenDisplayInfo "Select Guest"
[/php]


**"broken"**
[php]

displayOptions() { 
    local question=$1 old_ps3=$PS3 name
    shift

    printf "%$(tput cols)s\n" "" | tr ' ' '-' >&2
    PS3="$question (1-$#) " 
    select name; do 
        [[ $name ]] && break 
    done 
    PS3=$old_ps3

    echo -n "You choose '$displayOptions_res' (y/n)? "
    read
    [[ $REPLY = [yY] ]] || displayOptions "$question" "$@"; return;

    printf "%s" "$name"
} 



# askWhatVM_thenDisplayInfo QUESTION
askWhatVM_thenDisplayInfo() { 
    local question=$1 names name vmGuestName

    names=()
    while IFS=\" read _ name _; do 
        [[ $name ]] || continue
        names+=("$name")
    done < <(VBoxManage list vms)

    vmGuestName=$(displayOptions "$question" "${names[@]}")
	#displayOptions "$question" "${names[@]}"
	#vmGuestName="$displayOptions_res"
	
    echo ================================================== 
    VBoxManage showvminfo "$vmGuestName"
    echo ================================================== 
} 
askWhatVM_thenDisplayInfo "Select Guest"
[/php]


second question.
Is there a better way to do this
[php]
choice_OSfromList() {
	local names name name2
	
    names=()
    while IFS=":\n " read _ name name2; do 
        [[ $name ]] || continue
        names+=("$name$name2")
    done < <(VBoxManage list ostypes)
    
    unset names[0]
    unset names[1]
    unset names[2]
    
    displayOptions "Select OS" "${names[@]}"
    	
}
choice_OSfromList
echo "Selected OS = $displayOptions_res"
[/php]

I have to do more research now how to use IFS correctly
Notice that i have to use the second and third "results" from the  'while read' in order to get the correct information from the 'ostypes'
**while IFS=":\n " read _ name name2; do**

_

---

### Post by geirha on 2010-04-02
> **iMisspell said:**
> OK, a few more questions.

First: I would really like to have the *"You Choose 'this' (y/n)"* (i think its a nice option and once this script is done i plan on posting it online for others to use if they want, so i think its a good "fail safe")
Rather than calling the function again, I suggest just using a loop.
> **iMisspell said:**
> 
And why does it not matter if the following is comment-out or not ?
**printf "%$(tput cols)s\n" "" | tr ' ' '-' >&2**


Because it redirects the output to stderr (>&2). select also outputs to stderr, and var=$(cmd) only catches stdout of cmd, stderr will still go to the terminal. So if you redirect the output of that echo to stderr, it will work fine. Alternatively, use the read command to output it.

```
displayOptions() { 
    local question=$1 old_ps3=$PS3 name
    shift

    while true; do
        printf "%$(tput cols)s\n" "" | tr ' ' '-' >&2
        PS3="$question (1-$#) " 
        select name; do 
            [[ $name ]] && break 
        done 
        PS3=$old_ps3
        
        read -p "You choose '$name' (y/N)? "
        [[ $REPLY = [Yy] ]] && break
    done

    printf "%s" "$name"
} 

```


> **iMisspell said:**
> 
**"broken"**
[php]

displayOptions() { 
    local question=$1 old_ps3=$PS3 name
    shift

    printf "%$(tput cols)s\n" "" | tr ' ' '-' >&2
    PS3="$question (1-$#) " 
    select name; do 
        [[ $name ]] && break 
    done 
    PS3=$old_ps3

    echo -n "You choose '$displayOptions_res' (y/n)? "
    read
    [[ $REPLY = [yY] ]] || displayOptions "$question" "$@"; return;

    printf "%s" "$name"
} 
[/php]


Two reasons why this is broken. As mentioned before, echo outputs to stdout, so that will be caught by the command substitution, adding >&2 to the end of the echo line or using read -p instead will fix that. The second problem is that the printf at the end will never be reached because the return will be run no matter what the exit status of [[ $REPLY = [yY] ]] is.

```
[[ $REPLY = [yY] ]] || displayOptions "$question" "$@"; return;
```

is equivalent to
```
if [[ $REPLY != [yY] ]]; then
  displayOptions "$question" "$@"
fi
return

```


> **iMisspell said:**
> 
second question.
Is there a better way to do this
[php]
choice_OSfromList() {
	local names name name2
	
    names=()
    while IFS=":\n " read _ name name2; do 
        [[ $name ]] || continue
        names+=("$name$name2")
    done < <(VBoxManage list ostypes)
    
    unset names[0]
    unset names[1]
    unset names[2]
    
    displayOptions "Select OS" "${names[@]}"
    	
}
choice_OSfromList
echo "Selected OS = $displayOptions_res"
[/php]

I have to do more research now how to use IFS correctly
Notice that i have to use the second and third "results" from the  'while read' in order to get the correct information from the 'ostypes'
**while IFS=":\n " read _ name name2; do**

_

IFS=":\n " will use the four characters :, \, n and space as field separator. If you want a newline in there, use the special $'' quoting. IFS=$':\n '. Anyway, the default IFS will do for that case. You just want the part after ID:, right? or the part after Description:?

```

    while read key value; do 
        [[ $key = "Description:" ]] || continue
        names+=("$value")
    done < <(VBoxManage list ostypes)

```

Alternatively, you can grep out the lines that start with Description:
```

    while read _ value; do 
        names+=("$value")
    done < <(VBoxManage list ostypes | grep '^Description:')

```


See [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)

---

### Post by iMisspell on 2010-04-02
geirha, good thing you don't charge money for your explanations and help, I'd be broke from what ive learned in this thread alone, thanks.

For what im doing the following question would not matter, but.
> **geirha said:**
> Rather than calling the function again, I suggest just using a loop.By using a loop in this fashion, doesn't it burn up resources being its "active" in till the last questions (You choose ?) is answered ? And by calling the function a second time, you are not in a loop and less system resources are being used ?
Just wondering.


> **geirha said:**
> 
The second problem is that the printf at the end will never be reached because the return will be run no matter what the exit status of [[ $REPLY = [yY] ]] is.

```
[[ $REPLY = [yY] ]] || displayOptions "$question" "$@"; return;
```

is equivalent to
```
if [[ $REPLY != [yY] ]]; then
  displayOptions "$question" "$@"
fi
return

```

I see, that makes since and i should have realized that.
Your way is more elegant, i would have done the following...
[php]
		if [[ $REPLY != [yY] ]]; then
		  displayOptions "$question" "$@"
		  return;
		fi
[/php]


> **geirha said:**
> You just want the part after ID:, right?

Yes the ID: - its gonna be used for **'VBoxManage createvm --name "$vmNewGuestName" --ostype $os --register'**

Pretty sure i like this, the thought just popped into my head of trying to keep this compleatly 'Bash' based with no extrunal programs needed (even though sed and grep arnt that bing of a deal, plus its a good learning script for me :) ).
[php]
choice_OSfromList() {
	local res key value names
	
    while read key value; do 
        [[ $key = "ID:" ]] || continue
        names+=("$value")
    done < <(VBoxManage list ostypes)
    
    unset names[0]
    res=$(displayOptions "Select O/S" "${names[@]}")
    print "$res"
}

os=$(choice_OSfromList)
echo "Selected OS = $os"
}

os=$(choice_OSfromList)
echo "Selected OS = $os"
[/php]


Thanks again, you've been great.
_

---

### Post by geirha on 2010-04-02
> **iMisspell said:**
> For what im doing the following question would not matter, but.
By using a loop in this fashion, doesn't it burn up resources being its "active" in till the last questions (You choose ?) is answered ? And by calling the function a second time, you are not in a loop and less system resources are being used ?
Just wondering.

No, a loop will typically use less resources than recursing functions. If you say no four times, you'll have 5 functions "open".
[http://en.wikipedia.org/wiki/Recursion_(computer_science)#Recursion_versus_iteration](http://en.wikipedia.org/wiki/Recursion_(computer_science)#Recursion_versus_iteration)


> **iMisspell said:**
> 
[php]
choice_OSfromList() {
	local res key value names
	
    while read key value; do 
        [[ $key = "ID:" ]] || continue
        names+=("$value")
    done < <(VBoxManage list ostypes)
    
    unset names[0]
    res=$(displayOptions "Select O/S" "${names[@]}")
    print "$res"
}

os=$(choice_OSfromList)
echo "Selected OS = $os"
}

os=$(choice_OSfromList)
echo "Selected OS = $os"
[/php]

I'm quite sure you don't want to use the print command there. Either «printf "%s" "$res"» or «echo "$res"», though judging from the duplicate lines below, I'm guessing that's just something introduced by a bad copy/paste.

One last thing though, names[0] should be quoted.
```
unset "names[0]"
```
Otherwise, pathname expansion will be attempted, and names[0] will match a file named names0 if it exists.

```
$ echo names[0]
names[0]
$ touch names0
$ echo names[0]
names0
$ echo "names[0]"
names[0]

```

---

