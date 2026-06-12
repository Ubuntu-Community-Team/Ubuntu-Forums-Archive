---
title: "C++ Segmentation Fault"
date: 2010-12-15
forum: Programming Talk
---

### Post by Roberto_Lapuente on 2010-12-15
Im tring to read a text file but when i want to do this with an object of the class it gives me a segentation fault, what am i doing wrong? 
please help.

the main method
```
int main()
{
    Embeded embeded;
    embeded.setArchivoConfig("conf/conf.asc");

    embeded.loadConfig();

    cout << embeded.getIP();
}
```

loadConfig() in embeded class
```
void Embeded::loadConfig()
{
    vector<string> archivo;
    File file(archivoConfig);
    if(stop())
    {
        archivo = file.read();

        setID(archivo.front());
        archivo.erase(archivo.begin());

        setIP(archivo.front());
        archivo.erase(archivo.begin());

        setPORT(archivo.front());
        archivo.erase(archivo.begin());

        setCONF(atoi(archivo.front().c_str()));
        archivo.erase(archivo.begin());

        setTIME(atoi(archivo.front().c_str()));
        archivo.erase(archivo.begin());

        if(!start())
        {

        }
    }
}

```

the code form File class
Constructor```

File::File(string archivo)
{
    archivoObjeto = archivo;
}
```

Read
```
vector<string> File::read()
{
    return read(archivoObjeto, true);
}

vector<string> File::read(string archivo, bool comentarios)
{
    string lectura, resultado;
    vector<string> lineas;
    ifstream reader(archivo.c_str());

    // Hasta que sea el final del archivo
    if(reader.is_open())
    {
        while(!reader.good())
        {
            // Lee una linea y la guarda en lectura
            getline(reader,lectura);
            if (lectura.compare("\n") != 0)
            {
                // Si no quieres discriminar comentarios agrega todas las lineas a un string
                if (!comentarios)
                {
                    lineas.push_back(lectura);
                }
                else if (lectura[0] != '#')
                {
                    // Si quieres discriminar comentarios deja afuera las lineas que empiezan con #
                    lineas.push_back(lectura);
                }
            }
        }
        reader.close();
    }
    else
    {
        reader.close();
        exit(1);
    }
    return lineas;
}
```

---

### Post by Arndt on 2010-12-15
> **Roberto_Lapuente said:**
> Im tring to read a text file but when i want to do this with an object of the class it gives me a segentation fault, what am i doing wrong? 
please help.



I suggest you compile with -g and use gdb to see where the program crashes.

Like this:

```
$ g++ -g -o crash crash.c
$ gdb crash
GNU gdb (GDB) 7.0-ubuntu
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/arndt/tmp/crash...done.
(gdb) r
Starting program: /home/arndt/tmp/crash 

Program received signal SIGSEGV, Segmentation fault.
0x0804849a in g (p=0x80484eb "\201\303\t\033") at crash.c:3
3	    *p = 'a';
Current language:  auto
The current source language is "auto; currently c++".
(gdb) bt
#0  0x0804849a in g (p=0x80484eb "\201\303\t\033") at crash.c:3
#1  0x080484b0 in f (a=1) at crash.c:10
#2  0x080484c4 in main () at crash.c:15
(gdb)
```

(I see nothing directly obvious in your code, but I didn't read _that_ closely.)

---

### Post by dwhitney67 on 2010-12-15
I would rewrite the following:
```

...
// Hasta que sea el final del archivo
if(reader.is_open())
{
   while(!reader.good())
   {
      // Lee una linea y la guarda en lectura
      getline(reader,lectura);
      ...
   }
   ...
}
...

```

to be:
```

...
// Verifique el archivo de informacion esta abierto
if(reader)
{
   // hasta que hay lineas de informacion...
   while(getline(reader, lectura))
   {
      // procesar la informacion en lectura
      ...
   }
}

```

Remove the close() calls that you make; they are superfluous in the context you are using them.  The file will be automatically closed when the ifstream object goes out of scope.

---

### Post by Roberto_Lapuente on 2010-12-15
ok, i found the problem but i have a new one. The problem was that ifstream .good() is always false an i was trying to acces nonallocated memory space. 

Now, someone knows why it isnt good?

---

### Post by Roberto_Lapuente on 2010-12-15
Ok, got it. I cannot believe i did not see this. The while was set on !good()

---

### Post by dwhitney67 on 2010-12-15
> **Roberto_Lapuente said:**
> Ok, got it. I cannot believe i did not see this. The while was set on !good()

If you proceed with the approach of using good() as your conditional in your while-loop, you *may* end up with one additional string in your vector, but only if "comentarios" is set to false.  The reason is because good() will not report false until you reach the end of the file; the only way you reach EOF is when the getline() fails.

---

