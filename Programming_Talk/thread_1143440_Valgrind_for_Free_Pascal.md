---
title: "Valgrind for Free Pascal?"
date: 2009-04-29
forum: Programming Talk
---

### Post by jlund3 on 2009-04-29
I have used valgrind in my c++ projects and have found it a fairly useful tool. However, I have recently started tinkering a bit in Free Pascal. I tried using valgrind on the pascal code (though not expecting too much) and it detects no memory errors. Is there some way I can configure valgrind to work with Free Pascal? If not, is there a similar tool for Free Pascal?

---

### Post by blingo on 2009-04-30
Perhaps there isn't a memory leak?

Valgrind works with a binary regardless of the language the code was written before it was compiled.

I'm not familiar with Free Pascal, but can you deliberately  create a memory leak there?

---

### Post by jlund3 on 2009-04-30
> **blingo said:**
> Perhaps there isn't a memory leak?

Valgrind works with a binary regardless of the language the code was written before it was compiled.

I'm not familiar with Free Pascal, but can you deliberately  create a memory leak there?

program Leak;

{$mode objfpc}{$H+}

var
  Obj1: TObject;

begin
	Obj1 := TObject.Create();
	Obj1 := TObject.Create();
	Obj1.Destroy();
end.

That program should have does the equivalent of malloc twice but only does the equivalent of free once. Valgrind says that all heap blocks are freed and that there were no malloc/free at all!

---

### Post by blingo on 2009-05-18
Yes there is a tool for Free Pascal

[http://www.montefiore.ulg.ac.be/~latour/doc/pascal_fpc/html/prog/progsu114.html](http://www.montefiore.ulg.ac.be/~latour/doc/pascal_fpc/html/prog/progsu114.html)

Edit: note that by using this, a summary will be sent to standard output, so you may want to use this only in the debugging version of the program.

To my understanding, memory allocation in Free Pascal is usually buffered by some mechanism that does the actual allocation from the Operationg System.

I assume this mechanism is the one that also frees memory.
 
This kind of buffering, can probably not be seen by Valgrind, as to the outside world, all memory management seems good (if the mechanism works well)

See [http://www.freepascal.org/docs-html/prog/progsu157.html#x209-2150008.4.2](http://www.freepascal.org/docs-html/prog/progsu157.html#x209-2150008.4.2)
for details.

---

