---
title: "[PLEASE IGNORE, ANSWER FOUND] Very easy C++ question"
date: 2009-06-13
forum: Programming Talk
---

### Post by geo909 on 2009-06-13
EDIT:

Please ignore this thread, I found the solution.
Sorry for the spamming!

---

### Post by MadCow108 on 2009-06-13
you declare entry and info as local variables of the entry function.
they are deleted when the function ends (variables go out of scope).
So in print they are undefined.

set them as member variables of the entry class.

---

### Post by simeon87 on 2009-06-13
In these cases, it's better to leave the question in the thread and post the answer. That way, it can also be found by people who search for the answer on the internet.

Actually, this is better in all cases, regardless of whether you've found the answer yourself or not.

---

### Post by ibuclaw on 2009-06-13
> **simeon87 said:**
> In these cases, it's better to leave the question in the thread and post the answer. That way, it can also be found by people who search for the answer on the internet.

Actually, this is better in all cases, regardless of whether you've found the answer yourself or not.

+1

For historic purposes.

Original:
```

#include <iostream>
#include <string>
using namespace std;

class entry {

    public:
    int name, info;
    entry (){};
    entry (char * , char * );
    void print();
};

entry::entry(char * a, char * b){
    string name(a);
    string info(b);
}

void entry::print(void){
    cout << name << endl;
    cout << info << endl;
}

int main(){
entry a, b;

a = entry("George", "phone: 232962");
a.print();

return 0;
}

```

My Solution:
```

#include <iostream>
#include <string>
using namespace std;

class entry {

    public:
**    string name, info;**
    entry (){};
    entry (char * , char * );
    void print();
};

entry::entry(char * a, char * b){
[B]    name = a;
    info = b;[/B]
}

void entry::print(void){
    cout << name << endl;
    cout << info << endl;
}

int main(){
entry a, b;

a = entry("George", "phone: 232962");
a.print();

return 0;
}

```

Regards
Iain

---

### Post by markux^Hs on 2009-06-13
Why do people do that? Delete, or ask to delete their question once it has been answered. Selfishness!

---

### Post by Sinkingships7 on 2009-06-13
> **markux^Hs said:**
> Why do people do that? Delete, or ask to delete their question once it has been answered. Selfishness!

Indeed. The original question should be left, so that others may benefit from it as well.

---

### Post by JordyD on 2009-06-13
> **markux^Hs said:**
> Why do people do that? Delete, or ask to delete their question once it has been answered. Selfishness!

I don't think it's selfishness. They just don't realize how helpful it can be to other people and don't want it to clutter the forums.

---

### Post by markux^Hs on 2009-06-14
> **JordyD said:**
> I don't think it's selfishness. They just don't realize how helpful it can be to other people and don't want it to clutter the forums.

And that *isn't *selfish?

---

### Post by simeon87 on 2009-06-14
> **markux^Hs said:**
> And that *isn't *selfish?

The first step to solving a problem is to be aware of it. Just because you don't realize a problem, that doesn't mean you're selfish. One can act without knowing that it is a problem for others. If you don't change your behaviour when you've become aware of it, then you're selfish :P

---

### Post by markux^Hs on 2009-06-14
> **simeon87 said:**
> The first step to solving a problem is to be aware of it. Just because you don't realize a problem, that doesn't mean you're selfish. One can act without knowing that it is a problem for others. If you don't change your behaviour when you've become aware of it, then you're selfish :P

Touché :popcorn:

---

### Post by geo909 on 2009-06-16
Hello everybody,

I just gave a look at my threads and was surprised to find 9 replies to this one!!!

I made a super stupid mistake (declared as int some variables which were supposed to be strings) and spent one hour trying to find the solution to my problem! I thought nobody would really care about such a thing so I deleted the post without realizing that people had replied.

I apologize if I wasted your time, I didn't really realize that until I read your replies today. I will not do it again

---

### Post by Mirge on 2009-06-16
> **geo909 said:**
> Hello everybody,

I just gave a look at my threads and was surprised to find 9 replies to this one!!!

I made a super stupid mistake (declared as int some variables which were supposed to be strings) and spent one hour trying to find the solution to my problem! I thought nobody would really care about such a thing so I deleted the post without realizing that people had replied.

I apologize if I wasted your time, I didn't really realize that until I read your replies today. I will not do it again

You can go to "Thread Tools" -> "Subscribe to Thread" if you want an email notification when you get replies. Quite useful, I use it all the time!

---

