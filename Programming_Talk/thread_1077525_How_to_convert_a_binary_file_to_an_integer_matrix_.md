---
title: "How to convert a binary file to an integer matrix in c++ ?"
date: 2009-02-22
forum: Programming Talk
---

### Post by cherva on 2009-02-22
Can someone write a simple code to show me how to convert a binary file to an integer matrix in C++ ? I know I should open the file in binary mode, but then what ? I need to get somethin like this:
int file2[29312] = {77,90,-112,0,3,0,0,0,4,0,0,0,-1,-1,0,0,-72,0,0,0,0,0,0,0,64,
0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,-72,0,0,0,
14,31,-70,14,0,-76,9,-51,33,-72,1,76,-51,33,84,104,105,115,32,112,114,111,103,11
4,97,109,32,99,97,110,110,111,116,32,98,101,32,114,117,110,32,105,110,32,68,79,8
3,32,109,111,100,101,46,13,13,10,36,0,0,0,0,0,0,0,-43,90,-115,-39,-111,59,-29,-1
18,-111,59,-29,-118,-111,59,-29,-118,-111,59,-29,-118,-120,59,-29,-118,41,61,-27
,-118,-112,59,-29,-118,121,36,-23,-118,-105,59,-29,-118,82,105,99,104,-111,59,-2
9,-118,0,0,0,0,0,0,0,0,80,69,0,0,76,1,5,0,49,-54,102,57,0,0,0,0,0,0,0,0,-32,0,14
,1,11,1,6,0,32,92,0,0,-32,19,0,0,0,0,0,0.......................
so I can put it in a separate .h file and then when my program is runed to construct the file back to its original state....
I suppose the reconstructing is done like this:
```
void write(char filename[], int size, int file[])

{

	ofstream outfile (filename,ofstream::binary | ios::out);

	for (int i=0; i<size; i++) {

		outfile << (char)file[i];

	}

	outfile.close();

}
```

---

### Post by issih on 2009-02-22
```
int main () {
//set number of integers to read - calculate from file length if need be

int noOfIntegers = 23714; 

//generate array
int array[noOfIntegers];

//construct a binary input file stream
  ifstream in ( "test.txt" , ifstream::binary );

  //check stream has opened correctly - this is a bit poor you
  //should really be a bit more careful than this.
  if(in)
  {
    for(int i = 0; i<noOfIntegers; i++)
    {
       //use formatted extraction operation to put integer value
       //into array
       in >> array[i];
    } 
  }
  in.close();
  return 0;
}

```

Something like that anyway..this is untested

---

### Post by cherva on 2009-02-22
Well with this code the beggining of the array is full of zeroes and when I try to reconstruct a picture I get "Image has zero width"...

---

### Post by cabalas on 2009-02-22
There is a shorter (and in my opinion nicer) way to go reading and writing the array.  I've tested the following example and it works fine.

[PHP]
#include <iostream>
#include <fstream>

int main(int argc, char *argv[])
{
	int size = 4;
	int out_array[] = { 5, 8, 1233, 4 };
	int in_array[size];
	
	std::fstream out("test.bin", std::ios_base::binary | std::ios_base::out);
	out.write((char *)&out_array, sizeof(out_array));
	out.close();
	
	std::fstream in("test.bin", std::ios_base::binary | std::ios_base::in);
	in.read((char *)&in_array, sizeof(in_array));
	in.close();	

	for(int i = 0; i < size; i++)
		std::cout << "Element " << i << " is " << in_array[i] << std::endl;
	
	return 0;
}
[/PHP]

---

### Post by cherva on 2009-02-22
Well this can't reproduce the same picture.... now I get "Unrecognized image file format"
[COLOR="Red"]OK HERE IS A WORKING VARIANT OF WHAT I WANTED:[/COLOR]
```
#include <iostream>
#include <fstream>
#include <stdlib.h>

#include <vector>
using namespace std;

bool binread(vector<char>& buffer, char const* name) {
  ifstream is ("example", ios::binary);
  if (!is) {
    return false;
  }
  // get length of file:
  is.seekg (0, ios::end);
  buffer.resize(is.tellg());
  is.seekg (0, ios::beg);
  is.read(&buffer.front(), buffer.size());
  return true;
}

void load_1byte_ints(vector<int>& target, vector<char> const& buffer) {
  for (
    vector<char>::const_iterator i = buffer.begin(), end = buffer.end();
    i != end;
    ++i
  ) {
    target.push_back(int(*i));
  }
}





int main () {
  vector<char> buffer;
  if (!binread(buffer, __FILE__)) {
    return 1;
  }
  vector<int> nums;
  load_1byte_ints(nums, buffer);

  for (unsigned i = 0; i < nums.size(); ++i) {
    cout << nums[i] << ' ';
    if (i % 80 == 79) {
      cout << '\n';
    }
  }
  /////////////////////////////////////////////////////////////////
  // 		TEST FOR REPRODUCING THE FILE                    //
  /////////////////////////////////////////////////////////////////
  ofstream outfile ("example1",ofstream::binary | ios::out);

	for (int i=0; i<buffer.size(); i++) {

		outfile << (char)buffer[i];

	}

	outfile.close();
  return 0;
}

```

---

### Post by cabalas on 2009-02-22
Out of interest, though you are messing around with text files currently it seems that you are trying to load images, if so is there any reason you aren't using (or can't use) an existing library to do this? It would probably make your life easier.

---

### Post by issih on 2009-02-22
Cabalas' solution casting the array pointer to a character is far neater than either mine or yours, as it avoids doing any explicit conversions, it just copies the binary data as bytes into memory.

Much better solution, I'd work on doing it that way if I were you.

Stupidly, having looked at my own image loading code, cabalas' method is what my own code does :) That's what I get for doing something from memory.
<edit>
After a little investigation to work out why my original method failed, the formatted operations << and >> do not read and write nicely from binary streams, well they do, but they do not read and write in binary.

even with an output stream flagged as binary, using >> 43 will write the numerals 43 into the file NOT the binary equivalent, in the same way, even on a binary input stream doing in >> anInt will try to parse the binary stream as text looking for the next whitespace and will try to do a conversion from the text to an int, and understandably fail.

You need to use both read and write to output actual bytes, not << OR >>, they will mess with your answers something awful.

---

