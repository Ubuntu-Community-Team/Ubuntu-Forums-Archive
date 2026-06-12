---
title: "BASH: grep and regex"
date: 2011-07-29
forum: Programming Talk
---

### Post by Volens on 2011-07-29
I'm currently working with switches and routers and I'm trying to simplify some tasks using a bash script.
 
Basically its runs some commands via ssh and dumps the info to a text file on the local machine. I need to pull the last item from the line, however, I would prever that it didn't pull the leading space with it. I'm having trouble figurig out the right regular expression to isolate this data.
 
```
 
PORT=`grep -o -e '[[:space:]].*$' ./mactable`

```
 
My second problem is similar. A later command pulls a configuration file from the router/switch with a line like:
```

description            blaheastwingblah

```
 
How can I find this line then only take the end of it?
 
Do I pipe a grep from the initial grep command or use some other command like awk?
 
Yesterday I was using Perl (until I ran into other unrelated issues) and you could group sections that would be stored in an array as $1, $2, $3 etc. Is there something like that with grep groupings?
 
This is really only my second day with regex, I never knew grep was so versatile and I'm barely familiar with awk.
 
Thanks

---

### Post by Bachstelze on 2011-07-29
It would be better if you provided sample input for the first one.

The second one is easy enough;

```
firas@aoba ~ % echo "description            blaheastwingblah" | awk '{print $2}'
blaheastwingblah

```

---

### Post by Volens on 2011-07-29
I was a little messy with my descrption of the first one, but its essentially that same as the second one. It looks like awk is better suited to my current needs (maybe some grep | awk too).
 
Looks like I've been slacking in regards to my knowledge of commands...
 
Thanks

---

