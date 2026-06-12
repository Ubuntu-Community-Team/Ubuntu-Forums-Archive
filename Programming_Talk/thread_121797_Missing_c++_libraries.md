---
title: "Missing c++ libraries"
date: 2006-01-26
forum: Programming Talk
---

### Post by dallypost on 2006-01-26
I have a c++ program that I have compiled successfully under Warty and Horey. I recently upgraded to Breezy and installed c++ via synaptic.

Here is a sample of the code. Please not that my compile command is commented at line 1.

//compile with g++ cutter.c -g -O2 -o cutter

#include <stdio.h>
//#include <unistd.h> /* for gcc compiler */
#include <sys/io.h> /* for g++ compiler */
//#include <sys/perm.h> //same functionality as sys/io.h and unistd.h
#include <asm/io.h>

#include <iostream>
#include <time.h>
#include <math.h>
#include <cstdlib>
#include <ctime>

using namespace std;

int main()
{	 
	//#include "variables.c"
	//#include "port_up.c"
	//#include "port_down.c"
	

	if(liability_release!="yes" and liability_release!="YES"){
		//#include "header.c"	
		//#include "liability_release.c"
	}	
	while(liability_release=="yes" or liability_release=="YES"){		
		srand((unsigned)time(0)); 
		menu="";
		//#include "header.c"	
		//#include "main_menu.c"
		if(enable_show or enable_training){	
			//#include "run_menu.c"
		}	
		//#include "actions_menu.c"				
		//#include "actions.c"
	}
}

These are the errors:

lance@john:~/my/cutter/cutter_dev$ gcc cutter.c -g -O2 -o cutter
cutter.c:3:19: error: stdio.h: No such file or directory
cutter.c:5:43: error: sys/io.h: No such file or directory
cutter.c:7:20: error: asm/io.h: No such file or directory
cutter.c:9:20: error: iostream: No such file or directory
cutter.c:10:18: error: time.h: No such file or directory
cutter.c:11:18: error: math.h: No such file or directory
cutter.c:12:19: error: cstdlib: No such file or directory
cutter.c:13:17: error: ctime: No such file or directory

Under Warty and Horey, these libraries were installed with c++ compiler. How do I install the now?

Thanks,

Lance

---

### Post by amohanty on 2006-01-26
I think you might need to install the libc6-dev package.

HTH
AM

---

### Post by bartbes on 2006-01-26
Well I really don't know but when I tried to compile I got this:
```
#warning "You should include <sys/io.h>. This time I will do it for you."
cutter.c: In function ‘int main()’:
cutter.c:24: fout: ‘liability_release’ was not declared in this scope
cutter.c:28: fout: ‘liability_release’ was not declared in this scope
cutter.c:30: fout: ‘menu’ was not declared in this scope
cutter.c:33: fout: ‘enable_show’ was not declared in this scope
cutter.c:33: fout: ‘enable_training’ was not declared in this scope

```
Is this the whole program? I got no errors of missing headers.. maybe I already downloaded them.. (I have downloaded a lot of c/c++ headers in the short time using ubuntu). Try the above post I would say

---

### Post by amohanty on 2006-01-26
I think he provided pseudo code :) because if this is real code... its wrong in so many ways that I cant even begin.

AM

---

