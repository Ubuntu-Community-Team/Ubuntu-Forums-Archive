---
title: "seeking an fstream object"
date: 2007-08-22
forum: Programming Talk
---

### Post by desijays on 2007-08-22
could someone tell me the various function members available to perform seeking on an ifstream object?

and could there be a reason why the second statement in......

```

ifstream.seekg( 0, ios::beg ); 
ifstream.tellg();

```
would return -1 (which is failure)

---

### Post by Angry on 2007-08-22
Judging by what little code is shown, the only thing I can think of is that the file is in an incorrect state (could not be opened, is bad, whatever).

Check the state flag of the object (good, bad, fail or eof) to determine if a read is possible.

---

