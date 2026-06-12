---
title: "Java memory leak"
date: 2005-04-22
forum: Programming Talk
---

### Post by nocturn on 2005-04-22
I 'inherited' a java app at work that now appears to have a memory leak.
I do not have Java experience, what would be the best way to track down the leak, are there any good tools that can help?

Thanks.

---

### Post by HungSquirrel on 2005-04-22
Java IS a memory leak.  :P

---

### Post by nocturn on 2005-04-22
[QUOTE=HungSquirrel]Java IS a memory leak.  :P[/QUOTE]
Tell me about it...

If I get my way (which is very possible), most of the code will gradually be replaced with something in perl or python.

---

### Post by defkewl on 2005-04-25
[QUOTE=nocturn]Tell me about it...

If I get my way (which is very possible), most of the code will gradually be replaced with something in perl or python.[/QUOTE]
 Try these : [http://www.quest.com/jprobe/debugger.asp](http://www.quest.com/jprobe/debugger.asp)

---

### Post by nocturn on 2005-04-28
Thanks for the tips

I tried the profiler, but beause it is a class, called from a JSP file, it does not run inside it.

I cannot figure out what it is doing.  The app is supposed to http-transfer a file (40 MB in my test).  It uses 310 MB to do this, and after the class quits, the java process is till using 200 MB (as opposed to 8 before it started).

I hate java :-(

---

### Post by vague- on 2005-04-29
[QUOTE=nocturn]It uses 310 MB to do this, and after the class quits, the java process is till using 200 MB (as opposed to 8 before it started).[/QUOTE]


I cannot guarantee this, as I am not 100% sure, but I do not think that is a memory leak.  Instead, in a similar manner to other VMs such as Perl, the VM is probably keeping a large proportion of the memory previously allocated for future allocations - which saves asking the operating system for it repeatedly.  Many VMs can exhibit behaviour such as this when performing a high memory task off the bat.  Googling for a solution is probably a good idea.  Though not JVM specific (read: I have not tried them), you could try performing the memory hogging task in another process - thus, this process would close and free the memory associated with it.  I think there are solutions within the JVM itself.

Of course, I could be wrong and do just have some random straggling reference to a large chunk of the memory you parsed and so the GC will not get rid of it.

---

