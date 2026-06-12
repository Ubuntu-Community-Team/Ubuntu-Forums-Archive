---
title: "Having Troubles to read file in c++"
date: 2010-02-03
forum: Programming Talk
---

### Post by DiegoTc on 2010-02-03
Hi everyone.
I am still playing with files and had some trouble
I have the code in where I write the files to the file
```

#include <iostream>
#include <cstdio>
using namespace std;
int main (){
 FILE *archivo=0;
 archivo=fopen("prueba.dat","a");
 char *name=new char [30];
 int codigo,sueldo,contador,op;
 do{
     cout<<"Ingrese 0 si desea salir y cualquier numero si desea continua";
     cin>>op;
     cout<<"Ingrese codigo: ";
     cin>>codigo;
     cout<<"Ingrese nombre: ";
     cin>>name;
     cout<<"Ingrese sueldo: ";
     cin>>sueldo;
     fwrite(&codigo,1,sizeof(codigo),archivo);
     //fseek(archivo,4,SEEK_SET);
     fwrite(&name,1,sizeof(name),archivo);
     //fseek(archivo,sizeof(name),SEEK_SET);
     fwrite(&sueldo,1,sizeof(sueldo),archivo);
     //fseek(archivo,4,SEEK_SET);

 }while(op!=0);
 fclose(archivo);

}


```
Here it is the code, where I am reading the file. But it doesn't do the code it has to do
```

#include <iostream>
#include <cstdio>
using namespace std;
int main (){
    FILE *archivo=0;
    char *name=new char [30];
    archivo=fopen("prueba.dat","rb");
    int sueldo,codigo;

    while(!feof(archivo)){
        fread(&codigo,1,sizeof(codigo),archivo);
        cout<<codigo<<" ";
        fread(&name,1,sizeof(name),archivo);
        cout<<name<<" ";
        fread(&sueldo,1,sizeof(sueldo),archivo);
        cout<<sueldo<<" ";

    }

    fclose(archivo);



}

```

---

### Post by Zugzwang on 2010-02-03
So first of all, have you checked that the file has been written correctly?

Then, what are the errors that you get? You didn't say what is actually wrong.

Finally, you didn't check whether the calls to "fopen" or "fread" actually succeed. Go and check their return values!

---

### Post by MadCow108 on 2010-02-03
again a typical sizeof misuse

fwrite(&name,1,sizeof(name),archivo);

will give you the size of the pointer 4 and not what you probably want 30
sizeof only works in sizes known to the compiler, that is structures data types and stack!! arrays which have not decayed into pointers
and name is already a pointer, so the & operator is wrong, this is better:
fwrite(name,1,30,archivo);
same bug when reading


