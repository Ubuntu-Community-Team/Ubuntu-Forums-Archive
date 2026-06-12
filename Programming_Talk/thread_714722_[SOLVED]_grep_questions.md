---
title: "[SOLVED] grep questions"
date: 2008-03-04
forum: Programming Talk
---

### Post by VChief on 2008-03-04
Ok, I'm doing a UNIX class and we're doing grep. I'm having a problem though. We're using UNIX Shells by Example by Quigley. I'm doing the grep exercise. Now, I must not understand the metacharacters and am having trouble. The file used has a list of people along with their addresses, birthdates, salaries, etc. One of the exercises calls to find all strings ending in 700. Now, it says in the book that '$' is used as an end of line anchor and that using it should match all strings ending in 700. That doesn't work for me. However, \> does. That's happened a couple times in the exercises. According to the book, \> should be an end of word anchor. But, I tested it out with other lines and \> doesn't come back with anything except end of string results ($ doesn't seem to do anything). Also, it says that * should match 0 or more characters before the expression, but it doesn't do that. I thought it was a difference between UNIX and GNU, but the book covers GNU with the same thing. What am I missing here? I know I've got to be doing something wrong. Thank you very much!

---

### Post by ghostdog74 on 2008-03-04
to match beginning, use  ^

eg
```

# more file
700 slkdjflsf
lkasjflks 700
# grep "^700" file
700 slkdjflsf
# grep "700$" file
lkasjflks 700     

```

---

### Post by VChief on 2008-03-04
I'm trying to match the end, not the beginning.

---

### Post by ruy_lopez on 2008-03-04
Look at ghostdog's last example

---

### Post by VChief on 2008-03-04
> **leeward said:**
>  it says in the book that '$' is used as an end of line anchor and that using it should match all strings ending in 700. That doesn't work for me. However, \> does. ... ($ doesn't seem to do anything).  <--

---

### Post by ruy_lopez on 2008-03-04
Show the input/output.

---

### Post by VChief on 2008-03-04
Well, that was strange. I had a feeling the file was the problem. I copied, line by line, the file to a new file and everything worked fine. I don't know. Thank you, though.

---

