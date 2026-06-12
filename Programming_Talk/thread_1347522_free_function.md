---
title: "free function"
date: 2009-12-06
forum: Programming Talk
---

### Post by masterof14 on 2009-12-06
Hey! I'm using a stack to store a coordinate structure but when I want to remove and use the free function it doesn't free the stack entry, instant it puts the x coordinate to 0 and the y maintains its value these is my function code;

```
pilha *remove_coord(pilha * topo){
    pilha * aux;
    if(pilha_vazia(topo)!= 0)
    {
        printf("pilha vazia\n");
    }
    else
    {
        aux = topo;
        topo = (*topo).seg;
        free(aux);
    }
    return topo;
} 
```

Any clue? Thanks

---

### Post by MadCow108 on 2009-12-06
free does not necessarily change anything in the memory, it just allows that the memory block can be reused for other allocations. It may only be overwritten when another allocation uses this freed memory

if you want to check for a memory leak use the valgrind tool

I suspect from your previous posts that pilla is a singly linked list.
in this case your delete currupts the list as the previous element points to an invalid memory block after the delete

deletes in singly linked lists can only delete the next element not the current

---

### Post by LKjell on 2009-12-06
free only frees dynamic (heap) memory. Your use of free is something different.

---

### Post by Arndt on 2009-12-06
> **masterof14 said:**
> Hey! I'm using a stack to store a coordinate structure but when I want to remove and use the free function it doesn't free the stack entry, instant it puts the x coordinate to 0 and the y maintains its value these is my function code;

```
pilha *remove_coord(pilha * topo){
    pilha * aux;
    if(pilha_vazia(topo)!= 0)
    {
        printf("pilha vazia\n");
    }
    else
    {
        aux = topo;
        topo = (*topo).seg;
        free(aux);
    }
    return topo;
} 
```

Any clue? Thanks

Are these x and y things fields inside a "pilha"? What's the definition of pilha?

There's too little information here to say anything. This is a function which seems to be used for taking a pointer to an element in a linked list, free the element and return the rest of the list. As such, it looks OK.

How do you see in your program that something is wrong?

