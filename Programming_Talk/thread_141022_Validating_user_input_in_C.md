---
title: "Validating user input in C"
date: 2006-03-07
forum: Programming Talk
---

### Post by sapo on 2006-03-07
Hi fellows, i started learning C in college but i m kind new to it..

is there some easy way to validate input in c?

I usually code python and php, and both have functions to do it, like is_numeric in php or isdigit() in python, but i dont know if C have one.

And another question is: i wrote some simple apps here and in windows at college they were using getch() but it didnt work in linux, so i read that i had to change that to getchar() but getchar() isnt waiting for user input at all, is there any other way to wait for a user to press a key before exiting the app?

Any ideas are welcome, thanx :mrgreen:

---

### Post by thumper on 2006-03-07
Try these...
```
        #include <ctype.h>

        int isalnum(int  c );  

        int isalpha(int  c );  

        int isascii(int  c );  

        int isblank(int  c );  

        int iscntrl(int  c );  

        int isdigit(int  c );  

        int isgraph(int  c );  

        int islower(int  c );  

        int isprint(int  c );  

        int ispunct(int  c );  

        int isspace(int  c );  

        int isupper(int  c );  

        int isxdigit(int  c );  

```

---

### Post by sapo on 2006-03-07
Sorry about my newbieness, but i tried to write a function to validate this crap, but it is with a weird behavior, whats wrong with this?
```

float valida_numero() {
	float numero;
	while(1) {
		numero = 0;
		scanf("%f",&numero);
		if(!isdigit(numero)) {
			printf("Valor inválido!");
		} else {
			return numero;
		}
	}
}
```

when i type a string, it just loops forever printing "Valor inválido".

I dont get this C crap omg, how i miss python :(

---

### Post by sapo on 2006-03-07
Ok guys, this thing is too complicated omg... i m glad i learned python and php and not C!

i wrote this function based on this: [http://gd.tuwien.ac.at/languages/c/programming-bbrown/c_055.htm](http://gd.tuwien.ac.at/languages/c/programming-bbrown/c_055.htm)

And it works (at least for me) any coments or suggestions are welcome, thanx :)

```
#include <stdio.h>
#include <stdlib.h>
/* Função para validar numeros */
float valida_numero(char texto[50]) {
	char ch;
	char buffer[14];
	int char_count = 0;
	float numero;
	while(1) {
		printf(texto);
		ch = getchar();
		char_count = 0;
		while((ch != '\n') && (char_count < 14)) {
			buffer[char_count++] = ch;
			ch = getchar();
		}
		numero = atoi(buffer);
		if(numero != 0) {
			return numero;
		} else {
			printf("Numero invalido!");
		}
	}
}
	
main() {
       float nota1,nota2,nota3,peso1,peso2,peso3,media;
       printf("Digite os dados a seguir:\n");
       nota1 = valida_numero("Digite a nota 1:");
       nota2 = valida_numero("Digite a nota 2:");
       nota3 = valida_numero("Digite a nota 3:");
       peso1 = valida_numero("Digite o peso 1:");
       peso2 = valida_numero("Digite o peso 2:");
       peso3 = valida_numero("Digite o peso 3:");
       media = ((nota1*peso1) + (nota2 * peso2) + (nota3*peso3)) / (peso1 + peso2 + peso3);
       printf("A média final é: %.2f",media);
       getchar();
}

```

---

### Post by rplantz on 2006-03-08
[QUOTE=sapo]Ok guys, this thing is too complicated omg... i m glad i learned python and php and not C![/QUOTE]

Yeah, there is a lot to know before you can use C effectively.

I'm not sure what you wish to do, but you have to treat integers and floats differently in C. It does not take care of things for you.

I like to use strtol for integers and strtod for floats. You can read a character string from the user with scanf, then convert it to an integer with strtol. For example, try the following program:
```

#include <stdio.h>
#include <stdlib.h>
int main() {
  char buffer[200];
  int aNumber;
  char *not_integer;

  printf("Enter an integer: ");
  scanf("%s", buffer);
  aNumber = strtol(buffer, &not_integer, 10 );
  if (*not_integer != '\0') {
    fprintf(stderr, "%s is not valid.\n", not_integer);
    exit(1);
  }
  printf("You entered %i\n", aNumber);
  exit(0);
}

```
Test it with 123, then with 123abc.

Read the man page for strtol and see if you can relate it to what I've done here. I taught computer science at a university for over 20 years. From my experience with teaching C (and several other languages), I predict that your biggest problem here will be with the use of pointers in the &not_integer syntax. Everyone, including myself, has to think quite a bit about how pointers work before they get it.

I'm retired now, and one of the things I want to learn is python. Although I can put a C or C++ program together with ease, I really struggle to get scripts to work. Always something new to learn!

---

### Post by sapo on 2006-03-08
thanx, i m coding a lot of python latelly, making even gui apps with pygtk, and its great, simple, fast and very very easy to learn.

I started coding with pascal (but i hated that), then dedicated some time with clipper (loved this one and coded a lot with it), then i started with php.. now i m kinda tired of php and doing just python code.

I started in computer science this year, and i mot *that* interested in C, but i think its a good language to learn, at least i m not gonna learn pascal there hehe.

But about this pointers stuff.. i dont really understand how this thing works, i ll try reading about it.

thanx a lot :)

---

### Post by rplantz on 2006-03-08
[QUOTE=sapo]But about this pointers stuff.. i dont really understand how this thing works, i ll try reading about it.
[/QUOTE]

The statement ```

  char *not_integer;

```
allocates a place in memory called "not_integer" where you can store an address of (location of) where a character is stored in memory. That is, you can store a pointer to a character.

When the strtol (string to long) function is converting a string of characters to an integer, if it comes across a non-numerical character, it stops the conversion and provides you with the address of the offending character.

In order for you to receive that address, you need to tell strtol where to store it. The second argument to strtol, &not_integer, is the address of the place where you want strtol to put the address it found. The "&" is C's address-of operator.

It's really an organization issue. I had something delivered to my house a few weeks ago. I told them where to put it. It's the same thing here. You want something from strtol if it finds an error, so you tell strtol where to put it. In this case, strtol will send you an address of the first non-numeric character it finds.

Draw some diagrams. Use boxes for the memory locations and fill them in with the data. Number each box and think of that number as its address. For example, in my program you might have 200 boxes for buffer that are numbered 0 - 199. Then aNumber could be box number 200 and not_integer could be box number 201. The second argument in the call to strtol is 201. (You can probably get the idea without drawing all 200 boxes for buffer. :) )

---

### Post by sapo on 2006-03-08
Thanx, i think i understood.

This allocate stuff is something new to me, cause i have always coded in higher level languages, such as php and python, so they do it for me :p

But thanx a lot for the explanation :mrgreen:

---

