---
title: "Getting keyboard input in C"
date: 2009-11-24
forum: Programming Talk
---

### Post by Jim_in_Germany on 2009-11-24
Hi,

In my C program, the user should choose between two options (a or b).
Therefore I create a loop and ask the user to input a letter. If he/she inputs "a" the loop ends and the program does one thing, if he/she inputs "b" then the loop ends and the program does another thing. Any input apart from "a" or "b" should result in a message being displayed along the lines of "Please enter 'a' or 'b'" and the loop should be repeated.

Here was my first attempt:
```
main() {
  char opt;
  printf("Please choose a or b");
  while(1){
    scanf("%c",&opt);
    if (opt == 'a' || opt == 'b'){
      break;
    } else {
      printf("Please enter either 'a' or 'b'");
    }
  }
  ...rest of program...
}
```
However this is where the problems started. If the user for example entered "abcde" then "abcde\n" would be in the input buffer and "Please enter either 'a' or 'b'" would be printed out six times.

I half solved the problem by adding this line:
```
printf("Please enter either 'a' or 'b'");
while((opt=getchar())!='\n' && opt !=EOF);
``` which meant that the input buffer was cleared after the first message was displayed. The only exception was if the user simply pressed return.

Then I replaced that with```
printf("Please enter either 'a' or 'b'");
__fpurge(stdin);
``` 

Which works perfectly, but appears to be Linux specific.

I have read in other forums that this is "bad style" and if one did things properly from the start then one wouldn't have to deal with the problem of disgarding input.
It was also suggested that a combination of fgets to read a line and sscanf to parse it, would be a good idea.

Could somebody give me a clue as to how one might do this.
Is flushing the input buffer bad style?
How might one go about doing what I described above in a proper manner?

Thanks for your time and help.

---

### Post by LKjell on 2009-11-24
What I would have done is to use fgets or getline to read a line then compare the length of the line.

---

### Post by MindSz on 2009-11-24
Aye, I would use either getline() or gets() and if the size is 1 look at the character int the input buffer.

---

### Post by Jim_in_Germany on 2009-11-24
Cheers for that.
I'll try that out tomorrow (have to turn in soon) and let you know how I get on.

---

### Post by apmcd47 on 2009-11-24
> **LKjell said:**
> What I would have done is to use fgets or getline to read a line then compare the length of the line.

And another for this approach. scanf is a very tricky utility which can catch even the most experienced C programmers out. In my experience you should always read the line using, eg, fgets, then parse the line, possibly using the sscanf variant.

Andrew

---

### Post by Jim_in_Germany on 2009-11-25
Hi,
I've been trying to implement what you suggested and came up with the following.

```
#include <stdio.h>
#include <string.h>

int main(void) {
  char formatted_string[10];
  char input_string[10];
  printf("Please choose a or b");
  while(1){
    fgets(input_string, sizeof(input_string), stdin);
    sscanf(input_string, "%s", (char*)&formatted_string);
    if (strlen(formatted_string)==1){
      if (formatted_string[0] == 'a' || formatted_string[0] == 'b'){
        break;
      }else {
	printf("Please enter either 'a' or 'b'");
      } 
    }else {
      printf("Please enter either 'a' or 'b'");
    }
  }
  rest of my wonderful programme ...
}
```It kind of works, in so far as if a user enters nonsensical input up to 8 characters in length, the message "Please enter either 'a' or 'b'", is only outputted once.
However, if the user enters nonsensical input of over 9 characters, the message is displayed twice.

Firstly, please tell me if I am on the right track with what I am doing?

Secondly, presuming I am, how could I ensure that the error message is not printed out more than once if the user enters very long nonsensical input?

Thanks in advance.

---

### Post by dwhitney67 on 2009-11-25
Consider the following...
```

#include <string.h>
#include <stdbool.h>
#include <stdio.h>

char getInput();

int main()
{
   char entry = getInput();

   // use 'entry'...

   return 0;
}

char getInput()
{
   char line[10] = {0};

   while (true)
   {
      printf("Enter 'a' or 'b': ");
      fgets(line, sizeof(line), stdin);

      // remove newline character (this is optional; if not done, then line will be 2-chars in size)
      char* nl = strchr(line, '\n');
      if (nl) *nl = '\0';

      if (strlen(line) == 1 && (line[0] == 'a' || line[0] == 'b'))
      {
         break;
      }
      else
      {
         printf("Bad input; try again...\n\n");
      }
   }

   return line[0];
}

```

---

### Post by Jim_in_Germany on 2009-11-25
Hi,

