---
title: "C++ : Segmentation fault when dealing with arrays !"
date: 2009-07-01
forum: Programming Talk
---

### Post by credobyte on 2009-07-01
```
string filelist[] = {};

```
```
filelist[array_counter] = entry->d_name;
```

Loop ( while ) goes through ~ 15 filenames and "pushes" them into an array !
Now, after trying to execute it .. Segmentation fault :roll:

Any ideas ?

---

### Post by fr4nko on 2009-07-01
> **credobyte said:**
> ```
string filelist[] = {};

``````
filelist[array_counter] = entry->d_name;
```Loop ( while ) goes through ~ 15 filenames and "pushes" them into an array !
Now, after trying to execute it .. Segmentation fault :roll:

When you write 'string filelist = {}' you are defining an empty array, so no surprise it doesn't work ! It is a C-like array so it doesn not grow automatically.

You should do something like that:
```
#include <vector>
#include <iostream>

using namespace std;

int
main ()
{
  vector<string> filelist;

  filelist.push_back("hello world");

  cout << filelist[0] << endl;

  return 0;
}

```In this case, using 'push_back' the data will be appended at the end and the vector will grow as needed. Otherwise you should initilize the vector at the beginning and the code can be
```

vector<string> filelist(100); // initialised with 100 empty strings

[...]

filelist[index] = "hello world";

[...]

```Francesco

---

### Post by credobyte on 2009-07-01
Oh, well .. thanks for an explanation - *vector* did the job :)

---

