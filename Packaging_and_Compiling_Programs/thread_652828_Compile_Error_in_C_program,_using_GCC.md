---
title: "Compile Error in C program, using GCC"
date: 2007-12-29
forum: Packaging and Compiling Programs
---

### Post by Chinfrim on 2007-12-29
Okay, so I have this project to deliver for college, and I'm stumbling across a very stupid matter.

Supposedly, we have to write a program, with two modes of functioning,

so, when you type ./pos -s it will deliver the program of the supervisor of an enterprise,

and when you type ./pos -c it will deliver the customer interface,

if you just type ./pos, it's going to be like man, and tells you which modes exist, 

and the last case, ./pos (anything else) it gives an error and returns -1

Okay,

so I did the argc/argv, thing, but it will be better just to print the code here:

```
int main(int argc, char *argv[])
{

	
	if(argc == 1) /* Se o programa foi iniciado somente como ./pos, a função devolve as opções existentes */
	{
		printf("Bem vindo ao Programa Point of Sale (POS)\n");
		printf("Para entrar no modo de Supervisor, digite pos -s\n");
		printf("Para entrar no modo Caixa, digite pos -c\n");
		return 0;
	}
	else
	{
		if(argc == 2 && (!strcmp(argv[1],"-s"))){ /* ./pos -s -> Supervisor */
		{
			printf("Bem vindo ao Modo Supervisor!\n");
		} 
		if(argc == 2 && (!strcmp(argv[1],"-c"))){ /* ./pos -c -> Caixa */
		{
			printf("Bem vindo ao Modo Caixa!\n");
		}
	}
	return 0;
}
```

and the compiler delives these errors:

"main.c: In function &#8216;main&#8217;:
main.c:40: error: expected declaration or statement at end of input
main.c:40: error: expected declaration or statement at end of input
"
Where the 40th line, is the one after return 0;, and it only the closing bracket }

Note, don't mind the portuguese!

The error only seems to appear when this I write this part:

```
if(argc == 2 && (argv[1] == "-s"))
```

or even 

```
if(argc == 2 && (!strcmp(argv[1],"-s")))
```

What is missing!!

---

### Post by Vixis on 2007-12-29
remove two [COLOR="Red"] **{**[/COLOR]

```
int main(int argc, char *argv[])
{

	
	if(argc == 1) /* Se o programa foi iniciado somente como ./pos, a função devolve as opções existentes */
	{
		printf("Bem vindo ao Programa Point of Sale (POS)\n");
		printf("Para entrar no modo de Supervisor, digite pos -s\n");
		printf("Para entrar no modo Caixa, digite pos -c\n");
		return 0;
	}
	else
	{
		if(argc == 2 && (!strcmp(argv[1],"-s")))[COLOR="Red"]**{**[/COLOR] /* ./pos -s -> Supervisor */
		{
			printf("Bem vindo ao Modo Supervisor!\n");
		} 
		if(argc == 2 && (!strcmp(argv[1],"-c")))[COLOR="Red"]**{**[/COLOR] /* ./pos -c -> Caixa */
		{
			printf("Bem vindo ao Modo Caixa!\n");
		}
	}
	return 0;
}
```

---

### Post by OVERMiND on 2007-12-29
> if(argc == 2 && (!strcmp(argv[1],"-s")))**[COLOR="Red"]{[/COLOR]** /* ./pos -s -> Supervisor */
		{
			printf("Bem vindo ao Modo Supervisor!\n");
		} 

I guess you have doubled the "{" after the "if" statement in both cases ..

---

### Post by Chinfrim on 2007-12-29
Ok thanks!

Now, I'm thinking of having the main() function separate from the function that is going to call for the interface menu.

that is, I have the main.c file, and the interface.c, all I have to do is #include "interface.h" and create a interface.h with the function prototypes??

And, how I call for that function in the separate program? just like I would for any other?

---

