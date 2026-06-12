---
title: "Problems with Files in C++"
date: 2010-01-14
forum: Programming Talk
---

### Post by DiegoTc on 2010-01-14
Hi everyone, I am working on trying a small file program.
Only add numbers from keyboard and later saved them on an array.
Just for starting I am using an array, but when I write the file, and read it, they appear some stranges numbers. The array is of size 5. And it has 8 numbers the file

Here is the code
> 
void leer(int arr[],int op){
        if(op==1){
        FILE *arch=0;
        arch=fopen("archivo.gedit","wb");
        fwrite(&arr,1,sizeof(arr),arch);
        fclose(arch);
        }
        else if(op==2){
         FILE *arch=0;
         arch=fopen("archivoB.gedit","wb");
         fwrite(&arr,1,sizeof(arr),arch);
         fclose(arch);
        }
        else if(op==3){
          FILE *arch=0;
          arch=fopen("archivoC.gedit","wb");
          fwrite(&arr,1,sizeof(arr),arch);
          fclose(arch);
        }
    }

    void escribir(int arr[],int op){
        if(op==1){
        FILE *arch=0;
        arch=fopen("archivo.gedit","rb");
        if(arch==0){
         cout<<"Error";
        }
        fread(&arr,1,sizeof(arr),arch);
        fclose(arch);
        cout<<"Estos son los del A \n";
        for(int a=0;a<sizeof(arr);a++)
        cout<<arr[a]<<" ";
        cout<<"\n";
        }

        else if(op==2){
        FILE *arch=0;
        arch=fopen("archivoB.gedit","rb");
        if(arch==0){
         cout<<"Error";
        }
        fread(&arr,1,sizeof(arr),arch);
        fclose(arch);
        cout<<"Estos son los del B \n";
        for(int a=0;a<sizeof(arr);a++)
        cout<<arr[a]<<" ";
        cout<<"\n";

        }

        else if(op==3){
            FILE *arch=0;
            arch=fopen("archivoC.gedit","rb");
            if(arch==0){
                cout<<"Error";
            }
            fread(&arr,1,sizeof(arr),arch);
            fclose(arch);
            cout<<"Estos son los del C \n";
            for(int a=0;a<sizeof(arr);a++)
            cout<<arr[a]<<" ";
            cout<<"\n";

        }

    }

int main(){
    int op,contA=0,contB=0,dato,datos;
    archivos practica;
    int arrA[5];
    int arrB[5];
    int arrC[100];

    do{
        cout<<"-------Menu--------\n";
        cout<<"1. Data to FileA\n";
        cout<<"2. Data to File B\n";
        cout<<"3. Read Data from File A and B\n";
        //cout<<"4. Mostrar Nuevos Datos\n";
        cout<<"5. Salir\n";
        cin>>op;

        if(op==1){
          if(contA<5){
              cout<<"Ingrese numero: ";
              cin>>arrA[contA];
              contA++;
              datos=op;
          }
        }
        else if(op==2){
            if(contB<5){
                cout<<"Ingrese numero: ";
                cin>>arrB[contB];
                contB++;
                datos=op;
            }
        }

        else if(op==3){
            practica.leer(arrA,1);
            practica.leer(arrB,2);
            practica.escribir(arrA,1);
            practica.escribir(arrB,2);
        }
    }while(op!=5);

}



If i write these number on the arrys it prints me this:
File A={1}
It tell me the file has the following numbers=1,32570,4198688,0,0,0,2,0
FIle B={3,4,5,6}
It tell me the file has the following numbers=3,4,5,6,2081045584,4198757,0

---

### Post by MadCow108 on 2010-01-14
please format the code in code tags

your probably overrunning some boundaries.
compile it with -g and run it with valgrind
this will give you very good hints to the problem

one thing I've seen on a very quick glace at this spaghetti is a _possible_ wrong use of sizeof
arrays when passed into function decay into pointers! sizeof only gives the correct size (in bytes) if applied to arrays in the same stack frame
So sizeof(arr) gives you the the size of an int pointer (mostly 4 or 8 bytes) and NOT the size of the array!
check this first.

---

### Post by DiegoTc on 2010-01-14
> **MadCow108 said:**
> please format the code in code tags

[QUOTE=MadCow108;8663122]
one thing I've seen on a very quick glace at this spaghetti is a _probably_ wrong use of sizeof
arrays when passed into function decay into pointers! sizeof only gives the correct size (in bytes) if applied to arrays in the same stack frame
So sizeof(arr) gives you the the size of an int pointer (mostly 4 or 8 bytes) and NOT the size of the array!
check this first.

So instead of using sizeof(arr), I should use the number because i know its size. It a int array of 5. So I should put 20(5*4)

> **MadCow108 said:**
> please format the code in code tags
 
PS. Sorry because of that.

---

### Post by DiegoTc on 2010-01-14
Okay I find my problem

```

void leer(int arr[],int op){
        if(op==1){
        FILE *arch=0;
        arch=fopen("archivo.gedit","wb");
        fwrite(&arr,1,20,arch);
        fclose(arch);
        }
}        


```

This is the function where I am writing the values of the array into the file.

```
void escribir(int op){
        if(op==1){
            int arr[5];

            FILE *arch=0;
            arch=fopen("archivo.gedit","rb");
             if(arch==0){
                cout<<"Error";
             }
            fread(&arr,1,20,arch);
            fclose(arch);
            cout<<"Estos son los del A \n";
            for(int a=0;a<5;a++)
                cout<<arr[a]<<" ";
     
        }
}
``` 

This is the function were I am reading the file.
I supossed the file has open, and read. But when I do a cout to show what does the file has. It shows me strange numbers.

Still wondering why? :(

---

### Post by nmccrina on 2010-01-14
Since you are using C++, you might want to look at the fstream library. It is the "C++ Way" of doing file I/O. A skeleton program would look like this:

```

#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    ofstream fout; //this is like cout, but it writes to a file
    fout.open("output.txt");

    // Do stuff, like fout << 5; fout << "Hi!";

    fout.close();
    return 0;
}

```

[cplusplus.com]("http://www.cplusplus.com/reference/iostream/fstream/") has a lot more information.

---

### Post by MadCow108 on 2010-01-14
I guess you want to write your array into the file.
remember: arrays decay into pointers automatically in many cases.
mostly you can say: basically an array is a pointer, because it behaves like one

so this won't work as expected
fread(&arr,1,20,arch);
fwrite the same

fread/fwrite expects a pointer to data and writes 20 bytes from that pointer
arr is a pointer to data spanning 20 bytes
but &arr is a pointer to a pointer spanning 4 bytes, so it writes a pointer and 16 garbage bytes into the file

fread(arr,1,20,arch);
fwrite...
could work

---