(A more usual way to write (*topo).seg is topo->seg, but that doesn't change what the function does.)

---

### Post by LKjell on 2009-12-06
The thing I do not understand is to why have a function to do the basic like

pilha_vazia()

Can't you just write it ```
if(topo->seg == NULL)
{
       printf("pilha vazia\n");
}

```

It might not be a burden but having too many of these little "inline" function just complicate it more than necessary. Anyway use malloc to allocate dynamic memory.

---

### Post by MadCow108 on 2009-12-06
the reason for that will probably be encapsulation, which is always a good thing.
compiled with optimization this also gives no runtime costs for simple cases

---

### Post by dwhitney67 on 2009-12-06
> **LKjell said:**
> The thing I do not understand is to why have a function to do the basic like

pilha_vazia()

Can't you just write it ```
if(topo->seg == NULL)
{
       printf("pilha vazia\n");
}

```

It might not be a burden but having too many of these little "inline" function just complicate it more than necessary. Anyway use malloc to allocate dynamic memory.
The proper way would be:
```

if (topo && topo->seg == NULL)
{
   ...
}

```

Never dereference a pointer until you know it is valid.

---

### Post by masterof14 on 2009-12-06
> **MadCow108 said:**
> free does not necessarily change anything in the memory, it just allows that the memory block can be reused for other allocations. It may only be overwritten when another allocation uses this freed memory

if you want to check for a memory leak use the valgrind tool

I suspect from your previous posts that pilla is a singly linked list.
in this case your delete currupts the list as the previous element points to an invalid memory block after the delete

deletes in singly linked lists can only delete the next element not the current


Pilha means Stack my code is:

coordenadas.c (coordinates):

```
#include <stdio.h>
#include <stdlib.h>
#include "pilha.h"
#include "coordenadas.h"

pilha * pilha_coordenadas(char nomeficheiro[1024])
{
    char linha[1024];
    char controlo[1024];
    float x, y;
    coord * xy;
    pilha * p_coordenadas;
    FILE * ficheiro;
    p_coordenadas = cria_pilha();
    xy = (coord*) malloc(sizeof(coord));
    ficheiro = fopen(nomeficheiro, "r");
    while(fgets(linha, 1024, ficheiro) != NULL)
    {
        if(sscanf(linha, "%f %f %s", &x, &y, controlo) == 2)
        {
            xy->x = x;
            xy->y = y;
            p_coordenadas = insere_coord(p_coordenadas, xy);
        }
    }
    fclose(ficheiro);
    return p_coordenadas;
}
```

coordenadas.h:

```
#ifndef COORDENADAS_H
#define COORDENADAS_H

#include "tipos.h"

pilha * pilha_coordenadas(char nomeficheiro[1024]);


#endif
```

pilha.c (stack):

```
#include <stdlib.h>
#include <stdio.h>
#include "pilha.h"

pilha * cria_pilha()
{
    return NULL;
}
int pilha_vazia(pilha * topo)
{
    if (topo == NULL)
    {
        return 1;
    }
    else
    {
        return 0;
    }
}
pilha * insere_coord(pilha * topo, coord * xy)
{
    pilha * novo;
    novo = (pilha *) malloc(sizeof(pilha));
    if (novo == NULL)
    {
        printf("falta de memoria\n");
        exit(-1);
    }
    if(!dado_existente(topo, xy))
    {
        (*novo).xy = *xy;
        (*novo).seg = topo;
        return novo;
    }
    else
    {
        return topo;
    }
}
pilha *remove_coord(pilha * topo){
    pilha * aux;
    if(pilha_vazia(topo)!= 0)
    {
        printf("pilha vazia\n");
    }
    else
    {
        aux = topo;
        topo = (*topo).seg;
        free(aux);
    }
    return topo;
}
void imprime_topo(pilha * topo)
{
    printf("x =  %f\ty = %f\n", topo->xy.x, topo->xy.y);
}
int dado_existente(pilha * topo, coord * xy)
{
    int i;
    i = 0;
    while(topo != NULL)
    {
        if(topo->xy.x == xy->x && topo->xy.y == xy->y)
        {
            i = i + 1;
        }
        topo = topo->seg;
    }
    return i;
}
```

pilha.h:

```
#ifndef PILHA_H
#define PILHA_H

#include "tipos.h"

pilha * cria_pilha();
pilha * insere_coord(pilha * topo, coord * xy);
pilha * remove_coord(pilha * topo);
int pilha_vazia(pilha * topo);
void imprime_topo(pilha * topo);
int dado_existente(pilha * topo, coord * xy);


#endif
```

tipos.h (types):

```
#ifndef TIPOS_H
#define TIPOS_H

typedef struct coord_st
{
    float x;
    float y;
} coord;

typedef struct pilha_st
{
    coord xy;
    struct pilha_st * seg;
}pilha;

#endif
```

main.c:

```
#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <stdio.h>
#include <stdlib.h>
#include "pilha.h"
#include "coordenadas.h"



int main(int argc, char *argv[])
{
    char linha[1024];
    char nome[1024];
    char nomeficheiro[1024];
    int instante;
    pilha *p_coord;
    p_coord = cria_pilha();
    while(fgets(linha,1024,stdin)!= NULL)
    {
        if(sscanf(linha, "%s %d", nome, &instante) == 2)
        {
            sprintf(nomeficheiro, "%s_%d.data", nome, instante);
            p_coord = pilha_coordenadas(nomeficheiro);
        }
    }
    while(!pilha_vazia(p_coord))
    {
        imprime_topo(p_coord);
        remove_coord(p_coord);
    }

  return EXIT_SUCCESS;
}
```


perhaps these way is easier to get the mistake.

And thanks!

---

### Post by LKjell on 2009-12-06
I see you have put a lot of time to write this. But sometimes I think you over do with writing functions. Instead of writing ```
pilha *p = cria_pilha();
```
Write
```
pilha *p = NULL;
```
Extra layer of abstraction just complicate it more. The same with pilha_vazia. You do not need these fancy functions.

---

### Post by MadCow108 on 2009-12-06
> **LKjell said:**
> I see you have put a lot of time to write this. But sometimes I think you over do with writing functions. Instead of writing ```
pilha *p = cria_pilha();
```
Write
```
pilha *p = NULL;
```
Extra layer of abstraction just complicate it more. The same with pilha_vazia. You do not need these fancy functions.

Sorry but your advice is complete nonsense.
Abstraction is good. It makes things easier instead of more complicated.
Also it greatly enhances refactoring and reusability.

arbitrary example
stack *p = NULL;
means nothing to an external,
stack *p = empty_stack();
is completely clear.

and if you now change the container below the stack in which an empty stack is not NULL anymore, but for example a dummy element (as it is common in many list implementations).
Now in your world you have to change every occurrence of NULL, this will surely be fun, as NULL can mean a lot more than a empty stack.
but if you abstract it, its a simple change in a single location.

the only reason not to abstract is when the abstraction penalty gets to high for your performance.
but in this case it is clearly not the relevant, these functions get inlined at no extra cost.


@masterof14
what exactly is the problem?
do you have a memory leak? or a segmentation fault?
I don't want to read all this code in a foreign language and try to guess whats not working

---

### Post by masterof14 on 2009-12-06
I appreciate all of your help but I already found the bug > p_coord =remove_coord(p_coord);
Thanks

---

### Post by LKjell on 2009-12-07
> **MadCow108 said:**
> Sorry but your advice is complete nonsense.
Abstraction is good. It makes things easier instead of more complicated.
Also it greatly enhances refactoring and reusability.

arbitrary example
stack *p = NULL;
means nothing to an external,
stack *p = empty_stack();
is completely clear.

and if you now change the container below the stack in which an empty stack is not NULL anymore, but for example a dummy element (as it is common in many list implementations).
Now in your world you have to change every occurrence of NULL, this will surely be fun, as NULL can mean a lot more than a empty stack.
but if you abstract it, its a simple change in a single location.

the only reason not to abstract is when the abstraction penalty gets to high for your performance.
but in this case it is clearly not the relevant, these functions get inlined at no extra cost.


If you look at the code again p_coord = cria_pilha(); really does not do anything since in the while loop he is using the pointer to point to something else. Even if he change the cria_pilha to do other fancy stuff it is still lost in the while loop. 

But if the while loop had p_coord = pilha_coordenadas(nomeficheiro, p_coord); passing in whatever cria_pilha did would be useful.

```
    pilha *p_coord;
    p_coord = cria_pilha();
    while(fgets(linha,1024,stdin)!= NULL)
    {
        if(sscanf(linha, "%s %d", nome, &instante) == 2)
        {
            sprintf(nomeficheiro, "%s_%d.data", nome, instante);
            p_coord = pilha_coordenadas(nomeficheiro);
        }
    }

```

---

### Post by MadCow108 on 2009-12-07
even if its unnecessary in a certain situation, it may be very useful in others. (not to mention the readability!)
and just mixing the abstracted and not abstracted style is not a very good idea
either always abstract a certain part or never. Otherwise you just end up thinking something is encapsulated and modify the internals just to notice the original writer did not use it consistently and thus screwing everything up.

---

