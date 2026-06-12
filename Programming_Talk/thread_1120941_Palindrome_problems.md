---
title: "Palindrome problems"
date: 2009-04-09
forum: Programming Talk
---

### Post by Kaptainwow on 2009-04-09
Hello. I'm quite new to programming, though I've been working on and off for the past year. I am currently having issues with a program that checks to see if an input character string is a palindrome. The problem is in the strrev function, I'm just unsure of what is done wrong.

[php]
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

char* strrev(char* str, int str_length){
	char* str_rev = malloc(str_length);
	
	for (int x = 0; x != str_length; x++){
		str_rev[x] = str[(str_length + 1)- x];
	}
	
	str_rev[str_length] = '\n';
	
	return str_rev;
}


int main(){
	int length;
	char input[30];
	
	printf ("Input a word: ");
	fgets (input, 30, stdin);
	length = strlen(input)-1;
	char *reverse = strrev(input, length);
	if (strcmp(reverse, input) == 0){
		printf ("This is a palindrome!");
	}
	else {
		printf ("This is not a palindrome!");
	}
	
	return 0;
}
[/php]

---

### Post by dwhitney67 on 2009-04-09
You have lots of problems in your code.  Compile your code with the -g option, and then run it through a debugger such as gdb.  Personally, I prefer a gui for debugging, thus I rely on ddd.

On a side-note, your algorithm is very inefficient.  You should find the mid-point of the input string, then starting from the middle of the word, compare each character with its mirror.  Be wary of even-sized strings vs. odd-sized strings.

---

### Post by Arndt on 2009-04-09
> **dwhitney67 said:**
> You have lots of problems in your code.  Compile your code with the -g option, and then run it through a debugger such as gdb.  Personally, I prefer a gui for debugging, thus I rely on ddd.

On a side-note, your algorithm is very inefficient.  You should find the mid-point of the input string, then starting from the middle of the word, compare each character with its mirror.  Be wary of even-sized strings vs. odd-sized strings.

Good advice, and I'd like to add that it's useful to do a "dry run" with some suitable short string, and pretend you are the computer: do all the steps on paper yourself.

---

### Post by Therion on 2009-04-09
*Satan, oscillate my metallic sonatas!*








/I... I'm sorry for that...
//Loves palindromes so MUCH though...

---

### Post by soltanis on 2009-04-09
On a side note to the side note, an even better algorithm would be to measure the length of the string, and then iterating from each end compare each character to its mirror, meeting in the middle. Even/odd strings make no difference in this case.

Checking out K&R's reverse function will give you a good idea on how to do this --

```

/* from The C Programming Language, 2nd Ed, Kernighan & Ritchie
reverse: reverse string s in place */

void reverse(char[] s)
{
 int c, i, j;
 
 for (i = 0, j = strlen(s) - 1; i < j; i++, j--) {
  c = s[i];
  s[i] = s[j];
  s[j] = c;
 }
}

```

---

### Post by dwhitney67 on 2009-04-09
> **soltanis said:**
> On a side note to the side note, an even better algorithm would be to measure the length of the string, and then iterating from each end compare each character to its mirror, meeting in the middle. Even/odd strings make no difference in this case.
...
Yes, that works too.

However, there is no need to reverse the input string.  I do not know if you were implying that there is with the K&R code post.

---

### Post by soltanis on 2009-04-09
No, I wanted to give him example of code that iterated from either end of the string that he could adapt for his palindrome problem, without giving away the answer and preventing him from actually learning anything.

---

### Post by Kaptainwow on 2009-04-10
Thanks, guys. I finished it so that it actually works. But I'm open for suggestions on making it better if anyone thinks of something.



[php]
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int wtf (char* input, int length, int check){
	for (int x = 0, y = length; x <= length; x++, y--){
		if ((int)input[x] == (int)input[y]){
			return 1;
		}else{return 0;}
}return 0;}

int main(){
	int length;
	char input[30];
	
	printf ("Input a word: ");
	scanf ("%s", input);
	length = strlen(input)-1;
		
		int check = wtf (input, length, check);
		
		if (check == 1){
			printf("This is a palindrome!");
		}else{
			printf ("This is not a palindrome!");
		}
		
		return 0;
	}
[/php]

---

