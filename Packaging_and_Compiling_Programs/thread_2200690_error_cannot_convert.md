---
title: "error: cannot convert"
date: 2014-01-20
forum: Packaging and Compiling Programs
---

### Post by cdb10 on 2014-01-20
I have a code:
```

class myclass
{
         private:
                  int function2(int);
         public:
                  int function(int);
};
int main()
{
         myclass object1;
         object1.function(3);


}


int myclass::function(int x)
{
         int (*pointer)(int);
         pointer = function2;
         x++;
}


int myclass::function2(int x)
{
         x++;
}

```
[COLOR=#000000]During compilation error occurs:
[/COLOR]```
b.cpp: In member function &#8216;int myclass::function(int)&#8217;:
b.cpp:18:13: error: argument of type &#8216;int (myclass::)(int)&#8217; does not match &#8216;int (*)(int)&#8217;

```

---

