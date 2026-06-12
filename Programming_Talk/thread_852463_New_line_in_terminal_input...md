---
title: "New line in terminal input.."
date: 2008-07-07
forum: Programming Talk
---

### Post by nethan_lor on 2008-07-07
Hi, I want to know if there is any ctrl something to make a new line in console input for a C project ?

I mean I want to write something like :
1 2 3
4 5 6
and then send it with enter instead of
1 2 3 4 5 6 and then enter...

Is there anyway to do that ??

Thanks a lot !

---

### Post by gnusci on 2008-07-07
simply but works!

[PHP]#include <stdio.h>

int main(void){
	
	char line[1024];
	
	printf("Enter your numbers?\n");
	read(0, line, 1024 );
	printf("numbers:%s",line);
	read(0, line, 1024 );
	printf("numbers:%s",line);
	read(0, line, 1024 );
	printf("numbers:%s",line);
	
   return 0;
}[/PHP]

---

