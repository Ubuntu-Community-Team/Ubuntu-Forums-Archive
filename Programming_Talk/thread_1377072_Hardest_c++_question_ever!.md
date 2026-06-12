---
title: "Hardest c++ question ever!"
date: 2010-01-09
forum: Programming Talk
---

### Post by Jonasu on 2010-01-09
Well.. It might be.. and it might not be..

The last 3 or 4 hour's I've been googlin' for an "relative easy" question to answer. Maybe I'm just a google noob, but I've also been asking the same question in 2-3 forums.. and no one can solve my problem.. 

What I want to obtain is the size of a file.. That shouldn't be so hard should it? Well, the problem is that the file is already in use (it is in a download progress, witch means it is not the full file). 

In Windows (or in any other OS), you can just rightclick on the file to get the current size in bytes, not the size on disk, not the full file size.. but the current filesize in bytes. 

I got one code so far:
```

#include <iostream>
#include <sys/stat.h>

using namespace std;
int main()
{
    struct stat st;
    stat("lal.txt", &st);
    cout<<st.st_size;
    return 0;
}

```

Well.. it works somehow.. but it only gives me the current size on the disk!! I do NOT want that.. I just want the current file size!! Why is this so damn hard!?

So pleas.. if anyone know how to solve this, I would be really happy and thankful! :o

---

### Post by wmcbrine on 2010-01-09
> **Jonasu said:**
> Well.. it works somehow.. but it only gives me the current size on the disk!! I do NOT want that.. I just want the current file size!!The difference escapes me.

---

### Post by lisati on 2010-01-09
> **wmcbrine said:**
> the difference escapes me.

+1 :)

---

### Post by iponeverything on 2010-01-09
> **Jonasu said:**
> Well.. It might be.. and it might not be..

The last 3 or 4 hour's I've been googlin' for an "relative easy" question to answer. Maybe I'm just a google noob, but I've also been asking the same question in 2-3 forums.. and no one can solve my problem.. 

What I want to obtain is the size of a file.. That shouldn't be so hard should it? Well, the problem is that the file is already in use (it is in a download progress, witch means it is not the full file). 

In Windows (or in any other OS), you can just rightclick on the file to get the current size in bytes, not the size on disk, not the full file size.. but the current filesize in bytes. 

I got one code so far:
```

#include <iostream>
#include <sys/stat.h>

using namespace std;
int main()
{
    struct stat st;
    stat("lal.txt", &st);
    cout<<st.st_size;
    return 0;
}

```

Well.. it works somehow.. but it only gives me the current size on the disk!! I do NOT want that.. I just want the current file size!! Why is this so damn hard!?

So pleas.. if anyone know how to solve this, I would be really happy and thankful! :o

Try flushing the buffer cache before the stat..

---

### Post by kwyto on 2010-01-10
```

[COLOR=#000000]#include <iostream.h>[/COLOR]
[COLOR=#000000]#include <fstream.h>[/COLOR]
 
[COLOR=#7f0055]**const **[/COLOR][COLOR=#7f0055]**char **[/COLOR][COLOR=#000000]* filename = [/COLOR][COLOR=#2a00ff]"test.txt"[/COLOR][COLOR=#000000];[/COLOR]
 
int main () {
  long l,m;
  ifstream file (filename, ios::in|ios::binary);
 
  l = file.tellg();
 
  file.seekg (0, ios::end);
  m = file.tellg();
 
  file.close();
 
  cout << "size of " << filename;
 
  cout << " is " << (m-l) << " bytes.\n";
 
  return 0;
}
```
 
