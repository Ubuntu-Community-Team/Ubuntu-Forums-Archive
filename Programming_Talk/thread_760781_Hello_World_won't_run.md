---
title: "Hello World won't run"
date: 2008-04-20
forum: Programming Talk
---

### Post by jmkramer872 on 2008-04-20
I am new to programming in general (I'm learning C++), and even newer to Linux, so I figured I would start out with something simple, like Hello World, but I can't even get that to work.  

I used g++ to compile it, but it won't do anything.  I have double and triple checked my code to make sure there are no mistakes.  It compiles without any problem and creates an exe file, but when I run it, I just get the prompt again.  No complaints, nothing.  I'm running Ubuntu 7.10, if it matters.

---

### Post by themusicwave on 2008-04-20
post the code and we will check it out.

---

### Post by red_Marvin on 2008-04-20
Mind posting your code, the compile command you use, and the command you use to run it?

---

### Post by jmkramer872 on 2008-04-20
I have rearranged the code a few times based on books, etc.

Here's the latest code:

#include <iostream>


int main()
{
    using namespace std;
    cout << "Hello World" << endl;
}

And the compile command:

g++ test.cpp -o test

---

### Post by themusicwave on 2008-04-20
One thing I see is that your int main does not have:

return 0; 

at the end.  So you will want to add that to the program.

Also, I usually put the using namespace std after the includes, but I don't know if this is your problem.

---

### Post by Tomosaur on 2008-04-20
Runs fine here, what command are you using to run the program?

Also, I think 'using namespace std;' should generally go just beneath your include lines.

EDIT: And yes, you should generally have 'return 0' at the end of your main method, but it's not absolutely necessary to get your code to run.

---

### Post by themusicwave on 2008-04-20
This version works fine for me:

[PHP]
#include <iostream>

using namespace std;

int main()
{

    cout << "Hello World" << endl;

    return 0;
}
[/PHP]

---

### Post by Lux Perpetua on 2008-04-20
> **jmkramer872 said:**
> I have rearranged the code a few times based on books, etc.

Here's the latest code:

#include <iostream>


int main()
{
    using namespace std;
    cout << "Hello World" << endl;
}

And the compile command:

g++ test.cpp -o testRun **man test** in a terminal to see what's happening. :-) I made this mistake too the first time I compiled a program on a Unix box. Solution:

1. run your program with **./test**, or
2. name your program something else.

---

### Post by red_Marvin on 2008-04-20
And you run it with ./test ? It works on my computer, while I'm running hardy it shouldn't matter as it's valid code as far as I can see.

---

### Post by themusicwave on 2008-04-20
If you compile with:

g++ test.cpp -o hello

Then you run with:

./hello

Also, try running sudo apt-get install build-essential you may be missing a library or something.

---

### Post by finer recliner on 2008-04-20
you're probably running it like this:

```
test
```

which is going to try to run another program that comes with ubuntu that is already called 'test'. thats why you dont get the expected output.

to run the version of 'test' you created, run the executable located in your current directory:
```
./test
```

---

### Post by jmkramer872 on 2008-04-20
I put "using namespace std;" inside main because I saw it that way in a book on Linux.  It looked weird, but I thougt maybe it was a Linux thing.  I just put it back under the includes, and added the "return 0;" statement, but it still won't run.  To try to run it I just type "test" (what I named my output file) at the prompt.

---

### Post by jmkramer872 on 2008-04-20
Thanks finer recliner, that was my problem.  I used "./test" and it worked.

thanks for the quick replies

---

### Post by WW on 2008-04-20
> **Lux Perpetua said:**
> Run **man test** in a terminal to see what's happening. :-) I made this mistake too the first time I compiled a program on a Unix box. Solution:

Been there, done that.  Now I never call an executable "test".

---

### Post by LaRoza on 2008-04-20
The sticky has a great link on compiling and running such programs...

---

