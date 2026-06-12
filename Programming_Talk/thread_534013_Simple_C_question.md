---
title: "Simple C question"
date: 2007-08-24
forum: Programming Talk
---

### Post by band-aid on 2007-08-24
I'm just about finished reading Sams teach yourself C in 24 hours and decided to see if I could write a simple program bring together everything that I've learned. My goal was to have a program that displayed a menu, took the users choice (either set a rectangles dimensions or draw a rectangle), and carried it out. Here is what I have, it does not compile complaining about my pointer being undeclared in a function.

```


#include <stdio.h>
#include <stdlib.h>

int domenu();
void setrect(int height, int width);
void getrect();

struct rectangle{
	int height;
	int width;
};

int main(){
	struct rectangle * rectptr = malloc(sizeof(struct rectangle));
	if(rectptr == NULL){
		printf("failed to allocate memory... somehow.\n");
		return 1;
	}
	while(1){
		int choice;
		int height = 0;
		int width = 0;
		choice = domenu();
		switch(choice){
			case 1:		
				printf("Height then witdth");
				scanf("%d", &height);
				scanf("%d", &width);
				setrect(height, width);
				continue;
			case 2:
				getrect();
				continue;
			default: 
				printf("Thats not a choice.\n");
				continue;
		}
	}
return 0;
}

int domenu(){
	int choice;
	printf("1. Set the rectangles dimensions.\n");
	printf("2. Print the rectangle.\n");
	return choice;
}

void setrect(int height, int width){
	(rectptr.height) = height;
	(rectptr.width) = width;			/* I may need
							to derefrence these*/
}
void getrect(){
	for(int i = 0; i < rectptr.height; i++){
		for(int n = 0; n < rectptr.witdh; n++){
			printf("#");
		}
		printf("\n");
	}
}


```

Here is the output from GCC

```


rectangle.c: In function ‘setrect’:
rectangle.c:50: error: ‘rectptr’ undeclared (first use in this function)
rectangle.c:50: error: (Each undeclared identifier is reported only once
rectangle.c:50: error: for each function it appears in.)
rectangle.c: In function ‘getrect’:
rectangle.c:55: error: ‘rectptr’ undeclared (first use in this function)


```

'm sure its something simple, but I'm still getting my head wrapped around pointers and their uses so I suspect I've made a novice error. Thanks for your help.

---

### Post by visik7 on 2007-08-24
rectptr is never defined

---

### Post by Wybiral on 2007-08-24
Read about "function scope".

Unless it's passed to the function or declared global, you cannot access it in that function.

---

### Post by aks44 on 2007-08-24
band-aid, you're kidding, right?

If you're not... I suggest you to read a book... or at least your compiler errors...

---

### Post by bjarneh on 2007-08-24
a couple of tips, never write a complete program then try to compile, that will never work.

start off with empty functions and fill in parts at a time, then you will understand what causes the problem, in this case:

struct rectangle * rectptr = malloc(sizeof(struct rectangle));


should be

rectangle* rectptr = malloc(sizeof(rectangle));

to allocate a struct of type rectangle and naming the pointer for rectptr, as i expect you want.


and C cannot be learned in 24 hours no matter what the book says :-) 
i've only written a few things in C, and none of them complex, but i sure used more than 24 hours :-)


you also use the pointer inside the functions setrect and getrect, but it has no knowledge of this pointer, its not GLOBAL, it's only defined within the scope of main, so it has to be passed to the functions, or defined globally

---

### Post by band-aid on 2007-08-24
Ok I got it worked out. I knew it was something simple that I had screwed up on. Thanks for the help, and aks44 theres no need in being condescending. People come to these forums to learn not listen to snide remarks.

---

### Post by Wybiral on 2007-08-24
> **bjarneh said:**
> 
struct rectangle * rectptr = malloc(sizeof(struct rectangle));

should be

rectangle* rectptr = malloc(sizeof(rectangle));


Actually, in C, using "struct rectangle" is proper. Otherwise you have to declare the structure using "typedef".

C++ on the other hand doesn't require a "typedef" but instead treats "struct" as a "class" (it even allows for methods).

---

### Post by slavik on 2007-08-24
> **Wybiral said:**
> Actually, in C, using "struct rectangle" is proper. Otherwise you have to declare the structure using "typedef".

C++ on the other hand doesn't require a "typedef" but instead treats "struct" as a "class" (it even allows for methods).

the only difference between a class and a struct in C++ is that in a class, stuff not declared in a public/protected/private block are private (in struct, they are public).

Stroustroup only changed structs and later decided to add "class" because he didn't want to break backwards compatability with C's structs (where everything is public, but he wanted stuff to be private by default.)

EDIT: and what Wybiral said, in C:

struct foo {};

there is no such thing as "foo", only "struct foo". C++ typedefs any structs/classes to the tag name. :)

---

