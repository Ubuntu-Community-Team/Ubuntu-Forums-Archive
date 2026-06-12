---
title: "[C++] Trouble overloading &gt;&gt; and &lt;&lt;"
date: 2008-08-27
forum: Programming Talk
---

### Post by NovaAesa on 2008-08-27
Hi everyone.

I'm trying to overload the >> and << operators for a big assignment that I have. I have googled around for a while and haven't been able to work out my problem though. I have narrowed down the problem and can reproduce it in a much smaller programme that I have here:

Makefile:
```
CC=g++
CFLAGS=-c -Wall
LDFLAGS=
SOURCES=test.cpp bad.cpp
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=test

all: $(SOURCES) $(EXECUTABLE)
	
$(EXECUTABLE): $(OBJECTS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

%.o : %.cpp
	$(CC) $(CFLAGS) -c $<

clean:
	rm -rf *.o core
```

test.cpp:
```
#include "bad.h"
#include <iostream>

using namespace std;

int main() {

    bad iii;
    cin >> iii;
    cout << iii;
    
    return 0;
}
```

bad.h:
```
#include <iostream>
#include <string>
using namespace std;

class bad {

    friend ostream& operator << (ostream& out, const bad& b);
    friend istream& operator >> (istream& in, const bad& b);

  public:
    string getI();
    void setI(string i);
  
  private:
    string i;

};
```

bad.cpp:
```
#include "bad.h"
#include <string>

string bad::getI() {
    return i;
}

void bad::setI(string i) {
    this->i = i;
}

ostream& operator << (ostream& out, bad& b) {
    out << b.getI();
    return out;
}

istream& operator >> (istream& in, bad& b) {
    string temp;
    in >> temp;
    b.setI(temp);
    return in;
}
```

Console output:
```
ps@ps-desktop:~/Documents/Uni/08Sem2/SENG1120/Projects/test$ make clean && make all
rm -rf *.o core
g++ -c -Wall -c test.cpp
g++ -c -Wall -c bad.cpp
g++  test.o bad.o -o test
test.o: In function `main':
test.cpp:(.text+0x1a8): undefined reference to `operator>>(std::basic_istream<char, std::char_traits<char> >&, bad const&)'
test.cpp:(.text+0x1bb): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, bad const&)'
collect2: ld returned 1 exit status
make: *** [test] Error 1
ps@ps-desktop:~/Documents/Uni/08Sem2/SENG1120/Projects/test$ 

```

I know we aren't meant to ask about assignments here, but this technically isn't the assignment. It's just a small bit of code that reproduces the same error in the same situation.

If anyone could at least point me in the right direction I would be very happy!

Thank you.

---

### Post by NovaAesa on 2008-08-27
Nevermind, I had my consts not matching up between my definitions and implimentations for << and >>

---

