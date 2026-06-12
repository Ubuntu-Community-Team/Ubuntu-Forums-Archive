---
title: "bash script"
date: 2005-05-22
forum: Programming Talk
---

### Post by testingubuntu on 2005-05-22
I have a bash script i use to create thumbnails and stuff 
I am trying to protect against incorrect directories but it seems that it wont test the dir the way i want it to  

here is the script 
I'm using the 4th command or the "Test"   

```
#!/bin/bash

#*******************************************#
#             Convert.sh                                   #
#       Written By: James Lawrence                #
#               May 20 2005                              #
#                                                                 #
#     create thumbnails of images               #
#*******************************************# 

############
# Varibles #
############
user=`whoami`  
locate="/" # the location the user types in for a directory
images="/home/$user"  #default directory to start in
#############
# Functions #
#############

# Now ask the user where the JPG images are 
function CONVERTJPG
{
read -p "Type the path to the jpegs [$images]:" locate
cd $locate
  for img in  $(ls *.[jJ][pP][gG])  
do
  convert -sample 25%x25% $img thumb-$img # Create the thumbnails
done

}


# Now ask the user where the PNG images are
function CONVERTPNG
{
read -p "Type the path to the png images [$images]:" locate
cd $locate
for img in  $(ls *.[pP][nN][gG])
do
  convert -sample 25%x25% $img thumb-$img # Create the thumbnails
done

}

################################################################
[COLOR=Red]function TEST   # for testing new functions 

{
read -p "Type the path to the jpegs [$images]:" locate

if cd "$locate" 2>/dev/null; then
  echo "Now in $locate"

else
  echo "Wrong Directory Dude! can't change to $locate"
fi

for img in  $(ls *.[jJ][pP][gG])  
do
  convert -sample 25%x25% $img thumb-$img # Create the thumbnails
done

}[/COLOR]


######################
# a little interface #
######################
selection=
until [ "$selection" = "0" ]; do
    echo ""
    echo "Options..."
    echo " 1 - Seek n Convert Jpg's"
    echo " 2 - Seek n Convert Png's"
    echo " 3 - Location"
    echo " 4 - TEST"
    echo " 0 - Close"
    echo ""
    echo -n "Enter a Number: "
    read selection
    echo ""

###################
# Cases selection #
###################
    case $selection in
        1 ) $(CONVERTJPG) ;;
        2 ) $(CONVERTPNG) ;;
        3 ) pwd ;;
        4 ) $(TEST) ;;
        0 ) exit ;;
        * ) echo "Please enter 1, 2, 3 or 0"
    esac
done
 
```

---

### Post by tread on 2005-05-22
I am not on a linux box to try the script out .. but try renaming the "locate" variable? There is a program called locate .. maybe that would interfere?

---

### Post by testingubuntu on 2005-05-22
didn't help changing the varible

---

### Post by testingubuntu on 2005-05-22
here is what i gather,  I think the if then is working but the echo blah blah either way is what it failing if you notice 
> Enter a Number: 4

Type the path to the jpegs [/home/jim]:/home/jim.Graduation
convert.sh: line 94: [COLOR=Red]Wrong[/COLOR]: command not found 

Options...
 1 - Seek n Convert Jpg's
 2 - Seek n Convert Png's
 3 - Location
 4 - TEST
 0 - Close

Enter a Number: 
highlighted in red is the first work quoted after the echo statement 
Why is echo having a heart attack about double quotes? 
if i change the echo blah  to 'blah blah ' still same deal 
if i have the echo"blah blah " it prints the contents of the statement but tosses a error. like this ...
> Enter a Number: 4

Type the path to the jpegs [/home/jim]:/home/jim.Graduation
convert.sh: line 61: echoWrong Directory Dude! cant change to : command not found

Options...
 1 - Seek n Convert Jpg's
 2 - Seek n Convert Png's
 3 - Location
 4 - TEST
 0 - Close

Enter a Number: 

So what the hell can I do to just have it print 
the corect echo statements ?

---

### Post by mendicant on 2005-05-22
To call a function, you don't wrap it in $(...), you just call the name.
So you need:
```

    case $selection in
        1 ) CONVERTJPG ;;
        2 ) CONVERTPNG ;;
        3 ) pwd ;;
        4 ) TEST ;;
        0 ) exit ;;
        * ) echo "Please enter 1, 2, 3 or 0"
    esac

```

---

### Post by LordHunter317 on 2005-05-22
Your script is broken for the reason mendicant identified. You don't call functions you define with backticks or $(). That's used for output substitution, where the output of the command is replaced where the backticks or $() occured.

Your script has a thousand other major issues as well:




[list]
[*]UNIX users generally hates menus. Interactiveness for a task this simple is bad. All it lets me do is select JPG or PNG, essentially. It also breaks my ability to use the command in more powerful ways, like providing a whole list of directories.
[*]It does some dangerous things, which I'll outline below.
[*]It changes the PWD of the user and doesn't change it back, which is probably the worse sin you can do.
[/list]I'm going to provide a replacement script that's more in the style of a traditional UNIX script, as a courtesy.

[QUOTE=testingubuntu]
```
user=`whoami`  
locate="/" # the location the user types in for a directory
images="/home/$user"  #default directory to start in
```[/quote]You could have just said:```
images="/home/`whoami`"
```

> ```
function CONVERTJPG
{
read -p "Type the path to the jpegs [$images]:" locate
cd $locate
```This ought to be "$locate" in this context. 

> ```
for img in $(ls *.[jJ][pP][gG]) 
```This is the really bad sin. I'm going to say this once, and it's important:
**Never, ever,** use backticks (``) or $() on unbounded expressions.  
That menas if you don't know the output of the command in advance, you can't use them. This is because if the output is too large, you'll crash the shell or possibly have other bad behavior. 

Not safe.  In this case, for supports filename matching, so you just say:```
for img in $.[jJ][pP][gG]
```

> ```
convert -sample 25%x25% $img thumb-$img # Create the thumbnails
```Both variables need "" around them to protect against "Filesnames With Spaces In Them". In fact, anything that's a filename almost always needs "", unless it's a constant one you know doesn't.

CONVERTPNG has the same badness going on.  As does TEST.

Anyway, the way I'd write a script to convert whole directories of PNGs or JPGs and be semi-intelligent about it is:```
#!/bin/bash

function usage {
	echo "Usage: $0 [-v] jpg|png|both dirnames..."
	echo "Creates thumbnails of all jpgs, pngs or both filetypes in the supplied dirnames."
}

VERBOSE=0

set -- `getopt -n "$0" -o v -- "$@"`
if [ "$?" -ne 0 ] ; then
	usage
	exit 1
fi

for arg in "$@" ; do
	shift
	if [ "$arg" == "--" ] ; then
		break
	fi

	case "$arg" in
	"-v")
		VERBOSE=1
		;;
	*)	# Unreachable
		usage
		exit 1
		;;
	esac
done

FORMAT=""
case "$1" in
jpg)
	FORMAT="[jJ][pP][gG]"
	;;
png)
	FORMAT="[pP][nN][gG]"
	;;
both)
	FORMAT="[jJpP][pPnN][gG]"	# Not perfect, but works, especially for an example.
	;;

*)
	usage
	exit 1
	;;
esac
shift

# Process directories now
for i in "$@" ; do
	for file in "$i/*.${FORMAT}" ; do		
		 convert -sample 25%x25% "$file" "thumb-$file"
	done

	if [ "$VERBOSE" -eq "1" ] ; then
		echo "$0: Done processing $i"
	fi
done
```This is untested, but ought to work.

---

