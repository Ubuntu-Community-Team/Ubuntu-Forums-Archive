---
title: "maps, iterators, deleting objects"
date: 2007-05-13
forum: Programming Talk
---

### Post by scotty2hott2k on 2007-05-13
right, ive got a question...im using c++

i have a map of objects which are declared using new 

(to be more descriptive, i have a map of:  map <string name, gcn::Widget*> then to add a member to the map i do something like: map["button"] = new gcn::Button() )

. now, when i want to get rid of these objects, how is the best way so i don't leak memory?

is map.clear() good enough or will that simply clear out the pointer in the map to the actual memory and not release it?

sorry if its a really easy/stupid question, just thought i should make sure i get it right as i don't want to leak memory.

---

### Post by Mirrorball on 2007-05-13
[Here]("http://www.cplusplus.com/reference/stl/map/clear.html") it doesn't say that map::clear deletes dynamically allocated objects. What if you don't want them deleted, you just want to clear the map? Or the pointer could be pointing to a statically allocated object. I would delete the objects myself.

---

### Post by scotty2hott2k on 2007-05-13
sorry, but i don't compltely understand your reply. you are saying to use the delete keyword? if so, how would i go about using it? use an iterator and delete each one individually?

---

### Post by Mirrorball on 2007-05-14
Yes.

---

### Post by scotty2hott2k on 2007-05-14
sorry, but im being really thick here but can'tsee how to use the delete keyword in conjunction with the iterator...

basically i want to loop through and delete all objects in the map (using delete as i want to free the memory allocated using new).

code so far to achieve this...

```

    map <string, gcn::Widget*>::iterator it;

    for (it=widgets.begin(); it != widgets.end(); it++)
    {
       //what do i put here to actually delete them as "delete it;" doesn't work.
    }

```

---

### Post by Mirrorball on 2007-05-14
Put ```
delete *it; 
```

---

### Post by scotty2hott2k on 2007-05-14
hi, i get an error with that:

 error: type &#8216;struct std::pair<const std::basic_string<char, std::char_traits<char>, std::allocator<char> >, gcn::Widget*>&#8217; argument given to &#8216;delete&#8217;, expected pointer
:: === Build finished: 1 errors, 0 warnings ===

---

### Post by Mirrorball on 2007-05-14
Try:
```
delete it->second;
```

---

### Post by scotty2hott2k on 2007-05-14
hi, that compile and runs fine.

if i understand it right, it->first would delete the string name associated with the map and it->second deletes the data associated with the name of the map?

---

### Post by Mirrorball on 2007-05-14
Exactly.

---

### Post by scotty2hott2k on 2007-05-14
thak you very much for your time and effort in explainging it to me, it's very much appreciated.

---

