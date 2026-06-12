---
title: "do while loop problem"
date: 2015-07-15
forum: Programming Talk
---

### Post by NoWeDoR on 2015-07-15
```
#include <stdio.h>


int main()
{
	int choice;
	do
	{
		printf("Enter your choice: ");
		scanf("%d", &choice);
		switch (choice)
		{
		case 1:
		{
			printf("Hello World\n\n");
			break;


		}
		case 2:
		{
			printf("Hello World2\n\n");
			break;
		}
		case 3:
		{
			printf("Hello World3\n\n");
			break;
		}
		default:
		{
			return 0;
			break;
		}
		}
	} while (choice >= 1 && choice <= 3);
	return 0;
}

```

1) Like a this program, at first, when you enter unmeaning values (like * - / + . , etc.) as choice it is stopping [as it should be]("http://tureng.com/search/as%20it%20should%20be").
2) However, at first when you enter as choice 1,2 or 3 and then enter unmeaning values (like * - / + . , etc.) it is starting to loop forever.

Although at first isn't a thing like this, Why is it happening at second?

---

### Post by Wybiral on 2015-07-15
If the scan fails, I'm pretty sure scanf won't change the value of "choice". Try setting "choice" to 0 or something before the scan otherwise it'll retain the value from a previous scan.

---

