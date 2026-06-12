---
title: "Somebody wanna test my &quot;./kernel_headers_check.sh&quot; script?"
date: 2008-07-02
forum: Programming Talk
---

### Post by jingo811 on 2008-07-02
Somebody wanna test my "./kernel_headers_check.sh" script?
It shouldn't require much time unless I made some huge mistake with the logics.  Just manipulate the "$KH_COMMANDS_XXX" variables for testing.

[PHP]
#!/bin/bash


#######   Check if your kernel headers is at least version 2.6.6 or 2.4.26   #######


############   Howto run the script!   ############   maintainer: Witch   ##########
#
#	./kernel_headers_check.sh
#
####################################################################################

KH_COMMAND_ORIGIN=`/bin/uname -r`
# KH_COMMAND_NUMERICAL=`/bin/uname -r | awk -F '-' '{print $1}'`

KH_COMMAND_01=`/bin/uname -r | awk -F '.' '{ print $1 }'`
#	KH_COMMAND_01=1

KH_COMMAND_02=`/bin/uname -r | awk -F '.' '{ print $2 }'`
#	KH_COMMAND_02=4

KH_COMMAND_03_ALPHA=`/bin/uname -r | awk -F '.' '{ print $3 }'`
KH_COMMAND_03_BETA=`echo $KH_COMMAND_03_ALPHA | awk -F '-' '{ print $1 }'`
#	KH_COMMAND_03_BETA=26

####################################################################################
[/PHP]

---

### Post by ghostdog74 on 2008-07-02
you can do something like this. No need too much awk. Also, no need too much echoes if you use here documents.
```

#!/bin/bash
IFS="."
set -- $(/bin/uname -r)
if [ $1 -ge 2 ] ;then
    cat<<EOF
   Your blah blah
EOF
 if [ $2 -ge 6 ];then
    cat<<EOF
    blah blah
EOF
 else
    cat<<EOF
    failed blah blah
EOF    
 fi
else
 .....
 ....
 .....
fi



unset IFS

```

---

### Post by jingo811 on 2008-07-03
I removed this question it was too long and complicated for anyone to care about reading it.

---

### Post by dtmilano on 2008-07-03
If you do that (exit 0), in a file you source into another, folowing code will never be reached.

---

### Post by jingo811 on 2008-07-03
> **dtmilano said:**
> If you do that (exit 0), in a file you source into another, folowing code will never be reached.

Can I solve it by giving my function errors "exit codes 99" instead and make mother look like this instead?

**./Mother.sh**
[php]#!/bin/bash
. kernel_headers_check.sh
. funky.sh


if [ kernel_headers_check.sh "has exit 99 then STOP everything" ]

if [ funky.sh "has exit 99 then STOP everything" ]
[/php]

**kernel_headers_check.sh**
```
#!/bin/bash

kernel_headers_check () 
{ 
if
   blah blah blah; 
else
   exit 99
} 

exit 0
```



**funky.sh**
```
#!/bin/bash

funky ()
{ 
if
   blah blah blah; 
else
   exit 99
} 

exit 0
```

---

### Post by jingo811 on 2008-07-04
> **ghostdog74 said:**
> you can do something like this. No need too much awk. Also, no need too much echoes if you use here documents.
```

#!/bin/bash
IFS="."
set -- $(/bin/uname -r)
if [ $1 -ge 2 ] ;then
    cat<<EOF
   Your blah blah
EOF
 if [ $2 -ge 6 ];then
    cat<<EOF
    blah blah
EOF
 else
    cat<<EOF
    failed blah blah
EOF    
 fi
else
 .....
 ....
 .....
fi



unset IFS

```

I have implemented the heredoc but I'm not so sure about replacing my explanatory $KH_COMMAND_xxx variables with IFS and set -- $(/bin/uname -r).

```
IFS="."
set -- $(/bin/uname -r)
if [ $1 -ge 2 ] ;then
...
...
unset IFS
```

Because if I do it this way how can I manipulate $1?  Since when I do this...

[php]
$1=1 # or 1=1

IFS="."
#set -- $(/bin/uname -r)
if [ $1 -ge 2 ] ;then
...
...
unset IFS[/php]

