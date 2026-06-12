---
title: "C++ source code problem :)"
date: 2010-10-17
forum: Programming Talk
---

### Post by Patrunjel007 on 2010-10-17
Hello, my problem is not related to linux, but somewone please help me.I wrote this code
```

#include<iostream>
#define Nmax 20
using namespace std;
struct nod{int info,adr_urm;};
void adauga(nod v[],int x,int x1);
int lista_plina(nod v[],int x);
void insertion_sort(nod v[],int x);
void init(nod v[]);
int main(){
    nod lista[Nmax+1];
    init(lista);
    int vf=0,i,n,x;
    cout<<"n=";cin>>n;
    for(i=0;i<n && n<=Nmax;i++){
        cout<<"x=";cin>>x;
        adauga(lista,vf,x);}
    insertion_sort(lista,vf);
    for(i=0;i<n;i++)
        cout<<endl<<"x="<<lista[i].info<<endl;
    return 0;}
int lista_plina(nod v[],int x){
    return x==Nmax;}
void adauga(nod v[],int x,int x1){
    if(x>0){
        if(lista_plina(v,x)==0){
            v[x+1].info=x1;
            v[x].adr_urm=x+1;}
        else
            cout<<"Lista este plina";}
    else
        v[1].info=x1;}
void init(nod v[]){
    int i;
    for(i=0;i<=Nmax;i++){
        v[i].info=0;
        v[i].adr_urm=0;}}
void insertion_sort(nod a[],int x){
    int i,j;
    nod aux;
    for(i=2;i<=x;i++){
        j=i;
        while(j>1 && a[j-1].info>a[j].info){
            aux=a[j-1];
            a[j-1]=a[j];
            a[j]=aux;
            j--;}}}

``` that is supposed to get a limple binded list, and sort it by insertion sort, and then ouput it.It doesn't work right, can somewone, please, help me with this?

As i was debugging the source, i found out that the problem is at the "adauga" function.I hope it helps...

---

### Post by bodhi.zazen on 2010-10-17
*Thread moved to **Programming Talk**.*

---

### Post by Patrunjel007 on 2010-10-17
I'm verry sorry for posting in the wrong section

---

### Post by johnl on 2010-10-17
In case someone actually wants to help, I have taken the liberty of formatting the code nicely.

```

#include <iostream>

#define Nmax 20

using namespace std;

struct nod {
    int info;
    int adr_urm;
};

void adauga(nod v[], int x, int x1);
int lista_plina(nod v[], int x);
void insertion_sort(nod v[], int x);
void init(nod v[]);

int main()
{
    nod lista[Nmax + 1];

    init(lista);

    int vf = 0, i, n, x;

    cout << "n=";
    cin >> n;

    for(i = 0; i < n && n <= Nmax; i++) {
        cout << "x=";
        cin >> x;
        adauga(lista, vf, x);
    }

    insertion_sort(lista, vf);

    for(i = 0; i < n; i++)
        cout << endl << "x=" << lista[i].info << endl;

    return 0;
}

int lista_plina(nod v[], int x)
{
    return x == Nmax;
}

void adauga(nod v[], int x, int x1)
{
    if(x>0) {
        if(lista_plina(v,x) == 0) {
            v[x + 1].info = x1;
            v[x].adr_urm = x + 1;
        } else
            cout << "Lista este plina";
    } else
        v[1].info = x1;
}

void init(nod v[])
{
    int i;
    for(i = 0; i <= Nmax; i++) {
        v[i].info = 0;
        v[i].adr_urm = 0;
    }
}

void insertion_sort(nod a[],int x)
{
    int i,j;
    nod aux;

    for(i = 2; i <= x; i++) {
        j = i;
        while(j > 1 && a[j - 1].info > a[j].info) {
            aux = a[j - 1];
            a[j - 1] = a[j];
            a[j] = aux;
            j--;
        }
    }
}

```

---

### Post by bodhi.zazen on 2010-10-17
> **Patrunjel007 said:**
> I'm verry sorry for posting in the wrong section

Not a problem, hope you get an answer soon.

---

### Post by Some Penguin on 2010-10-17
Assorted notes:

* Please use meaningful variable names.  
```

int vf=0,i,n,x;

```
is seriously not cool.

* You have no comments.  I doubt that *you* really understand what every function is supposed to do versus what it's doing.

* 'vf' never, ever changes after it's initialized to 0.  This breaks everything.

* You are very inconsistent with array indices.  lista holds Nmax+1 items (indices 0..Nmax).   You iterate from 0..Nmax in asking for input.  You then, if vf == 0 (and it ALWAYS is), add the datum into slot *1* instead of 0, as if you don't know whether arrays start at 0 or 1.

* Similar objections hold for your actual sort.

* You should have easily noticed the above on your own through use of debuggers, through logging, and through simply stepping through your program by hand.  You could also have started going step-by-step, e.g. "let's first write a program which populates an array and see if that works, and THEN work on sorting".

---

