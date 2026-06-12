---
title: "ANSI C Lists"
date: 2009-12-05
forum: Programming Talk
---

### Post by masterof14 on 2009-12-05
Hey I'm practicing ANSI C lists, I'm trying to store on an ordered list strings, though I'm getting an error: incompatible types in assignment on line 62 from the "listas.c" here is my code 

listas.c:
```

#include "lista.h"
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

lista * cria_lista()
{
    lista * novo;
    novo = (lista *) malloc(sizeof(lista));
    if(novo == NULL)
    {
        exit(-1);
    }
    novo->seg = NULL;
    return novo;
}

int lista_vazia(lista * base)
{
    if(base->seg == NULL)
    {
        return 1;
    }
    else
    {
        return 0;
    }
}
void mostra_lista(lista * base)
{
    lista * aux;
    aux = base-> seg;
    while(aux != NULL)
    {
        printf(" %s ", aux->nome);
        aux = aux-> seg;
    }
}
void insere_int(lista * base, char nome[1024])
{
    lista * aux;
    lista * seguinte;
    lista * novo;
    aux = base;
    seguinte = aux->seg;
    if(procura_int(base, nome) != NULL)
    {
        printf("valor ja inserido\n");
    }
    else
    {
        while(seguinte != NULL && strcmp(nome, seguinte->nome) > 0)
        {
            aux = aux->seg;
            seguinte = seguinte->seg;
        }
        novo = (lista*)malloc(sizeof(lista));
        if(novo == NULL)
        {
            exit(-1);
        }
        novo->nome = nome;  /*MY ERROR!!!!!*/
        novo->seg = seguinte;
        aux->seg = novo;
    }
}
void remove_int(lista * base, char nome[1024])
{
    lista *anterior;
    lista * aux;
    anterior = base;
    aux = anterior->seg;
    while(aux != NULL && strcmp(aux->nome, nome) != 0)
    {
        anterior = anterior->seg;
        aux = aux->seg;
    }
    if(aux != NULL)
    {
        anterior->seg = aux->seg;
        free(aux);
        printf("removeu com sucesso\n");
    }
    else
    {
        printf("nao removeu\n");
    }
}
char *procura_int(lista * base, char nome[1024])
{
    lista * aux;
    aux = base->seg;
    while(aux != NULL && strcmp(aux->nome, nome) < 0) /*Uma vez que se trata de uma lista ordenada não faz sentido continuar a procurar se já ultrapassou o nome pretendido*/
    {
        aux = aux->seg;
    }
    return aux->nome;
}
```

listas.h:

```
#ifndef LISTA_H
#define LISTA_H

typedef struct lista_st{
    char nome[1024];
    struct lista_st * seg;
}lista;


lista * cria_lista();
void insere_int(lista * base, char nome[1024]);
void remove_int(lista * base, char nome[1024]);
int lista_vazia(lista * base);
void mostra_lista(lista * base);
char *procura_int (lista * base, char nome[1024]);
```

#endif

and on the main.c file i use these:

```
while(fgets(linha, 1024, stdin) != NULL)
            {
                if(sscanf(linha, "%s", nome) == 1)
                {
                    insere_int(lista_int, nome);
                }
            }
```

in order to get my string.

Any clue? Thanks

---

### Post by MadCow108 on 2009-12-05
please format your code in [code] tags

your code is wrong.
you need to use strcpy to copy strings into the list.
strncpy(novo->nome, nome, 1024);

the error itself is related to the difference between pointers and arrays.
unlike pointers you can't assign values to arrays, only to the contents of the array.

---

### Post by masterof14 on 2009-12-05
Thanks for the help! By the way why can't I do it with pointers? I mean I did the same thing (same code) with integer and it worked perfectly!

---

### Post by MadCow108 on 2009-12-05
your list buffer is no pointer its an array.
you can't assign values to arrays.

---

### Post by masterof14 on 2009-12-05
Ok it worked! Thanks!

---

### Post by MadCow108 on 2009-12-05
some additional clarification as this is often a problem:

arrays and pointers are only equivalent not equal.
An array implicitly converts to a pointer in many cases, e.g. when using the [] operator or, like in this case, when being past into a function.

thus a function parameter is always an pointer and no array.
a function: f(char test[]) is interpreted by the compiler as: f(char * test)
This is the reason for the error message:
conversion from char* to char[]
even though your function definition uses the array syntax. (I find this syntax possibility a quite confusing part of the standard)

this is also the reason the sizeof operator is so dangerous:
int ar[10]
sizeof(ar) //= 10*sizeof(int)
is correct, as ar is still an array

int ar[10]
f(ar)

in f:
sizeof(ar) //= sizeof(int*)
because the array converted to pointer which has a different size (4-8 bytes mostly)

---

### Post by LKjell on 2009-12-05
Interesting code even I do not understand the language you wrote.

I therefore wrote something similar but using pointer in the structure.

```
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

struct list
{
    char *str;
    struct list *next;
};

struct list *read()
{
	struct list *root = malloc(sizeof(struct list));
	struct list *current = root;
	struct list *old = root;
	struct list *pre = root;
	
	char *str = malloc(1024*sizeof(char));
	 
	while(fgets(str, 1024, stdin) != NULL)
	{
		current->str = str;
		
		current = malloc(sizeof(struct list));
		old->next = current;
		pre = old;
		old = current;
		
		str = malloc(1024*sizeof(char));
	}
	free(str);
	pre->next = NULL;
	
	if(pre != current)
		free(current);
	else
	{
		free(root);
		exit(EXIT_SUCCESS);
	}

	return root;
}

void print(struct list *str)
{
	struct list *node = str;
	
	while(node != NULL)
	{
		printf("%s", node->str);
		node = node->next;	
	}	
}

void sfree(struct list *str)
{
	assert(str != NULL);
	struct list *current = str;
	struct list *next = current->next;

	while(current != NULL)
	{
		free(current->str);
		free(current);
		current = next;
		if(current != NULL)
			next = current->next;
	}
}

int main()
{
	struct list *str = read();
	print(str);
	sfree(str);
	exit(EXIT_SUCCESS);
}
```

---

### Post by Arndt on 2009-12-05
This has nothing to do with your problem, but note that exit(-1) in practice means the same as exit(255). If you do mean exit(255), it's better to write that, but it's more usual to use exit(1) or exit(2).

---

### Post by masterof14 on 2009-12-05
MadCow108, I really appreciate your concern! Very good explanation! It works perfectly now!

---

