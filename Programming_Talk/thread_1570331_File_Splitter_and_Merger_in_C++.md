---
title: "File Splitter and Merger in C++"
date: 2010-09-08
forum: Programming Talk
---

### Post by meadhikari on 2010-09-08
I am a newbie and am currently learning file handling in c++
I was building a file splitting module.
How I tried to do this was
1. Get the bigfile from Command line argument
2. Get from the user how many parts to divide into
3. Calculate the size of the users file
And now is where I have problem
4. I want to separate each chunk from the bigfile and write to small file.
Please Help me with this

```
#include <iostream>
#include <fstream>
#include <string>

using namespace std;
int main(int argc, char** argv)
{
	int parts;
	cout <<"Enter the number of parts";
	cin >> parts;
	ifstream bigfile;
	bigfile.open(argv[1],ios::in | ios::binary);
	int size=0;	
	
        bigfile.seekg (0, ios::end);
        int length = bigfile.tellg();
        bigfile.seekg (0, ios::beg);
        int achunck = size/parts;

	// seek the file to bigining here
	for (int i = 0; i < parts; i++)
	{
		//extratct a chunk here and write it to the small file	
	}
	
   return 0;
}
```

---

### Post by Some Penguin on 2010-09-08
This isn't a "do my homework" forum.

And your code is an illogical mess even as incomplete as it is -- for instance, 'achunck' divides 'size' before you've even bothered to figure out what the size of the file (and you've chosen a horribly inefficient way of determining what that size is -- ask the filesystem!).

---

### Post by meadhikari on 2010-09-08
I am very very sorry for my writing.
and this is not a homework....
and I am just learning file handling

Its been a minute that I have learn calculating size with
```

is.seekg (0, ios::end);
length = is.tellg();
is.seekg (0, ios::beg);

```

and now I will be implementing that....
It was a blunder of mine to put that achunk before the while loop

If my way was efficient I would not have started this thread.
I am just learning...
and let me make you clear that this is not my homework

---

### Post by dwhitney67 on 2010-09-08
Since you know the size of the file, and you know the desired number of smaller files to create, just perform the basic math to determine the chunk size.

It is possible that the final file will contain more bytes than the others, but it won't be much more; it could possibly contain between 0 to "number of files" minus one bytes.

```

size_t avgChunkSize = fileSize / numFiles;
size_t addtBytes    = fileSize % numFiles;

```
As for reading from the larger file, and then subsequently writing to each smaller file, use a for-loop for the number of files, and then employ the read() and write() methods for the fstream objects.

After the loop has completed, don't forget to read the additional bytes from the source (big) file, if any, and write them to the last destination (small) file.


P.S.  An alternative, but not necessarily portable, way to deduce a file's size is to use the stat() C library function.

P.S. #2  The code you originally posted is also missing the necessary steps to create N unique file names to store the data.  I would recommend that you look into using the std::stringstream (inside the loop) to facilitate building each file name.

---

### Post by meadhikari on 2010-09-09
Thanks for the reply.
 I implemented it but I have a problem.....
When the file size is just greater than 1 or 2MB i get a error saying segmentation failure 
```
#include <iostream>
#include <fstream>
#include <string>
#include <sstream>
#include <cstdlib>

using namespace std;
int main(int argc, char** argv)
{
    int parts = atoi(argv[2]);
    
    ifstream bigfile;
    bigfile.open(argv[1],ios::in | ios::binary);
        
    // get length of file:
  bigfile.seekg (0, ios::end);
  int length = bigfile.tellg();
  bigfile.seekg (0, ios::beg);
   double achunk = length/parts;
   char buffer [achunk];
   for (int i = 0; i < parts; i++)
    {
        //creating the file name
         //Build File Name
         string filename = argv[1];
         string bigfilename = filename.substr(0,filename.size()-1);
         string partname = bigfilename;  //The original filename
         string charnum;     //archive number
         stringstream out;
         out << "." << i;
         charnum = out.str();
         partname.append(charnum);  //put the part name together
        //chunking and writing to small files
        bigfile.read (buffer,achunk);
        ofstream smallfile;
        smallfile.open(partname.c_str(),ios::out | ios::binary);
        smallfile <<buffer;
        smallfile.close();
            
    }
    
   return 0;
}

```

---

### Post by GeneralZod on 2010-09-09
If you're going to be reading the entirety of a part into memory all at once, it's probably a good idea to read it into a heap-based buffer, rather than a stack-based one :)

Is

```

char buffer [achunk];

```

even valid C++?

---

### Post by meadhikari on 2010-09-09
I am changing that with this.

