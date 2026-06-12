---
title: "c void prototype and function"
date: 2012-05-11
forum: Programming Talk
---

### Post by Grenage on 2012-05-11
I'm dabbling with C, and am a little flustered over the use of a void function.  Let's say I have a basic menu, and depending on which option is selected, a function is called:

```
#include <stdio.h>

void networkfail(void);

int main() {

	int menuselection;

	printf("\n\nYadda Yadda:\n\n");
	printf("1) Option 1.\n");
	printf("2) Option 2.\n");
	printf("3)\n");
	printf("4)\n");
	printf("5) Quit.\n\n");
	scanf("%d", &menuselection);

	switch (menuselection) {
		case 1:
			networkfail();
			break;
		case 2:
			break;
		case 3:
			break;
		case 4:
			break;
		case 5:
			break;
		default:
			printf("That wasn't an option.");
			break;
	}

	void networkfail() {
		printf("Shame.");
	}
	return 0;
}
```

The compilation error is:
```
undefined reference to `networkfail'
```

What I don't understand, is why.  As far as I am aware, the prototype is valid, and no parameters are required for the function.  If I include 'void' in the function call, I'm informed that I have supplied too many parameters.

---

### Post by r-senior on 2012-05-11
You are creating a nested function (a function inside a function), which is not standard C.

Did you have a reason for doing so? Or did you mean to do this:

```
#include <stdio.h>

[COLOR="Red"]void networkfail();[/COLOR]

int main() {
	int menuselection;

	printf("\n\nYadda Yadda:\n\n");
	printf("1) Option 1.\n");
	printf("2) Option 2.\n");
	printf("3)\n");
	printf("4)\n");
	printf("5) Quit.\n\n");
	scanf("%d", &menuselection);

	switch (menuselection) {
		case 1:
			networkfail();
			break;
		case 2:
			break;
		case 3:
			break;
		case 4:
			break;
		case 5:
			break;
		default:
			printf("That wasn't an option.");
			break;
	}
[COLOR="Red"]        networkfail();[/COLOR]
	return 0;
}

[COLOR="Red"]void networkfail() {
	printf("Shame.");
}[/COLOR]


```

---

### Post by Grenage on 2012-05-11
Oh God, I knew it would end up being a stupid mistake; thank you for the correction.

---

### Post by trent.josephsen on 2012-05-11
> **r-senior said:**
> You are creating a nested function (a function inside a function), which is not standard C.

Your analysis is correct, but I'm puzzled by the fact that you removed "void" from the parentheses of the function declaration, making it not a function prototype and preventing the compiler from catching the error if the function is later mistakenly called with arguments. void networkfail(void); was better.

---

### Post by r-senior on 2012-05-11
No puzzle, just a mistake on my part. The declarations would be better with void.

---

