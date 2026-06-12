---
title: "Strange behaviour of a character in a structure while printing"
date: 2007-12-27
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2007-12-27
Hello, I have a strange problem or the problem is very obvious and I can't see it :) I'm kind of a new C programmer so the chance of the latter is more :)

Anyway, I have a structure like this:

```
#define EN_COK_HECE 40

struct kel
{
    char kelime[EN_COK_HECE];
    char sesliHarfler[EN_COK_HECE];
    int sesliHarfKonumlari[EN_COK_HECE];
};
```

And on my program I use a code like this:

```
printf("%i ", (kelime->sesliHarfler)[2]);
printf("%i ", (kelime->sesliHarfler)[2]);
```

Yes, same line 2 times. But the strange thing is that they print a different output. The output is like "97 -112". And when I add the same line several times more it does not change (97 -112 -112 -112 -112...). So just the first statement changes the value of the character. But I just do printing, I don't do any assignments, so I cannot understand where the problem is.

I used %i for debugging. When I use %c then I get different characters like:

a Ê Ê Ê Ê Ê

First one is what it should be but I don't know why it changes into Ê nor continues that way instead of keeping to change everytime I use that statement.

I am using Windows platform with MinGW system. And the code above is plain C.

---

### Post by bmbernie on 2007-12-27
From your code snippet it looks like you are attempting to print the values in your arrays without first zeroing out the structure.  You should zero out the array first to ensure there are no garbage values in your data structure.  Without this first step you are going to be getting unpredictable results. 

You can use something like the following

```
memset(&kelime, 0, sizeof(kel));
```

---

### Post by ZuLuuuuuu on 2007-12-27
Hi,

But I print always the same character (which I initialised before as 'a'). If I would try to print the second, third, fourth etc. characters then the case you say could be the problem.

---

### Post by Compyx on 2007-12-28
Post your code, we can't help you based on the snippets you've provided. We need to see how 'kelime' is declared, how it's initialized and in what context it's used.

Copy and paste the code, don't retype.

---

### Post by Sporkman on 2007-12-28
You're printing a char as an int, try explicitly casting the variable as int.

---

### Post by ZuLuuuuuu on 2007-12-28
> **Compyx said:**
> Post your code, we can't help you based on the snippets you've provided. We need to see how 'kelime' is declared, how it's initialized and in what context it's used.

Copy and paste the code, don't retype.

Let me tell you that

"kelime" means "word"
"yeni" means "new"
"isaretci" means "pointer"
"sesli harfler" means "vowels"
and finally
"konum" means "place"

in Turkish so that you can maybe understand the code easier and faster. What I do is to create a "word" structure and keep in it the word itself, the vowels in it and the places of the vowels in it.

This is where I create the new "kelime".

```
kel *yeniKelime(char *kelime)
{
	kel yeniKelime, *isaretciYeniKelime;
	
	isaretciYeniKelime = &yeniKelime;
	
	strcpy(yeniKelime.kelime, kelime);
	yeniKelime.sesliHarfler[0] = '\0';
	yeniKelime.sesliHarfKonumlari[0] = -1;
	
	sesliHarfleriVeKonumlariniBul(isaretciYeniKelime);
	
	return isaretciYeniKelime;
}

```

sesliHarfleriVeKonumlariniBul() is a function to find the vowels and write the information to the structure. This is how I call the above function in the main program:

```
	ornekKelime = yeniKelime("Canol");
```

This is the code which does the initialisation:

```
void sesliHarfleriVeKonumlariniBul(kel *kelime)
{
	int i = 0, j = 0;
	
	for (i = 0; i < strlen(kelime->kelime); i++)
		if (Seslidir((kelime->kelime)[i]))
		{
			(kelime->sesliHarfler)[j] = (kelime->kelime)[i];
			(kelime->sesliHarfler)[j + 1] = '\0';
			(kelime->sesliHarfKonumlari)[j] = i;
			j++;
		}
}
```

Seslidir() controls if the letter is vowel or not. By the way I should tell you that I have this function in my "main" function and it works (it lists the vowels successfuly):

```
for (i = 0; i < strlen(ornekKelime->sesliHarfler); i++)
{
	if (i > 0)
		printf(", ");
	printf("%c", ornekKelime->sesliHarfler[i]);
}
```


> **Sporkman said:**
> You're printing a char as an int, try explicitly casting the variable as int.

I tried both printing chars and ints, nothing changed. But I also tried what you say by doing:

```
printf("%i ", (int)(kelime->sesliHarfler)[0]);
printf("%i ", (int)(kelime->sesliHarfler)[0]);
```

And unfortunately, nothing changed :( Thanks for your efforts...

---

### Post by dwhitney67 on 2007-12-28
> **ZuLuuuuuu said:**
> 

```
kel *yeniKelime(char *kelime)
{
	kel yeniKelime, *isaretciYeniKelime;
	
	isaretciYeniKelime = &yeniKelime;
	
       ...
	
	return isaretciYeniKelime;
}

```


If I guess wrong on this forgive me, however I think the problem you are having is that you are returning the pointer (address) of a local variable which is destroyed upon leaving the scope of the yeniKelime() function.  You may want to either consider declaring a kel structure that can be passed into the function, or alternatively, allocate a new kel structure after entering the function.

---

### Post by ZuLuuuuuu on 2007-12-28
> **dwhitney67 said:**
> If I guess wrong on this forgive me, however I think the problem you are having is that you are returning the pointer (address) of a local variable which is destroyed upon leaving the scope of the yeniKelime() function.  You may want to either consider declaring a kel structure that can be passed into the function, or alternatively, allocate a new kel structure after entering the function.

Yes, that exactly was the problem! Thank you very much... I rewrote that part of the code with using malloc() and now it seems working. However I am not used to use malloc. Is the code below a right usage of malloc()?

```
kel *yeniKelime(char *kelime)
{
	kel *yeniKelime;
	
	yeniKelime = malloc(sizeof(kel));
	
	strcpy(yeniKelime->kelime, kelime);
	yeniKelime->sesliHarfler[0] = '\0';
	yeniKelime->sesliHarfKonumlari[0] = -1;
	
	sesliHarfleriVeKonumlariniBul(yeniKelime);
	
	return yeniKelime;
}
```

I guess it is not necessary for "ornekKelime" because it is in main() function anyway but if I use this yeniKelime() function for local purposes, then I should call free() to give that memory back to system right?

---

### Post by dwhitney67 on 2007-12-29
Your usage of malloc() is correct.  And yes, eventually, as good practice, you should free() the memory allocated.  Allocated memory that has not been deallocated can be considered a "memory leak" in the application.

Here's a simple example using malloc() and free():
```

#include <stdlib.h>

struct Foo
{
  int val;
};


int main()
{
  struct Foo *f = malloc( sizeof(struct Foo) );

  // ...

  free( f );
  return 0;
}
```

P.S.  For security reasons, the following statement in your code should be replaced with a **strncpy()**:
```
strcpy(yeniKelime->kelime, kelime);
```

For more information on strncpy(), run this command:  man strncpy

---

### Post by anbumanij on 2007-12-29
Hi goody,

          If you use same object it will try to print the same value.. because the default value is being there in the memory.. try with


printf("%i ", (kelime->sesliHarfler)[1]);
printf("%i ", (kelime->sesliHarfler)[2]);

---

