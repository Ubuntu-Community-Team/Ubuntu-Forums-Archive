---
title: "If statement in Bash"
date: 2008-10-08
forum: Programming Talk
---

### Post by borgvall on 2008-10-08
I'm trying to make a script which should set the correct color profile for the screen that is being used. It's not working even after several hours of trial and error. So please help me out with this code.

```

#!/bin/bash
grafik=xrandr | head -1
screen0="Screen 0: minimum 320 x 240, current 1920 x 1200, maximum #1920 x 1200"
screen1="Screen 1: minimum 320 x 240, current 1280 x 800, maximum 1280 x 800"
if [ "$grafik" = "$screen0" ];
then
xcalib /usr/share/color/icc/Monitor_2008-03-27_2_Benq_brightness30.icc
else [ "$grafik" = "$screen1" ];
xcalib /usr/share/color/icc/Monitor_2008-03-27_3_m1330_luminance195.icc
fi

```

---

### Post by geirha on 2008-10-08
You want the first line of xrandr to be stored in grafik, you need to use the backticks for that:
```
grafik=`xrandr | head -1`
# alternatively you can use $() the same way
grafik=$(xrandr | head -1)
```

EDIT: Also, you probably only need to check if the first part is "Screen 0" or "Screen 1":
```

grafik=`xrandr | head -1`

case "$grafik" in
  "Screen 0"*)
     echo "Screen 0 stuff"
  ;;
  "Screen 1"*)
     echo "Screen 1 stuff"
  ;;
  *)
     echo no match
  ;;
esac

```

---

### Post by SeanHodges on 2008-10-08
$grafik is getting set incorrectly.

Use back-ticks to pass the output of your command into $grafik:

grafik=`xrandr | head -1`


Edit: geirha beat me to it :)

---

### Post by borgvall on 2008-10-08
Ah, I read some tutorials on this but thought that the backsticks just were ' but in another character type.

---

### Post by geirha on 2008-10-08
I was too slow on editing my previous post, have a look at the example I added there. Your else is also wrong, instead of else [ "$grafik" = "$screen1" ]; you want to use ```
elif [ "$grafik" = "$screen1" ]; then
``` with elif being short for else if.

---

### Post by borgvall on 2008-10-10
I noticed that what counts as screen 0 varies, therefore "minimum 320 x 240, current 1920 x 1200, maximum #1920 x 1200" and "minimum 320 x 240, current 1280 x 800, maximum 1280 x 800" are the things which shows if the external or the internal screen should be used. This force me to make the script look for those lines and not only compare the exact line which "xrandr | head -1" outputs. So I guess I need help with another operator.

---

### Post by dwhitney67 on 2008-10-10
When implementing an if-statement, is not the semi-colon optional?  Well, not if the "then" statement is on the same line.  But if the "then" is on a separate line, the semi-colon should not be present.  At least I think so; I could be wrong.

Semi-colon needed:
```

if [ some-condition ]; then
...
fi

```

Semi-colon not needed:
```

if [ some-condition ]
then
...
fi

```

---

### Post by borgvall on 2008-10-13
Ok, but that isn't the problem Please see my previous post, I hope it's possible to understand it.

---

### Post by SeanHodges on 2008-10-13
> **borgvall said:**
> I noticed that what counts as screen 0 varies, therefore "minimum 320 x 240, current 1920 x 1200, maximum #1920 x 1200" and "minimum 320 x 240, current 1280 x 800, maximum 1280 x 800" are the things which shows if the external or the internal screen should be used. This force me to make the script look for those lines and not only compare the exact line which "xrandr | head -1" outputs. So I guess I need help with another operator.

Perhaps this?

```
screen0="Screen 0"
screen1="Screen 1"
if [[ "$grafik" =~ "$screen0" ]]
then
...
elif [[ "$grafik" =~ "$screen1" ]]
then
...
fi
```

Also, check out geirha's "switch case" post earlier.

---

### Post by akvino on 2008-10-13
does [[ "$a" =~ "$b" ]] check for bitwise equality?

---

