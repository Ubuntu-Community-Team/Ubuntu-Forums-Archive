---
title: "Another Mutt question - unknown variable"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-02-04
Hi Guys,

I have a question I'm hoping someone can help me with.

I have Mutt and Mutt-patched installed from the Ubuntu repository.
It seems to be working pretty well except when I set abook to be used as an address book for Mutt.

I put this in the .muttrc file
```
set query_command= 'abook --mutt-query '%s'" macro index,pager A ''<pipe-message>abook --add-email-quiet<return>' "add the sender address to abook"

```

and I get the error that there is a problem with:
```
add the sender to abook
```

I tried using single quotes instead of double, but I still get the error and nothing is being added to abook, although everything is being added to my mutt-alias file.

Anyone have a clue as to what the problem might be?

---

### Post by LukeMorrison on 2013-02-04
I'm not much of a programmer or familiar with mutt at all, so this may be way off, but it appears you could be missing a double quotation or have added one somewhere in the command.  You have three double quotations in that line.

---

### Post by GrouchyGaijin on 2013-02-04
> **LukeMorrison said:**
> I'm not much of a programmer or familiar with mutt at all, so this may be way off, but it appears you could be missing a double quotation or have added one somewhere in the command.  You have three double quotations in that line.

Thanks Luke,

The thing is I tried this every which way and still no luck.
I'll try some more.

---

### Post by GrouchyGaijin on 2013-02-05
The answer is [here]("http://therandymon.com/woodnotes/mutt/node46.html")

Problem was that I had not commented out:
```
set alias_file=~/.mutt/mutt-alias
source ~/.mutt/mutt-alias
```

If this is not commented out the address book code will not work.

---

