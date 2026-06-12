---
title: "Awk and/or sed help"
date: 2010-05-11
forum: Programming Talk
---

### Post by hannaman on 2010-05-11
I have a command that outputs user account information from a database.  I want to be able to extract the user's e-mail address from this file.  The catch is that the e-mail is not always in the same field of the output depending on how the comments were entered.  I thought awk would be the best way to go with this, something like:
```
command | awk -F@ '{ print $1 }' | awk '{ print $NF }'
```
The problem is that would only get the part of the e-mail before the @ and I would need the whole e-mail address.  Is there a good way to get both parts of the e-mail?  (I can add the @ back in later if I need to.)

Thanks

---

### Post by DaithiF on 2010-05-11
Hi, easier to grep for a regular expression which matches email addresses.  Example:
```
grep -oE "[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}" somefile
```

note theres lots of debate about the best regex for matching email addresses, its possible there could be some obscure corner-case email address variants that would not get matched by this particular one.  But depending on your requirements, its probably good enough.  Google regular expression email address if you are interested.

---

### Post by hannaman on 2010-05-11
Thanks for the response.  Wouldn't that grep just return the entire line from the file that matches that regex?  I would still have the problem of extracting only the e-mail address from that line.

Thanks

---

### Post by DaithiF on 2010-05-11
Nope, thats what the -o param to grep does, just returns the matching parts

---

