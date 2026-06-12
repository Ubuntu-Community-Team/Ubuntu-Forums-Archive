---
title: "C++ Class Destructor Issue"
date: 2009-12-24
forum: Programming Talk
---

### Post by JupiterV2 on 2009-12-24
Is it expected behavior or a compiler/library bug that C++ class destructors aren't called when exit() is used:

[php]
#include <iostream>
#include <cstdlib>

class Test
{
    private:
        int i;
    
    public:
        Test(int);
        ~Test();
};

Test::Test(int n = 0)
{
    i = n;
    
    std::cout << "This is the constructor for test " << i << std::endl;
}

Test::~Test()
{
    std::cout << "This is the destructor for test " << i << std::endl;
}

int main()
{
    Test t0;
    Test t1(1);
    Test *t2 = new Test(2);
    
    std::cout << "None of the tests should call their destructors."
        << std::endl;
        
    exit(EXIT_SUCCESS);
}
[/php]

Test 2(t2) is dynamically allocated and delete is required for it's destructor to be called.

Tests 0 and 1 (t0, t1) also fail to call their destructors.

Is this expected/defined behavior or a bug in cstdlib.h? I realize that this header is just a C library wrapper but as it is a part of the C++ standard library you would think it would at least call C++ class destructors on exit before freeing the stack and exiting.

---

### Post by dwhitney67 on 2009-12-24
You are blowing your app clear to kingdom come using the exit() call.  Use a 'return' statement to return from the main() function.  Then you will see the destructors called for t0 and t1.

```

int main()
{
   ...

   //exit(EXIT_SUCCESS);

   return 0;   // or use EXIT_SUCCESS in lieu of 0
}

```

---

### Post by not_a_phd on 2009-12-24
From the man page for exit():

"The function **_exit**() terminates the calling process "immediately". Any open file descriptors belonging to the process are closed; any children of the process are inherited by process 1, *init*, and the process's parent is sent a **SIGCHLD** signal. "


Because it kills the process immediately, no additional user code will be executed. This includes the destructors for your various classes. 

On a separate note. Even with the **return 0** call, if you do not explicitly delete t2, you will not call that destructor either.

---

