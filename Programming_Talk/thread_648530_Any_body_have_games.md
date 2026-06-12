---
title: "Any body have games?"
date: 2007-12-23
forum: Programming Talk
---

### Post by kool_kat_os on 2007-12-23
Hi, has anybody made a C++ or C text game? If so can you post it's code on this thread?

---

### Post by samjh on 2007-12-24
Here's a *very* simple game written in the past 10 minutes.  I'll leave it to you to figure out how it works!

The language is C.

Save it to a file called guess.c then compile it using **gcc -o guess guess.c** and run it by typing **./guess**

I'd also recommend trying hangman style games as well.  Battleship style games can also be fun to write and can help teach you a lot about programming.

```
#include <stdlib.h>
#include <time.h>
#include <stdio.h>

int main(void)
{
	int choice, counter, guessed, target;

	choice = 0;
        counter = 1;
	guessed = 0;

	srand(time(NULL));
	target = rand() % 10 + 1;
	
	printf("The number guessing game!\n");
	printf("Can you guess the random number between 0 and 10?\n");

	while (!guessed) {
		printf("Guess %d: ", counter);
		scanf("%d", &choice);
		if (choice < target) {
			printf("Your guess is too low!\n");
		} else {
			if (choice > target) {
				printf("Your guess is too high!\n");
			} else {
				guessed = 1;
				printf("You got it! :)\n");
			}
		}
                counter++;
	}

	return 0;
}
```

---

### Post by Majorix on 2007-12-24
I was working on a Py game based on a TV show, but since the show is copyrighted I won't post the code. And it is not C/C++ as you requested.

Do you have any good ideas that could be converted to a C game?

---

### Post by kool_kat_os on 2007-12-24
samjh, the game you wrote, when you guess the right number the programs exit automatically.

---

### Post by Wybiral on 2007-12-24


Ah, the infamous number guessing game! This is probably one of the best projects for new programmers to learn the basics of loops/conditions/operators!

---

### Post by mike_g on 2007-12-24
> samjh, the game you wrote, when you guess the right number the programs exit automatically.

here:
> while (!guessed)
This loops until guessed is not equal to zero.

here is where guessed is set to non-zero:
> 				guessed = 1;
				printf("You got it! :)\n");


If you don't see "You got it!", Thats probably because there nothing ( like a getchar()) causing a pause when the program is about to end. If you run the program from the command line you should see the  string.

---

### Post by revanthedarth on 2007-12-24
But text-based programming isn't like programming graphical games. 

I have made a RPG with C++, if i find its source, I'll post it here. I also have made a HotDog Tycoon, but it was far too unbalanced and i didn't try to fix it. I chose the way to do more bugs, adding a rival :D But if i find its source, i'll post it too. But those games were written with so little knowledge of programming, so every work is done sooo unwisely that i might be ashamed to send it :D

---

### Post by samjh on 2007-12-24
> **kool_kat_os said:**
> samjh, the game you wrote, when you guess the right number the programs exit automatically.

You have to run it from terminal to see the "You got it! :)" output.

---

### Post by LaRoza on 2007-12-24
> **Wybiral said:**
> Ah, the infamous number guessing game! This is probably one of the best projects for new programmers to learn the basics of loops/conditions/operators!

It isn't a number guess game in reality, the quickest way to solve it is a mental binary search and it takes any fun out of it.

---

### Post by mike_g on 2007-12-24
Well tbh I don't think there was much fun in it to begin with, but its a good place to start for someone new to coding.

---

### Post by LaRoza on 2007-12-24
> **mike_g said:**
> Well tbh I don't think there was much fun in it to begin with, but its a good start for someone new to coding.

It is good to start with, I didn't mean to imply that it wasn't.

It can lead to more fun games, as most games require some randomness.

---

### Post by califman831 on 2007-12-24
A linux version of Dominos and Checkers would be great

---

