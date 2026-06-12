---
title: "Editing a binary file (C/C++)"
date: 2008-07-12
forum: Programming Talk
---

### Post by Yacoby on 2008-07-12
Heya

I have a binary file, and I want to edit some data within it. Is there any way I can edit it. I always seem to manage to either truncate the file, or append data to the end of the file

Regards,
Yacoby

---

### Post by Vadi on 2008-07-12
Either use a hex editor, or edit the source and recompile.

---

### Post by Yacoby on 2008-07-12
> **Vadi said:**
> Either use a hex editor, or edit the source and recompile.

Sorry, I don't think I was clear.

I have a program, that takes a given binary file, checks some data exists within it.
I then need to replace that data. However, as the file may be 100 - 300mb, I am unwilling to load it all into memory.

I was wondering if anyone knew if it was possible, and if so, how to do it.

---

### Post by rbprogrammer on 2008-07-12
Well, as long as you know the format of how the file is arranged, you could open it almost like any other file.

Try looking at this website [http://www.cplusplus.com/](http://www.cplusplus.com/)
Now since reading and writing files in C is different than C++, i have websites that can help with either language you want to use:
**C**: [http://www.cplusplus.com/reference/clibrary/cstdio/fopen.html](http://www.cplusplus.com/reference/clibrary/cstdio/fopen.html)
**C++**: [http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html)

---

### Post by Yacoby on 2008-07-12
But when I do this, the file gets truncated:
```
			std::ofstream ofs(file.c_str(), std::ios::binary | std::ios::out);
			ofs.seekp(4);

			for ( int y = 0; y < 512; ++y){
				for ( int x = 0; x < 512; ++x){
					ofs.write((char*)&x, 1);
				}
			}
			ofs.close();
			return;
```

or else the data gets appended to the end of the file:
```
			std::ofstream ofs(file.c_str(), std::ios::binary | std::ios::out | std::ios::app);
			ofs.seekp(4);

			for ( int y = 0; y < 512; ++y){
				for ( int x = 0; x < 512; ++x){
					ofs.write((char*)&x, 1);
				}
			}
			ofs.close();
			return;
```

I may go the hacky way, and read all the data *shrugs*

---

### Post by dwhitney67 on 2008-07-12
Do you know the format of the file?  Is it record-based?

If so, then open the file, find the record of interest, then poke the value into the appropriate field within the file-stream.  It's not rocket science. :-)

Here's an example, where a binary file is created, and subsequently, a field within it is changed:
[PHP]#include <cstdlib>    // for srand(), rand()
#include <fstream>
#include <iostream>


struct Record
{
  uint32_t field1;      // 4 bytes
  uint32_t field2;      // 4 bytes
  uint64_t field3;      // 8 bytes

  friend std::ostream& operator<<( std::ostream &os, const Record &rec )
  {
    os << "( 0x" << std::hex << rec.field1 << ", 0x"
                 << std::hex << rec.field2 << ", 0x"
                 << std::hex << rec.field3 << " )";
    return os;
  }
};


int main()
{
  srand( time(0) );

  // Open binary file for writing...
  //
  std::fstream ofs( "./myBinaryFile", std::ios::out | std::ios::binary );

  if (ofs)
  {
    // Add 10 records of data to the file...
    //
    for ( unsigned int i = 0; i < 10; ++i )
    {
      Record rec = { rand() % 100, rand() % 100, rand() % 100 };

      std::cout << "Writing Record " << i << " = " << rec << std::endl;

      ofs.write( (const char *)&rec, sizeof(Record) );
    }

    ofs.close();
  }


  std::cout << "Pause to  examine the myBinaryFile's contents using 'od -A d -x -v'" << std::endl;
  std::cout << "Press ctrl-d to continue..." << std::endl;
  char enter;
  std::cin >> enter;


  // Reopen the binary file so that data can be changed...
  //
  std::fstream ofs2( "./myBinaryFile", std::ios::in | std::ios::out | std::ios::ate | std::ios::binary );

  if (ofs2)
  {
    // Move the file pointer back to the third record, relative from the beginning of
    // the file.  The first record is at position 0; the second record at 1, the third at 2, etc.
    //
    ofs2.seekp( 2 * sizeof(Record), std::ofstream::beg );

    // Get the record
    //
    Record rec;
    ofs2.read( (char *) &rec, sizeof(Record) );

    // Reset the file pointer (again)
    //
    ofs2.seekp( 2 * sizeof(Record), std::ofstream::beg );

    // adjust the value(s)
    //
    rec.field2 = 0xBEEFCAFE;

    // write the adjusted data record to the file
    //
    std::cout << "Replace record 3 with: " << rec << std::endl;
    ofs2.write( (const char *)&rec, sizeof(Record) );

    ofs2.close();
  }

  return 0;
}[/PHP]
I hope this helps!

---

### Post by Yacoby on 2008-07-13
@dwhitney67
Thanks, I think I was forgetting the std::ios::in parameter in std:: ofstream:: ofstream

Many thanks.

---

### Post by pradeepthundiyil on 2012-09-13
Working Code.. 

This code replaces a string (OLD-STRING) in cout.exe with new string (NEW-STRING). 

#include "stdafx.h"
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main(int argc, char *argv[])
{
  fstream ifs;
  ifs.open ("C:\\Users\\user\\Desktop\\cout.exe", fstream::binary | fstream::in | fstream::out);

  std::string str((std::istreambuf_iterator<char>(ifs)), std::istreambuf_iterator<char>());

  size_t pos = str.find("OLD-STRING");

  if (pos != string::npos)
  {
    cout << "string found at position: " << int(pos) << endl;

    ifs.seekp(pos);

    ifs.write("NEW-STRING", 10);

  }
  else
  {
    cout << "could not find string" << endl;
  }

  if (ifs.is_open())
    ifs.close();

  return 0;
}

---

### Post by sisco311 on 2012-09-13
Old thread closed.

---

