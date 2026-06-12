---
title: "[C] Lots and lots of &quot;warning: assignment from incompatible pointer type&quot;"
date: 2009-07-07
forum: Programming Talk
---

### Post by Toddyn on 2009-07-07
Hi guys =)

I was programming some basic stuff to try to learn some C. But i can't avoid this warnings, i guess im using the wrong syntax, but im not sure! Freaking pointers are messing with my head hahahahha
(I'm using NetBeans IDE 6.5, the compiler is the one that comes with ubuntu (I'm a linux noob btw) gcc)

so basically this is what I have:

This is the header file
[php]/* 
 * File:   header.h
 * Author: Jorge
 *
 * Created on 10 de Abril de 2009, 00:07
 */

#ifndef _HEADER_H
#define    _HEADER_H

#define MAXIMO 100
#define ErroListaCheia -1
#define ErroListaVazia -2
#define ErroPosicao -3

typedef struct {
    char* nome;
    double valor;
} tLancamento;

typedef struct {
    struct tLancamento* info;
    struct tLista* proximo;
} tLista;

typedef struct {
    struct tLista* lista;
    int ultimo;
} cLista;

#ifdef    __cplusplus
extern "C" {
#endif




#ifdef    __cplusplus
}
#endif

#endif    /* _HEADER_H */[/php]I'm not gonna paste the whole .c file here, just gonna copy one of the functions, since this warning is present on most of them:

[php]#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <malloc.h>
#include "header.h"
.
.
.
.
.
.
int adicionaNoInicio(cLista* aLista, tLancamento* dado) {
    tLista* novo;
    novo = (tLista *) malloc(sizeof (tLista));
    if (novo == NULL)
        return ErroListaCheia;
    else {
        novo->proximo = aLista->lista;
        novo->info = dado; // THIS IS LINE 49
        aLista->lista = novo; // THIS IS LINE 50
        aLista->ultimo = aLista->ultimo + 1;
        return (1);
    }
}[/php]these are the first 2 warnings I get when i try to compile this:
principal.c: In function ‘adicionaNoInicio’:
[COLOR=DarkOrange]principal.c:49: warning: assignment from incompatible pointer type
principal.c:50: warning: assignment from incompatible pointer type[/COLOR]

I also get this error on most of the other functions :(

If you need more parts of the code or any other info, let me know asap!!

-----------------------

Yeah, you probably don't know the meaning of the variables', functions', structs' names because they are all in PT-BR (my language duh :P) but i guess you can still understand the code, right?

I also bet that my mistake is probably really easy to spot (or at least I hope so), and you guys will laugh at me hahaha but i seriously need some help here.

Sorry if I made any mistake or broke any rules on this post, I really had no time to read all rules and stuff (it is 5am here!), I will try to do better next time :P
Also excuse my english. I know its far from perfect hehehe

Thanks for your time and patience guys :)

---

### Post by fr4nko on 2009-07-07
There is a small problem in your code. You should define the struct tLista like that:
```

[COLOR=#000000][COLOR=#0000bb]typedef struct [/COLOR][COLOR=#007700]{
    [/COLOR][COLOR=#0000bb]tLancamento[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000bb]info[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]tLista[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000bb]proximo[/COLOR][COLOR=#007700];
} [/COLOR][COLOR=#0000bb]tLista[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
```
because the previous definition was something like:
```

[COLOR=#000000][COLOR=#0000bb]typedef struct [/COLOR][COLOR=#007700]{
    [/COLOR][COLOR=#0000bb]char[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000bb]nome[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]double valor[/COLOR][COLOR=#007700];
} [/COLOR][COLOR=#0000bb]tLancamento[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
```
If you want to define 'struct tLancamento' you should write:
```

[COLOR=#000000][COLOR=#0000bb]struct [/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb]tLancamento[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]{
    [/COLOR][COLOR=#0000bb]char[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000bb]nome[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]double valor[/COLOR][COLOR=#007700];
}[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
```Buena suerte! :-)

Francesco

---

