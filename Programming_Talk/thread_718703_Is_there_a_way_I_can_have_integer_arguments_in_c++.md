---
title: "Is there a way I can have integer arguments in c++?"
date: 2008-03-08
forum: Programming Talk
---

### Post by WarMonkey on 2008-03-08
I know that you can do:
```
#include <iostream>
#include <fstream>
using namespace std;

int main(int argc, char *argv[]) {
cout << argv[1] << "\n";
}
```

But how would I make it so the argument is an integer? I want to be able to add two arguments together. I tried changing char *argv[] to int *argv[], but contrary to my expectations, it did not work.

---

### Post by mike_g on 2008-03-08
No, but the arguments can be converted by using strtol, or atoi.

Edit: heres an example: 
 [http://www.cplusplus.com/reference/clibrary/cstdlib/strtol.html](http://www.cplusplus.com/reference/clibrary/cstdlib/strtol.html)

---

### Post by [h2o] on 2008-03-08
You need to convert the textual representation of a number to an integer.
If my memory serves me right you should either be looking at "atoi()" or maybe some method of the stringstream classes.

---

### Post by WarMonkey on 2008-03-08
Thanks! It works perfectly.

---

### Post by Jessehk on 2008-03-08
There are several ways of doing this. If you want to do this in the bare-bones way, you can use a C function such as *atoi()* as suggested before. However, if you want to take advantage of C++ features and use an (arguably overkill) solution, you can do something like this:

```

#include <iostream>
#include <stdexcept>
#include <sstream>
#include <string>

class ConvertError : public std::invalid_argument {
    public:
        ConvertError( const std::string &msg ) :
            std::invalid_argument( msg ) {}
};

template <typename TO>
TO fromString( const std::string &src ) {
    std::stringstream ss( src );
    TO result;
    
    if ( ! (ss >> result) )
        throw ConvertError( "Can't convert" );
    
    return result;
}

int main() {
    try {
        int x = fromString<int>( "32" );
        float f = fromString<float>( "3.14159" );
        int y = fromString<int>( "abc" );
        
        std::cout << x << std::endl;
        std::cout << f << std::endl;
        std::cout << y << std::endl;
    } catch ( ConvertError &e ) {
        std::cout << e.what() << std::endl;
    }
}

```

Or, if you don't mind using third party libraries, [Boost.LexicalCast](http://boost.org/libs/conversion/lexical_cast.htm) makes this kind of thing very easy.

---

