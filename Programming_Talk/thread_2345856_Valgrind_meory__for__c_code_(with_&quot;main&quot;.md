---
title: "Valgrind meory  for  c code (with &quot;main&quot;)  which calls another c project as library"
date: 2016-12-08
forum: Programming Talk
---

### Post by mghorba on 2016-12-08
Can valgrind be used to find the memory leaks in a function called as a  library by another function? 


I have a "main" that calls another c project as a library. I am running  valgrind for the executable of the "main", and valgrind finds memory  issues in the "main" body. But it does not indicate about the separate c  project which is called as a library. I intentionally placed a malloc in  the called project and did not free and Valgrrind did not find it in the  report. 
Are there any commands that would give me the capability to run a  project as library and find memory leaks with valgrind?

I have tried "valgrind --leak-check=full --track-origins=yes" and "valgrind --leak-check=yes" commands and it only finds the memory leaks in the "main" and not the c functions called by the "main" as library.

---

### Post by Rocket2DMn on 2016-12-09
Valgrind should find memory leaks in the library.  If it's a static library, you would of course need to rebuild your binary to link in the updated library with the intentional malloc without a corresponding free.
If you still have problems, you may just need to verify that the malloc is being called and actually returns successfully.

---