Thanks for the quick reply.

Your code is definitely better than what I wrote and once I work through it, I am sure I will learn a lot.
However, upon first inspection it still suffers from the same flaw: namely entering "123456789012345678901234567890" will make the error message "Bad input ..." be printed three times.

As I mentioned before "__fpurge(stdin);" works perfectly, but in every forum I was in, I was told that clearing stdin is bad style.

To be fair, if the user is asked to enter a single character, and they end up entering thirty characters, then they shouldn't complain at seeing a few too many error messages :)

Nonetheless, it would still be interesting to find out the "correct" way to do this. I have already learnt a lot, just by starting this thread and the subsequent research.

Thanks in advance

---

### Post by dwhitney67 on 2009-11-25
> **Jim_in_Germany said:**
> ...
However, upon first inspection it still suffers from the same flaw: namely entering "123456789012345678901234567890" will make the error message "Bad input ..." be printed three times.

Try this for getInput():
```

char getInput()
{
   char line[10] = {0};

   while (true)
   {
      printf("Enter 'a' or 'b': ");
      fgets(line, sizeof(line), stdin);

      if (strlen(line) == 2 && (line[0] == 'a' || line[0] == 'b'))
      {
         break;
      }
      else
      {
         printf("Bad input; try again...\n\n");

         const size_t pos = sizeof(line) - 1; 
         if (strlen(line) == pos && line[pos] != '\n') while (fgetc(stdin) != '\n');
      }
   }

   return line[0];
}

```

---

### Post by Jim_in_Germany on 2009-11-25
Hi,

That works just fine!
Thanks very much indeed for your time and help.
I will work through the code (still a C beginner unfortunately) to understand what you have done. If I have any questions I will post back here.
Thanks too for the other replies.

---

### Post by dwhitney67 on 2009-11-25
Here's a simpler solution:
```

char getInput()
{
   char input = 0;

   while (1)
   {
      printf("Enter 'a' or 'b': ");
      input = fgetc(stdin);

      if (fgetc(stdin) == '\n')
      {
         break;
      }
      else
      {
         printf("Bad input; try again...\n\n");
         while (fgetc(stdin) != '\n');
      }
   }

   return input;
}

```

---

### Post by MindSz on 2009-11-25
> **Jim_in_Germany said:**
> 
```

    fgets(input_string, sizeof(input_string), stdin);
    sscanf(input_string, "%s", (char*)&formatted_string);

```It kind of works, in so far as if a user enters nonsensical input up to 8 characters in length, the message "Please enter either 'a' or 'b'", is only outputted once.
However, if the user enters nonsensical input of over 9 characters, the message is displayed twice.

Firstly, please tell me if I am on the right track with what I am doing?

Secondly, presuming I am, how could I ensure that the error message is not printed out more than once if the user enters very long nonsensical input?

Thanks in advance.

I think it's because you call fgets using the size of your string (9 bytes) so it reads 8 charactesr plus the NULL character. If the data in the input buffer is greater than that, then the remainder will be caught in the next iteration of the loop ... hmmm, yeah I think that might be it.

If I don't make sense please say so ...I just got back from lunch and I need a crucial nap.

---

### Post by lisati on 2009-11-25
> **dwhitney67 said:**
> Here's a simpler solution:


Minor quibble here.

I'm not comfortable with "while (1)", and wish to respectfully suggest something like "while ((input!='a') && (input!='b'))" instead for the OP's program. 

Don't worry about it too much, however, as long as the OP is able to get a functioning program.

:)

---

### Post by Jim_in_Germany on 2009-11-25
> **MindSz said:**
> I think it's because you call fgets using the size of your string (9 bytes) so it reads 8 charactesr plus the NULL character. If the data in the input buffer is greater than that, then the remainder will be caught in the next iteration of the loop

Hi,
As far as I can tell that's exactly what's happening and that's exactly what I am trying to avoid.
I've just been looking at the solution proposed by dwhitney67 and although there is a fair amount of black magic going on there :), from what I can make out the lines
> const size_t pos = sizeof(line) - 1; 
if (strlen(line) == pos && line[pos] != '\n') while (fgetc(stdin) != '\n');
are actually also clearing the input buffer.

Is there any way to avoid doing this, or am I simply mistaken as to what is going on?

P.S. Have a nice nap.

Edit: labelled this thread as unsolved again as it seems I will still have some questions.

---

