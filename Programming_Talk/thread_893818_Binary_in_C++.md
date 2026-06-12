---
title: "Binary in C++"
date: 2008-08-18
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-08-18
I have successfully been able to convert data to binary (array of bool).

But how would i convert it back, or is their another way to use binary

my binary converter (obviously not for custom classes)
[PHP]template <class T>
bool* toBinary(T n) {
	int max = sizeof(T)*8;
	bool * bin = new bool[max];
	
	for (int i=max-1;i>-1;i--) {
		bin[i] = n%2;
		n = n >> 1;
	}
	
	return bin;
}

template <class T>
bool* toBinary(T * n, int length) {
	int max = sizeof(T)*8;
	bool * bin = new bool[max*length];
	bool * tmp;
	for (int i0=0;i0<length;i0++) {
		tmp = toBinary<T>(n[i0]);
		for (int i1=0;i1<max;i1++) {
			bin[i0*max+i1] = tmp[i1];
		}
		delete[] tmp;
	}
	return bin;
}[/PHP]

---

### Post by dribeas on 2008-08-18
What do you want to achieve? What's the purpose of converting from/to binary in your case? What you can and cannot do in binary depends on what you want to do with the data at hand.

   David

---

### Post by Mr.Macdonald on 2008-08-18
oh sorry,

I wish to analyze patterns in the binary to make a data compressor for learning's sake

thus i need to either bring it back as a char[] or write it to file and binary if it is possible

---

### Post by dribeas on 2008-08-18
> **Mr.Macdonald said:**
> oh sorry,

I wish to analyze patterns in the binary to make a data compressor for learning's sake

thus i need to either bring it back as a char[] or write it to file and binary if it is possible

You'd probably want to analyze with some granularity (byte/2-byte words/4-byte words)... maybe just bitwise... If you do need to analyze one bit at a time,  the methods above may be appropiate, maybe yielding both the bool* and a size_t/unsigned int with the size in the array... or maybe returning a std::vector<int/unsigned char> (std::vector<bool> are weird, keep away from them if you want efficiency, but std::vector<> of any other type are a good tool).

If you want to analyze with a different granularity (say byte) then instead of doing the conversion you can use casts and you won't need to make a copy of the original. Mileage will vary, and really depends on what and how you want to work with the data (your algorithms).

   David

---

### Post by Mr.Macdonald on 2008-08-18
currently my algorithm goes as follows

I make a dictionary size relative to data given
I go through the data and populate the dictionary
I then compress the data using the dictionary
I combine the data and the dictionary using markers for beginning and end
If the data could be compressed more, then i recursively compress the combined data
The first four bits tell how many times the data has been recursively compressed
0  being uncompressed
1  is normal compression
2+ is recursive compression

I have been doing it with chars but binary should be more efficient

The Code is tarred away but if you want to see it i will show you with commenting

---

### Post by dwhitney67 on 2008-08-18
> **Mr.Macdonald said:**
> oh sorry,

I wish to analyze patterns in the binary to make a data compressor for learning's sake

thus i need to either bring it back as a char[] or write it to file and binary if it is possible
If ultimately your goal is to write data, in binary, to a file for the sake of compression, then all you would need to do is open the file for binary output and then use the ostream write method to write the data.

For instance:
[PHP]#include <fstream>
#include <string>
#include <iostream>


void writeData( std::ofstream &ofs, int value, bool boolValue )
{
  ofs.write( (char*) &value, sizeof(value) );
  ofs.write( (char*) &boolValue, sizeof(boolValue) );
  ofs.flush();
}

void readData( std::ifstream &ifs, int &value, bool &boolValue )
{
  ifs.read( (char*) &value, sizeof(value) );
  ifs.read( (char*) &boolValue, sizeof(boolValue) );
}

int main()
{
  const std::string filename = "MyData.bin";

  // open file for output; specify that it will handle binary data.
  std::ofstream ofs( filename.c_str(), std::ios::binary );

  writeData( ofs, 0xcafebabe, true );

  int  value = 0;
  bool flag  = false;

  // open file for input; specify that it will handle binary data.
  std::ifstream ifs( filename.c_str(), std::ios::binary );

  readData( ifs, value, flag );

  std::cout << "Value from file = " << std::hex << value << std::endl;
  std::cout << "Flag from file  = " << (flag ? "true" : "false") << std::endl;

  return 0;
}[/PHP]
For more complex objects (classes), you should consider defining/developing serialization and deserialization methods.  Usually these have definitions that may look similar to:
[PHP]class MyObject
{
  public:
    ...
    size_t serialize( char *buf, size_t bufSize ) const;
    static MyObject * deserialize( const char *data, size_t dataLength );
    ...
};[/PHP]
The serialize method will take the class's member data and write, in binary format, into the given buffer.  The buffer can then be written to a file.

The deserialize does the opposite.  Given a buffer of data (e.g. data from a file), create and return an object containing the data.

There's probably other ways to accomplish the serialization/deserialization task, but if you want to learn the nuts/bolts how things work I suggest you try the way described above.

P.S.  Consider using std ostringstream for serialization, and std istringstream when deserializing.

---

