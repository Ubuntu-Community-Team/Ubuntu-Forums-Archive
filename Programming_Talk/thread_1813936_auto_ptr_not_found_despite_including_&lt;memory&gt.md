---
title: "auto_ptr not found despite including &lt;memory&gt;"
date: 2011-07-28
forum: Programming Talk
---

### Post by Kschikan on 2011-07-28
I'm trying to compile some cpptest suites, and GCC is telling me it can't find 'auto_ptr'. I searched around and saw the I needed to '#include <memory>', but I get the same error.

Under GCC 4.5.2 and Ubuntu 11.04, I get the following error:
```

kane@Griffin:~/battlecubes$ make tests
g++ -o test_suite test/*.cpp
test/AllTests.cpp: In function ‘int main()’:
test/AllTests.cpp:10:9: error: ‘auto_ptr’ was not declared in this scope
test/AllTests.cpp:10:29: error: expected primary-expression before ‘>’ token
test/AllTests.cpp:10:35: error: expected type-specifier before ‘ShipTest’
test/AllTests.cpp:10:35: error: expected ‘)’ before ‘ShipTest’
make: *** [tests] Error 1
```

When trying to compile the following file:

```
#include <cstdlib>
#include <memory>

#include "cpptest.h" 

int main ( ) 
{   
    Test::Suite ts;
  
    ts.add(auto_ptr<Test::Suite>(new ShipTest));
  
    Test::TextOutput output(Test::TextOutput::Verbose);
    return ts.run(output) ? EXIT_SUCCESS : EXIT_FAILURE;
}  
```

Any ideas?

---

### Post by GeneralZod on 2011-07-28
auto_ptr is in the "std" namespace.

---

### Post by Kschikan on 2011-07-28
Well, that was so blindingly obvious I feel dumb. Thanks for the update!

---

