---
title: "bash - how to set a variable when case doesn't match anything"
date: 2017-07-14
forum: Programming Talk
---

### Post by sparky-steve on 2017-07-14
Good day everyone,

I'm working on a script, and one except of that script it:

```
            fndstrg="http"            
                case "$line" in
                *"$fndstrg"* ) echo $line | tr -d '"' >> $WORKDIR/status.txt ;;
            esac

```

(And that is inside a while/done loop)

Mostly, that will find a line matching http, and output what I need (correctly) to the status file.

However, there are a few times when it will not find a match to "http" and in that case I want it to output "none" to the status file.


Any assistance is greatly welcomed!

SS

---

### Post by &amp;KyT$0P# on 2017-07-14
Does this work? -
```
            fndstrg="http"            
                case "$line" in
                *"$fndstrg"* ) echo $line | tr -d '"' >> $WORKDIR/status.txt ;;
                *) echo "none" >> $WORKDIR/status.txt ;;
            esac

```

---

### Post by sparky-steve on 2017-07-14
It does not work as I had wanted - it's throwing a lot of "none" into the status file, but that might be due to lack of context on my behalf... Let me share the entire subroutine for clarity.

```
    while read line;        do
            fndstrg="\"id\""
            case "$line" in
                *"$fndstrg"* ) echo $line | tr -d '"' | tr -d ','| awk '{print $2}' >> $WORKDIR/status.txt ;;
            esac
            fndstrg="filename"
            case "$line" in
                *"$fndstrg"* ) echo $line |tr -d ',' | cut -f 1 -d ' ' --complement >> $WORKDIR/status.txt ;;
            esac
            fndstrg="progress"
            case "$line" in
                *"$fndstrg"* ) echo $line  | tr -d '"' | tr -d ','| awk '{print $2}' >> $WORKDIR/status.txt ;;
            esac
#             fndstrg="http"
#             case "$line" in
#                 *"$fndstrg"* ) echo $line | tr -d '"' >> $WORKDIR/status.txt ;;
#             esac
            fndstrg="http"            
                case "$line" in
                *"$fndstrg"* ) echo $line | tr -d '"' >> $WORKDIR/status.txt ;;
                *) echo "none" >> $WORKDIR/status.txt ;;
            esac
        done < avail.txt 
```

The file it's reading from (avail.txt) has far more information than I need to process, so this is thinning it out, grabbing 4 vital components. What I am trying to achieve here is, when it doesnt find a match for http, it will send the text "none"

But thanks for trying!!!!

SS

---

### Post by sparky-steve on 2017-07-14
I can already envisage how to rewrite the code - but if I can get this working for now, that would be awesome.

---

### Post by &amp;KyT$0P# on 2017-07-14
> **sparky-steve said:**
> What I am trying to achieve here is, when it doesnt find a match for http, it will send the text "none"
:confused: But that's exactly what you have now, isn't it?

Please post some sample input, the expected output, and the output you're currently getting.

---

