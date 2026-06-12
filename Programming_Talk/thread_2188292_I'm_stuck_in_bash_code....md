---
title: "I'm stuck in bash code..."
date: 2013-11-16
forum: Programming Talk
---

### Post by alex_deco20 on 2013-11-16
Hi guys,
  Does anyone know's why my code doesn't run ? I want to replace the strtolower function from bash.
 
 ```


[COLOR=#880000]#!/bin/sh[/COLOR]
  sed [COLOR=#008800]"y/[FONT=Verdana]strtolower[/FONT]/lower/"[/COLOR] [COLOR=#666600]<[/COLOR]run[COLOR=#666600].[/COLOR]php [COLOR=#666600]>[/COLOR][FONT=Verdana]run[/FONT][COLOR=#666600][FONT=Verdana].[/FONT][/COLOR][FONT=Verdana]php[/FONT][COLOR=#666600][FONT=Verdana].[/FONT][/COLOR][COLOR=#000088][FONT=Verdana]new
[/FONT][/COLOR]
[COLOR=#000088]if[/COLOR] [COLOR=#666600][[/COLOR] [COLOR=#666600]-[/COLOR]f [COLOR=#006666]run.php[/COLOR] [COLOR=#666600]];[/COLOR] [COLOR=#000088]then[/COLOR]
  rm [FONT=Verdana]run[/FONT][COLOR=#666600][FONT=Verdana].[/FONT][/COLOR][FONT=Verdana]php [/FONT][COLOR=#666600][FONT=Verdana]&&[/FONT][/COLOR][FONT=Verdana] mv [/FONT][FONT=Verdana]run[/FONT][COLOR=#666600][FONT=Verdana].[/FONT][/COLOR][FONT=Verdana]php[/FONT][COLOR=#666600][FONT=Verdana].[/FONT][/COLOR][COLOR=#000088][FONT=Verdana]new[/FONT][/COLOR][FONT=Verdana]run[/FONT][COLOR=#666600][FONT=Verdana].[/FONT][/COLOR][FONT=Verdana]php
[/FONT]
fi

```

---

### Post by SeijiSensei on 2013-11-16
The "y" command to sed does "transliteration" according to the sed manual page ("man sed").  If you want to replace all instances of strtolower with lower, then use "s" like this:

```
s/strtolower/lower/g
```

Here's a little script I once wrote to replace all instances of string1 with string2 in all files matching filespec.  I used it just yesterday to change all instances of POST to GET in a bunch of PHP files. You might find it helpful:

```

#!/bin/bash

if [ "$1" = "" ]
then
    echo "Syntax: replaceall 'string1' 'string2' 'filespec'"
    echo "Include the single quotes in your command"
    exit
fi

WD=$(pwd)
NOW=`date +%s`
TMP=~/.replaceall
FILES=$(ls $3)
mkdir -p $TMP/$NOW

for i in $FILES;
do
   TEST=$(grep "$1" $i)
   #echo "Checking $i; TEST=$TEST"  #uncomment for debugging
   if [ "$TEST" != "" ] 
   then
      echo "Replacing '$1' with '$2' in $i"
      # save backup copies
      cp $i $TMP/$NOW/$i.bak
      # do the replacement
      (sed "s_$1_$2_g" $i > $i.new) && (rm -f $i; mv $i.new $i)
   fi
done

cd $WD
echo ""

exit 0

```

The "ls $3" command to get the filelist may not work correctly if you have files with embedded spaces.  I never create such files so I don't encounter the problem. Also if the strings have underscore characters in them, you'll need to use a different delimiter in sed.  The forward slash is the usual choice, as I used in the initial response above; the percent sign is often a good alternative.

You'll find the backup copies in ~/.replaceall/[some number]; the largest number is the most recent save.

---

