---
title: "find with regex appears impossible - help needed"
date: 2010-11-03
forum: Programming Talk
---

### Post by wiseguy12851 on 2010-11-03
I have spent the past 5 hours trying to get an extremely simple script to run, I'm using Ubuntu 10.10

I'm trying to get the "find" command to simply search a directory i created for files based on a regular expression which will be stored in a variable for whatever use.

The filename needs to match this regex:
```
"^.?[a-zA-Z0-9_.-]+.bash$"
```Here's what I've tried:

```
find ~/the/directory -type f -regextype 'posix-basic' -regex '^.?[a-zA-Z0-9_.-]+.bash$'
find ~/the/directory -type f -regextype 'posix-egrep' -regex '^.?[a-zA-Z0-9_.-]+.bash$'
find ~/the/directory -type f -regextype 'posix-basic' -name '^.?[a-zA-Z0-9_.-]+.bash$'
find ~/the/directory -type f -regextype 'posix-egrep' -name '^.?[a-zA-Z0-9_.-]+.bash$'
find ~/the/directory -type f | grep '^.?[a-zA-Z0-9_.-]+.bash$'
```

to name a few, help appreciated

---

### Post by saulgoode on 2010-11-03
What makes you think there's a problem?

---

### Post by wiseguy12851 on 2010-11-03
Nothing happens, It finds nothing - I've been trying different strategies and combinations for about 5 1/2 hours now. When I hit enter it finds nothing, displays nothing, and immediately awaits new command. I'm about to go crazy - this is ridiculously simple but I've wasted nearly 6 hours at this task.

---

### Post by tauman5263 on 2010-11-03
Why don't you try something like this:

```
ls -a | grep -E '^.?[a-zA-Z0-9_.-]+.bash$'
```

---

### Post by saulgoode on 2010-11-03
Be aware that the output of '*find*' will include the path to the file (the same path that you provide). If your regular expression is expected to match only the filename -- not the full path -- then you should use the standard UNIX command, '*basename*', to extract it.

```
find ~/the/directory -type f -exec basename {} \; | grep '^.?[a-zA-Z0-9_.-]+.bash$'
```

---

### Post by wiseguy12851 on 2010-11-04
Thanks for you help, One of the million combinations did succeed. If I remove the ( ^ ) & ( $ ) and write it like below it works.

```
find ~/the/directory -type f | awk '$0 ~ "/[a-zA-Z0-9.-]+.bash" {print $1}'
```

I still find it a little extreme to use awk on such a simple task, I will try your solutions now but this is a temporary fix. I used find because I needed the full path to be shown, awk also allows me to use the real regex commands which none of the others including grep allowed such as the ( + ) symbol

If you have any other simpler solutions I'm still open but I've got it fixed for now

---

### Post by Arndt on 2010-11-04
> **wiseguy12851 said:**
> Thanks for you help, One of the million combinations did succeed. If I remove the ( ^ ) & ( $ ) and write it like below it works.

```
find ~/the/directory -type f | awk '$0 ~ "/[a-zA-Z0-9.-]+.bash" {print $1}'
```

I still find it a little extreme to use awk on such a simple task, I will try your solutions now but this is a temporary fix. I used find because I needed the full path to be shown, awk also allows me to use the real regex commands which none of the others including grep allowed such as the ( + ) symbol

If you have any other simpler solutions I'm still open but I've got it fixed for now

I suppose you have thought of it already, but won't find -name '*.bash' do what you want? It does match a little more than your original.

---

### Post by rtlong on 2011-08-22
I realize this is old, but for anyone who stumbles upon it, I hope this helps.

[FONT="Courier New"]find[/FONT]'s [FONT="Courier New"]-regex[/FONT] option is a match on the **whole path**, so there is no need to use the **^** and **$** characters to specify the bounds for your expression. The OP would simply have needed to add '[FONT="Courier New"].+/[/FONT]' to the start of his original regex to make find happy.

```
find ~/the/directory -type f -regex '.+/.?[a-zA-Z0-9_.-]+.bash'
```

also note that if you're trying to match an optional literal "." (period), then you should escape it in the pattern:

```
find ~/the/directory -type f -regex '.+/\.?[a-zA-Z0-9_.-]+\.bash'
```

Then it will match:
```
~/the/directory/.foobar.bash
```

but it will not match this, which the original expression would have done:
```
~/the/directory/foobar-bash
```

---

### Post by ofnuts on 2011-08-22
> **wiseguy12851 said:**
> Thanks for you help, One of the million combinations did succeed. If I remove the ( ^ ) & ( $ ) and write it like below it works.

```
find ~/the/directory -type f | awk '$0 ~ "/[a-zA-Z0-9.-]+.bash" {print $1}'
```I still find it a little extreme to use awk on such a simple task, I will try your solutions now but this is a temporary fix. I used find because I needed the full path to be shown, awk also allows me to use the real regex commands which none of the others including grep allowed such as the ( + ) symbol

If you have any other simpler solutions I'm still open but I've got it fixed for now
grep -E or egrep does accept more complete regexps.

---

### Post by ziekfiguur on 2011-08-24
> **ofnuts said:**
> grep -E or egrep does accept more complete regexps.
Not necessarily, you can use '-regextype posix-egrep' or '-regextype posix-extended' with find.

---

### Post by ofnuts on 2011-08-25
> **ziekfiguur said:**
> Not necessarily, you can use '-regextype posix-egrep' or '-regextype posix-extended' with find.I was just answering to "*which none of the others including grep allowed such as the ( + ) symbol*"

---