...then I get these errors for the if check.
**./kernel_headers_check.sh: line 22: 1=1: command not found**
**./kernel_headers_check.sh: line 39: [: -ge: unary operator expected**

---

### Post by ghostdog74 on 2008-07-04
$1 is just the first field, $2 second field and so on after you set it. Save them into another  variable eg anothervariable=$1 for later processing if you want. Also, read up on how the if/else and test operators treats integers/strings and use the correct operator. The [manual]("http://tldp.org/LDP/abs/html/comparison-ops.html") is your friend. don't forget.

---

### Post by jingo811 on 2008-07-04
I'm not sure I follow what you mean when you say save the first field $1 into another variable for later processing. :confused:

# (1) B'coz when I change $1 formerly known as $KH_COMMAND_01 to $PRIMARY
# (2) Then I need to manually change all other $1 deeper into the code when I need to test certain values.  Have I understood you incorrect?

Before I started implementing IFS and set -- $ then I only had to manipulate these 2 variables in order to make everything in the script change values.
[PHP]#KH_COMMAND_01=`/bin/uname -r | awk -F '.' '{ print $1 }'`
	KH_COMMAND_01=1[/PHP]

[PHP]IFS="."
set -- $(/bin/uname -r)

PRIMARY=$1
PRIMARY=1

if [ $PRIMARY -ge 2 ]; then  # (1) B'coz when I change $1 to $PRIMARY
##################################
unset IFS

	cat<<EOF

		$KH_COMMAND_ORIGIN

		[  $1 ] Kernel version		    = OK # (2) Then I need to manually change all $1 deeper into the code when I need to test certain values.  Have I understood you incorrect?
EOF
	if [ $2 -ge 6 ]; then	#-------------------| 2.6.6 |---
	##################################
		cat<<EOF
		[  $2 ] Major revision of the kernel = OK
EOF
		if [ $KH_COMMAND_03_BETA -ge 6 ]; then
		#######################################
			cat<<EOF
		[ $KH_COMMAND_03_BETA ] Minor revision of the kernel = OK

[/PHP]

---

### Post by ghostdog74 on 2008-07-04
> 
```

...
PRIMARY=$1
PRIMARY=1
...

```

dude, why are you overwriting your variables?
let dissect this : /bin/uname -r | awk -F '.' '{ print $1 } 
-F"." is the same as IFS=".". print $1 in awk is the same as $1 after you set  it. so the above is equivalent to :

```

IFS="."
set -- $(/bin/uname -r)
KH_COMMAND_01=$1  # <--  that's what i mean by saving as another variable name for later processing.


```
It seems you don't understand how set works for positional parameters. Please, look [here for Example 14-18]("http://tldp.org/LDP/abs/html/internal.html#EX34"). Its all in the manual, as i have said.

---

### Post by jingo811 on 2008-07-04
> **ghostdog74 said:**
> 
dude, why are you overwriting your variables?

I guess it's b'coz I don't trust my coding skills enough.  So I like to be able to overwrite the input values in order to test and see that every ELSE en ELIF output goes well.  
To simulate somebody using kernel headers other than the usual **2.6.20-16-generic** which probably isn't necessary in the Ubuntu and Debian scene but I like to have complete control for what happens when things go wrong.

And after your last post where you showed me how the syntax should look like I think I got it right now.
No more ugly solutions like this anymore so I'm more than happy how it turned out in the end. 	:mrgreen:

```

KH_COMMAND_03_ALPHA=`/bin/uname -r | awk -F '.' '{ print $3 }'`
KH_COMMAND_03_BETA=`echo $KH_COMMAND_03_ALPHA | awk -F '-' '{ print $1 }'`
#	KH_COMMAND_03_BETA=26

```

[PHP]
IFS=".-"
set -- $(/bin/uname -r)

#...............................................................................

KH_COMMAND_ORIGIN=`/bin/uname -r`
KH_COMMAND_01=$1
#		KH_COMMAND_01=1
#KH_COMMAND_02=$2
		KH_COMMAND_02=4
KH_COMMAND_03=$3
#		KH_COMMAND_03=5

#...............................................................................

if [ $KH_COMMAND_01 -ge 2 ]; then
##################################
	cat<<EOF


			     $KH_COMMAND_ORIGIN


		[  $KH_COMMAND_01 ] Kernel version		    = OK
EOF
	if [ $KH_COMMAND_02 -ge 6 ]; then	#-------------------| 2.6.6 |---
	##################################
		cat<<EOF
		[  $KH_COMMAND_02 ] Major revision of the kernel = OK
EOF
		if [ $KH_COMMAND_03 -ge 6 ]; then
		#######################################
			cat<<EOF
		[ $KH_COMMAND_03 ] Minor revision of the kernel = OK

[/PHP]


> **ghostdog74 said:**
> 
It seems you don't understand how set works for positional parameters. Please, look [here for Example 14-18]("http://tldp.org/LDP/abs/html/internal.html#EX34"). Its all in the manual, as i have said.

Thanks for the link I tried to find something like that earlier today but searching for "set" in TLDP was no go.
And I couldn't come up with the right search word combinations in google to find what I wanted about the SET.  I just got a bunch of irrelevant websites that contained the word SET but no the command.

Then I lost hope and stopped searching and crossed my fingers hoping for the best.  So thanks for the precise links you're giving me, much appreciated!

---

### Post by ghostdog74 on 2008-07-04
the document is called advanced bash scripting guide. In google, just type something like: advanced bash set.
THat's how i found the link for you. i am sure now you can do it by yourself and good to hear you understood how it works.

---

### Post by jingo811 on 2008-07-08
Now this function is finally finished.  Tell me if it works OK on other Ubuntu versions other than Feisty 7.04.  I've used quite a lot of Bash-ism so it's no longer any Shell friendly I would think.

---

