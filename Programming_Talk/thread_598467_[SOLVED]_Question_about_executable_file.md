---
title: "[SOLVED] Question about executable file"
date: 2007-10-31
forum: Programming Talk
---

### Post by leileicats on 2007-10-31
Hi, folks. I am new to Linux environment.
I have coded a simple C++ program as follows:
```
#include <iostream>
using namespace std;

int main()
{
   cout << "Hello World!" << endl;
   return 0;
}
```

After compiling 
```
"lei@maverick:~/code/example/HelloWorld$ g++ HelloWorld.cpp -o hello"
```, I get the executable file "hello". Supposedly, if I key in command:
 ```
lei@maverick:~/code/example/HelloWorld$ hello
``` 
It should output "Hello World!" on the terminal.

However, I got this information:
```

lei@maverick:~/code/example/HelloWorld$ hello
The program 'hello' can be found in the following packages:
 * hello-dbs
 * hello
 * hello-debhelper
Try: sudo apt-get install <selected package>
bash: hello: command not found

```

Is that because the "bash" couldn't find my file?:confused:
Thanks a lot!

---

### Post by carlosjuero on 2007-10-31
try this
```

chmod +x hello
./hello

```

---

### Post by leileicats on 2007-10-31
Thanks, I got it.
I should key in "$ **./hello**" not just "$ hello"

---

### Post by LaRoza on 2007-10-31
The reason for this, is because the cwd is not in the PATH varible, and shouldn't be. Only paths defined in the PATH variable can be executed without specifying the location. "." means the current directory. ".." means one up.

---

