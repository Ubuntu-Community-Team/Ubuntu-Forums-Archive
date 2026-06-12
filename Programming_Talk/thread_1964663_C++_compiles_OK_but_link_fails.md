---
title: "C++ compiles OK but link fails"
date: 2012-04-24
forum: Programming Talk
---

### Post by bcz on 2012-04-24
I am relatively new to C++ and I probably have made a simple mistake.  I compile using c++ src.cc.  Here is my source.
```

//  Extract customer data

#include <iostream>
#include <fstream>
#include <sys/stat.h>
using namespace std;

#define ioSize 2048
ifstream iFile;

class DataPage{
char page[ioSize];
public: 
bool readPage(ifstream iFile){
  if(iFile.read(page,(int)ioSize))return 1;
  return 0;} 
};
DataPage page0;

int main(){
cout << "Running cust data extract\n";
iFile.open("MCU01",ios::binary);
if(page0.readPage(iFile)){cout << "Page 0 read OK";}
}

```

Any help appreciated

Bill

---

### Post by 11jmb on 2012-04-24
An error message would help.

---

### Post by bcz on 2012-04-24
An ifstream cannot be used as a parameter, so just use it as a global.  Problem solved.

Thanks to all;

---

### Post by GeneralZod on 2012-04-24
> **bcz said:**
> An ifstream cannot be used as a parameter, so just use it as a global.  Problem solved.


[Globals are bad](http://c2.com/cgi/wiki?GlobalVariablesAreBad); just make it a reference instead.

```

//  Extract customer data

#include <iostream>
#include <fstream>
#include <sys/stat.h>
using namespace std;

const int ioSize = 2048;

class DataPage{
    char page[ioSize];
public: 
    bool readPage(ifstream& iFile) {        
        if(iFile.read(page,(int)ioSize))
            return true;
        return false;
    }   
};

DataPage page0;

int main() {
    cout << "Running cust data extract\n" << endl;
    ifstream iFile;
    iFile.open("MCU01",ios::binary);
    if(page0.readPage(iFile)) {
        cout << "Page 0 read OK" << endl;        
    }
}


```

---

### Post by bcz on 2012-04-26
Thanks General ZOD for your very useful reply.  I have checked the syntax you used and learnt quite a bit.

Globals have their place, but are often misused.  As you point out, this is a cleaner way to solve the problem.

Thanks again

Bill

---

