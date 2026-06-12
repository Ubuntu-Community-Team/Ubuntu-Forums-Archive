---
title: "Store variables in a Dynamic Data Structure?"
date: 2007-06-30
forum: Programming Talk
---

### Post by squirrelix on 2007-06-30
Hey kids,
    I am writing a program, and I keep adding variables. For each variable, I need to add it to a help menu, as well as the code to change the value. 
   Then I wondered. Is there a way to store your program variables (global ones) in a data structure that you could iterate over. I looked at a hash table, (Using Java at the moment), but the code to tweak the variable is ugly. (Get the object from the table, cast to a float, add a value to it, stuff it back in the table). 
  This is really a "has anyone else wondered about this" kind of question. I understand that in certain languages, you can have variable name variable names (no, not a typo :P). Can anyone verify that?

 Thanks, and just curious. 
-- Squirrel

---

### Post by Dancingwllamas on 2007-07-01
If I understand what you are trying to do, you probably want to use an array or a linked list. An array will be very easy to iterate over (and very fast). Linked Lists will be trivial to expand as you add new items. I would recommend looking at [arrays]("http://java.about.com/od/beginningjava/l/aa_array.htm") first - they are generally easier for people to understand.

Feel free to ask if you need any more specifics.

---

### Post by brooksbp on 2007-07-01
> Then I wondered. Is there a way to store your program variables (global ones) in a data structure that you could iterate over.

If that's your main question... Absolutely.  There actually is a dedicated CS course at most universitys on this subject: Data Structures.  Google it.

---

