---
title: "Time reminder script"
date: 2011-05-27
forum: Programming Talk
---

### Post by hakermania on 2011-05-27
A simple time reminder script. It works with espeak or with festival, if installed.
Comments and recommendations are welcome.
Personally I have this script running on my startup because it is good reminder when you e.g. play a fullscreen game and you cannot see the time :P

```

#!/bin/bash
if [ X"$(which festival)" != X"" ]; then
Command="festival --tts"
else
Command="espeak"
fi
while [ 1 ]; do
if [ X"$(date '+%M')" = X"00" ]; then
case $(date '+%I') in
    01) echo "The time is One" | $Command;;
    02) echo "The time is Two" | $Command;;
    03) echo "The time is Three" | $Command;;
    04) echo "The time is Four" | $Command;;
    05) echo "The time is Five" | $Command;;
    06) echo "The time is Six" | $Command;;
    07) echo "The time is Seven" | $Command;;
    08) echo "The time is Eight" | $Command;;
    09) echo "The time is Nine" | $Command;;
    10) echo "The time is Ten" | $Command;;
    11) echo "The time is Eleven" | $Command;;
    12) echo "The time is Twelve" | $Command;;
    *) echo "Couldn't read time" | $Command;;
esac
fi
sleep 1m
done

```

---

### Post by kaibob on 2011-05-27
I tested the shell script and it seems to work fine. So, my comments are mostly items to consider.

* Indent the script for improved readability. There are many guides on this topic--the first referenced link below is one.

* See the second link below concerning the 'x"$foo" hack'. 

* My knowledge on this topic is limited, and there seems to be significant disagreement on this issue, but consider the use of "type" rather than "which" to check whether festival and espeak are installed. Perhaps other forum members will have some thoughts on this. See the third link below for a discussion of this topic. 

* The script assumes that espeak is always installed. Instead, should there be an alternative (e.g. report and exit) in case neither festival nor espeak are installed?

* You should use "-eq" rather than "=" when testing numbers with "[" or "[[". With bash, you may want to consider using "((". See the fourth link below. This assumes you have deleted the 'x"$foo" hack'.  

* The script echoes "$Command - Pernw" once every minute. I don't understand the reason for this. 

* I don't have festival installed but espeak works with numbers. Perhaps you could do away with the lengthy case statement. 

REFERENCE
[http://wiki.bash-hackers.org/scripting/style](http://wiki.bash-hackers.org/scripting/style)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://stackoverflow.com/questions/592620/check-if-a-program-exists-from-a-bash-script](http://stackoverflow.com/questions/592620/check-if-a-program-exists-from-a-bash-script)
[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)

---

### Post by hakermania on 2011-05-27
Very nice and helpful reply!
Thx for the links, i'll fix the code and i'll post back for any other suggestions, if any...

---

### Post by hakermania on 2011-05-27
Ok, this is the new version of the script, too simplified, after knowing that the text-to-speech tools can read numbers:
```
#!/bin/bash
type festival 1> /dev/null 2> /dev/null
if [ $? -eq 0 ]; then
    Command="festival --tts"
else
    type espeak 1> /dev/null 2> /dev/null
    if [ $? -eq 0 ]; then
        Command="espeak"
    else
        echo "There doesn't seem to be any program for text-to-speech conversion. Please install 'festival' or 'espeak'" >&2
        exit 2
    fi
fi

while [ 1 ]; do
    if [ $(date '+%M') -eq 0 ]; then
        echo "The time is $(date '+%l')" | $Command;
    fi
sleep 1m
done
```

---

### Post by kaibob on 2011-05-27
That looks good. I have included below the shell script as I would write it, but this is more a matter of style and preference than right or wrong. Also, my Bash skills are only middling, so there may be a better way to do this. 

```

#!/bin/bash

if type -P festival > /dev/null 2>&1 ; then
  command="festival --tts"
elif type espeak > /dev/null 2>&1 ; then
  command="espeak"
else
  echo "Festival and espeak not installed!"
  exit 1
fi

while true ; do
  if (("$(date '+%M')" == 0)) ; then
    echo "The time is $(date '+%l')" | "$command"
  fi
  sleep 1m
done

```

---

### Post by hakermania on 2011-05-28
Are you sure this gonna work?
type returns 0 if program exists, and you've written
if type -p festival; then command=festival

EDIT: Explained in the Bashpitfalls on #9, thx

---

