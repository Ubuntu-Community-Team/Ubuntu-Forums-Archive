---
title: "Very noob C question"
date: 2007-03-30
forum: Programming Talk
---

### Post by TreeFinger on 2007-03-30
Hello, everyone. I am just beginning to dabble in C if any of you have read my other posts. Right now I am following [this tutorial]("http://www.faqs.org/docs/learnc/x562.html") and I have to say I like it a lot. Right now I am learning about If statements and while statements.

I am trying to write a program that asks the user to guess my age and when it is incorrect have it ask the user again until the number is guessed correctly. But the program is a little screwed up and I can really not figure out why. I'll post my code and also the output now.

```

#include <stdio.h>

int
main()
 {
 const int age = 21;
 int guess;

 printf("Try to guess my age\n");
 printf("I am no older then 30 and no younger than 3\n");

 printf("Enter your guess: ");
 scanf("%d", &guess);

 while (guess != age);
	{
		printf("enter your guess: ");
		scanf("%d", &guess);
		printf("You are incorrect, please try again!\n");
	}

 printf("Correct! I am 21 years old.\n");
 
 return 0;
 }

```

Output:

```

treefingers@treefingers-desk:~$ ./agegame
Try to guess my age
I am no older then 30 and no younger than 3
Enter your guess: 21
enter your guess: 21
You are incorrect, please try again!
Correct! I am 21 years old.
treefingers@treefingers-desk:~$ ./agegame
Try to guess my age
I am no older then 30 and no younger than 3
Enter your guess: 21
enter your guess: 21
You are incorrect, please try again!
Correct! I am 21 years old.
treefingers@treefingers-desk:~$ ./agegame
Try to guess my age
I am no older then 30 and no younger than 3
Enter your guess: 21
enter your guess: 2
You are incorrect, please try again!
Correct! I am 21 years old.

```

---

### Post by spin2cool on 2007-03-30
Step through the program slowly and think about what is going on at each step.  Right now, the incorrect line executes whether they input the correct age or not.  You need to wrap the incorrect printf in an if statement.

I hope I just didn't do someone's homework for them...

---

### Post by j_g on 2007-03-30
The problem is the semi-colon at the end of the statement:

```

while (guess != age);

```

What is happening is that you've now got an empty clause if the statement happens to be true. And the { and } (following the while statement) merely serve to bracket some instructions. They no longer serve as the instructions executed if the test is true.

It's tantamount to this:

```

while (guess != age)
{
}

{
   printf("enter your guess: ");
   scanf("%d", &guess);
   printf("You are incorrect, please try again!\n");
}

```

Remove that semi-colon at the end of the while statement, and it will do what you expect.

---

### Post by Wybiral on 2007-03-30
At first glance I would say it's because you're printing the "you are incorrect" statement right after they enter something.

The while loop wont check for the condition until the instruction pointer returns the the "while" keyword.

Try moving your input command AFTER the "you are incorrect" message.

Also, you don't have to use the first input command, just set guess to something other then your age, actually "guess = !age" would work.

EDIT:

Wow, seems like everyone answered at once!

---

### Post by j_g on 2007-03-30
> I would say it's because you're printing the "you are incorrect" statement right after they enter something.

No, it has to do with the semi-colon at the end of the while statement. It's a common error among new C programmers.

---

### Post by Wybiral on 2007-03-30
> **j_g said:**
> No, it has to do with the semi-colon at the end of the while statement. It's a common error among new C programmers.

It is a common error. But that's not the only error... The problem in his output seems to be that he's expecting the while loop to exit as soon as the condition is false. And it's printing the "you are incorrect" message even in the event of a correct input.

---

### Post by j_g on 2007-03-30
Um. The "while loop" won't even be entered if the condition is not initially true, which it won't be if the first attempt at an age guess is correct.

He should print out the "You are incorrect" message before he attempts to get a "second guess", because that would better sync with the user's entry, but other than some "visual quirkiness", that has absolutely no bearing upon the logic of his code. The loop will end when the correct age is input (ie, "as soon as the condition is false'), and the final message will indicate a correct guess.

Your analysis of his "error" is incorrect, as is your interpretation of the logic of his code. I repeat. His problem is the semi-colon at the end of the while statement. Case closed.

---

### Post by TreeFinger on 2007-03-30
> **spin2cool said:**
> Step through the program slowly and think about what is going on at each step.  Right now, the incorrect line executes whether they input the correct age or not.  You need to wrap the incorrect printf in an if statement.

I hope I just didn't do someone's homework for them...

No, this is not homework assigned to me from a teacher. I am just learning C on my own.

Thank you guys for all the replies but I still can't figure it out.

I changed my code to this:
```

#include <stdio.h>

int
main()
 {
 const int age = 21;
 int guess;

 printf("Try to guess my age.\n");
 printf("I am no older then 30 and no younger than 3.\n");
 printf("Enter your guess now: ");
 scanf("%d", &guess);

 while (guess != age);
	printf("Enter you guess: ");
	scanf("%d", &guess);

 printf("Correct! I am 21 years old.\n");
 
 return 0;
 }

```

I still get the same output. I did some experimenting and if i type in the correct guess first it asks again for a guess. For this 2nd instance even if I do not type the correct age it will work.

