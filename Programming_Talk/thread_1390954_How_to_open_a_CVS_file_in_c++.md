---
title: "How to open a CVS file in c++"
date: 2010-01-26
forum: Programming Talk
---

### Post by DiegoTc on 2010-01-26
Hi
I am working on this small application(really small).
I have the followingcvs file name **hola.cvs**
This file has the following information
> 
Diego,Turcios,18
Julian,Turcios,56
Julieta,Turcios,24
Otro,Turcios,56


and the code I am using is this one
```

#include <cstdio>
#include <iostream>
#include <string>
#include <iomanip>
using namespace std;
int main(){
    FILE *arch =0;
    char *buffer=new char [1];
    string hola;
    arch=fopen("hola.cvs","rb");
    int a=0;
    if(arch==0){
        cout<<"Archivo no Existe";
        return 0;
    }
    while(!feof(arch)){
    fread(buffer,1,sizeof(buffer),arch);
    if(buffer[0]!='\n'){
        hola[a]=buffer[0];
        a++;
    }else{
     for(int b=0;b<a;b++){
         if(hola[b]!=',')
            cout<<hola[b];
            else
             cout<<setw(5);
     }
     a=0;

    }

    }
    fclose(arch);

}


```

My idea was to copy a complete line into a string, later print the string and each time a coma appears print a setw of 5 spaces, but it is not working :(

---

### Post by dwhitney67 on 2010-01-26
You probably meant CSV (Comma Separated Value) file?  In Spanish I suppose it would be VSC.

CVS is typically associated with Concurrency Revision System.

Anyhow, in C++, the use of fopen() is generally frowned upon because there are better utilities for opening files.  For example, fstream.

For parsing, you can use the STL string's method find_first_of() to search for a comma.  This will return a position marker that you can then use with the substr() method.  Repeat this until you reach the end of the string.

There is a tokenizer class available with the Boost C++ library, but if you are learning to program (in C++), then I do not recommend you use it at this stage.

---