this should help. if not then check this [http://www.angelfire.com/country/aldev0/cpphowto/cpp_BinaryFileIO.html](http://www.angelfire.com/country/aldev0/cpphowto/cpp_BinaryFileIO.html)

---

### Post by kwyto on 2010-01-10
another thing, maybe it would work if you close the file. read the size and opened the file again.

---

### Post by JackRock on 2010-01-10
> **wmcbrine said:**
> The difference escapes me.

He means that *during a download*, he wants to know the actual size, in bytes, the file is taking up.  While the download is progressing, *but not yet finished*, the size on disk will read the full file size after downloading is completed.  He wants to know how much is *already* downloaded and written to disk, excluding the portion that has not yet been downloaded.

---

### Post by Jonasu on 2010-01-10
@Kwoyto
I've already tried something similar, but I know it wont work because the code opens the file, witch is impossible, and I can not close it during dl process. But thanks anyway..

Btw. I've already read through the link you gave me, it didn't help anything because I think were going for the wrong functions..

@JackRock
Well... Somehow, but not exactly right.. U see, when a file is really small (witch my text file is, 19bytes) it doesn't take up the whole sector on the hdd, or even worse, it might have been spread out to even more sectors on the hdd witch makes my textfile to end up being 4kb.. That is what I get when run the st_size, and that is not the size I want to find.


This problem seems to get harder and harder, aren't there anyone out there that know the answer!?

---

### Post by The Secret on 2010-01-10
```
#include <iostream>
#include <fstream>

using namespace std;

int main(int argc, char *argv[])
{
    if (argc <= 1) {
        cout << "No file specified!" << endl;
        return 1;    
    }
    
    FILE * stream = fopen(argv[1], "r+");
    fseek(stream, 0, SEEK_END);
    long endPos = ftell(stream);
    fclose(stream);
    
    cout << "File size: " << endPos << endl;
    
    return 0;    
}

```

Does this return the same ?

---

### Post by dwhitney67 on 2010-01-10
> **Jonasu said:**
> ...
Well... Somehow, but not exactly right.. U see, when a file is really small (witch my text file is, 19bytes) it doesn't take up the whole sector on the hdd, or even worse, it might have been spread out to even more sectors on the hdd witch makes my textfile to end up being 4kb.. That is what I get when run the st_size, and that is not the size I want to find.

What OS are you using?

I ran this trivial program on my system; the results came out as expected.  That is, the file has a size of 19 bytes.
```

#include <fstream>
#include <sys/stat.h>
#include <iostream>
#include <cassert>

int main()
{
   using namespace std;
   const char* filename = "test.dat";

   // create 19 bytes test data file
   fstream outfile(filename, ios::out | ios::binary);

   if (outfile)
   {
      char buf[19] = {0};

      outfile.write(buf, sizeof(buf));
      outfile.close();

      cout << "Created file of size: " << sizeof(buf) << " bytes." << endl;

      // check size of test data file
      struct stat st_buf;
      stat(filename, &st_buf);

      cout << "File size is: " << st_buf.st_size << endl;

      assert(st_buf.st_size == sizeof(buf));
   }
}

```

---

### Post by Jonasu on 2010-01-10
> **dwhitney67 said:**
> What OS are you using?

I ran this trivial program on my system; the results came out as expected.  That is, the file has a size of 19 bytes.
```

#include <fstream>
#include <sys/stat.h>
#include <iostream>
#include <cassert>

int main()
{
   using namespace std;
   const char* filename = "test.dat";

   // create 19 bytes test data file
   fstream outfile(filename, ios::out | ios::binary);

   if (outfile)
   {
      char buf[19] = {0};

      outfile.write(buf, sizeof(buf));
      outfile.close();

      cout << "Created file of size: " << sizeof(buf) << " bytes." << endl;

      // check size of test data file
      struct stat st_buf;
      stat(filename, &st_buf);

      cout << "File size is: " << st_buf.st_size << endl;

      assert(st_buf.st_size == sizeof(buf));
   }
}

```

OMG! It somehow worked now! I can't believe it! Thanks!

I've marked this topic as solved!

---

### Post by dwhitney67 on 2010-01-10
> **Jonasu said:**
> OMG! It somehow worked now!...

Yeah, I guess we will chalk this up as another weird example where compiled/linked code behaves one way at a certain time, and totally different at another.  :rolleyes:

---

