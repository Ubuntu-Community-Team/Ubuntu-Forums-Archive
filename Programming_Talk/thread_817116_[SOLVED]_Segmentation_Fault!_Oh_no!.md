---
title: "[SOLVED] Segmentation Fault! Oh no!"
date: 2008-06-03
forum: Programming Talk
---

### Post by spadewarrior on 2008-06-03
Could one of you fine people please look at this function I've written and show me where the segmentation fault is? I've been staring at it for about 30 minutes and cannot work it out. It's driving me mad. i'm sure it's obvious but I've been working on this so long I must be going blind.

Help appreciated.


[PHP]int	get_money(void)
{
	int total, coin;
	system("clear");
	mvprintw(12, 22, "Please enter money. ");
	mvprintw(13, 22, "Only 5p, 10, 20p, 50p or 100p accepted. ");
	mvprintw(14, 22 ,"Enter 0 to finish	");
	refresh();
	
	while(coin!=0) 
	{	
		fflush(stdin);
		scanf("%d", coin);
		if(	(coin==5) || (coin==10) || (coin==20) || (coin==50) || (coin==100)	)
			{
			total=(total+coin);
			}
		else 
			{
			mvprintw(16, 22, "Invalid coin	");
			refresh();
			}
			
	} 
	
	return total;
}[/PHP]

---

### Post by Wybiral on 2008-06-03
scanf("%d", coin);

---

### Post by AZzKikR on 2008-06-03
Try

```
scanf("%d", &coin);
```

---

### Post by spadewarrior on 2008-06-03
Of course! 

Boy do I feel ashamed....

Thanks.

---

### Post by AZzKikR on 2008-06-03
It helps if you compile using the flag **-Wall**, which generates all warnings (assuming you use GCC). If I tried to compile it, it would output:

```

make all 
mkdir -p ./bin
g++ -Wall -O2 -c ./src/main.cpp -o ./bin/main.o
./src/main.cpp: In function `int get_money()':
./src/main.cpp:10: warning: format argument is not a pointer (arg 2)
./src/main.cpp:8: warning: 'coin' might be used uninitialized in this function
./src/main.cpp:8: warning: 'total' might be used uninitialized in this function
g++  -o ./bin/langton ./bin/langton.o ./bin/main.o

```

Helpful information :)

---

### Post by spadewarrior on 2008-06-03
Didn't know about that. Thanks!

---

### Post by nvteighen on 2008-06-03
**gcc -Wall** is the C programmer's best friend! :)

Don't forget to mark this thread as solved, using the "Thread Tools" above.

---

### Post by pmasiar on 2008-06-03
and don't forget to thank the person, who instead of giving you a fish, shown you how to fish by yourself.

That gcc -Wall trick should go to FAQ, if not there, IMHO.

---

