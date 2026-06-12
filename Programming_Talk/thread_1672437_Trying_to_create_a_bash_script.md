---
title: "Trying to create a bash script"
date: 2011-01-20
forum: Programming Talk
---

### Post by m0ngr31 on 2011-01-20
I'm trying to create a bash script, but I'm having a problem with the output of a command.

I am using a python script to find information from Amazon and it just returns the ASIN numbers of the results.

I need just the first ASIN number that it finds, and I thought that this would do it for me: 
```
search1=$(python asin_search.py "$title" "$author" | cut -d' ' -f1)
```
But it doesn't seem to work. This is a sample result:
```
B001F0WXY0 B0011UGNDG B0015DTW50 B001F0WXX6 B001O1O6IQ B001L10ZIO B001AZJKDC
```
How can I change my first command to get just the first ASIN number?

---

### Post by ksprasad on 2011-01-20
Command seems to be fine.
Are you sure the ASIN numbers are seperated by a single space ' '?
 
Regards,
ksprasad

---

### Post by m0ngr31 on 2011-01-20
I'm pretty sure... That's an exact paste from the terminal.

---

### Post by Vaphell on 2011-01-20
does the command alone without $() produce multiple lines, 1 result/line?
care to give sample output of it? because it's not clear if its the output of the command or echo $search1

```
echo $search1 | awk '{ print $1 }'
``` (results are in single line)

```
echo "$search1" | awk 'NR==1 { print $1 }'
```
or
```
echo "$search1" | head -n 1
```
(1result/line if that's the original output, "" preserve formatting )

---

### Post by m0ngr31 on 2011-01-20
That seems to get the first number thanks! Now, one more question... How could I have an if statement asking if i had a real asin number or the error message from the python script?

---

### Post by Vaphell on 2011-01-20
what does python program return when there is an error? describe the situation more clearly
if a occurs then something should happen
if b occurs then something else should happen

---

### Post by ksprasad on 2011-01-20
-

---

### Post by m0ngr31 on 2011-01-20
> **Vaphell said:**
> what does python program return when there is an error? describe the situation more clearly
if a occurs then something should happen
if b occurs then something else should happen

Valid answer:
```
B0011UGNDG
```

Error:
```
Traceback (most recent call last):
  File "asin_search.py", line 7, in <module>
    node = api.item_search('KindleStore', Title=sys.argv[1], Author=sys.argv[2])
  File "build/bdist.macosx-10.6-universal/egg/amazonproduct.py", line 489, in item_search
  File "build/bdist.macosx-10.6-universal/egg/amazonproduct.py", line 405, in _parse
amazonproduct.NoExactMatchesFound
```

---

### Post by Vaphell on 2011-01-20
check the exit code of python program

[php]python_out=$( python asin_search.py "$title" "$author" 2>/dev/null )
exit_code=$?  # $? is the status of last command 0 = success, 1+ = error

if [ "$exit_code" == "0" ]
then
  echo everything is peachy, ASIN: $( echo $python_out | awk '{print $1}' )
else
  echo Python program returned an error
fi[/php]

---

### Post by m0ngr31 on 2011-01-20
I actually figured it out right before you posted. Thanks so much for your help! It was pretty simple:
```
if [ "$search1" ]
```
I feel like a noob for not trying that first

---

