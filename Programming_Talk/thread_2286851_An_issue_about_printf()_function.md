---
title: "An issue about printf() function"
date: 2015-07-15
forum: Programming Talk
---

### Post by NoWeDoR on 2015-07-15
```

#include <stdio.h>

int main()
{
	char name[64];
	char surname[64];

	printf("Enter any name: ");
	fgets(name, sizeof(name), stdin);
	printf("\nName: s\n", name);   // There is no problem here it shows me correctly what I entered as name

	printf("Enter s's surname: ", name);
	fgets(surname, sizeof(surname), stdin);   // However, if you run this line you'll see the cursor is jumping following line as picture. How can I correct this? I want to it shows me """ Enter ....'s name: """ 
	printf("\nSurname: %s\n", surname);

	return 0;
}
```

Screen output:
[http://www.megafileupload.com/8ZcJ/Untitled.jpg](http://www.megafileupload.com/8ZcJ/Untitled.jpg)

---

### Post by Wybiral on 2015-07-15
fgets also catches the newline character from the user hitting enter: [http://stackoverflow.com/questions/2693776/removing-trailing-newline-character-from-fgets-input](http://stackoverflow.com/questions/2693776/removing-trailing-newline-character-from-fgets-input)

---

