---
title: "how to read binary .o files ??"
date: 2007-09-11
forum: Programming Talk
---

### Post by Elisei on 2007-09-11
hehe ; oh ... i am stuck again;

i need to open a .o file and read it in such a way that i could convert each raw o and 1 into ascii 0 and 1; 
the trick is i need to read in 16 bits at a time for which i am using something like this:

objectFile.read((char *) &word[codeAddress], sizeof(short));

while going through a .o file;

the problem is that it gives me decimal values; i then bit shift them to get binary equivalent, but they just dont match to what i need - according to a given certain ISA;

can somebody please give me hint on how to read .0 files 1 bit a t a time  or something like that so i could understand what the raw content of my .o file is;

---

### Post by geraldm on 2007-09-11
man od
man hexdump
To look at the symbols use 
nm {filename.o}

Gerald

---

### Post by bashologist on 2007-09-11
> **geraldm said:**
> man od
man hexdump
To look at the symbols use 
nm {filename.o}

Gerald
That last one doesn't work. ;_;
```
foo@bar:~$ Gerald
bash: Gerald: command not found
```

---

### Post by Lux Perpetua on 2007-09-11
> the problem is that it gives me decimal values; i then bit shift them to get binary equivalent, but they just dont match to what i need - according to a given certain ISA;I don't understand. How is that giving you "decimal values"? > ```
foo@bar:~$ Gerald
bash: Gerald: command not found
``````
sudo apt-get install Gerald
```;)

---

### Post by dwhitney67 on 2007-09-12
> **Elisei said:**
> hehe ; oh ... i am stuck again;

i need to open a .o file and read it in such a way that i could convert each raw o and 1 into ascii 0 and 1; 
the trick is i need to read in 16 bits at a time for which i am using something like this:

objectFile.read((char *) &word[codeAddress], sizeof(short));

while going through a .o file;

the problem is that it gives me decimal values; i then bit shift them to get binary equivalent, but they just dont match to what i need - according to a given certain ISA;

can somebody please give me hint on how to read .0 files 1 bit a t a time  or something like that so i could understand what the raw content of my .o file is;

It seems that you were looking for a programatical way to print the "ones" and "zeros" of a binary file.  Here's a simple example:

[PHP]#include <iostream>
#include <fstream>

using namespace std;


void displayShort( unsigned short* value )
{
  unsigned int mask = 0x8000;

  for ( int i = 0; i < 16; ++i )
  {
    int bit = *value & mask ? 1 : 0;
    cout << bit;
    mask >>= 1;
  }
  cout << endl;
}

int main( int argc, char** argv )
{
  if ( argc != 2 )
  {
    cout << "Usage: " << argv[0] << " <.o filename>" << endl;
    exit( 1 );
  }

  ifstream input( argv[1], ios::in | ios::binary );

  while ( ! input.eof() )
  {
    char buf[2] = { 0 };

    input.read( buf, sizeof( buf ) );

    displayShort( (unsigned short*) buf );
  }
}[/PHP]

Enjoy!

---

### Post by Elisei on 2007-09-12
it works thank you very much; simplest way is always the best; (mine worked too i just realized but didn't see an endian problem);

i shall call this program Gerald for anyone who wants to get it;:D

---

