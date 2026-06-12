---
title: "Memory usage of a simple JAva/Swing application"
date: 2009-06-29
forum: Programming Talk
---

### Post by sthiranga on 2009-06-29
I develop java swing programme that has lot of(jtabpanne) swing componat.
My problem is when i run my project it consume lot of memory.Initially 30 MB.
After loading that jtabbedpane containig form it will increase 5-10 MB sometime.
(this form load data from databse and save in to database/Mysql).After working 4-5 hours 
momery increase 80-90 MB and programme struck.

Also i set unusable object to null and but I can't see the memory decrease.
I don't know how to handle this problem.Really need some help.
I want know what is limit of heap size and how to incrase Heap size(Use Netbean IDE). 

Thanks.

---

### Post by Zugzwang on 2009-06-29
Memory will not be freed until the garbage collector is invoked (which is done automatically, but can also be done manually). However, even then, memory is not released by the JVM to the system. All in all, this shoudln't be your concern. If you want an application to use only a small number of memory, set the maximum amount of memory the JVM should allocate accordingly using the "-Xmx***m" switch for "***" being the amount of RAM in megabytes. Unfortunately, you have to guess which is the correct value in practice.

However, if your program gets stuck (if this is what you mean, please use a spell-checker before posting, otherwise we have to get what you mean) then this is unlikely to be caused by not giving the application enough memory as in this case a certain exception (OutOfMemoryException) is thrown when this happens. So you should see that somewhere.

Remember: *NEVER* catch an exception without reacting to it accordingly. If certain exceptions might be ignored in some situations, catch only these and not all RuntimeExceptions or all exception and drop them, otherwise you will not be informed.

As far as increasing the amount of memory available to the JVM is concerned, use the "-Xmx" switch as described above. Use google for finding out where to put that in Netbeans.

---

### Post by soltanis on 2009-06-29
This behavior is probably by virtue of the fact that Java is a memory whore, so I doubt there is much you can do besides increase the heap size (I interpreted "struck" as meaning "crashed").

---

### Post by sthiranga on 2009-06-30
Sorry for the spelling mistake.I was hurry.After 5-6 hours system stuck.

---

### Post by pbpersson on 2009-06-30
When you say the application became "stuck", do you just mean the GUI froze up?  Are you sure the application was not still running in the background and updating the database?  I have seen this happen before.

---

### Post by sthiranga on 2009-06-30
When application stuck can't load form or click buttons.those are not responded.So I can't add data to database.But other windows application are running without problems.

---

### Post by Zugzwang on 2009-06-30
> **sthiranga said:**
> When application stuck can't load form or click buttons.those are not responded.So I can't add data to database.But other windows application are running without problems.

Are you sure that you are not simply throwing exceptions away in your program? This is precisely what often happens in such situations when you run out of memory.

---

### Post by sthiranga on 2009-06-30
This Exception is thrown when it struk.
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space

---

### Post by Zugzwang on 2009-06-30
> **sthiranga said:**
> This Exception is thrown when it struk.
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space

There you have the problem. Note that you didn't write this in your original post.

Solution: Increase the heap size. Details where to put the respective option in netbeans can be found, for example, here: [http://www.codemiles.com/java/here-how-to-increase-java-heap-size-t663.html](http://www.codemiles.com/java/here-how-to-increase-java-heap-size-t663.html)

---

### Post by sthiranga on 2009-07-01
Thank for the help.

---

