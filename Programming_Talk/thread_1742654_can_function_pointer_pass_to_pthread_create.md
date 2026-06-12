---
title: "can function pointer pass to pthread_create?"
date: 2011-04-29
forum: Programming Talk
---

### Post by william2011 on 2011-04-29
can function pointer pass to pthread_create?
 
if so, if firstly i point to static function A, then 
i would like to change function pointer to point to static function B.
 
do it be error?
 
if no error, if i point back to function A, can the content of function A running before recovered?
 
if no, how to save the content of function A when i interrupt it when it is running

---

### Post by NovaAesa on 2011-04-29
I'm having trouble understanding you question. Are you changing the pointer *after* it has already been passed to pthread_create ? If so, changing the pointer should have no effect, since the pointer is passed by value.

---

### Post by william2011 on 2011-04-29
yes, if i have passed a function pointer (which pointed to function A) to pthread_create .
 
Then i would like to make the function pointer to point to another function B
 
will function A loss its data such as variables it run
 
if i do not save data in function A when it is signaled to stop.
 
how to save the status of function when it is interrupted?
 
i heard that there is a context i should save, but i do not know how to save these registers and to where? Any example to show how to save these registers and recover for function A so that pthread_create's function pointer can continue running function A as i do not understand how to use pop and push to switch between three or more functions
 
 
No effect, but pthread_create is running a function pointer's function address, i just change the address to another function
 
if function pointer not work,
 
**How one thread switch between two functions?**

---

### Post by schauerlich on 2011-04-29
Let me get this straight: You want a thread to run a function A, and then when it's done with that, run a function B? Just wrap both in another function, C, and pass in C.

---

### Post by NovaAesa on 2011-04-29
> **william2011 said:**
> **How one thread switch between two functions?**

schauerlich is right, as far as I can tell, you can't do this without wrapping the functions together inside another function.

---

### Post by schauerlich on 2011-04-29
> **NovaAesa said:**
> schauerlich is right, as far as I can tell, you can't do this without wrapping the functions together inside another function.

Another option is to manage a global queue of tasks (in the form of function pointers) that the various threads can choose from as they complete their previous task. That adds complexity and overhead (locking the task queue), though.

---

### Post by william2011 on 2011-04-29
how about the function contain a infinite loop that never stop, how to handle it to pass to function B. and back to function A to continue his job in the loop?

---

### Post by schauerlich on 2011-04-30
> **william2011 said:**
> how about the function contain a infinite loop that never stop, how to handle it to pass to function B. and back to function A to continue his job in the loop?

Sorry, I don't really understand what you're saying. Can you tell us what you're trying to accomplish?

---