### Post by mssever on 2008-10-13
> **akvino said:**
> does [[ "$a" =~ "$b" ]] check for bitwise equality?
No, =~ expects a regular expression on the right hand side and tests the left hand side for a match.

---

### Post by geirha on 2008-10-13
> **akvino said:**
> does [[ "$a" =~ "$b" ]] check for bitwise equality?

It matches regular expressions. Sort of like doing **echo "$a" | egrep "$b"**.

---

### Post by borgvall on 2008-10-15
> **SeanHodges said:**
> Perhaps this?

```
screen0="Screen 0"
screen1="Screen 1"
if [[ "$grafik" =~ "$screen0" ]]
then
...
elif [[ "$grafik" =~ "$screen1" ]]
then
...
fi
```

Also, check out geirha's "switch case" post earlier.

That was a good idea but this doesn't work from what I think because Screen 0 and Screen 1 changes when I unplug the external monitor. So again, what has to be compared is what's written after "Screen X:"

This is what I tried last time:
```

grafik=`xrandr | head -1`
screen0="minimum 320 x 240, current 1920 x 1200, maximum #1920 x 1200"
screen1="minimum 320 x 240, current 1280 x 800, maximum 1280 x 800"
if [[ "$grafik" =~ "$screen0" ]]
then
/home/victor/dokument/diverse/script/Benq.icc.sh
elif [[ "$grafik" =~ "$screen1" ]]
then
/home/victor/dokument/diverse/script/XPS.bright.icc.sh
fi

```

---

### Post by borgvall on 2008-10-16
> **borgvall said:**
> That was a good idea but this doesn't work from what I think because Screen 0 and Screen 1 changes when I unplug the external monitor. So again, what has to be compared is what's written after "Screen X:"

This is what I tried last time:
```

grafik=`xrandr | head -1`
screen0="minimum 320 x 240, current 1920 x 1200, maximum #1920 x 1200"
screen1="minimum 320 x 240, current 1280 x 800, maximum 1280 x 800"
if [[ "$grafik" =~ "$screen0" ]]
then
/home/victor/dokument/diverse/script/Benq.icc.sh
elif [[ "$grafik" =~ "$screen1" ]]
then
/home/victor/dokument/diverse/script/XPS.bright.icc.sh
fi

```

By the way that Benq.icc.sh and XPS.bright.icc.sh run xcalib and the icc file.

---

### Post by geirha on 2008-10-16
> **borgvall said:**
> That was a good idea but this doesn't work from what I think because Screen 0 and Screen 1 changes when I unplug the external monitor. So again, what has to be compared is what's written after "Screen X:"

This is what I tried last time:
```

grafik=`xrandr | head -1`
screen0="minimum 320 x 240, current 1920 x 1200, maximum #1920 x 1200"
screen1="minimum 320 x 240, current 1280 x 800, maximum 1280 x 800"
if [[ "$grafik" =~ "$screen0" ]]
then
/home/victor/dokument/diverse/script/Benq.icc.sh
elif [[ "$grafik" =~ "$screen1" ]]
then
/home/victor/dokument/diverse/script/XPS.bright.icc.sh
fi

```
It sounds like you just need to check the maximum value. If so, I'd use a case like this
```

case "`xrandr | head -1`" in
    *"1920 x 1200") /home/victor/dokument/diverse/script/Benq.icc.sh ;;
    *"1280 x 800") /home/victor/dokument/diverse/script/XPS.bright.icc.sh ;;
    *) 
        echo "no matching screen" >&2
        exit 1 
    ;;
esac  

```

---

### Post by borgvall on 2008-10-17
> **geirha said:**
> It sounds like you just need to check the maximum value. If so, I'd use a case like this
```

case "`xrandr | head -1`" in
    *"1920 x 1200") /home/victor/dokument/diverse/script/Benq.icc.sh ;;
    *"1280 x 800") /home/victor/dokument/diverse/script/XPS.bright.icc.sh ;;
    *) 
        echo "no matching screen" >&2
        exit 1 
    ;;
esac  

```

Thank you Geirha!

---

