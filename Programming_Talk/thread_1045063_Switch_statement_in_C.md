---
title: "Switch statement in C"
date: 2009-01-20
forum: Programming Talk
---

### Post by sboard1019 on 2009-01-20
Hey everyone, I have spent the last couple hours plowing through google trying to figure this out. The default for my switch statement is supposed to just print a message, however it prints the message twice. 

```
    printf("\nEnter Selection: ");

        do{
	    nav = getchar();
		switch(nav){
			case 'w':
				weekly(); //=> open weekly.c
				i=1;
				break;
			case 's':
				shopping(); //=> open shopping.c
				i=1;
				break;
			case 'p':
				pantry(); // open pantry.c
				i=1;
				break;
			case 'r':
				book(); // => open book.c
				i=1;
				break;
			case 'q':
				break;
			default:
				printf("Not an option -- Correct options are w, s, p, r and q. Try again:");			
				break;
		}
	} while(nav != 'q');
```

my output looks like:

```
Enter Selection: z
Not an option -- Correct options are w, s, p and r. Try again:
Not an option -- Correct options are w, s, p and r. Try again:

```

Any help would be very much appreciated! Thanks in advance!

---

### Post by muntasir_120 on 2009-01-20
As you type 'z' and hit enter, your program actally gets 2 chars: 'z' and '\n'.

---

### Post by sboard1019 on 2009-01-20
Ah, so it does. hahaha I should have caught that. Thank you very much!

---

