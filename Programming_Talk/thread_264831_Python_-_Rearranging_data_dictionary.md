---
title: "Python - Rearranging data dictionary"
date: 2006-09-25
forum: Programming Talk
---

### Post by ironfistchamp on 2006-09-25
Hey all its me again :p 

Right here is the problem this time. I have a data dictionary with the keys 1 - 10. Each key has a value of "TESTX" where X is a number. My problem is that the program can delete say key 2 and its value but I cant figure out how I can then change key 3 to key 2 and key 4 to key 3 and so on. I need to keep the order sequential. Is there a way to do this or is there a different storage method that would be more suited to what I want to do. 

Thanks for any help

Ironfistchamp

---

### Post by ohgod on 2006-09-25
Do you need to access the dict objects by strings?  If you're just using the numbers 1-10 as keys, maybe you could use a list instead?  That way if you delete list[2] then all the other elements in the list will 'slide down' to fill the spot you just deleted.

---

### Post by ironfistchamp on 2006-09-25
Perfect thats exactly what I wanted. Thanks very much


Ironfistchamp

---

