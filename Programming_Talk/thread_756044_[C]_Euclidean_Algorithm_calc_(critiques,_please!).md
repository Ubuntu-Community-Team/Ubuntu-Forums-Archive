---
title: "[C] Euclidean Algorithm calc (critiques, please!)"
date: 2008-04-15
forum: Programming Talk
---

### Post by nvteighen on 2008-04-15
Hi there!

I've now written a **very** simple Euclidean Algorithm calc in C (of course not using the Math Library's gcd()!!) and would like to know if there's something to correct, improve or whatever... Surely the use of buffers can be changed to something more efficient; for some reason, I feel I'm still working as I did in BASIC.

Hopefully I can "upgrade" this to an Extended Euclidean Algorithm calc soon!

(Ehmm.. yes, I gave up with the RSA program I wanted to code. I must go step-by-step and learn the basics first!)

Thanks!

[PHP]
/*Euclidean Algorithm implementation in C*/

#include <stdio.h>
#include <stdlib.h>

void Recursion(int *Num1, int *Num2)
{
	int buf = *Num2;

	*Num2 = *Num1 % *Num2;
	*Num1 = buf;
}

void Initiate(int *Num1, int *Num2)
{
	if(*Num1 < *Num2)
	{
		int buf = *Num1;
		*Num1 = *Num2;
		*Num2 = buf;
	}

	if(*Num2 == 0)
	{
		printf("Error! Division by zero detected!\n");
		exit(2);
	}
}

int main(int argc, char **argv)
{
	if(argc != 3)
	{
		printf("Usage: %s [Integer 1] [Integer 2]\n", argv[0]);
		exit(1);
	}

	int Num1 = atoi(argv[1]);
	int Num2 = atoi(argv[2]);

	Initiate(&Num1, &Num2);

	while(Num2 != 0)
		Recursion(&Num1, &Num2);

	printf("GCD is %d\n", Num1);

	return 0;
}
[/PHP]

---