also you should open your file in write binary mode wb instead of only w (although I don't really think that matters much)
and c++ has own file functions in the iostream library
its recommended to use these

---

### Post by dwhitney67 on 2010-02-03
@ DiegoTc

Your writing code in C++; thus why not use fstream (and string) for your file writing/reading needs?  It would make your life a lot easier.

For example:
```

#include <fstream>
#include <string>
#include <iostream>

int main()
{
   using namespace std;

   fstream file("prueba.dat", ios::out | ios::app);

   if (file)
   {
      while (true)
      {
         unsigned int numero = 0;
         unsigned int codigo = 0;
         string       name;
         unsigned int sueldo = 0;

         cout << "Entre 0 para terminar, o otro numero para continuar: ";
         cin  >> numero;

         if (numero == 0) break;

         cout << "Ingrese codigo: ";
         cin  >> codigo;

         cout << "Ingrese nombre: ";
         cin  >> name;

         cout << "Ingrese sueldo: ";
         cin  >> sueldo;

         file << codigo << name << sueldo << endl;
      }
   }
   else
   {
      cerr << "No se puede abrir prueba.dat" << endl;
      return -1;
   }

   return 0;
}

```
If you are looking to store the information in binary, then use the ios::binary option when opening the file.  Also, use the write() method.

You can read more about fstream here:
[http://www.cplusplus.com/reference/iostream/fstream/](http://www.cplusplus.com/reference/iostream/fstream/)

---

### Post by DiegoTc on 2010-02-03
Atually the first program works correctly
I can insert all the data I  ask the user.
When I run the second program. It only shows me the first 1 number of the file. Then it stops working

---

### Post by MadCow108 on 2010-02-03
have you fixed the problems I mentioned?
in the unfixed one it obviously will fail after the first fread because the second fwrite/fread combo is wrong, the first one is fine.

---

### Post by DiegoTc on 2010-02-03
@dwhitney67
Yes   I know it that way. But i want to try the cstdio lib.
And what I am seeing is that the file works fine, when it is not reading a string.
SO i think I am making bad the process of reading it, but i can't identify it :(

@MadCow108
Yes I fix it but always the same error

```
#include <iostream>
#include <cstdio>
using namespace std;
int main (){
 FILE *archivo=0;
 archivo=fopen("prueba.dat","wb");
 char *name=new char [6];
 int codigo,sueldo,contador,op;
 do{
     cout<<"Ingrese 0 si desea salir y cualquier numero si desea continua";
     cin>>op;
     cout<<"Ingrese codigo: ";
     cin>>codigo;
     cout<<"Ingrese nombre: ";
     cin>>name;
     cout<<"Ingrese sueldo: ";
     cin>>sueldo;
     fwrite(&codigo,1,sizeof(codigo),archivo);
     fwrite(&sueldo,1,sizeof(sueldo),archivo);
     fwrite(&name,1,6,archivo);

 }while(op!=0);
 fclose(archivo);

}
```
And the second program it will be like this
```
#include <iostream>
#include <cstdio>
using namespace std;
int main (){
    FILE *archivo=0;
    char *name=new char [6];
    archivo=fopen("prueba.dat","rb");
    int sueldo,codigo;

    while(!feof(archivo)){
        fread(&codigo,1,sizeof(codigo),archivo);
        cout<<codigo<<" ";
        fread(&sueldo,1,sizeof(sueldo),archivo);
        cout<<sueldo<<" ";
        fread(&name,1,6,archivo);
        cout<<name<<" ";

    }

    fclose(archivo);



}
```

So i am still wondering which one is the problem :S

---

### Post by MadCow108 on 2010-02-03
edit:
you still have the & operator to much for the string

its not needed for the pointer, as it already is a pointer

```

char *name=new char [6];
fwrite(&name,1,6,archivo);

```

here you try to write 6 bytes from the address of the name pointer to the file, the location the address of name points to only holds 4 bytes (or 8bytes on 64 bit systems) because name is a pointer already
you want to write the 6 bytes name points to:
fwrite(name,1,6,archivo);

---

### Post by DiegoTc on 2010-02-03
@MadCow108 Sorry i click in reply with out copying.
The problem still continue.
It only prints the "codigo" and the "salario", when it has to print the name the program stops running

---

### Post by MadCow108 on 2010-02-03
your exact same code with the corrected & works on my system
(except it prints twice because feof only gets set on the second iteration with the reads failing then)

maybe use valgrind on it to pinpoint your problem
(the uninitialized syscall error you'll get is superfluous in this simple case, make it disappear by initializing your string buffer)

---

### Post by DiegoTc on 2010-02-03
@MadCow108 thans for telling me that. Right i am using codeblocks in windows on my and it is the second time it happens this. It may be the version. I will try it on my laptop with ubuntu and codeblocks

---

### Post by lisati on 2010-02-03
For the first program, where are you setting the value of 'op'?

---

### Post by MadCow108 on 2010-02-03
are you maybe using a to long string?
your buffer is only 6 bytes long
that means it only takes 5 characters!
you also need room for the null termination to print the cstring correctly

---

### Post by DiegoTc on 2010-02-03
nop the string is "abc"
Si i think it is the codeblocks that is failing. One friend of my tells me he has the same trouble with codeblocks in windows

---

### Post by Zugzwang on 2010-02-03
It's highly unlikely that CodeBlocks is failing as it is only an IDE and no compiler. Try running your program with valgrind, as suggested, and see what comes out. Also *do* check the return values of fopen and fread, as the behaviour you mention suits to the case in which the last read operation fails. In that case, "name" stays uninitialised which might result in a program crash.

Also try using a hex editor to see if the generated file looks as expected.

---

### Post by dwhitney67 on 2010-02-03
> **DiegoTc said:**
> @dwhitney67
Yes   I know it that way. But i want to try the cstdio lib.
And what I am seeing is that the file works fine, when it is not reading a string.
SO i think I am making bad the process of reading it, but i can't identify it :(


Haga lo que quieres.

The problem you may be having is with writing the binary data to the file.

Here's two working programs, the first that writes the data, the second that reads it in.

writer.cpp:
```

#include <iostream>
#include <cstdio>

int main()
{
   using namespace std;

   FILE* archivo = fopen("prueba.dat", "a");

   if (archivo)
   {
      while (true)
      {
         unsigned int codigo, sueldo, op;
         char         nombre[6] = {0};

         cout << "Ingrese 0 si desea salir, o cualquier otro numero si desea continuar: ";
         cin  >> op;

         if (op == 0) break;

         cout << "Ingrese codigo: ";
         cin  >> codigo;
         cin.ignore(1024, '\n');   // clear the input stream before continuing

         cout << "Ingrese nombre: ";
         cin.read(nombre, sizeof(nombre) - 1);
         cin.ignore(1024, '\n');

         cout << "Ingrese sueldo: ";
         cin  >> sueldo;
         cin.ignore(1024, '\n');

         fwrite(&codigo, 1, sizeof(codigo), archivo);
         fwrite(nombre,  1, sizeof(nombre), archivo);
         fwrite(&sueldo, 1, sizeof(sueldo), archivo);
      }

      fclose(archivo);
   }
   else
   {
      cerr << "Error abriendo prueba.dat" << endl;
      return -1;
   }

   return 0;
}

```

reader.cpp:
```

#include <iostream>
#include <cstdio>

int main()
{
   using namespace std;

   FILE* archivo = fopen("prueba.dat", "r");

   if (archivo)
   {
      while (true)
      {
         unsigned int codigo, sueldo;
         char         nombre[6] = {0};

         fread(&codigo, 1, sizeof(codigo), archivo);
         fread(nombre,  1, sizeof(nombre), archivo);
         fread(&sueldo, 1, sizeof(sueldo), archivo);

         if (feof(archivo)) break;

         cout << "codigo: " << codigo << "\n"
              << "nombre: " << nombre << "\n"
              << "sueldo: " << sueldo << "\n"
              << endl;
      }

      fclose(archivo);
   }
   else
   {
      cerr << "Error abriendo prueba.dat" << endl;
      return -1;
   }

   return 0;
}

```

---

