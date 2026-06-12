---
title: "make make make and  make"
date: 2007-07-26
forum: Programming Talk
---

### Post by desijays on 2007-07-26
_Scenario_

I have a 102 'c' files. All these 'c' files were downloaded of the net. I made 3 extra 'c' files, containing code that calls some functions in the downloaded 'c' files. 

since the 3 'c' files were created by me, i can use 'make' to compile them cos i know in what ways they are interdependent.

but my 3 'c' files are using functions from the downloaded 'c' files. And I don't know how they are interdependent among them.

Now, how can I  use 'make' to compile the above scenario successfully?

Thanks

---

### Post by zanglang on 2007-07-26
The files didn't come with a makefile? Maybe you can try 'makedepend', it will basically go through all sourcefiles, parse any preprocessor directives and then write it into a makefile, creating a new one or append to existing. Check the manpages. :)

---

### Post by desijays on 2007-07-26
> **zanglang said:**
> The files didn't come with a makefile? Maybe you can try 'makedepend', it will basically go through all sourcefiles, parse any preprocessor directives and then write it into a makefile, creating a new one or append to existing. Check the manpages. :)

the files did come with a 'makefile.in' and a 'makefile.am'. I don't know what they are. I opened them expecting to see a list of rules, as is specified in a 'makefile', but i all i got was code i didn't understand.

say, the 102 'c' files did come with a makefile, now, all i have to do is add the names of my 'c' files in them appropriately, right?

but in any case, thanks for the lead in the form of 'makedepend'. I never knew something like that existed. I'll go thru it.

---

### Post by zanglang on 2007-07-26
Do they come with a file called 'autogen.sh', or 'configure'? If so, execute them first. That would probably generate a makefile which you can use. And yes, you'll just have to add them in.

---

