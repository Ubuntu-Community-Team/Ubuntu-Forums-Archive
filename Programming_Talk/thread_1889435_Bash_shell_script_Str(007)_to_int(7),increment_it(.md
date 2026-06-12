---
title: "Bash shell script: Str(007) to int(7),increment it(8) &amp; convert back to string(008)"
date: 2011-12-01
forum: Programming Talk
---

### Post by drwatson_droid on 2011-12-01
Bash shell script: Str(007) to int(7),increment it(8) & convert back to string(008)


Hi,
 I have the following requirement.

There will be  following text/line in a file (eg: search-build.txt)
PRODUCT_VERSION="V:01.002.007.Build1234"

I need to update the incremental build number (eg here  007) every time I give a build through script. I am able to search the string and get the item. 
> rexpression_sed='PRODUCT_VERSION=\"V:\([0-9]*\).\([0-9]*\).\([0-9]*\).Build\([0-9]*\)\"'
var2=`grep -sn $rexpression_sed search-build.txt | sed -e 's/'$rexpression_sed'/\1\t\2\t\3\t\4/g'| cut -f 3`
echo $var2Output 
007

How to convert this to integer (7), add 1 to it (8) and again get back in the same form (008 in the easiest way? I will be using sed -i on the file, with this new string that can be used with RE for replacing that part!
Or
Is there any better method than above.

Thanks for any help.

---

### Post by drwatson_droid on 2011-12-01
Re: Bash shell script: Str(007) to int(7),increment it(8) & convert back to string(00
thanks solved
> 
newval=0
filename=search-build.txt
rexpression_sed='PRODUCT_VERSION=\"V:\([0-9]*\).\([0-9]*\).\([0-9]*\).Build\([0-9]*\)\"'

incrementnum=`grep -sn $rexpression_sed $filename | sed -e 's/'$rexpression_sed'/\1\t\2\t\3\t\4/g'| cut -f 3`
echo "Current Incremental number is: " $incrementnum
if [ $incrementnum ]
then
    calcval=$(expr $incrementnum + 1)
    #echo $calcval
    if [ $calcval -le 9 ];
    then
        newval="00$calcval"
    elif [ $calcval -le 99 ];
    then
        newval="0$calcval"
    else
        newval="$calcval"
    fi
    echo "New Incremental number is: " $newval
    rexpression_rep_final='PRODUCT_VERSION="V:\1.\2.'$newval'.Build\4"'
    #replace with new number
    sed -i 's/'$rexpression_sed'/'$rexpression_rep_final'/' $filename
fi


---

### Post by Vaphell on 2011-12-01
you could extract that value with sed, just replace everything with \3 only. No need to pass everything to cut to get that \3.

Also
```
$ x='007'
$ echo PROD_VER=V:111.222.**$( printf "%03d" $(( 10#$x+1 ))** ).build666
PROD_VER=V:111.222.**008**.build666

```

**$(( ... ))** does integer arithmetic
**10#$x** forces treating x as base-10 (leading zeros indicate base-8)
**printf %03d $i** prints $i as a zero-padded 3-digit number (printf formatting works just like in C function of the same name)

---

