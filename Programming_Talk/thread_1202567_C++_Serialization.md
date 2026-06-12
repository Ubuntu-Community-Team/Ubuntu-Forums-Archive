---
title: "C++ Serialization"
date: 2009-07-02
forum: Programming Talk
---

### Post by Swenghk on 2009-07-02
Is there a tutorial that covers C++ serialization using human-readable code?

Or maybe a tutorial about how to write to a text file, and read back that text from the file to load data...such as a load/save game routine.

---

### Post by leblancmeneses on 2009-07-02
```

    public interface ITransformation
    {
        void Init(Configuration.TransformationServiceElement section);

        void RequestWriter(object serialize, Stream stream);
        T ResponseReader<T>(System.IO.Stream stream) where T : class;
    }

```


by implementing a contract
you can then swap serialization process...
json format, xml format, binary format


in c++ though since you don't have access to rich reflection capabilities found in java/c# i don't think you can send a generic object to serialize and query for /public/private properties values to save.  


Instead I think you must be strongly typed to your object so your object should contain OnSerialize which returns byte[] , OnDeserialize which returns new instance of object.
that would be the simplest way to go.

I think all that would be needed is memcpy to dump it's local memory space to a file and read it back in

also
[http://stackoverflow.com/questions/321619/c-serialization-performance](http://stackoverflow.com/questions/321619/c-serialization-performance)

---

### Post by .Maleficus. on 2009-07-02
This page might help.

[http://www.java2s.com/Code/Cpp/File/Saveandreadclassbackandforthtoafile.htm](http://www.java2s.com/Code/Cpp/File/Saveandreadclassbackandforthtoafile.htm)

---

### Post by Swenghk on 2009-07-02
That should do it! Thanks-you both!

---

### Post by dwhitney67 on 2009-07-02
> **Swenghk said:**
> Is there a tutorial that covers C++ serialization using human-readable code?

Or maybe a tutorial about how to write to a text file, and read back that text from the file to load data...such as a load/save game routine.

There are two types of data:  text and binary.  Typically, text files use printable characters, similar to what you are reading at this very moment.  Binary, on the other hand, is the computer's interpretation of the data in raw format, and this data may not be understood equally on computer's with dissimilar architectures (e.g. Intel vs. PowerPC).

Here's an example of writing text to a file in C++:
```

#include <fstream>

int main()
{
  using namespace std;

  fstream file("file.txt", ios::out);

  file << "This is my first use of fstream." << endl;
}

``` 
If you compile/run the code above, a text file with the name 'file.txt' will appear in the current directory.  It will contain the text shown above.

If you want to serialize raw data, the concept is the same, although the opening of the file and the writing of the data differ.  Here's an example:
```

#include <fstream>

int main()
{
  using namespace std;

  int value = 55555;
  fstream file ("file.bin", ios::out | ios::binary);

  file.write(&value, sizeof(value));
}

```
Here the write() method is used (vs the << operator as used in the previous example).  The reason is that I need to provide the address of the data, and the size of this data... which in the case above, is 4 bytes.

If you compile/run this second example, a file called 'file.bin' will appear in your working directory.  You can examine its contents using this command:
```

od -A d -x -v file.bin

```
Refer to the man-page for 'od' for more information on that command.

As for the C++ stuff on opening files and etc, go here:  [http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

P.S.  No error checking was done in any of the previous examples, nor were any animals harmed.

---

