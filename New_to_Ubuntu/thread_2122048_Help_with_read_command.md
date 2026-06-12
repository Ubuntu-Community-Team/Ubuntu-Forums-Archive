---
title: "Help with read command"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by toad3000 on 2013-03-03
I'm having trouble with the read command. So I want to keep asking the user to keep entering values but once the user stops I have to stop.

I was thinking of doing while [ true ] 
but then I need to know when the user stops. I heard pressing ctrl -d works on stdin but it's not working. 

any suggestion.

oh and I can't have the user press any key to exit.

---

### Post by papibe on 2013-03-03
Hi toad3000.
> **toad3000 said:**
> I heard pressing ctrl -d works on stdin
That is correct. But not in the middle of a line, just as the only character press on an empty line.

'read' itself can be use on the while condition as is returns true when a line is read, and false when it gets a EOF (end of file).

This would work as you intent:
```
while read line; do
    ...
done
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by toad3000 on 2013-03-03
Hey thanks a lot! I didn't know that read returns a true or false. Thank you. This clears up so much!

---

