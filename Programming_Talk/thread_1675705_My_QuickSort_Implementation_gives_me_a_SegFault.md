---
title: "My QuickSort Implementation gives me a SegFault"
date: 2011-01-26
forum: Programming Talk
---

### Post by Roberto_Lapuente on 2011-01-26
Hi, I implemented QuickSort to work with integers and it worked and know that I use the same implementation for Comparable objects i'm getting a Segmentation Fault, please help!

```
void Quick_Sort(Comparable datos[], int min, int max)
{
    int indice_pivote;

    if ((max-min) > 0)
    {
        indice_pivote = Encontrar_Pivote(datos, min, max);
        Quick_Sort(datos, min, indice_pivote-1);
        Quick_Sort(datos, indice_pivote+1, max);
    }
}

int Encontrar_Pivote(Comparable datos[], int min, int max)
{
    Comparable pivote = datos[min];
    int indice_pivote = min++;
    int res = 0;

    while (min<max)
    {
        if (datos[min].Compare_To(pivote)<=0 && datos[max].Compare_To(pivote)>=0)
        {
            min++;
            max--;
        }
        else if (datos[min].Compare_To(pivote)>=0 && datos[max].Compare_To(pivote)<=0)
        {
            Rotar(datos, min, max);
            min++;
            max--;
        }
        else if (datos[min].Compare_To(pivote)<=0 && datos[max].Compare_To(pivote)<=0)
        {
            min++;
        }
        else if (datos[min].Compare_To(pivote)>=0 && datos[max].Compare_To(pivote)>=0)
        {
            max--;
        }
    }

    if (min > max)
        res = max;
    else if (datos[min].Compare_To(pivote) < 0)
        res = min;
    else if (datos[min].Compare_To(pivote) > 0)
        res = (min - 1);

    Rotar(datos, res, indice_pivote);
    return res;
}

void Rotar(Comparable datos[], int primero, int segundo)
{
    Comparable aux = datos[primero];
    datos[primero] = datos[segundo];
    datos[segundo] = aux;
}

```

---

### Post by talonmies on 2011-01-26
Where is the segmentation fault occurring? What is Comparable? How are you calling Quick_Sort when it fails?

---

### Post by Arndt on 2011-01-26
> **Roberto_Lapuente said:**
> Hi, I implemented QuickSort to work with integers and it worked and know that I use the same implementation for Comparable objects i'm getting a Segmentation Fault, please help!

```
void Quick_Sort(Comparable datos[], int min, int max)
{
    int indice_pivote;

    if ((max-min) > 0)
    {
        indice_pivote = Encontrar_Pivote(datos, min, max);
        Quick_Sort(datos, min, indice_pivote-1);
        Quick_Sort(datos, indice_pivote+1, max);
    }
}

int Encontrar_Pivote(Comparable datos[], int min, int max)
{
    Comparable pivote = datos[min];
    int indice_pivote = min++;
    int res = 0;

    while (min<max)
    {
        if (datos[min].Compare_To(pivote)<=0 && datos[max].Compare_To(pivote)>=0)
        {
            min++;
            max--;
        }
        else if (datos[min].Compare_To(pivote)>=0 && datos[max].Compare_To(pivote)<=0)
        {
            Rotar(datos, min, max);
            min++;
            max--;
        }
        else if (datos[min].Compare_To(pivote)<=0 && datos[max].Compare_To(pivote)<=0)
        {
            min++;
        }
        else if (datos[min].Compare_To(pivote)>=0 && datos[max].Compare_To(pivote)>=0)
        {
            max--;
        }
    }

    if (min > max)
        res = max;
    else if (datos[min].Compare_To(pivote) < 0)
        res = min;
    else if (datos[min].Compare_To(pivote) > 0)
        res = (min - 1);

    Rotar(datos, res, indice_pivote);
    return res;
}

void Rotar(Comparable datos[], int primero, int segundo)
{
    Comparable aux = datos[primero];
    datos[primero] = datos[segundo];
    datos[segundo] = aux;
}

```

Isn't it the case that the pivot element can be the first element (index 0), and then you will call QuickSort recursively with -1?

Why do you implement quicksort? It's not a good sorting algorithm - merge sort is both stable and has a guaranteed nlogn behaviour.

---

### Post by fct on 2011-01-26
Looks like homework. I'll explain a method to debug segfaults:

First, compile using gcc with the "-g" arg to include debugging symbols.

$ ulimit -c unlimited

Run program until it segfaults, then find the "core" file.

$ gdb your_program core

gdb will be right at the moment it crashed. Then use the "bt" gdb command to get the backtrace. With commands like "info local" and "info args" you can get info about local variables, function args and their values when it crashed.

Check this tutorial for more info:
[http://cs.baylor.edu/~donahoo/tools/gdb/tutorial.html](http://cs.baylor.edu/~donahoo/tools/gdb/tutorial.html)

---

