---
title: "Not a problem -- (Just interesting to me)"
date: 2010-01-15
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-01-15
Not sure if this happens to anyone else BUT 


if i try to compile this VERY basic c++ program (was showing someone how cout worked)

[PHP]
#include <iostream>
#include <cstdlib>
using namespace std;

int main () 
{
    cout <<"frggr"; //ROFL -- apparently cout <<"frggr"; is malware... makes me smile, my handle is famous :)

    
    
    system ("PAUSE");
    return 0;
    
}[/PHP]


Avast sees it as malware... I tested and it seems that it is the cout<<"frggr"; line that make this happen.

Anyone know why  \\ does this happen to anyone else if they try to compile this.

---

### Post by c0mput3r_n3rD on 2010-01-15
Maybe in windoze....

---

### Post by lisati on 2010-01-15
> **c0mput3r_n3rD said:**
> Maybe in windoze....

More likely that something in the compiled code resembles something in AVAST's definitions, maybe a misplaced confidence in a sequence of bytes common to this code and some malware?

---

### Post by Axos on 2010-01-15
Yeah, way back in the dark ages I had to write some NetBIOS code (barf). Bing! The virus scanner thought my program was evil. I had to rearrange the code to prevent the false detection.

---

