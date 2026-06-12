---
title: "script to list directories and sizes in shell using du"
date: 2008-10-09
forum: Programming Talk
---

### Post by pcozzy on 2008-10-09
I thought to share this, basically the lazy terminal typer I am, made this script to list the directory u are in and only directories with there sizes in color.

I named it space.sh and placed it in my /usr/local/bin dir. U need to chmod +x space.sh and then run it using ./space.sh or if you placed in your PATH then just type space.sh it will run.  It will not run correctly using sh, I am not that smart to know why.  test it modify it to your liking.

```

#!/bin/bash
#Creator: pcozzy
#Date: October 9, 2008
#purpose: Print out the subdirsizes using du and colorize them.
#			I made this script on ubuntu 8.04 hardy
#			Colors may be different on some systems
#			I excluded regular files in this listing use ls command.
#			I choose not to follow symbolic links too! du -P
#


####################################################################
##Color 	Foreground	Background
#black			30			40
#red			31 			41
#green			32 			42
#yellow			33 			43
#blue			34 			44
#magenta		35 			45
#cyan			36 			46
#white			37 			47
####################################################################
#
#	I choose these colors because for me Red sticks out and 
#	usually the megabyte size Directory, I like to watch
#	as for gigabyte size Green catches my attention.
#	To change colors is as easy as changing the number
#	in the echo statement.
####################################################################

for i in *
do
	subdir_1="$i"
	s1=`du -Psh "$subdir_1"`
	sub_cut1=`echo "$s1" | sed 's/\(^[0-9].*\)[\t]\([a-z,A-Z].*\)/\1/g'`
	sub_cut2=`echo "$s1" | sed 's/\(^[0-9].*\)[\t]\([a-z,A-Z].*\)/\2/g'`
	sub_cut3=`echo "$sub_cut1" | sed 's/\(^[0-9].*\)\([a-z,A-Z].*\)/\2/g'`
	sub_cut4=`echo "$sub_cut1" | sed 's/\(^[0-9].*\)\([a-z,A-Z].*\)/\1/g'`
	Value_1=`test -d "$subdir_1" ;echo $?`

	if [ "$sub_cut3" = "K" ]; then
		if [ "$sub_cut4" = "4.0" ]; then
			sub_cut3_1="Kilobyte ~"
			color1='\E[35;40m'			
		else
			sub_cut3_1="Kilobyte"
			color1='\E[35;40m'
		fi
	elif [ "$sub_cut3" = "M" ];then
		sub_cut3_1="Megabyte"
		color1='\E[31;40m'
	elif [ "$sub_cut3" = "G" ];then
		sub_cut3_1="Gigabyte"
		color1='\E[32;40m'
	else
		sub_cut3_1="Not Worth Measuring"
	fi
	if [ "$Value_1" -eq "0" ] && [ "$sub_cut1" != "0" ]; then
		echo -en "\033[1m$sub_cut2 \033[0m"; tput sgr0
		echo -en $color1"\033[4m$sub_cut4 \033[0m"; tput sgr0
		echo -e $color1"\033[4m$sub_cut3_1\033[0m"; tput sgr0
	fi
done
echo -e '\E[35;40m'"~ May be an empty Directory or one with Symbolic links"; tput sgr0
echo
#end


```

enjoy, I sure there may be better solutions.  They should make a bash scripting section here because there are tons out there.

---

