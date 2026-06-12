---
title: "Shell script timestamp variable"
date: 2015-02-28
forum: Programming Talk
---

### Post by fr33z0n3r on 2015-02-28
I'm no linux expert so I was hoping someone could help me on this shell script issue with a timestamp variable.

This is the line I have in use.  It is a line to insert into my logfile for the shell script.  I am noticing that the date does not update when I reuse the variable LOGENTRY.  How can I get this variable to update the timestamp?

```
LOGENTRY="`date '+%b %d %k:%M:%S'` `hostname -s` `basename $0`:"
echo $LOGENTRY  something to log

```


Thanks in advance!

---

### Post by Gustaf_Alhll on 2015-02-28
Make a loop and delay by using "sleep 1".
Ex.
```
while true; do
    LOGENTRY="`date '+%b %d %k:%M:%S'` `hostname -s` `basename $0`:"
    echo $LOGENTRY  something to log
    sleep 1
done
```
There are better ways to do it, but this is one way to.
Hope this helps!

---

### Post by Lars Noodén on 2015-02-28
I'm pretty sure that there is not a way to use a regular environment variable in that way.  I think you'd have to put it on a single line:

```

echo "$(/bin/date +'%b %d %k:%M:%S') $(/bin/hostname -s) $(/usr/bin/basename -- "$0"):" "something to log"

```

---

### Post by fr33z0n3r on 2015-02-28
Rats!  I have been playing with it since posting and discovered that by eliminating the VERY helpful variable, it was able to update. 

I just figured linux is so powerful, why can't a variable actively evaluate again and again by default?

Is there some way to force evaluation?  I've seen eval?

---

### Post by ian-weisser on 2015-02-28
It's just a variable - an inert set of data bytes. It's not a class or a function or a method or anything active.

You can write a function to update the variable if you really want to.

Or you can write a function to create an updated timestamp string each time you need to log something.

---

### Post by ofnuts on 2015-02-28
What you can do is keep the format in a variable to make sure that the same date format is used consistently. But considering that all logging goes also to the same file, if you want to make your logging simpler you write a function:

```

function log {
        printf "%s (%06d): %s\n" "$(date '+%F %H:%M:%S')" $$ "$*" >> /some/path/to/file.log
}

```
and in your code
```

log "this line will be logged"
log this line will be logged too

```

---

### Post by fr33z0n3r on 2015-03-02
@ofnuts - I thought I submitted my response, but I guess I missed that.  I went with middle ground, but I will look to implement a simple function like you proposed.  Its not painful.  Thanks!

---

