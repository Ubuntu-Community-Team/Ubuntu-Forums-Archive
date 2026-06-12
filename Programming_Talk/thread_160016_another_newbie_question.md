---
title: "another newbie question"
date: 2006-04-14
forum: Programming Talk
---

### Post by mwanafunzi on 2006-04-14
Hi all,
    There is a question that I have been given to do ( not an assignment), that I am having problems with. Here is the question

Write a function function which is passed a string and a character and returns the postion of the character in the string.

here is what I have so far

```

#include <iostream>
void findChar(char passedString[], char passedChar[])
{	
	int counter = 1, position = 0;
	char check;
	for (counter; counter < strlen(passedString);counter++)
	{
		check = passedString[counter];
		if (check == passedChar[0])
			position = counter;
	}
	std::cout << "the position of the character is: " << position << std::endl;	
}

int main()
{	
	char myString[14], ourChar[1];
	std::cout << "please enter the string you want checked: ";
	std::cin.getline(myString,40);
	std::cout << strlen(myString) << std::endl;
	std::cout << "please enter the character you want the position of: ";
	std::cin.getline(ourChar, 0);
	std::cout << strlen(ourChar) << std::endl;

	findChar(myString, ourChar);	
	return 0;
}
```

lets say that I want enter the word 'jamming' 
and I want the position of the character 'g'

I get back 0 as the position number.

I tried this (below) and it seems to work fine. Why is there a difference

```

#include <iostream>
void findChar(char passedString[], char passedChar[])
{	
	int counter = 1, position;
	char check;
	for (counter; counter < strlen(passedString);counter++)
	{
		check = passedString[counter];
		if (check == passedChar[0])
			position = counter;
	}
	std::cout << "the position of the character is: " << position << std::endl;	
}

int main()
{	
	char myString[] = "jamming", ourChar[] = "g";
	findChar(myString, ourChar);	
	return 0;
}
```

cheers

---

### Post by gerbman on 2006-04-14
Your call to cin.getline(ourChar,0) in the first segment of code is reading zero characters into ourChar...so there is nothing in the array that is passed to findChar. You initially set position to zero within findChar, and this is not changed because no characters in passedString match anything in ourChar, which contains nothing (or maybe just uninitialized data). There are many ways to fix this :-)

---

### Post by mwanafunzi on 2006-04-14
i originally had (ourChar,1), but that did not work as intended either... the character number position of the character that I am getting , when using "jamming" as the string, is 10 .

---

### Post by gerbman on 2006-04-14
The return value of cin.getline includes the terminating null character, so maybe it's only reading the null. What happens when you use something bigger than 1? Make sure ourChar is the same size or bigger, too.

---

### Post by mwanafunzi on 2006-04-14
thanks for the help with that, it is working fine. I have another question though in regards to having "two strings".. When I input the "two strings" and I ask to check the s. I get back a count of 10 as the position of the letter. My question is. Why does the space between the strings get ignored? 
cheers

---

### Post by gerbman on 2006-04-14
[QUOTE=mwanafunzi]thanks for the help with that, it is working fine. I have another question though in regards to having "two strings".. When I input the "two strings" and I ask to check the s. I get back a count of 10 as the position of the letter. My question is. Why does the space between the strings get ignored? 
cheers[/QUOTE]It reads in the entire line of input, including the space. In the for-loop that checks for the character, you aren't quitting the loop after finding the first instance of the character being looked for. It'll end up returning the last one it finds. Also, make sure you start 'counter' at zero. G'luck...programming rules!! :-)

---

### Post by mwanafunzi on 2006-04-14
thanks for the help.

---