### Post by Toddyn on 2009-07-07
Hmmm that kinda helped decreasing the number of warnings. But im still getting some :(

this is my new header file:
[php]/* 
 * File:   header.h
 * Author: Jorge
 *
 * Created on 10 de Abril de 2009, 00:07
 */

#define MAXIMO 100
#define ErroListaCheia -1
#define ErroListaVazia -2
#define ErroPosicao -3

typedef struct {
    char *nome;
    float valor;
} tLancamento;

typedef struct {
    tLancamento *info;
    struct tLista *proximo;
} tLista;

typedef struct {
    tLista *lista;
    int ultimo;
} cLista;[/php]Like i said, the number of warnings has decreased but I'm still having some trouble:

```
gcc    -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/principal.o.d -o build/Debug/GNU-Linux-x86/principal.o principal.c
principal.c: In function ‘adicionaNoInicio’:
principal.c:46: warning: assignment from incompatible pointer type
principal.c: In function ‘retiraDoInicio’:
principal.c:62: warning: assignment from incompatible pointer type
principal.c: In function ‘eliminaDoInicio’:
principal.c:74: warning: assignment from incompatible pointer type
principal.c: In function ‘adicionaNaPosicao’:
principal.c:96: warning: assignment from incompatible pointer type
principal.c:100: warning: assignment from incompatible pointer type
principal.c: In function ‘retiraDaPosicao’:
principal.c:119: warning: assignment from incompatible pointer type
principal.c:120: warning: assignment from incompatible pointer type
principal.c:121: warning: assignment from incompatible pointer type
principal.c: In function ‘adicionaEmOrdem’:
principal.c:140: warning: assignment from incompatible pointer type
principal.c: In function ‘retiraEspecifico’:
principal.c:173: warning: assignment from incompatible pointer type
principal.c: In function ‘destroiLista’:
principal.c:187: warning: assignment from incompatible pointer type
principal.c: In function ‘main’:
principal.c:247: warning: assignment from incompatible pointer type
principal.c:249: warning: assignment from incompatible pointer type
```this is the code for principal.c
[php]/*
 * File:   principal.c
 * Author: Jorge
 *
 * Created on 10 de Abril de 2009, 00:46
 */

#include <string.h>
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <stddef.h>
#include <malloc.h>
#include "header.h"

cLista* criaLista() {
    cLista *aLista;
    aLista = (cLista *)malloc(sizeof(cLista));
    if (aLista != NULL) {
        aLista->ultimo = 0;
        aLista->lista = NULL;
    }
    return (aLista);
}

bool listaVazia(cLista* aLista) {
    if (aLista->ultimo == 0)
        return true;
    else
        return false;
}

bool maior(tLancamento* t1, tLancamento* t2) {
    if (t1->valor >= t2->valor)
        return true;
    else
        return false;
}

int adicionaNoInicio(cLista* aLista, tLancamento* dado) {
    tLista *novo;
    novo = (tLista *)malloc(sizeof(tLista));
    if (novo == NULL)
        return ErroListaCheia;
    else {
        novo->proximo = aLista->lista;
        novo->info = dado;
        aLista->lista = novo;
        aLista->ultimo = aLista->ultimo + 1;
        return (1);
    }
}

tLancamento* retiraDoInicio(cLista* aLista) {
    tLista *saiu;
    tLancamento *volta;
    if (listaVazia(aLista))
        return (NULL);
    else {
        saiu = aLista->lista;
        volta = saiu->info;
        aLista->lista = saiu->proximo;
        aLista->ultimo = aLista->ultimo - 1;
        free(saiu);
        return (volta);
    }
}

void eliminaDoInicio(cLista* aLista) {
    tLista *saiu;
    if (listaVazia(aLista) == false)
    {
        saiu = aLista->lista;
        aLista->lista = saiu->proximo;
        aLista->ultimo = aLista->ultimo - 1;
        free(saiu->info);
        free(saiu);
    }
}

int adicionaNaPosicao(cLista* aLista, tLancamento* info, int posicao) {
    tLista *novo, *anterior;
    if (posicao > aLista->ultimo + 1)
        return (ErroPosicao);
    else
        if (posicao == 1)
            return (adicionaNoInicio(aLista, info));
        else {
            novo = (tLista *)malloc(sizeof(tLista));
            if (novo == NULL)
                return (ErroListaCheia);
            else {
                anterior = aLista->lista;
                int i;
                for (i = 0; i < posicao - 2; i++) {
                anterior = anterior->proximo;
            }
            novo->proximo = anterior->proximo;
            novo->info = info;
            anterior->proximo = novo;
            aLista->ultimo = aLista->ultimo + 1;
            return (aLista->ultimo);
        }
    }
}

tLancamento* retiraDaPosicao(cLista* aLista, int posicao) {
    tLista *anterior, *eliminar;
    tLancamento *volta;
    if (posicao > aLista->ultimo)
        return NULL;
    else
        if (posicao == 1)
            return (retiraDoInicio(aLista));
        else {
            anterior = aLista->lista;
            int i;
            for (i = 0; i < posicao - 2; i++)
                anterior = anterior->proximo;
            eliminar = anterior->proximo;
            volta = &(eliminar->info);
            anterior->proximo = eliminar->proximo;
            aLista->ultimo = aLista->ultimo - 1;
            free(eliminar);
            return (volta);
        }
}

int adicionaEmOrdem(cLista* aLista, tLancamento* info) {
    tLista *atual;
    int posicao;
    if (listaVazia(aLista))
        adicionaNoInicio(aLista, info);
    else {
        atual = aLista->lista;
        posicao = 1;
        tLancamento* lancamentoAtual;
        lancamentoAtual = atual->info;
        while (atual->proximo != NULL && maior(info, lancamentoAtual)) {
            atual = atual->proximo;
            lancamentoAtual = atual->info;
            posicao = posicao + 1;
        }
        if (maior(info, lancamentoAtual))
            return (adicionaNaPosicao(aLista, info, posicao + 1));
        else
            return (adicionaNaPosicao(aLista, info, posicao));
    }
}

int adiciona(cLista* aLista, tLancamento* info) {
    if (listaVazia(aLista))
        return adicionaNoInicio(aLista, info);
    else
        return adicionaNaPosicao(aLista, info, aLista->ultimo + 1);
}

tLancamento* retira(cLista* aLista) {
    return retiraDaPosicao(aLista, aLista->ultimo);
}

tLancamento* retiraEspecifico(cLista* aLista, float value) {
    tLista *atual;
    if (listaVazia(aLista))
        return NULL;
    else {
        atual = aLista->lista;
        int posicao;
        for (posicao = 1; posicao < aLista->ultimo; posicao++) {
            if (atual->info->valor == value)
                return retiraDaPosicao(aLista, posicao);
            else
                atual = atual->proximo;
        }
        return NULL;
    }
}

void destroiLista(cLista *aLista) {
    tLista *atual, *anterior;
    if (listaVazia(aLista))
        free(aLista);
    else {
        atual = aLista->lista;
        while (atual != NULL) {
            anterior = atual;
            atual = atual->proximo;
            free(anterior->info);
            free(anterior);
        }
        free(aLista);
    }
}

int perguntaLista() {
    int x = -1;
    while (x < 1 || x > 2) {
        printf("\nEsolha que lista o programa deve manipular:");
        printf("\n1 - Devedores");
        printf("\n2 - Credores\n\n");
        scanf("%d", &x);
        if (x < 1 || x > 2)
            printf("\nOpção invalida!!!\n");
    }
    return x;
}

int mostreMenu() {
    int x = -1;
    while (x < 0 || x > 10) {
        printf("\nOpções disponiveis:");
        printf("\n0 - Adicionar lançamento");
        printf("\n1 - Adicionar lançamento na posição");
        printf("\n2 - Adicionar lançamento em ordem");
        printf("\n3 - Adicionar lançamento no início");
        printf("\n4 - Retirar último lançamento");
        printf("\n5 - Retirar lançamento da posição");
        printf("\n6 - Retirar primeiro lançamento");
        printf("\n7 - Retirar lançamento específico");
        printf("\n8 - Totalizar lançamentos");
        printf("\n9 - Destruir lista");
        printf("\n10 - Finalizar programa\n\n");
        scanf("%d", &x);
        if (x < 0 || x > 10)
            printf("\nOpção inválida!!!\n");
    }
    return x;
}

int main(int argc, char** argv) {

    cLista *devedores, *credores, *escolhida;
    tLancamento *info;
    info = (tLancamento *)malloc(sizeof(tLancamento));
    int opcao, queLista;

    devedores = criaLista();
    credores = criaLista();
    opcao = -1;
    queLista = -1;
    char pessoa[MAXIMO];
    float valor;

    while (opcao != 10) {
        queLista = perguntaLista();
        if (queLista == 1)
            escolhida = &devedores;
        else
            escolhida = &credores;
        opcao = mostreMenu();
        switch (opcao) {
            case 0:
            {
                // Adicionar lançamento
                printf("\nNome do contato: ");
//                fgets (pessoa, MAXIMO, stdin);
                printf("\nValor: ");
                scanf("%f", &valor);
                info->nome = pessoa;
                info->valor = valor;
                adiciona(escolhida, info);
            } break;
            case 1:
            {
                // Adicionar lançamento na posição
                printf("\nNome do contato: ");
//                scanf("%s", &pessoa);
                printf("\nValor: ");
                scanf("%f", &valor);
                int posicao;
                printf("\nPosicao: ");
                scanf("%d", &posicao);
                info->nome = pessoa;
                info->valor = valor;
                adicionaNaPosicao(escolhida, info, posicao);
            } break;
            case 2:
            {
                // Adicionar lançamento em ordem
                printf("\nNome do contato: ");
//                scanf("%s", &pessoa);
                printf("\nValor: ");
                scanf("%f", &valor);
                info->nome = pessoa;
                info->valor = valor;
                adicionaEmOrdem(escolhida, info);
            } break;
            case 3:
            {
                // Adicionar lançamento no início
                printf("\nNome do contato: ");
//                scanf("%s", &pessoa);
                printf("\nValor: ");
                scanf("%f", &valor);
                info->nome = pessoa;
                info->valor = valor;
                adicionaNoInicio(escolhida, info);
            } break;
            case 4:
            {
                // Retirar último lançamento
                retira(escolhida);

            } break;
            case 5:
            {
                // Retirar lançamento na posição
                int posicao;
                printf("\nPosicao: ");
                scanf("%d", &posicao);
                retiraDaPosicao(escolhida, posicao);
            } break;
            case 6:
            {
                // Retirar primeiro lançamento
                retiraDoInicio(escolhida);
            } break;
            case 7:
            {
                // Retirar lançamento específico
                printf("\nValor especifico a ser removido: ");
                scanf("%f", &valor);
                retiraEspecifico(escolhida, valor);
            } break;
            case 8:
            {
                // Totalizar lançamentos
                int i;
                float total;
                total = 0;
                for(i = 0; i < escolhida->ultimo; i++)
                    total = total + escolhida->lista->info->valor;
                printf("\nValor total dos lançamentos: %f", total);
            } break;
            case 9:
            {
                // Destruir Lista
                destroiLista(escolhida);
            } break;
            case 10:
            {
                // Finalizar programa
            }
        }
    }
    return (EXIT_SUCCESS);
}
[/php]i figured i would post it here as it might make it easier to spot the mistakes.. i've been trying to find the cause of the warnings there for over 5 hours (yea, im a noob i know =[ ) so any help is more than welcome.
don't mind the main(), i'm still working on it... im concerned more about the warnings than the main().


thanks guys

---

### Post by fr4nko on 2009-07-07
yet another error.
```
typedef struct {
    tLancamento *info;
    struct tLista *proximo;
} tLista;
```should be
```
typedef struct {
     tLancamento *info;
     tLista *proximo;
 } tLista;
```Generally speaking, if you write something like:
```

struct boo {
  int x;
  double v;
};

```you define the new type 'struct boo', Instead if you write
```

typedef struct {
  int x;
  double v;
} boo;

```you define a new type 'boo'. This is why you are doing confusion.

Francesco

---

### Post by Toddyn on 2009-07-07
> **fr4nko said:**
> yet another error.
```
typedef struct {
    tLancamento *info;
    struct tLista *proximo;
} tLista;
```should be
```
typedef struct {
     tLancamento *info;
     tLista *proximo;
 } tLista;
```Generally speaking, if you write something like:
```

struct boo {
  int x;
  double v;
};

```you define the new type 'struct boo', Instead if you write
```

typedef struct {
  int x;
  double v;
} boo;

```you define a new type 'boo'. This is why you are doing confusion.

Francesco

Hmm weird :o

when i try using this:
[php]typedef struct {
     tLancamento *info;
     tLista *proximo;
 } tLista;[/php]

i get this:
```

gcc    -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/principal.o.d -o build/Debug/GNU-Linux-x86/principal.o principal.c
In file included from principal.c:14:
header.h:23: error: expected specifier-qualifier-list before ‘tLista’
```


any ideas on why is this happening?

---

### Post by monraaf on 2009-07-07
> **Toddyn said:**
> Hmm weird :o

when i try using this:
[php]typedef struct {
     tLancamento *info;
     tLista *proximo;
 } tLista;[/php]

i get this:
```

gcc    -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/principal.o.d -o build/Debug/GNU-Linux-x86/principal.o principal.c
In file included from principal.c:14:
header.h:23: error: expected specifier-qualifier-list before ‘tLista’
```


any ideas on why is this happening?

The classical way to do this is:
[PHP]
typedef struct _foo {
    struct _foo *next;
} foo, *fooptr;
[/PHP]

---

### Post by fr4nko on 2009-07-07
You should write something like
```

struct _tLista {
    [COLOR=#000000][COLOR=#0000bb]tLancamento [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]info[/COLOR][COLOR=#007700]; 
    struct _[/COLOR][COLOR=#0000bb]tLista [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]proximo[/COLOR][COLOR=#007700];
 }

typedef struct _tLista tLista;
[/COLOR][/COLOR]
```the reason is that the definition of struct tLista is recursive. If you perform a typedef and a struct definition at the same time the compiler get confused because the struct definition is recursive. It will work if you define in the first step the struct definition and you perform the typedef only as a second step. Note also tht I've put un underscore in struct _tLista to avoid confusion with the flowing typedef but this is not strictly required.

Francesco

---

### Post by crazyfuturamanoob on 2009-07-07
Maybe just declare all structs like this:
```

typedef struct StructName {
    // variables
    ....
} StructName;

```

---

