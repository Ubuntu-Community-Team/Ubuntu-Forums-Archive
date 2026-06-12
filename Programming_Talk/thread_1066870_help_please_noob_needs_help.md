---
title: "help please noob needs help"
date: 2009-02-11
forum: Programming Talk
---

### Post by fox_mccloud on 2009-02-11
hey all-

Hoping you all could shed some light for me im new to the world of programing and my boss needs me to write something that will allow one text page to fill out another text page specifically i need a order form that is in txt format that has the customers name and address on it in lines 2 and lines 3 through 5 to auto fill a place on a sheet for the address labels to print from that has possitions for 10 names and addresses that txt file can be changed depending on what needs to be written please just let me now if there is any way to make this possible thank you all and if i can do anything in return just let me know thank you all again

-debugged in Mississippi

---

### Post by rgb96 on 2009-02-11
You do know these are Ubuntu forums, and not programming forums, right?

What language are you trying to program in? I can probably point you in the right direction.

Edit: Also, lrn 2 punctuate.

---

### Post by bapoumba on 2009-02-11
Moved to PT, but meh.. Openoffice does this, no?

---

### Post by jimi_hendrix on 2009-02-11
this sounds like a job for PERL!

---

### Post by badperson on 2009-02-11
try this  in perl:
```
s/[^a-z |^\s]+//g;
```

that will strip out all puncution...:lolflag:

It sounds like you want to read one text file and create a new text file that has either the same information formatted differently, or only selected information included? 
bp

---

### Post by Krupski on 2009-02-11
> **rgb96 said:**
> You do know these are Ubuntu forums, and not programming forums, right?

What language are you trying to program in? I can probably point you in the right direction.

Edit: Also, lrn 2 punctuate.

Hey I'm not a mod and it's none of my business, but why jump on the OP?

How about U lrn 2 B nicer?

---

### Post by Krupski on 2009-02-11
> **fox_mccloud said:**
> hey all-

Hoping you all could shed some light for me im new to the world of programing and my boss needs me to write something that will allow one text page to fill out another text page specifically i need a order form that is in txt format that has the customers name and address on it in lines 2 and lines 3 through 5 to auto fill a place on a sheet for the address labels to print from that has possitions for 10 names and addresses that txt file can be changed depending on what needs to be written please just let me now if there is any way to make this possible thank you all and if i can do anything in return just let me know thank you all again

-debugged in Mississippi

Do you want to make a program that prints out a complete (filled out) form - the same form each time but with data (i.e. names and addresses) obtained from another file?

If so... it's easy. Hopefully, your "database" file (the one with the names and such) has a standard and consistent format.

Then, you could just open the database file and read a fixed number of strings from it, like this (pseudo code):

```

open "database.file" for input

while not eof
  read cust_name$
  read cust_addr$
  read cust_city$
  read cust_state$
  read cust_zip$
  call print_label
wend

close "database.file"

end

print_label:
  print cust_name$
  print cust_addr$
  print cust_city$+", "+cust_state$
  print cust_zip$
return


```

Note that your database file MUST have exactly 5 entries per customer (even if they are blank). Otherwise, reading 5 at a time will throw you out of sync and you'll end up printing things like the customer name for a zip code or whatever!  :)

Hope this helps somewhat....

-- Roger

---

