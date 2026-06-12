---
title: "[SOLVED] Bash Plz Help!"
date: 2008-04-19
forum: Programming Talk
---

### Post by fallenshadow on 2008-04-19
Can someone show me an example on how to do a double multiple choice in bash. Something like: 

if y then [commands]
if n then [go to next options]
if q then [exit]

next options
if y then [commands]
if n then [exit]

I know this may look a bit confusing but hopefully someone will understand.

---

### Post by ghostdog74 on 2008-04-19
see [here]("http://tldp.org/LDP/abs/html/comparison-ops.html") for more info, especially look at the examples at the bottom

---

### Post by fallenshadow on 2008-04-19
I don't understand it, just to let everyone know I am not a programmer but I understand basic concepts such as commands should have if [something] then [something]

---

### Post by ghostdog74 on 2008-04-19
how many hours did you take to read the document before you say you don't understand. How about [this]("http://tldp.org/LDP/abs/html/part2.html"), the basics ? It shows you how to declare variables. From there, you can better understand how to compare variables using if/else .

---

### Post by fallenshadow on 2008-04-19
I found this code some where and it gives me a yes no quit choice but I don't know why my commands won't work and I don't know how to get the no choice to go to 2nd y/n options.

```
{
printf 'Proceed with the installation? (y/n/q): '
    read yn

    case $yn in
      y | Y)
        cp "blah" "blah2/blah3"
        ;;
      n | N)
        What goes here? to get to 2nd options
        ;;
      q | Q)
        exit 
        ;;
      *)
        echo ""
        echo "Please enter 'y', 'n', or 'q'."
}
```

---

### Post by ghostdog74 on 2008-04-19
Read [this page]("http://tldp.org/LDP/abs/html/testbranch.html#EX29") and see if you can spot the difference using case.

---

### Post by fallenshadow on 2008-04-19
The only way I really learn things is by example, if you could show me an example I would understand.

---

### Post by ghostdog74 on 2008-04-19
look at example 10-24 from the link i gave!. check the case syntax. it ends with esac. yours is missing.

---

### Post by fallenshadow on 2008-04-19
Why didn't you say that in the first place?? :confused:

Anyway does not matter im sorted now.

---

### Post by ghostdog74 on 2008-04-19
> **fallenshadow said:**
> Why didn't you say that in the first place?? :confused:


I have shown you where you can find examples from the start. its really not my job to spoon feed you till the end.

---

