---
title: "c++ problem"
date: 2009-02-28
forum: Programming Talk
---

### Post by abhilashm86 on 2009-02-28
i did a c++ in order to copy 1 file to another, can i declare ifstream and ofstream at beggining itself as i did below?
no error in compilation, 
also file has been created, but contents are not copied?
what is exact reason for this?
> #include<iostream>
#include<fstream>
using namespace std;
int main()
{
        ifstream i;
        ofstream o;
        ifstream("beer.cpp");
        ofstream("ber.cpp");

        string s;
        while(getline(i,s))
        o<<s<<endl;
}

abhilash@abhi:~$ vim cp4.cpp
abhilash@abhi:~$ g++ cp4.cpp
abhilash@abhi:~$ ./a.out
abhilash@abhi:~$ cat ber.cpp
abhilash@abhi:~$ ls ber.cpp -l
-rw-r--r-- 1 abhilash abhilash 0 2009-02-28 10:48 ber.cpp

u see ber.cpp has created,but no contents are copied..........

---

### Post by krazyd on 2009-02-28
[http://cplusplus.com/reference/iostream/ofstream/ofstream.html](http://cplusplus.com/reference/iostream/ofstream/ofstream.html)
[http://cplusplus.com/reference/iostream/ifstream/ifstream.html](http://cplusplus.com/reference/iostream/ifstream/ifstream.html)

See the two links above (that site is great for C++ stuff).

Basically, I think the lines```
ifstream i;
ofstream o;
ifstream("beer.cpp");
ofstream("ber.cpp");
```should be replaced with```
ifstream i ("beer.cpp");
ofstream o ("ber.cpp");
``` Otherwise the implementation doesn't know to bind the streams i and o to the relevant files.

---

### Post by christian8807 on 2009-02-28
#include<iostream>
#include<fstream>
using namespace std;
int main()
{
ifstream inData;
ofstream outData;
inData.open("beer.cpp", ios::in);
outData("ber.cpp");

string s;
while(!inData.eof())
{
inData >> s;
outData<<s<<endl;
}
inData.close();
outData.close();
return 0;
}

---

### Post by Sockerdrickan on 2009-02-28
[php]#include <fstream>

int main() {
     std::ifstream in("beer.cpp");
     std::ofstream out("beer2.cpp");

     out<<in.rdbuf();
}[/php]

---

