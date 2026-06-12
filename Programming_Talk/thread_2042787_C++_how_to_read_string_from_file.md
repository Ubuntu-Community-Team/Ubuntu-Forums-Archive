---
title: "C++ how to read string from file"
date: 2012-08-15
forum: Programming Talk
---

### Post by sreeharitk on 2012-08-15
Hi all
Happy greetings to all of UBUNTU !!!!!!!!!!!! :):):):)
Hope everybody celebrating life in Planet Earth :):):)
Thanks for the great help provided so far :)
The following program is written for reading text string from a file but it is only reading first word. how to over come that?

#include <iostream>
#include <fstream>
using namespace std;

int read()
{

ifstream in  ("char.txt");
char str[67];
in>>str;
cout<<str<<endl;
return 0;
}

The output should be " This is a string"
However it returns only " This"
how to overcome this??!!

---

### Post by ofnuts on 2012-08-15
Stream string extraction (<<) is "formatted input" and reads items for the stream (numerical or boolean values, words). 

If you want to read the plain stream contents, use  get() or getline().

---

### Post by sreeharitk on 2012-08-15
Thank you sir!!!!!!!!!
It worked!
I changed my code in the following way..
Thanks a lot again :)

#include <iostream>
#include <fstream>
using namespace std;
int main()
{
int i,j,k;
ifstream inobj  ("char.txt");
char str [30];
**[SIZE=3]inobj.get(str, 30);[/SIZE]**
cout<<str<<endl;
return 0;
}
With regards

---

### Post by Zugzwang on 2012-08-15
> **sreeharitk said:**
> Thank you sir!!!!!!!!!
It worked!
I changed my code in the following way..
Thanks a lot again :)

#include <iostream>
#include <fstream>
using namespace std;
int main()
{
int i,j,k;
ifstream inobj  ("char.txt");
char str [30];
**[SIZE=3]inobj.get(str, 30);[/SIZE]**
cout<<str<<endl;
return 0;
}
With regards

Warning! This code is very dangerous. Please read up on null-termination of strings. Your code above may sometimes work and sometimes not work, and you do not catch error cases. You could improve it as follows:

```


#include <iostream>
#include <fstream>
using namespace std;
int main()
{
 int i,j,k;
 ifstream inobj  ("char.txt");
 char str [31];
 i = inobj.get(str, 30);
 if (i>=0) {
   str[i] = '\0';
   cout<<str<<endl;
 }
 return 0;
}

```

---

