---
title: "From C to Mips Assembler(help please)"
date: 2009-06-30
forum: Programming Talk
---

### Post by Aejo on 2009-06-30
Pleaseeeeeee can anyone give the MIPS code for this C program?????? it's a head-tail probability.
Pleaseeeeeee i need helpppp.

#include <stdio.h>
#include <stdlib.h>
#define base 2

int sequenza(int);
int proba(int);
int main(){

printf("\n    L'applicazione consiste nel determinare\n ");
printf("     la probabilità su uno lancio di moneta \n\n");
printf("L'applicazione scomette che nei prossimi n lanci non usciranno piu di due croci consecutive\n");
int c;
  do{

    int numero, successo, i, seq = 1;
printf("\n\n->inserire un numero superiore o uguale a zero  :");

/*inserimento numero di lancio*/
scanf("%d", &numero);

/*controllo se il numero inserito è negativo*/
while(numero < 0){
printf("Attenzione il numero inserito non è valido! inserirlo di nuovo > ");
scanf("%d", &numero);
}

/*calcolo du numero de sequenza possibile*/
 seq = sequenza(numero);

/*calcolo numero di sequenza di successo*/
 successo = proba(numero);

printf("\nprobabilità di successo = %d / %d\n\n", successo, seq);
printf(" Digitare c per continuare oppure w per uscire ");
c=getchar();

}while((getchar())!='w');

 return 0;
}


int proba(int n){
 if(n < 3)
 return sequenza(n);
   else
  return proba(n - 1) + proba(n - 2)+ proba(n - 3);
}

int sequenza(int a){
 int i, seq = 1;
 for(i = 1; i<= a;i++)
  seq = seq * base;
  return seq;
}

---

### Post by unknownPoster on 2009-06-30
This looks like a homework problem. We don't do your homework for you:

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by Can+~ on 2009-06-30
Nope. This is a homework. Have some reference about the MIPS:

[https://www.cs.tcd.ie/~waldroj/itral/spim_ref.html](https://www.cs.tcd.ie/~waldroj/itral/spim_ref.html)

And download SPIM, it's available on the repository:

```
sudo apt-get install spim
```

spim myfile.asm

---

### Post by Elfy on 2009-06-30
Read the links you've been given, but thread closed here.

> What is allowed:

Just because posting homework assignments is against forum policy, you can ask questions that are related to homework. If you get stuck on certain aspects of the assignment (like compiling your code in Linux, or something not specific to the solution to the problem.) you can ask.

---

