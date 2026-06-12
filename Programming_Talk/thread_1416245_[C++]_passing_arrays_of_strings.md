---
title: "[C++] passing arrays of strings"
date: 2010-02-25
forum: Programming Talk
---

### Post by falconindy on 2010-02-25
**Disclaimer**: homework related, but this is in hindsight.

The assignment was to create a class that mimics a book -- among the attributes was a requirement to have a field that could contain up to 4 authors per book. I tried to use an array of strings and pass it through the constructor, but this didn't work out as well as I would have liked. I eventually gave in and used a vector instead (which was far simpler).

My question is then, how? There's got to be a simple way to pass around arrays of strings, but I certainly couldn't figure out an effective manner of doing it. Below is an example of what I was trying to do (with more interesting subject matter):

```
#include <string>
#include <iostream>
using namespace std;

class Cheesy {
    private:
        string type[4];

    public:
        Cheesy(string&);
        void printMe();
};

Cheesy::Cheesy(string& type) {
    *this->type = type;
}

void Cheesy::printMe() {
    for (int i = 0; i < 4; i++)
        cout << "[" << i << "] " << type[i] << endl;
}

int
main(int argc, char** argv) {
    string* curd = new string[4];

    curd[0] = "limburger";
    curd[1] = "gouda";
    curd[2] = "brie";
    curd[3] = "muenster";

    Cheesy goodness = Cheesy(curd[0]);
    goodness.printMe();

}
```

It compiles and runs, but only the first element prints. I thought by passing the first element of the string array by reference, I could get access to the entire thing. Apparently, no so luck.

Where did I go wrong?

---

### Post by Some Penguin on 2010-02-25
```

*this->type = type;

```


1.   Resolves 'this->type'.
2.   Deferences it -- which for an array, is dereferencing the first element of the array.
3.   Replaces that first element with the passed-in one.

Thus, you only change one.

---

### Post by dwhitney67 on 2010-02-25
There's nothing wrong in passing an array, but bear in mind that you will not know the size unless you explicitly specify it or request the size be given via a parameter.

Here's an example of passing a fixed-sized array by reference:
```

#include <string>
#include <algorithm>
#include <iostream>

class Cheesy
{
public:
   Cheesy(const std::string (&cheeseType)[4])
   {
      std::copy(cheeseType, cheeseType + 4, type);
   }

   friend std::ostream& operator<<(std::ostream& os, const Cheesy& c)
   {
      for (int i = 0; i < 4; ++i)
      {
         os << "[" << i << "] " << c.type[i] << std::endl;
      }
      return os;
   }

private:
   std::string type[4];
};

int main()
{
   std::string curd[4] = { "limburger", "gouda", "brie", "muenster" };

   Cheesy goodness = Cheesy(curd);

   std::cout << goodness << std::endl;
}

```
Of course, I can think of other types of cheeses, thus as you discovered, using a vector is more appropriate in this case.

---

### Post by PmDematagoda on 2010-02-25
falconindy: Please read the Ubuntu Forums CoC where it mentions:-
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.
On that note, this thread is closed.

---

