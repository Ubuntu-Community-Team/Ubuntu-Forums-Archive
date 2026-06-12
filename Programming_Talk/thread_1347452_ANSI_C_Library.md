---
title: "ANSI C Library"
date: 2009-12-06
forum: Programming Talk
---

### Post by masterof14 on 2009-12-06
Hey! I made two C headers one named "pilha.h":

```
#ifndef PILHA_H
#define PILHA_H


typedef struct pilha_st
{
    coord xy;
    struct pilha_st * seg;
}pilha;


pilha * cria_pilha();
pilha * insere_coord(pilha * topo, coord * xy);
coord coordenada_topo(pilha * topo);
pilha * remove_float(pilha * topo);
int pilha_vazia(pilha * topo);


#endif
```

 and the oder one named "coordenadas.h":

```
#ifndef COORDENADAS_H
#define COORDENADAS_H

typedef struct coord_st
{
    float x;
    float y;
} coord;

pilha * le_coordenadas(char nome[1024]);


#endif
```

my problem is: in both headers I need to declare the other header I already tried #include "the_oder_header.h" and #ifndef THE_OTHER_HEADER_H but on the main file always comes the same warning: implicit declaration of function 'function_name', witch results on a segmentation fault error :-?

Any clue? Thanks

---

### Post by dwhitney67 on 2009-12-06
Consider declaring your data structures, together, in a separate header file.  Then include this header file within the two existing header files that you have.

Something like...


Types.h:
```

#ifndef TYPES_H
#define TYPES_H

typedef struct pilha_st
{
    coord xy;
    struct pilha_st * seg;
} pilha;

typedef struct coord_st
{
    float x;
    float y;
} coord;

#endif

```
Then for pilha.h:
```

#ifndef PILHA_H
#define PILHA_H

#include "Types.h"

pilha * cria_pilha();
pilha * insere_coord(pilha * topo, coord * xy);
coord   coordenada_topo(pilha * topo);
pilha * remove_float(pilha * topo);
int     pilha_vazia(pilha * topo);

#endif

```
And for coordenadas.h:
```

#ifndef COORDENADAS_H
#define COORDENADAS_H

#include "Types.h"

pilha * le_coordenadas(char nome[1024]);

#endif

```

If after this you are still getting compiler warnings/errors, or if your program continues to SEGFAULT, then the issue with your application lies elsewhere.

---

### Post by masterof14 on 2009-12-06
Thanks a lot! Worked perfectly!

---