So for some reason the program feels it needs to run the while statement just once even if the first answer is correct. I am not sure why though..

---

### Post by po0f on 2007-03-30
TreeFinger,

Change:

```
while (guess != age);
	printf("Enter you guess: ");
	scanf("%d", &guess);
```

to:

```
while (guess != age) **{**
	printf("Enter you guess: ");
	scanf("%d", &guess);
**}**
```

Maybe you should put all of the IO in a do-while, instead.

---

### Post by j_g on 2007-03-30
You've still got that semi-colon at the end of your while statement. Why are you putting it there? If you can answer that question, then I'm sure you'll find your mistake.

Try this, and then do a comparison to your original code to see your error:

```

#include <stdio.h>

int
main()
{
  const int age = 21;
  int guess;

  printf("Try to guess my age\n");
  printf("I am no older then 30 and no younger than 3\n");

  printf("Enter your guess: ");
  scanf("%d", &guess);

  while (guess != age)   /* <==== Look, ma! No semi-colon */
  {
    printf("You are incorrect, please try again!\n");
    printf("enter your guess: ");
    scanf("%d", &guess);
  }

  printf("Correct! I am 21 years old.\n");
  return 0;
}
```

---

### Post by Wybiral on 2007-03-30
> **j_g said:**
> Um. The "while loop" won't even be entered if the condition is not initially true, which it won't be if the first attempt at an age guess is correct.

He should print out the "You are incorrect" message before he attempts to get a "second guess", because that would better sync with the user's entry, but other than some "visual quirkiness", that has absolutely no bearing upon the logic of his code. The loop will end when the correct age is input (ie, "as soon as the condition is false'), and the final message will indicate a correct guess.

Your analysis of his "error" is incorrect, as is your interpretation of the logic of his code. I repeat. His problem is the semi-colon at the end of the while statement. Case closed.

Simmer down j_g... We've been through this.

Like I said, there are two errors. To quote myself "But that's not the _only_ error"

You're such a defensive guy... You need to chill out man.

I know that the semi colon will cause errors too (a big one in the case that the first value entered is wrong) but I was trying to point out another error. So just chill.

I'm not interpreting the logic of his code wrong, there were two problem with what he wanted to happen and what was going to happen.

Stop drinking coffee or something...

---

### Post by TreeFinger on 2007-03-30
OK, I got it now. I am not sure why but the tutorial I am following includes a ';' after the while statement.

```

while (guessed_number != MAGIC_NUMBER);
    {
      printf("enter your guess: ");
      scanf("%d", &guessed_number);
    }

```

I changed mine to the way you guys suggested and it works now.

```

#include <stdio.h>

int
main()
 {
 const int age = 21;
 int guess;

 printf("Try to guess my age.\n");
 printf("I am no older then 30 and no younger than 3.\n");
 printf("Enter your guess now: ");
 scanf("%d", &guess);

 while (guess != age) {
	printf("Incorrect! Try again: ");
	scanf("%d", &guess);
}

 printf("Correct! I am 21 years old.\n");
 
 return 0;
 }

```

Thank you all very much for wasting your time on me :p

So do I never include a semi-colon in a while statement? Is this the same for If and else statements also?

---

### Post by WW on 2007-03-30
The code in the tutorial for which you gave the link has two errors. First, as you have discovered, it has a semi-colon at the end of the line with the "while" statement.  Second, there is a missing semi-colon at the end of the last "printf" statement.

I looked at a few other examples in that tutorial, and it didn't take long to find another mistake.  The code in "Example 6-1" in Section 6.3 declares
```
float hourly_wage[4] = {2, 4.9, 10, 123.456};
```
It defines a variable called index, assigns index=4, and then refers to hourly_wage[index].  This is not correct. hourly_wage should only be indexed with integers 0, 1, 2, or 3.

I suggest finding a better tutorial.

Edit: It gets worse.  The example in Section 6.8 is just loaded with mistakes. The author says "When compiled and executed this will display...", but there is no way he actually compiled that example.

---

### Post by tho on 2007-03-30
> **TreeFinger said:**
> OK, I got it now. I am not sure why but the tutorial I am following includes a ';' after the while statement.

```

while (guessed_number != MAGIC_NUMBER);
    {
      printf("enter your guess: ");
      scanf("%d", &guessed_number);
    }

```

I changed mine to the way you guys suggested and it works now.

```

#include <stdio.h>

int
main()
 {
 const int age = 21;
 int guess;

 printf("Try to guess my age.\n");
 printf("I am no older then 30 and no younger than 3.\n");
 printf("Enter your guess now: ");
 scanf("%d", &guess);

 while (guess != age) {
	printf("Incorrect! Try again: ");
	scanf("%d", &guess);
}

 printf("Correct! I am 21 years old.\n");
 
 return 0;
 }

```

Thank you all very much for wasting your time on me :p

So do I never include a semi-colon in a while statement? Is this the same for If and else statements also?

To remove one of the unnecessary calls to scanf, you could do something like:
```

#include <stdio.h>

int main(int argc, char *argv[])
{
	int age, guess;
	age = 20;
	
	while(scanf("%d", &guess)) {
		if (guess != age) {
			printf("Wrong!\n");
		} else break;
	}
	printf("Correct!\n");
	return 0;
}

```

---

