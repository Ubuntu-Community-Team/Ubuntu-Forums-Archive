---
title: "If then and user choices in a script"
date: 2013-05-22
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-05-22
Hi Guys,

I'm back with more annoying questions.

Background:

I'm using a script called [tasky]("https://github.com/connermcd/tasky/tree/d73118428ba62c67bc37735d35b81aaad3158a1c") to add and remove items from Google tasks.

The command to add a task is simple:

```
tasky a subject -d date -n note
```

In order to make the process easier I wrote a script that walks the user through adding a new task.

```

#!/bin/bash
read -p Subject: sub
read -p "Due Date(MM/DD/YY):" ddate
read -p "Note:" note


~/scripts/tasky a "$sub" -d "$ddate" -n "$note"


```

With this script, the user has to provide a date and note.

What would I need for the script to ask the user:

3. **If** there is a due date enter it, if not skip it.
4.** If **there is a note, enter it, if not skip it.

The part I don't know how to do is if there is a date enter it or skip if there is no due date and if there is a note enter it or skip if there is no note.

I hope that makes sense.

I really appreciate the help guys!

---

### Post by Vaphell on 2013-05-22
```
#!/bin/bash

params=()
read -p Subject: sub
read -p "Due Date(MM/DD/YY):" ddate
read -p "Note:" note
[ -n $ddate ] && params+=( "-d" "$ddate" )
[ -n $note ] && params+=( "-n" "$note" )

~/scripts/tasky a "$sub" "${params[@]}"
```

---

### Post by GrouchyGaijin on 2013-05-22
Thank you.
That is pretty cool except the note works, I can either add a note or skip it.
But if I do not add a date, it crashes.

```

Traceback (most recent call last):
  File "/home/john/scripts/tasky", line 457, in <module>
    main(parse_arguments(sys.argv))
  File "/home/john/scripts/tasky", line 440, in main
    handle_input_args(args)
  File "/home/john/scripts/tasky", line 250, in handle_input_args
    d = time.strptime(dstr, "%m/%d/%y")
  File "/usr/lib/python2.7/_strptime.py", line 454, in _strptime_time
    return _strptime(data_string, format)[0]
  File "/usr/lib/python2.7/_strptime.py", line 325, in _strptime
    (data_string, format))
ValueError: time data '' does not match format '%m/%d/%y'



```

---

### Post by Vaphell on 2013-05-22
is it possible to run **~/scripts/tasky a "subject"** without date and note?

---

### Post by GrouchyGaijin on 2013-05-22
Yes it is.

---

### Post by Vaphell on 2013-05-22
me fail
```
#!/bin/bash

params=()
read -p "Subject: " sub
read -p "Due date (MM/DD/YY): " ddate
read -p "Note: " note

[ -n[COLOR="#0000FF"] "[/COLOR]$ddate[COLOR="#0000FF"]"[/COLOR] ] && params+=( "-d" "$ddate" )
[ -n [COLOR="#0000FF"]"[/COLOR]$note[COLOR="#0000FF"]"[/COLOR] ] && params+=( "-n" "$note" )

~/scripts/tasky a "$sub" "${params[@]}"
```

---

### Post by GrouchyGaijin on 2013-05-22
That fixed it :-)
Thank you man!!

---

