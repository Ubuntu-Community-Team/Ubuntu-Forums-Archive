---
title: "programming with C++"
date: 2007-06-11
forum: Programming Talk
---

### Post by pardesi on 2007-06-11
i have already posted this in Absolute beginner forum [http://ubuntuforums.org/showthread.php?t=470588](http://ubuntuforums.org/showthread.php?t=470588).I was reffered here
so any refernce can be made there. but let me breif u .i am a noob to all thsi . i just installed the essential packages via the code
```
sudo aptitude install build-essential

gedit sampleProgram.cpp
```
then wrote thsi in a Gedit document
```
#include <iostream>
int main()
{
   std::cout <<  "Hello world" << std::endl;
   return 0;
}
```
now when i write this
```
g++ sampleProgram.cpp -o sampleProgram.bin
```
 i get this
```
pardesi@pardesi-desktop:~$ g++ sampleProgram.cpp -o sampleProgram.bin
pardesi@pardesi-desktop:~$ 


```
someone please help

---

### Post by WW on 2007-06-11
Believe it or not, that means it worked. Now, to run the program, enter the command
```

$ ./sampleProgram.bin

```

---

### Post by LaRoza on 2007-06-11
It seems you left the old thread, I didn't know you went here. I posted on the old thread about what to do and answered your other question.

If you respond to anything I wrote there, post it here instead so I can find it :)

---

### Post by leibowitz on 2007-06-11
This made my day. 

Thanks

---

### Post by LaRoza on 2007-06-11
> **leibowitz said:**
> This made my day. 

Thanks

How? Was it amusing? Helpful?

---

### Post by pardesi on 2007-06-11
**@WW**Thanks u made my night;)

**@LaRoza** Thanks :p:p:p .Sorry i posted here as you acvised me to do so .Yes replying to your last but one post on the other forum yes i know a bit of python i learned it from wikipedia.Yes that's much simpler(upto what i know) it's logical and above all beautiful...programming...

i know now why i am into ubuntu.

---

### Post by Sockerdrickan on 2007-06-11
Remember, you don't have to name it .bin, this is Linux ;D

---

### Post by leibowitz on 2007-06-11
LaRoza: I was refering to the pardesi problem. Not related to you or your reply in any way.

---

### Post by LaRoza on 2007-06-11
> **leibowitz said:**
> LaRoza: I was refering to the pardesi problem. Not related to you or your reply in any way.

Just curious, I was not sure if you were referring to the post I wrote, or the thread.

---

### Post by LaRoza on 2007-06-11
> **Tux0r said:**
> Remember, you don't have to name it .bin, this is Linux ;D

I find file extensions useful for determining the file type, even if the computer doesn't use it. This is especially useful if the source and the executable have the same name. 

To pardesi, you don't need to use file extensions at all, but I think it is a good practice so you can determine file type, and it makes it easier to use the files on another OS.

---

### Post by meatpan on 2007-06-11
As mentioned above, 'silence is success' in linux.  This philosophy is a bit different from some other operating system philosophies.   

If you are still unsure if your program was successful, consider inspecting the program's return value.  This is a bit more advanced usage, but you might find it helpful during debugging.  In a bash shell, you can inspect the return code by running 'echo $?'.  A value of zero means success, and anything else means failure.

---

