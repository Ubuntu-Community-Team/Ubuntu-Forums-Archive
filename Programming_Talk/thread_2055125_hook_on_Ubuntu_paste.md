---
title: "hook on Ubuntu paste?"
date: 2012-09-08
forum: Programming Talk
---

### Post by scottkosty on 2012-09-08
I would like to be able to execute a function in C when the user pastes something from the clipboard.

In particular, I would like to fix this issue:
[https://github.com/shantzu/ClipIt/issues/17](https://github.com/shantzu/ClipIt/issues/17)

Any ideas?

Thanks,

Scott

---

### Post by trent.josephsen on 2012-09-08
[pwsafe](http://nsd.dyndns.org/pwsafe/) puts a password in the selection buffer and clears it out again when it's sent to an application (by middle-clicking). Perhaps you could look at how it's done there.

---

### Post by scottkosty on 2012-09-09
thanks trent.josephsen. That's a creative idea.

Now I'm thinking a better approach is just to use a different key-binding. For example, ctrl+shift+v would call a function and then would issue a system paste (i.e. a ctrl+v). How in C can I issue a system paste?

Thanks,

Scott

---

### Post by conradin on 2012-09-11
the buffer space for copy paste isnt the only buffer space. middle click is a seprate buffer then ctrl+shft+v.
perhaps a linked list if buffer spaces could give the functionality you desire? Or with pointers. Maybe dynamic memory allocation with malloc. 
is this FIFO or LIFO when the stack is popped?

---

### Post by scottkosty on 2012-09-12
> **conradin said:**
> the buffer space for copy paste isnt the only buffer space. middle click is a seprate buffer then ctrl+shft+v.
perhaps a linked list if buffer spaces could give the functionality you desire? Or with pointers. Maybe dynamic memory allocation with malloc. 
is this FIFO or LIFO when the stack is popped?

I'm not sure how the clipboard is stored by ClipIt. My guess is that it's a vector.

---

