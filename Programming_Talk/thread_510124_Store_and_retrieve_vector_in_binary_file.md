---
title: "Store and retrieve vector in binary file"
date: 2007-07-26
forum: Programming Talk
---

### Post by Ryutatsu on 2007-07-26
This is probably a stupidly simple question but I'm new to C++. Basically my plan is to have one program create a vector containing objects of a custom class and store it to a file. That file will then be read later by another program that should load the entire vector into a vector within that program. I also need to store and retrieve two ints separate from the vector but that will probably be the easy part. Right now I can create the vector but I'm not sure how to store or retrieve it. I've tried the following for writing it:

	```

        ofstream mapOut("default.dat",ios::binary);
	mapOut.write((char *)(&map),sizeof(map));
	mapOut.close();
```

and this to retrieve it:
	```

        ifstream mapIn("default.dat",ios::binary);
	mapIn.read((char *)(&map),sizeof(map));
	mapIn.close();
```

Am I missing something?

---

### Post by Soybean on 2007-07-26
That code would only work if "map" (which is a std::vector, if I understand correctly?) stored everything in one contiguous chunk of memory, and the size of that chunk was sizeof(map). As far as I know, neither of these is likely to be true. My understanding is that you shouldn't assume anything about how or where STL classes keep the objects they index. And I believe sizeof(map) probably returns the size of the vector itself, not including the objects in it.

Your custom class will need to have read and write functions for itself, and you'll need to iterate through the vector calling the read/write function for each element. It can also be helpful to start by writing map.size() to the file, so you know how many elements to expect when you go to read it back in.

---

### Post by Ryutatsu on 2007-07-26
Sounds like a good idea. I've got a few things that I thought of that I'd like to try as well to see which one I like the best.

---

### Post by Wybiral on 2007-07-26
Soybean speaks the truth!

Check this out (remember that each int is 4 bytes on a 32 bit machine)

```

#include <iostream>
#include <vector>

using namespace std;

int main()
{ 
    vector<int> x;

    for(int i=0; i<10; ++i)
    {
        x.push_back(i);
        cout << sizeof(x) << endl;
    }

    return 0;
}

```

---