### Post by simeon87 on 2009-04-10
> **Kaptainwow said:**
> Thanks, guys. I finished it so that it actually works. But I'm open for suggestions on making it better if anyone thinks of something.

Well, it may work but the code could be improved:

- the function wtf should be renamed to is_palindrome to express what it actually does
- that function should be formatted without putting everything into a few lines: the positioning of brackets is quite horrible and the logical structure isn't visible right away. Compare it with the main function.. it's instantly clear which bracket closes which other bracket.. this is not the case for the palindrome checking function.

---

### Post by Arndt on 2009-04-10
> **Kaptainwow said:**
> Thanks, guys. I finished it so that it actually works. But I'm open for suggestions on making it better if anyone thinks of something.



[php]
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int wtf (char* input, int length, int check){
	for (int x = 0, y = length; x <= length; x++, y--){
		if ((int)input[x] == (int)input[y]){
			return 1;
		}else{return 0;}
}return 0;}

int main(){
	int length;
	char input[30];
	
	printf ("Input a word: ");
	scanf ("%s", input);
	length = strlen(input)-1;
		
		int check = wtf (input, length, check);
		
		if (check == 1){
			printf("This is a palindrome!");
		}else{
			printf ("This is not a palindrome!");
		}
		
		return 0;
	}
[/php]

Why is 'check' given as an argument to 'wtf'? It's not used. It looks like it's not even given a value at that point, but I don't know the details of C99 enough. Does someone know when such a call pattern could ever be useful?

Also, you don't limit the length of the input anymore, as the first version did. Entering a string longer than 30 characters will overwrite other variables.

Casting to (int) in 'wtf' serves no purpose.

---

### Post by Kaptainwow on 2009-04-10
Thanks for the pointers, guys. The wtf thing, check being passed in, and the unnecessary type casting were all left on accident because I pasted it before checking it more. So here's how it is now:

[php]
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int is_palindrome (char* input, int length){
	for (int x = 0, y = length; x <= length; x++, y--){
		if (input[x] == input[y]){
			return 1;
		}else{
			return 0;
		}
	}
	
	return 0;
}

int main(){
	int length;
	char input[30];
	
	printf ("Input a word: ");
	fgets (input, 30, stdin);
	length = strlen(input)-1;
		
	int check = is_palindrome (input, length);
		
	if (check == 1){
		printf("This is a palindrome!");
	}else{
		printf ("This is not a palindrome!");
	}
		
	return 0;
}
[/php]

---

### Post by johnl on 2009-04-10
```

int is_palindrome (char* input, int length){
    for (int x = 0, y = length; x <= length; x++, y--){
        if (input[x] == input[y]){
            return 1;
        }else{
            return 0;
        }
    }
    
    return 0;
} 

```

Think about this carefully.  For each pair of characters in the string, check if they are equal.  If they are NOT equal, the string is obviously not a palindrome, so bail.

If they are equal, you need to continue to test the rest of the characters -- the next pair might not be equal.

Additionally,  you are going through the entire string twice -- x goes from 0 to length, y goes from length to 0.  This doesn't affect the result, but it's not necessary :)

This will address the first issue:
```

int is_palindrome (char* input, int length){
    for (int x = 0, y = length; x <= length; x++, y--){
        /* if they are not equal we can bail right away */
        if (input[x] != input[y]){
            return 0;
        }
    }
    /* we made it through the for-loop: all pairs are equal */
    return 1;
} 

```

---

### Post by nvteighen on 2009-04-10
Hum... Maybe Zatanna should use this? [http://www.passfailstudios.com/index.php?id=37](http://www.passfailstudios.com/index.php?id=37)

But ok, your code doesn't work. 

1) There's a really weird design decision when you ask the string's length as argument for is_palindrome(). I'd just hold that data internal to that function, as it's only relevant for it. Just use a local variable.

2) Your loop is also wrong. Let's see: A string is held in an array that ranges **(0..length(string) - 1)** (yeah, writing in Perl :p), so you when you start checking backwards you have to start checking at length - 1, not at length. Of course, you saw you have to skip the '\n', so in this case, our starting position will be length - 2.

3) The loop's body makes no sense either: If run your code and ask for "abca", it will consider it a palindrome, because the first and last characters are the same... and the function is_palindrome() will return 1 because of that. No, you don't want to return... you can only return when you know a word is **not** a palindrome, but not earlier ;)

---