```

vector<char> buffer (achunk);

bigfile.read (&buffer[0], achunk);

smallfile.write (&buffer[0], achunk);

```

But what to do with the variable length which holds the size of the file. Is it the one causing segmentation failure

---

### Post by dwhitney67 on 2010-09-09
GeneralZod is correct, however he was not suggesting that you use a vector.

He was suggesting the following:
```

size_t chunkSize = fileSize / numParts;
size_t addtBytes = fileSize % numParts;

char* buffer = new char[chunkSize];

...

delete [] buffer;

```
Also, fix this:
```

smallfile <<buffer;

```
This is probably more appropriate:
```

smallfile.write(buffer, chunkSize);

```
Or if you are not comfortable using chunkSize above, use bigFile.gcount(), although I've never tried this (ie. I don't know if it works).

Don't attempt to compute the chunkSize as a double; there's no point to this.

Lastly, don't forget to write out the additional bytes to the last file.  You may find that some of the steps used to define the unique file names belong outside of the for-loop.

---

### Post by meadhikari on 2010-09-10
Splitter Its working fine.....
```
#include <iostream>
#include <fstream>
#include <string>
#include <sstream>
#include <cstdlib>
#include <vector>
using namespace std;
int main(int argc, char** argv)
{
    int parts = atoi(argv[2]);
    
    ifstream bigfile;
    bigfile.open(argv[1],ios::in | ios::binary);
        
    // get length of file:
    bigfile.seekg (0, ios::end);
    int length = bigfile.tellg();
    bigfile.seekg (0, ios::beg);
    
    int achunk = length/parts;
       vector<char> buffer (achunk);
   
       for (int i = 0; i < parts; i++)
    {
         
         //Build File Name
         string partname = argv[1];
                 string charnum;     //archive number
                 stringstream out;
                 out << "." << i;
                 charnum = out.str();
                 partname.append(charnum);  //put the part name together
        
        //chunking and writing to small files
        bigfile.read (&buffer[0], achunk);
        ofstream smallfile;
        smallfile.open(partname.c_str(),ios::out | ios::binary);
        smallfile.write (&buffer[0], achunk);
        smallfile.close();
            
    }
    
   return 0;
}

```
Merger with few errors
```
#include <iostream>
#include <fstream>
#include <string>
#include <sstream>
#include <cstring>
#include <cstdio>
#include <cstdlib>
#include <vector>


using namespace std;
int main(int argc, char** argv)
{
    int parts = atoi(argv[2]);
    
   
    //obtaining the name of the main file
    string temp = argv[1];
    int lengthoftemp =temp.size();
    int lengthofbigfile = lengthoftemp-1;
    string  bigfilename = temp.substr(0,lengthofbigfile);
    
    //opening the main file 
    ifstream smallfile;
     smallfile.open(argv[1],ios::out | ios::binary);//instead of argv[1] bigfilename needs to be but why can not it be done
    
    
    // get length of file:
    smallfile.seekg (0, ios::end);
    int length = smallfile.tellg();
    smallfile.seekg (0, ios::beg);
    vector<char> buffer (length);
    smallfile.close();
  
   
     for (int i = 0; i < parts; i++)
    {
          
         
         //Build File Name for small files
         string partname = bigfilename;
                 string charnum;     //archive number
                 stringstream out;
                 out << i;
                 charnum = out.str();
                 partname.append(charnum);  //put the part name together
         
         //writing chunck to bigfile(am I conceptually wrong somewhere here)
         ifstream smallfile;
         smallfile.open(partname.c_str(),ios::out | ios::binary);
         smallfile.read (&buffer[0], length);
         ofstream bigfile;
         bigfile.open(argv[1],ios::out | ios::binary);
         bigfile <<smallfile;
         smallfile.close();
    }    
    return 0;
}
    

```

Thanks so much for your concern on my work.

---

### Post by dwhitney67 on 2010-09-10
You still have not accounted for file sizes that are not wholly divisible by the number of (file) parts.

For instance, if you have a file size, of say 1000 bytes, and you divide this into 10 parts, then your application works fine.

But if the original file has a size, of say 1003 bytes, then your application does not work because it is missing the code to write the remaining 3 bytes, after you have completed writing 10 parts, each containing 100 bytes.

Revisit your code to add in the additional step that is missing.  Similar for the merger code.

P.S.  In the example above, the remaining 3 bytes should be written to the 10th file, or as an alternative, an additional byte to each of the files, as necessary.  The latter is probably the better solution (ie the average number of bytes is distributed across all files).

---