### Post by MindSz on 2009-11-25
It might not be good practice, but since fgets stops at the number of bytes received OR at the '\n' and EOF characters, I just use fgets with 100 bytes as input (or more if you think it's appropriate). The only problem there would be that if you don't get either the '\n' or the EOF character then you would be in trouble ... namely, your program will be stuck waiting to fill the 100 bytes you need for input.

---

### Post by LKjell on 2009-11-25
I just took what you guys made and wrote it a different way.
It does not really matter whether you work with the string or the char.
They should behave the same.

```
#define _GNU_SOURCE
#include <stdbool.h>
#include <stdio.h>
#include <stdlib.h>

char *getInput()
{
	char *str = NULL;
	size_t len = 0;
	ssize_t read;
	
	while (true)
	{
		printf("Enter 'a' or 'b': ");
		read = getline(&str, &len, stdin);

		if (read == 2 && (str[0] == 'a' || str[0] == 'b'))
			break;
	      	else if(read == -1)
	      	{
	      		printf("\n");
	      		free(str);
	      		exit(EXIT_FAILURE);
	      	}
	}
	
	return str;
}

int main()
{
	char *str = getInput();
	char entry = str[0];
	
	printf("You pressed: %s", str);
	printf("And you pressed: %c\n", entry);
	
	free(str);
	return EXIT_SUCCESS;
}
```

---

### Post by LKjell on 2009-11-25
> **dwhitney67 said:**
> Here's a simpler solution:
```

char getInput()
{
   char input = 0;

   while (1)
   {
      printf("Enter 'a' or 'b': ");
      input = fgetc(stdin);

      if (fgetc(stdin) == '\n')
      {
         break;
      }
      else
      {
         printf("Bad input; try again...\n\n");
         while (fgetc(stdin) != '\n');
      }
   }

   return input;
}

```
I cannot see that you check whether the input is 'a' or 'b' here

---

### Post by dwhitney67 on 2009-11-25
> **LKjell said:**
> I cannot see that you check whether the input is 'a' or 'b' here

And I cannot believe I posted an incredibly wrong/incomplete solution.  You're right; apparently I did forget some logic in there.

How's this?:
```

char getInput()
{
   char input = 0;

   while (1)
   {
      printf("Enter 'a' or 'b': ");
      input = fgetc(stdin);

      if ((input == 'a' || input == 'b') && fgetc(stdin) == '\n')
      {
         break;
      }
      else
      {
         printf("Bad input; try again...\n\n");
         while (fgetc(stdin) != '\n');
      }
   }

   return input;
}

```

P.S.  @ the OP:  getline() is not portable; it is a GNU-extension.

---

### Post by Jim_in_Germany on 2009-11-26
Hi,
I've worked through the proposed solutions and in doing so learnt a lot, so thanks to everyone that answered.

It seems to me now that the options are:

a) clear the input buffer in some way, using e.g.
> const size_t pos = sizeof(line) - 1; 
if (strlen(line) == pos && line[pos] != '\n') while (fgetc(stdin) != '\n');

b) use "getline" which although appearing to do everything I want, i.e by setting str as a NULL pointer, and declaring len as 0, allow the user to input a string of any length, is gcc specific.

Is this correct?
Is it such bad style to clear the input buffer?

Thanks in advance.

---

### Post by LKjell on 2009-11-26
Just stick with the stuff which feels more natural. Test on various machines with different setting to see if stuff just work. Another thing is to encapsulate much of your code so you do not have to rewrite for simple thing as input from stdin.

---

### Post by Tony Flury on 2009-11-26
The other way of doing it would be to keep track using a flag that you have generated an error message, and supress the error if the user enters the wrong input again. Just remember to reset the flag when you get valid data.

The code is left to the reader - but that is the way i would have removed multiple error messages.

---

### Post by LKjell on 2009-11-26
> **Tony Flury said:**
> The other way of doing it would be to keep track using a flag that you have generated an error message, and supress the error if the user enters the wrong input again. Just remember to reset the flag when you get valid data.

The code is left to the reader - but that is the way i would have removed multiple error messages.

Good idea. But the thing is that fgets read a block of characters into the buffer. Then the next time you call it you do not know whether it reads from the stream buffer or from a new line. That is why the OP wants to clean the buffer first. In fact you can actually write:
```
char getInput()
{
   char input = 0;

   while (1)
   {
      printf("Enter 'a' or 'b': ");
      input = fgetc(stdin);

      if ((input == 'a' || input == 'b') && fgetc(stdin) == '\n')
      {
         break;
      }
      else
      {
         printf("Bad input; try again...\n\n");
         //while (fgetc(stdin) != '\n');
      }
   }

   return input;
}
```

---

