---
title: "C programming and String Manipulation!"
date: 2010-04-03
forum: Programming Talk
---

### Post by Face_Man on 2010-04-03
Hello All,

let say i have a string 

```

   char MyString[1024];
   char Part1[1024];
   char Part2[1024];

```

and inside MyString is 

```

"blaa blaa ballblaa blaa ballblaa [COLOR="Red"](part1start)[/COLOR]  blaa ballblaa blaa ballblaa blaa ballblaa blaa ballblaa blaa ballblaa blaa ball blaa [COLOR="red"](part1end)[/COLOR] blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  [COLOR="DarkOrange"](part2start)[/COLOR] blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa [COLOR="DarkOrange"](part2end)[/COLOR] ball  blaa blaa ball  blaa blaa ball "

```

how can i copy what is between [COLOR="red"](part1start)[/COLOR] and [COLOR="Red"](part1end)[/COLOR]  to  Part1
and what is between [COLOR="DarkOrange"](part2start)[/COLOR] and [COLOR="DarkOrange"](part2end)[/COLOR]  to  Part2 ?


Any help would be much appreciated.

---

### Post by Some Penguin on 2010-04-03
Have a look at strstr() and strncpy() and remember that you can do arithmetic on pointers.

---

### Post by heikaman on 2010-04-03
also don't forget to null terminate part1 and part2

---

### Post by Face_Man on 2010-04-03
Thank you guys, Just in case if anyone was interested here how i did it

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

main(){
        char MyString[1024];
	char From[] = "(part1start)";
	char End[] = "(part1end)";
	char *pdest;
	char *pdest2;
	int  result;
	 
	strcpy(MyString,"blaa blaa ballblaa blaa ballblaa (part1start)  blaa ballblaa blaa ballblaa blaa ballblaa blaa ballblaa blaa ballblaa blaa ball blaa (part1end) blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  (part2start) blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa (part2end) ball  blaa blaa ball  blaa blaa ball ");
	
	printf(MyString);	printf("\n\n");

	pdest = strstr( MyString, From);
	pdest2 = strstr( pdest, End);
	result = (int)(pdest2 - pdest + 10);
	pdest[result]='\0';
	
	printf(pdest);
} 



Result
===============================================================================================
blaa blaa ballblaa blaa ballblaa (part1start)  blaa ballblaa blaa ballblaa blaa ballblaa blaa ballblaa blaa ballblaa blaa ball blaa (part1end) blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa ball  (part2start) blaa blaa ball  blaa blaa ball  blaa blaa ball  blaa blaa (part2end) ball  blaa blaa ball  blaa blaa ball 
 
(part1start)  blaa ballblaa blaa ballblaa blaa ballblaa blaa ballblaa blaa ballblaa blaa ball blaa (part1end)




```

---

