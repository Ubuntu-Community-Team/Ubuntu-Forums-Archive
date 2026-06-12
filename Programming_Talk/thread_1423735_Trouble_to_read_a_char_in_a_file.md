---
title: "Trouble to read a char* in a file"
date: 2010-03-07
forum: Programming Talk
---

### Post by DiegoTc on 2010-03-07
Hi guys
I am having troubles to read a char* from a file. Each time it reads me it prints garbage values :(

Here is the code

```

char * Columnas::convertir(string name)
{
    int longi = name.length();
	char *name1 = new char[longi + 1];
	name.copy(name1,longi,0);
	name1[longi] = '\0';
	return name1;
}

void Columnas::Save(FILE *archivo)
{
    int quetipo;
    char *whichName;
    string na1;
    bool option1;
    int sizevector=(int)Tipo.size();


    for(int i=0;i<sizevector;i++){
        quetipo=Tipo.at(i);
        na1=ColumnName.at(i);
        cout<<"Este es como string: "<<na1<<'\n';
        whichName=convertir(na1);
        cout<<"Este es como char: "<<whichName<<'\n';
        option1=Primaria.at(i);

        fwrite(&quetipo,sizeof(int),1,archivo);
        fwrite(whichName,20,1,archivo);
        fwrite(&option1,sizeof(bool),1,archivo);
    }

    cout<<"Archivo Guardado con Exito\n";
}

void Columnas::Load(FILE *archivo)
{
    int quetipo;
    string na1;
    char *whichName;
    bool option1;

    while(!feof(archivo)){
        fread(&quetipo,sizeof(int),1,archivo);
        fread(whichName,20,1,archivo);
        fread(&option1,sizeof(bool),1,archivo);
        cout<<quetipo<<"  "<<whichName<<'\n';
    }
}

```

Thanks :D

---

### Post by MadCow108 on 2010-03-07
why are you using C methods in C++?
use C++ streams, their easier.


your problem is this:
```
char *whichName;
    while(!feof(archivo)){
...
        fread(whichName,20,1,archivo);
...
    }

```
no buffer space...


also the string class has the c_str method which returns a cstring.
So you don't need your convert method in this case.

---

### Post by DiegoTc on 2010-03-07
So that means I have to write it like this?

```

        string na1;
        na1=ColumnName.at(i);
        fwrite(na1.c_str(),20,1,archivo);


```

and for reading it
I have to declared a const char 

```
const char *whichName=na1.c_str();
fread(whichName,20,1,archivo);
```

---

### Post by dwhitney67 on 2010-03-07
DiegoTC

I think MadCow108 was asking the more "generic" question as to why you are mixing C constructs with C++.

Do not use fopen(); use std::fstream

For example:
```

#include <fstream>
#include <iostream>

int main()
{
   std::fstream out("data.dat", std::ios::out | std::ios::binary);

   if (out)
   {
      int num1 = 10;
      int num2 = 20000;

      out.write(reinterpret_cast<const char*>(&num1), sizeof(num1));
      out.write(reinterpret_cast<const char*>(&num2), sizeof(num2));

      out.close();
   }

   std::fstream in("data.dat", std::ios::in | std::ios::binary);

   if (in)
   {
      int num1 = 0;
      int num2 = 0;

      in.read(reinterpret_cast<char*>(&num1), sizeof(num1));
      in.read(reinterpret_cast<char*>(&num2), sizeof(num2));

      in.close();

      std::cout << num1 << "\t" << num2 << std::endl;
   }
}

```

Btw, if you are writing/reading basic data types (including the STL string), then use the overloaded operator<<() or operator>>() methods as necessary.

For example:
```

std::fstream in("myfile.txt", std::ios::in);
std::string  str;
int          num;

in >> str >> num;

```

Or for outputting:
```

std::string  nombre("dwhitney67");
int          edad = 67;
std::fstream out(myfile.txt", std::ios::out);

out << nombre << "," << edad << std::endl;

```

---

### Post by MadCow108 on 2010-03-07
no you can't use the buffer of a string class directly.
```

char buffer[20];
// or
char * buffer = new char[20];

fread(buffer,20,1,archivo);
buffer[19] = '\0'; // just to make sure its null terminated
string str(buffer); // make it more 'C++esque'

```

for writing you should make sure your string is 20 bytes long, else you should stop at the end and pad the rest with something 
```

fwrite(na.c_str(), na.length(), 1 ,fd);
for(int i=0; i<20-na.length(); i++)
  fputc(0,fd);

```

(or stick with your convert method but fix the buffer overflow while null terminating)
(or write the length of the string into the file too)

and please have a look at the C++ file handling methods and consider to use these.

---

### Post by DiegoTc on 2010-03-07
Thanks problem solved

---

