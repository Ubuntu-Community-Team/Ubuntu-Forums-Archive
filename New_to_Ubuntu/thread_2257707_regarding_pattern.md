---
title: "regarding pattern"
date: 2014-12-21
forum: New to Ubuntu
---

### Post by snehasish2 on 2014-12-21
As i am new to ubuntu i stuck in a place. how can i get a perticular  pattern from my terminal and can save to any file like .txt file or any  libre office file. 
file looks like:-
> 

[Dec 17 00:00:07] [302134] [snapdeal-suggest] [info] -  Initial query: lg e975
[Dec 17 00:00:07] [302134] [snapdeal-suggest] [info] -  Input query: lg,  Spell-corrected query: lg e975, NumSuggestions: 0, Time taken: 70  microseconds



and i want

> 

   _TIME STAND--------_                                                               _ Initial query_-------                                                         _NumSuggestions_
  [Dec 17 00:00:07]----------                                                   lg e975---------                                                                                                      0





can you guys help me..

---

### Post by schragge on 2014-12-22
You should describe format of the input file in more detail. Does the line with *NumSuggestions:* always follow the line with *Initial query:*? Is the number and the order of stanzas fixed, i.e *NumSuggestions:* is always the third stanza on the second line after *Spell-corrected query:* and before *Time taken:*?

This is probably a job for perl or python (which also happens to have a nice library [python-logsparser]("http://packages.ubuntu.com/trusty/python-logsparser")). I could quickly come up with an awk script like this:
```

#!/usr/bin/awk -f
BEGIN {
 FS=": |, "
 printf "%-18s %s %s\n", "TIME STAND",  "Initial query", "NumSuggestions"
}

/Initial query:/ {
 sub(/] \[.*/,"",$1)
 printf "%s]  %s", $1, $2
 getline
 printf "%8s\n", $6
}

```
that does what you want with your example, but it makes quite a few assumptions about the input format and thus not guaranteed to work on another set of input data.

Save this snippet of code into a file named say *prettyformat*, make it executable with
```
chmod +x prettyformat
``` and call it in terminal like this
```
./prettyformat <your_input_data >your_output_data
```

---

