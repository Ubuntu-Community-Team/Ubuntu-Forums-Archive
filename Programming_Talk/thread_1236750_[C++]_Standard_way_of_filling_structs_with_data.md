---
title: "[C++] Standard way of filling structs with data"
date: 2009-08-10
forum: Programming Talk
---

### Post by Drone022 on 2009-08-10
What is ***the*** standard way of reading data from a binary file and sticking it in a struct in C++, everywhere I look people seem to do it different ways. I dont want to read into an array first, I want it to go straight to the struct.


This doesnt seem to work...
```

typedef struct header {
	unsigned short blah;
	int blah2;
	unsigned short blah3;
	unsigned short blah4;
	int blah 5;
}THE_STRUCTURE;



int main () {

	THE_STRUCTURE structure;

  ifstream file ("myfile.format", ios::in|ios::binary|ios::ate);
  if (file.is_open())
  {
    size = file.tellg();
    file.seekg (0, ios::beg);
    file.read (reinterpret_cast<char *>(&structure), sizeof(structure));

}


```

Something of that nature seems to give me incorrect values, isnt there something nicer than forcing the pointer cast like that?

Also, just checking, sizeof(struct) will always be a 2^n value?

---

### Post by Npl on 2009-08-10
> **Drone022 said:**
> What is ***the*** standard way of reading data from a binary file and sticking it in a struct in C++, everywhere I look people seem to do it different ways. I dont want to read into an array first, I want it to go straight to the struct.


This doesnt seem to work...
```

typedef struct header {
	unsigned short blah;
	int blah2;
	unsigned short blah3;
	unsigned short blah4;
	int blah 5;
}THE_STRUCTURE;



int main () {

	THE_STRUCTURE structure;

  ifstream file ("myfile.format", ios::in|ios::binary|ios::ate);
  if (file.is_open())
  {
    size = file.tellg();
    file.seekg (0, ios::beg);
    file.read (reinterpret_cast<char *>(&structure), sizeof(structure));

}


```

Something of that nature seems to give me incorrect values, isnt there something nicer than forcing the pointer cast like that?

Also, just checking, sizeof(struct) will always be a 2^n value?Since C leaves alot implementation details to the compiler there is no standard way of doing what you want.
first, the structures can be packed differently on different compilers/architectures(/even different versions of the same compiler). eg. alot of them will add a 2 byte padding after "blah" to bring blah2 to a multiple-of-4 offset.
You have some compiler specific extensions to counter that (#pragma packed in MSVC, attribute(packed) in gcc) 

and then there`s the endianess-problem.

and sizeof struct will usually be a multiple of the "biggest component" - sizeof(int) in your case.

---

### Post by dwhitney67 on 2009-08-10
I agree, there really is no standard way to read/write the data because there are various ways to do it.  Some folks who write C++ code actually use the C library, others such as yourself have attempted to use the C++ library.  Take it step further and consider using the Boost library (see [here]("http://www.boost.org/doc/libs/1_39_0/libs/serialization/doc/index.html") for documentation).

Here's a working example using "regular" C++:
```

#include <fstream>
#include <iostream>
#include <iomanip>

#pragma pack(1)
struct Data
{
   int  field1;
   int  field2;
   char field3;

   friend std::ostream& operator<<(std::ostream& os, const Data& data)
   {
      os << data.field1 << " "
         << data.field2 << " "
         << std::hex << std::setw(2) << std::setfill('0') << (unsigned int) data.field3 << std::dec;
      return os;
   }
};
#pragma pack(0)

int main()
{
   // opening file for output
   std::fstream outfile("binary.dat", std::ios::out | std::ios::binary);

   if (outfile)
   {
      std::cout << "Writing data to binary file..." << std::endl;
      for (size_t i = 0; i < 10; ++i)
      {
         Data data = { i+100, i+2000, i };

         std::cout << data << std::endl;

         outfile.write(reinterpret_cast<const char*>(&data), sizeof(data));
      }

      outfile.close();
   }
   std::cout << std::endl;


   // opening file for input
   std::fstream infile("binary.dat", std::ios::in | std::ios::binary);

   if (infile)
   {
      // find the number of records in the file
      infile.seekg(0, std::ios::end);
      const size_t numRecords = infile.tellg() / sizeof(Data);
      infile.seekg(0, std::ios::beg);

      std::cout << "Reading data from binary file..." << std::endl;
      for (size_t i = 0; i < numRecords; ++i)
      {
         Data data;
         infile.read(reinterpret_cast<char*>(&data), sizeof(data));

         std::cout << data << std::endl;
      }
   }
}

```

Note that in the example presented above, the data is stored in machine-dependent format, which in the case of my Intel architecture, is Little Endian.  Typically it is wise to encode the data in Big Endian format when the data will be sent to another machine, simply because that is a commonly accepted, yet unwritten, standard.

In conclusion, do not treat the example above as the defacto way to do things.  Some may argue that it is best to read/write each individual field to the file, as opposed to the entire structure in one attempt.  Once again, this is not standardized because the needs of one application may differ from another.

---

### Post by Reiger on 2009-08-10
> **dwhitney67 said:**
> Typically it is wise to encode the data in Big Endian format when the data will be sent to another machine, simply because that is a commonly accepted, yet unwritten, standard.

Except of course that Big Endian is how you treat the data during computations in the first place (e.g.: "<<" is called *left* shift) and that Big Endian is more human readable (because the data will be a consistent sequence format (fully left-to-right): 0xfcd0 will be 0xfc 0xd0, as opposed to 0xd0 0xfc).

---

### Post by Habbit on 2009-08-10
Reiger, the advantages depend on whose perspective you're looking for:
```

#include <cstdint>
#include <iostream>
int main() {
    using namespace std;
    uint64_t val64 = 42;
    uint32_t val32 = *reinterpret_cast<uint32_t*>(&val64);
    uint16_t val16 = *reinterpret_cast<uint16_t*>(&val64);
    uint8_t  val8  = *reinterpret_cast<uint8_t *>(&val64);
    cout << val64 << " " << val32 << " " << val16 << " " << val8  << endl;
}
```
This code will output "42 42 42 42" on a little-endian machine, and "42 0 0 0" on a big-endian machine. Particularly in assembler, these "nifty" tricks are common.

---

### Post by johnl on 2009-08-10
Cannot comment on the 'C++' way to do it, but in C it is common to do exactly as you wrote, and read the entire struct at once.

dwhitney pointed out some of the shortcomings of this (endianess, padding), but these can be overcome fairly easily.

1. specify the alignment of any structures to be used with the __attribute__((packed)) or #pragma pack directives

2. specify what byte order the file should be stored as
-or-
3. allow the file to be stored in either byte order and encode which order is used into the file.

#3 is interesting because it means there is no performance hit loading a file on the same architecture it was created on, but it is still possible to read/write across architectures.  You can see any example of this in the PCAP file format, which requires the first value in the file header to written as '0xA1B2C3D4' in the host byte order.

If the reading program reads it backwards '0xD4C3B2A1' it knows that the byte order of the file is different than the host byte order and should be converted.

---

### Post by Drone022 on 2009-08-12
Thanks for the replies guys, I looked into the #pragma pack directive and it seems to work well. 

Very much appreciated.

---

### Post by dribeas on 2009-08-12
If you don't have limitations on the libraries you use try boost::serialization. The problem with direct binary dump is that the types you are using don't have fixed sizes. That is, 'unsigned short' usually is but does not have to be, 16 bits and 'int' usually is 32 bits, but it does not need to. Else, use C99 (and future C++0x) fixed size types (uint16_t, int32_t)

---

