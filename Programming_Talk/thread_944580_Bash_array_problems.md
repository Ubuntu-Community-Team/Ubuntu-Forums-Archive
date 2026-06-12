---
title: "Bash: array problems"
date: 2008-10-11
forum: Programming Talk
---

### Post by dexter on 2008-10-11
Hi,

I'm trying to write a little script that automates ripping dvd titles to the harddrive using mplayer. I'm however facing an issue with array i cannot resolve. This is my current script:

```

#!/bin/sh

# required:
# - lsdvd
# - mplayer

DVD_DEVICE="/dev/dvd"
SHOW_HELP="false"
PERFORM_RIPPING="true"
LIST_DVD_CONTENT="true"

# check possible parameters
# -l: only list the dvd titles
# -d: specify dvd-device (e.g. /dev/dvd1, default is /dev/dvd)
# -h: display help info

# The getopts command uses a couple of predetermined variables. 
# The OPTIND variable is initially set to 1. Thereafter it contains the index of the next parameter to be processed. 
# The getopts command returns true  if an option is found, so a common option processing paradigm uses a while loop 
# with a case  statement as in this example. The first argument to getopts is a list of option letters to be recognized, 
# in this case, p and r. A colon (:) after an option letter indicates that the option requires a value; for example, a -f
# option might be used to indicate a file name, as in the tar command. The leading colon in this example tells getopts to be
# silent and suppress the normal error messages, as this script will provide its own error handling. 
# source: [http://www.ibm.com/developerworks/library/l-bash-parameters.html?ca=drs-](http://www.ibm.com/developerworks/library/l-bash-parameters.html?ca=drs-)

while getopts ":d:hl" optname
do    
  case "$optname" in
    "d")        
      DVD_DEVICE=$OPTARG
      ;;    
    "h")
      SHOW_HELP="true"
      PERFORM_RIPPING="false"
      LIST_DVD_CONTENT="false"
      ;;        
    "l")
      PERFORM_RIPPING="false"
      ;;      
    "?")
      echo "Unkown option $OPTARG"
      SHOW_HELP="true"
      PERFORM_RIPPTING="false"
      LIST_DVD_CONTENT="false"
      ;;
  esac
done

if [ "$SHOW_HELP" = "true" ] 
then
  echo "This script can be used to display the content of a dvd and rip the titles to your hard drive."
  echo "It requires mplayer and lsdvd."
  echo "Options"
  echo " -d: specify the dvd-device to be used (default is /dev/dvd)."
  echo " -h: show help."  
  echo " -l: only list the dvd titles."
fi

if [ "$LIST_DVD_CONTENT" = "true" ] 
then
  echo "Using dvd-device $DVD_DEVICE"
  lsdvd $DVD_DEVICE
fi

if [ "$PERFORM_RIPPING" = "true" ]
then
  NUMBER_OF_FILES=0
  ARRAY_TITLENUMBERS={}
  ARRAY_TITLENAMES={}
  
  echo "Enter track title and filenames (0 to exit)"
  echo "Title"
  read TITLENUMBER
  while [ $TITLENUMBER -ne 0 ]
  do  
      echo "Save as:"
      read TITLENAME

      ARRAY_TITLENUMBERS[$NUMBER_OF_FILES]=$TITLENUMBER
      ARRAY_TITLENAMES[$NUMBER_OF_FILES]=$TITLENAME

      NUMBER_OF_FILES=$NUMBER_OF_FILES+1
      
      echo "Title"
      read TITLENUMBER
  done
  
#  ITR_TITLE=0
#  while [ $ITR_TITLE -lt $NUMBER_OF_FILES ]
#  do
#    echo "${ARRAY_TITLENUMBERS[$ITR_TITLE]}: ${ARRAY_TITLENAMES[$ITR_TITLE]}"
#  done
    
  
fi

```

The problem is situated in lines 79 and 80, bash doesn't seem to be able to store my variables i read from the console in the arrays. The values in the arrays will be used later in the script to pass as parameters to mplayer.

When running (Title=1, Saved as test) i get the following errors:
```

./rip-vob: 95: ARRAY_TITLENUMBERS[0]=1: not found
./rip-vob: 95: ARRAY_TITLENAMES[0]=test: not found

```

I've checked many tutorials on the internet but nothing seems to work. I also get the same errors when trying something simple like
```

ARRAY_TEST[1]="20"

```

My bash version is
```
GNU bash, version 3.2.39(1)-release (x86_64-pc-linux-gnu)
```

---

### Post by geirha on 2008-10-11
```
NUMBER_OF_FILES=$NUMBER_OF_FILES+1
```
bash does not do arithmetics this way, you need to use (()) or $(()).
```
NUMBER_OF_FILES=$((NUMBER_OF_FILES+1))
# or
(( NUMBER_OF_FILES++ ))
# you can also use let
let "NUMBER_OF_FILES++"

```

Also
```
ARRAY_TITLENUMBERS={}
```
you don't need to declare arrays, but the above will just create a variable with the string {}. The bash way of declaring an array is: ```
declare -a ARRAY_TITLENUMBERS
``` Though as just stated, it's not necessary to declare an array, and doing ARRAY_TITLENUMBERS={} will not make it fail in any way.

Lastly, since you set variables to "true" and "false", you can make the if-statements shorter by running the values of the variables as commands. true and false are builtin bash commands that will always return true and false respectively. E.g.
```

some_var="true"

if $some_var; then
   echo do something
fi

```

Of course your way of doing it is perfectly fine, it's just a matter of preference. I find it slightly more readable.

Apart from that minor syntax error, your code is structured, easy to read and well indented :)

---

### Post by dexter on 2008-10-11
I've found the solution to my array problem, I started from a script i found on the web, seems like that one used /bin/sh which links to dash on my system...

geirha, thanks for the tip on bash arithmetics and the compliments :). I'm actually an embedded software programmer (C/C++), so i know how important a good code layout is if you have to read it again afterwards.

---

### Post by geirha on 2008-10-11
Ah, indeed, I failed to notice that the shebang was wrong. It's one of the most common mistakes in bash scripting. I think mostly because certain popular distros in the olden days used to link /bin/sh to /bin/bash.

Glad you got it sorted :)

---

### Post by deepaksrm on 2009-11-21
Im exactly facing the same problem with my script!

Here is my script.
The script is about finding a process and starting back the process if it had stopped.

> #!/bin/bash
process[1]="thin"
path[1]="/home/deepak/CampusYap/"
initiate[1]="thin start -d"

process_id=`ps -ef | pgrep $process[1] | wc -m`
if [ "$process_id" -gt "0" ]; then
  echo "Hurray the process ${process[1]} is running!!"
else
  cd ${path[1]}
  ${initiate[1]}
  echo "Oops the process has stopped"
fi> 
DontWorry.sh: 2: process[1]=thin: not found
DontWorry.sh: 3: path[1]=/home/deepak/CampusYap/: not found
DontWorry.sh: 4: initiate[1]=thin start -d: not foundI tried using #!/bin/bash and #!/bin/sh none of them worked.
What am i missing?

---

### Post by geirha on 2009-11-23
Let me guess, you are runing the script with
```
sh DontWorry.sh
```
That'll run it with sh, not bash. Make it executable and run it directly
```
chmod +x DontWorry.sh
./DontWorry.sh
```
When running it like that, it will use the shebang.

On the code itself, why are you using arrays? You only have one element in each array, so you might as well use strings. Also, to see if the process is running, check the return value of pgrep directly. Don't go through the hassle of counting the number of bytes of output.

```
if pgrep "$process" >/dev/null; then
    echo running
else
    echo not running
fi

```

---

