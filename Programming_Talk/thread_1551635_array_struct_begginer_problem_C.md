---
title: "array struct begginer problem C"
date: 2010-08-12
forum: Programming Talk
---

### Post by cristiangarofalo on 2010-08-12
Hey Guys, 
This is embarrasing but Ive been back and forth with this and at this point I'm lost.

I just want to pass an array of structures to a function.  How can I do that? I'm doing something like this (see below with no success)
 
Can anyone give me a hand with this?

int main ()
{
struct parameters
{
char par[8];
char val[8];
} m_parameters[10];

//my code here

use_struct (m_parameters):

} // end main

void use_struct(struct m *m_parameters)
{

}

---

### Post by Bachstelze on 2010-08-12
It's exactly the same thing as passing an array of ints or anything else.

```
void use_struct(struct m_parameters[]);
```

---

### Post by trent.josephsen on 2010-08-12
Can't help unless we know what problem you're encountering.  "no success" tells us nothing.

I see two potential issues with the code: (1) you can't tell, from inside use_struct, what the size of the array is; and (2) use_struct is not prototyped when it is called.

Make that three issues, as I just realized that no definition of "struct m" exists for the definition of use_struct (it should obviously be "struct parameters", and the definition of the struct should be at the top level of the file).

---

### Post by cristiangarofalo on 2010-08-12
> **Bachstelze said:**
> It's exactly the same thing as passing an array of ints or anything else.

```
void use_struct(struct m_parameters[]);
```


It shouldn't be a pointer? I want my array to be modified in the use_struct function.

Also when I copiled the code as you kindly told me , Compiler says:

It's scope is only this definition or declaration, which is probably not what you want. Then it has other messages stating that the structure is not being recognized inside the function.

---

### Post by Bachstelze on 2010-08-12
Uh, yes, should be something like [font=monospace]struct parameters[]  t[/font], not [font=monospace]struct m_parameters[][/font].  If you want to pass a pointer, you will need to also pass the length of the array as a second parameter, or make your array null-terminated.

---

### Post by trent.josephsen on 2010-08-12
Okay, here's what it boils down to.  In all but a few contexts, the name of an array (like "ary" in "int ary[10]") is treated *exactly* the same as a pointer to its first element.  You might hear someone say that the array "decays" into a pointer.  When you write a function that takes an "array" parameter, what it really takes is a pointer to the first element of the array.

```
int myfunc(int ary[]); // is the same as
int myfunc(int *ary);
```

In the body of the function, you can use the pointer almost exactly as you would use the original array.  This is part of the relationship between arrays and pointers in C, which is often misleadingly described as equivalence ("arrays and pointers are the same thing" or some such nonsense).  You can index it, pass it to other functions, return it, and do most things that are interesting to do with arrays.

Because it's a pointer variable, though, and not an array variable, you can't use sizeof to determine the number of elements it points to.  (sizeof will only tell you the size of the pointer and not the size of the block it references.)  This means that in order to avoid memory violations, you probably want to pass in a second parameter, the size of the array.

The complaint you're getting about scope is probably because you've misplaced the definition of the struct.  Without seeing your code, though, I can't tell you exactly what's wrong.  Put the struct definition up near the top of the file -- before the definition of main().  You need that struct definition to be "in scope" (visible) to all the functions that use it.

---

### Post by cristiangarofalo on 2010-08-12
Thank you All, Thank Trend for the Clarification. I was Able to compile but it seems the structure is not being modified on the main , See a piece of the code, ( name conventions are in spanish sorry.. , I'm argentinan)

I debug the parseo_mensaje function and the values  inside the function are being  properly pupulated. Now In the main it seems its empty. Any advice? This code is only for testing what I'm doing don't be scared =)


struct msg_parametros
{
char parametro[ETIQUETA];
char valor[ETIQUETA];
} matriz_msg_parametros[10];


void parseo_mensaje(char *mensaje,struct msg_parametros  *matriz_msg_parametros );

int main ()
{
int cant_parametros,i;
char mensaje[MAXMENS];
strcpy(mensaje,"NOTIFICAPARAM01=abier|PARAM02=salamin|PARAM03=abuelo|PARAM04=tio|PARAM05=nene|PARAM06=nena");
parseo_mensaje(mensaje,matriz_msg_parametros);

printf("parametro %s ",matriz_msg_parametros[3].parametro);
printf("valor %s\n ",matriz_msg_parametros[3].valor);
} 

void parseo_mensaje(char *mensaje,struct msg_parametros *matriz_msg_parametros )
{
int i,j,k,m,long_mensaje,cant_parametros;
char separador_parametro='|';
char separador_valor='=';

i = 8 ; j = 1 ; k = 1 ; m = 0 ;long_mensaje = longitud_cadena(mensaje);
cant_parametros= cantidad_parametros_mensaje(mensaje);
do 
{
j = posicion_caracter_buscado(mensaje,separador_valor,i)-1;
strcpy(matriz_msg_parametros[m].parametro,imprimir_valor_variable(mensaje,i,j)); 
i=j+1;
    if (m == cant_parametros-1)
    {
        strcpy(matriz_msg_parametros[m].valor,imprimir_valor_variable(mensaje,j+1,long_mensaje));  
        printf("valor %s\n ",matriz_msg_parametros[m].valor); //
    }
    else
    { 
    j = posicion_caracter_buscado(mensaje,separador_parametro,i)-1;
    strcpy(matriz_msg_parametros[m].valor,imprimir_valor_variable(mensaje,i,j));  
    i=j+1;
    }
m++;
} //end While
while  (m <= cant_parametros); 


} // parseo_mensaje

---

### Post by trent.josephsen on 2010-08-12
Not sure, but guessing it has something to do with what imprimir_valor_variable does.

If you're not already, be sure to enable lots of warnings so that your compiler can let you know when you make obvious mistakes.

---

