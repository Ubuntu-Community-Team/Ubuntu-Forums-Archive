---
title: "C++ global class instance's static member not same between functions"
date: 2012-02-29
forum: Programming Talk
---

### Post by SGFzc2U= on 2012-02-29
entity.C
```

std::vector<int> entity::vec;
entity::entity(){
    vec.push_back(1);
    std::cout<<"From constructor:"<<vec.size()<<std::endl;
}
void entity::showAmount(){
    std::cout<<"From showAmount: "<<vec.size()<<std::endl;
}

```bug.C
```

entity a,b;
int main(){
    b.showAmount();
    return 0;
}

```Output:
From constructor:1
From constructor:2
From showAmount: 0

:confused::confused::confused:

When the entity declarations are local in main(), everything works as expected, with output:
From constructor:1
From constructor:2
From showAmount: 2

---

### Post by dwhitney67 on 2012-02-29
Surely there is more to your code than you have shown.  Please post all of it, not just a snip.

--------------------------------
Edit:

The problem you are experiencing is probably related to a race condition between initializing the static member of the class and the construction of the global variables, which btw, should be avoided!  On my system, I experimented with some code that mimics what you have above, and the application crashed with a Segmentation Fault.  If I place the declaration of entity objects 'a' and 'b' within the main() function, then all works well.

---

### Post by SGFzc2U= on 2012-03-01
That's all the code for recreating the bug minus the #includes and the class definition. Since the full source is >500 rows, it would fill the whole page :)

I found out, that the problem only occurs when the static member is a vector. When it's int, it works as expected. Here's the new source:
entity.C
```

std::vector<int> entity::vec;
int entity::amount=0;
entity::entity(){
    vec.push_back(1);
    amount++;
    std::cout<<"From constructor: vec:"<<vec.size()<<" amount: "<<amount<<std::endl;
}
void entity::showAmount(){
    std::cout<<"From showAmount: vec:"<<vec.size()<<" amount: "<<amount<<std::endl;
}

```bug.C is the exact same as last time.
Out:
From constructor: vec:1 amount: 1
From constructor: vec:2 amount: 2
From showAmount: vec:0 amount: 2

Maybe I'll just substitute the vector with a pointer, and not fight with this anymore.

---

### Post by Npl on 2012-03-01
what likely happens is that the constructors are called in this sequence:
a.entity(); // accesses uninitialized entity::vec -> size = 1
b.entity(); // accesses uninitialized entity::vec -> size = 2
entity::vec.vector(); // initializes entity::vec -> size = 0

then later entity::showAmount() is called.

lesson learned: never depend on initialization order. it should work if you move "std::vector<int> entity::vec;" into bug.c, before "entity a,b;" but thats ugly since you might need an entity instance elsewhere.

similary moving entity a,c into main works because then its guaranteed that entity::vec already got initialized.

either rework your object hierarchy or use the singleton pattern.

---

