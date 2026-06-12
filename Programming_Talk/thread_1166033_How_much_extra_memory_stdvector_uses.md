---
title: "How much extra memory std::vector uses?"
date: 2009-05-21
forum: Programming Talk
---

### Post by yesint on 2009-05-21
Dear C++ programmers,
I'm writing a program, which uses complex multi-dimensional data structures like

vector< vector< vector<double> > >  

(in reality complex class is used instead of double)
It seems that the memory consumption of such things is ~5-10 times larger then for plain 3D array of doubles. 
How much memory std::vector uses for "housekeeping"?

---

### Post by hod139 on 2009-05-21
There is very little overhead.  For example, comparing the memory usage between:

```

#include <unistd.h> // sleep is declared here

class AClass
{
public:
  AClass(int n){
     data = new double**[n];
     for(int i = 0; i < n; ++i){
        data[i] = new double*[n];
        for(int j = 0; j < n; ++j){
           data[i][j] = new double[n];
        }
     }
  }
  
  double*** data;
};


int main(){
  AClass foo(100);
  sleep(100);
  return 0;
}

```and 
```

#include<vector>
#include <unistd.h> // sleep is declared here

class AClass
{
public:
  AClass(int n){
     data.resize(n);
     for(int i = 0; i < n; ++i){
        data[i].resize(n);
        for(int j = 0; j < n; ++j){
           data[i][j].resize(n);
        }
     }
     
  std::vector< std::vector< std::vector<double> > > data;
};


int main(){
  AClass foo(100);
  sleep(100);
  return 0;
}

```produces the following memory usage results (using pmap command).  For the C style double***
```

08048000      4K r-x--  /home/sberard/temp/a.out
08049000      4K rw---  /home/sberard/temp/a.out
0804a000   8052K rw---    [ anon ]
b7d33000      4K rw---    [ anon ]
b7d34000   1316K r-x--  /lib/tls/i686/cmov/libc-2.7.so
b7e7d000      4K r----  /lib/tls/i686/cmov/libc-2.7.so
b7e7e000      8K rw---  /lib/tls/i686/cmov/libc-2.7.so
b7e80000     12K rw---    [ anon ]
b7e83000     40K r-x--  /lib/libgcc_s.so.1
b7e8d000      4K rw---  /lib/libgcc_s.so.1
b7e8e000      4K rw---    [ anon ]
b7e8f000    140K r-x--  /lib/tls/i686/cmov/libm-2.7.so
b7eb2000      8K rw---  /lib/tls/i686/cmov/libm-2.7.so
b7eb4000    928K r-x--  /usr/lib/libstdc++.so.6.0.9
b7f9c000     12K r----  /usr/lib/libstdc++.so.6.0.9
b7f9f000      8K rw---  /usr/lib/libstdc++.so.6.0.9
b7fa1000     24K rw---    [ anon ]
b7fbb000      8K rw---    [ anon ]
b7fbd000      4K r-x--    [ anon ]
b7fbe000    104K r-x--  /lib/ld-2.7.so
b7fd8000      8K rw---  /lib/ld-2.7.so
bfae9000     84K rw---    [ stack ]
 total    10780K

```and for the STL vector:
```

08048000     20K r-x--  /home/sberard/temp/a.out
0804d000      4K rw---  /home/sberard/temp/a.out
0804e000   8052K rw---    [ anon ]
b7cef000      4K rw---    [ anon ]
b7cf0000   1316K r-x--  /lib/tls/i686/cmov/libc-2.7.so
b7e39000      4K r----  /lib/tls/i686/cmov/libc-2.7.so
b7e3a000      8K rw---  /lib/tls/i686/cmov/libc-2.7.so
b7e3c000     12K rw---    [ anon ]
b7e3f000     40K r-x--  /lib/libgcc_s.so.1
b7e49000      4K rw---  /lib/libgcc_s.so.1
b7e4a000      4K rw---    [ anon ]
b7e4b000    140K r-x--  /lib/tls/i686/cmov/libm-2.7.so
b7e6e000      8K rw---  /lib/tls/i686/cmov/libm-2.7.so
b7e70000    928K r-x--  /usr/lib/libstdc++.so.6.0.9
b7f58000     12K r----  /usr/lib/libstdc++.so.6.0.9
b7f5b000      8K rw---  /usr/lib/libstdc++.so.6.0.9
b7f5d000     24K rw---    [ anon ]
b7f77000      8K rw---    [ anon ]
b7f79000      4K r-x--    [ anon ]
b7f7a000    104K r-x--  /lib/ld-2.7.so
b7f94000      8K rw---  /lib/ld-2.7.so
bf987000     84K rw---    [ stack ]
 total    10796K

```

---

### Post by Zugzwang on 2009-05-21
> **yesint said:**
>  
How much memory std::vector uses for "housekeeping"?

You can find it out using:
```

#include <vector>
#include <iostream>
using namespace std;

int main() {
	std::vector<double> test;
	std::cout << "Housekeeping: " << sizeof(test) << "\n";
}

```
Here, it's 24 bytes on a 64 bit machine or 12 bytes on a 32 bit machine (provided that housekeeping-stuff is not "hidden behind variables").

*However*, take into account the following facts:
[LIST]
[*]When cascading vectors, the housekeeping overhead will also be cascaded. So if you have a 4*4*4 matrix, you end up up with (4*(4*(1)+1)+1)*12 bytes overhead.
[*]When the vector automatically resizes (when adding stuff), it is likely to resize to a size too large, which will require additional size. By resizing it explicitely to the size needed, this can be avoided.
[/LIST]

---

### Post by monkeyking on 2009-05-21
It depends on how you use it.

if you get 10elems in size 10 vector,
and then add a new element.
The vector will then resize to twice the oldsize or something similar.
So you end up wasting some space.

This is not a problem for small vectors,
but will be a huge problem if you got a vector of size 500 meg.

If you know the dims you need you should use .reserve,
you can also supply your own allocator for the vector.


But a vector<vector<vector<struct>>> looks like it should be avoided, do you really need a datastructure like this?

---

### Post by yesint on 2009-05-28
Thank you for the answers guys! 
The puzzling thing is that the overhead is much much larger than computed one. All vectors are born with the correct size and are not dynamically resized. With my vector dimensions the size of the whole structure should be approximately 2 times larger in comparison to plain 3D array, but in reality it is 10-12 times larger! I suspect that the problem is in the memory management of the internal data structure, not in the vectors.

---

