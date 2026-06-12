---
title: "[c] why is this a if statement?"
date: 2010-04-07
forum: Programming Talk
---

### Post by lavinog on 2010-04-07
Looking at the ureadahead source I see:
```

/* Be nicer */
if (nice (15))
	;

```

What benefit does using an if block here offer?

---

### Post by Ravenshade on 2010-04-07
Someone missed out the statement. The if function isn't doing anything. (From my perspective). Unless C does something with spaces.

---

### Post by saulgoode on 2010-04-08
I am going to engage in some wild speculation and hypothesize that it has something to do with being able to debug the program, particularly on an ARM processor. 

I admit I am just guessing (and assuming that the programmer hasn't erred in the coding), but the ARM processor presents a couple of curious challenges for debuggers. For example, whether an instruction gets executed can be made dependent upon the state of processor status flags at run time. Adding a superfluous 'if' may be to permit a breakpoint to be set, trace logging, or single-stepping to take place which might otherwise be impossible.

---

### Post by JDShu on 2010-04-08
I took a look at the source, it looks like it was just done to improve legibility. Better than just calling nice() by itself in the middle of all the if statements is my guess. I would appreciate clarification as well, because this is an interesting question.

---

### Post by MadCow108 on 2010-04-08
this is also often done to avoid the unused result warning of gcc
the compiler will optimize the unnecessary if away

---

### Post by MindSz on 2010-04-08
> **MadCow108 said:**
> this is also often done to avoid the unused result warning of gcc
the compiler will optimize the unnecessary if away

I agree. Also, it can serve as a place holder in case you eventually decide to do something special in that particular case.

---

### Post by Cracauer on 2010-04-08
To me that smells "company policy A requires to have warnings about ignored return values on but company policy B forbids casting away the return value with (void)nice(15)" so let's go make a real mess.

---

