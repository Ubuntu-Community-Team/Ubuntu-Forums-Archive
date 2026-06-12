---
title: "[SOLVED] Syntax error with ELIF at line 48."
date: 2008-07-02
forum: Programming Talk
---

### Post by jingo811 on 2008-07-02
Can somebody explain to me why I can't use ELIF the way I have done?
How can I correct this?

```
linux@linux:~/bash$ **./kernel_header_check.sh **
./kernel_header_check.sh: line 48: syntax error near unexpected token `elif'
./kernel_header_check.sh: line 48: `    [COLOR="Red"]elif [ $KH_COMMAND_02 -eq 4 ]; then'[/COLOR]
linux@linux:~/bash$ 
```



[PHP]
##################################################################################
#
#	maintainer: Witch
#
#				Pseudo code explanations
#
#	Test if your kernel headers is at least these versions 2.6.6 or 2.4.26
#
##################################################################################

KH_COMMAND_01=`/bin/uname -r | awk -F '.' '{ print $1 }'`
KH_COMMAND_02=`/bin/uname -r | awk -F '.' '{ print $2 }'`

KH_COMMAND_03_ALPHA=`/bin/uname -r | awk -F '.' '{ print $3 }'`
KH_COMMAND_03_BETA=`echo $KH_COMMAND_03_ALPHA | awk -F '-' '{ print $1 }'`

##################################################################################


#	Test if first number in "uname-r" is equal to or greater than 2.

if [ $KH_COMMAND_01 -ge 2 ]; then
	echo
	echo "Primary OK."
#--------------------------------------------------------------------------2.6.6

		if [ $KH_COMMAND_02 -ge 6 ]; then

			if [ $KH_COMMAND_03_BETA -ge 6 ]; then
#		When it fails quit!	ERROR layer 2 and 3
#--------------------------------------------------------------------------2.4.26

		ELIF [ $KH_COMMAND_02 -eq 4 ]; then
			
			if [ $KH_COMMAND_03_BETA -ge 26 ]; then
#		When it fails quit!	ERROR layer 2 and 3
#---------------------------------------------------------------------------------
		else
#			ERROR layer 2 and #
		fi
#---------------------------------------------------------------------------------
		
else
#	When it fails quit!		ERROR layer 1
fi
[/PHP]


[PHP]
#!/bin/bash

# Test if your kernel headers is at least these versions 2.6.6 or 2.4.26
#
#	maintainer: Witch

# Howto run the script.
#
#	./kernel_header_check.sh
#
##################################################################################

# KH_COMMAND_ORIGIN=`/bin/uname -r`
# KH_COMMAND_NUMERICAL=`/bin/uname -r | awk -F '-' '{print $1}'`

KH_COMMAND_01=`/bin/uname -r | awk -F '.' '{ print $1 }'`
KH_COMMAND_02=`/bin/uname -r | awk -F '.' '{ print $2 }'`

KH_COMMAND_03_ALPHA=`/bin/uname -r | awk -F '.' '{ print $3 }'`
KH_COMMAND_03_BETA=`echo $KH_COMMAND_03_ALPHA | awk -F '-' '{ print $1 }'`

##################################################################################


if [ $KH_COMMAND_01 -ge 2 ]; then
	echo
	echo "Primary OK."

#--------------------------------------------------------------------------2.6.6
	if [ $KH_COMMAND_02 -ge 6 ]; then
		echo
		echo "Secondary New OK."

		if [ $KH_COMMAND_03_BETA -ge 6 ]; then
			echo
			echo "Tertiary OK."
			echo
			echo "(2) Your current kernel headers will work with NDISwrapper!"
			echo
		else
			echo
			echo "Tertiary (3) Failed!"
			echo
			echo "(3) You need at least kernel header versions 2.6.6 or 2.4.26 in order to use NDISwrapper."
			echo

#--------------------------------------------------------------------------2.4.26
	elif [ $KH_COMMAND_02 -eq 4 ]; then
		echo
		echo "Secondary Old OK."

		if [ $KH_COMMAND_03_BETA -ge 26 ]; then
			echo
			echo "Tertiary OK."
			echo
			echo "(2) Your current kernel headers will work with NDISwrapper!"
			echo
		else
			echo
			echo "Tertiary (3) Failed!"
			echo
			echo "(3) You need at least kernel header versions 2.6.6 or 2.4.26 in order to use NDISwrapper."
			echo

#---------------------------------------------------------------------------------
	else
		echo
		echo "Secondary (2) Failed!"
		echo
		echo "(2) You need at least kernel header versions 2.6.6 or 2.4.26 in order to use NDISwrapper."
		echo
	fi
#---------------------------------------------------------------------------------
	
else
	echo
	echo "(1) Failed!  You need at least kernel header versions 2.6.6 or 2.4.26 in order to use NDISwrapper."
	echo
fi

	
[/PHP]

---

### Post by jingo811 on 2008-07-02
Hehe I forgot to close 2 if statements :mrgreen: You didn't need to do that in php if I remember correctly.  Now I can start testing this script!
Tnx for the help :KS me!

Oh even though I solved this could some people test this script and see if it works on your PCs.
It checks if you have at least kernel header version 2.6.6 or 2.4.26.

---

