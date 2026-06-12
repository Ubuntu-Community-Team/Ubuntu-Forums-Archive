---
title: "Eclipse CDT error"
date: 2007-06-18
forum: Programming Talk
---

### Post by cedcey on 2007-06-18
Hello,
I am using CDT and I'd like to start writing code in Eclipse but when I create a project and then a source file I get an error: undefined reference to `main'.
I can't write anything because of it, if I write something and run it it does not work.
I tried to deactivate Build Automatically option but when I finish the code and build it, gives me the same error.

Best regards,

---

### Post by ptillemans on 2007-08-04
Make sure anywhere there is a main method like ::

#include <iostream>

int main() {
        std::cout << "Hello\n";
        return 0;
}


Another thing which can happen is the the C/CPP files are not in a source directory. THen they are not included in the build and the linker cannot find the main method.

---

